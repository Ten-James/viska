## 1. Popište, co se rozumí pojmem informační systém, co řeší a uveďte příklady.

**Odpověď:** Informační systém je soubor vzájemně propojených komponent, které sbírají, zpracovávají, ukládají a distribuují informace pro podporu rozhodování a řízení organizace. Řeší automatizaci procesů, správu dat a poskytování informací uživatelům. Příklady: bankovní systém, e-shop, fakultní informační systém.

## 2. Popište, co se rozumí pojmem doména informačního systému a uveďte příklady.

**Odpověď:** Doména je oblast reality, kterou informační systém modeluje a spravuje - zahrnuje business procesy, pravidla a entity. Příklady: bankovnictví (účty, transakce), e-commerce (produkty, objednávky), zdravotnictví (pacienti, diagnózy).

Viz [[Domain model]].

## 3. Na jaké otázky si musíme odpovědět při realizaci informačního systému? Uveďte příklady odpovědí na jednotlivé otázky v kontextu nějakého konkrétního informačního systému.

**Odpověď:** Co systém dělá (funkční požadavky), jak to dělá (architektura), kdo to používá (uživatelské role), kde běží (deployment). Pro e-shop: zpracování objednávek, třívrstvá architektura, zákazníci/admini, cloud hosting.

## 4. Z jakých pohledů (míry abstrakce) se můžeme dívat na informační systém? A v jakých rolích?

**Odpověď:** Konceptuální (business analytik), logický (architekt), fyzický (vývojář), deployment (DevOps). Každá úroveň má jinou míru detailu a zaměření.

## 5. Co se rozumí architekturou informačního systému a co zahrnuje?

**Odpověď:** Architektura definuje strukturu systému, jeho komponenty a jejich vztahy. Zahrnuje vrstvení aplikace, komunikační protokoly, datové toky a technologické volby.

## 6. Jaké jsou rozdíly mezi statickou, dynamickou a mobilní architekturou informačního systému? Uveďte příklady.

**Odpověď:** Statická popisuje strukturu komponent (třídy, moduly), dynamická popisuje běhové chování (sekvenční diagramy, states). Mobilní architektura řeší distribuci komponent přes zařízení a síť.

## 7. Co obsahuje struktura každého informačního systému? Uveďte příklady.

**Odpověď:** Prezentační vrstva (UI), aplikační logika, datová vrstva (databáze). Příklad: web frontend, REST API, PostgreSQL.

Viz [[Service layer]].

## 8. Popište, co se rozumí pojmem komponenta informačního systému. Uveďte příklady.

**Odpověď:** Komponenta je samostatná, znovupoužitelná část systému s definovaným rozhraním. Příklady: autentizační modul, payment gateway, email služba.

Viz [[Gateway]].

## 9. Jaký je rozdíl mezi architekturou a návrhem informačního sytému?

**Odpověď:** Architektura řeší high-level strukturu a klíčová rozhodnutí (vrstvení, technologie), návrh řeší konkrétní implementaci (třídy, vzory). Architektura je strategická, návrh je taktický.

## 10. Jak se správně postupuje při stanovení architektury a návrhu informačního systému?

**Odpověď:** Identifikace požadavků, volba architektonického stylu, dekompozice na komponenty, výběr návrhových vzorů, iterativní zpřesňování.

Viz [[Domain model]], [[Service layer]].

## 11. Které kompetence obsahuje informační systém? Uveďte příklady těchto kompetencí.

**Odpověď:** Funkční (business logika), datové (persistence, validace), komunikační (API, messaging), bezpečnostní (autentizace, autorizace). Příklad: zpracování objednávky, uložení do DB, notifikace emailem.
## 12. Co se rozumí pojmem návrhový vzor? Co každý vzor obsahuje? Uveďte příklady.

**Odpověď:** Návrhový vzor je opakovaně použitelné řešení častého problému v návrhu softwaru. Obsahuje název, popis problému, řešení a konsekvence použití.

Viz [[Data mapper]], [[Unit Of Work]], [[Service layer]].

## 13. Popište podstatu třívrstvé architektury. Jaký je rozdíl mezi fyzickou a logickou třívrstvou architekturou?

