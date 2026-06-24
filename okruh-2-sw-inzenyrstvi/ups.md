# UPS — Úvod do počítačových sítí
**Okruh:** 2 — Softwarové inženýrství a aplikace &nbsp;&nbsp; **Stav:** ✓ hotovo
**Zdroj otázek:** `podklady/SZZ-okruhy.md`

## Oficiální témata / otázky
1. Ethernet — verze, rychlosti.
2. IPv4 — adresa, maska, CIDR, IP datagram.
3. IP protokol.
4. Protokoly ARP, ICMP, IGMP.
5. TCP a UDP protokoly.
6. Fragmentace a segmentace.
7. Směrování; firewally.
8. Aplikační protokoly — DNS, SMTP, POP3, IMAP, HTTP, FTP (charakteristika, použití, fáze komunikace).
9. Bezdrátové sítě standardu 802.11 b/g/a/n.
10. ISDN a ADSL.

---
## Odpovědi v bodech

### 1. Ethernet
EN: *Ethernet* — standard IEEE 802.3 pro LAN.
| Verze | Rychlost | Médium |
|---|---|---|
| 10BASE-T | 10 Mb/s | UTP |
| 100BASE-TX | 100 Mb/s | UTP Cat5 |
| 1000BASE-T | 1 Gb/s | UTP Cat5e/6 |
| 10GBASE-T | 10 Gb/s | UTP Cat6a/7 |
- Rámec: cíl MAC (6B) + zdroj MAC (6B) + typ (2B) + data + FCS
- MAC = 48bitový fyzický identifikátor síťové karty

---

### 2. IPv4 — adresa, maska, CIDR, IP datagram
- IPv4 = 32bitová adresa, zápis 4 oktetů (0–255): `192.168.1.10`
- Maska rozděluje adresu na síťovou část a část hostitele
- `192.168.1.10 AND 255.255.255.0 = 192.168.1.0` (adresa sítě)
- CIDR EN: *Classless Inter-Domain Routing* — `/24` = 24 jedničkových bitů = 254 hostitelů
- `/30`=2 hostitele · `/24`=254 · `/16`=65534 · `/8`=16M
- Speciální: `.0` = adresa sítě · `.255` = broadcast · `127.0.0.1` = loopback
- IP datagram hlavička (min 20 B): Version, TTL, Protocol (6=TCP,17=UDP,1=ICMP), src IP, dst IP, Fragment Offset

---

### 3. IP protokol
EN: *Internet Protocol* — vrstva L3.
- Nespolehlivý (best-effort), bez spojení (connectionless), nezaručuje pořadí.
- Router: přijme paket → porovná cíl se směrovací tabulkou → pošle dál (next hop).
- TTL se sníží o 1 na každém routeru; TTL=0 → zahozen + ICMP Time Exceeded.
- IPv6: 128bitové adresy, zápis hex `2001:db8::1`, fragmentuje jen odesílatel.

---

### 4. ARP, ICMP, IGMP
**ARP** EN: *Address Resolution Protocol* — převod IP → MAC adresa.
- Broadcast: "Kdo má IP x?" → odpověď: "Já, MAC=XX:XX…" → uloží do ARP cache.

**ICMP** EN: *Internet Control Message Protocol* — diagnostika a chyby L3.
- Echo Request/Reply = `ping`; Time Exceeded = `traceroute`; Destination Unreachable; Redirect.

**IGMP** EN: *Internet Group Management Protocol* — správa multicastových skupin.
- Multicast = jeden odesílatel → skupina příjemců.
- Membership Report ("chci skupinu"), Leave Group, Membership Query (router se ptá).

---

### 5. TCP a UDP
**TCP** EN: *Transmission Control Protocol* — spolehlivý, spojovaný (L4).
- 3-way handshake: `SYN → SYN-ACK → ACK`; ukončení: `FIN → FIN-ACK → ACK`
- Zaručuje doručení (ACK), pořadí. Hlavička 20 B. Použití: HTTP, FTP, SMTP, SSH.

