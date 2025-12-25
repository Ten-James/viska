> A general structure to organize database mappers that handle inheritance hierarchies.

```cs
// Abstract mapper pro hierarchii
public abstract class VehicleMapper
{
    protected abstract string TableName { get; }

    public Vehicle Find(int id)
    {
        var sql = $"SELECT * FROM {TableName} WHERE id = @id";
        var data = ExecuteQueryRow(sql, id);
        return CreateDomainObject(data);
    }

    protected abstract Vehicle CreateDomainObject(DataRow data);

    public void Insert(Vehicle vehicle)
    {
        InsertBase(vehicle); // Společná logika
        InsertSpecific(vehicle); // Specifická pro podtřídu
    }

    protected abstract void InsertSpecific(Vehicle vehicle);
}

// Konkrétní mapper
public class CarMapper : VehicleMapper
{
    protected override string TableName => "cars";

    protected override Vehicle CreateDomainObject(DataRow data)
    {
        return new Car
        {
            Id = (int)data["id"],
            Brand = (string)data["brand"],
            Wheels = (int)data["wheels"]
        };
    }

    protected override void InsertSpecific(Vehicle vehicle)
    {
        var car = (Car)vehicle;
        var sql = "INSERT INTO cars (id, wheels) VALUES (@id, @wheels)";
        ExecuteNonQuery(sql, car.Id, car.Wheels);
    }
}
```

Organizační struktura pro mappery v dědičné hierarchii. Minimalizuje duplicitní kód pomocí abstraktních mapper tříd.

![[Pasted image 20251225091037.png]]

**Kombinuje se s:**
- [[Single Table Inheritance]] - jako organizační struktura
- [[Class Table Inheritance]] - jako organizační struktura
- [[Concrete Table Inheritance]] - jako organizační struktura
- [[Data mapper]] - základní princip mapování
- [[Layer supertype]] - pro společnou funkcionalitu mapperů

