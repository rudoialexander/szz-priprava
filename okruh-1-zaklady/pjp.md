# PJP — Programovací jazyky a překladače
**Okruh:** 1 — Základy informatiky &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`
> Pozn.: PJP je probráno letos prakticky — viz `../6. semestr/pjp/2026/` (test_otazky, ustni_zkouska_otazky). Pro SZZ stačí obecný přehled.

## Oficiální témata / otázky
1. Chomského hierarchie, teorie formálních jazyků a gramatik, návaznost na teorii automatů (konečné automaty, zásobníkové automaty, Turingův stroj).
2. Bezkontextové jazyky a jejich modely — zásobníkové automaty, bezkontextové gramatiky.
3. Struktura překladače a fáze překladu — lexikální analýza, deterministická syntaktická analýza, generování kódu.

---
## Odpovědi v bodech

### 1. Chomského hierarchie

```
Typ 0  ⊃  Typ 1  ⊃  Typ 2  ⊃  Typ 3
(nejsilnější)          (nejslabší)
```

| Typ | Název | Automat | Příklad |
|---|---|---|---|
| 3 | Regulární | Konečný automat (KA) | `[a-z]+`, regex |
| 2 | Bezkontextová | Zásobníkový automat (ZA) | Java, C, výrazy |
| 1 | Kontextová | Lineárně omezený automat | přirozený jazyk |
| 0 | Neomezená | Turingův stroj | vše co jde spočítat |

**KLÍČ:** Regulární ⊂ Bezkontextové ⊂ Kontextové ⊂ Neomezené

---

### 2. Bezkontextové jazyky

**DEFINICE**
Bezkontextová gramatika = pravidla tvaru `A → α`
- levá strana = vždy 1 neterminál
- pravá strana = cokoliv (terminály + neterminály)
EN: context-free grammar (CFG)

**PŘÍKLAD:**
```
E → E + E
E → ( E )
E → číslo
```

**Zásobníkový automat (ZA)**
EN: pushdown automaton (PDA)
= konečný automat + zásobník
→ rozpoznává přesně bezkontextové jazyky

**Použití v překladačích:**
- Syntaktická analýza (parser) ověřuje kód pomocí CFG
- Gramatika Java/C/Python = bezkontextová gramatika

---

### 3. Turingův stroj

**DEFINICE**
Turingův stroj = teoretický model počítače s neomezenou páskou.
EN: Turing machine

- Čte a zapisuje na pásku (neomezená paměť)
- Pohybuje se doleva/doprava
- Simuluje jakýkoliv algoritmus

**Proč důležitý:**
- Definuje hranici co je vůbec vypočitatelné (Church-Turing thesis)
- Cokoliv počítač umí = Turingův stroj to také umí

---

### 4. Fáze překladu

```
zdrojový kód
     ↓
[Lexikální analýza]   → tokeny (slova)
     ↓
[Syntaktická analýza] → AST (abstraktní syntaktický strom)
     ↓
[Sémantická analýza]  → typy, smysl
     ↓
[Generování kódu]     → assembler / bytekód
     ↓
strojový kód
```

| Fáze | Co dělá | EN |
|---|---|---|
| Lexikální | rozseká text na tokeny | lexical analysis |
| Syntaktická | ověří gramatiku, postaví AST | parsing |
| Sémantická | ověří typy a smysl | semantic analysis |
| Generování kódu | přeloží na strojový kód | code generation |

---

## Flashcards (ústní trénink)

**Q:** Co je Chomského hierarchie?
**A:** 4 typy gramatik (0–3): regulární (KA) → bezkontextové (ZA) → kontextové → neomezené (Turingův stroj). Každá je podmnožinou té silnější.

**Q:** Co je Turingův stroj?
**A:** Teoretický model s neomezenou páskou — definuje co je vypočitatelné. Odpovídá gramatikám typu 0.

**Q:** Co je bezkontextová gramatika?
**A:** Pravidla tvaru A → α, levá strana vždy jeden neterminál. Používá se v syntaktické analýze překladačů.

**Q:** Jaké jsou fáze překladu?
**A:** Lexikální analýza (tokeny) → syntaktická analýza (AST) → sémantická analýza → generování kódu.
