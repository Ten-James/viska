> A type that acts as the supertype for all types in its layer.

```cs
// Layer Supertype pro všechny doménové entity
public abstract class DomainObject
{
    public int Id { get; protected set; }
    public DateTime CreatedAt { get; protected set; }
    public DateTime UpdatedAt { get; protected set; }

    protected DomainObject()
    {
        CreatedAt = DateTime.Now;
        UpdatedAt = DateTime.Now;
    }

    public void MarkAsModified()
    {
        UpdatedAt = DateTime.Now;
    }
}

// Všechny entity dědí z DomainObject
public class Customer : DomainObject
{
    public string Name { get; set; }
    public string Email { get; set; }
}

public class Order : DomainObject
{
    public decimal Total { get; set; }
    public List<OrderItem> Items { get; set; }
}

// Layer Supertype pro všechny mappery
public abstract class Mapper<T> where T : DomainObject
{
    protected abstract string TableName { get; }

    public virtual void Insert(T entity)
    {
        entity.MarkAsModified();
        InsertSpecific(entity);
    }

    protected abstract void InsertSpecific(T entity);
}
```

Společný předek pro všechny třídy ve vrstvě. Obsahuje společnou funkcionalitu, kterou nechceme duplikovat.

**Příklad:**
- [[Identity field]] - společné ID pro všechny entity

**Kombinuje se s:**
- [[Domain model]] - jako base class pro entity
- [[Data mapper]] - jako base class pro mappery
- [[Inheritance Mappers]] - pro organizaci mapper hierarchie

### Value Object, eg., Money
A small simple object, like money or a date range, whose equality isn’t based on identity. • Represents a monetary value
![[Pasted image 20251225091545.png]]


### Special Case (e.g., Null Object)
A subclass that provides special behavior for particular cases.
![[Pasted image 20251225091605.png]]

### Service Stub (Mock Object)
Removes dependence upon problematic services during testing.
![[Pasted image 20251225091643.png]]