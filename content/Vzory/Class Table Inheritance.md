>Represents an inheritance hierarchy of classes with one table for each class.

![[Pasted image 20251225090630.png]]

Pro:
- Pro každý řádek jsou použité všechny sloupce, takže tabulky jsou přehlednější a neplýtváme místem. 
- Vztah mezi doménovým modelem dědičnosti a databází je přímočarý.
Proti:
- Pro načtení objektu je třeba se pracovat s více tabulkami, což znamená použití spojení více dotazů v paměti. 
- Jakýkoli přesun dat v dědičné hierarchii nahoru nebo dolů způsobuje změny v databázi.
- Tabulky nadtypů se mohou stát úzkým hrdlem, protože se k nim musí často přistupovat.
- Vysoký stupeň normalizace databáze může ztížit pochopení pro ad-hoc dotazy