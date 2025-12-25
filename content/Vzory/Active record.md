> An object that wraps a row in a database table or view,
encapsulates the database access, and adds domain logic on that
data.

```cs
public class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }

    public void Save()
    {
        if (Id == 0)
            Insert();
        else
            Update();
    }

    public void Delete()
    {
        var sql = "DELETE FROM customers WHERE id = @id";
        ExecuteNonQuery(sql, Id);
    }

    public static Customer Find(int id)
    {
        var sql = "SELECT * FROM customers WHERE id = @id";
        var data = ExecuteQuery(sql, id);
        return new Customer { Id = id, Name = data["name"], Email = data["email"] };
    }

    private void Insert() { /* INSERT SQL */ }
    private void Update() { /* UPDATE SQL */ }
}

// Použití:
var customer = Customer.Find(1);
customer.Email = "novy@email.cz";
customer.Save();
```

Objekt obsahuje jak data, tak i databázovou logiku. Každá instance reprezentuje jeden řádek v tabulce.

![[Pasted image 20251221133006.png]]

**Kombinuje se s:**
- [[Table data gateway]] - pro sdílení databázové logiky
- [[Transaction script]] - pro jednoduché aplikace