**Odpověď:** Třívrstvá architektura odděluje prezentaci, aplikační logiku a data do samostatných vrstev. Logická je organizace kódu do modulů, fyzická je deployment na různé servery (web server, app server, DB server).

Viz [[Service layer]], [[Data mapper]].

## 14. Co je podstatou vzoru MVC? V čem se liší od třívrstvé architektury?

**Odpověď:** MVC (Model-View-Controller) odděluje data (Model), zobrazení (View) a řízení (Controller). Oproti třívrstvé architektuře je MVC primárně prezentační vzor, zatímco třívrstvá architektura pokrývá celý systém včetně datové vrstvy.

## 15. Co řeší skupina návrhových vzorů pro doménovou logiku?

**Odpověď:** Organizaci business logiky - jak strukturovat kód, který implementuje obchodní pravidla a procesy. Určuje, kde a jak se umístí doménová logika v architektuře.

Viz [[Transaction script]], [[Domain model]], [[Table model]], [[Service layer]].

## 16. Popište podstatu jednotlivých vzorů pro doménovou logiku (Transaction script, Domain model, Table module, Service layer).

**Odpověď:** [[Transaction script]] - procedurální funkce na use case; [[Domain model]] - objekty s daty i logikou; [[Table model]] - třída pro celou tabulku s logikou; [[Service layer]] - fasáda koordinující doménovou logiku.

## 17. V čem se od sebe liší jednotlivé vzory pro doménovou logiku? Kdy, kde a proč je použít/nepoužít? Uveďte příklady.

**Odpověď:** [[Transaction script]] je nejjednodušší pro malé aplikace, [[Domain model]] nejlepší pro složitou logiku, [[Table model]] vhodný pro tabulkově orientované aplikace. [[Service layer]] koordinuje ostatní vzory a definuje aplikační rozhraní. Použití závisí na komplexitě domény.
## 18. Co společně řeší skupina návrhových vzorů pro práci s datovými zdroji?

**Odpověď:** Přístup k databázi a mapování mezi databázovými strukturami a objekty v paměti. Určují, jak se data načítají, ukládají a transformují mezi DB a aplikační vrstvou.

Viz [[Table data gateway]], [[Row data gateway]], [[Active record]], [[Data mapper]].

## 19. Popište podstatu jednotlivých vzorů pro práci s datovými zdroji (Table data gateway, Row data gateway, Active record, Data mapper).

**Odpověď:** [[Table data gateway]] - jedna třída pro celou tabulku; [[Row data gateway]] - objekt na řádek bez logiky; [[Active record]] - objekt na řádek s logikou i DB přístupem; [[Data mapper]] - separátní mapper pro oddělení domény od DB.

## 20. V čem se liší jednotlivé vzory pro práci s datovými zdroji? Kdy, kde a proč je použít/nepoužít?

**Odpověď:** [[Active record]] je nejjednodušší ale mísí logiku s DB, [[Data mapper]] nejlépe odděluje doménu ale je složitější. [[Table data gateway]] dobrý pro procedurální kód, [[Row data gateway]] pro jednoduché CRUD. Viz sekce "Kombinuje se s" v jednotlivých vzorech.

## 21. Se kterými vzory pro doménovou logiku by se mohly použít některé ze vzorů pro práci s datovými zdroji a proč? Uveďte příklady.

**Odpověď:** [[Transaction script]] s [[Table data gateway]] nebo [[Row data gateway]] - procedurální přístup; [[Domain model]] s [[Data mapper]] - čistá doména; [[Active record]] s jednoduchým [[Domain model]]. Viz "Kombinuje se s" v jednotlivých vzorech.

## 22. Pro každý ze čtyř návrhových vzorů pro práci s datovými zdroji si promyslete a napište kousíček zdrojového kódu, ze kterého bude poznat, o který vzor jde.

**Odpověď:** Viz code snippety v [[Table data gateway]], [[Row data gateway]], [[Active record]], [[Data mapper]].
## 23. Co společně řeší návrhové vzory pro objektově-relační chování?

**Odpověď:** Problémy spojené s mapováním objektů na relační databázi - cachování, sledování změn, načítání dat, správu transakcí. Optimalizují výkon a zajišťují konzistenci dat mezi objekty a databází.

