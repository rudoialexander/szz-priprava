# Tematické okruhy ke SZZ — Aplikovaná informatika (VŠPJ)

> Čitelná verze dokumentu `SZZ_okruhy_AI_2019-2020_2023.docx` (V Jihlavě, 24. 1. 2023, doc. Ing. Radek Kolman, Ph.D.).
> **Zdroj pravdy** pro rozsah zkoušky. Platí pro studium zahájené nejdříve 2019/20.

**Charakter otázek:** otázka nemusí pokrývat všechna témata okruhu; je spíše **obecného rázu** — student prokazuje **přehled v oboru a chápání souvislostí**.

---

## Okruh 1 — Základy informatiky

### Datové struktury a algoritmy (DSA)
Algoritmy řazení výběrem (Select-sort), vkládáním (Insert-sort), zaměňováním (Buble-sort), řazení haldou (Heap-sort), přihrádkové řazení (Radix-sort, Caset-sort), řazení slučováním (Merge-sort), řazení dělením (Quick-sort). Minimální, průměrná a maximální asymptotická operační složitost algoritmů řazení. Adresní metody vyhledávání (přímý přístup, otevřené a zřetězené rozptylování). Asociativní metody vyhledávání (sekvenční, binárním půlením, binární vyhledávací stromy). Operační a paměťová složitost algoritmů vyhledávání. Datové typy zásobník, fronta, prioritní fronta, pole, tabulka, seznam, množina — jejich specifikace a implementace.

### Diskrétní struktury (DIS)
Množiny (intuitivní definice, podmnožiny, operace s množinami a jejich vlastnosti, mohutnost množin). Relace (definice, inverzní relace, relace na množině a jejich vlastnosti, ekvivalence, uspořádání). Zobrazení (definice, vlastnosti). Výroková logika (výrok, logické spojky, formule a pravdivostní ohodnocení, tautologie a kontradikce, de Morganovy zákony, negace formulí, sémantický důsledek, CNF/DNF). Predikátová logika (rozdíly oproti výrokové logice, syntaxe a sémantika, interpretace, sémantický důsledek). Neorientované grafy (definice a základní pojmy, isomorfismus, stupeň uzlu, sledy v grafu, souvislost grafu, stromy a kostry). Orientované grafy (definice a základní pojmy, sledy v orientovaném grafu, silná souvislost, stupně uzlu). Vlastnosti grafů (pokrytí, Eulerův graf, vzdálenost na grafu). Kořenové stromy (definice, hloubka, pravidelné a binární stromy). Reprezentace grafů v paměti (matice incidence, matice sousednosti, spojová reprezentace). Základní grafové algoritmy (prohledávání do šířky a do hloubky, určení minimální kostry, Huffmanův kód, Dijkstrův algoritmus).

### Operační systémy (OPS)
Synchronizace procesů, důvody synchronizace, postupový prostor. Synchronizační metody (producent a konzument, čtenáři a písař, vzájemné vyloučení). Chyby v synchronizaci (uváznutí, stárnutí). Synchronizační prostředky (semafory, zasílání zpráv). Přidělování procesoru (jednotlivé stavy přidělování procesoru, funkce modulu přidělování procesoru, způsoby přidělování v multiprogramovém systému). Přidělování paměti (adresování paměti, funkce modulu přidělování paměti, stránkování na žádost). Systém souborů, úkoly, úrovně, charakteristika souborových systémů FAT32, NTFS, EXT2 (výhody, práva, použití, způsob ukládání souborů).

### Programovací jazyky a překladače (PJP)
Chomského hierarchie, teorie formálních jazyků a gramatik, návaznost na teorii automatů (konečné automaty, zásobníkové automaty, Turingův stroj). Bezkontextové jazyky a jejich modely (zásobníkové automaty, bezkontextové gramatiky). Struktura překladače a charakteristika fází překladu (lexikální analýza, deterministická syntaktická analýza a generování kódu).

