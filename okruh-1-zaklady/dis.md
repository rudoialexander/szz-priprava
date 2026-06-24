# DIS — Diskrétní struktury
**Okruh:** 1 — Základy informatiky &nbsp;&nbsp; **Stav:** ⏳ rozpracováno
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Množiny — definice, podmnožiny, operace a jejich vlastnosti, mohutnost množin.
2. Relace — definice, inverzní relace, vlastnosti relace na množině, ekvivalence, uspořádání.
3. Zobrazení — definice, vlastnosti.
4. Výroková logika — výrok, spojky, formule a pravdivostní ohodnocení, tautologie/kontradikce, de Morganovy zákony, negace formulí, sémantický důsledek, CNF/DNF.
5. Predikátová logika — rozdíly oproti výrokové, syntaxe a sémantika, interpretace, sémantický důsledek.
6. Neorientované grafy — pojmy, isomorfismus, stupeň uzlu, sledy, souvislost, stromy a kostry.
7. Orientované grafy — pojmy, sledy, silná souvislost, stupně uzlu.
8. Vlastnosti grafů — pokrytí, Eulerův graf, vzdálenost na grafu.
9. Kořenové stromy — definice, hloubka, pravidelné a binární stromy.
10. Reprezentace grafů v paměti — matice incidence, matice sousednosti, spojová reprezentace.
11. Grafové algoritmy — BFS/DFS, minimální kostra, Huffmanův kód, Dijkstrův algoritmus.

---

## Odpovědi v bodech

---

### 1. Množiny
EN: Sets

```
DEFINICE: Množina
Kolekce prvků bez duplicit a bez pořadí.
EN: Set
```

- `a ∈ A` = prvek a patří do A
- `a ∉ A` = prvek a nepatří do A
- `∅` = prázdná množina

**Podmnožina:**
- `A ⊆ B` = každý prvek A je také v B
- `A ⊂ B` = A ⊆ B AND A ≠ B (vlastní podmnožina)

**Operace:**

| Operace | Symbol | Popis | EN |
|---|---|---|---|
| Sjednocení | A ∪ B | prvky v A nebo B | Union |
| Průnik | A ∩ B | prvky v A i B | Intersection |
| Rozdíl | A \ B | prvky v A ale ne v B | Difference |
| Doplněk | Ā | prvky co nejsou v A | Complement |
| Kartézský součin | A × B | všechny dvojice (a,b) | Cartesian product |

```
VZOREC: Mohutnost (EN: Cardinality)
|A| = počet prvků
|A × B| = |A| · |B|   ← podmínka: žádná, mohutnosti mohou být různé
```

**De Morganovy zákony:**
```
Ā ∪ B̄ = (A ∩ B)‾
Ā ∩ B̄ = (A ∪ B)‾
```

---

### 2. Relace
EN: Relation

```
DEFINICE: Relace
Podmnožina kartézského součinu A × B.
Říká, které dvojice prvků spolu "souvisí".
EN: Relation R ⊆ A × B
```

- Píšeme: `(a, b) ∈ R` nebo `aRb`

**Inverzní relace:**
```
R⁻¹ = {(b,a) | (a,b) ∈ R}
EN: Inverse relation — obrátíme všechny dvojice
```

**Vlastnosti relace na množině A:**

| Vlastnost | Definice | Příklad |
|---|---|---|
| Reflexivní | `(a,a) ∈ R` pro každé a | = (rovnost) |
| Symetrická | `(a,b) ∈ R → (b,a) ∈ R` | přátelství |
| Antisymetrická | `(a,b) ∈ R AND (b,a) ∈ R → a=b` | ≤ |
| Tranzitivní | `(a,b) ∈ R AND (b,c) ∈ R → (a,c) ∈ R` | < |

**Ekvivalence:**
```
DEFINICE: Ekvivalence
Relace která je: reflexivní + symetrická + tranzitivní
EN: Equivalence relation
Příklad: "má stejnou barvu vlasů"
```

**Uspořádání:**
```
DEFINICE: Částečné uspořádání
Relace která je: reflexivní + antisymetrická + tranzitivní
EN: Partial order
Příklad: ≤ na číslech, ⊆ na množinách
```

---

### 3. Zobrazení
EN: Function / Mapping

```
DEFINICE: Zobrazení (funkce)
Relace f: A → B kde každý prvek A má právě jeden obraz v B.
EN: Function / Mapping
```

