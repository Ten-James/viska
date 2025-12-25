> Saves a graph of objects by serializing them into a single large object (LOB), which it stores in a database field.

```cs
public class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
    public CustomerPreferences Preferences { get; set; } // Komplexní objekt
}

public class CustomerMapper
{
    public void Insert(Customer customer)
    {
        // Serializuje Preferences do JSON/XML
        var preferencesJson = JsonSerializer.Serialize(customer.Preferences);

        var sql = "INSERT INTO customers (name, preferences) VALUES (@name, @preferences)";
        ExecuteNonQuery(sql, customer.Name, preferencesJson);
    }

    public Customer Find(int id)
    {
        var data = ExecuteQueryRow("SELECT * FROM customers WHERE id = @id", id);

        // Deserializuje JSON zpět na objekt
        var preferencesJson = (string)data["preferences"];
        var preferences = JsonSerializer.Deserialize<CustomerPreferences>(preferencesJson);

        return new Customer
        {
            Id = (int)data["id"],
            Name = (string)data["name"],
            Preferences = preferences
        };
    }
}
```

Celý graf objektů se serializuje (JSON, XML, binárně) a uloží jako jeden BLOB/TEXT sloupec. Jednoduché, ale nelze dotazovat na vnitřní strukturu.

![[Pasted image 20251222101055.png]]

**Kombinuje se s:**
- [[Data mapper]] - pro serializaci komplexních objektů
- [[Domain model]] - ukládání value objects nebo agregátů

