Architektura [[Informační systém]] leží na vyšší úrovni abstrakce
tak, že zahrnuje
- pohled na [[Doména]] informačního systému (skupina souvisejících „věcí“ z
pohledu zákazníka),
- pohled vývojáře na globální strukturu systému a chování jeho částí, jejich
propojení a synchronizace,
- pohled na přístup k datům a toky dat v systému,
- fyzické rozmístění komponent
![[Pasted image 20251221091540.png]]

## Návrh x Nasazení
- **NÁVRH** (design) popisuje systém rozdělený do logických částí,
tedy **JAK** funguje a s ČÍM **pracuje** (třídy, tabulky, komponenty,
služby a vztahy mezi nimi).
- **NASAZENÍ** (deployment) popisuje **KDE** systém běží (na jakém
HW, SW platformě,…).


## Tří vrstvá architektura
- Komunikace s uživatelem (prezentace informací, předání  
požadavků)  
- Zpracování informací a jejich (dočasné) uchování.  
- Trvalé uchování informací (dat).  

## MVC bráško
![[Pasted image 20251221123106.png]]

### nedorozumění
- Obvykle vůbec neřeší přístup k datům (ve smyslu přístupu k
databázi).
- Existují variace pro různé platformy a situace.
- Je nutno chápat jako velmi obecný (a správný)

### návrhový/architektonický koncept.
- Neplést si s třívrstvou architekturou (která je lineární).