**Vlastnosti:**

| Vlastnost | Definice | EN |
|---|---|---|
| Injekce | různé vstupy → různé výstupy | Injective / One-to-one |
| Surjekce | každý prvek B má vzor | Surjective / Onto |
| Bijekce | injekce + surjekce | Bijective / One-to-one correspondence |

```
PŘÍKLAD:
f: {1,2,3} → {a,b,c}
f(1)=a, f(2)=b, f(3)=c  →  bijekce ✅

f: {1,2,3} → {a,b}
f(1)=a, f(2)=a, f(3)=b  →  surjekce, ale ne injekce ❌
```

---

### 4. Výroková logika
EN: Propositional logic

```
DEFINICE: Výrok
Tvrzení, které je buď pravdivé (1) nebo nepravdivé (0).
EN: Proposition
```

**Logické spojky:**

| Spojka | Symbol | Název | EN | Pravda když |
|---|---|---|---|---|
| Negace | ¬p | ne p | NOT | p je 0 |
| Konjunkce | p ∧ q | p a zároveň q | AND | oba 1 |
| Disjunkce | p ∨ q | p nebo q | OR | aspoň jeden 1 |
| Implikace | p → q | pokud p pak q | IMPLIES | falsejen 1→0 |
| Ekvivalence | p ↔ q | p právě tehdy q | IFF | oba stejné |

**Pravdivostní tabulka pro implikaci (nejčastěji zkouší):**
```
p=1, q=1 → p→q = 1
p=1, q=0 → p→q = 0  ← jediný případ kdy je implikace FALSE
p=0, q=1 → p→q = 1
p=0, q=0 → p→q = 1
```

**Tautologie vs. kontradikce:**
```
TAUTOLOGIE  = formule pravdivá pro VŠECHNY ohodnocení
EN: Tautology
Příklad: p ∨ ¬p  (vždy pravda)

KONTRADIKCE = formule nepravdivá pro VŠECHNA ohodnocení
EN: Contradiction
Příklad: p ∧ ¬p  (vždy nepravda)
```

**De Morganovy zákony (logika):**
```
¬(p ∧ q) = ¬p ∨ ¬q
¬(p ∨ q) = ¬p ∧ ¬q
```

**CNF a DNF:**
```
CNF = Conjunctive Normal Form = konjunkce klauzulí
    = AND klauzulí, kde každá klauzule je OR literálů
    Příklad: (p ∨ q) ∧ (¬p ∨ r)
EN: Conjunctive Normal Form

DNF = Disjunctive Normal Form = disjunkce konjunkcí
    = OR skupin, kde každá skupina je AND literálů
    Příklad: (p ∧ q) ∨ (¬p ∧ r)
EN: Disjunctive Normal Form
```

**Sémantický důsledek:**
```
φ ⊨ ψ  = "ψ je sémantický důsledek φ"
       = ve všech případech kde φ platí, platí i ψ
EN: Semantic entailment
```

---

### 5. Predikátová logika
EN: Predicate logic / First-order logic

```
ROZDÍL oproti výrokové logice:
Výroková: pracuje s celými výroky (p, q)
Predikátová: pracuje s objekty, vlastnostmi a kvantifikátory
EN: First-order logic adds: variables, predicates, quantifiers
```

**Kvantifikátory:**
```
∀x P(x)  = "pro každé x platí P(x)"  (univerzální)
EN: For all / Universal quantifier

∃x P(x)  = "existuje x takové, že P(x)"  (existenční)
EN: There exists / Existential quantifier
```

**Příklad:**
```
∀x (Člověk(x) → Smrtelný(x))   = každý člověk je smrtelný
∃x (Člověk(x) ∧ Moudrý(x))     = existuje moudrý člověk
```

**Negace kvantifikátorů (de Morgan pro predikáty):**
```
¬∀x P(x)  =  ∃x ¬P(x)
¬∃x P(x)  =  ∀x ¬P(x)
```

**Interpretace:**
```
DEFINICE: Interpretace
Přiřazení konkrétního významu symbolům (doména, hodnoty predikátů).
EN: Interpretation / Model
```

---

### 6. Neorientované grafy
EN: Undirected graphs

```
DEFINICE: Graf
G = (V, E) kde V = uzly (vrcholy), E = hrany
EN: Graph — V = vertices, E = edges
Hrana = {u, v} — neuspořádaná dvojice uzlů
```

