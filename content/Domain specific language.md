### Co je DSL?

Doménově specifický jazyk je programovací nebo deklarativní jazyk zaměřený na konkrétní úzkou oblast (doménu). Má omezenou expresivitu, ale o to vyšší efektivitu v dané oblasti.

**Hlavní přínosy:**

- Zvyšují produktivitu vývojářů.
- Zlepšují komunikaci s experty z praxe (nedoménovými experty).
- Umožňují neprogramátorům nahlédnout do logiky systému.

### Kategorie DSL

1. **External DSL (Externí):** Samostatný jazyk oddělený od hlavního kódu (např. SQL, XML, HTML). Vyžaduje vlastní parser.
2. **Internal DSL (Interní):** Specifické využití syntaxe existujícího jazyka (např. LINQ v C#). Využívá hostitelský jazyk, ale čte se jako doménový zápis.

### Analýza konkrétních jazyků

- **HTML:** Je DSL pro strukturu webu. Je deklarativní (říká CO, ne JAK) a má vlastní sémantiku (značky, DOM).
- **CSS:** Je DSL pro vzhled. Má vlastní pravidla (kaskáda, selektory) a popisuje vlastnosti, ne výpočty.
- **SQL:** Je DSL pro práci s daty. Neřeší algoritmy (for/while), ale deklaruje požadovaný výsledek. Je interpretován jako výrazový strom.
- **LINQ:** Interní DSL vkládající dotazování přímo do C#. Má vlastní gramatiku a generuje AST (abstraktní syntaktický strom).

Proč DateTime NENÍ DSL?

Je to pouze knihovna/API. Nemá vlastní výrazový jazyk, nevyjadřuje doménová pravidla (např. "každý druhý pátek") a nic neinterpretuje. Aby se z něj stalo DSL, musel by umožňovat zápisy typu Every().Monday().At(14,00).

### Kdy uvažovat o DSL?

- **Interní DSL:** Pokud syntaxe hostitelského jazyka stačí, uživatelé jsou programátoři a je potřeba úzká vazba na aplikaci.
- **Externí DSL:** Pokud doména vyžaduje zcela jiný zápis, uživatelé nejsou programátoři nebo je potřeba vysoká míra formalizace a nezávislosti.

### Problémy spojené s DSL

- **Jazyková kakofonie:** Nutnost učit se mnoho malých jazyků může projekt zkomplikovat.
- **Náklady:** Návrh a údržba DSL něco stojí.
- **Ghetto Language:** Riziko vytvoření jazyka, který nikdo jiný nezná, což ztěžuje nábor nových lidí.
- **Omezená abstrakce:** Každý model může omezovat způsob, jakým o problému přemýšlíme.
