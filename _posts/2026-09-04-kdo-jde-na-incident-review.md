---
layout: post
title: Kdo jde na incident review, když kód napsal agent?
subtitle: Odpovědnost v agentním vývoji – proč se nedá delegovat a jaký záznam ji doloží
excerpt: Kód, který napsal agent, shodil produkci. Na postmortem přijde člověk, který dal merge – ale ten diff jen podepsal, nečetl. Proč git ví, kdo napsal, ale ne kdo rozhodl, proč trailer Co-authored-by nic nedokládá a proč se odpovědnost v agentním vývoji neztrácí, jen odhaluje, že nikdy nebyla zapsaná.
tags: [ai, governance, architecture, software-engineering, agents, opinion]
comments: true
---

> **English summary:** This article asks who is accountable when code written by an autonomous coding agent causes a production incident. It argues that responsibility cannot be delegated to the agent because the agent never decided anything – it only executed – and proposes a three-layer model: responsibility for the outcome (always the organisation), for the decision (task definition, boundaries, acceptance criteria – the layer where responsibility cannot simply be delegated to a tool) and for execution (formerly the developer, now the agent, where responsibility quietly dissolves). Drawing on the "responsibility gap" literature, recent software-engineering research on agentic pull requests, the GitLab 2026 AI Accountability Report, open-source contribution policies and the EU liability framework, it shows that almost every existing provenance mechanism records *who wrote* the code, not *who decided and why*. Its core claim: the primary accountability artefact in agentic development is not a git trailer or an audit log, but a decision record written before the code exists.
>
> Řešíte, jak ve své organizaci nastavit odpovědnost za kód, který píší AI agenti? [Podívejte se na moje služby](https://patriksima.github.io/sluzby/).

---

Představme si běžnou situaci z blízké budoucnosti – nebo u některých týmů už ze současnosti.

V pátek odpoledne padne produkce. Postmortem v pondělí ukáže příčinu: změna v obsluze chybových stavů platební služby, která za určitých okolností tiše polkne výjimku a vrátí úspěch. Commit má jméno vývojáře. Pull request prošel review, měl zelené testy a byl mergnutý ve čtvrtek.

Jenže vývojář ten kód nenapsal. Napsal ho agent – dostal ticket, vytvořil větev, napsal implementaci i testy, doplnil popis pull requestu. Vývojář diff prošel, zdál se rozumný, měl 1 800 řádků a v tom týdnu jich takových viděl dvanáct. Dal approve.

Kdo teď jde na incident review?

Dnes je odpověď jednoduchá: ten, kdo dal merge. Otázka je, jak dlouho ještě bude jednoduchá. A jestli je vůbec správná.

Protože vývojář v našem příběhu neudělal nic, co by porušilo proces. Proces řekl: agent píše, člověk schvaluje. Člověk schválil. Že schválení 1 800 řádků za dvacet minut není review, ale podpis bianko šeku, ví každý, kdo to někdy dělal. Proces to ale nevidí.

A agent? Agent nerozhodl nic. Dostal zadání a provedl ho. Že se u chybového stavu rozhodl pro tiché polknutí výjimky, není rozhodnutí v tom smyslu, v jakém ho zná odpovědnost. Nikdo mu neřekl, jak se má u platební služby k chybám chovat – a on si to vybral tak, jak to statisticky vypadalo nejpravděpodobněji.

Tady vzniká otázka, kterou tento článek zkoumá:

**Kde leží odpovědnost ve vývoji, ve kterém kód píše – a brzy i schvaluje – někdo, kdo ji nemůže nést? A jaký záznam ji vůbec doloží?**

Hned na začátku jedno přiznání: většina tohoto textu není o AI. Je o tom, že jsme odpovědnost za rozhodnutí v softwaru dlouhé roky nikam nezapisovali, protože rozhodnutí a jeho provedení dělal tentýž člověk a stačilo se ho zeptat. Agentní vývoj tuhle konstrukci rozebírá. Odpovědnost neruší – jen ukazuje, že nikdy nebyla zapsaná.

## Definice problému

Když se řekne „odpovědnost za kód", myslíme tím obvykle jednu věc. Ve skutečnosti jsou to nejméně tři, a agentní vývoj je od sebe odtrhává.

**Odpovědnost za výsledek.** Systém běží, nebo neběží. Data unikla, nebo neunikla. Tuhle odpovědnost nese organizace – vůči zákazníkovi, regulátorovi, soudu. Nemění se s tím, kdo kód napsal, a nikdy se nezmění. Ilustruje to i evropská směrnice o odpovědnosti za vadné výrobky, která nově výslovně zahrnuje software – a nijak nerozlišuje, zda vznikl ručně nebo s pomocí AI (Směrnice (EU) 2024/2853). Jde sice jen o jeden konkrétní režim, odpovědnost za škodu způsobenou vadným výrobkem, ne o obecnou odpovědnost za každý incident v produkci. Princip je ale stejný: právo se ptá po výrobci, ne po nástroji.

**Odpovědnost za rozhodnutí.** Co má změna dělat, co dělat nesmí, kde jsou hranice a podle čeho poznáme, že je hotová. Jak se má platební služba chovat, když selže volání do banky. Agent může hledat chyby, navrhovat alternativy, testovat i dělat review – ale tohle je místo, kde odpovědnost nelze jednoduše delegovat na nástroj. A zároveň místo, které se v dnešní praxi téměř nikde nezapisuje. Rozhodnutí bydlí v hlavě seniora, v ústní dohodě na standupu, nebo v promptu, který po dokončení úlohy zmizí.

**Odpovědnost za provedení.** Že kód dělá to, co má, že je čitelný, že neotevírá díru. Tuhle odpovědnost dřív nesl vývojář a byla jasně přiřaditelná: jméno v commitu bylo jméno člověka, který o každém řádku přemýšlel. Dnes ji přebírá agent – a agent ji nést nemůže.

Klíčové je, co se stane s třetí vrstvou.

Neztratí se. Přeteče nahoru. Když provedení dělá někdo, kdo nenese odpovědnost, musí ji unést vrstva rozhodnutí a vrstva výsledku. A vrstva rozhodnutí dnes nemá ani formu, ani vlastníka, ani záznam.

To je celý problém v jedné větě: **odpovědnost za provedení se rozpouští a odpovědnost za rozhodnutí, která ji má nahradit, nikde neexistuje.**

## Co k tomu říká teorie

Otázka, kdo odpovídá za jednání stroje, který se učí, není nová. Andreas Matthias ji v roce 2004 popsal jako *responsibility gap* – mezeru v odpovědnosti. Jeho argument byl jednoduchý: tradiční připsání odpovědnosti předpokládá, že člověk mohl chování stroje předvídat a ovlivnit. U učícího se systému to výrobce ani provozovatel v principu nedokáže. Buď takové stroje nepoužijeme, nebo se smíříme s tím, že za část jejich chování neodpovídá nikdo (Matthias, 2004).

Santoni de Sio a Mecacci o sedmnáct let později ukázali, že těch mezer je víc, a ta nejdůležitější je v *aktivní* odpovědnosti – povinnosti dopředu rozhodnout, aby se věci nepokazily (Santoni de Sio & Mecacci, 2021). Přesně to, co v agentním vývoji nikdo nezapisuje.

Softwarové inženýrství se k tématu dostalo teprve v posledních dvou letech, a dostalo se k němu rychle.

Christoph Treude analyzoval podmínky užití devíti nástrojů pro agentní programování a našel jednu společnou konstrukci: smlouvy **kolabují delegaci do pouhého užití**. Uživatel vlastní výstup a nese za něj plnou odpovědnost bez ohledu na to, kolik autonomních kroků agent udělal, aby ho vytvořil (Treude, 2026). Právně je to čisté. Prakticky to znamená, že celá tíha spočívá na člověku, který ke konci procesu klikl na tlačítko.

Treude zároveň navrhuje, jak z toho ven: přestat uvažovat o odpovědnosti jako o jednom bloku a navázat ji na konkrétní události ve workflow – kdo zadal úlohu, kdo schválil plán, kdo provedl změnu, kdo pustil merge. Odpovědnost se má přiřazovat po fázích, ne až na konci.

Majid Alenezi to pojmenoval nejostřeji. Posun, kterým software prochází, je posun **od autorství k vlastnictví výsledku**. Agenti generují kód, otevírají pull requesty, opravují chyby – ale nepřebírají odpovědnost. Odpovědnost s rostoucí autonomií nemizí, koncentruje se kolem dohledu: kolem toho, kdo stanovil omezení, definoval akceptační kritéria a validoval chování před nasazením (Alenezi, 2026).

To je přesně vrstva rozhodnutí. Literatura ji vidí. Jen ji zatím nikdo nevybavil artefaktem.

## Co se děje v praxi

Teorie by byla akademická, kdyby ji praxe nedoháněla stejnou rychlostí.

GitLab v červnu 2026 publikoval průzkum mezi 1 528 vývojáři a lidmi, kteří o nástrojích rozhodují. Osm z deseti organizací říká, že zavedla AI nástroje rychleji, než stihla vytvořit pravidla pro jejich řízení. Čtyřicet tři procent nedokáže ve vlastní codebase spolehlivě rozlišit, co napsala AI a co člověk. A nejzajímavější číslo: 87 % je přesvědčeno, že do 24 hodin od incidentu dokáže určit, zda k němu přispěl AI kód – ale mezi těmi, kdo incident v posledním roce skutečně zažili, to třetina určit nedokázala (GitLab, 2026).

To není číslo o kvalitě AI kódu. Je to číslo o tom, že organizace neví, kdo v ní rozhoduje.

Empirie z otevřených repozitářů doplňuje druhou půlku obrazu. Analýza více než 450 000 pull requestů od autonomních agentů na GitHubu ukazuje, že zhruba 46 % oprav, které agenti navrhli, bylo zamítnuto (AIDev, 2025; Li et al., 2026). Skoro každá druhá. Lidský review tedy zdaleka není formalita – je to místo, kde se rozhoduje. Jenže se rozhoduje *až po* provedení, s tisíci řádky na stole a bez záznamu toho, co se vlastně mělo stát.

A pak jsou tu open-source projekty, které si problém odžily dřív než firmy.

Linuxové jádro si tuhle otázku vyřešilo dřív než většina firem. Po debatách o příspěvcích generovaných AI nástroji přijalo formální pravidlo: nástroj smí být uveden jako `Assisted-by:`, ale **nesmí přidat `Signed-off-by:`**. Lidský přispěvatel musí kód celý zkontrolovat a přebírá za něj plnou odpovědnost, protože jen člověk může právně certifikovat původ příspěvku (Linux kernel, 2026).

Je to nejčistší formulace celého problému, jakou znám. Nástroj může pomáhat. Rozhodnout a podepsat může jen člověk. A ten podpis má smysl jen tehdy, když člověk ví, co podepisuje.

Daniel Stenberg, autor knihovny curl, k tomu přidal druhou lekci: v lednu 2026 ukončil program odměn za nalezené chyby, protože ho zaplavily AI generované reporty, které nikdo neprověřil. Podíl skutečně potvrzených zranitelností spadl z patnácti procent pod pět (Stenberg, 2026). Problém nebyl v AI. Problém byl v lidech, kteří odevzdali výstup stroje, aniž by za něj převzali odpovědnost.

## Proč git ví, kdo napsal, ale ne kdo rozhodl

Odpověď, ke které se průmysl přirozeně uchýlil, je *provenance*: zaznamenat, co napsal stroj.

Nástroje připojují ke commitům trailer `Co-authored-by`. Vznikají standardy pro kryptografické atestace, protokoly pro záznam řetězce delegace, rozšíření formátu C2PA pro zdrojový kód. Vendoři nabízejí auditní logy agentních sezení.

Je to užitečná práce. A míří vedle.

Za prvé je nespolehlivá. Trailer `Co-authored-by` je pole pro identitu člověka, ne nástroje. Editor ho někdy přidá bez vědomí vývojáře – VS Code měl počátkem roku chybu, která připisovala Copilotu i kód, který Copilot nenapsal, a to i uživatelům s vypnutými AI funkcemi (Zircote, 2026). Trailer navíc zmizí při squash merge a dá se odstranit jedním příkazem.

Za druhé – a to je podstatnější – **zaznamenává špatnou vrstvu.**

Všechny tyto mechanismy odpovídají na otázku „kdo napsal". Auditní log od vendora řekne, že v 14:32 běželo sezení pod tímto účtem a vytvořilo tento diff. Neřekne, co mělo sezení udělat, jaká byla hranice, a podle čeho měl člověk poznat, že výsledek je správný. Enterprise auditní logy velkých poskytovatelů obsahují typicky jen metadata – identifikátory, časy, účty – nikoli obsah zadání.

Jinými slovy: provenance dokládá provedení. Ale odpovědnost za provedení je přesně ta vrstva, která se rozpouští. Dokládáme tedy s velkou přesností to, za co nikdo neodpovídá, a nedokládáme vůbec to, za co odpovídá člověk.

Jedinou výjimkou, kterou jsem v literatuře našel, je protokol pro *human delegation provenance* – kryptografický záznam toho, který člověk autorizoval kterou akci a s jakým rozsahem, přes celý řetězec agentů (Dalugoda, 2026). Ten se skutečně ptá „kdo rozhodl". Odpovídá ale strojově: tokenem, ne záznamem, který by si na incident review někdo přečetl a pochopil.

## Rozhodnutí na papír dřív než kód

Pokud je problém v tom, že vrstva rozhodnutí nemá artefakt, řešení není složité. Je jen nezvyklé: **napsat rozhodnutí dřív, než vznikne kód, a udělat z něj vstup pro agenta i podpis pro člověka.**

Architekti tenhle nástroj znají léta pod zkratkou ADR – *architecture decision record*. Krátký zápis: kontext, rozhodnutí, důsledky. Používá se pro velká rozhodnutí, párkrát do roka, a často se na něj zapomene.

V agentním vývoji se z něj stává něco jiného. Stává se z něj **záznam záměru** ke každé netriviální změně, a jeho role není dokumentační, ale důkazní. Doloží, že člověk rozhodl, co rozhodl, a agent to provedl. Když se něco pokazí, incident review nezačíná u diffu, ale u záznamu: bylo tohle rozhodnutí správné? Bylo úplné? Chybělo v něm chování platební služby při selhání banky?

Z toho plyne několik konkrétních posunů, které bych si ohlídal.

**Záměr před kódem.** Ke každé změně, u které by mě mrzelo, že ji nikdo nečetl, existuje krátký zápis: co má změna dělat, co nesmí, kde končí, a podle čeho poznáme, že je hotová. Agent ho dostane jako vstup. Člověk ho podepíše dřív, než agent začne. Podpis ADR je podpis rozhodnutí. Podpis diffu je podpis provedení – a ten už dnes nic neznamená.

**Instrukce pro agenty jsou architektura.** Soubory typu AGENTS.md, systémové prompty, kontextové instrukce v repozitáři – to není konfigurace. Ne podle nějakého standardu, ale funkčně: je to místo, kde se dnes reálně rozhoduje, jak se agent bude chovat k chybám, k datům, k bezpečnosti. A cokoli, co určuje hranice chování systému, si zaslouží verzování, review a vlastníka stejně jako architektonické rozhodnutí. V našem příběhu by jediná věta v AGENTS.md – „chybové stavy externích služeb nikdy nepolykej tiše" – incident odvrátila.

**Agent má vlastní identitu a minimální práva.** Nikdy nesdílí účet s člověkem. Má krátkodobé credentials a rozsah, který odpovídá zadání. Není to jen bezpečnostní hygiena – je to podmínka toho, aby se dalo říct, kdo co udělal. Společná směrnice šesti kybernetických agentur z května 2026 to formuluje jako požadavek: každý agent nese ověřenou, kryptograficky ukotvenou identitu (CISA et al., 2026).

**Definice hotovo se přesouvá.** Z „funguje a testy jsou zelené" na „splňuje kritéria, která jsem napsal *před* spuštěním". Rozdíl je zásadní. Agent si testy píše sám, a testy, které si napsal sám, dokazují jen to, že si rozuměl. Kritéria napsaná předem dokazují, že rozuměl *mně*.

**Incident review se ptá jinak.** Ne „kdo napsal", ale „kdo rozhodl a na základě čeho". Pokud rozhodnutí existuje a bylo špatné, učíme se o rozhodování. Pokud neexistuje, našli jsme skutečnou příčinu incidentu – a není to agent.

Nic z toho není revoluce. Je to návrat k něčemu, co disciplinované týmy dělaly vždycky, jen implicitně a v hlavách. Agentní vývoj to vynucuje explicitně a na papíře.

## Kde to nestačí

Bylo by nepoctivé tvrdit, že záznam rozhodnutí je univerzální řešení.

**Režie.** Když se zápis vyžaduje ke každému commitu, změní se v rituál a přestane se číst. Hranice musí být praktická: záznam patří ke změnám, u kterých má rozhodnutí obsah. Přejmenování proměnné ho nemá. Chování při selhání platby ho má. Kde přesně hranice leží, si musí najít každý tým – a musí ji pravidelně přehodnocovat, jinak se z ní stane další schvalovací kolo.

**Kvalita rozhodnutí.** Zapsané rozhodnutí může být špatné. Záznam ho neopraví. Opraví jen to, že bude vidět, čí bylo a proč – což je přesně ta věc, kterou incident review potřebuje, aby se organizace něco naučila místo toho, aby hledala viníka.

**Plná autonomie.** Existuje formální argument, že jakmile agenti začnou rozhodovat i o tom, co mají rozhodovat – tedy vznikne zpětná smyčka, ve které agent přepisuje své vlastní zadání – nelze současně zaručit, že každý výsledek půjde přiřadit, že byl předvídatelný a že odpovědnost nezůstane prázdná (Tibebu & Shemtaga, 2026). Z toho plyne praktický závěr: dokud chceme, aby odpovědnost někdo nesl, musí topologie zůstat dopředná. Člověk rozhoduje, agent provádí, člověk ověřuje. Ve chvíli, kdy agent začne rozhodovat o vlastních hranicích, nepřestáváme mít odpovědnost – přestáváme mít možnost ji komukoli připsat.

## Závěr

Vývojář z úvodního příběhu neselhal. Selhal proces, který mu řekl, že podpis diffu je totéž co odpovědnost za rozhodnutí, které v diffu nikde není zapsané.

Matthias připomíná, že mezera v odpovědnosti vzniká všude, kde jednání stroje nemůže nikdo předvídat. Santoni de Sio a Mecacci ukazují, že ta nejdůležitější část odpovědnosti je ta aktivní – povinnost rozhodnout předem. Treude a Alenezi popisují, jak se odpovědnost v softwaru posouvá od autorství k vlastnictví výsledku. Linuxové jádro to shrnulo do jednoho pravidla: stroj smí pomáhat, podepsat může jen člověk.

Všichni se shodnou, že odpovědnost zůstává na člověku. Málokdo říká, jaký záznam to doloží.

Mou osobní úvahou je, že rozhodující veličinou přestává být kvalita kódu a stává se jí **kvalita a dohledatelnost rozhodnutí**. Kód se dá vygenerovat znovu. Rozhodnutí, které nikdo nezapsal, se dá jen zpětně domýšlet – a zpětně domýšlené rozhodnutí je to, čemu se na incident review říká hledání viníka.

Firmy, kde rozhodování bylo vždycky implicitní a bydlelo v hlavách seniorů, to teď zabolí. Ne kvůli AI. Ale protože jim najednou chybí zápis, který nikdy neměly, a dřív to nebylo vidět.

Nemusí to ale bolet dlouho. Tři věci, které se dají udělat v pondělí, bez nového nástroje a bez schvalovacího kola:

1. **K první netriviální změně, kterou tento týden dostane agent, napište záznam záměru.** Pět vět: co má změna dělat, co nesmí, kde končí, podle čeho poznáte, že je hotová, a kdo to rozhodl. Dejte ho agentovi jako vstup a do pull requestu jako odkaz.
2. **Pošlete AGENTS.md (nebo jeho ekvivalent) do review jako architektonickou změnu.** Kdo je vlastník, kdo schvaluje úpravy, a je v něm věta o tom, jak se agent chová k chybám externích služeb?
3. **Do šablony incident review přidejte jednu otázku před „kdo napsal": „kdo rozhodl a kde je to zapsané".** Pokud odpověď neexistuje, máte příčinu incidentu dřív, než otevřete diff.

Otevřená otázka tedy nezní „jak zaznamenat, co napsal agent". To umí git.

Zní:

**Máte dnes někde zapsané, *proč* vypadá váš systém tak, jak vypadá? Kdo rozhodl, jak se má chovat při selhání? A kdyby to v pátek odpoledne spadlo – šli byste na review s diffem, nebo s rozhodnutím?**

Pokud odpověď zní „s diffem", agent to za vás nezjistí. Provede přesně to, co jste nerozhodli.

---

> **Řešíte, jak nastavit odpovědnost za kód, který ve vaší organizaci píší AI agenti?** Pomáhám technickým lídrům a architektům navrhovat governance, která drží krok s agentním vývojem, aniž by ho zastavila. [Podívejte se na moje služby](https://patriksima.github.io/sluzby/) nebo si [rovnou zarezervujte 30minutový hovor](https://calendly.com/patriksima78/30min).

---

## Literatura

- Alenezi, M. (2026). *From Determinism to Delegation: AI-Native Software Engineering and the Evolution of the Agentic Engineer*. arXiv:2606.28791.

- CISA, NSA, ASD, CCCS, NCSC-NZ, NCSC-UK (2026). *Careful Adoption of Agentic AI Services*. Joint guidance, May 2026.

- Dalugoda, A. (2026). *HDP: A Lightweight Cryptographic Protocol for Human Delegation Provenance in Agentic AI Systems*. arXiv:2604.04522.

- Evropský parlament a Rada (2024). *Směrnice (EU) 2024/2853 o odpovědnosti za vadné výrobky*. Úřední věstník EU.

- GitLab (2026). *The 2026 AI Accountability Report*. Průzkum The Harris Poll, 1 528 respondentů, šest zemí.

- Li, H. et al. (2025). *The Rise of AI Teammates in Software Engineering (SE) 3.0: How Autonomous Coding Agents Are Reshaping Software Engineering* (AIDev dataset). arXiv:2507.15003; navazující analýza zamítnutých agentních oprav arXiv:2606.13468.

- Linux kernel community (2026). *Documentation/process/coding-assistants.rst*. Pravidla pro příspěvky vytvořené s pomocí AI nástrojů.

- Matthias, A. (2004). *The responsibility gap: Ascribing responsibility for the actions of learning automata*. **Ethics and Information Technology**, 6(3), 175–183.

- Santoni de Sio, F., & Mecacci, G. (2021). *Four Responsibility Gaps with Artificial Intelligence: Why they Matter and How to Address them*. **Philosophy & Technology**, 34(4), 1057–1084.

- Stenberg, D. (2026). Oznámení o ukončení programu bug bounty projektu curl, leden 2026.

- Tibebu, T., & Shemtaga, S. (2026). *The Accountability Horizon: An Impossibility Theorem for Governing Human-Agent Collectives*. arXiv:2604.07778.

- Treude, C. (2026). *Accountable Agents in Software Engineering: An Analysis of Terms of Service and a Research Roadmap*. arXiv:2605.04532.

- Zircote (2026). *Recording AI Authorship in Provenance You Can Trust*. Blog, červenec 2026.
