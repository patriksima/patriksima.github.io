---
layout: post
title: "Když schválení stojí víc než nástroj"
subtitle: "Jak velké organizace hledají rovnováhu mezi centrálním řízením a autonomií týmů v době AI"
tags: [management, leadership, organizations, strategy, ai, governance]
excerpt: "Zaměstnanec potřebuje levný AI nástroj, ale jeho schválení trvá týdny a projde několika odděleními. Proč u AI cena neříká nic o riziku, proč 'rychlejší schvalování' není totéž co 'méně kontroly' a co se stane, když rozhodovací proces začne stát víc než hodnota rozhodnutí, o němž rozhoduje."
---

> **English summary:** This article analyzes how large organizations balance centralized control against team autonomy in the era of AI. It starts from a hypothetical case - an employee whose request for an inexpensive AI tool gets routed through a multi-week, multi-department approval process - and draws on Coase and Williamson's transaction-cost economics, the principle of subsidiarity, and the empowerment literature. Its core argument: for AI tools, price and risk are decoupled, so the fix is not "less control" but *unbundling* the fast risk/data review (which should scale with risk) from the slow procurement and budget sign-off (which scales with price). It treats decision latency on reversible, low-risk choices as a measurable competitive variable - and argues that the approval process survives not because nobody did the math, but because every checkpoint has an owner with something to lose.
>
> Řešíte, kde ve své organizaci nastavit hranici mezi kontrolou a autonomií? [Podívejte se na moje služby](/sluzby/).

---

Představme si zaměstnance - říkejme mu třeba analytik - který narazí na nový nástroj postavený na umělé inteligenci. Slibuje, že mu ušetří několik hodin týdně rutinní práce. Licence stojí zhruba tolik co lepší večeře pro dva. Analytik nadšeně vyplní žádost. A pak začne čekat.

Žádost putuje na IT, které posuzuje bezpečnost. Pokračuje na nákup, který vyjednává podmínky. Zastaví se u právního oddělení kvůli zpracování osobních údajů. Vrátí se k přímému nadřízenému ke schválení rozpočtu. Po třech týdnech je nástroj schválen. Analytik mezitím dávno vyřešil svůj problém jinak - a o trochu vychladl ve své chuti přicházet s dalšími návrhy.

Organizace přitom navenek deklaruje, že inovace a využívání AI jsou jejími prioritami.

Tady nevzniká příběh o líné byrokracii nebo zlém managementu. A pozor - nevzniká ani příběh o tom, že by se ten nástroj neměl vůbec posuzovat. Bezpečnostní a datová prověrka je u AI nástroje zcela namístě; problém je v tom, že legitimní rychlý krok (kam ten nástroj posílá data?) je svázán do jednoho balíku s týdny procurementu a schvalování rozpočtu navrženými pro rozhodnutí za miliony. Vzniká tak docela přesná manažerská otázka: **proč může schvalovací proces stát víc - v čase, energii i ztracené příležitosti - než samotné rozhodnutí, o němž se rozhoduje, a proč se ta část kontroly, která chrání, vleče stejně dlouho jako ta, která jen brzdí?**

Hned na začátku jedno přiznání: AI zde slouží spíš jako čočka než jako vlastní téma. Zostřuje obecnější problém, který organizace řešily dávno před ní - kde má rozhodnutí padat a kolik kontroly si zaslouží. AI ale dodává dvě věci, které ten starý problém vyhrocují: rychlost, s jakou přicházejí nové nástroje, a něco zákeřnějšího, k čemu se dostaneme - rozpojení ceny a rizika.

## Definice problému

Jádrem napětí je střet dvou veličin, které velké organizace musí současně optimalizovat: **rychlosti rozhodování** a **kontroly nad rozhodováním**.

Čím větší organizace je, tím víc rozhodnutí se v ní každý den děje a tím vyšší je riziko, že některé z nich způsobí škodu - bezpečnostní incident, porušení regulace, neuhlídaný náklad. Přirozenou obrannou reakcí je rozhodování centralizovat: stáhnout je nahoru, standardizovat a podřídit kontrole.

