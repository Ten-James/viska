>Represents an inheritance hierarchy of classes with one table for each class.

```cs
// Tabulky: vehicles (id, brand), cars (id, wheels), airplanes (id, wingspan)
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
        // JOIN přes obě tabulky
        var sql = @"SELECT v.*, c.wheels
                    FROM vehicles v
                    JOIN cars c ON v.id = c.id
                    WHERE v.id = @id";
        var data = ExecuteQueryRow(sql, id);

        return new Car
        {
            Id = id,
            Brand = (string)data["brand"],
            Wheels = (int)data["wheels"]
        };
    }

    public void Insert(Car car)
    {
        // Nejdřív insert do parent tabulky
        ExecuteNonQuery("INSERT INTO vehicles (brand) VALUES (@brand)", car.Brand);
        var id = GetLastInsertId();

        // Pak do child tabulky
        ExecuteNonQuery("INSERT INTO cars (id, wheels) VALUES (@id, @wheels)", id, car.Wheels);
    }
}
```

Každá třída má vlastní tabulku. Podtřídy mají foreign key na parent tabulku. Normalizované, ale vyžaduje JOINy.

![[Pasted image 20251225090630.png]]

**Pro:**
- Pro každý řádek jsou použité všechny sloupce, takže tabulky jsou přehlednější a neplýtváme místem.
- Vztah mezi doménovým modelem dědičnosti a databází je přímočarý.

**Proti:**
- Pro načtení objektu je třeba se pracovat s více tabulkami, což znamená použití spojení více dotazů v paměti.
- Jakýkoli přesun dat v dědičné hierarchii nahoru nebo dolů způsobuje změny v databázi.
- Tabulky nadtypů se mohou stát úzkým hrdlem, protože se k nim musí často přistupovat.
- Vysoký stupeň normalizace databáze může ztížit pochopení pro ad-hoc dotazy.

**Kombinuje se s:**
- [[Data mapper]] - implementuje mapování dědičnosti
- [[Inheritance Mappers]] - organizuje mappery pro hierarchii
- [[Foreign key mapping]] - pro propojení parent a child tabulek