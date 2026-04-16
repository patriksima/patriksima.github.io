---
layout: post
title: "AI mě dělá rychlejším. A hloupějším."
subtitle: "Jak používání AI nástrojů oslabuje paměť, kritické myšlení a hluboké porozumění kódu — a co s tím"
tags: [ai, programming, critical-thinking, deep-work, opinion]
---

_Posledních pár měsíců mám nepříjemný pocit. Programuju víc než kdy dřív — ale rozumím tomu míň. AI mi generuje kód, já ho vkládám, občas upravím, a jedu dál. Jenže když potom potřebuju vysvětlit, proč ta architektura vypadá tak, jak vypadá, nebo proč jsem zvolil zrovna tenhle přístup — stojím a nevím. A nejsem v tom sám._

## Osobní zkušenost: z řešitele problémů na prostředníka

Začalo to nenápadně. Přestal jsem číst dokumentaci — proč ji číst, když se můžu AI rovnou zeptat? Pak odpadlo i čtení chybových hlášek. Dřív jsem stack trace procházel řádek po řádku a často mě to navedlo k pochopení hlubšího problému. Teď error message prostě zkopíruju do chatu a čekám na odpověď.

Debugování? To samé. Dřív jsem strávil hodiny s debuggerem, krokoval kód, sledoval stavy proměnných. Teď popíšu problém AI a čekám na opravu. Když nefunguje, dám lepší kontext a zeptám se znovu. Je to cyklus rostoucí závislosti.

Nejhorší je ale ztráta hlubokého porozumění. Dřív mě každá chyba něco naučila. Dnes se řešení objeví „magicky" a já se nenaučím nic. Dopamin z okamžité odpovědi nahradil satisfakci z vlastního pochopení.