Jenže rychlost a kontrola jdou proti sobě. Každý kontrolní bod, který přidáme, zvyšuje jistotu, že rozhodnutí bude „správné" - a současně zpomaluje okamžik, kdy vůbec padne.

A tady je první věc, kterou většina debat o „kontrole versus rychlosti" přehlíží: **kontrola není jedna věc.** Schvalovací proces obvykle slévá dohromady minimálně dvě různé kontroly s různou logikou. Jedna je kontrola rizika - odvíjí se od toho, jaká data nástroj vidí a kam je posílá. Druhá je kontrola nákladu - odvíjí se od toho, kolik nástroj stojí. U serveru za miliony jdou obě ruku v ruce. U AI nástroje za pár stovek se rozcházejí. Otázka tedy nezní jen „kolik kontroly", ale **kterou kontrolu na co a jak rychle** - a proč ji slučujeme do jednoho schvalovacího kolečka, když patří na dvě různé rychlosti.

## Proč centralizace přirozeně vzniká

Centralizace není manažerský zlozvyk. Je to racionální odpověď na reálná rizika a v řadě situací přináší hmatatelné výhody.

**Bezpečnost a compliance.** Jeden neuhlídaný nástroj, který odešle firemní data na neznámý server, může způsobit škodu o mnoho řádů vyšší než cena tisíce licencí. Centrální posouzení rizika je proto pojistka, ne šikana.

**Vyjednávací síla.** Když nákup sjednává jednu rámcovou smlouvu pro pět tisíc lidí, dosáhne lepší ceny než pět tisíc jednotlivců nakupujících po jednom. Ekonom by řekl, že centralizace internalizuje úspory z rozsahu.

**Governance a přehlednost.** Vedení potřebuje vědět, jaké nástroje firma používá, kde leží data a jaká rizika nese. Bez určité míry centrální evidence se organizace stává nepřehlednou sama sobě.

Na jedné straně tedy stojí pádné důvody rozhodování soustředit. Na straně druhé - a právě tady začíná problém - má každá z těchto výhod svou cenu.

## Když se prostředí změní rychleji než procesy

Centralizace funguje nejlépe ve stabilním prostředí, kde se rozhoduje o věcech podobných tomu, co už firma zná. Schvalovací proces navržený pro nákup serverů za miliony dává smysl právě proto, že taková rozhodnutí jsou velká, vzácná a drahá na chybu.

Nástup AI ale mění samotnou povahu rozhodnutí. Nové nástroje přicházejí v týdenním rytmu, jsou levné, a jejich hodnota se z velké části odvíjí od toho, **jak rychle je člověk začne používat.** Pokud na ně aplikujeme proces navržený pro velká a vzácná rozhodnutí, vznikne nepoměr: schvalujeme nástroj za pár stovek stejně důkladně jako investici za miliony.

A teď ta zákeřná část. U serveru cena zhruba odpovídá riziku - drahá věc je obvykle i důležitá věc. U AI se tahle vazba láme. **Nástroj za pár stovek může nést riziko za miliony**: může odeslat celou zákaznickou databázi na cizí server, natrénovat se na vašem proprietárním kódu nebo založit GDPR průšvih. „Levné" tedy v žádném případě neznamená „nízkoriziikové". Kdo posuzuje AI nástroje podle cenovky, dělá přesně tu chybu, která plodí bezpečnostní incidenty.

A tady se hodí sáhnout po jedné z nejvlivnějších ekonomických teorií dvacátého století.

## Transakční náklady: proč má rozhodování svou režii

Ronald Coase ve své práci *The Nature of the Firm* (1937) položil zdánlivě prostou otázku: proč vůbec existují firmy? Proč si lidé neobstarávají všechno na otevřeném trhu? Jeho odpověď zní, že **používání trhu není zadarmo** - vyhledat dodavatele, vyjednat podmínky a uhlídat smlouvu stojí čas a úsilí. Těmto nákladům říkáme **transakční náklady.** Firma existuje proto, že některé věci umí zařídit levněji vlastní koordinací než přes trh.

