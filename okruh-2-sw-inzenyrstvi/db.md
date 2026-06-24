# DB — Úvod do databázových systémů
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`
> Pozn.: tematicky navazuje NIDB (okruh 3) — pokročilejší SQL, normalizace, transakce.

## Oficiální témata / otázky
1. Databázový systém — definice, účel, DBMS (database management system).
2. Návrh databáze — konceptuální, logický a fyzický model.
3. Konceptuální modelování, ER model — princip a účel, základní konstrukty, integritní omezení.
4. Relační model dat — definice, princip, integritní omezení.
5. Relační algebra — základní operace, spojení, použití pro dotazování.
6. Transformace ER modelu do relačního modelu.
7. Jazyk SQL pro definici dat (DDL) a pro manipulaci s daty (DML).
8. Příkaz SELECT — klauzule, dotazy nad více tabulkami a spojení, agregační funkce, vnořené poddotazy, univerzální a existenční kvantifikátor.
9. Další možnosti SQL — ošetření NULL, podmíněné větvení, řádkové výrazy.
10. Implementace a použití transakcí v SQL.

---
## Odpovědi v bodech

### 9. Další možnosti jazyka SQL
EN: *Advanced SQL features*

**NULL**
- NULL = chybějící/neznámá hodnota. Trojhodnotová logika: TRUE / FALSE / UNKNOWN.
- Porovnávat jen přes `IS NULL` / `IS NOT NULL` (ne `=` nebo `<>`).
- `COALESCE(a, b, c)` — první non-NULL; `NULLIF(a, b)` — NULL pokud a=b, jinak a.

**Podmíněné větvení** EN: *conditional expression*
```sql
CASE WHEN podmínka THEN výsledek ... ELSE výsledek_default END
```

**Řádkové výrazy** EN: *row value constructors*
- Porovnání n-tice sloupců najednou: `WHERE (a, b) = (1, 2)`
- Použití: `WHERE (oddeleni, pozice) IN (SELECT oddeleni, pozice FROM vedeni)`

---

### 10. Implementace a použití transakcí v jazyce SQL
EN: *Transaction implementation and usage*

**ACID:**
| Písmeno | Vlastnost | Význam |
|---|---|---|
| A | Atomicity (atomicita) | vše nebo nic |
| C | Consistency (konzistence) | DB přejde z platného stavu do platného stavu |
| I | Isolation (izolace) | transakce se navzájem nevidí |
| D | Durability (trvalost) | po COMMIT přežije výpadek |

**Příkazy:**
```sql
BEGIN;  ...  COMMIT;      -- potvrzení
BEGIN;  ...  ROLLBACK;    -- zrušení
SAVEPOINT bod1;  ROLLBACK TO SAVEPOINT bod1;
```

**Problémy bez izolace:**
- Dirty read — čtu neuložená data jiné transakce
- Non-repeatable read — stejný SELECT vrátí jiný výsledek
- Phantom read — nové řádky přibyly mezi dvěma SELECT

**Úrovně izolace** EN: *isolation levels*
| Úroveň | Dirty | Non-rep. | Phantom |
|---|---|---|---|
| READ UNCOMMITTED | možný | možný | možný |
| READ COMMITTED | ✗ | možný | možný |
| REPEATABLE READ | ✗ | ✗ | možný |
| SERIALIZABLE | ✗ | ✗ | ✗ |

```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

## Flashcards (ústní trénink)
> Q/A po probrání každého tématu.
