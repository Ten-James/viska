### Úvod a lidský faktor

Software není jen kód, je tvořen lidmi, což přináší specifické výzvy. Základní otázky k zamyšlení zahrnují omezení testování, rozdíly mezi bezpečností a spolehlivostí a roli řízení rizik při návrhu.

Příklad z praxe (Společnost Cybersoft):

Programátor Petr, zkušený vývojář, zjistí těsně před spuštěním klíčové webové platformy chybu v hlavní součásti systému. Oprava by znamenala zpoždění o několik týdnů, což by při běžící masivní reklamní kampani způsobilo obrovské finanční ztráty a ztrátu důvěry. Petr se přesto rozhodne chybu opravit, aby upřednostnil kvalitu a bezpečnost před termínem.

### Základní pojmy a standardy

- **Software:** Sada komponent tvořená instrukcemi, které řídí počítač.
    
- **Vývojář:** Navrhuje systém podle specifikace (formální smlouvy či dohody).
    
- **Zákazník:** Pořizuje software k uspokojení svých potřeb na základě nabídky.
    
- **Standardy:** Neexistuje jediný univerzální způsob měření kvality. Hodnotí se soubor kritérií: metodika, testování, verifikace, validace a etika programátora.
    

### Testování a zajištění kvality

- **Vývojářské testování:** Programy jsou složité a úplné testování je u velkých projektů nemožné kvůli exponenciálnímu počtu stavů.
    
- **Unit Testing (testování jednotek):** Klíčová aktivita během vývoje, která však nezaručuje naprostou bezchybnost (chyby nemusí být jen v algoritmech).
    
- **Verifikace a Validace (V&V):**
    
    - **Verifikace (ověření):** Statické techniky, důkazy správnosti.
        
    - **Validace (potvrzení):** Dynamické techniky (testování) prokazující soulad s požadavky.
        

### Bezpečnost, spolehlivost a zabezpečení

1. **Spolehlivost (Reliability):** Pravděpodobnost, že software neselže při různých vstupech. Program s méně chybami nemusí být nutně spolehlivější, pokud tyto chyby způsobují kritická selhání.
    
2. **Bezpečnost (Security):** Ochrana dat a algoritmů před neoprávněným přístupem ("díry" v systému). Většinu zločinů páchají "důvěryhodní" lidé uvnitř firmy, nikoliv hackeři.
    
3. **Zabezpečení (Safety):** Schopnost softwaru nezpůsobit škodu v daném prostředí. Software bezpečný v jednom prostředí může být nebezpečný v jiném (např. při selhání HW).
    

### Příčiny selhání a řízení rizik

- **Lidský faktor:** Zapomínání, spěch, přílišná sebedůvěra, zlomyslnost či sebeuspokojení.
    
- **Riziko:** Definováno jako hrozba s vysokou pravděpodobností výskytu a závažnými důsledky (riziko = součásti × hrozby × zranitelnosti).
    
- **Typická rizika:** Nerealistické termíny, změny požadavků, nedostatek lidí, chyby v externích komponentách.
    
- **Řízení rizik:** Proces odhadu dopadu rizik, který musí být dokumentován a zahrnovat fáze: hodnocení, plánování, implementaci a monitorování.
    

### Smlouvy a zlepšování kvality

- **SLA (Service-Level Agreements):** Formální závazek o úrovni služeb (závazky, výkonnost, sankce).
    
    - _Customer-based:_ Pro jednoho zákazníka.
        
    - _Service-based:_ Pro všechny využívající danou službu.
        
- **Techniky zvyšování kvality:**
    
    - _Formální revize:_ Kritika odborníky.
        
    - _Inspekce:_ Kontrola odstranění chyb z minulosti.
        
    - _Procházení kódu (Code Review):_ Kontrola řádek po řádku nezávislými vývojáři.
        