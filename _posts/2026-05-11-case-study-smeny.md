---
layout: post
title: "RosterIQ – Inteligentní plánovač směn"
subtitle: "Case study: jak jsme nahradili Excelovské tabulky aplikací, která plánuje sama — a ještě se na data ptá česky"
tags: [case-study, ai, scheduling, blazor, azure]
share-title: "RosterIQ – Case study: plánovač směn s AI chatem | Patrik Šíma"
share-description: "Jak jsme nahradili ruční plánování směn v call centru vlastní aplikací, která ušetří hodiny práce měsíčně a umí odpovídat na dotazy v přirozeném jazyce."
---

## Kontext

Tým třinácti lidí v call centru sestavoval každý měsíc rozvrh ručně v Excelu. Vedoucí strávila sestavením rozvrhu přibližně **dvě hodiny**, a i pak se pravidelně přicházelo na chyby — ranní směna po pozdní odpolední, nevyváženost mezi zaměstnanci, přehlédnutá dovolená.

Pravidel bylo hodně: kdo může mít ranní směnu a kdy, kdo vyžaduje zvláštní zacházení (nováčci, zkrácené úvazky), jak se počítají náhradní volna, svátky. Žádný generický nástroj tato specifika nereflektoval.

---

## Co jsme postavili

Aplikaci **RosterIQ** — webový nástroj šitý přímo na potřeby tohoto provozu.

### Automatické plánování

Aplikace zná všechna pravidla provozu a na jejich základě sestaví měsíční rozvrh sama. Vedoucí nemusí hlídat, jestli po pozdní odpolední nemá někdo ráno příliš brzo nastoupit, jestli se směny rovnoměrně střídají, nebo jestli rozvrh respektuje státní svátky. Systém to ohlídá automaticky — a pokud je potřeba výjimka, lze ji ručně přepsat.

### Správa absencí

Zaměstnanci žádají o absenci (dovolená, lékař, nemoc, náhradní volno, OČR) přímo v aplikaci. Vedoucí žádost schválí nebo zamítne, a rozvrh se automaticky přizpůsobí. Každé rozhodnutí je zaznamenáno — kdo schválil a kdy.

### AI chat

Vedoucí může aplikaci klást dotazy v běžné češtině: *„Kdo má příští týden odpolední směnu?"* nebo *„Kolik dní dovolené zbývá Novákovi?"* Systém odpoví okamžitě, bez nutnosti proklikávat filtry nebo exportovat tabulky. Odpovědi se objevují průběžně, jako při psaní — čekání je minimální.

### Přehled a auditní stopa

Každá změna v rozvrhu je zaznamenaná — co se změnilo, kdo to změnil a kdy. Nic se nesmaže, vše je dohledatelné. Měsíc lze uzamknout, aby se do uzavřeného rozvrhu nedělaly dodatečné zásahy.

Změny v aplikaci se projeví všem přihlášeným uživatelům okamžitě, bez nutnosti obnovit stránku.

---

## Co se změnilo

| Oblast | Před | Po |
|---|---|---|
| Sestavení měsíčního rozvrhu | ~2 hodiny ručně | Automaticky za sekundy |
| Kontrola pravidel | Manuální, náchylná na chyby | Automatická |
| Evidence absencí | Poznámky v Excelu | Strukturovaný proces se schvalováním |
| Dohledatelnost změn | Žádná | Kompletní historie |
| Dotazy nad daty | Procházení tabulek | Otázka v přirozeném jazyce |

---

## Jak vývoj probíhal — a co nás překvapilo

Aplikace vznikala od **února 2025** a aktivně se vyvíjí dodnes — celkem přes **15 měsíců a 130+ commitů**. Po první produkční verzi v dubnu 2025 přišlo přibližně deset měsíců ostrého provozu, během nichž jsme sbírali zpětnou vazbu. V únoru 2026 pak nastala druhá, výrazně intenzivnější vlna vývoje.

