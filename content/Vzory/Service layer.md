> Defines an application's
> boundary with a layer of
> services that establishes a set of
> available operations and
> coordinates the application's
> response in each operation.

```cs
public class OrderService
{
    private readonly IOrderRepository _orderRepo;
    private readonly ICustomerRepository _customerRepo;
    private readonly IUnitOfWork _unitOfWork;

    public void PlaceOrder(int customerId, List<OrderItem> items)
    {
        var customer = _customerRepo.Find(customerId);
        if (!customer.CanPlaceOrder())
            throw new InvalidOperationException("Zákazník nemůže objednat");

        var order = new Order(customer);
        foreach (var item in items)
            order.AddItem(item);

        _orderRepo.Add(order);
        _unitOfWork.Commit();
    }

    public OrderDTO GetOrderDetails(int orderId)
    {
        var order = _orderRepo.Find(orderId);
        return MapToDTO(order);
    }
}
```

Definuje aplikační rozhraní - sadu operací, které aplikace poskytuje. Koordinuje doménovou logiku a transakce.

**Kombinuje se s:**
- [[Domain model]] - orchestruje doménové objekty
- [[Transaction script]] - obsahuje transaction scripty
- [[Unit Of Work]] - řídí transakce
- [[Data Transfer Object]] - pro přenos dat mezi vrstvami