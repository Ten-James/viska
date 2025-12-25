>An object that carries data between processes in order to reduce the number of method calls.

```cs
public class CustomerDTO
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
}

public class OrderDTO
{
    public int Id { get; set; }
    public CustomerDTO Customer { get; set; }
    public List<OrderItemDTO> Items { get; set; }
    public decimal TotalPrice { get; set; }
}

// Použití:
public OrderDTO GetOrder(int orderId)
{
    var order = _repository.Find(orderId);
    return new OrderDTO
    {
        Id = order.Id,
        Customer = MapCustomerToDTO(order.Customer),
        Items = order.Items.Select(MapItemToDTO).ToList(),
        TotalPrice = order.CalculateTotal()
    };
}
```

Jednoduchý datový objekt bez logiky. Přenáší data mezi vrstvami (např. z service layer do presentation layer) nebo přes síť.

**Kombinuje se s:**
- [[Service layer]] - pro přenos dat z/do služeb
- [[Data mapper]] - pro konverzi z doménových objektů
- [[Gateway]] - pro vzdálenou komunikaci

