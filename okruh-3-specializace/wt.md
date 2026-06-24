# WT — Webové technologie
**Okruh:** 3 — Specializace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Knihovna jQuery — možnosti použití při tvorbě www stránek.
2. AJAX — vlastnosti, příklady použití.
3. Architektura MVC — vysvětlení, výhody.
4. Framework Bootstrap — vlastnosti, použití, výhody.
5. Framework Symfony — využití při tvorbě webových aplikací, vlastnosti, výhody.
6. Twig — vlastnosti, použití.
7. Objektově-relační mapování (ORM, Doctrine) — mapování objektů na relační DB, výhody.

---
## Odpovědi v bodech

### 1. Knihovna jQuery
EN: *jQuery library*

```
DEFINICE
jQuery = JavaScriptová knihovna která zjednodušuje práci s HTML,
CSS a událostmi. Heslo: "Write less, do more."
```

| Funkce | Příklad |
|---|---|
| Výběr elementů | `$('#tlacitko')` |
| Změna obsahu | `$('p').text('Nový text')` |
| Změna stylu | `$('div').css('color', 'red')` |
| Události | `$('#btn').click(function(){...})` |
| AJAX | `$.ajax({...})` |
| Animace | `fadeIn()`, `slideDown()` |

---

### 2. AJAX
EN: *Asynchronous JavaScript and XML*

```
DEFINICE
AJAX = načtení dat ze serveru BEZ znovunačtení celé stránky.
```

- Bez AJAX: klik → celá stránka se znovu načte.
- S AJAX: klik → požadavek na pozadí → přijde jen část dat → aktualizace bez reloadu.

Příklady: našeptávač Google, ověření emailu, košík bez reloadu.

```javascript
$.ajax({ url: 'data.php', method: 'GET',
  success: function(odpoved) { $('#vysledek').html(odpoved); }
});
// moderní alternativa: fetch('data.php').then(r => r.json())
```

---

### 3. Architektura MVC
EN: *Model-View-Controller*

```
DEFINICE
MVC = vzor dělící aplikaci na 3 části. Odděluje data, logiku a zobrazení.
```

| Část | Zodpovědnost |
|---|---|
| Model | data a business logika (DB, výpočty) |
| View | zobrazení (HTML šablona) |
| Controller | přijme požadavek, rozhodne co se stane |

Tok: `Uživatel → Controller → Model → View → Uživatel`

**Výhody:** jasné zodpovědnosti, snadné testování, paralelní práce týmu, znovupoužitelnost.

---

### 4. Framework Bootstrap
EN: *Bootstrap CSS framework*

```
DEFINICE
Bootstrap = CSS/JS framework pro rychlý vývoj responzivních webů.
```

- Grid systém: 12 sloupců, prefixy `col-md-X`.
- Komponenty: Navbar, Card, Modal, Button, Alert, Form.
- Utility třídy: `text-center`, `mt-3`, `bg-primary`.

**Výhody:** rychlý vývoj, responzivní bez psaní CSS, konzistentní vzhled, velká komunita.

---

### 5. Framework Symfony
EN: *Symfony PHP framework*

```
DEFINICE
Symfony = PHP framework pro webové aplikace. Architektura MVC. Modulární.
```

| Vlastnost | Popis |
|---|---|
| Routing | mapování URL na Controller |
| Dependency Injection | automatické dodání závislostí |
| Formuláře | tvorba a validace v PHP |
| Bezpečnost | autentizace, autorizace, CSRF |
| ORM | integrace s Doctrine |
| Šablony | Twig |

Struktura: `src/Controller/` (C), `src/Entity/` (M), `templates/` (V).

**Výhody:** velká komunita, znovupoužitelné komponenty, vhodný pro velké projekty.

---

### 6. Twig
EN: *Twig template engine*

```
DEFINICE
Twig = šablonovací systém pro PHP. Odděluje HTML od logiky (View). Používá Symfony.
```

| Zápis | Účel |
|---|---|
| `{{ proměnná }}` | výpis hodnoty |
| `{% tag %}` | logika (if, for, block) |
| `{# komentář #}` | komentář |

```twig
{% if vek >= 18 %}<p>Dospělý</p>{% else %}<p>Nezletilý</p>{% endif %}
{% for u in uzivatele %}<li>{{ u.jmeno }}</li>{% endfor %}
```

**Dědičnost šablon:** základní šablona s `{% block %}`, podšablony přes `{% extends %}` přepisují bloky.

---

### 7. Objektově-relační mapování (ORM, Doctrine)
EN: *Object-Relational Mapping*

```
PROBLÉM: OOP pracuje s objekty, DB s tabulkami. Ruční převod = zdlouhavé.
ŘEŠENÍ: ORM = vrstva která převod dělá automaticky.
```

Mapování: PHP třída ↔ tabulka, vlastnost ↔ sloupec, objekt ↔ řádek.

```php
// místo SQL píšeš PHP:
$uzivatel = $entityManager->find(Uzivatel::class, 5);
echo $uzivatel->getJmeno();
```

**Doctrine** = nejpoužívanější ORM pro PHP, integrován v Symfony.
- Entita = PHP třída mapovaná na tabulku (atributy `#[Entity]`, `#[Column]`).
- Doctrine automaticky převádí objekty na SQL a zpět.

**Výhody:** píšeš PHP místo SQL, nezávislost na konkrétní DB, čitelnější a snadněji udržovatelný kód.

## Flashcards (ústní trénink)
**Q: Co je jQuery a k čemu slouží?**
A: JavaScriptová knihovna zjednodušující práci s HTML, CSS, událostmi a AJAX. Heslo "write less, do more".

**Q: Co je AJAX a jaká je jeho hlavní výhoda?**
A: Technika načtení dat ze serveru bez znovunačtení celé stránky. Stránka se aktualizuje plynule na pozadí.

**Q: Co je MVC a z jakých částí se skládá?**
A: Návrhový vzor dělící aplikaci na Model (data/logika), View (zobrazení), Controller (řízení požadavku).

**Q: Jaké jsou výhody frameworku Symfony?**
A: MVC architektura, znovupoužitelné komponenty, routing, dependency injection, integrace s Doctrine a Twig.

**Q: Co je Twig a proč se používá?**
A: Šablonovací systém pro PHP oddělující HTML od logiky. Podporuje proměnné, podmínky, cykly a dědičnost šablon.

**Q: Co je ORM a jaké má výhody?**
A: Objektově-relační mapování — automatický převod mezi objekty a DB tabulkami. Píšeš PHP místo SQL, nezávislost na DB. Doctrine je ORM pro PHP.

**Q: Co je Doctrine?**
A: Nejpoužívanější ORM pro PHP, integrovaný v Symfony. Mapuje entity (PHP třídy) na databázové tabulky.
