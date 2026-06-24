# BOD — Bezpečnost a ochrana dat
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Úvod do informační bezpečnosti, legislativa a normy.
2. Kryptografie — proudové šifry, blokové šifry.
3. Hashovací funkce a datová integrita.
4. Symetrické šifrování.
5. Asymetrické šifrování, výměna klíčů.
6. Digitální podpisy, identifikace a autentizace entity.
7. Certifikáty a certifikační autority; komerční/kvalifikované certifikáty, časová razítka.
8. Viry — historie a současnost; antivirové programy.
9. Chyby v programech, revize kódu, testování bezpečnosti.

---
## Odpovědi v bodech

### 1. Úvod do informační bezpečnosti, legislativa a normy

**CIA triáda:**
| Pilíř | EN | Meaning |
|---|---|---|
| Důvěrnost | Confidentiality | jen oprávnění vidí data |
| Integrita | Integrity | data nebyla změněna |
| Dostupnost | Availability | systém funguje kdy ho potřebuji |

**Normy:** ISO/IEC 27001, eIDAS, GDPR, Zákon 181/2014 Sb.

---

### 2. Kryptografie — proudové šifry, blokové šifry

```
KRYPTOGRAFIE
├── Symetrické    (1 klíč)
│   ├── Proudová  → bajt po bajtu  → RC4
│   └── Bloková   → bloky 128 bit  → AES, DES
├── Asymetrické   (2 klíče: Kpub + Kpriv) → RSA
├── Hash          (jednosměrná, bez klíče) → SHA-256
└── Digitální podpis (hash + asymetrika)
```

| | Proudová | Bloková |
|---|---|---|
| Šifruje po | bajtech | blocích (128 bit) |
| Rychlost | rychlejší | pomalejší |
| Příklad | RC4 | AES, DES |

---

### 3. Hashovací funkce a datová integrita

```
"heslo123" → [SHA-256] → "ef92b778..."  (vždy 256 bit)
"heslo124" → [SHA-256] → "9f8a3c12..."  (úplně jiný!)
```

**Vlastnosti:** jednosměrná, lavinový efekt, bezkoliznost
**Použití:** integrita souborů, ukládání hesel (+ salt)
**Salt** = náhodný řetězec přidaný k heslu před hashováním → zabrání rainbow table útokům

| Algoritmus | Stav |
|---|---|
| MD5, SHA-1 | ✗ prolomené |
| SHA-256, SHA-3 | ✓ bezpečné |

---

### 4. Symetrické šifrování

```
Alžběta → [plaintext + klíč K] → ciphertext → Bob → [ciphertext + klíč K] → plaintext
```

**Problém:** jak bezpečně předat klíč K?
**Řešení:** asymetrikou (Diffie-Hellman)
**Algoritmy:** AES-128/256 (standard), DES (✗ prolomený)
**Výhoda:** rychlé → vhodné pro velké objemy dat

---

### 5. Asymetrické šifrování, výměna klíčů

```
Bob: Kpub (veřejný) + Kpriv (soukromý, nikdy nesdílí)
Alžběta: zašifruje Bobovým Kpub → Bob dešifruje Kpriv
Hacker: má Kpub + ciphertext → bez Kpriv nemůže nic
```

**Diffie-Hellman:** dva účastníci se dohodnou na sdíleném klíči přes nezabezpečený kanál (bez předání klíče přímo)
**Algoritmy:** RSA (faktorizace), ECC (eliptické křivky)
**V praxi (HTTPS):** asymetrika předá symetrický klíč → symetrika šifruje data

---

### 6. Digitální podpisy, identifikace a autentizace entity

```
PODEPISOVÁNÍ:  zpráva → hash → [Kpriv odesílatele] → podpis
OVĚŘENÍ:       podpis → [Kpub odesílatele] → hash1
               zpráva → hash2
               hash1 == hash2 → ✓ platný
```

**Zaručuje:** autenticitu + integritu + nepopiratelnost
**≠ šifrování:** podpis ≠ důvěrnost, jen ověření původu

**Autentizace — faktory:**
- Co znáš → heslo, PIN
- Co máš → telefon, token
- Co jsi → biometrika

---

### 7. Certifikáty a CA; kvalifikované certifikáty, časová razítka

```
CA = důvěryhodná třetí strana (notář)
Certifikát = Kpub + identita + platnost + podpis CA

Řetěz důvěry: Root CA → Intermediate CA → Certifikát
```

| Typ | Právní síla | Příklad |
|---|---|---|
| Komerční | ✗ | HTTPS, Let's Encrypt |
| Kvalifikovaný | ✓ = vlastnoruční podpis | I.CA, PostSignum |

**Časové razítko:** důkaz že dokument existoval v daný čas (TSA server)

---

### 8. Viry — historie a současnost; antivirové programy

| Typ | Jak se šíří |
|---|---|
| Virus | připojí se k souboru |
| Worm | sám po síti |
| Trojan | tváří se jako legitimní program |
| Ransomware | zašifruje data, chce výkupné |

**Detekce antivirem:**
- Signaturová → databáze známých virů
- Heuristická → podezřelé chování
- Sandbox → izolované spuštění

**Limit:** zero-day, polymorfní viry → antivirus nedetekuje

---

### 9. Chyby v programech, revize kódu, testování bezpečnosti

**Nejčastější chyby (OWASP Top 10):** SQL Injection, XSS, broken auth, sensitive data exposure

```
SQL Injection:
  vstup: ' OR '1'='1
  dotaz: SELECT * FROM users WHERE name='' OR '1'='1' → vrátí vše!
  obrana: prepared statements
```

**Revize kódu:** manuální (vývojář) nebo automatická (SonarQube)
**Penetrační test:** etický hacker zkouší proniknout → zpráva o zranitelnostech

---

## Flashcards

**Q:** Rozdíl symetrické vs. asymetrické šifrování?
**A:** Symetrické = 1 klíč, rychlé, problém distribuce. Asymetrické = 2 klíče, pomalé, Kpub sdílí volně.

**Q:** Co je digitální podpis?
**A:** Hash zprávy zašifrovaný soukromým klíčem. Zaručuje autenticitu, integritu, nepopiratelnost.

**Q:** Rozdíl certifikát vs. digitální podpis?
**A:** Certifikát = průkaz totožnosti (Kpub patří osobě X). Podpis = stvrzení dokumentu osobou X.

**Q:** Co je hashování a proč se používá pro hesla?
**A:** Jednosměrná funkce, fixní délka výstupu. Server ukládá hash+salt, nikdy plaintext heslo.

**Q:** Co je ransomware?
**A:** Malware který zašifruje data a chce výkupné (např. WannaCry 2017).
