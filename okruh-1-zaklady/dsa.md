# DSA — Datové struktury a algoritmy
**Okruh:** 1 — Základy informatiky &nbsp;&nbsp; **Stav:** ⏳ rozpracováno
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Algoritmy řazení — výběrem (Select-sort), vkládáním (Insert-sort), záměnou (Bubble-sort), haldou (Heap-sort), přihrádkové (Radix-sort, Counting-sort), slučováním (Merge-sort), dělením (Quick-sort).
2. Asymptotická operační složitost řazení — minimální, průměrná, maximální.
3. Adresní metody vyhledávání — přímý přístup, otevřené a zřetězené rozptylování (hashování).
4. Asociativní metody vyhledávání — sekvenční, binárním půlením, binární vyhledávací stromy.
5. Operační a paměťová složitost algoritmů vyhledávání.
6. Abstraktní datové typy — zásobník, fronta, prioritní fronta, pole, tabulka, seznam, množina; specifikace a implementace.

---

## Odpovědi v bodech

---

### Složitost — základy (nutno znát pro vše dál)

```
DEFINICE: Složitost
Jak rychle roste počet operací / paměť v závislosti na velikosti vstupu n.
EN: Time complexity / Space complexity
```

```
NOTACE O(…)  — nejhorší případ (worst case)
         Ω(…) — nejlepší případ (best case)
         Θ(…) — průměrný případ (average case)
```

| Složitost | Název | Příklad |
|---|---|---|
| O(1) | konstantní | přímý přístup do pole |
| O(log n) | logaritmická | binární půlení |
| O(n) | lineární | sekvenční hledání |
| O(n log n) | linearitmická | Merge-sort, Heap-sort |
| O(n²) | kvadratická | Bubble, Insert, Select |
| O(2ⁿ) | exponenciální | hrubá síla kombinatorika |

---

## ŘAZENÍ (Sorting)

> **Stabilní řazení** = stejné prvky zůstanou ve stejném pořadí jako na vstupu.
> EN: Stable sort

---

### 1. Select-sort — Řazení výběrem
EN: Selection sort

**Idea:** Najdi minimum → přesuň na začátek → opakuj pro zbytek.

**Postup:**
- Projdi pole, najdi nejmenší prvek.
- Prohoď ho s prvkem na pozici `i`.
- Posuň `i` o 1 doprava. Opakuj.

**Příklad:** `[5, 3, 1, 4]`
- krok 1: min=1 → `[1, 3, 5, 4]`
- krok 2: min=3 → `[1, 3, 5, 4]`
- krok 3: min=4 → `[1, 3, 4, 5]`

| | Složitost |
|---|---|
| Nejlepší | O(n²) |
| Průměrný | O(n²) |
| Nejhorší | O(n²) |
| Paměť | O(1) — in-place |
| Stabilní? | ❌ NE |

---

### 2. Insert-sort — Řazení vkládáním
EN: Insertion sort

**Idea:** Jako třídění karet v ruce — každý nový prvek vlož na správné místo.

**Postup:**
- Vezmi prvek na pozici `i`.
- Posuv doleva, dokud nenajdeš správné místo.
- Vlož.

**Příklad:** `[5, 3, 1, 4]`
- i=1: 3 < 5 → `[3, 5, 1, 4]`
- i=2: 1 < 5, 1 < 3 → `[1, 3, 5, 4]`
- i=3: 4 < 5 → `[1, 3, 4, 5]`

| | Složitost |
|---|---|
| Nejlepší | O(n) — již seřazeno |
| Průměrný | O(n²) |
| Nejhorší | O(n²) — obrácené pořadí |
| Paměť | O(1) — in-place |
| Stabilní? | ✅ ANO |

---

### 3. Bubble-sort — Řazení záměnou (bublinové)
EN: Bubble sort

**Idea:** Velké prvky „bublají" na konec — opakovaně prohoď sousedy, pokud jsou ve špatném pořadí.

**Postup:**
- Projdi pole, porovnej každé dva sousedy.
- Pokud `a[j] > a[j+1]` → prohoď.
- Opakuj `n-1` průchodů.

