---
layout: post
title: "Toxický senior: Jak ho poznat a co s ním"
subtitle: Nepostradatelný člověk je ve skutečnosti největší riziko firmy
tags: [career, leadership, toxicity, software engineering, management]
---

> „Kdybych odešel, tak se to tu zhroutí."

Pokud tohle někdo ve firmě říká – nebo si to aspoň myslí – je to problém. A ne malý. Nepostradatelnost není známka geniality. Je to červená vlajka.

V IT branži se často mluví o tom, co dělá seniora seniorem. Méně se ale mluví o „nepostradatelných primadonách" – lidech, kteří si hlídají své know-how, nepřipouští diskuzi a blokují ostatní. Pojďme se na ně podívat zblízka.

## Tři archetypy toxického chování

V praxi se vyskytuje několik variant toxických „seniorů". Všechny spojuje jedno: **budují si pozici, ze které je nelze vyhodit**. A firmy jim to tolerují – dokud není pozdě.

### 1. Strážce kódu

Představte si vývojáře, který ve firmě pracuje roky. Postupně se stal architektem celého technického stacku. Všechny projekty sdílejí společný základ, který on sám navrhl a udržuje. Problém? **Ten základ je špatný.** Ale nikdo to neví, protože nikdo jiný mu nerozumí.

Když přijde nový člověk a navrhne zlepšení, Strážce ho odmítne. Když někdo opraví chybu jinak, než by ji opravil on, je to „špatně". Když se management zeptá na technický stav, dostane uklidňující odpověď. A když se někdo ozve nahlas?

Strážce má v týmu reputaci „toho chytrého". Ostatní mu věří – nebo se mu neodváží odporovat. Vedení nemá technické znalosti na to, aby posoudilo kvalitu jeho práce. A tak nový člověk, který vidí problémy, nakonec odchází. Strážce zůstává.

**Důsledek:** Firma je závislá na jednom člověku. Technický dluh roste. Inovace se nedějí. Noví lidé neutíkají před prací, ale před Strážcem.

### 2. Neprůstřelný správce

Tahle varianta se často vyskytuje v infrastruktuře. Správce sítí, administrátor serverů, DevOps „guru" – člověk, který má klíče od všeho. A nikdo jiný neví, jak to funguje.

Systémy rostly metodou pokus-omyl. Dokumentace neexistuje, nebo je zastaralá. Když se někdo zeptá na stav infrastruktury, dostane vágní odpověď. Když vedení navrhne audit od externích specialistů, je to „zbytečné" nebo „urážlivé".

Typický scénář: Nový manažer prosadí nezávislý audit. Ten dopadne špatně – bezpečnostní díry, zastaralé systémy, chybějící zálohy. Konfrontace se správcem nevede ke spolupráci, ale k požadavkům: „Dej mi rozpočet na tohle a tohle." Priority vedení ho nezajímají. Komunikace končí.

A pak přijde zvrat: Správce má blízký vztah s majitelem nebo vyšším vedením. Odchází manažer, ne správce.

**Důsledek:** Kritická infrastruktura je black box. Bezpečnostní rizika nikdo nezná. Firma je rukojmím jednoho člověka.

### 3. Teritoriální kolega

Tohle je nejzákeřnější varianta, protože se často maskuje za „pomoc nováčkům". Kolega, který je ve firmě déle, se cítí ohrožen každým, kdo by mohl být schopnější.

Začíná to nenápadně. Nový člověk dostává nejhorší úkoly. Jeho návrhy jsou ignorovány nebo zesměšňovány. Na poradách je přerušován. Postupně se stupňuje tlak – od pasivní agrese přes záměrné zatajování informací až po otevřenou šikanu.

Častý scénář: Nováček situaci eskaluje k vedení. Vedení donutí staršího kolegu sepsat dokumentaci a předat znalosti. A pak? **Vyhodí oba dva.** Technicky problém vyřešen – dokumentace existuje, konflikt zažehnán. Ale jakou zprávu tohle vysílá zbytku týmu? „Neozývej se, nebo skončíš taky."

