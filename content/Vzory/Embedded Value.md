> Maps an object into several fields of another object's table.

```cs
public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
    public string ZipCode { get; set; }
}

public class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
    public Address Address { get; set; } // Value object
}

public class CustomerMapper
{
    public void Insert(Customer customer)
    {
        // Address se mapuje do sloupců customers tabulky
        var sql = @"INSERT INTO customers (name, street, city, zip_code)
                    VALUES (@name, @street, @city, @zipCode)";
        ExecuteNonQuery(sql,
            customer.Name,
            customer.Address.Street,
            customer.Address.City,
            customer.Address.ZipCode);
    }

    public Customer Find(int id)
    {
        var data = ExecuteQueryRow("SELECT * FROM customers WHERE id = @id", id);
        return new Customer
        {
            Id = (int)data["id"],
            Name = (string)data["name"],
            Address = new Address
            {
                Street = (string)data["street"],
                City = (string)data["city"],
                ZipCode = (string)data["zip_code"]
            }
        };
    }
}
```

Value object (Address) nemá vlastní tabulku - jeho vlastnosti se ukládají jako sloupce v parent tabulce (customers).

![[Pasted image 20251222101037.png]]

**Kombinuje se s:**
- [[Data mapper]] - mapuje value objects
- [[Domain model]] - pro value objects v doméně