Viz [[Unit Of Work]], [[Identity Map]], [[Lazy Load]].

## 24. Kdy bychom měli zvážit použití vzoru Unit of Work a proč? Na příkladu vysvětlete, jak jej použít.

**Odpověď:** Když potřebujeme koordinovat více změn v objektech a zapsat je v jedné transakci, zajistit atomicitu operací. Používá se s [[Data mapper]] pro sledování nových, změněných a smazaných objektů.

Viz code snippet v [[Unit Of Work]].

## 25. Kdy bychom měli zvážit použití vzoru Identity Map a proč? Na příkladu vysvětlete, jak jej použít.

**Odpověď:** Když chceme zajistit, že každý objekt z DB existuje v paměti pouze jednou (cachování). Předchází duplikátům a zrychluje načítání opakovaně používaných objektů.

Viz code snippet v [[Identity Map]].

## 26. Kdy bychom měli zvážit použití vzoru Lazy Load a proč? Na příkladu vysvětlete jak jej použít.

**Odpověď:** Když nechceme načítat všechna data najednou kvůli výkonu - data se načtou až při prvním přístupu. Typicky pro relace (1:N, M:N) nebo velké objekty.

Viz code snippet v [[Lazy Load]].

## 27. Popřemýšlejte, se kterými vzory pro práci s datovými zdroji byste mohli společně použít některé ze vzorů pro objektově-relační chování a proč? Zkuste najít příklady.

**Odpověď:** [[Data mapper]] s [[Unit Of Work]], [[Identity Map]] a [[Lazy Load]] - plná podpora ORM; [[Active record]] může používat [[Identity Map]]. [[Table data gateway]] a [[Row data gateway]] typicky nepoužívají tyto vzory.

## 28. V jakých situacích byste použili vzor Identity field a proč? A kdy naopak ne? Napište fragment kódu, ze kterého bude patrné, proč jste tento vzor využili.

**Odpověď:** Vždy když mapujeme objekty na databázi s primárním klíčem. Nepoužívá se u value objektů bez identity nebo u stateless služeb.

Viz code snippet v [[Identity field]].

## 29. Jaký je rozdíl mezi vzory Foreign key mapping a Associate table mapping? Napište dva fragmenty kódu, ze kterých bude patrné, že jste použili tyto vzory.

**Odpověď:** [[Foreign key mapping]] pro 1:N vztahy (foreign key v child tabulce), [[Association Table mapping]] pro M:N vztahy (samostatná asociační tabulka). Viz code snippety v těchto vzorech.

## 30. V čem se liší vzor Dependent mapping od vzoru Data mapper? Kdy je vhodné jej použít?

**Odpověď:** [[Dependent Mapping]] nemá vlastní mapper - parent mapper řídí persistenci i child objektů. Používá se pro agregáty, kde child nemá smysl bez parent (OrderItems v Order).

Viz [[Dependent Mapping]].

## 31. Napište fragment kódu, ze kterého bude patrné, že jste použili vzor Dependent mapping.

**Odpověď:** Viz code snippet v [[Dependent Mapping]].

## 32. Vymyslete alespoň dva příklady vhodné pro použití vzoru Embedded value. Co je podstatou tohoto vzoru? Proč a kdy je vhodné jej použít?

**Odpověď:** Value object (Address, Money) ukládaný jako sloupce v parent tabulce místo vlastní tabulky. Příklady: Customer.Address, Product.Price - když value object nemá vlastní identitu a patří k jedné entitě.

Viz [[Embedded Value]].

## 33. Vymyslete alespoň dva příklady vhodné pro použití vzoru Serialized LOB. Co je podstatou tohoto vzoru? Proč a kdy je vhodné jej použít?

**Odpověď:** Serializace složitých objektů do JSON/XML (CustomerPreferences, ProductConfiguration). Použití když nepotřebujeme dotazovat vnitřní strukturu a chceme jednoduchost.

Viz [[Serialized LOB]].
## 34. Popište podstatu vzorů Single / Class / Concrete Table Inheritance a v jakých situacích je vhodné je použít.