Coaseova otázka se ale týká hranice mezi firmou a trhem - proč něco děláme uvnitř organizace místo nákupu venku. Náš problém leží o úroveň hlouběji, uvnitř firmy, a tam přebírá štafetu **Oliver Williamson**, který na Coaseho navázal a za rozpracování transakční ekonomie získal Nobelovu cenu. Williamson ukázal, že i uvnitř organizace nevolíme mezi způsoby řízení náhodně, ale podle **charakteru transakce**: jak je nejistá, jak často se opakuje a jak specifické zdroje váže (Williamson, 1981). Stručně shrnuto: použít na jednoduchou transakci složitou strukturu plodí zbytečné náklady, použít na složitou transakci jednoduchou strukturu plodí přetížení a riziko.

I interní rozhodnutí má totiž svou režii: čas lidí, kteří žádost posuzují, schůzky, čekání, přepínání kontextu. A platí jednoduché pravidlo - koordinace rozhodnutí má smysl jen tehdy, když je její přínos vyšší než její náklad. U nákupu serverů je tato bilance jednoznačně kladná: pečlivé schválení ušetří víc, než stojí. U licence za pár stovek se ale snadno otočí - pokud schválení spotřebuje několik hodin práce napříč čtyřmi odděleními, jeho režie převýší cenu nástroje.

Z toho plyne praktické vodítko - a zároveň past. Vodítko zní: rozhodnutí časté, levné a nízkoriziikové (denní pořízení nástroje) si žádá lehký mechanismus; rozhodnutí vzácné, drahé a riziikové (volba klíčové platformy na deset let) snese těžkou governance. Past spočívá v tom, jak odhadujeme „velikost" transakce. Organizace ji obvykle odhadují podle ceny - a u AI je to chyba. Povahu AI transakce neurčuje cenovka, ale to, k jakým datům nástroj přistupuje a kam je posílá. Potíž tedy nevzniká z toho, že firma má těžké mechanismy, ale z toho, že je používá i tam, kam svou vahou nepatří - a že váhu transakce měří penězi místo rizikem.

Je to důsledek toho, že stejný proces se aplikuje na rozhodnutí různé velikosti - a že „velikost" měříme špatným metrem.

## Subsidiarita: rozhodovat tam, kde je nejvíc informací

Druhý užitečný koncept pochází původně z politické filozofie a evropského práva: **princip subsidiarity.** Říká, že rozhodnutí má padat na nejnižší úrovni, která je schopná ho kompetentně učinit. Vyšší úroveň zasahuje jen tehdy, když to nižší skutečně nezvládne.

Důvod není ideologický, ale informační. Člověk, který práci vykonává, má obvykle nejlepší informace o tom, co potřebuje. Čím dál posuneme rozhodnutí od něj, tím víc kontextu cestou ztratíme - a tím větší je riziko, že rozhodne někdo, kdo problému rozumí méně.

Souvisí s tím pojem **empowerment**, který je užitečné nezploštit. Conger a Kanungo (1988) ho přerámovali z pouhého „delegování pravomocí" na **motivační** konstrukt zakotvený v pocitu vlastní schopnosti (self-efficacy): nejde jen o to dovolit lidem jednat, ale umožnit jim cítit se schopni jednat. Spreitzer (1995) tuto psychologickou stránku operacionalizovala do čtyř dimenzí - smysl, kompetence, sebeurčení a dopad. Vedle této psychologické větve stojí komplementární větev strukturální: zda člověk reálně má informace, zdroje a pravomoc rozhodnout. Pro náš problém jsou důležité obě - empowerment bez reálné možnosti rozhodnout (chybí struktura) i bez pocitu, že na rozhodnutí stačím (chybí motivace), je jen rétorika.

Subsidiarita tedy tlačí rozhodování dolů, blíž k práci, zatímco governance a riziko ho táhnou nahoru. Žádný z těch tlaků není „špatně" - jde o to najít mezi nimi rovnováhu pro konkrétní typ rozhodnutí.

## Diskuse: proč deklarovaná inovativnost často neodpovídá procesům

Vraťme se k naší úvodní situaci. Organizace upřímně deklaruje, že chce být inovativní a využívat AI. A přesto její procesy tomu odporují. Jak to?

