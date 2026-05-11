---
layout: post
title: "Smeny – Inteligentní plánovač směn"
subtitle: "Case study: jak jsme nahradili Excelovské tabulky strukturovanou .NET aplikací s AI chatem"
tags: [case-study, dotnet, aspire, blazor, azure, mcp, scheduling, ai]
share-title: "Smeny – Case study: plánovač směn s AI chatem | Patrik Šíma"
share-description: "Jak vrstvená .NET 10 aplikace s Azure OpenAI nahradila ruční plánování směn v call centru a přidala AI chat pro dotazy nad daty v přirozeném jazyce."
---

## Přehled

**Smeny** je interní webová aplikace pro automatizované plánování pracovních směn malého týmu (~13 zaměstnanců). Nahrazuje ruční sestavování měsíčních rozvrhů v Excelu a přináší strukturovaný systém pro správu absencí, sledování docházky a AI-asistovanou analýzu dat.

---

## Problém

Tým sestavoval měsíční rozvrhy ručně v tabulkovém procesoru. Proces byl časově náročný a náchylný na chyby, zejména při dodržení souboru složitých pravidel:

- Ranní a odpolední směna mají být v průběhu měsíce rovnoměrně distribuovány mezi všechny zaměstnance.
- Po odpolední směně (končí v 19:00) nesmí automatický plánovač přiřadit ranní směnu (začíná v 7:00) bezprostředně následující pracovní den – nedostatečný odpočinek. Pokud je mezi nimi víkend nebo svátek, omezení neplatí.
- Specifičtí zaměstnanci (nováčci, poloviční úvazky, cizinci) vyžadují manuální plánování.
- Evidence absencí (dovolená, lékař, nemoc, náhradní volno, neplacené volno, ošetřování člena rodiny) musí být integrována do rozvrhu — včetně půldenních variant.
- Penalizace (zákaz příchozí linky) ovlivňují přiřazování.
- Rozvrh musí respektovat české státní svátky.

Neexistoval žádný auditní záznam změn ani přehled o historii rozhodnutí.

---

## Řešení

### Architektura

Aplikace je navržena jako **vrstvená .NET 10 solution** s jasným oddělením odpovědností:

| Projekt | Role |
|---|---|
| `Smeny.Domain` | Doménové entity, enumy, pravidla, bez závislosti na infrastruktuře |
| `Smeny.Infrastructure` | EF Core, SQL Server, auditní pipeline, JSON konvertory |
| `Smeny.Api` | ASP.NET Core Web API – HTTP orchestrace, JWT autentizace, role-based autorizace |
| `Smeny.Spa` | Blazor Server frontend s YARP reverse proxy a Google OAuth |
| `Smeny.McpServer` | Model Context Protocol server pro AI integraci |
| `Smeny.Shared` | Sdílené DTO kontrakty mezi API a SPA |
| `Smeny.Aspire.*` | Orchestrace lokálního a cloudového prostředí |

### Klíčové funkcionality

**Automatický plánovač**
- Generuje měsíční rozvrhy na základě doménových pravidel implementovaných v `Scheduling`.
- Respektuje blokace, penalty, flagy zaměstnanců (`Manual`, `Novice`, `Foreigner`, `PartTime`) a české státní svátky (včetně výpočtu pohyblivých velikonočních svátků).
- Validace přes `ScheduleValidation` vrstvu před persistencí.
- Pravidlo ochranného odpočinku platí i na přechodu měsíců; admin může pravidlo přepsat ručním zápisem.

**Správa absencí s workflow schvalování**
- Zaměstnanci podávají žádosti o absenci (`AbsenceRequest`) s typem (`BlockType`): půldenní i celodenní varianty dovolené, lékař, náhradní volno, nemoc, neplacené volno, OČR.
- Admini schvalují nebo zamítají — `ReviewedBy` (email) a `ReviewedAt` (timestamp) jsou persistovány jako auditní stopa.
- Schválené absence jsou automaticky promítnuty do rozvrhu.

**Uzamykání rozvrhů**
- `ScheduleLock` per zaměstnanec × měsíc – po uzamčení nelze rozvrh pro daného zaměstnance měnit.
- Zaznamenáno kdo (`LockedBy`) a kdy (`LockedAt`) uzamkl.

**AI Chat (admin-only)**
- Administrátor může klást přirozené dotazy v češtině nad daty rozvrhu.
- `AiChatService` sestavuje kontext z MCP serveru a předává ho **Azure OpenAI** přes Aspire client integraci.
- Podporuje synchronní odpovědi (`POST /api/aichat/ask`) i **Server-Sent Events streaming** (`POST /api/aichat/ask-stream`) pro UX v reálném čase.
- MCP server (`Smeny.McpServer`) exponuje 7 read-only nástrojů:

| Nástroj | Popis |
|---|---|
| `admin-summary` | Souhrnný přehled pro administrátora |
| `employees` | Seznam zaměstnanců |
| `employee-schedules` | Rozvrh konkrétního zaměstnance |
| `monthly-overview` | Měsíční přehled směn |
| `search-absences` | Vyhledávání absencí |
| `codebooks` | Číselníky (enumy, typy) |
| `employee-attendance` | Docházkový přehled zaměstnance |

**Auditní log**
- Každá změna entity (`ScheduleSlot`, `Employee`, `Penalty`, …) je zachycena automaticky v `SmenyDbContext` – entita, akce (`AuditAction`), starý/nový stav (JSON), kdo změnil, kdy.
- `AuditLog` je technická entita bez soft-delete (neobsahuje `State`).

**Real-time notifikace**
- SignalR hub (`NotificationsHub`) broadcastuje události (např. `AbsenceRequestsChanged`) do všech připojených klientů.
- SPA okamžitě reflektuje změny bez nutnosti manuálního refreshe.

---

## Technologický stack

```
.NET 10 / ASP.NET Core / Blazor Server
Entity Framework Core + SQL Server
Azure OpenAI přes Aspire client integraci
Model Context Protocol (vlastní implementace)
SignalR (real-time)
YARP Reverse Proxy
JWT Bearer + Google OAuth
OpenTelemetry (traces, metriky, OTLP)
Azure Container Apps (deployment via azd)
.NET Aspire (orchestrace)
xUnit + Testcontainers.MsSql + FluentAssertions (testy)
```

---

## Doménový model (výběr)

```
Employee ──< ScheduleSlot (Morning/Afternoon segment per den)
Employee ──< Schedule (přímý zápis směny bez segmentu)
Employee ──< AbsenceRequest (Pending → Approved/Rejected)
Employee ──< Penalty (IncomingLineBanned, From–To)
Employee ──< ScheduleLock (Year/Month, IsLocked)

ScheduleSlot:
  Segment: TimeSegment (Morning | Afternoon)
  ShiftType: Morning | Afternoon | Common | MorningIncoming | PartTime | Weekend | RookieShift
  BlockType: [celodenní/půldenní] Timeoff | Medical | Toil | SickLeave | UnpaidLeave | ChildCare

AuditLog: EntityType, EntityId, Action, OldValues JSON, NewValues JSON, ChangedBy, ChangedAt
```

Všechny entity dědí z `BaseEntity` (UUIDv7 ID, soft-delete `State`, `CreatedAt`/`UpdatedAt`). `AuditLog` je výjimkou – nemá `State` ani soft-delete. Hard delete pro ostatní entity neexistuje.

---

## Testovací strategie

- **Integrační testy** běží proti reálnému SQL Serveru v Docker kontejneru (`Testcontainers.MsSql`).
- `ApiWebApplicationFactory` / `McpWebApplicationFactory` s override DI služeb.
- `BaseTest` generuje JWT tokeny pro autentizované volání.
- Pokrytí: CRUD endpointy, scheduling validace, MCP kontrakty, AI Chat přístupová práva, docházkový přehled.

---

## Výsledky

| Oblast | Před | Po |
|---|---|---|
| Sestavení měsíčního rozvrhu | ~2 hodiny ručně | Automaticky v sekundách |
| Kontrola pravidel | Manuální, náchylná na chyby | Automatická validace |
| Evidence absencí | Excel poznámky | Strukturovaný workflow se schvalováním |
| Auditní stopa | Žádná | Kompletní, per-entita |
| Analýza dat | Ad-hoc tabulky | AI dotazy v přirozeném jazyce |
| Notifikace změn | Email/ústně | Real-time v aplikaci |

---

## Klíčová rozhodnutí a lessons learned

1. **`ScheduleSlot` s explicitním `TimeSegment`** – k původní entitě `Schedule` přibyla `ScheduleSlot` s polem `Segment` (Morning/Afternoon), což zpřehlednilo logiku plánovače a dotazy nad rozvrhem. Obě entity koexistují: `ScheduleSlot` pokrývá segmentované sloty generované plánovačem, `Schedule` slouží pro přímé zápisy bez segmentu.

2. **MCP jako AI kontextová vrstva** – oddělení AI kontextu do samostatného MCP serveru umožňuje nezávislé cachování, verzování a testování nástrojů bez zásahu do core API. Autentizace probíhá přes `X-Mcp-Api-Key` hlavičku.

3. **Aspire pro orchestraci** – zjednodušilo lokální vývoj (SQL Server kontejner, Azure OpenAI konfigurace) a deployment do Azure Container Apps přes `azd up`. CI/CD lze nakonfigurovat přes `azd pipeline config`.

4. **Soft-delete everywhere (kromě AuditLogu)** – žádná produkční data nelze omylem smazat; archivace je implicitní. `AuditLog` je write-only append záznam bez `State`.

5. **Granularita `BlockType`** – půldenní varianty absencí (MorningTimeoff, AfternoonTimeoff, MorningMedical, …) se ukázaly jako nutnost pro reálný provoz, kde zaměstnanec přijde ráno k lékaři a odpoledne je v práci.
