---
layout: post
title: "Když schválení stojí víc než nástroj"
subtitle: "Jak velké organizace hledají rovnováhu mezi centrálním řízením a autonomií týmů v době AI"
tags: [management, leadership, organizations, strategy, ai, governance]
excerpt: "Zaměstnanec potřebuje levný AI nástroj, ale jeho schválení trvá týdny a projde několika odděleními. Proč u AI cena neříká nic o riziku, proč rychlejší schvalování není totéž co méně kontroly a co se stane, když rozhodovací proces začne stát víc než hodnota rozhodnutí, o němž rozhoduje."
---

> **English summary:** This article analyzes how large organizations balance centralized control against team autonomy in the era of AI. It starts from a hypothetical case - an employee whose request for an inexpensive AI tool gets routed through a multi-week, multi-department approval process - and draws on Coase and Williamson's transaction-cost economics, the principle of subsidiarity, and the empowerment literature. Its core argument: for AI tools, price and risk are decoupled, so the fix is not "less control" but *unbundling* the fast risk/data review (which should scale with risk) from the slow procurement and budget sign-off (which scales with price). It treats decision latency on reversible, low-risk choices as a measurable competitive variable - and argues that the approval process survives not because nobody did the math, but because every checkpoint has an owner with something to lose.
>
> Řešíte, kde ve své organizaci nastavit hranici mezi kontrolou a autonomií? [Podívejte se na moje služby](/sluzby/).

---

Představme si zaměstnance – říkejme mu třeba analytik – který narazí na nový nástroj postavený na umělé inteligenci. Slibuje, že mu ušetří několik hodin týdně rutinní práce. Licence stojí zhruba tolik co lepší večeře pro dva. Analytik nadšeně vyplní žádost. A pak začne čekat.

Žádost putuje na IT, které posuzuje bezpečnost. Pokračuje na nákup, který vyjednává podmínky. Zastaví se u právního oddělení kvůli zpracování osobních údajů. Vrátí se k přímému nadřízenému kvůli schválení rozpočtu. Po třech týdnech je nástroj schválen.

Analytik mezitím svůj problém dávno vyřešil jinak – a o něco ochladl v chuti přicházet s dalšími návrhy.

Organizace přitom navenek deklaruje, že inovace a využívání AI jsou jejími prioritami.

Tady nevzniká příběh o líné byrokracii nebo špatném managementu. A pozor – nevzniká ani příběh o tom, že by se nástroj neměl vůbec posuzovat. Bezpečnostní a datová prověrka je u AI nástroje zcela namístě.

Problém je jinde: legitimní rychlý krok („kam ten nástroj posílá data?“) je spojen do jednoho balíku s týdny procurementu a schvalování rozpočtu navrženými pro rozhodnutí za miliony.

Vzniká tak přesná manažerská otázka:

**Proč může schvalovací proces stát víc – v čase, energii i ztracených příležitostech – než samotné rozhodnutí, o kterém rozhoduje? A proč se část kontroly, která chrání, často vleče stejně dlouho jako část, která pouze zpomaluje?**

Hned na začátku jedno přiznání: AI zde slouží spíš jako čočka než jako vlastní téma. Zostřuje obecnější problém, který organizace řešily dávno před ní – kde má rozhodnutí padat a kolik kontroly si zaslouží.

AI ale přidává dvě věci, které tento starý problém výrazně zvyšují: rychlost, s jakou přicházejí nové nástroje, a něco ještě důležitějšího – rozpojení ceny a rizika.

## Definice problému

Jádrem napětí je střet dvou veličin, které velké organizace musí současně optimalizovat: **rychlosti rozhodování a kontroly nad rozhodováním.**

Čím větší organizace je, tím více rozhodnutí v ní každý den vzniká a tím vyšší je riziko, že některé z nich způsobí škodu – bezpečnostní incident, porušení regulace nebo neuhlídaný náklad.

Přirozenou reakcí je rozhodování centralizovat: stáhnout ho výše, standardizovat a podřídit kontrole.

Jenže rychlost a kontrola jdou často proti sobě. Každý kontrolní bod, který přidáme, zvyšuje jistotu, že rozhodnutí bude správné – a současně prodlužuje dobu, než vůbec padne.

A tady je první věc, kterou většina debat o „kontrole versus rychlosti“ přehlíží:

**Kontrola není jedna věc.**

Schvalovací proces obvykle slučuje dohromady minimálně dvě různé kontroly s odlišnou logikou.

Jedna je kontrola rizika – odvíjí se od toho, k jakým datům nástroj přistupuje a kam je posílá.

