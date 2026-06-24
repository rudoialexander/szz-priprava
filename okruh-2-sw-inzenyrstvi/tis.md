# TIS — Tvorba internetových stránek
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. WWW stránky — základní části, tagy, validace, HTML.
2. HTML5 — vlastnosti, použití.
3. Kaskádové styly (CSS) — třídy, základní vlastnosti, použití.
4. Pozicování pomocí kaskádových stylů.
5. Formuláře a jejich kontrola, regulární výrazy.
6. Přístup k databázi pomocí PHP a práce s daty.
7. Zabezpečení www stránek — cookies, session.

---
## Odpovědi v bodech

### 1–2. HTML, HTML5

```html
<!DOCTYPE html>
<html>
  <head><title>Stránka</title></head>
  <body>
    <h1>Nadpis</h1>
    <p>Odstavec</p>
    <a href="url">Odkaz</a>
    <img src="foto.jpg" alt="popis">
  </body>
</html>
```

**HTML5 novinky:**
```
Sémantické tagy:  <header> <nav> <main> <footer> <article>
Multimédia:       <video> <audio> <canvas>
Formuláře:        type="email" "date" "range" "color"
Lokální úložiště: localStorage, sessionStorage
```

---

### 3. CSS — kaskádové styly

**Box model:** margin → border → padding → content

**Selektory:**
```css
p { }        /* element */
.trida { }   /* třída */
#id { }      /* ID */
```

**Kaskáda — priorita:** `!important` > inline > ID > třída > element

---

### 4. Pozicování CSS

```css
position: static;    /* výchozí — normální tok */
position: relative;  /* posun od původní pozice */
position: absolute;  /* vůči nejbližšímu rodiči */
position: fixed;     /* fixní vůči oknu prohlížeče */
position: sticky;    /* relative + fixed kombinace */
```

**Flexbox:**
```css
display: flex;
justify-content: center;   /* horizontální */
align-items: center;       /* vertikální */
```

**Grid:**
```css
display: grid;
grid-template-columns: 1fr 1fr 1fr;
```

**Media queries:**
```css
@media (max-width: 768px) { /* mobilní styly */ }
```

---

### 5. Formuláře a regulární výrazy

```html
<form method="POST">
  <input type="text" required>
  <input type="email">
  <input type="password">
  <button type="submit">Odeslat</button>
</form>
```

**Regex základy:**
```
.       → libovolný znak
*       → 0 nebo více
+       → 1 nebo více
[a-z]   → malé písmeno
\d      → číslice
^       → začátek
$       → konec

Email: ^[\w.]+@[\w.]+\.[a-z]{2,}$
```

---

### 6. PHP a přístup k databázi

```php
// Připojení:
$pdo = new PDO("mysql:host=localhost;dbname=db", "user", "pass");

// SELECT:
$stmt = $pdo->prepare("SELECT * FROM uzivatele WHERE id = ?");
$stmt->execute([$id]);
$radky = $stmt->fetchAll();

// INSERT:
$stmt = $pdo->prepare("INSERT INTO uzivatele (jmeno) VALUES (?)");
$stmt->execute([$jmeno]);
```

**Prepared statements** → ochrana proti SQL injection!

---

### 7. Zabezpečení — cookies, session

**Cookie** = data v prohlížeči (klient)
```php
setcookie("uzivatel", "Jan", time() + 3600);
// Atributy: HttpOnly, Secure, SameSite
```

**Session** = data na serveru (bezpečnější)
```php
session_start();
$_SESSION["id"] = 42;
session_destroy();
```

**Hrozby:**
```
XSS         → escapovat výstup (htmlspecialchars())
SQL Injection → prepared statements
CSRF        → CSRF token v každém formuláři
Session Hijacking → HTTPS + HttpOnly + regenerace ID
```

---

## Flashcards

**Q:** Rozdíl cookie vs. session?
**A:** Cookie = data v prohlížeči. Session = data na serveru, bezpečnější.

**Q:** Proč používat prepared statements?
**A:** Ochrana před SQL injection — parametry se escapují automaticky.

**Q:** Co je XSS?
**A:** Útočník vloží JS do stránky, spustí se v prohlížeči oběti. Obrana: htmlspecialchars().

**Q:** Rozdíl position absolute vs. fixed?
**A:** Absolute = pozice vůči rodiči. Fixed = fixní vůči oknu, zůstane i při scrollování.

**Q:** HTML5 sémantické tagy?
**A:** header, nav, main, footer, article, section.
