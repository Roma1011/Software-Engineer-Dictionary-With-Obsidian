

# PascalCase

**განსაზღვრა:** იდენტიფიკატორი, სადაც **ყოველი სიტყვის** პირველი ასო **დიდია** და გამყოფები (სფეისი/ქვედხაზი) **არ არის**. напр.: `OrderService`, `UserId`, `GetByIdAsync`.

**სად გამოიყენება (.NET/C#):**

- **Namespaces, Types, Interfaces, Enums, Properties, Events, Methods** — ყველა საჯარო API ზედაპირი.
    
- **Public constants/static readonly** (`DefaultRetryCount`).
    

**რატომ:**  
წაკითხვადობა, სტანდარტიზაცია, საჯარო API-ს ერთგვაროვნება, tooling (Analyzer-ები/Refactoring) უკეთ მუშაობს.

**აკრონიმები:** გამოიყენე **Id, Http, Db, Xml** (არა `ID`, `HTTP`). напр.: `OrderId`, `HttpClient`, `DbContext`.

**მაგალითი (Idiomatic C#):**

```csharp
public sealed record OrderId(Guid Value);

public enum OrderStatus { Pending, Paid, Cancelled }

public interface IOrderRepository
{
    Task<Order?> FindAsync(OrderId id, CancellationToken ct);
}

public sealed class OrderService
{
    private readonly IOrderRepository _repository; // _camelCase field

    public OrderService(IOrderRepository repository) => _repository = repository;

    public async Task<Order?> GetByIdAsync(OrderId id, CancellationToken ct = default)
        => await _repository.FindAsync(id, ct);

    public int RetryCount { get; private set; } = 3;
}
```

**Checklist:**

- Types/Methods/Properties/Enums → **PascalCase**
    
- აკრონიმები → **Id/Http/Db/Xml** ფორმით
    
- Public constants → **PascalCase**
    

---

# camelCase

**განსაზღვრა:** იდენტიფიკატორი, სადაც **პირველი სიტყვის** პირველი ასო **პატარაა**, შემდეგი სიტყვების — **დიდი**. напр.: `userId`, `retryCount`, `cancellationToken`.

**სად გამოიყენება (.NET/C#):**

- **პარამეტრები და ლოკალური ცვლადები**.
    
- **Private ველები** — ხშირად `_camelCase` პრეფიქსით (`_userRepository`).
    

**რატომ:**  
ლოკალური და შიდა კონტექსტის გამოკვეთა; მკაფიო განსხვავება ტიპებსა და წევრებს შორის.

**მაგალითი:**

```csharp
public async Task<bool> TryConfirmAsync(OrderId orderId, int retryCount, CancellationToken cancellationToken)
{
    for (var attempt = 0; attempt < retryCount; attempt++)
    {
        var success = await ConfirmInternalAsync(orderId, cancellationToken);
        if (success) return true;
    }
    return false;
}
```

**Checklist:**

- Parameters/locals → **camelCase**
    
- Private fields → **_camelCase**
    
- Public API surface → **არასოდეს** camelCase
    

---

# სად ქმნის პრობლემას წესების უგულებელყოფა

**1) JSON კონტრაქტები და API-ს სტაბილურობა**

- ASP.NET Core-ში property-ები **PascalCase**-ია, მაგრამ JSON-ში ინდუსტრიული ნორმა **camelCase**.  
    თუ გამოიყენე არათანმიმდევრული სტილი (მაგ. ერთ endpoint-ში `orderId`, მეორეში `OrderID`), ფრონტზე გაჩნდება runtime-შეცდომები და **breaking change**-ები ვერსიებს შორის.
    
- `System.Text.Json`-ის ქარხნული წაკითხვა case-insensitive-ია, მაგრამ **გენერირებული/გარე კლიენტები** (JS/TS, მობილური SDK) ხშირად **case-sensitive** არიან.
    

```csharp
// რეკომენდებული: expose JSON camelCase, შენს C# პროპერტეები რჩება PascalCase-ში
builder.Services.AddControllers()
    .AddJsonOptions(o =>
        o.JsonSerializerOptions.PropertyNamingPolicy = JsonNamingPolicy.CamelCase);
```

**2) Swagger/OpenAPI & კლიენტ-გენერაცია**

- Naming-ის ქაოსი იძლევა ცუდად გენერირებულ მოდელებს (TS-ში `OrderID` vs `orderId`) და ხელს უშლის typed SDK-ების სტაბილურობას.
    

**3) SignalR / სათაურები / JS interop**