Druhá je kontrola nákladu – odvíjí se od toho, kolik nástroj stojí.

U serveru za miliony jdou obě ruku v ruce. U AI nástroje za pár stovek se ale mohou rozcházet.

Otázka tedy nezní jen „kolik kontroly potřebujeme“, ale především:

**Jakou kontrolu používáme, na co ji používáme a jak rychle má probíhat?**

A proč ji často slučujeme do jednoho schvalovacího procesu, když různé typy rozhodnutí vyžadují různou rychlost?

## Proč centralizace přirozeně vzniká

Centralizace není manažerský zlozvyk. Je to racionální odpověď na reálná rizika a v mnoha situacích přináší jasné výhody.

**Bezpečnost a compliance.**

Jeden neuhlídaný nástroj, který odešle firemní data na neznámý server, může způsobit škodu o mnoho řádů vyšší než cena tisíce licencí. Centrální posouzení rizika je proto pojistka, ne překážka.

**Vyjednávací síla.**

Když nákup sjednává jednu rámcovou smlouvu pro pět tisíc lidí, dosáhne lepší ceny než pět tisíc jednotlivců nakupujících samostatně. Ekonom by řekl, že centralizace využívá úspory z rozsahu.

**Governance a přehlednost.**

Vedení potřebuje vědět, jaké nástroje firma používá, kde leží data a jaká rizika nese. Bez určité míry centrální evidence se organizace stává nepřehlednou sama sobě.

Na jedné straně tedy stojí silné důvody rozhodování soustředit.

Na straně druhé – a právě tady začíná problém – má každá z těchto výhod svou cenu.

## Když se prostředí změní rychleji než procesy

Centralizace funguje nejlépe ve stabilním prostředí, kde se rozhoduje o věcech podobných tomu, co už firma zná.

Schvalovací proces navržený pro nákup serverů za miliony dává smysl právě proto, že taková rozhodnutí jsou velká, vzácná a drahá na chybu.

Nástup AI ale mění samotnou povahu rozhodování.

Nové nástroje přicházejí v týdenním rytmu, jsou levné a jejich hodnota se často odvíjí od toho, **jak rychle je člověk začne používat.**

Pokud na ně aplikujeme proces navržený pro velká a vzácná rozhodnutí, vznikne nepoměr: schvalujeme nástroj za pár stovek stejně důkladně jako investici za miliony.

A teď přichází ta zásadní část.

U serveru cena často přibližně odpovídá riziku – drahá věc je obvykle i strategicky důležitá.

U AI se tato vazba rozpadá.

**Nástroj za pár stovek může nést riziko za miliony.**

Může odeslat celou zákaznickou databázi na cizí server, zpracovávat firemní kód mimo kontrolované prostředí nebo vytvořit problém s GDPR.

„Levné“ tedy v žádném případě neznamená „nízkorizikové“.

Kdo posuzuje AI nástroje pouze podle cenovky, používá metr, který u této technologie přestává fungovat.

A právě tady se hodí sáhnout po jedné z nejvlivnějších ekonomických teorií dvacátého století.

## Transakční náklady: proč má rozhodování svou režii

Ronald Coase ve své práci *The Nature of the Firm* (1937) položil zdánlivě jednoduchou otázku: proč vůbec existují firmy?

Proč si lidé nezajišťují všechno prostřednictvím trhu?

Jeho odpověď zní: protože používání trhu není zadarmo. Vyhledat dodavatele, vyjednat podmínky a uhlídat smlouvu stojí čas a úsilí.

Těmto nákladům říkáme **transakční náklady**.

Firma existuje proto, že některé věci umí koordinovat levněji sama než prostřednictvím trhu.

Coase ale řešil především hranici mezi firmou a trhem. Náš problém je trochu jiný: co se děje uvnitř firmy.

Tady navázal **Oliver Williamson**, který rozpracoval teorii transakčních nákladů a ukázal, že i uvnitř organizace volíme různé způsoby řízení podle povahy rozhodnutí.

Williamson ukázal, že ani uvnitř organizace nevolíme způsob řízení náhodně. Záleží na charakteru rozhodnutí: jak je nejisté, jak často se opakuje a jak důležité zdroje ovlivňuje (Williamson, 1981).

Stručně řečeno: použít na jednoduché rozhodnutí složitý proces vytváří zbytečné náklady. Použít na složité rozhodnutí příliš jednoduchý proces zase vytváří riziko.