**Příklad:** `[5, 3, 1, 4]`
- průchod 1: 5↔3, 5↔1, 5↔4 → `[3, 1, 4, 5]`
- průchod 2: 3↔1, 3<4 → `[1, 3, 4, 5]`
- průchod 3: seřazeno ✓

| | Složitost |
|---|---|
| Nejlepší | O(n) — s příznakem "prohozeno?" |
| Průměrný | O(n²) |
| Nejhorší | O(n²) |
| Paměť | O(1) — in-place |
| Stabilní? | ✅ ANO |

---

### 4. Heap-sort — Řazení haldou
EN: Heap sort

**Idea:** Postav haldu (binární strom, kde otec ≥ děti) → opakovaně odeber maximum.

```
DEFINICE: Halda (Max-heap)
Binární strom, kde každý uzel je větší nebo roven oběma dětem.
EN: Heap (max-heap)
```

**Postup:**
1. Postav max-heap z pole (heapify) — O(n).
2. Prohoď kořen (maximum) s posledním prvkem.
3. Zmenši haldu o 1, oprav haldu (sift-down).
4. Opakuj od kroku 2.

| | Složitost |
|---|---|
| Nejlepší | O(n log n) |
| Průměrný | O(n log n) |
| Nejhorší | O(n log n) |
| Paměť | O(1) — in-place |
| Stabilní? | ❌ NE |

**Kdy použít:** Potřebuješ garantované O(n log n) a nemáš extra paměť.

---

### 5. Merge-sort — Řazení slučováním
EN: Merge sort

**Idea:** Rozděl pole na půl → rekurzivně seřaď každou půlku → slij dohromady.

**Postup:**
1. Rozděl pole na 2 poloviny.
2. Rekurzivně seřaď obě.
3. Slij (merge) dvě seřazené poloviny do jedné.

```
VZOREC: T(n) = 2·T(n/2) + O(n)  →  O(n log n)
```

| | Složitost |
|---|---|
| Nejlepší | O(n log n) |
| Průměrný | O(n log n) |
| Nejhorší | O(n log n) |
| Paměť | O(n) — potřebuje pomocné pole |
| Stabilní? | ✅ ANO |

**Kdy použít:** Velká data, stabilita nutná, máš paměť navíc. Ideální pro spojové seznamy.

---

### 6. Quick-sort — Řazení dělením
EN: Quick sort

**Idea:** Vyber pivot → prvky menší dej vlevo, větší vpravo → rekurzivně seřaď obě části.

**Postup:**
1. Vyber pivot (náhodně / první / střed).
2. Partition: přeskupuj prvky kolem pivotu.
3. Rekurze na levou a pravou část.

| | Složitost |
|---|---|
| Nejlepší | O(n log n) — pivot vždy dělí na půl |
| Průměrný | O(n log n) |
| Nejhorší | O(n²) — pivot je vždy min/max |
| Paměť | O(log n) — zásobník rekurze |
| Stabilní? | ❌ NE |

**Proč nejoblíbenější:** V praxi nejrychlejší díky cache-friendliness, i když worst-case je O(n²).

---

### 7. Radix-sort — Přihrádkové řazení
EN: Radix sort (also: Bucket sort, Counting sort)

**Idea:** Neporovnávej prvky — řaď podle číslic (od nejméně významné po nejvýznamnější).

**Postup (LSD — Least Significant Digit):**
1. Seřaď podle poslední cifry (stabilně!).
2. Seřaď podle předposlední cifry.
3. Opakuj pro všechny cifry.

**Příklad:** `[170, 45, 75, 90, 802, 24, 2, 66]`
- po 1. cifře: `[170, 90, 802, 2, 24, 45, 75, 66]`
- po 2. cifře: `[802, 2, 24, 45, 66, 170, 75, 90]`
- po 3. cifře: `[2, 24, 45, 66, 75, 90, 170, 802]` ✓

```
VZOREC: O(d · n)  kde d = počet číslic, n = počet prvků
```

| | Složitost |
|---|---|
| Všechny případy | O(d · n) — lineární pro pevné d |
| Paměť | O(n + k) kde k = rozsah číslic |
| Stabilní? | ✅ ANO (musí být!) |

**Kdy použít:** Čísla nebo řetězce s pevnou délkou. Rychlejší než O(n log n) pro velké n.

---

### Srovnávací tabulka — VŠECHNA řazení