Na vývoji jsem pracoval s pomocí AI asistenta. Přesto — nebo možná právě proto — bylo zajímavé sledovat, kde asistent pomáhal a kde to byl naopak zdroj zdržení. AI zvládá dobře rutinní kód: CRUD operace, testy, UI komponenty, konfigurace. Jenže klíčové části aplikace — logika plánování, pravidla spravedlivého rozdělení směn — vyžadovaly hodně iterací a manuálního přemýšlení i s asistentem po boku.

**Co bylo skutečně těžké:**

**Spravedlivost při nerovnoměrných dovolených.** Základní pravidlo zní jednoduše: každý má mít za měsíc přibližně stejný počet ranních a odpoledních směn. Jakmile ale někdo čerpá dovolené, musí se výpočet přepočítat jen přes dny, kdy byl k dispozici. Tento algoritmus prošel několika přepisy — a poslední verze s proporcionálními cíli přišla až v únoru 2026, tedy rok po spuštění první verze.

**Pravidlo ochranného odpočinku přes přechod měsíce.** Po pozdní odpolední směně nesmí plánovač přiřadit ranní směnu následující pracovní den. Jednoduché pravidlo — pokud nepřemýšlíte o tom, co se stane posledního dne měsíce. Plánovač musí znát i směny z předchozího měsíce. Drobnost, která si vyžádala samostatný commit.

**Přepis datového modelu uprostřed vývoje.** Původní model ukládal každý den zaměstnance jako jeden záznam. Ukázalo se, že pro rozlišení ranního a odpoledního segmentu to nestačí. Museli jsme přejít na model se dvěma záznamy na den — ranní a odpolední slot. Refaktoring uprostřed běžícího systému je vždy nepříjemný, tady to nebyla výjimka.

**Azure OpenAI autentizace.** Propojení AI modelu s aplikací bylo papírově jednoduché, v praxi jsme strávili neočekávaně mnoho času laděním konfigurace autentizace vůči Azure. Tento typ problému AI asistent pomáhá hledat jen omezeně — logy z cloudu jsou příliš kontextové.

**Co se naopak ukázalo jako dobrý nápad:**

Přidat půldenní varianty absencí — zaměstnanec jde ráno k lékaři a odpoledne je v práci. Zdánlivá drobnost, která se v praxi ukázala jako každodenní potřeba, a bez níž by vedoucí musela i nadále sáhnout po Excelu.

A AI chat nečekaně změnil i to, jak přemýšlíme o dalším rozvoji aplikace. Když vedoucí narazí na odpověď, která není úplně přesná, řekne přesně co chybí — a to se stane konkrétním požadavkem. Průzkum potřeb se zjednodušil: místo vágního *„co by se vám hodilo"* dostáváme *„tady mi chybí tohle"*.

---

## Závěr: jde to s AI samo od sebe?

Ne. Ale jde to rychleji — a jako jednotlivec zvládnete udělat to, na co byste jinak potřebovali tým.

AI asistent ušetřil hodiny na rutinním kódu: testy, CRUD operace, UI komponenty, konfigurace. Díky tomu zbyl čas na to, co šlo s AI jen omezeně — porozumět doméně, vymyslet správný datový model, odladit logiku, která musí fungovat správně v každém hraničním případě.

RosterIQ vznikl za 15 měsíců vedlejšího projektu. Jsou v produkci, denně používané, a stále se rozvíjejí. Ne proto, že by AI vývoj zautomatizovala — ale proto, že snížila náklady na ty části, které automatizovat lze, a uvolnila prostor pro části, které ne.

Pokud řešíte podobný problém — ruční procesy, které by šly zautomatizovat, ale žádný krabicový nástroj přesně nesedí — podívejte se na [RosterIQ](/rosteriq/) nebo rovnou [pojďme si o tom promluvit](https://calendly.com/patriksima78/30min). Třicet minut stačí k tomu, aby bylo jasné, jestli má smysl něco stavět, a co by to obnášelo.
