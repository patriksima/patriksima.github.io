---
layout: post
title: "CAF pro migraci on-prem do Azure: praktický rámec, ne jen technický projekt"
subtitle: "Proč je Cloud Adoption Framework silný pro architekty a management — a kde má reálné limity"
tags: [azure, cloud, architecture, migration, governance, security, management]
---

_CAF je podle mě jeden z nejlepších rámců pro enterprise migraci do cloudu. Právě proto má smysl mluvit i o jeho ceně: komplexitě, nárocích na lidi a organizační disciplíně._

Pokud řešíte migraci on-prem do Azure, největší chyba je dívat se na ni jen jako na technický přesun serverů. Azure Cloud Adoption Framework (CAF) je cenný právě tím, že pokrývá **celý transformační cyklus**: strategii, plán, landing zones, governance, bezpečnost, provoz i optimalizaci.

Pro cílovku architekt + management je to zásadní: rozhodujete totiž o změně operating modelu firmy, ne o jednom infrastrukturním projektu. A pro HR/headhuntery je to zároveň dobrý signál, jak vypadá profil seniorních rolí, které umí techniku i byznysový kontext.

---

## Co CAF řeší dobře v praxi

### 1) Pokrývá celý transformační cyklus

CAF není jen dokumentace k migraci serverů. Pokrývá strategii, plán, připravenost prostředí, adopci i provozní disciplínu (govern/secure/manage).

**Praktický dopad:** Dává společný rámec pro IT i business a snižuje riziko, že se migrace zredukuje na izolovaný infrastrukturní projekt.

Zdroj: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/

### 2) Řeší migrační realitu, ne jen cílový stav

U on-prem → Azure je klíčové plánování migračních vln, závislostí, rollback scénářů, split provozu a připravenosti lidí. CAF to explicitně adresuje.

**Praktický dopad:** Lepší kontrola rizik při cutoveru a menší tlak na ad hoc rozhodování během migrace.

Zdroj: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/migrate/plan-migration

### 3) Landing zones dává jako standardizovanou cílovou architekturu

CAF pracuje s landing zones jako s kombinací platformních i aplikačních vzorů včetně governance.

**Praktický dopad:** Konzistentní škálování a menší pravděpodobnost, že v cloudu rychle vznikne nový legacy.

Zdroj: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/

### 4) Governance chápe jako organizační disciplínu

Nejde jen o technické policy. Jde o role, odpovědnosti, rozhodovací model a dlouhodobou provozní disciplínu.

**Praktický dopad:** Bez governance týmu a jasného RACI se cloud governance typicky rozpadá mezi přeregulovanost a chaos.

Zdroj: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/govern/build-cloud-governance-team

### 5) Bezpečnost a compliance staví na shared responsibility

Přechod do cloudu neznamená, že právní a provozní odpovědnost automaticky přebírá poskytovatel. Část zodpovědnosti zůstává na zákazníkovi.

**Praktický dopad:** Nutnost mapovat interní kontroly, procesy a odpovědnosti na požadavky regulace (např. GDPR).

Zdroje:
- https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility
- https://learn.microsoft.com/en-us/compliance/regulatory/gdpr

### 6) Dává konkrétní provozní mantinely pro scale

Pro enterprise provoz jsou důležité i technické parametry governance vrstvy:

- Microsoft uvádí, že Azure Policy compliance evaluace běží typicky v intervalu cca 24 hodin.
- Management groups mají limity (až 10 000 skupin na tenant, hloubka až 6).

**Praktický dopad:** Hierarchii management groups a policy inheritance je vhodné navrhnout dopředu, protože pozdní redesign bývá nákladný.

Zdroje:
- https://learn.microsoft.com/en-us/azure/governance/policy/overview
- https://learn.microsoft.com/en-us/azure/governance/management-groups/overview

### 7) Vyžaduje aktivní leadership managementu

CAF funguje jako transformační program, ne jako izolovaná iniciativa architektů.

**Praktický dopad:** Pokud leadership nedrží priority, mandáty a rozpočtová pravidla, migrace obvykle narazí na organizační limity.

Zdroj: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/

### 8) Finanční přínosy jsou kontextové, ne univerzální

