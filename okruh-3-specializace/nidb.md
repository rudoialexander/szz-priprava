# NIDB — Návrh a implementace databázových systémů
**Okruh:** 3 — Specializace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`
> Pozn.: navazuje na DB (okruh 2). Zde důraz na normalizaci, transakce a fyzickou vrstvu.

## Oficiální témata / otázky
1. Plánování databáze — sběr požadavků a nalézání faktů, uživatelské pohledy, strategie konceptuálního návrhu.
2. Funkční závislosti — definice, Armstrongova pravidla, minimální pokrytí, nalezení klíče.
3. Normální formy relací — 1.-3. NF, metody normalizace, pokrytí závislostí, výhody/nevýhody, denormalizace.
4. Pokročilejší rysy SQL — datové typy a operátory, pohledy, oprávnění, uživatelské role.
5. Transakce — princip a účel, implementace, prokládání a problémy, stupeň izolace a uzamykání.
6. Fyzická vrstva databáze — odvozená data, integritní omezení, uložení tabulek, indexy, pohledy.
7. Procedurální rozšíření SQL — kursory a triggery, zajištění integritních omezení.
8. Objektově orientované databáze — motivace, výhody/nevýhody, objektový návrh, třídy, metody, vztahy.
9. Objektově-relační model — motivace, vlastnosti, příklady.

---
## Odpovědi v bodech

### 1. Plánování databáze
EN: *Database planning*
- Cíl: pochopit co DB má dělat a pro koho.
- Sběr požadavků: rozhovory, analýza dokumentů, pozorování, dotazníky.
- Uživatelský pohled EN: *user view* = jak konkrétní skupina vidí data (účetní ≠ skladník).
- Strategie návrhu: Top-down (celek → detaily) · Bottom-up (atributy → entity) · Kombinovaná (nejčastější).

---

### 2. Funkční závislosti
EN: *Functional dependencies*

`A → B` = znáš-li A, víš přesně B. Příklad: `RČ → Jméno`, `PSČ → Město`.

**Armstrongova pravidla** EN: *Armstrong's axioms*
| Pravidlo | Zápis | Výklad |
|---|---|---|
| Reflexivita | A → A | atribut určuje sám sebe |
| Rozšíření | A → B, pak AC → BC | přidej atribut na obě strany |
| Tranzitivita | A → B, B → C, pak A → C | řetězení |

**Minimální pokrytí** EN: *minimal cover*
```
PROBLÉM: sada závislostí obsahuje redundantní závislosti.
ŘEŠENÍ: nejmenší sada závislostí která říká totéž.
Postup: 1) pravá strana = 1 atribut  2) odstraň zbytečné atributy vlevo  3) odstraň redundantní závislosti
```

**Nalezení klíče** EN: *finding a key*
- Klíč = minimální množina atributů jejichž uzávěr = všechny atributy.
- Uzávěr EN: *closure* = co vše lze z atributu odvodit. Příklad: uzávěr RČ = celý řádek → RČ je klíč.

---

### 3. Normální formy relací
EN: *Normal forms*

```
PROBLÉM: redundantní data → při změně musíš updatovat na více místech → nekonzistence.
ŘEŠENÍ: normalizace = rozdělení tabulky do menších podle pravidel.
```

**1NF** — každá buňka = jedna hodnota (atomická). Žádné seznamy v buňce.

**2NF** — musí platit 1NF + každý neklíčový atribut závisí na CELÉM klíči.
```
PROBLÉM: klíč (StudentID, PředmětID), ale JménoStudenta závisí jen na StudentID.
ŘEŠENÍ: rozděl → Student(StudentID, Jméno) + Zápis(StudentID, PředmětID, Známka)
```

**3NF** — musí platit 2NF + žádná tranzitivní závislost mezi neklíčovými atributy.
```
PROBLÉM: ZaměstnanecID → OdděleníID → NázevOddělení (tranzitivní).
ŘEŠENÍ: rozděl → Zaměstnanec(ZaměstnanecID, OdděleníID) + Oddělení(OdděleníID, Název)
```

**Denormalizace** EN: *denormalization*
```
PROBLÉM: příliš normalizovaná DB = mnoho JOIN = pomalé dotazy.
ŘEŠENÍ: záměrné sloučení tabulek. Výměna: konzistence za rychlost.
```

| NF | Klíčové pravidlo |
|---|---|
| 1NF | atomické hodnoty |
| 2NF | závislost na celém klíči |
| 3NF | žádná tranzitivní závislost |

---

### 4. Pokročilejší rysy SQL
EN: *Advanced SQL features*

**Datové typy:** `INT`, `DECIMAL(8,2)`, `VARCHAR(100)`, `DATE`, `BOOLEAN`.

**Pohledy** EN: *views* = uložený SELECT pod jménem, chová se jako tabulka.
```sql
CREATE VIEW aktivni_zamestnanci AS
SELECT jmeno, plat FROM zamestnanci WHERE aktivni = TRUE;
```

**Oprávnění** EN: *privileges*
```sql
GRANT SELECT ON zamestnanci TO jan;
REVOKE SELECT ON zamestnanci FROM jan;
```

**Role** EN: *roles*
```
PROBLÉM: přidělovat oprávnění každému zvlášť = zdlouhavé.
ŘEŠENÍ: role = skupina oprávnění → přiřadíš roli, ne jednotlivá práva.
```
```sql
CREATE ROLE manazer;
GRANT SELECT, UPDATE ON platy TO manazer;
GRANT manazer TO jan;
```

---

### 5. Transakce
EN: *Transactions*

```
PROBLÉM: převod peněz — odečteš z účtu A, server spadne před připsáním na B → peníze zmizí.
ŘEŠENÍ: transakce = skupina příkazů která se provede buď CELÁ nebo VŮBEC.
```

**ACID:**
| Písmeno | Vlastnost | Výklad |
|---|---|---|
| A | Atomicita | vše nebo nic |
| C | Konzistence | DB přejde z platného stavu do platného stavu |
| I | Izolace | transakce se navzájem nevidí |
| D | Trvalost | po COMMIT přežije výpadek |

```sql
BEGIN;
  UPDATE ucet SET zustatek = zustatek - 1000 WHERE id = 1;
  UPDATE ucet SET zustatek = zustatek + 1000 WHERE id = 2;
