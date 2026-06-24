# ZSP — Základy strukturovaného programování
**Okruh:** 1 — Základy informatiky &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Algoritmus, program, proces.
2. Překladač, interpret, preprocesor.
3. Reprezentace dat v paměti, základní datové typy, proměnné, konstanty, přetypování.
4. Operátory a jejich priorita, výrazy.
5. Základní příkazy; řízení běhu programu — řídicí struktury.
6. Datový typ ukazatel.
7. Funkce a procedury — návratový typ, formální a skutečné parametry, předání hodnotou a referencí.
8. Rozklad problému na podproblémy, procedurální přístup, rekurze.
9. Jednorozměrná a vícerozměrná pole; řetězce.
10. Standardní vstup/výstup, práce se soubory — binární a textové soubory.
11. Strukturované datové typy; dynamické datové struktury.
12. Modulární programování, hlavičkové soubory.

---
## Odpovědi v bodech

### 1. Algoritmus, program, proces

**DEFINICE**
- **Algoritmus** = konečná posloupnost kroků řešící problém (nezávislý na jazyce)
- **Program** = algoritmus zapsaný v programovacím jazyce
- **Proces** = program právě běžící na CPU (má paměť, stav)
EN: algorithm / program / process

```
Algoritmus → zapíšeš → Program → spustíš → Proces
(idea)                  (kód)               (běh)
```

**Vlastnosti algoritmu:**
| Vlastnost | Popis |
|---|---|
| Konečnost | skončí po konečném počtu kroků |
| Determinismus | stejný vstup → stejný výstup |
| Vstup/výstup | má definované vstupy a výstupy |
| Obecnost | řeší celou třídu problémů |

---

### 2. Překladač, interpret, preprocesor

**DEFINICE**
- **Překladač** = přeloží celý zdrojový kód → strojový kód (před spuštěním)
- **Interpret** = čte a vykonává kód řádek po řádku (za běhu)
- **Preprocesor** = upraví zdrojový kód před překladem (makra, include)
EN: compiler / interpreter / preprocessor

| | Překladač | Interpret |
|---|---|---|
| Kdy překládá | před spuštěním | za běhu |
| Rychlost běhu | rychlejší | pomalejší |
| Příklad | C, C++ | Python, JS |

```c
#include <stdio.h>    // preprocesor: vloží soubor
#define MAX 100       // preprocesor: nahradí MAX číslem
```

---

### 3. Reprezentace dat, datové typy, přetypování

**Základní datové typy:**
| Typ | Velikost | Popis |
|---|---|---|
| `char` | 1 B | znak |
| `int` | 4 B | celé číslo |
| `float` | 4 B | desetinné číslo |
| `double` | 8 B | desetinné, přesnější |
| `bool` | 1 B | true / false |

- **Proměnná** = pojmenované místo v paměti, hodnota se mění
- **Konstanta** = hodnota se nemění (`const int MAX = 100`)
EN: variable / constant

**Přetypování:**
```c
int x = 5;
float y = (float) x;      // explicitní
float z = x;              // implicitní
// příklad: (float) 5 / 2 = 2.5 místo 5/2 = 2
```
EN: type casting

---

### 4. Operátory a výrazy

| Typ | Příklady |
|---|---|
| Aritmetické | `+ - * / %` |
| Porovnávací | `== != < > <= >=` |
| Logické | `&& || !` |
| Přiřazení | `= += -= *=` |

**Priorita (od nejvyšší):** `()` → `! ++ --` → `* / %` → `+ -` → `< >` → `== !=` → `&&` → `||` → `=`

```c
int x = 3 + 4 * 2;   // = 11 (* má vyšší prioritu než +)
```

---

### 5. Řídící struktury

```
1. Sekvence   → příkazy za sebou
2. Větvení    → if / else / switch
3. Cyklus     → for / while / do-while
```
EN: control structures

```c
for (int i = 0; i < 10; i++)   // známý počet opakování
while (x > 0)                   // podmínka na začátku
do { ... } while (x > 0)        // podmínka na konci (min. 1x)
```

- `while` — podmínka se ověří před prvním průchodem
- `do-while` — tělo se provede vždy aspoň jednou

---

### 6. Ukazatele

**DEFINICE**
Ukazatel = proměnná která uchovává adresu jiné proměnné.
EN: pointer

```c
int x = 5;
int *p = &x;   // p = adresa x
*p → 5         // hodnota na adrese p
```

