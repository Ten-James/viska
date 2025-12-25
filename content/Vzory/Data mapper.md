> A layer of mappers that moves data between objects and a
> database while keeping them independent of each other and the
> mapper itself.

```cs
public class CustomerMapper
{
    public Customer Find(int id)
    {
        var sql = "SELECT * FROM customers WHERE id = @id";
        var data = ExecuteQuery(sql, id);
        return new Customer(data["name"], data["email"]);
    }

    public void Insert(Customer customer)
    {
        var sql = "INSERT INTO customers (name, email) VALUES (@name, @email)";
        ExecuteNonQuery(sql, customer.Name, customer.Email);
    }

    public void Update(Customer customer)
    {
        var sql = "UPDATE customers SET name = @name, email = @email WHERE id = @id";
        ExecuteNonQuery(sql, customer.Name, customer.Email, customer.Id);
    }
}

// Použití:
var mapper = new CustomerMapper();
var customer = mapper.Find(1);
customer.ChangeEmail("novy@email.cz");
mapper.Update(customer);
```

Odděluje doménové objekty od databázové logiky. Mapper se stará o vše co souvisí s databází, zatímco doménové objekty zůstávají čisté.

![[Pasted image 20251221133014.png]]

**Kombinuje se s:**
- [[Domain model]] - pro mapování doménových objektů
- [[Unit Of Work]] - pro koordinaci změn
- [[Identity Map]] - pro cachování objektů
- [[Lazy Load]] - pro odložené načítání relací