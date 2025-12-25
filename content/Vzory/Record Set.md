>An in-memory representation of tabular data, typically the result of a database query.

```cs
// V .NET je to DataTable/DataSet
var sql = "SELECT * FROM customers WHERE city = @city";
DataTable recordSet = ExecuteQuery(sql, "Praha");

foreach (DataRow row in recordSet.Rows)
{
    var name = (string)row["name"];
    var email = (string)row["email"];
    Console.WriteLine($"{name}: {email}");
}

// Lze předávat mezi vrstvami:
public DataTable GetCustomersByCity(string city)
{
    return _gateway.FindByCity(city);
}
```

Generická tabulková datová struktura (v .NET typicky DataTable). Neváže se na konkrétní doménu, jen drží data z databáze.

![[Pasted image 20251221123346.png]]

**Kombinuje se s:**
- [[Table data gateway]] - vrací Record Set
- [[Table model]] - pracuje s Record Set
- [[Transaction script]] - manipuluje s daty

