# NUR — Návrh uživatelských rozhraní
**Okruh:** 3 — Specializace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Návrhy rozhraní pro Windows aplikace.
2. Layouty webových stránek.
3. Návrhy webdesignu a řešení pro webové aplikace.
4. Bootstrap.

---
## Odpovědi v bodech

### 1. Návrhy rozhraní pro Windows aplikace
EN: *Windows application UI design*

```
DEFINICE
GUI = Graphical User Interface = grafické rozhraní ovládané myší/klávesnicí.
Windows aplikace se řídí standardy Microsoftu (Fluent Design System).
```

**Základní prvky Windows UI:**
| Prvek | EN | Použití |
|---|---|---|
| Okno | *window* | hlavní kontejner aplikace |
| Tlačítko | *button* | spuštění akce |
| Textové pole | *text box* | vstup textu |
| Zaškrtávací pole | *checkbox* | ano/ne volba |
| Přepínač | *radio button* | výběr jedné z možností |
| Rozbalovací seznam | *dropdown* | výběr z více možností |
| Nabídka | *menu* | skupiny příkazů |
| Panel nástrojů | *toolbar* | rychlý přístup k akcím |

**Principy:** Konzistence · Zpětná vazba · Přístupnost EN: *accessibility* · Minimalizace chyb.

---

### 2. Layouty webových stránek
EN: *Web page layouts*

| Typ | Popis |
|---|---|
| Fixní EN: *fixed* | pevná šířka v px |
| Fluidní EN: *fluid* | šířka v %, přizpůsobuje se |
| Responzivní EN: *responsive* | mění strukturu podle breakpointů |
| Adaptivní EN: *adaptive* | různé pevné layouty pro různá zařízení |

**Struktura stránky:** Header · Nav · Content · Footer

**CSS techniky:**
- Flexbox = 1D layout (řádek nebo sloupec)
- CSS Grid = 2D layout (řádky i sloupce)

**Breakpointy:** < 576px = mobil · 576–768px = tablet · > 992px = desktop

---

### 3. Návrhy webdesignu a řešení pro webové aplikace
EN: *Web design and web application solutions*

| Princip | Výklad |
|---|---|
| Hierarchie EN: *visual hierarchy* | důležité prvky jsou větší/výraznější |
| Bílý prostor EN: *white space* | prázdné místo = čitelnost |
| Kontrast | min. poměr 4,5:1 (WCAG) |
| Zarovnání EN: *alignment* | prvky jsou vizuálně svázané osami |

**Typografie:** Sans-serif pro web · min. 16px · řádkování 1,4–1,6×

**UX patterns:**
- Breadcrumbs = navigační drobečky
- Lazy loading = obsah se načítá při scrollu
- Skeleton screen = kostra obsahu místo spinneru
- Infinite scroll = nový obsah při scrollu dolů

---

### 4. Bootstrap
EN: *Bootstrap CSS framework*

```
DEFINICE
Bootstrap = open-source CSS/JS framework pro responzivní weby.
Vytvořen Twitterem. Nejrozšířenější CSS framework.
```

**Grid systém:** 12 sloupců · `container` → `row` → `col-md-X`

| Prefix | Breakpoint |
|---|---|
| `col-` | < 576px |
| `col-sm-` | ≥ 576px |
| `col-md-` | ≥ 768px |
| `col-lg-` | ≥ 992px |

**Komponenty:** Navbar · Card · Modal · Button · Form · Alert

**Utility třídy:** `text-center` · `text-danger` · `bg-primary` · `mt-3` · `px-2`

## Flashcards (ústní trénink)
**Q: Co je Bootstrap a proč se používá?**
A: Open-source CSS framework pro rychlý vývoj responzivních webů. Poskytuje hotový grid systém, komponenty a utility třídy.

**Q: Jak funguje Bootstrap grid systém?**
A: Stránka = 12 sloupců. Prvky zabírají 1–12 sloupců. Responzivní prefixy (col-md-8) určují počet sloupců pro danou velikost obrazovky.

**Q: Jaký je rozdíl mezi responzivním a adaptivním layoutem?**
A: Responzivní = plynule mění strukturu podle breakpointů. Adaptivní = různé pevné layouty pro různá zařízení.

**Q: Jaké jsou základní principy webdesignu?**
A: Vizuální hierarchie, bílý prostor, kontrast (min 4,5:1), zarovnání.

**Q: Jaké jsou základní prvky Windows GUI?**
A: Okno, tlačítko, textové pole, checkbox, radio button, dropdown, menu, toolbar.
