> An object that acts as a gateway to a database table.
> One instance handles all the rows in the table.

```cs
public class CustomerGateway
{
    public DataTable FindAll()
    {
        var sql = "SELECT * FROM customers";
        return ExecuteQuery(sql);
    }

    public DataRow Find(int id)
    {
        var sql = "SELECT * FROM customers WHERE id = @id";
        return ExecuteQueryRow(sql, id);
    }

    public void Insert(string name, string email)
    {
        var sql = "INSERT INTO customers (name, email) VALUES (@name, @email)";
        ExecuteNonQuery(sql, name, email);
    }

    public void Update(int id, string name, string email)
    {
        var sql = "UPDATE customers SET name = @name, email = @email WHERE id = @id";
        ExecuteNonQuery(sql, name, email, id);
    }
}

// Použití:
var gateway = new CustomerGateway();
var customers = gateway.FindAll();
gateway.Insert("Jan", "jan@email.cz");
```

Jedna instance gateway třídy pro celou tabulku. Poskytuje metody pro práci se všemi řádky.

![[Pasted image 20251221132949.png]]

**Kombinuje se s:**
- [[Transaction script]] - jako datová vrstva
- [[Table model]] - pro strukturované výsledky
- [[Active record]] - sdílená databázová logika

**Nekombinuje se s:**
- [[Domain model]] - příliš závislé na databázi