COMMIT;    -- nebo ROLLBACK při chybě
```

**Problémy při prokládání:**
- Dirty read — čtu neuložená data jiné transakce
- Non-repeatable read — stejný SELECT vrátí podruhé jiný výsledek
- Phantom read — mezi dvěma SELECT přibyly nové řádky

**Úrovně izolace:**
| Úroveň | Dirty | Non-rep. | Phantom |
|---|---|---|---|
| READ UNCOMMITTED | možný | možný | možný |
| READ COMMITTED | ✗ | možný | možný |
| REPEATABLE READ | ✗ | ✗ | možný |
| SERIALIZABLE | ✗ | ✗ | ✗ |

**Uzamykání** EN: *locking* — transakce uzamkne řádek/tabulku → ostatní čekají. Uvolní po COMMIT/ROLLBACK.

---

### 6. Fyzická vrstva databáze
EN: *Physical database layer*

**Uložení tabulek:** tabulka = soubor stránek (pages) na disku, typicky 8 KB blok.

**Indexy** EN: *indexes*
```
PROBLÉM: SELECT bez indexu prochází každý řádek = pomalé.
ŘEŠENÍ: index = pomocná B-stromová struktura = rejstřík v knize.
```
```sql
CREATE INDEX idx_prijmeni ON zamestnanci(prijmeni);
```
| | Bez indexu | S indexem |
|---|---|---|
| Čtení | pomalé | rychlé |
| Zápis | rychlý | pomalejší (index se aktualizuje) |

**Odvozená data** EN: *derived data* — hodnota vypočítatelná z jiných dat. Buď počítat při dotazu nebo uložit jako vypočítaný sloupec.

**Integritní omezení:**
| Omezení | Výklad |
|---|---|
| `PRIMARY KEY` | unikátní, nenulový identifikátor |
| `FOREIGN KEY` | odkaz musí existovat v jiné tabulce |
| `NOT NULL` | hodnota nesmí být prázdná |
| `UNIQUE` | hodnota musí být unikátní |
| `CHECK` | vlastní podmínka (`CHECK (plat > 0)`) |

**Pohledy:** pohled = uložený dotaz, ne data. Materializovaný pohled EN: *materialized view* = výsledek uložen na disk → rychlejší.

---

### 7. Procedurální rozšíření SQL
EN: *Procedural SQL extensions*

```
DEFINICE
Standardní SQL = deklarativní. Procedurální rozšíření přidává: proměnné, podmínky, cykly, funkce.
Dialekty: PL/pgSQL (PostgreSQL), T-SQL (MS SQL), PL/SQL (Oracle).
```

**Uložené procedury:**
```sql
CREATE PROCEDURE zvys_plat(id INT, castka DECIMAL)
BEGIN
  UPDATE zamestnanci SET plat = plat + castka WHERE zamestnanec_id = id;
