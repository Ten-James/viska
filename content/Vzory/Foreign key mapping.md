> Maps an association between objects to a foreign key reference between tables.

```cs
public class Order
{
    public int Id { get; set; }
    public Customer Customer { get; set; } // Objektová reference
}

public class OrderMapper
{
    public void Insert(Order order)
    {
        var sql = "INSERT INTO orders (customer_id, total) VALUES (@customerId, @total)";
        // Uloží se foreign key (customer.Id), ne celý objekt
        ExecuteNonQuery(sql, order.Customer.Id, order.Total);
    }

    public Order Find(int id)
    {
        var sql = "SELECT * FROM orders WHERE id = @id";
        var data = ExecuteQueryRow(sql, id);

        // Načte Customer pomocí foreign key
        var customerId = (int)data["customer_id"];
        var customer = _customerMapper.Find(customerId);

        return new Order { Id = id, Customer = customer };
    }
}
```

Mapuje objektové reference (Order.Customer) na cizí klíče v databázi (orders.customer_id). Při ukládání se uloží jen ID, při načítání se objekt načte přes foreign key.

![[Pasted image 20251222100955.png]]

**Kombinuje se s:**
- [[Data mapper]] - implementuje mapování relací
- [[Identity field]] - používá ID pro reference
- [[Lazy Load]] - pro odložené načtení relací
- [[Identity Map]] - zajistí, že se každý objekt načte jen jednou