**Odpověď:** [[Single Table Inheritance]] - jedna tabulka pro hierarchii (jednoduché, ale plýtvání místem); [[Class Table Inheritance]] - tabulka na třídu (normalizované, ale JOINy); [[Concrete Table Inheritance]] - tabulka na konkrétní třídu (bez JOINů, ale složité polymorfní dotazy). Viz detaily v jednotlivých vzorech.

## 35. Napište fragment kódu, ze kterého bude patrné, že jste použili vzor Single / Class / Concrete Table Inheritance.

**Odpověď:** Viz code snippety v [[Single Table Inheritance]], [[Class Table Inheritance]], [[Concrete Table Inheritance]].

## 36. Jaký je rozdíl mezi vzory Single / Class / Concrete Table Inheritance? Napište fragmenty kódu, ze kterých bude patrný tento rozdíl.

**Odpověď:** [[Single Table Inheritance]] má type sloupec a všechny fieldy v jedné tabulce; [[Class Table Inheritance]] má JOINy přes parent-child tabulky; [[Concrete Table Inheritance]] duplikuje parent fieldy v každé tabulce. Viz code snippety v těchto vzorech.

## 37. Vymyslete a popište příklad na využití vzoru Gateway.

**Odpověď:** PaymentGateway pro komunikaci s platební bránou, EmailGateway pro email službu, DatabaseGateway pro přístup k DB. Zapouzdřuje externí systém a poskytuje jednodušší rozhraní.

Viz [[Gateway]].

## 38. Vymyslete a popište příklad na využití vzoru Mapper.

**Odpověď:** CustomerDtoMapper převádí mezi Customer (doména) a CustomerDTO (API), OrderMapper mapuje Order objekty na databázové řádky. Odděluje dva nezávislé objektové modely.

Viz [[Mapper]].

## 39. Vymyslete a popište příklad na využití vzoru Layer Supertype. Napište fragment kódu využívající dědičnost, ze kterého bude patrné, že jste použili tento vzor.

**Odpověď:** DomainObject jako base class pro všechny entity s `Id`, `CreatedAt`, `UpdatedAt`. `Mapper<T>` jako base pro všechny mappery se společnou logikou. Eliminuje duplikaci společné funkcionality.

Viz [[Layer supertype]].

## 40. Vymyslete a popište příklad na využití vzoru Service Stub (Mock Object). Napište fragment kódu, ze kterého bude patrné, že jste použili tento vzor.

**Odpověď:** MockPaymentService pro testování bez volání reálné platební brány, FakeEmailService pro testování notifikací. Nahrazuje závislost na externí službě testovací implementací s předvídatelným chováním.

## 41. Popište, co se rozumí vodopádovým modelem a jaké jsou jeho výhody a nevýhody.

**Odpověď:** Sekvenční fáze (analýza → design → implementace → testování → deployment) bez návratu. Výhody: jasná struktura, dokumentace; nevýhody: neflexibilní, pozdní odhalení chyb, nereaguje na změny požadavků.

## 42. Popište, co se rozumí iterativním a inkrementálním vývojem. Uveďte příklad.

**Odpověď:** Vývoj v krátkých cyklech (iteracích), každá přidává novou funkcionalitu (inkrement). Příklad: první iterace základní CRUD, druhá přidá autentizaci, třetí reporting - v každé iteraci analýza, vývoj, testování.

## 43. Co se rozumí UP (unified process), na jakých principech, charakteristikách a fázích je postaven? Uveďte příklady.

**Odpověď:** Iterativní framework s fázemi Inception, Elaboration, Construction, Transition. Principy: use-case driven, architektura-centrické, iterativní a inkrementální. Charakteristiky: řízení rizik, správa požadavků.

## 44. Jaké jsou čtyři základní charakteristiky agilního softwarového vývoje, které ho odlišují od vodopádového a dalších robustních přístupů?

**Odpověď:** Lidé nad procesy, fungující software nad dokumentací, spolupráce se zákazníkem nad vyjednáváním smlouvy, reakce na změny nad dodržováním plánu. Důraz na flexibilitu a komunikaci.

## 45. Na jakých principech a praktikách je založeno tzv. extrémní programování?

**Odpověď:** Test-driven development, pair programming, continuous integration, refaktoring, small releases. Principy: jednoduchost, komunikace, feedback, odvaha, respekt.

## 46. Které nejdůležitější charakteristiky má SCRUM?

