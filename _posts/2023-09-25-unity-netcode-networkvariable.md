---
layout: post
title:  Použití Native Collection ve vlastní NetworkVariable
subtitle: Strasti, pasti, nástrahy, postřehy a střípky z vývoje multiplayer deskovky
tags: [unity,netcode,networking,gamedev,multiplayer]
category: devlog
---

Jakmile se pustíte do multiplayeru s pomocí [NGO](https://docs-multiplayer.unity3d.com/netcode/current/about/) brzy přijdete na to,
že vám defaultní struktury _NetworkVariable_ a _NetworkList_ nebudou stačit. Budete si muset napsat vlastní.

## Jak pracovat s vlastní síťovou proměnnou?

V prvé řadě je třeba zmínit několik důležitých informací.

_NetworkVariable_ používejte uvnitř třídy _NetworkBehaviour_, jinak nebude fungovat.
Párkrát jsem se nachytal, že jsem si nevšiml a měl proměnou uvnitř MonoBehaviour
nebo Lifetimescope ([VContainer](https://vcontainer.hadashikick.jp/)) a hledal jsem chybu půl dne.

Tady pozor na to, že každá proměnná se po sítí aktualizuje jinak, v jiný čas a taky pořadí! To není garantované. Píšou to
[tady](https://docs-multiplayer.unity3d.com/netcode/current/learn/rpcvnetvar/), ale já to samozřejmě pořádně nečetl.

Netcode nabízí několik interface, jejichž význam nemusí být hned jasný, takže lehce dovysvětlím:

- [INetworkSerializeByMemcpy](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/serialization/inetworkserializebymemcpy/)
- [INetworkSerializable](https://docs-multiplayer.unity3d.com/netcode/current/advanced-topics/serialization/inetworkserializable/)
- [NetworkVariableBase](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkvariable/#custom-networkvariable-implementations)

**INetworkSerializeByMemcpy**

- struct
- musí být unmanaged (i nested)
- (de)serializace je automatická

Takový typ pak můžete použít rovnou v NetworkVariable<MujTyp> a lze posílat přes RPC.

**INetworkSerializable**

- struct
- managed i unmanaged typy
- (de)serializaci si musíte napsat

Takový typ pak můžete použít rovnou v NetworkVariable<MujTyp> a lze posílat přes RPC.

**NetworkVariableBase**

- class!

Tady si můžete implementovat co chcete včetně (de)serializace. Instanci si tvoříte již sami.

## Příklad použití vlastní proměnné

Představte si, že chcete s hráči spárovat nějaká data.

Typicky uděláte v první verzi zřejmě použijete pro vztah hráč a data Dictionary,
kde klíč bude Guid nebo jiný identifikátor hráče (klidně i string) a hodnota bude nějaká struktura s informacemi o hráči.

Například:

```
public class NetworkPlayersInfo : NetworkBehaviour
{
    private readonly PlayerInfoNetworkVariable m_PlayersInfoNetworkVariable = new();
}

[Serializable]
public class PlayerInfoNetworkVariable : NetworkVariableBase
{
    private Dictionary<Guid, PlayerInfo> m_PlayersInfo = new();
    // povinné metody ReadDelta, ReadField, WriteDelta, WriteField
}
```

Vypadá to hezky, ale má to pár háčků. Pojďme si ukázat upravenou verzi a posléze ji okomentovat.

```
public class NetworkPlayersInfo : NetworkBehaviour
{
    private readonly PlayerInfoNetworkVariable m_PlayersInfoNetworkVariable = new();
    
    private void Awake()
    {
        m_PlayersInfoNetworkVariable.Initialize();
    }
}

[Serializable]
public class PlayerInfoNetworkVariable : NetworkVariableBase
{
    private NativeHashMap<byte, PlayerInfo> m_PlayerInfoMap;
    
    public void Initialize()
    {
        m_PlayerInfoMap = new NativeHashMap<byte, PlayerInfo>(10, Allocator.Persistent);
    }
    
    public override void Dispose()
    {
        m_PlayerInfoMap.Dispose();
    }

    // povinné metody ReadDelta, ReadField, WriteDelta, WriteField
}

public struct PlayerInfo : INetworkSerializeByMemcpy {
    // jen unmanaged typy
    public byte PlayerId;
    public ushort TotalMoney;
    // atd.
}
```

Za prvé, snažte se po sítí přenášet, co nejmenší množství dat. Tzn. ideálně jen unmanaged typy - byte, ushort, enumy atd.

Pokud to jde, doporučuji použít [Unity Native Collection](https://docs.unity3d.com/Manual/JobSystemNativeContainer.html). Mělo
by to být lepší než System.Collections.

Problém je, že s Native Collection nemůžete vytvořit instanci přímo v deklaraci fieldu ani v konstruktoru
kvůli memory leaku. To je třeba jeden z důvodů, proč nelze vytvořit instanci _NetworkList_ přímo v deklaraci,
ale musíte ji vytvořit v Awake()

Je to opět uvedeno [tady v příkladu](https://docs-multiplayer.unity3d.com/netcode/current/basics/networkvariable/):

```
void Awake()
{
    // NetworkList can't be initialized at declaration time like NetworkVariable. It must be initialized in Awake instead.
    // If you do initialize at declaration, you will run into Memmory leak errors.
    TeamAreaWeaponBoosters = new NetworkList<AreaWeaponBooster>();
}
```

## Závěr

Několik doporučení:
- pro ladění je super [ParrelSync](https://github.com/VeriorPies/ParrelSync)
- ještě lepší je [Multiplayer Play Mode](https://docs-multiplayer.unity3d.com/tools/1.1.0/mppm/), ale funguje bohužel až od verze 2023.1 a dost často padá
- hodně používejte NetworkLog a Debug
- pamatujte, že čas ani pořadí proměných není garantované - musíte vymyslet vlastní synchronizaci (o tom jindy)
- pro testovaní nepište zbytečně WriteDelta a ReadDelta - je to opruz a je to důležité až pro produkční verzi
- používejte Asserty, hodně to usnadní ladění
- klidně rozsekejte logiku jedna proměnná = jeden NetworkVariable objekt
- budete téměř vždy potřebovat callbacky, že se data změnily
- navrhněte si naming a ten dodržujte
- počítejte s tím, že nad síťovými proměnnými budete stavět další vrstvu, protože network variables jsou psány pro optimalizaci pásma a vy budete potřebovat
získané data nějak prezentovat (například si přes síť pošlete u karetní hry jen CardId:byte a na klientovi si z registru karet vytáhnete textury apod.)

P.S.: _NetworkList_ má aktuálně nepříjemnou chybu, že neposílá připojeným klientům oznámení o změně,
viz [nahlášený bug](https://github.com/Unity-Technologies/com.unity.netcode.gameobjects/issues/2689).

Neváhejte komentovat, sdílet svůj názor, nápad, zkušenost. Uvítám každou dobrou radu, kritiku i pomoc.
Rovněž uvítám kolegy programátory, grafiky, zvukaře, animátory, vfx specialisty a mnoho dalších, kteří se na vývoji her podílí.