### Základy strukturované programování (ZSP)
Algoritmus, program, proces. Překladač, interpret, preprocesor. Reprezentace dat v paměti počítače, základní datové typy, proměnné, konstanty, přetypování. Operátory a jejich priorita, výrazy. Základní příkazy. Řízení běhu programu — řídicí struktury. Datový typ ukazatel. Funkce a procedury, návratový typ, formální a skutečné parametry, parametry volané hodnotou a referencí. Rozklad problému na podproblémy, procedurální přístup, rekurze. Jednorozměrná a vícerozměrná pole. Řetězce. Standardní vstup a výstup, funkce vstupu/výstupu, práce se soubory. Binární a textové soubory. Strukturované datové typy. Dynamické datové struktury. Modulární programování, hlavičkové soubory.

---

## Okruh 2 — Softwarové inženýrství a aplikace

### Bezpečnost a ochrana dat (BOD)
Úvod do informační bezpečnosti, legislativa a normy. Kryptografie. Proudové šifry, blokové šifry. Hashovací funkce a datová integrita. Symetrické šifrování. Asymetrické šifrovaní, výměna klíčů. Digitální podpisy, identifikace a autentizace entity. Certifikáty a certifikační autority. Komerční/kvalifikované certifikáty, časová razítka. Viry — historie a současnost. Antivirové programy. Chyby v programech, revize kódu, testování bezpečnosti.

### Objektově orientované programování (OOP)
Principy objektového programování, třídy a jejich použití. Struktura objektu, atributy a metody. Dynamický charakter objektu, konstruktor, destruktor, instance třídy. Kopírovací a přesunující operace. Přetěžování metod, přetěžování operátorů. Dědičnost, hierarchie tříd, kompozice. Abstraktní třídy, polymorfismus, virtuální metody. Výjimky a jejich zpracování. Abstraktní datové typy, základní knihovny. Staticky a dynamicky vázané metody, abstraktní datový typ, abstraktní třída. Šablony, knihovna STL. Soubory a proudy.

### Softwarové inženýrství (SWI)
Softwarový proces a jeho základní modely. Softwarové profese a týmy. Architektura software. Plánování softwarových projektů, techniky zobrazení plánů. Metody odhadu nákladů na informační systém. Fáze analýzy požadavků na informační systém. Objektová analýza, základní diagramy UML. Modelování procesů, modelování požadavků, katalog požadavků, funkční a nefunkční požadavky. Model jednání, aktéři, případy užití. Konceptuální analýza, modelování dat. Integritní omezení a jejich popis (OCL). Metodiky tvorby softwarových produktů, klasické, agilní. Modelem řízený vývoj, přímé a reverzní inženýrství, okružní jízda (round-trip). Zajištění kvality, softwarové metriky, analýza a řízení rizik, bezpečnost informačních systémů, testování.

### Řízení softwarových projektů (ŘSP)
Rozdíl mezi tradičními, agilními a extrémními způsoby řízení projektů. Charakteristika agilních metod vývoje SW a jejich srovnání s tradičními (plánovacími) a formálními přístupy. Způsoby získávání, formalizace a dokumentace zákaznických požadavků. Extrémní programování (XP). Scrum, scrumban. Procesní zlepšování v oblasti vývoje SW. IT management v organizacích, ITIL.

### Tvorba internetových stránek (TIS)
Www stránky (základní části, tagy, validace, html). HTML 5 — vlastnosti, použití. Kaskádové styly (třídy, základní vlastnosti, použití). Pozicování pomocí kaskádových stylů. Formuláře a jejich kontrola, regulární výrazy. Přístup k databázi pomocí PHP a práce s daty. Zabezpečení www stránek (cookies, session).