**Důsledek:** Firma přichází o talenty. Ti, co zůstávají, se naučí mlčet. Kultura se rozpadá.

## Proč to firmy tolerují?

Tady je jádro problému. Toxické chování existuje, protože mu to někdo dovolí. Proč?

### Strach z nepostradatelnosti

„Co když odejde a my to nezvládneme?" Tohle je past. Čím déle čekáte, tím je závislost větší. Čím je závislost větší, tím je strach silnější. A tak se nic neděje – dokud toxický člověk neodejde sám, nebo dokud se firma nezhroutí.

### Osobní vztahy

Toxický člověk je často ve firmě dlouho. Zná lidi. Má „kamarády" ve vedení. Hraje golf se správnými lidmi. A když přijde konflikt, management věří tomu, koho zná déle – ne tomu, kdo má pravdu.

### Neschopnost posoudit kvalitu

Vedení často nemá technické znalosti na to, aby rozpoznalo špatný kód, rizikovou infrastrukturu nebo toxickou dynamiku v týmu. Spoléhá se na „experty" – tedy na ty samé lidi, kteří problém způsobují.

### Averze ke konfliktu

Řešit toxické chování je nepříjemné. Znamená to těžké rozhovory, možná právníky, určitě drama. Je jednodušší zavřít oči a doufat, že to nějak dopadne. (Nedopadne.)

## Jak tomu předcházet?

Toxické chování se daří tam, kde chybí systémové pojistky. Podívejme se na osvědčené postupy, které problém buď odhalí včas, nebo mu úplně zabrání.

### Collective Code Ownership místo silných vlastníků

Martin Fowler rozlišuje tři modely vlastnictví kódu. **Strong code ownership** – kdy jeden člověk „vlastní" modul a ostatní musí žádat o změny – je živnou půdou pro Strážce kódu. Fowler doporučuje buď **weak ownership** (vlastník dohlíží, ale ostatní mohou měnit), nebo ideálně **collective ownership** – kód patří celému týmu.

Prakticky: Pokud refaktoring vyžaduje povolení jednoho člověka, máte problém. Pokud změna veřejného rozhraní znamená týden čekání na „vlastníka", máte problém.

### Povinné code review od více lidí

Každý pull request by měl projít revizí od minimálně dvou dalších vývojářů. Ne proto, že nikomu nevěříme – ale proto, že **znalosti se šíří přirozeně**. Když tři lidé vidí každou změnu, žádná část kódu nezůstane black boxem.

**Pozor na zneužití:** Code review může být samo o sobě nástrojem šikany. Toxický člověk používá PR komentáře k ponižování: „Proč se ptáš? Nezdržuj!" „Když to nechápeš, co tady děláš?" „Klikni approve a neblokuj sprint." 

Tohle není code review – je to zastrašování. Zdravé code review znamená **trpělivě vysvětlovat**, odpovídat na otázky, a brát feedback jako příležitost ke zlepšení. Pokud se lidé bojí ptát „proč", něco je špatně. Kultura týmu by měla oceňovat zvídavost, ne ji trestat.

### Sdílení znalostí v praxi

Čisté pair programming (dva vývojáři, jeden počítač, celý den) je v praxi vzácné. Existují ale praktičtější alternativy:

- **Code walkthroughs** – autor provede kolegy svým kódem a vysvětlí rozhodnutí. Otázky jsou vítány.
- **Mob programming sessions** – celý tým řeší složitý problém společně. Znalosti se šíří organicky.
- **Pravidelné knowledge sharing** – týdenní session, kde někdo prezentuje část systému, kterou zná nejlépe.
- **Dokumentační dny** – čas vyhrazený na psaní dokumentace a wiki.

Klíčové je, aby **žádná část systému nezůstala v hlavě jednoho člověka**. Forma je méně důležitá než výsledek.

### Rotace zodpovědností

Každý člen týmu by měl během roku pracovat na různých částech systému. Pro infrastrukturu: Nikdo by neměl být jediný, kdo umí restartovat produkci nebo má přístup ke kritickým systémům.