Nejde přitom o ojedinělou anomálii. Podle průzkumu McKinsey *The State of AI* dnes používá AI alespoň v jedné oblasti drtivá většina organizací (88 %), ale téměř dvě třetiny ji zatím nezačaly škálovat napříč firmou a jen kolem 39 % hlásí měřitelný dopad na provozní zisk. Ambice tak výrazně předbíhá realitu nasazení. A když oficiální cesta vázne, lidé si najdou neoficiální: Gartner uvádí, že 69 % organizací má podezření nebo přímo důkaz, že jejich zaměstnanci používají zakázané AI nástroje, a předpovídá, že do roku 2030 zažije bezpečnostní nebo compliance incident spojený se „stínovou AI" (*shadow AI*) přes 40 % firem. Pomalé schvalování riziko neodstraní - jen ho přesune mimo dohled.

Odpověď nezní, že vedení lže. Zní, že **strategie a procesy žijí v různých časech.** Strategie se přepíše za jedno odpoledne na workshopu. Procesy - schvalovací toky, role, limity, návyky - se měnily roky a mění se pomalu. Vznikne tak rozpor, kterému se říká **strategy-process misalignment**: deklarovaný záměr a skutečné mechanismy organizace míří jinam.

Tady je ale potřeba jít o krok dál, než kam se obvykle chodí - a tady přiznávám, že běžné vysvětlení „je to vada designu, ne lidí" je útěšné, ale neúplné. Schvalovací proces není počasí. Někdo ho navrhl, někdo ho vykonává a někdo z jeho existence těží. Každý kontrolní bod má svého vlastníka, jehož role, rozpočet nebo pocit bezpečí jsou na ten bod navázané. Kontrolní funkce bývají odměňovány za to, co zachytí nebo zformalizují, ne za to, jak rychle to pustí dál - typicky to platí pro právní review i schvalování nákupu. Proces proto často nepřežívá proto, že si nikdo nespočítal jeho transakční náklady - přežívá proto, že jeho zrušení po někom žádá, aby se vzdal kusu vlastní důležitosti.

To má dva důsledky. Za prvé, hledání viníků mezi jednotlivci míří vedle: analytik, který čeká na licenci, neselhal, a neselhal ani člověk na nákupu, který poctivě vykonává proces tak, jak byl navržen. Za druhé redesign procesu pak není kreslení nového diagramu, ale **vyjednávání o incentivách.** Právě proto bývá těžší, než vypadá, a proto se „inovativní" strategie a pomalé procesy můžou roky míjet, aniž by to kdokoli myslel zle. Dokud problém vnímáme jako vlastnost diagramu, kreslíme diagramy. Jakmile ho začneme vnímat jako vlastnost pobídek, můžeme začít měnit pobídky - a teprve to hne procesem.

## Možná řešení: rozpojit kontrolu, ne ji rušit

Pokud problém leží v designu (a v incentivách, které ho drží na místě), řešením není „méně kontroly" ani „více kontroly", ale **chytřejší rozložení kontroly - a hlavně její rozpojení.**

Úplně první krok je oddělit ty dvě kontroly, které schvalovací proces slévá dohromady: **kontrolu rizika** (patří k tomu, jaká data nástroj vidí) a **kontrolu nákladu** (patří k tomu, kolik stojí). U serveru za miliony jdou ruku v ruce a klidně můžou sdílet jedno pomalé kolečko. U AI nástroje za pár stovek se rozcházejí - a slévat je znamená buď utrácet drahý dohled na levné riziko, nebo, což je horší, mávnout rukou nad levným nástrojem s velkým rizikem. Rychlá datová prověrka („kam to posílá data?") a pomalý procurement („vyjednejme cenu") nemají žádný důvod běžet stejnou rychlostí. Na téhle jediné myšlence stojí většina toho, co následuje.

