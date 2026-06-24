# PGVR — Počítačová grafika a virtuální realita
**Okruh:** 3 — Specializace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Obraz — reprezentace a zobrazovací řetězec, barevné modely.
2. Algoritmizace 2D objektů; modelování křivek, ploch a těles.
3. Promítání, viditelnost, textury a světlo ve scéně.
4. Globální zobrazovací metody.
5. Virtuální realita, tvorba 3D modelů, prezentační vrstvy simulačních nástrojů.

---
## Odpovědi v bodech

### 1. Obraz — reprezentace a zobrazovací řetězec, barevné modely
EN: *Image representation, rendering pipeline, colour models*

| Typ | Popis | Příklad |
|---|---|---|
| Rastrová EN: *raster* | mřížka pixelů | PNG, JPG |
| Vektorová EN: *vector* | matematické křivky | SVG, PDF |

Rastrová: kvalita závisí na DPI, zvětšení = rozmazání.
Vektorová: lze libovolně zvětšit bez ztráty kvality.

**Zobrazovací řetězec** EN: *rendering pipeline*
`3D model → transformace → projekce → rasterizace → displej`

**Barevné modely:**
| Model | Použití |
|---|---|
| RGB | displeje, web (aditivní — 0,0,0=černá) |
| CMYK | tisk (subtraktivní — vše=černá) |
| HSV/HSL | výběr barev v editorech |

---

### 2. Algoritmizace 2D objektů; modelování křivek, ploch a těles
EN: *2D object algorithms; curves, surfaces and solids modelling*

```
PROBLÉM: objekt je spojitý, displej je mřížka pixelů.
ŘEŠENÍ: algoritmus určí které pixely leží na objektu.
```
- Bresenhamův algoritmus = kreslení úsečky, pouze celočíselná aritmetika.
- Midpoint algoritmus = kreslení kružnice na rastru.

**Křivky:**
- Bézierova křivka = řídicí body; kubická má 4 body (prochází krajními).
- B-spline = zobecnění Bézierovy; lokální kontrola tvaru.
- NURBS = standard v CAD.

**Tělesa:**
- Povrchové modelování = pouze povrch.
- Objemové modelování = plné těleso s objemem.
- CSG EN: *Constructive Solid Geometry* = kombinace operacemi (sjednocení, průnik, rozdíl).

---

### 3. Promítání, viditelnost, textury a světlo ve scéně
EN: *Projection, visibility, textures and lighting*

**Promítání:**
- Rovnoběžné EN: *orthographic* = paprsky rovnoběžné, vzdálené se nezmenšuje.
- Perspektivní EN: *perspective* = vychází z jednoho bodu, vzdálené je menší (realistické).

**Viditelnost:**
- Z-buffer = pro každý pixel pamatuj nejbližší hloubku, vzdálenější zahoď.
- Painter's algorithm = kresli od nejdál k nejblíž.

**Textury:** 2D obrázek natažený na 3D povrch. UV mapování = jak se textura mapuje.

**Světlo:**
| Typ | Popis |
|---|---|
| Ambientní | rovnoměrné ze všech stran |
| Bodové | z jednoho bodu do všech směrů |
| Směrové | rovnoběžné paprsky (slunce) |
| Reflektor | kužel světla |

Phongův model = ambientní + difúzní + spekulární složka.

---

### 4. Globální zobrazovací metody
EN: *Global rendering methods*

```
Lokální metody = jen přímé světlo.
Globální metody = odrazy, stíny, průhlednost — realistické.
```

**Ray Tracing** = paprsek z kamery pro každý pixel → sleduje odrazy a lomy.
- Výhody: realistické odrazy, stíny, průhlednost.
- Nevýhody: pomalé.

**Radiozita** EN: *Radiosity* = světelná energie se přerozděluje mezi plochy.
- Výhody: měkké stíny, difúzní osvětlení.
- Nevýhody: jen matné povrchy, pomalé.

| | Ray Tracing | Radiozita |
|---|---|---|
| Odrazy | ✓ | ✗ |
| Měkké stíny | ✗ | ✓ |

---

### 5. Virtuální realita, tvorba 3D modelů, prezentační vrstvy simulačních nástrojů
EN: *VR, 3D modelling, simulation tools*

| Typ | Popis |
|---|---|
| VR | plně umělé prostředí (headset) |
| AR | reálný svět + digitální prvky |
| MR | digitální objekty interagují s reálným světem |

Klíčové: stereoskopický obraz · tracking · latence < 20 ms.

**Tvorba 3D modelů:**
- Polygonální EN: *polygon mesh* = síť trojúhelníků, nejběžnější.
- NURBS = přesné křivky, pro CAD.
- Sculpting = organické tvary, jako hlína.
- Procedurální = model generován algoritmem.

**Simulační nástroje:** 2D grafy → 3D vizualizace → VR/AR vrstva (piloti, lékaři).

## Flashcards (ústní trénink)
**Q: Jaký je rozdíl mezi rastrovou a vektorovou grafikou?**
A: Rastrová = mřížka pixelů, závisí na rozlišení. Vektorová = matematické křivky, lze zvětšit bez ztráty kvality.

**Q: Co je rendering pipeline?**
A: Zobrazovací řetězec: 3D model → transformace → projekce → rasterizace → displej.

**Q: Jaký je rozdíl mezi RGB a CMYK?**
A: RGB = aditivní míchání světla (displeje). CMYK = subtraktivní míchání inkoustu (tisk).

**Q: Co je Z-buffer?**
A: Algoritmus viditelnosti — pro každý pixel pamatuj nejmenší hloubku, vzdálenější plochy zahoď.

**Q: Jaký je rozdíl mezi ray tracingem a radiozitou?**
A: Ray tracing = sleduje paprsky, realistické odrazy a stíny. Radiozita = přerozděluje světelnou energii, měkké difúzní osvětlení.

**Q: Co je VR a jak se liší od AR?**
A: VR = plně umělé prostředí. AR = reálný svět doplněný digitálními prvky.
