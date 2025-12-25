> Represents an inheritance hierarchy of classes with one table per concrete class in the hierarchy.

![[Pasted image 20251225090831.png]]

Pro:
- Každá tabulka je samostatná a neobsahuje žádná prázdná pole.
- Při čtení dat z konkrétních mapperů není třeba provádět žádná spojení. 
- Ke každé tabulce se přistupuje pouze tehdy, když se přistupuje k dané třídě, což snižuje náklady na dotazování.
Proti: 
- V databázi nelze dobře pracovat s abstraktními třídami.
- Pokud jsou pole na doménových třídách posunuta nahoru nebo dolů v dědičné hierarchii, je nutné změnit tabulky.
- Pokud se změní pole nadtřídy, je nutné změnit každou tabulku, která toto pole má. 
- Vyhledání nadtřídy (polymorfismus) je nutné zkontrolovat všechny tabulky, což vede k vícenásobným přístupům do databáze.

Kdy a jak je tedy použít?
- Efektivita uložení.
- Výkonnost.
- Dotazování.
- Lze je i kombinovat (např. pro různé úrovně dědičné hierarchie můžeme použít různé vzory)