| Algoritmus | Best | Avg | Worst | Paměť | Stabilní |
|---|---|---|---|---|---|
| Select-sort | O(n²) | O(n²) | O(n²) | O(1) | ❌ |
| Insert-sort | **O(n)** | O(n²) | O(n²) | O(1) | ✅ |
| Bubble-sort | **O(n)** | O(n²) | O(n²) | O(1) | ✅ |
| Heap-sort | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ |
| Merge-sort | O(n log n) | O(n log n) | O(n log n) | **O(n)** | ✅ |
| Quick-sort | O(n log n) | O(n log n) | **O(n²)** | O(log n) | ❌ |
| Radix-sort | O(dn) | O(dn) | O(dn) | O(n+k) | ✅ |

> **Pamatuj:** Žádný porovnávací algoritmus nemůže být lepší než O(n log n) — to je teoret. dolní hranice.
> EN: Comparison-based sorting lower bound

---

## VYHLEDÁVÁNÍ (Searching)

Dělí se na **2 kategorie:**
- **Adresní** — víme, kde (přibližně) prvek je → hashování
- **Asociativní** — hledáme podle hodnoty → sekvenční, půlení, BST

---

### Adresní metody — Hashování
EN: Address-based search / Hashing

```
DEFINICE: Hashovací funkce
Funkce h(k), která převede klíč k na index do tabulky.
EN: Hash function
```

**Ideál:** h(k) = k mod m (kde m = velikost tabulky)

**Problém:** Kolize — dvě různé hodnoty dají stejný index.

#### Řešení kolizí

**1. Zřetězené rozptylování** (EN: Chaining)
- Na každém indexu je spojový seznam.
- Kolize → přidej do seznamu.
- Hledání: spočítej h(k) → projdi seznam.

```
Složitost: O(1) průměr, O(n) nejhorší (vše na 1 indexu)
```

**2. Otevřené rozptylování** (EN: Open addressing)
- Kolize → hledej další volné místo (linear probing: +1, +2, …).
- Vše je v samotné tabulce, žádné seznamy.

```
Složitost: O(1) průměr, O(n) nejhorší
Paměť: O(1) navíc (in-place)
```

---

### Asociativní metody

#### 1. Sekvenční vyhledávání
EN: Sequential / Linear search

**Idea:** Projdi prvek po prvku, dokud nenajdeš.

```
Složitost: O(n) — vždy projde průměrně n/2 prvků
Kdy použít: neseřazené pole, malé n
```

---

#### 2. Binární půlení
EN: Binary search

**Idea:** Pole musí být **seřazené**. Porovnej se středem → hledej v levé nebo pravé polovině.

**Postup:**
1. `low = 0`, `high = n-1`
2. `mid = (low + high) / 2`
3. Pokud `a[mid] == hledaný` → nalezeno.
4. Pokud `a[mid] < hledaný` → `low = mid + 1`
5. Pokud `a[mid] > hledaný` → `high = mid - 1`
6. Opakuj dokud `low <= high`.

```
Složitost: O(log n)
Podmínka: pole musí být seřazené!
```

**Příklad:** Hledej 7 v `[1, 3, 5, 7, 9, 11]`
- mid=5 → a[mid]=5 < 7 → hledej vpravo
- mid=9 → a[mid]=9 > 7 → hledej vlevo
- mid=7 → nalezeno ✓

---

#### 3. Binární vyhledávací strom (BST)
EN: Binary Search Tree

```
DEFINICE: BST
Binární strom, kde pro každý uzel platí:
  levý podstrom < uzel < pravý podstrom
EN: Binary Search Tree
```

**Operace:**
- **Hledání:** jdi doleva nebo doprava podle hodnoty → O(log n) průměr
- **Vložení:** najdi správné místo, vlož jako list
- **Mazání:** 3 případy (list / 1 dítě / 2 děti)

| | Složitost |
|---|---|
| Průměr (vyvážený strom) | O(log n) |
| Nejhorší (degenerovaný = seznam) | O(n) |

> **Degenerovaný BST:** vkládáš vzestupně → strom se stane seznamem → O(n).
> Řešení: AVL strom, Red-Black strom (vyvažování).

---

### Srovnávací tabulka — VYHLEDÁVÁNÍ

