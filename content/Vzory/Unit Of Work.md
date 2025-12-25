>Maintains a list of objects affected by a business transaction and coordinates the writing out of changes and the resolution of concurrency problems.

```cs
public class UnitOfWork
{
    private List<object> _newObjects = new();
    private List<object> _dirtyObjects = new();
    private List<object> _deletedObjects = new();

    public void RegisterNew(object obj) => _newObjects.Add(obj);
    public void RegisterDirty(object obj) => _dirtyObjects.Add(obj);
    public void RegisterDeleted(object obj) => _deletedObjects.Add(obj);

    public void Commit()
    {
        using var transaction = BeginTransaction();
        InsertNew();
        UpdateDirty();
        DeleteRemoved();
        transaction.Commit();
    }
}

// Použití:
var uow = new UnitOfWork();
var customer = new Customer("Jan");
uow.RegisterNew(customer);
customer.ChangeAddress("Praha 1");
uow.RegisterDirty(customer);
uow.Commit(); // Vše se zapíše najednou v transakci
```

Koordinuje všechny změny v objektech a zapíše je najednou v rámci transakce. Zajišťuje konzistenci dat a optimalizuje databázové operace.

**Kombinuje se s:**
- [[Data mapper]] - pro mapování a persistenci objektů
- [[Identity Map]] - pro sledování načtených objektů
- [[Domain model]] - jako doménové objekty, které spravuje