I interní rozhodnutí má totiž svou režii: čas lidí, kteří žádost posuzují, schůzky, čekání a přepínání kontextu.

Platí jednoduché pravidlo:

**Koordinace rozhodnutí dává smysl jen tehdy, pokud její přínos převyšuje její náklady.**

U nákupu serverů je tato bilance jednoznačně kladná. Pečlivé schválení může zabránit chybě, která by stála miliony.

U licence za několik stovek se ale může snadno otočit. Pokud schválení spotřebuje několik hodin práce napříč několika odděleními, jeho režie převýší cenu nástroje.

Z toho plyne praktické vodítko – a zároveň určitá past.

Rozhodnutí, která jsou častá, levná a nízkoriziková, si žádají lehký mechanismus. Rozhodnutí, která jsou vzácná, drahá a riziková, snesou těžší governance.

Past spočívá v tom, jak odhadujeme „velikost“ rozhodnutí.

Organizace ji často měří podle ceny.

U AI je to ale chyba.

Povahu AI nástroje neurčuje cenovka, ale především to, k jakým datům přistupuje a kam je posílá.

Problém tedy není v tom, že firma používá důkladné mechanismy. Problém vzniká tehdy, když stejnou míru kontroly aplikuje i tam, kde svou vahou neodpovídá skutečnému riziku.

A že velikost rozhodnutí měří špatným metrem.

## Subsidiarita: rozhodovat tam, kde je nejvíce informací

Druhý užitečný koncept pochází původně z politické filozofie a evropského práva: **princip subsidiarity.**

Říká, že rozhodnutí má padat na nejnižší úrovni, která je schopná ho kompetentně učinit. Vyšší úroveň zasahuje pouze tehdy, když to nižší skutečně nezvládne.

Důvod není ideologický, ale praktický.

Člověk, který práci vykonává, má často nejlepší informace o tom, co potřebuje. Čím dále rozhodnutí posuneme od něj, tím více kontextu cestou ztratíme.

A tím roste riziko, že rozhodne někdo, kdo situaci zná méně.

S tím souvisí pojem **empowerment**, který je dobré nezjednodušit pouze na „delegování pravomocí“.

Conger a Kanungo (1988) ho popsali jako proces, ve kterém nejde jen o to lidem něco dovolit, ale také posílit jejich pocit schopnosti jednat.

Spreitzer (1995) tuto psychologickou stránku rozpracovala do čtyř oblastí: smysl, kompetence, sebeurčení a dopad.

Vedle této psychologické roviny existuje ještě druhá – strukturální. Člověk musí mít nejen pocit, že může rozhodovat, ale také informace, zdroje a skutečnou pravomoc.

Pro náš problém jsou důležité obě.

Empowerment bez reálné možnosti rozhodnout je jen fráze. A pravomoc bez důvěry a schopnosti jednat zase zůstává nevyužitá.

Subsidiarita tedy tlačí rozhodování níže, blíž k samotné práci. Governance a řízení rizik ho naopak táhnou výše.

Ani jeden z těchto tlaků není špatně.

Jde o to najít správnou úroveň pro konkrétní typ rozhodnutí.

## Diskuse: proč deklarovaná inovativnost často neodpovídá procesům

Vraťme se k úvodní situaci.

Organizace upřímně deklaruje, že chce být inovativní a využívat AI. Přesto její vlastní procesy tuto snahu zpomalují.

Jak je to možné?

Nejde o ojedinělou chybu.

Podle průzkumu McKinsey *The State of AI* dnes používá AI alespoň v jedné oblasti většina organizací, ale mnoho z nich ji stále nedokáže rozšířit napříč celou firmou a jen část firem uvádí měřitelný dopad na výsledky. Ambice tak často předbíhá skutečné zavedení.

A když oficiální cesta nefunguje, lidé si hledají vlastní.

Vzniká fenomén **shadow AI** – používání AI nástrojů mimo schválené firemní procesy.

Pomalé schvalování totiž riziko neodstraňuje.

Pouze ho přesouvá mimo dohled.

Odpověď není, že vedení lže.

Spíš platí, že **strategie a procesy žijí v různých časech.**

Strategii lze změnit během jednoho odpoledne. Procesy – schvalovací toky, role, limity a návyky – vznikaly roky a mění se pomalu.

Vzniká tak rozpor mezi tím, co firma říká, že chce, a tím, jak je skutečně nastavena.

Tady je ale potřeba jít o krok dál.

Vysvětlení „je to problém návrhu, ne lidí“ je sice částečně pravdivé, ale neúplné.

Schvalovací proces není počasí.

