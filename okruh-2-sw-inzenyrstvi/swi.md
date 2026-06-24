# SWI — Softwarové inženýrství
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Softwarový proces a jeho základní modely.
2. Softwarové profese a týmy.
3. Architektura software.
4. Plánování softwarových projektů, techniky zobrazení plánů.
5. Metody odhadu nákladů na informační systém.
6. Fáze analýzy požadavků na informační systém.
7. Objektová analýza, základní diagramy UML.
8. Modelování procesů a požadavků, katalog požadavků, funkční a nefunkční požadavky.
9. Model jednání — aktéři, případy užití.
10. Konceptuální analýza, modelování dat; integritní omezení (OCL).
11. Metodiky tvorby SW produktů — klasické, agilní.
12. Modelem řízený vývoj; přímé a reverzní inženýrství, okružní jízda (round-trip).
13. Zajištění kvality, softwarové metriky, analýza a řízení rizik, bezpečnost IS, testování.

---
## Odpovědi v bodech

### 1. Softwarový proces a jeho základní modely

```
Waterfall   → lineární, fáze za sebou, změny drahé
Iterativní  → opakované cykly, průběžné výsledky
Agilní      → krátké sprinty, spolupráce se zákazníkem
Spirálový   → iterativní + analýza rizik v každém cyklu
```

---

### 2. Softwarové profese a týmy

| Role | Co dělá |
|---|---|
| Product Owner | definuje požadavky, prioritizuje |
| Scrum Master | odstraňuje překážky, hlídá proces |
| Vývojář | implementuje |
| Tester (QA) | testuje kvalitu |
| Architekt | navrhuje strukturu systému |
| DevOps | nasazení, infrastruktura |

Typy týmů: hierarchický, agilní (samořídící), distribuovaný

---

### 3. Architektura softwaru

```
Vrstvená:     UI → Business logika → Data
MVC:          Model (data) / View (UI) / Controller (logika)
Mikroservisy: malé nezávislé služby přes API
Klient-server: klient → request → server → response
```

---

### 4. Plánování projektů, techniky zobrazení plánů

```
Ganttův diagram → časová osa úkolů (nepřehledné závislosti)
PERT diagram    → závislosti + kritická cesta
WBS             → rozklad projektu na menší části
Milník          → klíčový bod v projektu (okamžik, ne aktivita)
```
EN: Gantt chart / PERT / critical path / milestone / WBS

---

### 5. Metody odhadu nákladů

| Metoda | Základ | Vhodné pro |
|---|---|---|
| Function Points | funkcionalita (vstupy, výstupy, soubory) | velké projekty |
| COCOMO | řádky kódu (Effort = a × KLOC^b) | předem definované projekty |
| Planning Poker | zkušenost týmu, kartičky | agilní projekty |

---

### 6. Analýza požadavků

```
Funkční požadavky    → co systém DĚLÁ ("uživatel se přihlásí")
Nefunkční požadavky → jak to DĚLÁ ("odezva < 2s", "99.9% uptime")
```

Způsoby získání: rozhovory, dotazníky, prototypy, workshopy, pozorování

**Katalog požadavků:**
```
ID   | Typ | Popis                | Priorita
R001 | F   | Přihlášení uživatele | Vysoká
R002 | NF  | Odezva < 2s          | Střední
```

---

### 7. UML diagramy

```
STRUKTURÁLNÍ:
  Class diagram      → třídy + vztahy (asociace, dědičnost)
  Component diagram  → komponenty systému
  Deployment diagram → fyzické nasazení

BEHAVIORÁLNÍ:
  Use case diagram   → aktéři + případy užití
  Sequence diagram   → komunikace objektů v čase
  Activity diagram   → tok činností (flowchart)
  State diagram      → stavy objektu
```

---

### 8. Modelování procesů, požadavků, katalog

```
Activity diagram → tok činností
BPMN             → business procesy
User story:      "Jako [role] chci [funkcionalita] aby [důvod]"
```

---

### 9. Model jednání — aktéři, případy užití

```
Aktér    = kdo interaguje se systémem (člověk nebo jiný systém)
Use case = co aktér se systémem dělá

<<include>> → vždy se zahrne (Koupit VŽDY zahrnuje Zaplatit)
<<extend>>  → volitelné rozšíření
```

Struktura use case: název, aktér, předpoklad, hlavní tok, alternativní tok, výsledek

---

### 10. Konceptuální analýza, modelování dat, OCL

**ER model:** Entita + Atribut + Vztah + Kardinalita (1:1, 1:N, M:N)

**Integritní omezení:** NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK

**OCL:**
```
context Zákazník
inv: self.věk > 18        // invariant — musí platit vždy

pre:  podmínka před operací
post: podmínka po operaci
```
EN: OCL — Object Constraint Language

---

### 11–12. Metodiky SW, MDD

```
Klasické: Waterfall (lineární), RUP (iterativní + struktura)
Agilní:   Scrum (sprinty), XP (párové programování, TDD)

MDD — Model Driven Development:
  PIM → PSM → Kód
  Přímé inženýrství:   model → kód
  Reverzní inženýrství: kód → model
  Okružní jízda:        model ↔ kód (round-trip)
```

---

### 13. Kvalita, metriky, rizika, testování

**Metriky:** LOC, cyklomatická složitost, pokrytí testy, hustota chyb

**Testování:**
```
Jednotkové → 1 funkce/třída
Integrační → spolupráce komponent
Systémové  → celý systém
Akceptační → zákazník ověřuje

Whitebox → tester zná kód
Blackbox → tester nezná kód
Regresní → nová změna nerozbila staré funkce
```

**Řízení rizik:** identifikace → analýza (pravděpodobnost × dopad) → mitigace → monitoring

---

## Flashcards

**Q:** Rozdíl waterfall vs. agilní?
**A:** Waterfall plánuje vše předem, změny drahé. Agilní = krátké iterace, zákazník průběžně vidí výsledky.

**Q:** Co je kritická cesta?
**A:** Nejdelší cesta v PERT diagramu — určuje minimální dobu projektu.

**Q:** Funkční vs. nefunkční požadavky?
**A:** Funkční = co systém dělá. Nefunkční = jak to dělá (výkon, bezpečnost, dostupnost).

**Q:** Co je <<include>> v use case diagramu?
**A:** Povinné zahrnutí jiného use case (vždy se provede).

**Q:** Co je round-trip engineering?
**A:** Synchronizace modelu a kódu oběma směry — změna v kódu = změna v modelu a naopak.

**Q:** Úrovně testování?
**A:** Jednotkové → integrační → systémové → akceptační.
