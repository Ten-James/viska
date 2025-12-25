> A single instance that handles
> the business logic for all rows
> in a database table or view.

```cs
public class CustomerTableModule
{
    private DataTable _data;

    public CustomerTableModule(DataTable data)
    {
        _data = data;
    }

    public decimal GetTotalRevenue()
    {
        decimal total = 0;
        foreach (DataRow row in _data.Rows)
            total += (decimal)row["revenue"];
        return total;
    }

    public void ApplyDiscount(decimal percentage)
    {
        foreach (DataRow row in _data.Rows)
        {
            var current = (decimal)row["price"];
            row["price"] = current * (1 - percentage);
        }
    }
}

// Použití:
var customerData = gateway.GetAllCustomers();
var module = new CustomerTableModule(customerData);
var total = module.GetTotalRevenue();
```

Jedna instance třídy obsahuje logiku pro všechny řádky tabulky. Pracuje s DataTable nebo Record Set.

![[Pasted image 20251221132517.png]]

**Kombinuje se s:**
- [[Table data gateway]] - pro získání dat
- [[Record Set]] - jako datová struktura
- [[Transaction script]] - pro komplexnější operace

