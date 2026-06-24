# PIS — Podnikové informační systémy
**Okruh:** 3 — Specializace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Proces vytvoření informačního systému.
2. Složení IS, vlastnosti, implementační typy, objektový přístup, vývojové fáze.
3. Model technické infrastruktury informačního systému.
4. Automatizovaný sběr dat, technologie následného zpracování údajů.
5. Podpora projektových činností a podpora v rozhodování prostřednictvím IS.
6. Životní cyklus informačního systému.
7. Podnikové aplikace kategorie ERP, CRM, SCM — základní principy.
8. Softwarové technologie pro realizaci informačních systémů.

---
## Odpovědi v bodech

### 1. Proces vytvoření informačního systému
EN: *IS development process*

IS = soubor lidí, dat, procesů a technologií pro sběr, zpracování a distribuci informací.

Fáze: `Analýza → Návrh → Implementace → Testování → Nasazení → Údržba`

| Metoda | Popis |
|---|---|
| Waterfall | fáze za sebou, nelze se vrátit |
| Iterativní | opakované cykly, postupné zpřesňování |
| Agilní | krátké sprinty, rychlá reakce na změny |

---

### 2. Složení IS, vlastnosti, implementační typy, objektový přístup, vývojové fáze
EN: *IS components, properties, implementation types*

**Složení:** Hardware · Software · Data · Lidé · Procesy

**Vlastnosti:** Integrita · Bezpečnost · Dostupnost · Škálovatelnost EN: *scalability*

**Implementační typy:**
- Vývoj na míru = přesně dle požadavků, drahé.
- Hotové řešení = rychlé, levnější, méně flexibilní.
- Kombinace = hotové + úpravy.

**Objektový přístup:** IS jako soustava objektů komunikujících spolu. Výhoda: znovupoužitelnost.

**Fáze:** `Analýza → Návrh → Implementace → Testování → Nasazení → Údržba`

---

### 3. Model technické infrastruktury IS
EN: *IS technical infrastructure model*

Vrstvy: Klienti → Aplikační vrstva → Datová vrstva → Síťová vrstva

| Model | Popis |
|---|---|
| Jednovrstvý | vše na jednom počítači |
| Dvouvrstvý EN: *client-server* | klient + server |
| Třívrstvý | klient + aplikační server + DB server |
| Cloud | škálovatelná infrastruktura jako služba |

Komponenty: server · DB server · firewall · zálohovací systém · load balancer

---

### 4. Automatizovaný sběr dat, technologie zpracování údajů
EN: *Automated data collection, processing technologies*

**Sběr dat:**
| Technologie | Použití |
|---|---|
| Čárový kód / QR | sklady, obchody |
| RFID | bezkontaktní čip, logistika |
| IoT senzory | teplota, pohyb, průmysl |
| EDI | automatická výměna dat mezi systémy |

**Zpracování:**
- Dávkové EN: *batch* = data zpracována najednou (v noci).
- Real-time = data zpracována ihned.
- ETL = Extract, Transform, Load — přenos dat mezi systémy.
- Data warehouse = centrální úložiště historických dat pro analýzu.
- OLAP = analytické dotazy nad velkými objemy dat.

---

### 5. Podpora projektových činností a rozhodování
EN: *IS support for projects and decision making*

**Projektové řízení:** Ganttův diagram · sledování úkolů · správa zdrojů · reporty.
Nástroje: MS Project, Jira, Trello, SharePoint, Git.

**Podpora rozhodování:**
| Úroveň | Nástroj |
|---|---|
| Operativní | transakční IS |
| Taktické | MIS (Management IS) |
| Strategické | DSS, Business Intelligence |

BI = sbírá data → analyzuje trendy → dashboardy a reporty pro vedení.

---

### 6. Životní cyklus IS
EN: *IS lifecycle*

`Plánování → Analýza → Návrh → Implementace → Testování → Nasazení → Provoz → Vyřazení`

| Model | Klíčová vlastnost |
|---|---|
| Waterfall | fáze striktně za sebou |
| Iterativní | opakované cykly |
| Spirálový | iterativní + analýza rizik |
| Agilní | sprinty 2 týdny, průběžné změny |

---

### 7. ERP, CRM, SCM
EN: *Enterprise applications*

| Systém | Definice | Příklady |
|---|---|---|
| ERP | integrovaný systém pro všechny procesy firmy (finance, HR, výroba) | SAP, MS Dynamics |
| CRM | řízení vztahů se zákazníky | Salesforce, HubSpot |
| SCM | řízení dodavatelského řetězce (suroviny → výroba → zákazník) | SAP SCM |

---

### 8. Softwarové technologie pro realizaci IS
EN: *Software technologies for IS*

| Vrstva | Technologie |
|---|---|
| Backend | Java, C#, Python, PHP |
| Frontend | HTML, CSS, JavaScript, React |
| Databáze | SQL (MySQL, PostgreSQL), NoSQL (MongoDB) |

**Architektura:**
- Monolitická = celý IS jeden celek.
- SOA = sada služeb komunikujících přes síť.
- Mikroslužby = malé nezávislé služby.

**Nasazení:** On-premise · Cloud · Hybridní

**Middleware** = software propojující části IS (RabbitMQ, API gateway).

## Flashcards (ústní trénink)
**Q: Co je IS a z čeho se skládá?**
A: Soubor lidí, dat, procesů a technologií. Složení: hardware, software, data, lidé, procesy.

**Q: Jaké jsou fáze životního cyklu IS?**
A: Plánování → Analýza → Návrh → Implementace → Testování → Nasazení → Provoz → Vyřazení.

**Q: Co je ERP, CRM, SCM?**
A: ERP = všechny procesy firmy. CRM = vztahy se zákazníky. SCM = dodavatelský řetězec.

**Q: Jaký je rozdíl mezi waterfall a agilním vývojem?**
A: Waterfall = fáze striktně za sebou. Agilní = krátké sprinty, průběžné změny.

**Q: Co je Business Intelligence?**
A: Systém který sbírá data, analyzuje trendy a zobrazuje dashboardy pro strategická rozhodnutí.

**Q: Jaké jsou typy nasazení IS?**
A: On-premise (vlastní servery), cloud (poskytovatel), hybridní (kombinace).
