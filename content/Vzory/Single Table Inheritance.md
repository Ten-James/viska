>Represents an inheritance hierarchy of classes as a single table that has columns for all the fields of the various classes.

```cs
// Tabulka: vehicles (id, type, brand, wheels, wingspan)
public abstract class Vehicle
{
    public int Id { get; set; }
    public string Brand { get; set; }
}

public class Car : Vehicle
{
    public int Wheels { get; set; }
}

public class Airplane : Vehicle
{
    public double Wingspan { get; set; }
}

public class VehicleMapper
{
    public Vehicle Find(int id)
    {
        var sql = "SELECT * FROM vehicles WHERE id = @id";
        var data = ExecuteQueryRow(sql, id);

        var type = (string)data["type"];
        return type switch
        {
            "Car" => new Car { Id = id, Brand = (string)data["brand"], Wheels = (int)data["wheels"] },
            "Airplane" => new Airplane { Id = id, Brand = (string)data["brand"], Wingspan = (double)data["wingspan"] },
            _ => throw new Exception("Unknown type")
        };
    }
}
```

Celá hierarchia dědičnosti v jedné tabulce. Sloupec "type" určuje typ objektu. Některé sloupce jsou NULL pro některé typy.

![[Pasted image 20251225090429.png]]

**Pro:**
- V databázi je pouze jedna tabulka, o kterou se musíme starat.
- Při získávání dat se nepoužívají žádná spojení.
- Refaktoring, který přesunuje data nahoru nebo dolů v hierarchii tříd, nevyžaduje změnu v databázi.

**Proti:**
- Pole jsou někdy potřeba a někdy ne, což může být matoucí pro lidi, kteří pracují přímo s tabulkami.
- Sloupce používané pouze některými podtřídami vedou k plýtvání místem v databázi.
- Jedna tabulka může být příliš velká, s mnoha indexy a častým zamykáním, což může ovlivnit výkon.

**Kombinuje se s:**
- [[Data mapper]] - implementuje mapování dědičnosti
- [[Inheritance Mappers]] - organizuje mappery pro hierarchii