Někdo ho navrhl, někdo ho vykonává a někdo za něj nese odpovědnost.

Každý kontrolní bod má svého vlastníka. Jeho role, rozpočet nebo pocit bezpečí mohou být s tímto bodem propojené.

Kontrolní funkce bývají přirozeně hodnoceny podle toho, co zachytí a čemu zabrání, ne podle toho, jak rychle rozhodnutí pustí dál.

Proces proto často nepřežívá pouze proto, že by nikdo neviděl jeho náklady.

Přežívá také proto, že jeho změna zasahuje do rolí, odpovědností a zavedených způsobů práce.

To má dva důsledky.

Za prvé: hledání viníků mezi jednotlivci míří vedle. Analytik, který čeká na licenci, neselhal. Stejně tak člověk na nákupu, který poctivě provádí existující proces.

Za druhé: změna procesu není jen překreslení diagramu.

Je to také změna pobídek.

A právě proto bývá těžší, než se na první pohled zdá.

Dokud problém vnímáme jako chybu v diagramu, kreslíme nové diagramy.

Jakmile ho začneme chápat jako otázku nastavení odpovědností a pobídek, můžeme skutečně něco změnit.

## Možná řešení: rozpojit kontrolu, ne ji rušit

Pokud problém spočívá v návrhu procesu a pobídkách, které ho udržují, řešením není „méně kontroly“ ani „více kontroly“.

Řešením je **lépe navržená kontrola.**

První krok je oddělit dvě věci, které schvalovací proces často spojuje:

**kontrolu rizika** a **kontrolu nákladu.**

Kontrola rizika souvisí s tím, jaká data nástroj zpracovává a kam je posílá.

Kontrola nákladu souvisí s tím, kolik nástroj stojí.

U serveru za miliony dávají smysl společně.

U AI nástroje za pár stovek se mohou výrazně lišit.

Rychlá datová prověrka („kam to posílá data?“) a pomalejší procurement („jaké podmínky vyjednáme?“) nemusí běžet stejnou rychlostí.

Na této jednoduché myšlence stojí většina praktických řešení.

**Mantinely místo schvalování každého jednotlivého kroku.**

Místo aby někdo posuzoval každou žádost, organizace předem definuje pravidla:

- schválený seznam nástrojů,
- jasná pravidla pro práci s daty,
- hranice toho, co se nesmí.

Uvnitř těchto mantinelů se lidé rozhodují sami.

Kontrola se přesouvá z jednotlivých rozhodnutí na prostředí, ve kterém rozhodnutí vznikají.

Ve světě technologií se podobný přístup objevuje v podobě platform engineeringu: centrální tým nevytváří překážky, ale připravuje bezpečnou a snadno dostupnou cestu.

Tomu odpovídá i pojem *golden path*.

Nejlepší pravidlo často není to nejpřísnější.

Je to to, které je jednodušší dodržet než obejít.

**Rozpočty týmů a hranice autonomie.**

Tým může získat vlastní rozpočet pro menší nástroje a rozhodovat o něm samostatně.

Velká rozhodnutí zůstávají v centrálním procesu. Malá se řeší okamžitě.

Hranice se nastavuje tam, kde se náklady kontroly začnou vyrovnávat hodnotě samotného rozhodnutí.

A hodnotu zde neurčuje jen cena.

Určuje ji především riziko.

**Centrální nákup tam, kde dává smysl.**

Centralizace se neruší.

Používá se tam, kde přináší skutečnou hodnotu – například díky úsporám z rozsahu nebo vysokým bezpečnostním nárokům.

U levných a nízkorizikových rozhodnutí se pravomoc deleguje.

Nejde o opuštění kontroly.

Jde o to použít správný druh kontroly na správném místě.

Společným jmenovatelem těchto přístupů je posun:

Od kontroly jednotlivých rozhodnutí ke kontrole podmínek, ve kterých lidé rozhodují.

Manažer pak netráví čas schvalováním každé licence.

Navrhuje systém, ve kterém dobrá rozhodnutí vznikají přirozeně.

## Kde guardrails nestačí

Bylo by nepoctivé tvrdit, že mantinely jsou univerzální řešení.

Mají své hranice.

Tam, kde jde o vysoce citlivá nebo regulovaná data – například zdravotnictví, finance nebo osobní údaje – nemusí předem definovaný rámec stačit.

Riziko jediné chyby může být tak vysoké, že individuální posouzení je správná volba i za cenu pomalejšího procesu.

Podobně u rozhodnutí s velkým reputačním dopadem může být opatrnost racionální.

