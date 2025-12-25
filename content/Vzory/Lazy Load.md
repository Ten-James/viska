>An object that doesn't contain all of the data you need but knows how to get it.

```cs
public class Order
{
    private List<OrderItem> _items;
    private bool _itemsLoaded = false;

    public List<OrderItem> Items
    {
        get
        {
            if (!_itemsLoaded)
            {
                _items = LoadItemsFromDatabase(Id);
                _itemsLoaded = true;
            }
            return _items;
        }
    }
}

// Nebo s Lazy<T>:
public class Customer
{
    private Lazy<List<Order>> _orders;

    public Customer()
    {
        _orders = new Lazy<List<Order>>(() => LoadOrdersFromDatabase(Id));
    }

    public List<Order> Orders => _orders.Value;
}

// Použití:
var customer = customerMapper.Find(1); // Nenačte orders
var orders = customer.Orders; // Teprve teď se načtou orders z DB
```

Data se načítají až ve chvíli, kdy jsou poprvé potřeba. Optimalizuje výkon tím, že se načítají jen skutečně použitá data.

**Kombinuje se s:**
- [[Data mapper]] - pro odložené načítání relací
- [[Identity Map]] - zajistí konzistenci lazy-loaded objektů
- [[Domain model]] - v doménových objektech s relacemi