Neexistuje jedno číslo, které by spolehlivě popsalo ROI migrace napříč firmami. Výsledek závisí na kvalitě modernizace, provozní disciplíně a FinOps vyspělosti.

**Praktický dopad:** Je rozumnější řídit průběžné metriky a byznys case iterativně, než slibovat fixní procenta úspor.

Nezávislý kontext:
- FinOps Foundation dataset 2026: 1 192 respondentů, pokrytí $83B+ cloud spend.
- Zdroj: https://data.finops.org/

---

## Nevýhody CAF, které je fér přiznat

Pokud chceme CAF propagovat poctivě, musíme otevřeně říct i náklady:

1. **Vyšší organizační overhead na začátku**
   - governance tým, procesy, odpovědnosti a decision model zpočátku zpomalují delivery.

2. **Vysoké nároky na kompetence**
   - bez zkušeností s cloudem, security a governance roste riziko chyb a zpoždění.

3. **Strmá křivka učení ALZ + IaC**
   - robustní přístup, ale potřebuje engineering disciplínu, která ve firmách často není „out of the box“.

4. **Riziko provozních bottlenecků**
   - příliš centralizovaný model brzdí týmy, příliš volný model vytváří shadow IT.

5. **Hybridní přechodové období je složité**
   - on-prem + cloud dočasně zvyšují integrační, bezpečnostní i provozní komplexitu.

Tohle nejsou argumenty proti CAF. To jsou argumenty pro realistické očekávání, správné sequencing a silné vedení transformace.

---

## CAF vs TOGAF: v souladu, nebo konkurence?

Krátká odpověď: **doplňují se**.

1. **Účel rámce**
   - TOGAF je vendor-neutrální enterprise architektonický rámec.
   - CAF je praktický rámec pro cloud adopci a exekuci konkrétně na Azure.

2. **Typ výstupu**
   - TOGAF dává metodu řízení architektury (proces, artefakty, governance).
   - CAF dává implementační cestu (landing zones, migrace, govern/secure/manage).

3. **Granularita**
   - TOGAF je silný na úrovni enterprise architecture.
   - CAF jde víc do provozních detailů cloud transformace.

4. **Governance**
   - TOGAF pomáhá nastavit rozhodovací model a architektonické řízení.
   - CAF přidává cloud-native guardrails a operating model pro Azure.

5. **Role v programu migrace**
   - TOGAF: „jak řídit architekturu napříč firmou".
   - CAF: „jak to bezpečně a provozně zvládnout v Azure".

6. **Praktické doporučení**
   - V enterprise funguje dobře kombinace: TOGAF jako governance/meta-rámec, CAF jako exekuční blueprint pro cloud.

Pro management je to důležité: nejde o volbu „TOGAF nebo CAF", ale o správné rozdělení rolí mezi strategické řízení architektury a cloudovou exekuci.

---

## Co je „Microsoft claim“ a co nezávislá data

Aby byl text transparentní:

- **Microsoft claims:** rozsah CAF, doporučené postupy migrace, governance role, policy evaluace, limity management groups, shared responsibility model.
- **Nezávislá data:** FinOps Foundation dataset (metodika a velikost vzorku).
- **Co nepřehánět:** univerzální benchmark „CAF přinese X %“ napříč firmami a obory.

---

## Co si z toho má odnést architekt, manager i HR

- **Architekt:** CAF je dobrý rámec, protože spojuje techniku s operating modelem.
- **Manager:** úspěch migrace není jen o platformě, ale hlavně o people/governance/finance disciplíně.
- **HR/Headhunter:** nejcennější profily jsou lidé, kteří umí překlenout architekturu, bezpečnost, governance a byznysovou exekuci.

Pokud bych to měl shrnout jednou větou: **CAF je velmi silný framework pro migrace z on-prem do Azure, ale funguje jen tehdy, když ho berete jako transformační program, ne jako technický projekt.**

---

> Tento článek je odborný komentář, ne právní poradenství ani regulatorní výklad pro konkrétní instituci. V regulovaných odvětvích je vždy nutné mapovat CAF doporučení na lokální regulatorní interpretaci.