END;
CALL zvys_plat(5, 1000);
```

**Kurzory** EN: *cursors*
```
PROBLÉM: SELECT vrátí více řádků — chceš je zpracovat jeden po jednom.
ŘEŠENÍ: kurzor = ukazatel na aktuální řádek výsledku.
```
```sql
DECLARE cur CURSOR FOR SELECT jmeno FROM zamestnanci;
OPEN cur;
FETCH cur INTO @jmeno;
CLOSE cur;
```

**Triggery** EN: *triggers*
```
PROBLÉM: chceš aby se něco automaticky stalo při INSERT/UPDATE/DELETE.
ŘEŠENÍ: trigger = kód který se spustí automaticky při události na tabulce.
```
```sql
CREATE TRIGGER log_zmeny
AFTER UPDATE ON zamestnanci
FOR EACH ROW
BEGIN
  INSERT INTO audit_log VALUES(NOW(), OLD.plat, NEW.plat);
END;
```
Použití: validace, přepočet odvozených hodnot, auditní záznamy.

---

### 8. Objektově orientované databáze
EN: *Object-oriented databases (OODB)*

```
MOTIVACE
Relační DB ukládá tabulky. OOP programy pracují s objekty.
Převod objektů ↔ tabulky = zdlouhavý.
ŘEŠENÍ: OODB ukládá přímo objekty — třídy, metody, dědičnost.
```

| Konstrukt | Výklad |
|---|---|
| Třída EN: *class* | šablona objektu |
| Metoda EN: *method* | funkce patřící třídě |
| Vztahy EN: *relationships* | reference mezi objekty místo cizích klíčů |

**Výhody:** přirozené mapování z OOP, podpora dědičnosti.
**Nevýhody:** slabá standardizace, méně nástrojů, pomalejší dotazování.

---

### 9. Objektově-relační model
EN: *Object-relational model (ORDB)*

```
MOTIVACE
Relační DB = jednoduchá, ale neumí složité typy.
OODB = mocná, ale nestandardní.
ŘEŠENÍ: relační DB rozšířená o OOP prvky. Příklad: PostgreSQL.
```

**Vlastnosti:** uživatelsky definované typy, pole a vnořené tabulky, dědičnost tabulek, metody na typech.

```sql
CREATE TYPE adresa AS (ulice VARCHAR(100), mesto VARCHAR(50));
CREATE TABLE osoba (id INT PRIMARY KEY, bydliste adresa);
```

| | Relační | OO databáze | Objektově-relační |
|---|---|---|---|
| Základ | tabulky | objekty | tabulky + OOP prvky |
| SQL | ano | ne | ano (rozšířené) |
| Rozšířenost | vysoká | nízká | střední |

## Flashcards (ústní trénink)
> Q/A po probrání každého tématu.
