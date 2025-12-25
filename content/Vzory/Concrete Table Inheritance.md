> Represents an inheritance hierarchy of classes with one table per concrete class in the hierarchy.

```cs
// Tabulky: cars (id, brand, wheels), airplanes (id, brand, wingspan)
// Žádná společná tabulka vehicles!

public abstract class Vehicle
{
    public int Id { get; set; }
    public string Brand { get; set; }
}

public class Car : Vehicle
{
    public int Wheels { get; set; }
}

public class CarMapper
{
    public Car Find(int id)
    {
        // Jen cars tabulka, žádné JOINy
        var sql = "SELECT * FROM cars WHERE id = @id";
        var data = ExecuteQueryRow(sql, id);

        return new Car
        {
            Id = id,
            Brand = (string)data["brand"],
            Wheels = (int)data["wheels"]
        };
    }
}

// Pro polymorfní dotaz na všechna Vehicle:
public List<Vehicle> FindAllVehicles()
{
    var vehicles = new List<Vehicle>();

    // Musíme dotazovat každou tabulku zvlášť
    vehicles.AddRange(LoadCarsFromTable());
    vehicles.AddRange(LoadAirplanesFromTable());

    return vehicles;
}
```

Každá konkrétní třída má vlastní nezávislou tabulku. Pole z parent třídy jsou duplikována v každé tabulce. Žádné JOINy, ale polymorfní dotazy jsou složité.

![[Pasted image 20251225090831.png]]

**Pro:**
- Každá tabulka je samostatná a neobsahuje žádná prázdná pole.
- Při čtení dat z konkrétních mapperů není třeba provádět žádná spojení.
- Ke každé tabulce se přistupuje pouze tehdy, když se přistupuje k dané třídě, což snižuje náklady na dotazování.

**Proti:**
- V databázi nelze dobře pracovat s abstraktními třídami.
- Pokud jsou pole na doménových třídách posunuta nahoru nebo dolů v dědičné hierarchii, je nutné změnit tabulky.
- Pokud se změní pole nadtřídy, je nutné změnit každou tabulku, která toto pole má.
- Vyhledání nadtřídy (polymorfismus) je nutné zkontrolovat všechny tabulky, což vede k vícenásobným přístupům do databáze.

**Kdy použít:**
- Efektivita uložení.
- Výkonnost.
- Dotazování.
- Lze je i kombinovat (např. pro různé úrovně dědičné hierarchie můžeme použít různé vzory).

**Kombinuje se s:**
- [[Data mapper]] - implementuje mapování dědičnosti
- [[Inheritance Mappers]] - organizuje mappery pro hierarchii