```
PŘÍKLAD:
        A ——— B
        |   / |
        |  /  |
        | /   |
        C ——— D

V = {A, B, C, D}
E = {AB, AC, BC, BD, CD}

Stupně: deg(A)=2, deg(B)=3, deg(C)=3, deg(D)=2
```

**Základní pojmy:**

| Pojem | Definice | EN |
|---|---|---|
| Stupeň uzlu | počet hran incidentních s uzlem | Degree |
| Sled | posloupnost uzlů spojených hranami | Walk |
| Cesta | sled bez opakování uzlů | Path |
| Kružnice | cesta začínající a končící ve stejném uzlu | Cycle |
| Souvislý graf | mezi každými dvěma uzly existuje cesta | Connected graph |

```
VZOREC: Součet stupňů = 2 · |E|
2+3+3+2 = 10 = 2 · 5 hran ✓
EN: Handshaking lemma
```

**Isomorfismus:**
```
DEFINICE: Isomorfní grafy
Stejná struktura, různé "jmenovky" uzlů.
EN: Graph isomorphism

G₁:  A—B    G₂:  X—Y
     |  |        |  |
     C—D         Z—W

G₁ ≅ G₂  (bijekce: A↔X, B↔Y, C↔Z, D↔W)
```

**Strom a kostra:**
```
DEFINICE: Strom = souvislý graf bez kružnic
|E| = |V| - 1
EN: Tree

     A
    / \
   B   C        ← strom: 4 uzly, 3 hrany ✓
    \
     D

DEFINICE: Kostra = podgraf který je strom + obsahuje všechny uzly
EN: Spanning tree
```

---

### 7. Orientované grafy
EN: Directed graphs (Digraphs)

```
DEFINICE: Orientovaný graf
Hrany mají směr: (u, v) ≠ (v, u)
EN: Directed graph / Digraph
```

```
PŘÍKLAD:
        A ──→ B
        ↑     |
        |     ↓
        D ←── C

in-degree(A)  = 1  (přichází z D)
out-degree(A) = 1  (odchází do B)
in-degree(B)  = 1, out-degree(B) = 1
```

**Stupně uzlu:**
```
Vstupní stupeň  (in-degree)  = počet hran PŘICHÁZEJÍCÍCH do uzlu
Výstupní stupeň (out-degree) = počet hran ODCHÁZEJÍCÍCH z uzlu
```

**Silná souvislost:**
```
DEFINICE: Silně souvislý graf
Z každého uzlu se dostaneš do každého jiného.
EN: Strongly connected

Příklad výše: A→B→C→D→A  ✓  silně souvislý

Protipříklad:
        A ──→ B
Z B se nedostaneš zpět do A → NENÍ silně souvislý ✗
```

---

### 8. Vlastnosti grafů
EN: Graph properties

**Eulerův graf:**
```
DEFINICE: Eulerův uzavřený tah
Projde každou hranou právě jednou a vrátí se na start.
EN: Eulerian circuit

PODMÍNKA: každý uzel má SUDÝ stupeň

PŘÍKLAD — má Eulerův tah:
        A ——— B
        |     |
        D ——— C
deg(A)=deg(B)=deg(C)=deg(D) = 2  (vše sudé ✓)
Tah: A→B→C→D→A ✓

PŘÍKLAD — nemá Eulerův tah:
        A
       /|\
      B—C—D
deg(A)=3  (liché ✗)
```

**Vzdálenost:**
```
DEFINICE: d(u,v) = délka nejkratší cesty mezi u a v
EN: Graph distance

        A ——— B ——— C
              |
              D

d(A,C) = 2  (A→B→C)
d(A,D) = 2  (A→B→D)
d(C,D) = 2  (C→B→D)
```

**Pokrytí:**
```
DEFINICE: Vrcholové pokrytí
Nejmenší množina uzlů pokrývající všechny hrany.
EN: Vertex cover

        A ——— B ——— C
              |
              D

Pokrytí = {B}  ← B je na každé hraně ✓
```

---

### 9. Kořenové stromy
EN: Rooted trees

```
DEFINICE: Kořenový strom
Strom s jedním vyznačeným uzlem = kořen (nahoře).
EN: Rooted tree

             [1]          ← kořen (Root),   hloubka 0
            /   \
          [2]   [3]       ← vnitřní uzly,   hloubka 1
         /   \     \
       [4]  [5]   [6]     ← listy (Leaves), hloubka 2

Výška stromu = 2  (max hloubka listu)
```

