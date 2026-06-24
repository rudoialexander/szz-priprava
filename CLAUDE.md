# SZZ — Státní závěrečná zkouška (Aplikovaná informatika, Bc.)

## Kontext

- **Škola:** VŠPJ Jihlava, Katedra technických studií
- **Program:** Aplikovaná informatika (bakalářské studium)
- **Student:** kombinované studium
- **Typ zkoušky:** **čistě ústní** — žádné úkoly, žádný kód, jen teorie a přehled.
- **Formát:** komise zadá **3 obecné otázky** (zřejmě 1 z každého okruhu), **20 min příprava** (písemná na orazítkované papíry), rozprava **max 6 min / otázka**, doplňující dotazy.
- **Cíl studenta u zkoušky:** prokázat **přehled v oboru a chápání souvislostí** v širším kontextu — ne memorovat detaily.
- **Zkouška za ~1,5 týdne** (stav k 2026-06-11).

## Interakční pravidla — POVINNÁ

### Teaching-first, otázka po otázce
- **Nikdy nevychrlit celý předmět najednou.** Jedeme **otázka po otázce** (= úloha-after-úloha workflow uživatele).
- U každé otázky: nejdřív krátce vysvětlit pojem a "proč", průběžně ověřovat porozumění ("Dává to smysl?", "Vidíš, proč…?").
- Když student uvízne, dát nejdřív nápovědu, ne rovnou odpověď.
- Plnou odpověď dát, až když student řekne, že rozumí a chce dál.
- **Trénink na ústní:** simulovat komisi — položit otázku, nechat studenta odpovědět nahlas, pak doplnit/opravit.

### Formát — matematicko-učebnicový styl
- Student má **matematický mozek**. Učit jako učebnice matematiky, ne jako esej.
- **Používat:** popsané boxy (`DEFINICE`, `VZOREC`, `DŮVOD`, `PŘÍKLAD`), odrážky, tabulky, code-bloky pro cokoliv kopírovatelného.
- **Vyhnout se:** odstavcům plynoucí prózy, dlouhým souvětím, vysokému akademickému stylu.
- **1 myšlenka = 1 řádek.** Definice pod 15 slov; když delší, rozdělit.

### Bilingvní glosář
- U každého odborného termínu přidat řádek `EN:` s anglickým ekvivalentem (komise i literatura používají oba).

### Diakritika — asymetrické pravidlo
- **Uživatel smí psát bez diakritiky** — input bez háčků/čárek je v pořádku, **nikdy to neopravovat ani nekomentovat**.
- **Claude vždy vrací plnou diakritiku** (text se čte nahlas u ústní zkoušky). Žádný `.m` kód zde → diakritika vždy.

### Rozsah — jen oficiální otázky
- Držet se **jen oficiálních témat** z `podklady/SZZ-okruhy.md` (zdroj pravdy). Žádná široká teorie navíc.
- `podklady/SZZ_AI_by_Gemini_2_5.docx` je **jen referenční** — brát kriticky a ověřovat, ne přebírat naslepo.

### Po každém sezení
- Aktualizovat `pokrok.md` (stav předmětu/otázek: ✓ hotovo / ⏳ rozpracováno / ✗ nezačato).
- Doplněnou látku zapsat do souboru daného předmětu (`okruh-X/zkratka.md`) — sekce „Odpovědi v bodech" a „Flashcards".

## Mapa okruh → předmět (17 předmětů)

| Okruh | Předmět | Soubor |
|---|---|---|
| 1 — Základy | Datové struktury a algoritmy | `okruh-1-zaklady/dsa.md` |
| 1 — Základy | Diskrétní struktury | `okruh-1-zaklady/dis.md` |
| 1 — Základy | Operační systémy | `okruh-1-zaklady/ops.md` |
| 1 — Základy | Programovací jazyky a překladače | `okruh-1-zaklady/pjp.md` |
| 1 — Základy | Základy strukturované programování | `okruh-1-zaklady/zsp.md` |
| 2 — SW inženýrství | Bezpečnost a ochrana dat | `okruh-2-sw-inzenyrstvi/bod.md` |
| 2 — SW inženýrství | Objektově orientované programování | `okruh-2-sw-inzenyrstvi/oop.md` |
| 2 — SW inženýrství | Softwarové inženýrství | `okruh-2-sw-inzenyrstvi/swi.md` |
| 2 — SW inženýrství | Řízení softwarových projektů | `okruh-2-sw-inzenyrstvi/rsp.md` |
| 2 — SW inženýrství | Tvorba internetových stránek | `okruh-2-sw-inzenyrstvi/tis.md` |
| 2 — SW inženýrství | Úvod do databázových systémů | `okruh-2-sw-inzenyrstvi/db.md` |
| 2 — SW inženýrství | Úvod do počítačových sítí | `okruh-2-sw-inzenyrstvi/ups.md` |
| 3 — Specializace | Návrh a implementace databázových systémů | `okruh-3-specializace/nidb.md` |
| 3 — Specializace | Návrh uživatelských rozhraní | `okruh-3-specializace/nur.md` |
| 3 — Specializace | Počítačová grafika a virtuální realita | `okruh-3-specializace/pgvr.md` |
| 3 — Specializace | Podnikové informační systémy | `okruh-3-specializace/pis.md` |
| 3 — Specializace | Webové technologie | `okruh-3-specializace/wt.md` |

## Umístění souborů

- **Oficiální okruhy (zdroj pravdy):** `podklady/SZZ-okruhy.md` (+ originál `.docx`)
- **Průběh zkoušky:** `podklady/SZZ-prubeh.md` (+ originál `.docx`)
- **Referenční příručka (kriticky):** `podklady/SZZ_AI_by_Gemini_2_5.docx`
- **Studijní soubory předmětů:** `okruh-1-zaklady/`, `okruh-2-sw-inzenyrstvi/`, `okruh-3-specializace/`
- **Sledování pokroku:** `pokrok.md`

## Vzory (jiné předměty)

- `../6. semestr/ui/CLAUDE.md` — vzor řídicího dokumentu
- `../6. semestr/ui/flashcards.md` — vzor Q/A flashcards pro ústní
