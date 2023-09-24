---
layout: post
title:  Blog o vývoji her
subtitle: Současný vývoj, plány do budoucna, zákulisí
tags: [unity,netcode,networking,gamedev,multiplayer,boardgames]
category: devlog
---

Ahoj,

já jsem Patrik a chtěl bych se s vámi podělit o zážitky a zkušenosti s vývojem online multiplayer deskovky v [Unity](https://unity.com/)
s využitím [Netcode for GameObjects](https://docs-multiplayer.unity3d.com/netcode/current/about/) (NGO).


## Cesta k vývoji

[Unity](https://unity.com/) se jako hobby vývojář věnuji pár let. Nikdy jsem nevydal hru. Nikdy jsem žádnou nedokončil.
Nikdy jsem se neúčastnil žádného [jamu](https://itch.io/jams).

Mám ale nějakou zkušenost s vývojem multiplayer karetní/deskové hry. Vyvinul ji sice někdo jiný a já se "jen"
staral vývoj klienta v Unity a serverovou část v Javě. Nicméně musel jsem kód hodně optimalizovat a rozšířit o podporu Websocket.
K tomu jsem těsně spolupracoval s art directorem a grafickým týmem.

Byla to skvělá zkušenost, ale herní vývoj moc nenese, tak jsem skočil rovnýma nohama do fintechu na .NET.
Tím šel hobby vývoj k ledu. Priority byly prostě jinde.

Herní průmysl jsem, ale po očku sledoval. Bavil jsem se s lidmi v oboru, přemýšlel a vymýšlel, jak se dostat zpátky.

## Nápad na hru

Nápadů jsem měl spousty. [V šuplíku](https://www.facebook.com/groups/GDCczsk). Nápad je ovšem sám o sobě bezcenný. Důležitá je exekuce. A dle moudrých knih,
to chce i notnou dávku [štěstí](https://www.databazeknih.cz/knihy/krev-pot-a-pixely-pribehy-vitezstvi-a-silenstvi-ze-zakulisi-vyvoje-videoher-403587).

Z vlastních zkušeností a pozorování okolí jsem dospěl k závěru, že slušnou šanci na úspěch může mít multiplayer.
Viděl jsem to u kamarádů, u syna, známých i na různých platformách. I [poměrně triviální hry](https://snake.io/) mohou být velmi zábavné,
když můžete hrát s kámoši nebo proti komukoliv z druhého konce planety.

Bylo rozhodnuto. Bude to tedy mulťák.

## Multiplayer

První pokusy naprogramovat triviální multiplayer byly tragické. Tehdy snad ještě experimentální Netcode for Entities v Unity byly
nedodělané, plné chyb a já si trhal vlasy, zuby i nehty. Po čase jsem to vzdal. Neměl jsem na to nervy ani skill.

Zkoušel jsem i různé alternativy. Ale například Photon či Mirror a další se mi prostě nelíbily.

V Unity se ale kopli do zadku a přišli s [Netcode for GameObjects](https://docs-multiplayer.unity3d.com/netcode/current/about/).
K tomu rozjeli [Unity Gaming Services](https://dashboard.unity3d.com/), které s NGO spolupracují. A najednou to zdá, že v roce 2023 by to i šlo. Nebo ne?

## Žánr

Co se týče typu hry, žánru a podobně, neměl jsem vůbec páru co bych chtěl dělat. Jen jsem věděl, že to bude multiplayer v Unity.
A věděl jsem, že to rozhodně nikdy nebude Áčková hra, náročné MMORPG nebo FPSko. To je na roky vývoje s nejistým výsledkem.
Tedy nikdy neříkej nikdy. Ale teď určitě ne. 

Bylo potřeba zvolit něco jednoduchého. Něco, co mám šanci dokončit sám, bez pomoci po večerech. Za rozumnou dobu.

Ale co by to mělo být?

Nakonec pomohla náhoda. Jednoho dne jsme se synem hráli klasické deskovky. A pro něj to byla děsná nuda. Pořád čtete pravidla,
hádáte se, kostky pořád někde padají, málo místa na stole, ve dvou to je taky nic moc.

"Tati, mě to neba. Kdyby to bylo na PSku, tak by to bylo lepší," zazdil to syn.

A nápad byl na světě. Co takhle se pokusit tuhle deskovku portovat?

## Port deskovky

"Ses zbláznil? To nikdo nebude hrát," říkal mi známý - dlouholetý hráč deskovek.

Core hráči deskovek si užívají to fyzično, figurky, kontakt s lidmi, pokec, i při o pravidla.

Online je úplně něco jiného. Bude to fungovat? Funguje to již jinde? Zkoušel to někdo?

Odpověď je ano. Ano, zkoušel, funguje a dokonce jsou některá studia i poměrně úspěšná.

Publikum se asi najde. Kámen úrazu bude hratelnost. A druhý oříšek je, zda se jen inspirovat nebo
portovat a domluvit se s původním autorem.

Tohle ještě nemám vyřešeno. Nechám si poradit od zkušenějších.

## Hratelnost ##

Problém portování klasických deskovek do digitální podoby je v tom, že u stolu vidíte celý board.

Layout boardu, design karet apod. je na míru ušitý fyzické reprezentaci. To co, ale funguje fyzicky, 
nemusí fungovat online, nebo je potřeba udělat úplně jinak.

Výhody a nevýhody portu:
- AI - vytvořit slušné AI nemusí být snadné
- pokud bude dost hráčů na serveru nebude problém sehnat parťáky, případně lze hrát s kamarády přes [Lobby](https://docs.unity.com/ugs/manual/lobby/manual/unity-lobby-service)
- automatická kontrola pravidel
- semi automatické hraní (automatická aplikace některých efektů a pravidel hry)
- vizuální a audio efekty
- případné rozšíření hry
- balance hry
- překlad

UX/UI jsem zatím neřešil, tak daleko ještě nejsem. Ale uvítal bych pomoct zkušených kolegů z branže.

## Prototyp

Aktuálně jsem ve fázi budování prototypu. Ten je určen pro případného vydavatele a úzké skupině vybraných jednotlivců.

V této fázi je důležité soustředit se jen na to podstatné, tedy na základní herní mechaniku. Žádný zbytečný refaktoring,
efekty, audio, video apod. Jen to, co "prodá" myšlenku vydavateli.

## Finance

Vývoj stojí peníze. Hromadu peněz. I přesto, že si hru boucháte doma na koleně, stojí to váš čas = [ušlá příležitost](https://cs.wikipedia.org/wiki/N%C3%A1klady_ob%C4%9Btovan%C3%A9_p%C5%99%C3%ADle%C5%BEitosti)

Já jsem si toho dobře vědom a vím, že nic není zadarmo. Je to makačka, nervy, stres a bude potřeba peníze. Dříve nebo později.

Proto jsem se vydal cestou spolupráce se [Vláďou Geršlem](https://www.cybersail.consulting/), který je zkušeným matadorem v oboru.
Je to velká studnice znalostí a zkušeností. Zná trh, zná vydavatele, ví prostě [JAK](https://visiongame.cz/co-je-cyber-sail-consulting/).

To je můj plán, jak uvést hru v život a najít na vývoj peníze. Musím ale dokončit prototyp.

## Závěr ##

Vývoj her je obrovské téma. Chystám články o tom, jak se motivovat a vydržet u vývoje, jak se soustředit na to podstatné,
jak přemýšlet o architektuře, performance, jak ukládat data apod.

Máte se rozhodně na co těšit!

Na závěr bych rád poděkoval české a slovenské herní komunitě, protože jsou skvělí.
Je to výborný zdroj inspirace, podpory a dobré nálady.

Doporučuji skupiny na Facebooku [GDCczsk](https://www.facebook.com/groups/GDCczsk) a [Unity3D :: CZ_SK](https://www.facebook.com/groups/1170118506368976)
a rovněž skupinu [Unity 3D](https://nyx.cz/discussion/18006) na dnes již legendárním serveru Nyx.

Rovněž velké díky [Vláďovi Geršlovi](https://www.cybersail.consulting/) za jeho cenné připomínky, rady a tipy.

Stay tuned!

Neváhejte komentovat, sdílet svůj názor, nápady či zkušenosti. Uvítám každou dobrou radu, kritiku i pomoc.
Rovněž uvítám kolegy programátory, grafiky, zvukaře, animátory, vfx specialisty a mnoho dalších, kteří se na vývoji her podílí.

