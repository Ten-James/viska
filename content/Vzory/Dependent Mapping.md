>Has one class perform the database mapping for a child class.

```cs
public class Order
{
    public int Id { get; set; }
    public List<OrderItem> Items { get; set; }
}

public class OrderItem
{
    public int ProductId { get; set; }
    public int Quantity { get; set; }
    // Nemá vlastní mapper - závislé na Order
}

public class OrderMapper
{
    public void Insert(Order order)
    {
        var sql = "INSERT INTO orders (customer_id) VALUES (@customerId)";
        var orderId = ExecuteInsert(sql, order.CustomerId);

        // OrderMapper ukládá i OrderItems
        foreach (var item in order.Items)
        {
            var itemSql = "INSERT INTO order_items (order_id, product_id, quantity) VALUES (@orderId, @productId, @quantity)";
            ExecuteNonQuery(itemSql, orderId, item.ProductId, item.Quantity);
        }
    }

    public void Delete(Order order)
    {
        // Nejdřív smaže závislé items
        ExecuteNonQuery("DELETE FROM order_items WHERE order_id = @id", order.Id);
        // Pak parent
        ExecuteNonQuery("DELETE FROM orders WHERE id = @id", order.Id);
    }
}
```

Závislé objekty (OrderItem) nemají vlastní mapper. Parent objekt (Order) řídí persistenci i svých child objektů.

![[Pasted image 20251222101017.png]]

**Kombinuje se s:**
- [[Data mapper]] - parent mapper mapuje i children
- [[Embedded Value]] - podobný princip závislosti
- [[Unit Of Work]] - koordinuje uložení hierarchie

