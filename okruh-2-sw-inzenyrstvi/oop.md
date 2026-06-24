# OOP — Objektově orientované programování
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Principy objektového programování, třídy a jejich použití.
2. Struktura objektu — atributy a metody.
3. Dynamický charakter objektu — konstruktor, destruktor, instance třídy.
4. Kopírovací a přesunující operace.
5. Přetěžování metod, přetěžování operátorů.
6. Dědičnost, hierarchie tříd, kompozice.
7. Abstraktní třídy, polymorfismus, virtuální metody.
8. Výjimky a jejich zpracování.
9. Abstraktní datové typy, základní knihovny.
10. Staticky a dynamicky vázané metody.
11. Šablony, knihovna STL.
12. Soubory a proudy.

---
## Odpovědi v bodech

### 1. Principy OOP, třídy a jejich použití

**4 pilíře:**
```
Zapouzdření   → data + metody v jednom objektu, skryté vnitřnosti
Dědičnost     → třída přebírá vlastnosti jiné třídy
Polymorfismus → stejné volání, různé chování podle typu objektu
Abstrakce     → skryj detail, ukaž jen co je potřeba
EN: encapsulation / inheritance / polymorphism / abstraction
```

```cpp
Třída  = šablona (blueprint)     → Auto
Objekt = instance třídy          → auto1 = new Auto()
```

---

### 2. Struktura objektu — atributy a metody

```cpp
class Auto {
private:                          // jen uvnitř třídy
  string barva;
  int rychlost;
public:                           // přístupné zvenku
  void jeď() { ... }
  int getRychlost() { return rychlost; }
  void setRychlost(int r) { rychlost = r; }
};
```

**Přístupová práva:** `private` → jen třída, `protected` → třída + potomci, `public` → kdekoliv

---

### 3. Konstruktor, destruktor, instance

```cpp
class Auto {
public:
  Auto(string b) { barva = b; }   // konstruktor — volá se při vytvoření
  ~Auto() { ... }                  // destruktor — volá se při zániku
};

Auto a("červená");   // volá konstruktor
// konec scope → volá destruktor
```

- Konstruktor: stejné jméno jako třída, bez návratového typu
- Destruktor: `~` před jménem, uvolňuje paměť

---

### 4. Kopírovací a přesunující operace

```cpp
Auto(const Auto& other) { ... }   // copy constructor — oba objekty existují
Auto(Auto&& other) { ... }        // move constructor — originál se vyprázdní

Auto a2 = a1;              // copy
Auto a2 = std::move(a1);   // move — a1 už není platný, rychlejší
```

---

### 5. Přetěžování metod a operátorů

```cpp
// Přetěžování metod — stejné jméno, různé parametry:
void tiskni(int x) { ... }
void tiskni(string s) { ... }

// Přetěžování operátorů:
Auto operator+(const Auto& other) { ... }
auto3 = auto1 + auto2;    // ✓
```
Nelze přetížit: `:: . .* ?:`

---

### 6. Dědičnost, hierarchie tříd, kompozice

```cpp
class Auto : public Vozidlo { }   // Auto JE Vozidlo (dědičnost)

class Auto {
  Motor motor;                     // Auto MÁ Motor (kompozice)
};
```

```
Vozidlo → Auto → OsobníAuto
                → SUV
        → Motocykl
```

**Pravidlo:** preferuj kompozici před dědičností → méně závislostí

---

### 7. Abstraktní třídy, polymorfismus, virtuální metody

```cpp
class Vozidlo {
  virtual void zvuk() = 0;        // čistě virtuální → abstraktní třída
  virtual void jeď() { ... }      // virtuální s implementací
};

Vozidlo v;    // ✗ nelze instanciovat!
Auto a;       // ✓ implementuje zvuk()
```

**Polymorfismus:**
```cpp
Vozidlo* v = new Auto();
v->zvuk();    // volá Auto::zvuk() — runtime rozhodnutí!
```
> Stejné volání → různé chování podle skutečného typu objektu.

---

### 8. Výjimky a jejich zpracování

```cpp
try {
  if (b == 0) throw runtime_error("dělení nulou!");
  int r = a / b;
} catch (runtime_error& e) {
  cout << e.what();
} catch (...) {
  // zachytí vše
}
```

**Hierarchie:** `exception` → `runtime_error`, `logic_error`, `invalid_argument`...

---

### 9. Abstraktní datové typy, základní knihovny

- ADT = datový typ definovaný operacemi, ne implementací
- Příklady: Stack (push/pop), Queue (enqueue/dequeue), List
- Implementace skryta → uživatel zná jen rozhraní

---

### 10. Staticky a dynamicky vázané metody

```
Statická vazba:   bez virtual → překladač rozhodne → rychlejší
Dynamická vazba:  s virtual   → runtime rozhodne   → flexibilní

vtable = tabulka virtuálních metod každé třídy
```

```cpp
Vozidlo* v = new Auto();
v->zvuk();   // bez virtual → "vroom" (Vozidlo)
             // s virtual   → "beep"  (Auto)
```

---

### 11. Šablony, knihovna STL

```cpp
template <typename T>
T max(T a, T b) { return a > b ? a : b; }   // funguje pro jakýkoliv typ
```

**STL kontejnery:**
| Kontejner | Popis |
|---|---|
| `vector<T>` | dynamické pole, O(1) přístup |
| `list<T>` | spojový seznam |
| `map<K,V>` | klíč → hodnota, O(log n) |
| `set<T>` | unikátní hodnoty |
| `stack<T>` | LIFO |
| `queue<T>` | FIFO |

---

### 12. Soubory a proudy

```cpp
ofstream f("data.txt");
f << "text" << endl;
f.close();

ifstream f("data.txt");
string line;
while (getline(f, line)) { cout << line; }
f.close();
```

**Přetížení <<:**
```cpp
ostream& operator<<(ostream& os, const Auto& a) {
  os << a.barva; return os;
}
cout << auto1;   // "červená"
```

---

## Flashcards

**Q:** 4 pilíře OOP?
**A:** Zapouzdření, dědičnost, polymorfismus, abstrakce.

**Q:** Co je polymorfismus?
**A:** Stejné volání, různé chování podle skutečného typu objektu za běhu. Funguje díky `virtual`.

**Q:** Rozdíl abstraktní třída vs. normální?
**A:** Abstraktní má aspoň 1 čistě virtuální metodu (`= 0`), nelze ji instanciovat.

**Q:** Rozdíl copy vs. move constructor?
**A:** Copy = oba objekty existují. Move = originál se vyprázdní, rychlejší.

**Q:** Statická vs. dynamická vazba?
**A:** Statická = bez virtual, rozhodne překladač. Dynamická = s virtual, rozhodne runtime.

**Q:** Dědičnost vs. kompozice?
**A:** Dědičnost = "je" (Auto JE Vozidlo). Kompozice = "má" (Auto MÁ Motor). Preferuj kompozici.