**Pojmy:**

| Pojem | Příklad výše | EN |
|---|---|---|
| Kořen | [1] | Root |
| List | [4],[5],[6] | Leaf |
| Hloubka uzlu [3] | 1 | Depth |
| Výška stromu | 2 | Height |
| Rodič [2] | [1] | Parent |
| Potomci [2] | [4],[5] | Children |

**Typy stromů:**
```
Binární strom:         každý uzel max 2 potomci
         [1]
        /   \
      [2]   [3]
      /
    [4]

Pravidelný (k-ární):   každý vnitřní uzel má přesně k potomků
         [1]           (zde k=2, ale [3] nemá potomky → NENÍ pravidelný)

Úplný binární strom:   všechny listy ve stejné hloubce
         [1]
        /   \
      [2]   [3]
     / \   / \
   [4][5][6][7]    ← všichni ve hloubce 2 ✓
```

---

### 10. Reprezentace grafů v paměti
EN: Graph representation

```
Pracovní graf pro příklady:
        A ——— B
        |     |
        C ——— D

V = {A,B,C,D},  E = {AB, AC, BD, CD}
```

**1. Matice sousednosti:**
EN: Adjacency matrix

```
     A  B  C  D
A  [ 0  1  1  0 ]
B  [ 1  0  0  1 ]
C  [ 1  0  0  1 ]
D  [ 0  1  1  0 ]

M[i][j] = 1 pokud hrana existuje, jinak 0
Paměť: O(V²)  →  pro 4 uzly: 4×4 = 16 buněk
Výhoda: hrana (u,v)? → O(1)
Nevýhoda: plýtvá pamětí pro řídké grafy
```

**2. Matice incidence:**
EN: Incidence matrix

```
       AB  AC  BD  CD
A   [  1   1   0   0 ]
B   [  1   0   1   0 ]
C   [  0   1   0   1 ]
D   [  0   0   1   1 ]

Řádky = uzly, Sloupce = hrany
M[i][j] = 1 pokud uzel i leží na hraně j
Paměť: O(V · E)
```

**3. Seznam sousedů:**
EN: Adjacency list

```
A → [ B, C ]
B → [ A, D ]
C → [ A, D ]
D → [ B, C ]

Paměť: O(V + E)
Výhoda: efektivní pro řídké grafy
Nevýhoda: hrana (u,v)? → O(stupeň uzlu)
```

**Srovnání:**

| | Matice sousednosti | Seznam sousedů |
|---|---|---|
| Paměť | O(V²) | O(V+E) |
| Hrana (u,v)? | O(1) | O(stupeň) |
| Kdy použít | hustý graf | řídký graf |

---

### 11. Grafové algoritmy
EN: Graph algorithms

#### BFS — Prohledávání do šířky
EN: Breadth-First Search

```
IDEA: Nejdřív projdi všechny sousedy, pak sousedy sousedů.
Struktura: FRONTA (queue)
Složitost: O(V + E)
Použití: nejkratší cesta v neohodnoceném grafu
```

```
PŘÍKLAD — start z A:
        A ——— B ——— E
        |     |
        C ——— D

Fronta:  [A]
Krok 1:  odeber A → navštív B, C     Fronta: [B, C]
Krok 2:  odeber B → navštív D, E     Fronta: [C, D, E]
Krok 3:  odeber C → D již navštíven  Fronta: [D, E]
...

Pořadí: A → B → C → D → E
Vrstvy: A(0) | B,C(1) | D,E(2)
```

#### DFS — Prohledávání do hloubky
EN: Depth-First Search

```
IDEA: Jdi co nejhlouběji, pak se vrať a zkus jinou cestu.
Struktura: ZÁSOBNÍK nebo rekurze
Složitost: O(V + E)
Použití: detekce cyklů, topologické třídění
```

```
PŘÍKLAD — start z A:
        A ——— B ——— E
        |     |
        C ——— D

Zásobník: [A]
Krok 1: odeber A → push B, C         Zásobník: [B, C]
Krok 2: odeber C → push D            Zásobník: [B, D]
Krok 3: odeber D → push (B již vis.) Zásobník: [B]
Krok 4: odeber B → push E            Zásobník: [E]
Krok 5: odeber E

Pořadí: A → C → D → B → E   ← jde hlouběji dřív
```