- JS მხარეს ობიექტების ველები **case-sensitive**-ია. არათანმიმდევრულობა იწვევს მყუდრო ბაგებს (`data.userId` vs `data.UserId`).
    

**4) EF Core & მონაცემთა ბაზები (განსაკუთრებით PostgreSQL)**

- PostgreSQL არაკონსისტენტური case-ისას ქმნის **დაბრუნებულ იდენტიფიკატორებს** (`"UserId"` საჭიროებს quote-ს, ხოლო `userId` — არა).
    
- უსისტემო PascalCase სქემები პოსტგრესში ხშირად აიძულებს quoted identifiers-ს — მძიმე SQL, მოულოდნელი შეცდომები. (პროექტის დასაწყისში შეარჩიე ერთიანი naming-strategy: DB-ში ხშირად **snake_case**, C#-ში **PascalCase**.)
    

**5) Source generators/Reflection/Keyed lookup-ები**

- თუ ინსტრუმენტი ქეიებს case-sensitive-ად ამუშავებს (Dictionary<string, …>), `UserId` და `userId` არის სხვადასხვა ქეი — subtle bug-ები კონვენციის დარღვევისას.
    

**6) Analyzers/Style Enforcement**

- Roslyn/StyleCop-ი გამუდმებით გააგდებს IDE warning-ებს ( напр. `IDE1006`) და კოდის რევიუები გადაიქცევა naming-დაბალანსებელ დისკუსიად, არა ბიზნეს-ლოგიკად.
    

**7) Domain Ubiquitous Language**

- `ID`, `URL`, `DB`-სავით ALLCAPS აკრონიმები არღვევენ Microsoft-ის სახელდების გაიდს (სწორია `Id`, `Url` არ არის რეკომენდებული; სჯობს `Uri`), ზრდიან კოგნიტურ ტვირთს.
    

---

## მოკლე „ოპერაციული“ წესები (დასაფიქსირებლად .editorconfig-ით)

`.editorconfig` ამონაჭერი:

```ini
[*.cs]

# PascalCase for public members (types, methods, properties, events)
dotnet_naming_rule.public_members_pascal.severity = warning
dotnet_naming_rule.public_members_pascal.symbols = public_members
dotnet_naming_rule.public_members_pascal.style = pascal_style

dotnet_naming_symbols.public_members.applicable_kinds = class,struct,interface,enum,method,property,event,delegate
dotnet_naming_symbols.public_members.applicable_accessibilities = public, protected, protected_internal
dotnet_naming_style.pascal_style.capitalization = pascal_case

# _camelCase for private fields
dotnet_naming_rule.private_fields_underscore_camel.severity = warning
dotnet_naming_rule.private_fields_underscore_camel.symbols = private_fields
dotnet_naming_rule.private_fields_underscore_camel.style = underscore_camel_style

dotnet_naming_symbols.private_fields.applicable_kinds = field
dotnet_naming_symbols.private_fields.applicable_accessibilities = private
dotnet_naming_style.underscore_camel_style.capitalization = camel_case
dotnet_naming_style.underscore_camel_style.required_prefix = _

# Parameters & locals: camelCase (via IDE analyzers; enforce in reviews/linters)
```

და აკრონიმების პრაქტიკა (რევიუ წესად დაფიქსირე):

- ✅ `OrderId`, `HttpClient`, `DbContext`, `XmlDocument`
    
- ❌ `OrderID`, `HTTPClient`, `DBContext`, `XMLDocument`
    

---

თუ გინდა, ამ ორ ჩანაწერს დავამატებ შენს „დიქშინარს“ Markdown-ფაილად და მაგავე პროექტში ჩაგიყრი `.editorconfig`-ს მინიმალური წესებით, რომ CI-ში Naming Warning-ებად გაქცეს.