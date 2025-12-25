> An object model of the
> domain that incorporates both
> behavior and data.

```cs
public class BankAccount
{
    public int Id { get; private set; }
    public decimal Balance { get; private set; }
    public string Owner { get; private set; }

    public BankAccount(string owner)
    {
        Owner = owner;
        Balance = 0;
    }

    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Částka musí být kladná");
        Balance += amount;
    }

    public void Withdraw(decimal amount)
    {
        if (amount > Balance)
            throw new InvalidOperationException("Nedostatečný zůstatek");
        Balance -= amount;
    }
}

// Použití:
var account = new BankAccount("Jan Novák");
account.Deposit(1000);
account.Withdraw(200); // Balance = 800
```

Model který má všechnu logiku pro danou entitu. Zapouzdřuje jak data, tak i chování (business logiku).

![[Pasted image 20251221132510.png]]

**Kombinuje se s:**
- [[Data mapper]] - pro oddělení persistence
- [[Unit Of Work]] - pro správu transakcí
- [[Service layer]] - pro orchestraci doménové logiky