**Guardrails místo schvalování každého kroku.** Místo aby někdo posuzoval každou jednotlivou žádost, organizace předem vymezí mantinely: schválený seznam prověřených nástrojů, jasná pravidla pro nakládání s daty, definici toho, co se nikdy nesmí. Uvnitř těchto mantinelů se lidé rozhodují sami. Kontrola se přesouvá z jednotlivého rozhodnutí na rámec, ve kterém rozhodnutí probíhá. Ve světě softwaru tomu odpovídá *platform engineering*: centrální tým nepřipravuje schvalování, ale produkt - předpřipravenou, bezpečnou a snadno dostupnou variantu, kterou je jednodušší použít než obejít (Skelton & Pais, 2019). Pro takovou cestu nejmenšího odporu se v platform-engineering praxi vžil termín *golden path* (původně z prostředí Spotify). Mantinel, který je pohodlnější než jeho obcházení, funguje lépe než zákaz.

**Rozpočty týmů a limity pro autonomní rozhodování.** Tým dostane rozpočet - řekněme na nástroje do určité částky měsíčně - o němž rozhoduje sám. Velká rozhodnutí dál procházejí standardním procesem, malá se vyřeší okamžitě. Na téže logice stojí i známý princip „dvou pizz" (Amazon): malý tým s vlastním rozpočtem a jasnými hranicemi rozhoduje rychleji než velká skupina protlačující návrh schvalovacími vrstvami. Hranice se nastaví tam, kde se transakční náklady kontroly začnou vyrovnávat hodnotě rozhodnutí - a „hodnotu" tu měříme rizikem, ne jen cenou.

**Centrální nákup tam, kde dává ekonomický smysl.** Centralizace se neruší - uplatní se selektivně. U nástrojů, kde úspory z rozsahu nebo bezpečnostní rizika jednoznačně převažují, zůstane centrální nákup. U levných a nízkoriziikových nástrojů se pravomoc deleguje. Jde o vědomé rozdělení, ne o plošné pravidlo.

Společným jmenovatelem je posun od kontroly *jednotlivých rozhodnutí* ke kontrole *podmínek*, za nichž lidé rozhodují. Manažer pak netráví čas schvalováním licencí, ale navrhováním a údržbou mantinelů.

## Kde guardrails nestačí

Bylo by nepoctivé tvrdit, že mantinely jsou univerzální lék. Mají své hranice a stojí za to je pojmenovat.

Tam, kde jde o vysoce citlivá nebo regulovaná data - zdravotnictví, finance, osobní údaje pod GDPR - nemusí předem definovaný rámec stačit. Riziko jediného pochybení může být tak vysoké, že individuální posouzení dává smysl i za cenu pomalosti. Podobně u rozhodnutí s velkým reputačním dopadem může být „raději pomalu a jistě" racionální volba, ne projev byrokratické opatrnosti.

A pozor na jednu symetrii, kterou nadšení pro guardrails rádo přehlíží: **mantinely neporazí shadow AI automaticky.** Seznam schválených nástrojů, který nestačí potřebám lidí, požene použití do podzemí úplně stejně jako pomalé schvalování - riziko se jen přesune, pokud schválená cesta není opravdu lepší než ta neoficiální. Není náhoda, že Gartner ve své vlastní zprávě nedoporučuje „guardrails místo schvalování", ale vrstvený přístup: schválené nástroje, jasné politiky, školení a pravidelné audity současně. Guardrails fungují jen tehdy, když jsou pohodlnější než obcházení.

Mantinely navíc nejsou zadarmo. Špatně navržené se samy zvrhnou v novou byrokracii: seznam „schválených nástrojů", který nikdo neudržuje, je nakonec stejnou brzdou jako schvalovací kolečko, jen lépe maskovanou. A čím víc mantinelů přidáme, tím blíž se zase dostáváme k centralizaci, které jsme se chtěli vyhnout. Problém tedy nezmizí - jen se přesune o úroveň výš: kdo, jak často a podle čeho samotné guardrails reviduje? To je trvalá práce, ne jednorázové nastavení.

## Závěr

Vrátím se k otázce z úvodu. Napětí mezi centrálním řízením a autonomií týmů není soubojem dobrého a špatného managementu. Je to **trvalý kompromis** mezi dvěma věcmi, které firma potřebuje současně: jistotou, že se rozhoduje bezpečně a odpovědně, a rychlostí, bez níž deklarovaná inovativnost zůstane jen na papíře.