A existuje ještě jedna věc, kterou zastánci mantinelů někdy přehlížejí:

**Guardrails automaticky neporazí shadow AI.**

Seznam schválených nástrojů, který nestačí potřebám lidí, vytvoří stejný problém jako pomalé schvalování.

Lidé si najdou jinou cestu.

Mantinely fungují pouze tehdy, když jsou současně bezpečné i praktické.

Špatně navržené mantinely se mohou samy stát novou byrokracií.

Seznam schválených nástrojů, který nikdo neudržuje, není řešení.

Je to jen jiná forma překážky.

Proto ani guardrails nejsou jednorázové nastavení.

Je to průběžná práce.

Kdo je bude spravovat? Jak často se budou měnit? Podle jakých dat?

To jsou otázky, které rozhodnou, zda se z nich stane nástroj rychlosti, nebo další vrstva kontroly.

## Závěr

Napětí mezi centrálním řízením a autonomií týmů není soubojem dobrého a špatného managementu.

Je to trvalý kompromis mezi dvěma věcmi, které firma potřebuje současně:

bezpečným rozhodováním a rychlostí, bez které inovace zůstane pouze prohlášením.

Coase nám připomíná, že každé rozhodnutí má svou režii.

Williamson ukazuje, že způsob řízení musí odpovídat povaze rozhodnutí.

Subsidiarita připomíná, že informace bývají nejbohatší tam, kde se práce skutečně vykonává.

AI ale přidává nový problém:

Rozpojuje cenu a riziko.

A tím rozbíjí jednoduchý předpoklad, že levné rozhodnutí je automaticky bezpečné.

Proto rychlejší schvalování neznamená méně kontroly.

Často znamená pouze lepší návrh kontroly.

Mou osobní úvahou je, že rozhodující proměnnou se stává **latence rozhodování** – jak dlouho trvá, než vratné a nízkorizikové rozhodnutí dostane své „ano“.

Na rozdíl od obecné fráze o „správné rovnováze“ je tato veličina měřitelná.

Lze sledovat čas od žádosti k rozhodnutí, počet rozhodnutí vyřešených bez eskalace nebo množství návrhů, které skončily u prvního odmítnutí.

Z toho plyne konkrétní tvrzení:

Organizace, které dokážou zkracovat latenci u vratných rozhodnutí, budou při práci s AI rychlejší než ty, které ji nechávají růst.

U nevratných a vysoce rizikových rozhodnutí naopak pomalost může být správnou cenou za bezpečnost.

Otevřená otázka tedy nezní:

„Kolik hodin práce stojí tento proces?“

To je viditelná část účtu.

Důležitější otázka je:

**Kolik dobrých nápadů ve vaší organizaci loni zemřelo u prvního „ne“? Jak dlouho čeká vratné rozhodnutí na své „ano“? A kolik práce se děje mimo oficiální cestu jen proto, že ta oficiální je pomalejší než její obejití?**

Tyto náklady často neuvidíte v žádné tabulce.

Přesto mohou být tím, co ve skutečnosti rozhoduje o schopnosti organizace inovovat.

---

> **Hledáte, kde ve své organizaci nastavit hranici mezi kontrolou a autonomií?** Pomáhám technickým lídrům a manažerům navrhovat procesy, které chrání firmu, aniž by dusily rychlost. [Podívejte se na moje služby](/sluzby/) nebo si [rovnou zarezervujte 30minutový hovor](https://calendly.com/patriksima78/30min).

---

## Literatura

- Coase, R. H. (1937). *The Nature of the Firm*. **Economica**, 4(16), 386–405.

- Conger, J. A., & Kanungo, R. N. (1988). *The Empowerment Process: Integrating Theory and Practice*. **Academy of Management Review**, 13(3), 471–482.

- Gartner (2025). *Gartner Identifies Critical GenAI Blind Spots That CIOs Must Urgently Address*. Stamford, CT: Gartner, Inc.

- McKinsey & Company (2025). *The State of AI*. QuantumBlack, AI by McKinsey.

- Skelton, M., & Pais, M. (2019). *Team Topologies: Organizing Business and Technology Teams for Fast Flow*. Portland, OR: IT Revolution Press.

- Spreitzer, G. M. (1995). *Psychological Empowerment in the Workplace: Dimensions, Measurement, and Validation*. **Academy of Management Journal**, 38(5), 1442–1465.

- Williamson, O. E. (1981). *The Economics of Organization: The Transaction Cost Approach*. **American Journal of Sociology**, 87(3), 548–577.