#### Minimální kostra
EN: Minimum Spanning Tree (MST)

```
DEFINICE: Kostra s minimálním součtem vah hran.

PŘÍKLAD:
        A —2— B
        |  \  |
        4   3 5
        |    \|
        C —1— D

Hrany seřazené: CD(1), AB(2), AD(3), AC(4), BD(5)
```

**Kruskalův algoritmus:**
```
1. Seřaď hrany podle váhy.
2. Přidej hranu pokud nevytvoří cyklus.
3. Stop při |V|-1 hranách.

CD(1) → přidej ✓
AB(2) → přidej ✓
AD(3) → přidej ✓  (A,B,C,D spojeni → stop)

Výsledek — MST:
        A —2— B
              |
              3
              |
        C —1— D
Celková váha = 1+2+3 = 6
```

#### Dijkstrův algoritmus
EN: Dijkstra's algorithm

```
IDEA: Nejkratší cesty z jednoho uzlu do všech ostatních.
Podmínka: hrany musí mít NEZÁPORNÉ váhy.
Složitost: O((V+E) log V)
```

```
PŘÍKLAD — start z A:
        A —1— B
        |     |
        4     2
        |     |
        C —1— D

Start: dist = {A:0, B:∞, C:∞, D:∞}

Krok 1: vezmi A(0) → B: 0+1=1, C: 0+4=4
        dist = {A:0, B:1, C:4, D:∞}

Krok 2: vezmi B(1) → D: 1+2=3
        dist = {A:0, B:1, C:4, D:3}

Krok 3: vezmi D(3) → C: 3+1=4 (stejné, nez lepší)
        dist = {A:0, B:1, C:4, D:3}

Krok 4: vezmi C(4) → hotovo

Nejkratší cesty z A: B=1, C=4, D=3
```

#### Huffmanův kód
EN: Huffman coding

```
IDEA: Časté znaky → kratší kód. Méně časté → delší kód.
Výsledek: optimální prefixový kód (komprese)
Složitost: O(n log n)
```

```
PŘÍKLAD — znaky s frekvencemi:
A:5, B:2, C:1, D:3

Krok 1: Uzly seřazené: C(1), B(2), D(3), A(5)

Krok 2: Spoj 2 nejmenší: C(1)+B(2) = CB(3)
        Uzly: CB(3), D(3), A(5)

Krok 3: Spoj 2 nejmenší: CB(3)+D(3) = CBD(6)
        Uzly: A(5), CBD(6)

Krok 4: Spoj zbylé: A(5)+CBD(6) = root(11)

Výsledný strom:
            [11]
           /    \
         A(5)  [6]
         =0   /    \
           D(3)   [3]
           =10   /    \
               B(2)  C(1)
               =110  =111

Kódy: A=0, D=10, B=110, C=111
Časté A má nejkratší kód (1 bit) ✓
```

---

## Flashcards (ústní trénink)

**Q:** Co je ekvivalence? Jaké 3 vlastnosti musí mít?
**A:** Relace reflexivní + symetrická + tranzitivní. Příklad: "má stejný věk".

**Q:** Jaký je rozdíl mezi CNF a DNF?
**A:** CNF = AND klauzulí (každá OR). DNF = OR skupin (každá AND).

**Q:** Kdy je implikace p→q nepravdivá?
**A:** Pouze když p=1 a q=0.

**Q:** Co je podmínka Eulerova uzavřeného tahu?
**A:** Každý uzel grafu má sudý stupeň.

**Q:** Jaký je rozdíl mezi BFS a DFS?
**A:** BFS používá frontu (do šířky), DFS zásobník (do hloubky).

**Q:** Co je minimální kostra? Uveď algoritmus.
**A:** Kostra s minimálním součtem vah. Kruskal: seřaď hrany, přidávej nejlehčí bez cyklu.

**Q:** Proč Dijkstrův algoritmus nefunguje pro záporné hrany?
**A:** Předpokládá, že nejkratší cesta se jen prodlužuje — záporná hrana může zkrátit již "uzavřenou" cestu.

**Q:** Co je bijekce?
**A:** Zobrazení které je zároveň injekce (různé vstupy→různé výstupy) a surjekce (každý výstup má vzor).
