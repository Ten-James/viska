>Ensures that each object gets loaded only once by keeping every loaded object in a map. Looks up objects using the map when referring to them.

```cs
public class IdentityMap<T>
{
    private Dictionary<int, T> _map = new();

    public T Get(int id)
    {
        if (_map.ContainsKey(id))
            return _map[id];
        return default(T);
    }

    public void Add(int id, T obj)
    {
        _map[id] = obj;
    }
}

public class CustomerMapper
{
    private IdentityMap<Customer> _identityMap = new();

    public Customer Find(int id)
    {
        var customer = _identityMap.Get(id);
        if (customer != null) return customer; // Vrátí z cache

        customer = LoadFromDatabase(id);
        _identityMap.Add(id, customer);
        return customer;
    }
}
```

Zajišťuje, že každý objekt existuje v paměti pouze jednou. Pokud se objekt načítá vícekrát, vrátí se stejná instance z cache.

**Kombinuje se s:**
- [[Data mapper]] - pro cachování načtených objektů
- [[Unit Of Work]] - pro sledování změn
- [[Lazy Load]] - pro efektivní načítání dat