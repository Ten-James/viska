> An object that sets up a communication between two independent objects.

```cs
// Mapper mezi doménou a DTO
public class CustomerDtoMapper
{
    public CustomerDTO ToDto(Customer customer)
    {
        return new CustomerDTO
        {
            Id = customer.Id,
            FullName = $"{customer.FirstName} {customer.LastName}",
            Email = customer.Email
        };
    }

    public Customer ToDomain(CustomerDTO dto)
    {
        var names = dto.FullName.Split(' ');
        return new Customer
        {
            Id = dto.Id,
            FirstName = names[0],
            LastName = names.Length > 1 ? names[1] : "",
            Email = dto.Email
        };
    }
}

// Mapper mezi objekty a databází
public class OrderMapper
{
    public Order MapFromDatabase(DataRow row)
    {
        return new Order
        {
            Id = (int)row["id"],
            Total = (decimal)row["total"],
            OrderDate = (DateTime)row["order_date"]
        };
    }

    public void MapToDatabase(Order order, DataRow row)
    {
        row["id"] = order.Id;
        row["total"] = order.Total;
        row["order_date"] = order.OrderDate;
    }
}
```

Obecný vzor pro překlad mezi dvěma nezávislými objektovými modely. Odděluje systémy od sebe.

![[Pasted image 20251225091337.png]]

**Příklady:**
- [[Data mapper]] - mezi objekty a databází

**Kombinuje se s:**
- [[Data Transfer Object]] - mapování mezi doménou a DTO
- [[Service layer]] - pro transformaci dat
- [[Gateway]] - pro transformaci dat z/do externích systémů