**UDP** EN: *User Datagram Protocol* — nespolehlivý, nespojovaný (L4).
- Žádný handshake, žádné potvrzování. Hlavička 8 B. Použití: DNS, streaming, VoIP, hry.

| | TCP | UDP |
|---|---|---|
| Doručení | zaručeno | ne |
| Pořadí | zaručeno | ne |
| Rychlost | pomalejší | rychlejší |

---

### 6. Fragmentace a segmentace
**Segmentace** EN: *segmentation* — L4, TCP, dělí data na segmenty podle MSS (Maximum Segment Size).

**Fragmentace** EN: *fragmentation* — L3, IP, dělí datagram podle MTU (Ethernet MTU = 1500 B).
- Router (IPv4) nebo odesílatel (IPv6) dělí datagram.
- Pole hlavičky: Identification (stejné pro všechny fragmenty), Fragment Offset (pozice v násobcích 8B), MF (More Fragments), DF (Don't Fragment).
- Cíl složí fragmenty zpět.

---

### 7. Směrování a firewally
**Směrování** EN: *routing* — výběr cesty pro IP paket přes routery.
- Směrovací tabulka: cílová síť → rozhraní / next hop; `0.0.0.0/0` = default gateway.
- Statické = ručně; Dynamické = automaticky (RIP, OSPF, BGP).
- RIP = malé sítě (max 15 skoků); OSPF = velké sítě; BGP = mezi autonomními systémy.

**Firewall** — filtruje provoz podle pravidel.
| Typ | Popis |
|---|---|
| Paketový filtr | IP, port, protokol; bez kontextu |
| Stavový EN: *stateful* | sleduje stav spojení |
| Aplikační (proxy) | rozumí obsahu; nejbezpečnější |
- Pravidla: zdroj IP, cíl IP, port, protokol → ALLOW/DENY. Implicitní: DENY ALL.

---

### 8. Aplikační protokoly
| Protokol | Port | Transport | Účel |
|---|---|---|---|
| DNS | 53 | UDP | IP adresa pro doménové jméno |
| HTTP | 80 | TCP | webové stránky |
| HTTPS | 443 | TCP | HTTP + TLS |
| FTP | 21/20 | TCP | přenos souborů (plaintext!) |
| SMTP | 25/587 | TCP | odesílání e-mailu |
| POP3 | 110 | TCP | příjem e-mailu (stáhni a smaž) |
| IMAP | 143 | TCP | příjem e-mailu (server = master) |

- HTTP metody: GET, POST, PUT, DELETE. Kódy: 200 OK, 301 redirect, 404 nenalezeno, 500 chyba serveru.
- POP3 vs IMAP: POP3 = offline/1 zařízení; IMAP = synchronizace/více zařízení.

---

### 9. Bezdrátové sítě 802.11
EN: *IEEE 802.11 Wi-Fi standards*
| Standard | Pásmo | Max rychlost |
|---|---|---|
| 802.11b | 2,4 GHz | 11 Mb/s |
| 802.11g | 2,4 GHz | 54 Mb/s |
| 802.11a | 5 GHz | 54 Mb/s |
| 802.11n | 2,4/5 GHz | 600 Mb/s |
- 2,4 GHz = větší dosah, více rušení; 5 GHz = menší dosah, méně rušení.
- MIMO EN: *Multiple Input Multiple Output* = více antén → vyšší propustnost (802.11n).

---

### 10. ISDN a ADSL
**ISDN** EN: *Integrated Services Digital Network* — digitální přenos hlasu i dat po telefonní lince.
- BRI: 2× B kanál (64 kb/s) + 1× D kanál (16 kb/s) = 128 kb/s.
- PRI: 30× B + 1× D = 2 Mb/s. B = data/hlas, D = řídící signalizace.

**ADSL** EN: *Asymmetric Digital Subscriber Line* — širokopásmové DSL připojení.
- Download až 24 Mb/s, upload až 3,5 Mb/s. Médium: stávající telefonní linka.
- Asymetrické: uživatel stahuje víc než nahrává. Dosah max ~5 km od ústředny.

## Flashcards (ústní trénink)
> Q/A po probrání každého tématu.
