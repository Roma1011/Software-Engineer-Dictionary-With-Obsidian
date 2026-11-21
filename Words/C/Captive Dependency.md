### Captive Dependency

**Captive Dependency** არის Dependency Injection-ის შეცდომა, როცა **უფრო ხანგრძლივი სიცოცხლის სერვისი** თავის თავში ინახავს **უფრო ხანმოკლე სიცოცხლის დამოკიდებულებას**. შედეგად, ხანმოკლე დამოკიდებულება ვეღარ თავისუფლდება თავის დროზე და იმდენ ხანს ცოცხლობს, რამდენსაც მისი მფლობელი სერვისი.

ტერმინი Mark Seemann-მა შემოიტანა წიგნში *Dependency Injection in .NET*.

**ახსნა:**
.NET DI-ში სერვისს სამი სიცოცხლე აქვს:

| Lifetime      | რამდენ ხანს ცოცხლობს                                    |
| ------------- | ------------------------------------------------------- |
| **Singleton** | მთელი აპლიკაციის განმავლობაში, ერთი ეგზემპლარი          |
| **Scoped**    | ერთი scope-ის (ვებში: ერთი HTTP მოთხოვნის) განმავლობაში |
| **Transient** | ყოველ მოთხოვნაზე ახალი ეგზემპლარი                       |

სერვისმა შეიძლება მიიღოს მხოლოდ ისეთი დამოკიდებულება, რომელიც **მასზე ტოლი ან მეტი ხანი** ცოცხლობს.

**Captive Dependency** სწორედ ამ წესის დარღვევაა: სერვისი იღებს დამოკიდებულებას, რომელიც **მასზე ნაკლები ხანი** უნდა ცოცხლობდეს.

ქვემოთ `A → B` ნიშნავს: A სერვისი B-ს იღებს დამოკიდებულებად.

```
Singleton  →  Singleton   ✔
Scoped     →  Singleton   ✔
Scoped     →  Scoped      ✔
Transient  →  Scoped      ✔
Singleton  →  Scoped      ✘  Captive Dependency
Singleton  →  Transient   ✘  Captive Dependency
```

**მაგალითი:**

```csharp
builder.Services.AddDbContext<AppDbContext>();          // Scoped
builder.Services.AddSingleton<ReportCache>();           // Singleton

public class ReportCache
{
    private readonly AppDbContext _db;                   // ✘ singleton-ის სიცოცხლეს მიება

    public ReportCache(AppDbContext db) => _db = db;
}
```

აქ `AppDbContext` ერთი მოთხოვნისთვის იყო განკუთვნილი, მაგრამ singleton-ში მოხვედრის გამო მთელი აპლიკაციის სიცოცხლის განმავლობაში რჩება.

**რა პრობლემებს იწვევს:**

- **Thread safety**: `DbContext` არ არის thread-safe, singleton-ს კი ერთდროულად ბევრი მოთხოვნა იყენებს
- **მოძველებული მონაცემები**: change tracker ძველ entity-ებს ინახავს
- **მეხსიერების გაჟონვა**: ობიექტი არასდროს თავისუფლდება
- **Dispose-ის შეცდომა**: scope დაიხურება, singleton კი უკვე disposed ობიექტს მიმართავს (`ObjectDisposedException`)

**როგორ ვიპოვოთ:**
ASP.NET Core-ში Development გარემოში ჩართულია `ValidateScopes` და `ValidateOnBuild`, ამიტომ Singleton → Scoped შემთხვევაში აპლიკაცია გაშვებისას ისვრის:

```
InvalidOperationException: Cannot consume scoped service 'AppDbContext'
from singleton 'ReportCache'.
```

> [!WARNING]
> Singleton → Transient შემთხვევას ვალიდაცია **ვერ** იჭერს. Transient სერვისი singleton-ში ჩუმად თავადაც singleton ხდება.

**გამოსავალი:**

1. **სიცოცხლეების გათანაბრება**: თუ შესაძლებელია, `ReportCache` გახადე Scoped.
2. **`IServiceScopeFactory`**: singleton-ში საჭიროების დროს შექმენი საკუთარი scope:

```csharp
public class ReportCache
{
    private readonly IServiceScopeFactory _scopeFactory;

    public ReportCache(IServiceScopeFactory scopeFactory) => _scopeFactory = scopeFactory;

    public async Task<int> CountAsync()
    {
        using var scope = _scopeFactory.CreateScope();
        var db = scope.ServiceProvider.GetRequiredService<AppDbContext>();
        return await db.Reports.CountAsync();
    }
}
```

3. **Factory**: მაგალითად `IDbContextFactory<AppDbContext>`, რომელიც ყოველ ჯერზე ახალ ეგზემპლარს ქმნის.
4. **Options**: singleton-ში `IOptionsSnapshot<T>`-ის (Scoped) ნაცვლად გამოიყენე `IOptionsMonitor<T>` (Singleton).

|ტერმინი|აღწერა|
|---|---|
|**Captive Dependency**|„ხანმოკლე დამოკიდებულება ხანგრძლივი სიცოცხლის სერვისში ჩარჩება და მის ვადას იღებს"|
|**სწორი მიმართულება**|„დამოკიდებულება ყოველთვის ტოლ ან უფრო ხანგრძლივ სიცოცხლეზე"|