Pokud ano, máte **bus factor 1** – stačí, aby jeden člověk odešel (nebo byl „sražen autobusem"), a projekt se zhroutí. Zdravý tým má bus factor minimálně 2–3.

### Pravidelné nezávislé audity

Interní pohled má slepé skvrny. **Externí audit** – ať už kódu, infrastruktury, nebo bezpečnosti – odhalí problémy, které insideři nevidí (nebo nechtějí vidět). Důležité: audit nesmí být „test" pro konkrétního člověka, ale běžná součást provozu.

Neprůstřelný správce obvykle audit sabotuje nebo bagatelizuje výsledky. Právě to je varovný signál.

### Dokumentace jako standard, ne jako trest

Dokumentace by měla být **součástí definice hotového** (definition of done). Ne jako administrativní zátěž, ale jako přirozená část práce. Pokud někdo systematicky odmítá dokumentovat s výmluvou „nemám čas" nebo „je to zbytečné", ptejte se proč.

Tip: Dokumentaci by měl psát někdo jiný než autor kódu. Pokud kolega nedokáže na základě dokumentace systém provozovat, dokumentace je nedostatečná.

### Strukturovaný onboarding s měřitelnými milníky

Nováček by měl mít jasný plán: co má umět po týdnu, po měsíci, po třech měsících. **Mentor z jiného týmu** poskytuje nezávislý pohled. Pravidelné check-iny odhalí, zda dostává podporu – nebo „nejhorší úkoly".

Pokud nováčci systematicky odcházejí z jednoho týmu nebo od jednoho „seniora", je to data point, ne náhoda.

### 1:1 meetingy a anonymní zpětná vazba

McKinsey výzkum ukazuje, že **vztah s přímým nadřízeným je největší faktor spokojenosti** zaměstnanců – důležitější než plat nebo benefity. Pravidelné 1:1 meetingy vytvářejí prostor pro problémy, které by jinak zůstaly nevyřčené.

Pro eskalaci toxického chování je klíčová **psychologická bezpečnost** – lidé musí věřit, že můžou mluvit bez rizika odvety. Anonymní kanály (360° feedback, engagement surveys) pomáhají tam, kde důvěra chybí.

### Exit interviews – proč lidé odcházejí?

Když někdo odchází, zeptejte se proč. **Skutečně se zeptejte** – ne formální HR dotazník, ale upřímný rozhovor. Pokud více lidí zmiňuje stejné jméno nebo stejný problém, máte vzorec.

Firma, která ignoruje exit interviews, ignoruje nejcennější zpětnou vazbu.

### Klíčová otázka: Proč jsme to nevěděli dřív?

Když toxické chování vyjde najevo, první otázka by měla být: **Proč jsme to nezjistili dřív?** Odpověď obvykle odhalí systémové díry:

- Chyběla pravidelná zpětná vazba
- Neexistovaly nezávislé audity
- Onboarding byl „hoď ho do vody"
- Dokumentace nebyla vyžadována
- Nikdo nesledoval, proč lidé odcházejí

Toxický člověk je symptom. Chybějící procesy jsou příčina.

## Jeden člověk nikdy nestačí

Na závěr jedna jednoduchá pravda: **Jeden člověk není nikdy dost geniální na to, aby nahradil tým.**

Týmová práce vždy vyhraje nad individuálním „hrdinstvím". Sdílené znalosti jsou odolnější než silos jednoho experta. Kultura otevřenosti porazí kulturu strachu.

Pokud ve vaší firmě existuje někdo „nepostradatelný" – je čas to změnit. Ne proto, že ten člověk je špatný (i když možná je). Ale proto, že **nepostradatelnost je riziko**. Pro firmu, pro tým, a nakonec i pro toho „nepostradatelného" samotného.

Protože až jednou odejde – dobrovolně nebo ne – zhroutí se všechno. A to není úspěch. To je selhání.

---

*Tyto scénáře nejsou vymyšlené – dějí se v IT firmách každý den. Poznáváte něco z vlastní zkušenosti?*
