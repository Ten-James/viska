>Saves a database ID field in an object to maintain identity between an in-memory object and a database row.

```cs
public class Customer
{
    // Identity field - unikátní ID z databáze
    public int Id { get; private set; }

    public string Name { get; set; }
    public string Email { get; set; }

    public Customer(int id, string name, string email)
    {
        Id = id;
        Name = name;
        Email = email;
    }
}

public class CustomerMapper
{
    public void Update(Customer customer)
    {
        // Používá Id pro identifikaci správného řádku
        var sql = "UPDATE customers SET name = @name, email = @email WHERE id = @id";
        ExecuteNonQuery(sql, customer.Name, customer.Email, customer.Id);
    }
}
```

Každý objekt má pole (typicky Id), které odpovídá primárnímu klíči v databázi. Umožňuje mapovat mezi objekty a databázovými řádky.

**Kombinuje se s:**
- [[Data mapper]] - pro identifikaci objektů při persistenci
- [[Identity Map]] - klíč pro vyhledávání v mapě
- [[Unit Of Work]] - identifikace změněných objektů