| Metoda | Složitost (avg) | Složitost (worst) | Podmínka |
|---|---|---|---|
| Sekvenční | O(n) | O(n) | žádná |
| Binární půlení | O(log n) | O(log n) | seřazené pole |
| BST | O(log n) | O(n) | vyvážený strom |
| Hashování (řetězení) | O(1) | O(n) | dobrá hash funkce |
| Přímý přístup | O(1) | O(1) | klíče = indexy |

---

---

## ADT — Abstraktní datové typy
EN: Abstract Data Types

```
DEFINICE: ADT
Datový typ popsaný operacemi (co umí), ne implementací (jak je udělaný).
```

| ADT | EN | Princip | Klíčová operace | Složitost |
|---|---|---|---|---|
| Zásobník | Stack | LIFO | push/pop | O(1) |
| Fronta | Queue | FIFO | enqueue/dequeue | O(1) |
| Prioritní fronta | Priority Queue | max první | extractMax | O(log n) |
| Pole | Array | index | a[i] | O(1) přístup |
| Seznam | Linked List | řetěz uzlů | vložení na začátek | O(1) |
| Tabulka | Hash Table | klíč→hodnota | get/set | O(1) avg |
| Množina | Set | unikátní prvky | contains | O(1) avg |

### Zásobník (Stack) — LIFO
- push(x) = vlož na vrch O(1)
- pop() = odeber z vrchu O(1)
- Použití: rekurze, undo, parser závorek

### Fronta (Queue) — FIFO
- enqueue(x) = vlož na konec O(1)
- dequeue() = odeber ze začátku O(1)
- Použití: BFS, tiskové fronty, plánování procesů

### Prioritní fronta (Priority Queue)
- Vždy odebereš prvek s nejvyšší prioritou
- Implementace: halda (heap)
- insert O(log n), extractMax O(log n)
- Použití: Dijkstrův algoritmus, plánování CPU

### Pole (Array)
- Pevná řada boxů v paměti, přístup přes index O(1)
- Vložení/mazání uprostřed O(n) — musí posouvat prvky
- Nevýhoda: pevná velikost

### Seznam (Linked List)
- Uzly: hodnota + ukazatel na další
- Vložení na začátek O(1), hledání O(n)
- Výhoda oproti poli: dynamická velikost
- Typy: jednosměrný, obousměrný, kruhový

### Tabulka (Hash Table)
- klíč → hashovací funkce → index → hodnota
- get/set/delete průměr O(1)
- Použití: databáze, cache, slovníky

### Množina (Set)
- Kolekce unikátních prvků bez duplicit
- Implementace: hash tabulka nebo BST
- Operace: add, remove, contains, union, intersection

---

## Flashcards (ústní trénink)

**Q:** Jaká je nejhorší složitost Quick-sortu a proč?
**A:** O(n²) — pivot je vždy nejmenší nebo největší prvek (např. již seřazené pole).

**Q:** Který řadicí algoritmus je nejrychlejší v praxi a proč?
**A:** Quick-sort — nejlepší cache-friendliness, průměrně O(n log n).

**Q:** Co je stabilní řazení? Uveď příklad stabilního a nestabilního.
**A:** Stabilní = zachovává pořadí stejných prvků. Stabilní: Merge-sort, Insert-sort. Nestabilní: Quick-sort, Heap-sort.

**Q:** Proč nemůže být žádný porovnávací algoritmus lepší než O(n log n)?
**A:** Protože rozhodovací strom všech možností má hloubku log(n!) ≈ n log n (Stirlingův vzorec).

**Q:** Co je kolize v hashování a jak ji řešíme?
**A:** Dva klíče dají stejný index. Řešení: zřetězení (seznamy) nebo otevřené rozptylování (hledej další volné místo).

**Q:** Kdy použiješ Radix-sort místo Quick-sortu?
**A:** Když řadíš velké množství čísel s pevným počtem číslic — Radix je O(dn), tedy lineární.

**Q:** Jaká je podmínka pro použití binárního vyhledávání?
**A:** Pole musí být seřazené.

**Q:** Co je degenerovaný BST?
**A:** Strom vzniklý vkládáním seřazených dat — stane se seznamem, složitost O(n). Řešení: AVL nebo Red-Black strom.
