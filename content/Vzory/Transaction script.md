> Organizes business logic by procedures where each procedure
> handles a single request from the presentation.

```cs
public class OrderService
{
    public void ProcessOrder(int customerId, List<OrderItem> items)
    {
        using var transaction = BeginTransaction();

        // Kontrola zákazníka
        var customer = GetCustomer(customerId);
        if (customer == null)
            throw new Exception("Zákazník nenalezen");

        // Vytvoření objednávky
        var orderId = CreateOrder(customerId);

        // Přidání položek
        decimal total = 0;
        foreach (var item in items)
        {
            AddOrderItem(orderId, item);
            total += item.Price * item.Quantity;
            UpdateStock(item.ProductId, -item.Quantity);
        }

        // Aktualizace ceny
        UpdateOrderTotal(orderId, total);

        transaction.Commit();
    }
}
```

Funkce nebo metoda, která řeší jeden kompletní use case napříč více tabulkami v rámci transakce. Jednoduchý a přímočarý přístup.

![[Pasted image 20251221132501.png]]

**Kombinuje se s:**
- [[Table data gateway]] - pro přístup k datům
- [[Row data gateway]] - pro manipulaci s řádky
- [[Service layer]] - jako implementace služeb