> An object that acts as a gateway to a single record in
> a data source. There is one instance per row.

```cs
public class CustomerRow
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }

    public void Update()
    {
        var sql = "UPDATE customers SET name = @name, email = @email WHERE id = @id";
        ExecuteNonQuery(sql, Name, Email, Id);
    }

    public void Delete()
    {
        var sql = "DELETE FROM customers WHERE id = @id";
        ExecuteNonQuery(sql, Id);
    }

    public static CustomerRow Find(int id)
    {
        var sql = "SELECT * FROM customers WHERE id = @id";
        var data = ExecuteQueryRow(sql, id);
        return new CustomerRow
        {
            Id = (int)data["id"],
            Name = (string)data["name"],
            Email = (string)data["email"]
        };
    }
}

// Použití:
var customer = CustomerRow.Find(1);
customer.Email = "novy@email.cz";
customer.Update();
```

Každá instance reprezentuje jeden řádek v databázi. Podobné Active Record, ale bez business logiky - jen databázové operace.

![[Pasted image 20251221132959.png]]

**Kombinuje se s:**
- [[Transaction script]] - jako datové objekty

**Nekombinuje se s:**
- [[Domain model]] - příliš závislé na databázi