**Odpověď:** Sprinty (2-4 týdny), denní stand-upy, role (Product Owner, Scrum Master, Team), artefakty (Product Backlog, Sprint Backlog, Increment). Transparence, inspekce, adaptace.

## 47. Popište proces typický pro tzv. testy řízený softwarový vývoj. Uveďte příklad.

**Odpověď:** Red-Green-Refactor: napsat failing test, implementovat minimum pro pass, refaktorovat. Příklad: test na AddCustomer() → implementace → refaktoring duplicit. Test před kódem.

## 48. Proč nemůže být testování softwaru nikdy úplné a jaký to má dopad na řízení rizik?

**Odpověď:** Nekonečný počet možných vstupů a stavů, časová a ekonomická omezení. Dopad: prioritizace testů podle rizika, zaměření na kritické scénáře, akceptace zbytkového rizika.

## 49. Jaký je rozdíl mezi pojmy správnost, spolehlivost, bezpečnost (security) a zabezpečení (safety)?

**Odpověď:** Správnost = splňuje specifikaci; spolehlivost = funguje konzistentně v čase; security = ochrana před útoky; safety = neškodí lidem/majetku. Různé aspekty kvality.

## 50. Jaké skryté problémy mohou vzniknout při použití externích softwarových komponent?

**Odpověď:** Bezpečnostní zranitelnosti, nekompatibilita verzí, ukončení podpory (end-of-life), licenční problémy. Skrytá závislost na vendor, vendor lock-in, neočekávané chování.

## 51. Co tvoří riziko podle rovnice „riziko = součásti × hrozby × zranitelnosti" a jak se tato rovnice používá v praxi?

**Odpověď:** Součásti = co chráníme (data, systémy); hrozby = co může ublížit (hackeři, výpadky); zranitelnosti = slabiny (neopravené bugy). V praxi: identifikace všech tří faktorů, prioritizace podle součinu.

## 52. Jaké jsou nejčastější příčiny selhání softwaru spojené s lidským faktorem?

**Odpověď:** Chyby v požadavcích, špatná komunikace, nedostatečné testování, time pressure vedoucí ke špatným rozhodnutím. Nepochopení domény, únava, přehlédnutí edge cases.

## 53. Proč je důležité dokumentovat rizika a jaké fáze zahrnuje řízení rizik po nasazení do provozu?

**Odpověď:** Zajišťuje kontinuitu knowledge base, umožňuje learning a prevenci. Fáze: monitoring, incident response, post-mortem analýza, aktualizace rizikového registru.

## 54. Jaké přístupy existují ke zvyšování kvality softwaru a proč mají největší význam ve fázi specifikace požadavků?

**Odpověď:** Code reviews, testing, static analysis, refaktoring, design patterns. Význam v early fázích: chyby v požadavcích jsou nejdražší na opravu, správná specifikace předchází costly změnám.

## 55. Co je doménově specifický jazyk? Proč a kdy je dobré ho využít? Uveďte příklady.

**Odpověď:** Jazyk zaměřený na konkrétní doménu s vyšší expresivitou než general-purpose jazyk. Použití: opakující se vzory, business rules, konfigurace. Příklady: SQL, HTML, CSS, regex.

## 56. Co je cílem využití doménově specifického jazyka a jaké vlastnosti by měl mít?

**Odpověď:** Zvýšit produktivitu, umožnit expresi doménových konceptů, umožnit non-programátorům psát logiku. Vlastnosti: čitelnost, stručnost, zaměření na doménu, validace.

## 57. Jaký je rozdíl mezi externím a interním doménově specifickým jazykem? Uveďte příklady.

**Odpověď:** Externí DSL má vlastní syntax a parser (SQL, HTML); interní DSL používá syntax host jazyka (Ruby DSLs, fluent interfaces v C#). Externí flexibilnější, interní jednodušší na implementaci.

## 58. S jakými problémy se můžeme setkat při návrhu doménově specifického jazyka? Uveďte příklady.

**Odpověď:** Scope creep (feature creep), složitost parsingu, učící křivka pro uživatele, údržba parseru/compileru. Příklad: SQL začal jednoduše, nyní obrovská složitost; balance mezi expresivitou a jednoduchostí.