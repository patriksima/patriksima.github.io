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
Nikdy jsem se neúčastnil žádného [jamu](https://itch.io/jams). Získal jsem ale pracovní zkušenost s vývojem multiplayer
karetní/deskové hry, poměrně úspěšné. Staral jsem se o vývoj klienta v Unity i o serverovou část v Javě. Nutno podotknout,
že hru vyvinul někdo jiný, já jsem kód jen upravoval, rozšiřoval a optimalizoval.

Herní vývoj moc nenese. A účty je třeba platit, takže jsem přeskočil do fintechu na .NET. Hobby vývoj šel taky k ledu. Priority byly prostě jinde.

Herní průmysl jsem, ale po očku sledoval, bavil se s lidmi v oboru, přemýšlel a vymýšlel jak se dostat zpátky a mít na složenky.

## Nápad na hru

Nápadů jsem měl spousty. [V šuplíku](https://www.facebook.com/groups/GDCczsk). Nápad je ovšem sám o sobě k... bezcenný. 
Důležitá je exekuce. A zřejmě to chce i dost [štěstí](https://www.databazeknih.cz/knihy/krev-pot-a-pixely-pribehy-vitezstvi-a-silenstvi-ze-zakulisi-vyvoje-videoher-403587).

Z vlastních zkušeností a pozorování okolí jsem došel k závěru, že slušnou šanci na úspěch bude mít multiplayer.
Viděl jsem to u sebe, u syna, u kamarádů, známých i na různých platformách. I [poměrně triviální hry](https://snake.io/) mohou být rázem velmi zábavné,
když můžete hrát s kámoši nebo proti komukoliv z druhého konce planety.

Bude to tedy mulťák.

## Multiplayer

První pokusy byly tragické. Když jsem zkoušel [Netcode for GameObjects](https://docs-multiplayer.unity3d.com/netcode/current/about/) v Unity.
Byl snad ještě v experimentální verzi a já si trhal vlasy, zuby i nehty. Po čase jsem to vzdal. Neměl jsem na to nervy ani skill.

Hledal jsem alternativy. Photon, Mirror a další se mi prostě nelíbily. U NGO se mi líbila ta jednoduchost, ale hodně tomu chybělo.

V Unity se ale kopli do zadku a s NGO docela pohnuli. K tomu rozjeli [Unity Gaming Services](https://dashboard.unity3d.com/), které s NGO spolupracují. A najednou se v 
roce 2023 zdá, že by to i šlo. Nebo ne?

## Žánr

Vůbec jsem neměl představu co chci dělat. Jaký žánr, typ hry, nic. Jen jsem věděl, že to bude multiplayer v Unity.
A věděl jsem, že to rozhodně nikdy nebude Áčková hra, náročné MMORPG nebo FPSko. To je na roky vývoje s nejistým výsledkem. 

Chtělo to něco jednoduchého. I relativně jednoduchá hrá v multiplayeru může být zábavná sranda, kterou někdo bude hrát.

Ale co by to mělo být?

Nakonec pomohla náhoda. Jednoho dne jsme se synem hráli klasické deskovky. Pro teenagery je to nuda. Je to pomalé,
pořád čtete pravidla apod.

"Hej, není to digitálně?"

A nápad byl na světě. Zkusím port jedné deskovky.

## Port deskovky

"Ses zbláznil? To nikdo nebude hrát," říkal mi známý - dlouholetý hráč deskovek.

Hráči deskovek si užívají to fyzično, figurky, kontakt s lidmi, pokec, i při o pravidla.

Online je úplně něco jiného. Bude to fungovat? Funguje to již jinde? Zkoušel to někdo?

Odpověď je ano. Ano, zkoušel, funguje a dokonce jsou taková studia i poměrně úspěšná.

Publikum se asi najde. Kámen úrazu bude hratelnost. A druhý kámen, zda se jen inspirovat nebo
portovat a domluvit se s původním autorem.

Tohle ještě nemám vyřešeno. Pojďme tedy k hratelnosti.

## Hratelnost ##

Problém portování klasických deskovek do digitální podoby je v tom, že u stolu vidíte celý board.
Layout boardu, design karet apod. je na míru ušitý fyzické reprezentaci. To co, ale funguje fyzicky, 
nemusí fungovat online, nebo je potřeba udělat úplně jinak.

Výhody a nevýhody portu:
- AI - vytvořit slušné AI nemusí snadné
- pokud bude dost hráču na serveru nebu problém sehnat parťáky, případně lze hrát s kamarády přes [Lobby](https://docs.unity.com/ugs/manual/lobby/manual/unity-lobby-service)
- automatická kontrola pravidel
- semi automatické hraní (automatická aplikace některých efektů a pravidel hry)
- vizuální a audio efekty
- případné rozšíření hry
- balance hry
- překlad

UX/UI jsem zatím neřešil, tak daleko ještě nejsem. Ale uvítal bych pomoct zkušených kolegů z branže.

## Prototyp

Aktuálně jsem ve fázi budování prototypu, který implementuje základní herní smyčku. Prototyp je určen pro případného vydavatele
a k verifikaci nápadu v úzké skupině vybraných jednotlivců. Důležité je se soustředit na to podstatné, zbytečně nerefactorovat,
nevymýšlet zbytečné efekty, grafiku, zvuky apod. Je to podstatné, co pomůže prototyp "prodat" u publishera. Ten někdy umí zajistit
i další financování vývoje. O tom, ale později v dalších článcích.

## Závěr ##

Vývoj her je obrovské téma. Chystám články o tom, jak se motivovat a vydržet u vývoje, jak se soustředit na to podstatné,
jak přemýšlet o architektuře, performance, jak ukládat data apod.

Na závěr bych rád poděkoval české a slovenské herní komunitě, protože jsou skvělí a umí se navzájem podpořit. Je to výborný zdroj inspirace a dobré nálady.
Doporučuji skupiny na Facebooku [GDCczsk](https://www.facebook.com/groups/GDCczsk) a [Unity3D :: CZ_SK](https://www.facebook.com/groups/1170118506368976)
a rovněž skupiny [Unity 3D](https://nyx.cz/discussion/18006) na dnes již legendárním server Nyx.

Stay tuned!

Neváhejte komentovat, sdílet svůj názor, nápad, zkušenost. Uvítám každou dobrou radu, kritiku i pomoc.
Rovněž uvítám kolegy programátory, grafiky, zvukaře, animátory, vfx specialisty a mnoho dalších, kteří se na vývoji her podílí.