### Úvod do databázových systémů (DB)
Databázový systém (definice, účel, database management system). Návrh databáze (konceptuální, logický a fyzický model). Konceptuální modelování, ER model (princip a účel konceptuální analýzy, základní konstrukty ER modelu, integritní omezení). Relační model dat (definice, princip, integritní omezení). Relační algebra (základní operace, spojení, použití relační algebry pro dotazování). Transformace ER modelu do relačního modelu. Jazyk SQL pro definici dat, jazyk SQL pro manipulaci s daty. Příkaz SELECT jazyka SQL (základní dotazy, použitelné klauzule, dotazy nad více tabulkami a spojení, agregační funkce, vnořené poddotazy, implementace univerzálního a existenčního kvantifikátoru). Další možnosti jazyka SQL (ošetření hodnot NULL, podmíněné větvení, řádkové výrazy). Implementace a použití transakcí v jazyce SQL.

### Úvod do počítačových sítí (UPS)
Ethernet — verze, rychlosti. IPv4 adresa, maska, CIDR, IP datagram. IP protokol. Protokoly ARP, ICMP, IGMP. TCP a UDP protokoly. Fragmentace a segmentace. Směrování. Firewally. Protokoly DNS, SMTP, POP3, IMAP, HTTP, FTP — charakteristika, použití, fáze komunikace. Bezdrátové sítě standardu 802.11 b/g/a/n. ISDN a ADSL.

---

## Okruh 3 — Specializace

### Návrh a implementace databázových systémů (NIDB)
Plánování databáze (sběr požadavků a nalézání faktů, uživatelské pohledy, strategie konceptuálního návrhu). Funkční závislosti (definice, Armstrongova pravidla, minimální pokrytí, nalezení klíče). Normální formy relací (definice 1.-3. NF, metody normalizace, pokrytí závislostí, výhody a nevýhody normalizace, denormalizace). Pokročilejší rysy jazyka SQL (datové typy a operátory, pohledy, oprávnění, uživatelské role). Transakce (princip a účel, způsoby implementace, prokládání transakcí a související problémy, stupeň izolace a uzamykání). Fyzická vrstva databáze (reprezentace odvozených dat, zajištění integritních omezení, fyzické uložení tabulek, indexy, pohledy). Procedurální rozšíření SQL (účel, použití, kursory a triggery, možnosti pro zajištění integritních omezení). Objektově orientované databáze (motivace, výhody a nevýhody, základy objektového návrhu, třídy, metody, navazování vztahů). Objektově-relační model (motivace, vlastnosti, příklady).

### Návrh uživatelských rozhraní (NUR)
Návrhy rozhraní pro Windows aplikace. Layouty webových stránek. Návrhy webdesignu a řešení pro webové aplikace. Bootstrap.

### Počítačová grafika a virtuální realita (PGVR)
Obraz, jeho reprezentace a zobrazovací řetězec, barevné modely. Algoritmizace dvourozměrných objektů, modelování křivek, ploch a těles. Promítání, viditelnost, textury a světlo ve scéně. Globální zobrazovací metody. Virtuální realita, tvorba 3D modelů, prezentační vrstvy simulačních nástrojů.

### Podnikové informační systémy (PIS)
Proces vytvoření informačního systému. Složení IS (komponenty), vlastnosti IS, implementační typy IS, vývoj a projektování IS, fáze vývoje IS, objektový přístup k IS, vývojové fáze. Model technické infrastruktury informačního systému. Automatizovaný sběr dat, technologie následného zpracování údajů v informačním systému. Podpora projektových činností prostřednictvím informačních systémů, podpora v rozhodování. Životní cyklus informačního systému. Základní principy podnikových aplikací kategorie ERP, CRM, SCM. Softwarové technologie pro realizaci informačních systémů.

### Webové technologie (WT)
Knihovna jQuery — možnosti použití při tvorbě www stránek. AJAX — vlastnosti, příklady použití. Architektura MVC, vysvětlení, výhody. Framework Bootstrap (vlastnosti, použití, výhody). Využití frameworku Symfony při tvorbě webových aplikací, vlastnosti, výhody. Twig — vlastnosti, použití. Mapování objektového modelu na relační databáze (objektově-relační mapování — ORM, doctrine), jeho výhody.