Williamson nám připomíná, že mechanismus řízení má odpovídat povaze transakce - a Coase, že každé rozhodnutí má svou režii, která nesmí přerůst jeho hodnotu. Subsidiarita dodává, že informace bývají nejbohatší tam, kde se vykonává práce. AI ale není jen další položka, na kterou tato pravidla aplikujeme: rozpojuje cenu a riziko, a tím rozbíjí pohodlný předpoklad, že levné rozhodnutí je i bezpečné rozhodnutí. To je důvod, proč „rychlejší schvalování" a „méně kontroly" nejsou totéž - a proč nejlepší tah obvykle není slevit z kontroly, ale rozpojit ji.

Mou osobní úvahou je, že rozhodující proměnnou se přitom stává **latence rozhodování** - jak dlouho trvá, než vratné, nízkoriziikové rozhodnutí dostane „ano". Na rozdíl od mlhavé „správné rovnováhy" je tahle veličina měřitelná: dá se sledovat čas od žádosti k rozhodnutí, podíl rozhodnutí vyřešených bez eskalace, počet návrhů, které umřely u prvního „ne". Z toho plyne konkrétní, a tedy vyvratitelná sázka: organizace, které latenci u *vratných* rozhodnutí systematicky měří a zkracují, budou v iteraci s AI rychlejší než ty, které ji nechávají růst - zatímco u *nevratných*, vysoce riziikových rozhodnutí na rychlosti nezáleží a pomalost tam má svou cenu. Není to obecné „najděte rovnováhu"; je to tvrzení, které si můžete na vlastních datech ověřit nebo vyvrátit.

Otevřená otázka pro čtenáře proto nezní „kolik hodin práce ten proces spotřebuje" - to je ta levná, viditelná část účtu, a často vyjde směšně nízko (čtyři lidé po hodině je skoro nic). Zní spíš: **kolik dobrých nápadů ve vaší organizaci loni umřelo u prvního „ne"? Jak dlouho čeká vratné, nízkoriziikové rozhodnutí na své „ano"? A kolik práce se reálně děje mimo oficiální cestu, protože ta oficiální je pomalejší než ji obejít?** Ty náklady do tabulky nedostanete - a přesto jsou to ony, ne cena licence, kdo skutečně rozhoduje. A pokud je odpověď nepříjemná: je problém v lidech, kteří proces vykonávají, nebo v tom, jak je proces navržen - a komu jeho současná podoba vyhovuje natolik, že ho nikdo nemění?

---

> **Hledáte, kde ve své organizaci nastavit hranici mezi kontrolou a autonomií?** Pomáhám technickým lídrům a manažerům navrhovat procesy, které chrání firmu, aniž by dusily rychlost. [Podívejte se na moje služby](/sluzby/) nebo si [rovnou zarezervujte 30minutový hovor](https://calendly.com/patriksima78/30min).

---

### Literatura

- Coase, R. H. (1937). The Nature of the Firm. *Economica*, 4(16), 386–405.
- Conger, J. A., & Kanungo, R. N. (1988). The Empowerment Process: Integrating Theory and Practice. *Academy of Management Review*, 13(3), 471–482.
- Gartner (2025). *Gartner Identifies Critical GenAI Blind Spots That CIOs Must Urgently Address* [tisková zpráva, 19. 11. 2025]. Stamford, CT: Gartner, Inc.
- McKinsey & Company (2025). *The State of AI*. QuantumBlack, AI by McKinsey.
- Skelton, M., & Pais, M. (2019). *Team Topologies: Organizing Business and Technology Teams for Fast Flow*. Portland, OR: IT Revolution Press.
- Spreitzer, G. M. (1995). Psychological Empowerment in the Workplace: Dimensions, Measurement, and Validation. *Academy of Management Journal*, 38(5), 1442–1465.
- Williamson, O. E. (1981). The Economics of Organization: The Transaction Cost Approach. *American Journal of Sociology*, 87(3), 548–577.