Nejde jen o mě. Vývojář Namanyay Goel, autor článků, které vidělo přes milion lidí, to [popsal přesně](https://nmn.gl/blog/ai-illiterate-programmers):

> _„Stal jsem se lidským clipboardem — pouhým prostředníkem mezi svým kódem a LLM. Po 12 letech programování jsem se nějak stal horším ve svém vlastním řemesle."_

Goel popsal přesně to, co zažívám i já: přestal číst dokumentaci, přestal debugovat, přestal se ptát, _proč_ věci fungují. A když jednoho dne Cursor spadl společně s ChatGPT, zíral na terminál a nevěděl, co s chybovou hláškou od AWS.

## Co říká věda: kognitivní offloading a digitální amnézie

Tohle není jen pocit — je to dobře zdokumentovaný kognitivní fenomén.

### Google efekt (digitální amnézie)

V roce 2011 psycholožka **Betsy Sparrow** (Columbia University) spolu s kolegy z Harvardu a University of Wisconsin-Madison publikovala studii, která popsala tzv. [Google efekt](https://en.wikipedia.org/wiki/Google_effect): lidé si hůř zapamatují informace, o kterých věří, že je snadno najdou online. Místo toho si pamatují, _kde_ informaci najít, ale ne informaci samotnou.

Důležitější je ale **mechanismus**, který za tím stojí — **kognitivní offloading**: přenášení kognitivní zátěže na externí nástroj. Mozek se doslova „rozhodne", že si informaci nemusí zapamatovat, protože je dostupná jinde. A právě to AI nástroje posilují — nejsou jen úložištěm informací, ale aktivně generují odpovědi, čímž eliminují i ten krok hledání.

Meta-analýza z roku 2024 (Gong a Yang, 35 studií) potvrdila, že časté vyhledávání na internetu je spojeno se změnami ve zpracování a zapamatování informací. Součástí analyzovaných studií byly i experimenty s fMRI, které ukázaly sníženou aktivaci mozku při vybavování informací původně nalezených online, a to v oblastech spojených s hlubším kognitivním zpracováním.

### AI a kritické myšlení: studie Microsoft Research

V roce 2025 tým z Microsoft Research (včetně výzkumníků z Cambridge) publikoval studii **„The Impact of Generative AI on Critical Thinking"** na konferenci CHI 2025. Dotazovali 319 knowledge workerů, kteří sdíleli 936 příkladů používání GenAI v práci.

Klíčová zjištění:

- **Vyšší důvěra v AI = méně kritického myšlení.** Čím víc člověk věří, že AI dá správnou odpověď, tím méně ověřuje a přemýšlí.
- **Vyšší sebedůvěra ve vlastní schopnosti = více kritického myšlení.** Lidé, kteří si věří v dané oblasti, AI výstupy víc kontrolují.
- **AI mění _povahu_ kritického myšlení** — posouvá ho směrem k verifikaci výstupů a integraci odpovědí, ale oslabuje vlastní generování a hlubší analýzu problémů.

> Lee, H.-P. et al. (2025). _The Impact of Generative AI on Critical Thinking._ CHI '25, ACM. [doi:10.1145/3706598.3713778](https://doi.org/10.1145/3706598.3713778)

Jinými slovy: AI nás posouvá z role _myslitelů_ do role _recenzentů_. A to je zásadní rozdíl. Recenzování cizího textu vyžaduje méně kognitivního úsilí než vlastní tvorba řešení od nuly.

## METR studie: AI dělá zkušené vývojáře pomalejšími

Možná nejpřekvapivější výzkum přišel v červenci 2025 od neziskové organizace **METR** (Model Evaluation & Threat Research). Provedli randomizovanou kontrolovanou studii se **16 zkušenými vývojáři** velkých open-source projektů (průměrně 22 000+ hvězdiček, 1M+ řádků kódu).

Vývojáři dostali 246 reálných úkolů (bug fixy, features, refaktoring) a náhodně jim bylo přiřazeno, zda mohou používat AI (Cursor Pro s Claude 3.5/3.7 Sonnet) nebo ne.

**Výsledek: s AI byli o 19 % pomalejší.**

A to nejzajímavější? **Vývojáři si mysleli, že jsou s AI o 24 % rychlejší.** I po dokončení studie, kdy jim data ukázala zpomalení, stále subjektivně vnímali AI jako zrychlení o 20 %.

Je férové říct, že 16 vývojářů je malý vzorek a výsledky nemusí platit univerzálně. Ale právě ta propast mezi subjektivním vnímáním a měřitelnou realitou je alarmující bez ohledu na velikost studie.

> METR (2025). _Measuring the Impact of Early 2025 AI on Experienced Open-Source Developer Productivity._ [metr.org](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/), [arXiv:2507.09089](https://arxiv.org/abs/2507.09089)

Studie identifikovala několik faktorů zpomalení: čas strávený formulováním promptů, kontrolou AI výstupů, opravami chyb v generovaném kódu a především **ztrátou kontextu**, ke které dochází při přepínání mezi vlastním přemýšlením a interakcí s AI.

Ale nejde jen o rychlost. Jde o samotnou schopnost myslet.

## Paul Graham: „Psaní je myšlení"

V říjnu 2024 napsal Paul Graham esej [„Writes and Write-Nots"](https://www.paulgraham.com/writes.html), ve které varuje před rozdělením společnosti na ty, kdo umí psát (a tedy myslet), a ty, kdo neumí. Klíčový argument:

> _„Psaní je myšlení. Existuje druh myšlení, které lze provádět pouze psaním."_

Graham cituje informatika **Leslieho Lamporta**:

> _„Pokud přemýšlíte bez psaní, jen si myslíte, že přemýšlíte."_

A přidává analogii s fyzickou silou:

> _„V předindustriální době většinu lidí jejich práce udržovala silnými. Dnes, pokud chcete být silní, musíte cvičit. Takže silní lidé stále existují, ale jen ti, kteří se pro to rozhodnou. S psaním to bude stejné. Chytří lidé budou stále existovat, ale jen ti, kteří se pro to rozhodnou."_

Tato analogie přesně sedí na programování s AI. Dřív nás programování nutilo myslet, debugovat, navrhovat, chápat. Teď tuto „kognitivní námahu" můžeme delegovat. A jako u fyzické síly: kdo přestane cvičit, oslabne.

## Co to znamená pro programátory

Všechny výzkumy ukazují stejným směrem: čím víc delegujeme myšlení na AI, tím méně se učíme, méně si pamatujeme a méně kriticky přemýšlíme. A nejhorší je, že si toho ani nevšimneme.

Juniorní vývojáři, se kterými mluvím, umí rychle dodat kód. Ale když se zeptám, _proč_ to funguje takhle a ne jinak, nebo jaké jsou edge cases, je ticho. To není jejich chyba. Je to důsledek toho, že nikdy nemuseli s problémem skutečně zápasit.

A nejde jen o juniory. Sám si přestávám pamatovat implementační detaily vlastních projektů, protože jsem je reálně nestavěl ručně. Když se kolega zeptá, jak přesně něco funguje, musím jít do kódu. Nevím to z hlavy. A to mě zneklidňuje víc, než bych čekal — protože v kontrastu: u kódu, který jsem nechal vygenerovat, si nepamatuju nic. Ale když si na chybu sáhnu sám, projdu debugger, přečtu stack trace, prokouším se logikou — ta znalost zůstane.

## Co s tím dělám

Nejde o to přestat AI používat, ten vlak už jede. Ale jde o to **vědomě si zachovat schopnost hluboce přemýšlet**. Pár věcí, které mi pomáhají:

### 1. „No-AI dny"

Jednou týdně programuju bez AI. Čtu chybové hlášky. Používám debugger. Píšu kód od nuly. Je to pomalejší a frustrující, ale cítím silnější spojení s kódem a větší porozumění tomu, co dělám. Goel, kterého jsem zmiňoval výše, tohle praktikuje taky a [otevřeně přiznává](https://nmn.gl/blog/ai-illiterate-programmers), že „to stojí za prd, ale funguje to."

### 2. Vývojářský deník

Před každým úkolem si zapíšu, co chci udělat a proč. Po dokončení, co fungovalo a co ne. Nutí mě to formulovat myšlenky vlastními slovy — a právě to je ten druh myšlení, který se při práci s AI ztrácí. Inspirace přišla z [článku na Stack Overflow blogu](https://stackoverflow.blog/2024/12/18/you-should-keep-a-developer-s-journal/), který doporučuje právě tenhle přístup jako nástroj hlubšího učení.

### 3. AI jako sparring partner, ne jako autor

Když AI použiju, snažím se ho používat jako diskusního partnera: „Jaké jsou nevýhody tohoto přístupu? Co by se rozbilo, kdybych to udělal jinak?" Místo „napiš mi řešení" se ptám „jaké jsou trade-offs?" Tím si udržuju vlastní úsudek a nutím se přemýšlet. Hodně mi pomáhá i práce v plánovacím módu: nechám si navrhnout řešení, ale aktivně ho rozebírám. Proč takhle a ne jinak? Tou diskuzí se dostanu k pochopení problému mnohem hlouběji, než kdybych jen přijal první výstup.

### 4. Čtení zdrojového kódu

Pravidelně čtu cizí zdrojový kód — open-source projekty, pull requesty kolegů. Je to ekvivalent čtení knih pro spisovatele. Žádná AI to za mě neudělá a právě tam se skrývá to hluboké porozumění vzorcům, architektuře a řemeslu.

## Závěr

Nejsme tak produktivnější, jak si myslíme. Ale závislejší jsme určitě.

Každý problém, který necháme AI vyřešit za nás, je příležitost k učení, kterou jsme promarnili. Optimalizujeme na dnešní commit za cenu zítřejší schopnosti.

AI je neuvěřitelně silný nástroj. Ale nástroj, který používáte bez porozumění, vás nakonec ovládne. Budoucnost nepatří těm, kdo umí AI používat. Patří těm, kdo umí myslet i bez něj.

---

### Zdroje

- Sparrow, B., Liu, J., & Wegner, D. M. (2011). _Google Effects on Memory: Cognitive Consequences of Having Information at Our Fingertips._ Science, 333(6043), 776–778.
- Gong, Y., & Yang, D. (2024). _Meta-analysis of the Google effect on memory._ Memory & Cognition. (35 studií, zahrnuje fMRI experimenty)
- Lee, H.-P. et al. (2025). _The Impact of Generative AI on Critical Thinking._ CHI '25, ACM. [doi:10.1145/3706598.3713778](https://doi.org/10.1145/3706598.3713778)
- METR (2025). _Measuring the Impact of Early 2025 AI on Experienced Open-Source Developer Productivity._ [arXiv:2507.09089](https://arxiv.org/abs/2507.09089)
- Graham, P. (2024). [_Writes and Write-Nots._](https://www.paulgraham.com/writes.html)
- Goel, N. (2025). [_We're Creating a Generation of AI-Illiterate Programmers._](https://nmn.gl/blog/ai-illiterate-programmers)
- Goel, N. (2025). [_AI and Learning._](https://nmn.gl/blog/ai-and-learning)
