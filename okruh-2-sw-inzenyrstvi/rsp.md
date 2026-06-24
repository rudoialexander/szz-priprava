# ŘSP — Řízení softwarových projektů
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Rozdíl mezi tradičními, agilními a extrémními způsoby řízení projektů.
2. Charakteristika agilních metod a srovnání s tradičními (plánovacími) a formálními přístupy.
3. Způsoby získávání, formalizace a dokumentace zákaznických požadavků.
4. Extrémní programování (XP).
5. Scrum, scrumban.
6. Procesní zlepšování v oblasti vývoje SW.
7. IT management v organizacích, ITIL.

---
## Odpovědi v bodech

### 1. Tradiční vs. agilní vs. extrémní řízení projektů

| | Tradiční | Agilní | Extrémní (XP) |
|---|---|---|---|
| Plánování | předem vše | iterativně | minimální |
| Změny | drahé | vítány | vítány |
| Zákazník | začátek + konec | průběžně | součást týmu |
| Příklad | Waterfall, RUP | Scrum | XP |

---

### 2. Charakteristika agilních metod

**Agile Manifesto — 4 hodnoty:**
```
Jednotlivci a interakce   >  procesy a nástroje
Fungující software        >  obsáhlá dokumentace
Spolupráce se zákazníkem  >  vyjednávání smluv
Reakce na změnu           >  dodržování plánu
```

---

### 3. Získávání, formalizace a dokumentace požadavků

**Získávání:** rozhovory, dotazníky, pozorování, prototypy, workshopy
EN: requirements elicitation

**User story:** "Jako [role] chci [funkcionalita] aby [důvod]"

**MoSCoW prioritizace:**
```
Must have    → kritické
Should have  → důležité
Could have   → hezké mít
Won't have   → ne teď
```

**SRS** = Software Requirements Specification (formální dokument požadavků)

---

### 4. Extrémní programování (XP)

**Klíčové praktiky:**
```
Párové programování  → 2 vývojáři na 1 počítači (driver + navigator)
TDD                  → Red → Green → Refactor
Refaktoring          → průběžné zlepšování kódu
Malé release         → časté dodávání malých verzí
Zákazník na místě    → zákazník součástí týmu
40h týden            → žádné přesčasy
Kontinuální integrace → build + testy po každé změně
```
EN: Extreme Programming / pair programming / TDD

---

### 5. Scrum, Scrumban

**Scrum:**
```
Role:      Product Owner / Scrum Master / Dev Team
Artefakty: Product Backlog / Sprint Backlog / Increment
Ceremonie: Sprint Planning → Daily Standup → Review → Retro
Sprint:    1-4 týdny (typicky 2)
Velocity:  kolik story points tým zvládne za sprint
```

**Scrumban = Scrum + Kanban:**
- WIP limit (max úkolů In Progress)
- Průběžný tok + struktura Scrumu

---

### 6–7. Procesní zlepšování, ITIL

**CMMI — úrovně zralosti:**
```
1. Initial → 2. Managed → 3. Defined → 4. Quantitative → 5. Optimizing
```

**ITIL — správa IT služeb:**
```
Service Desk    → jediný kontaktní bod
Incident Mgmt   → rychlé obnovení po výpadku
Problem Mgmt    → odstranění příčiny opakujících se incidentů
Change Mgmt     → řízení změn bez výpadků

Incident ≠ Problem:
  Incident → konkrétní výpadek (rychle oprav)
  Problem  → příčina opakování (najdi kořen)
```

Životní cyklus ITIL: Strategy → Design → Transition → Operation → Improvement

---

## Flashcards

**Q:** Rozdíl tradiční vs. agilní?
**A:** Tradiční plánuje vše předem, změny drahé. Agilní = iterace, zákazník průběžně, změny vítány.

**Q:** Co je TDD?
**A:** Test Driven Development — nejdřív napíšeš test (selže), pak kód (test projde), pak refaktoruješ.

**Q:** Role v Scrumu?
**A:** Product Owner (co), Scrum Master (jak), Dev Team (kdo).

**Q:** Incident vs. Problem v ITIL?
**A:** Incident = konkrétní výpadek (rychle oprav). Problem = příčina opakování (najdi kořen).

**Q:** Co je MoSCoW?
**A:** Prioritizace požadavků: Must / Should / Could / Won't have.
