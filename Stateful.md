

**Stateful** ობიექტს ან სისტემას აქვს **შიდა მდგომარეობა (state)**,  
რომელიც **შეიცვლება დროთა განმავლობაში**  
და ამ მდგომარეობის ცოდნა აუცილებელია მისი სწორად მუშაობისთვის.

ანუ:
> stateful ობიექტს **გახსოვს წარსული**.


### მახასიათებლები:

- შიდა ველები/მონაცემები იცვლება და ინახება.
    
- ერთი ოპერაციის შედეგი დამოკიდებულია წინა ოპერაციებზე.
    
- ობიექტი ან სერვისი შეიძლება იმუშაოს არასწორად, თუ მისი state დაიკარგება.
    

---

###  მაგალითები:

- **class BankAccount** → აქვს balance, რომელიც იცვლება.
    
- **Entity Framework-ის DbContext** → ინახავს ChangeTracker-ს.
    
- **TCP connection** → ინახავს session-ის მდგომარეობას.
    
- **Shopping Cart** → ინახავს პროდუქტის სიას.


```csharp
class Counter
{
    private int count = 0;

    public int Next()
    {
        count++;      // state-changing
        return count; // result depends on previous calls
    }
}
```
