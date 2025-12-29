
# Jak vyvíjet v týmu (2025-26)

## Co je podstatné?

- **Lidé a jejich spolupráce**
- Plány, pravidla, procesy a řízení
- **Dokumentace**
- Techniky a technologie
- Cílem je **kvalitní produkt (software)**

### Od zadání k produktu

- Základem jsou lidé a kvalita jejich výstupů].
- Je nutné organizovat práci a koordinovat tým s přiměřenou administrativní zátěží.
- Dokumentace je nezbytná (kdo nedokumentuje, neváží si své práce).
- Plánování času a nákladů je nutné, i když nelze vše odhadnout předem.
- Důležitá jsou správná rozhodnutí o technologii a architektuře na začátku.

---

## Vodopádový model (1970)

> Kde chyba však jsme to specifikovali před rokem 

![[Pasted image 20251225091919.png]]
- Skládá se ze sedmi navazujících fází: Specifikace požadavků, Návrh, Implementace, Integrace, Testování, Ladění, Instalace a Údržba.
- Následující fáze začíná až po kompletním dokončení předchozí.

### Výhody a nevýhody

***Výhody:** Včasné odhalení chyb, důraz na dokumentaci (snadná záměna lidí), jednoduché řízení.

***Nevýhody:** Nemožnost dovést fázi k dokonalosti před přechodem dál, trvání na potenciálně chybných rozhodnutích.

---

## Moderní přístupy k vývoji

### Iterativní a inkrementální vývoj
- **Iterativní návrh:** Opakovaný proces analýzy, návrhu, implementace a testování.
- **Inkrementální model:** Produkt je budován postupně po přírůstcích.
- Každá iterace končí funkčním produktem, ke kterému se přidává další funkčnost.

### Unified Process (UP)

- Představen Ivarem Jacobsonem (1999).
- **3 klíčové charakteristiky:**
    1. **Use-case-driven:** Případy užití se používají ve všech fázích, slouží k verifikaci a validaci.
    2. **Architecture-centric:** Popis architektury je jádrem vývoje.
    3. **Risk-focused:** Zaměření na nejkritičtější rizika v raných fázích.
- **4 fáze:**
    -**Inception (Zahájení):** Realizovatelnost, rozsah, klíčové požadavky, harmonogram.
    -**Elaboration (Rozpracování):** Potvrzení schopnosti postavit systém, zpřesnění architektury a rizik.
    -**Construction (Konstrukce):** Vytvoření systému, průběžná akceptace přírůstků.
    -**Transition (Nasazení):** Nasazení u zákazníka, oprava vad, vydání (release).

---

## Agilní vývoj a metodiky
![[Pasted image 20251225092327.png]]

### Agilní manifest (2001)
- Jednotlivci a interakce nad procesy a nástroji.
- Fungující software nad obsáhlou dokumentací.
- Spolupráce se zákazníkem nad vyjednáváním o smlouvách.
- Reagování na změnu nad dodržováním plánu.

### Extrémní programování (XP)
- Všechny osvědčené metody se dělají naplno.
- **Principy:** Komunikace, jednoduchost, zpětná vazba, odvaha.
- **Praktiky:** Párové programování, společné vlastnictví kódu, neustálá integrace, refaktorování, testování.

### SCRUM
- Role: Product owner, Vývojový tým, SCRUM master.
- Nástroje: Backlog (user stories), Sprinty, Denní schůzky.

### TDD (Test-Driven Development)
1. Napsat test.
2. Ujistit se, že test neprojde.
3. Napsat kód, aby testem prošel.
4. Refaktorovat a opakovat.

---

## Shrnutí
- Nejdůležitější jsou **lidé**.
- Kvalita je měřena funkčním softwarem s dobrým zdrojovým kódem.
- Nutnost minimální, dobře strukturované dokumentace.
- Soustředění na otázky: CO-JAK-KDE-KDO-KDY-PROČ.


[[Rizika Vývoje IS]]

