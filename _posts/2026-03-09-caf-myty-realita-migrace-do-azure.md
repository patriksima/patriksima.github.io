---
layout: post
title: "CAF pro migraci z on-premises do Azure: co funguje, co ne a kde firmy nejčastěji narážejí"
subtitle: "Pohled architekta na Cloud Adoption Framework — silné stránky, reálné limity a nejčastější chyby"
tags: [azure, cloud, architecture, migration, governance, security, caf, well-architected]
---

_Není náhoda, že Cloud Adoption Framework (CAF) nezačíná technologií, ale strategií a plánem. Microsoft jej popisuje jako postup od business cílů přes připravenost prostředí až po dlouhodobé řízení, zabezpečení a provoz, nikoli jako jednorázový „přesun serverů“ ([CAF overview](https://learn.microsoft.com/azure/cloud-adoption-framework/overview#how-does-the-cloud-adoption-framework-work), [Prepare your organization for the cloud](https://learn.microsoft.com/azure/cloud-adoption-framework/plan/prepare-organization-for-cloud)). Pokud se migrace zúží pouze na infrastrukturu, výsledek často nepřinese očekávanou hodnotu. CAF pro takovou situaci představuje silný rámec. Není to však kouzelná hůlka._

## Proč CAF stojí za pozornost

Pokud řešíte migraci z on-premises do Azure, Cloud Adoption Framework je nejlepší strukturovaný rámec, který máte k dispozici. Ne proto, že pochází od Microsoftu, ale proto, že pokrývá **celý životní cyklus transformace**: od strategie přes realizaci migrace až po governance a provozní disciplínu.

To je zásadní rozdíl oproti ad hoc přístupu, kdy tým připraví landing zone, přesune první workloady a teprve následně zjistí, že nemá governance model, cost management ani bezpečnostní baseline.

CAF vás vede k tomu, abyste tyto oblasti řešili **předem** — a právě v tom spočívá jeho největší hodnota.

---

## Kde CAF skutečně pomáhá

### Migrační strategie přes 8Rs

Jedním z nejcennějších prvků CAF je explicitní práce s **migračními strategiemi 8Rs** (Retire, Retain, Rehost, Replatform, Refactor, Rearchitect, Rebuild, Replace). V praxi vidím, že firmy buď bez rozmyslu rehostují vše a následně platí za předimenzované virtuální stroje, nebo se pokusí vše rearchitektovat najednou a projekt nikdy nedokončí.

Správný přístup je **workload-by-workload assessment**: na základě business value, technického dluhu a závislostí rozhodnete, co rehostovat, co refaktorovat a co nahradit SaaS řešením. CAF tento rozhodovací rámec poskytuje, ale vyžaduje lidi, kteří jej umějí aplikovat, nejen přečíst.

### Landing Zones: Start Small vs Enterprise Scale

CAF nabízí dva přístupy k landing zones a volba mezi nimi je architektonicky zásadní:

- **Start Small** — jednodušší topologie, rychlejší start, vhodná pro menší organizace nebo PoC. Riziko: řešení vám přeroste přes hlavu a redesign bude bolestivý.
- **Enterprise Scale (ALZ)** — plnohodnotná hierarchie management groups, hub-spoke nebo Virtual WAN, centralizovaná konektivita a identity. Riziko: over-engineering pro firmu, která má dvacet workloadů.

U Enterprise Scale máte navíc klíčovou volbu: **ALZ accelerator** vs **custom implementace**.

- **ALZ accelerator** je správná volba, když potřebujete rychle dosáhnout osvědčeného baseline a máte standardní enterprise požadavky.
- **Custom implementace** dává smysl, pokud máte atypická regulatorní nebo síťová omezení, která by vedla k rozsáhlému „přepisování“ akcelerátoru.

V praxi nejčastěji vídám tuto chybu: firma zvolí Enterprise Scale, protože řešení „působí robustně“, ale nemá engineering kapacitu na údržbu IaC (Bicep/Terraform), a landing zone se postupně stane neudržovaným monolitem. **Velikost landing zone musí odpovídat provozní zralosti organizace, nikoli ambicím architekta.**

### Governance jako organizační disciplína, ne jen Azure Policy

CAF správně chápe governance jako kombinaci **technických guardrails** (Azure Policy, RBAC, Defender for Cloud) a **organizačních procesů** (RACI, změnové řízení, cost review). Bez obojího to nefunguje.

Důležitý technický detail: Azure Policy compliance evaluation má dvě roviny:
- **Near-real-time** — při vytvoření nebo modifikaci resource se policy vyhodnotí okamžitě.
- **Full compliance scan** — probíhá přibližně jednou za 24 hodin a zachytí drift u existujících zdrojů.

Pokud navrhujete governance, musíte počítat s oběma. Spoléhat se pouze na full scan znamená, že non-compliant resource může existovat celé hodiny, než jej systém zachytí — a v regulovaném prostředí vás to může stát audit finding.

Management groups mají limit 10 000 na tenant a maximální hloubku stromu 6 úrovní. V praxi doporučuji nejvýše 3–4 úrovně — hlubší hierarchie komplikuje policy inheritance, troubleshooting i onboarding nových týmů.

### Vazba na Well-Architected Framework

V mnoha článcích o CAF chybí jedna důležitá souvislost: CAF a **Azure Well-Architected Framework (WAF)** se vzájemně doplňují. CAF řeší *jak migrovat a provozovat*, zatímco WAF řeší *jak navrhovat kvalitní workloady* (reliability, security, cost optimization, operational excellence, performance efficiency).

V praxi to znamená, že CAF vám dá landing zone a governance model, ale kvalita jednotlivých workloadů závisí na tom, zda je navrhujete podle principů WAF. Ignorovat WAF při adopci CAF je jako postavit dálnici a pustit na ni auta bez brzd.

### Bezpečnost a shared responsibility

Přechod do cloudu **nepřesouvá** odpovědnost za data a compliance na Microsoft. Shared responsibility model je jasný — Microsoft odpovídá za infrastrukturu, vy odpovídáte za konfiguraci, identitu, data a aplikační bezpečnost.

To v praxi znamená:
- **Network security groups, private endpoints, encryption at rest/in transit** — vaše odpovědnost.
- **Identity governance (Entra ID, PIM, Conditional Access)** — vaše odpovědnost.
- **Mapování interních kontrol na regulatorní požadavky (GDPR, NIS2)** — vaše odpovědnost.

CAF vám poskytne rámec a doporučení. Mapování na vaši konkrétní regulaci však musíte provést sami — nebo s někým, kdo rozumí jak zabezpečení Azure, tak regulatornímu prostředí.

### FinOps a finanční řízení

Neexistuje žádné magické procento úspor, které by platilo univerzálně. ROI migrace závisí na kvalitě modernizace, provozní disciplíně a FinOps vyspělosti.

Data z [FinOps Foundation](https://data.finops.org/) (2026, 1 192 respondentů, pokrytí $83B+ cloud spend) ukazují obrovský rozptyl ve výsledcích. Firmy, které mají zralý FinOps, šetří. Firmy, které prostě přesunuly workloady bez optimalizace, typicky platí víc než on-prem.

**Doporučení:** Neříkejte managementu „ušetříme 30 %“. Řekněte raději „budeme měřit unit cost per workload a iterativně optimalizovat“. Takové očekávání je poctivější a dlouhodobě udržitelnější.

---

## Anti-patterny, které v CAF programech opakovaně vídám

1. **„Lift-and-shift everything" bez business segmentace**
   - výsledek: cloud bill roste, ale business value ne.

2. **Central platform tým jako úzké hrdlo**
   - pokud každý network peering nebo policy exemption jde přes jeden tým, delivery se zastaví.

3. **Policy-only governance bez operating modelu**
   - technické guardrails bez ownershipu, výjimek a pravidelných review vedou k obcházení pravidel.

4. **Enterprise-scale design bez enterprise provozu**
   - robustní architektura bez robustního provozu je papírově krásná, ale reálně křehká.

5. **„Multi-cloud" jako politické rozhodnutí bez provozního plánu**
   - CAF funguje výborně pro Azure operating model; v multi-cloud scénáři musíte explicitně řešit, co bude jednotné napříč cloudy (identita, tagging, cost model, security baseline) a co zůstane cloud-specifické.

---

## Nevýhody CAF, které je fér přiznat

Pokud chceme CAF propagovat poctivě, musíme otevřeně říct i náklady:

1. **Vyšší organizační overhead na začátku**
   - governance tým, procesy, odpovědnosti a decision model zpočátku zpomalují delivery.

2. **Vysoké nároky na kompetence**
   - bez zkušeností s cloudem, security a governance roste riziko chyb a zpoždění.

3. **Strmá křivka učení ALZ + IaC**
   - jde o robustní přístup, ale vyžaduje engineering disciplínu, která ve firmách často není přirozeně vybudovaná.

4. **Riziko provozních bottlenecků**
   - příliš centralizovaný model brzdí týmy, příliš volný model vytváří shadow IT.

5. **Hybridní přechodové období je složité**
   - kombinace on-premises a cloudu dočasně zvyšuje integrační, bezpečnostní i provozní komplexitu.

To nejsou argumenty proti CAF. Jsou to argumenty pro realistická očekávání, správné pořadí kroků a silné vedení transformace.

---

## Co CAF neřeší (a musíte to vyřešit vy)

CAF je podle Microsoft Learn primárně **strukturovaný framework a guidance** pro rozhodování, nikoli „autopilot“ ([CAF overview](https://learn.microsoft.com/azure/cloud-adoption-framework/overview), [Why use CAF](https://learn.microsoft.com/azure/cloud-adoption-framework/overview#why-use-the-cloud-adoption-framework)). Jinými slovy: pomáhá rozhodovat, ale samotná rozhodnutí i jejich realizace zůstávají na organizaci. V praxi to znamená, že CAF vám typicky **nedodá hotovou odpověď** v těchto oblastech:

1. **Prioritizaci business trade-offů mezi útvary**
   - CAF pomůže strukturovat rozhodnutí, ale konflikt „rychlost vs compliance vs náklady" musí vyřešit váš governance model a leadership.

2. **Kvalitu vstupních dat a CMDB realitu**
   - CAF explicitně pracuje s workload inventory, ownershipem a dependency mapou, ale jejich kvalitu za vás nevygeneruje ([Document cloud adoption plan](https://learn.microsoft.com/azure/cloud-adoption-framework/plan/document-cloud-adoption-plan)).

3. **Aplikační dluh a kvalitu kódu**
   - CAF pomůže s volbou migrační strategie, ale neodstraní sám od sebe monolitický design, slabé integrační kontrakty ani chybějící testovací strategii.

4. **Organizační politiku a rozhodovací disciplínu**
   - CAF dává role, procesy a doporučený operating model, ale jejich dodržování je otázka mandátu, kultury a exekuční disciplíny ([Prepare your organization for cloud](https://learn.microsoft.com/azure/cloud-adoption-framework/plan/prepare-organization-for-cloud)).

5. **Ekonomický model konkrétní firmy**
   - CAF neříká univerzální „správnou cenu"; tu určují vaše unit economics, SLA cíle, rizikový profil a investiční horizont.

6. **Vendor a sourcing strategii mimo Azure**
   - CAF podporuje i multicloud úvahy, ale implementační guidance je primárně na Azure; pro suverenitu, exit strategy a sourcing policy potřebujete vlastní enterprise pravidla nad rámec CAF.

Jinými slovy, CAF výrazně snižuje chaos v adopci cloudu, ale nenahrazuje odpovědnost za rozhodnutí, která jsou specifická pro váš byznys a regulatorní kontext.

---

## CAF vs TOGAF: jak je propojit v reálném programu

Krátká odpověď zní: **doplňují se**. V silných transformačních programech používám TOGAF jako řídicí vrstvu a CAF jako exekuční vrstvu.

Praktické mapování TOGAF ADM na CAF vypadá typicky takto:

1. **Preliminary + A (Architecture Vision)**
   - v TOGAF nastavujete principy, scope a governance model.
   - v CAF paralelně definujete cloud strategy, business outcomes a operating model.

2. **B/C/D (Business, Data/Application, Technology Architecture)**
   - v TOGAF modelujete target state a identifikujete gapy.
   - v CAF z toho vzniká workload segmentation, 8Rs rozhodnutí a roadmapa migrace/modernizace.

3. **E/F (Opportunities & Solutions, Migration Planning)**
   - v TOGAF prioritizujete work packages a tranzice.
   - v CAF navrhujete landing zones, identity/network baseline, governance guardrails a migrační waves.

4. **G/H (Implementation Governance, Architecture Change Management)**
   - TOGAF drží architektonickou konformitu a řízení změn.
   - CAF přidává cloud provozní mechanismy: policy compliance, cost governance, security posture, incident learnings.

Stejně důležitý je vztah **TOGAF Architecture Repository ↔ CAF Landing Zones**:
- Repository drží principy, standardy a schválené architektonické building blocks.
- Landing zones jsou jejich cloudová, provozně vynutitelná implementace (policy, RBAC, networking, subscriptions).

Pokud tyto dvě vrstvy oddělíte, ale nepropojíte, skončíte buď s „krásnou dokumentací“ bez exekuce, nebo s „rychlou exekucí“ bez architektonického řízení.

---

## Jak pracovat se zdroji bez vendor biasu

Můj přístup je jednoduchý: vendor guidance beru jako architektonický vstup, nikoli jako důkaz výsledku.

- CAF/WAF beru jako kvalitní „how-to" pro návrh a provoz v Azure.
- FinOps Foundation a interní metriky beru jako důkaz, jestli to ekonomicky funguje.
- Benchmarky typu „X % úspora" beru jako marketingový signál, dokud je nepotvrdí naše vlastní data.

---

## Co si z toho odnést jako architekt a sponsor transformace

- **Architekt:** CAF funguje tehdy, když rozhodnutí o 8Rs, landing zone a guardrails děláte podle kontextu workloadu, nikoli podle jedné „šablony pro vše“.
- **Delivery leadership:** rychlost migrace bez governance vytváří technický a bezpečnostní dluh, který se vrátí v provozu.
- **Business sponsor:** úspěch měřte přes reliability, bezpečnost, lead time změn a unit economics workloadů — ne přes počet přesunutých serverů.

Pokud bych to měl shrnout jednou větou: **CAF je velmi silný framework pro migrace z on-premises do Azure, ale funguje pouze tehdy, když jej chápete jako transformační program, nikoli jako technický projekt.**

---

> Tento článek je odborný komentář, ne právní poradenství ani regulatorní výklad pro konkrétní instituci. V regulovaných odvětvích je vždy nutné mapovat CAF doporučení na lokální regulatorní interpretaci.
