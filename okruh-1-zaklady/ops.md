# OPS — Operační systémy
**Okruh:** 1 — Základy informatiky &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Synchronizace procesů — důvody synchronizace, postupový prostor.
2. Synchronizační úlohy — producent a konzument, čtenáři a písař, vzájemné vyloučení.
3. Chyby v synchronizaci — uváznutí (deadlock), stárnutí (starvation).
4. Synchronizační prostředky — semafory, zasílání zpráv.
5. Přidělování procesoru — stavy, funkce modulu, způsoby přidělování v multiprogramovém systému (plánování).
6. Přidělování paměti — adresování paměti, funkce modulu, stránkování na žádost.
7. Systém souborů — úkoly, úrovně; FAT32, NTFS, EXT2 (výhody, práva, použití, způsob ukládání).

---
## Odpovědi v bodech

### 1. Synchronizace procesů
**DEFINICE**
Synchronizace = koordinace přístupu více procesů ke sdíleným prostředkům.
EN: process synchronization

**DŮVOD**
- Bez synchronizace → race condition (výsledek závisí na pořadí přístupu)
- Kritická sekce = část kódu, kde proces přistupuje ke sdílenému prostředku

**POSTUPOVÝ PROSTOR**
- Vstupní sekce → kritická sekce → výstupní sekce → nekritická sekce

---

### 2. Synchronizační úlohy

**Producent a konzument**
EN: producer-consumer problem
- Producent vkládá data do bufferu, konzument je odebírá
- Problém: buffer plný → producent čeká; buffer prázdný → konzument čeká
- Řešení: semafory `empty`, `full`, `mutex`

**Čtenáři a písař**
EN: readers-writers problem
- Číst může více procesů najednou ✓
- Psát může jen 1 proces, nikdo jiný nečte ✓

**Vzájemné vyloučení**
EN: mutual exclusion / mutex
- Kritickou sekci vykonává max. 1 proces najednou

---

### 3. Chyby v synchronizaci

**DEFINICE — Deadlock (uváznutí)**
= množina procesů čeká na prostředky, které drží jiné procesy ze stejné množiny → nikdo nemůže pokračovat.
EN: deadlock

**4 Coffmanovy podmínky** (musí platit všechny):
1. Vzájemné vyloučení
2. Drž a čekej
3. Bez odnímání
4. Kruhové čekání

**Prevence deadlocku:**
- Uspořádat přidělování prostředků v pevném pořadí (zruší kruhové čekání)
- Detekce + zotavení (zabít jeden proces)

**DEFINICE — Starvation (stárnutí)**
= proces čeká donekonečna, protože jiné procesy mají vždy přednost.
EN: starvation
- Řešení: prioritní stárnutí (aging) — čím déle čeká, tím vyšší priorita

---

### 4. Synchronizační prostředky

**DEFINICE — Semafor**
= celočíselná proměnná + 2 atomické operace.
EN: semaphore

| Operace | Co dělá |
|---|---|
| `wait(S)` / P(S) | S-- ; pokud S < 0 → proces čeká |
| `signal(S)` / V(S) | S++ ; pokud někdo čeká → probuď ho |

**Binární semafor = mutex** (S ∈ {0,1})

**Zasílání zpráv**
EN: message passing
- `send(P, zpráva)` / `receive(Q, zpráva)`
- Synchronizace bez sdílené paměti (vhodné pro distribuované systémy)

---

### 5. Přidělování procesoru

**5 stavů procesu:**
```
Nový → Připravený → Běžící → Ukončený
                 ↑      ↓
               Čekající (blokovaný)
```

| Stav | Co se děje |
|---|---|
| Nový (new) | proces se vytváří |
| Připravený (ready) | čeká na přidělení CPU |
| Běžící (running) | CPU ho právě vykonává |
| Čekající (waiting) | čeká na I/O nebo událost |
| Ukončený (terminated) | hotov |

**Přechody:**
- Běžící → Čekající: čeká na I/O
- Čekající → Připravený: I/O dokončeno
- Běžící → Připravený: OS ho přerušil (preempce)
- Připravený → Běžící: OS přidělil CPU

**Způsoby plánování:**
- FCFS (First Come First Served) — jednoduchý, může způsobit starvation
- SJF (Shortest Job First) — minimalizuje průměrnou čekací dobu
- Round Robin — každý dostane časový kvantum, pak se vystřídají
- Prioritní plánování — vyšší priorita → dříve CPU

---

### 6. Přidělování paměti

**Adresování paměti:**
- Logická adresa = adresa v programu
- Fyzická adresa = skutečné místo v RAM
- MMU (Memory Management Unit) převádí logickou → fyzickou

**Stránkování na žádost (demand paging):**
EN: demand paging
- Stránka se načte do RAM až při prvním přístupu
- Page fault = stránka není v RAM → OS ji načte z disku
- Výhoda: program může být větší než RAM, šetří paměť

---

### 7. Systém souborů

**Souborové systémy — srovnání:**

| | FAT32 | NTFS | EXT2 |
|---|---|---|---|
| OS | Windows (starý) | Windows | Linux |
| Max. soubor | 4 GB | 16 TB | 2 TB |
| Práva | ✗ | ✓ | ✓ |
| Žurnálování | ✗ | ✓ | ✗ |
| Použití | USB, SD karty | systémový disk Win | systémový disk Linux |

**Způsob ukládání:**
- **FAT32** — linked list clusterů (jdi po šipkách)
- **NTFS** — MFT (Master File Table) — kartotéka, každý soubor = 1 záznam
- **EXT2** — inode tabulka — název souboru je odkaz na inode číslo

---

## Flashcards (ústní trénink)

**Q:** Co je deadlock a jak mu předejít?
**A:** Kruhové čekání procesů na prostředky. Prevence: pevné pořadí přidělování nebo detekce + zabití procesu.

**Q:** Co je demand paging?
**A:** Stránka se načte do RAM až při přístupu (page fault). Šetří paměť, program může být větší než RAM.

**Q:** Jaké jsou stavy procesu?
**A:** Nový → Připravený → Běžící → Ukončený, s odboček do Čekající (při I/O).

**Q:** Co je semafor?
**A:** Celočíselná proměnná s operacemi wait (zamkni) a signal (odemkni). Binární semafor = mutex.

**Q:** Producent a konzument — jaký je problém?
**A:** Sdílený buffer — producent čeká při plném, konzument při prázdném, přístup chráníme mutexem.

**Q:** Rozdíl FAT32 / NTFS / EXT2?
**A:** FAT32 = linked list, bez práv, USB. NTFS = MFT kartotéka, práva, žurnál, Windows. EXT2 = inode, práva, Linux.
