>Represents an inheritance hierarchy of classes as a single table that has columns for all the fields of the various classes.

![[Pasted image 20251225090429.png]]

Pro: 
- V databázi je pouze jedna tabulka, o kterou se musíme starat. 
- Při získávání dat se nepoužívají žádná spojení. 
- Refaktoring, který přesunuje data nahoru nebo dolů v hierarchii tříd, nevyžaduje změnu v databázi. 
Proti:
- Pole jsou někdy potřeba a někdy ne, což může být matoucí. pro lidi, kteří pracují přímo s tabulkami.
- Sloupce používané pouze některými podtřídami vedou k plýtvání místem v databázi.
- Jedna tabulka může být příliš velká, s mnoha indexy a častým zamykáním, což může ovlivnit výkon.