| Operátor | Čti jako | Vrátí |
|---|---|---|
| `&x` | „adresa x" | číslo adresy |
| `*p` | „hodnota na adrese p" | hodnotu |

```c
int *p = NULL;   // ukazatel nikam — bezpečná výchozí hodnota
```

---

### 7. Funkce a procedury

- **Funkce** = pojmenovaný blok kódu, vrací hodnotu
- **Procedura** = pojmenovaný blok kódu, nevrací hodnotu (`void`)
EN: function / procedure

| Typ předání | Co se předá | Změní originál? |
|---|---|---|
| Hodnotou | kopie hodnoty | ✗ ne |
| Referencí | adresa proměnné | ✓ ano |

```c
void hodnotou(int x) { x = 99; }     // originál se nezmění
void referencí(int *x) { *x = 99; }  // originál se změní
```

- **Formální parametry** = v definici funkce
- **Skutečné parametry** = hodnoty při volání
EN: pass by value / pass by reference

---

### 8. Rekurze

**DEFINICE**
Rekurze = funkce volá sama sebe.
EN: recursion

**Podmínky:**
1. **Základní případ** (base case) — kdy se přestane volat
2. **Rekurzivní případ** — zjednodušuje problém

```c
int fact(int n) {
    if (n == 0) return 1;       // základní případ
    return n * fact(n - 1);     // rekurzivní případ
}
```

| | Rekurze | Iterace |
|---|---|---|
| Čitelnost | lepší | horší |
| Paměť | více (zásobník) | méně |

---

### 9. Pole a řetězce

**Pole:**
```c
int arr[5] = {1, 2, 3, 4, 5};   // indexuje se od 0
int mat[3][3];                    // vícerozměrné (matice)
```
- Přístup mimo hranice → **undefined behavior**
EN: array

**Řetězec** = pole znaků ukončené `\0`
EN: string

```c
char s[] = "ahoj";
// v paměti: ['a']['h']['o']['j']['\0']
```

| Funkce | Co dělá |
|---|---|
| `strlen(s)` | délka |
| `strcmp(s1, s2)` | porovnání (0 = stejné) |
| `strcpy(dst, src)` | kopie |

```c
s1 == s2            // ✗ porovnává adresy!
strcmp(s1, s2) == 0 // ✓ porovnává obsah
```

---

### 10. Vstup/výstup, soubory

- **Textový soubor** = čitelný text (txt, md)
- **Binární soubor** = surové bajty (obrázky, exe)
EN: text file / binary file

```c
FILE *f = fopen("data.txt", "r");
fscanf(f, "%d", &x);
fclose(f);
```

| Mód | Co dělá |
|---|---|
| `"r"` | čtení |
| `"w"` | zápis (přepíše) |
| `"a"` | přidání na konec |
| `"rb"` | čtení binárně |

---

### 11. Strukturované typy a dynamické struktury

**Struct:**
```c
struct Osoba {
    char jmeno[50];
    int vek;
};
```

**Dynamická alokace:**
```c
int *p = malloc(10 * sizeof(int));  // alokuj
free(p);                             // uvolni — jinak memory leak!
```
EN: malloc / free / memory leak

**Linked list:**
```
[1] → [2] → [3] → NULL
```

---

### 12. Modulární programování

- Kód rozdělen do souborů (`.c` + `.h`)
- `.h` = hlavičkový soubor = deklarace funkcí
- `.c` = implementace
EN: modular programming / header files

---

## Flashcards (ústní trénink)

**Q:** Rozdíl algoritmus / program / proces?
**A:** Algoritmus = idea, program = kód, proces = běžící program na CPU.

**Q:** Překladač vs. interpret?
**A:** Překladač přeloží vše předem (C), interpret řádek po řádku za běhu (Python).

**Q:** Kdy použít do-while místo while?
**A:** Když chci, aby se tělo provedlo aspoň jednou.

**Q:** Předání hodnotou vs. referencí?
**A:** Hodnotou = kopie, originál se nezmění. Referencí = adresa, originál se změní.

**Q:** Co musí mít každá rekurzivní funkce?
**A:** Základní případ (base case), jinak nekonečná smyčka.

**Q:** Proč nelze porovnat řetězce pomocí `==`?
**A:** Porovnává adresy, ne obsah. Použít `strcmp`.

**Q:** Proč volat `free()` po `malloc()`?
**A:** Bez free nastane memory leak — program postupně spotřebuje veškerou RAM.
