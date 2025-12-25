> An object that encapsulates access to an external system or resource.

```cs
// Gateway pro externí API
public class PaymentGateway
{
    private readonly HttpClient _client;

    public PaymentGateway(string apiUrl)
    {
        _client = new HttpClient { BaseAddress = new Uri(apiUrl) };
    }

    public PaymentResult ProcessPayment(decimal amount, string cardNumber)
    {
        var request = new { amount, cardNumber };
        var response = _client.PostAsJsonAsync("/payments", request).Result;
        return response.Content.ReadAsAsync<PaymentResult>().Result;
    }

    public PaymentStatus GetPaymentStatus(string paymentId)
    {
        var response = _client.GetAsync($"/payments/{paymentId}").Result;
        return response.Content.ReadAsAsync<PaymentStatus>().Result;
    }
}

// Použití:
var gateway = new PaymentGateway("https://api.payment.com");
var result = gateway.ProcessPayment(100.50m, "1234-5678-9012-3456");
```

Zapouzdřuje přístup k externímu systému (API, databáze, filesystem). Poskytuje jednodušší rozhraní pro práci s externí resource.

![[Pasted image 20251225091245.png]]

**Příklady:**
- [[Table data gateway]] - pro přístup k databázové tabulce
- [[Row data gateway]] - pro přístup k řádku v databázi

**Kombinuje se s:**
- [[Service layer]] - používá gateway pro externí systémy
- [[Data Transfer Object]] - pro přenos dat přes gateway

