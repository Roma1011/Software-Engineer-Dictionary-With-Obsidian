
| ფორმატი      | ვიზუალი      | მთავარი გამოყენება                                    | .NET რჩევა                            |
| ------------ | ------------ | ----------------------------------------------------- | ------------------------------------- |
| `snake_case` | `first_name` | SQL columns, Redis keys, Python configs               | API/DB world-ში OK; C# კოდში იშვიათად |
| `kebab-case` | `first-name` | URLs, CSS class-ები, REST paths                       | გამოიყენე route/template-ებში         |
| `camelCase`  | `firstName`  | local variables, parameters, private fields (w/o `_`) | C# კოდში default variable style       |
| `PascalCase` | `FirstName`  | Classes, Records, Public Properties/Methods, Enums    | C# public surface                     |
## 1) `snake_case`

**აღწერა:** სიტყვები პატარა ასოებით, გამყოფი `_`.  
**Example (DB):**

`CREATE TABLE users (   user_id     INT PRIMARY KEY,   first_name  NVARCHAR(100),   last_name   NVARCHAR(100) );`

**Როდის ვხმარობთ**

- **DB schemas/columns**, **ENV/CFG keys** (`MAX_WORKERS`), ზოგჯერ **JSON** თუ შეთანხმებულია კლიენტთან.
    
- Data engineering पाइპლაინები (CSV headers, S3 paths).
    

**Რას ერიდო**

- C# public members-ში არ გამოიყენო; გართულდება consistency და Roslyn analyzers-თან კონფლიქტი.
    




## 2) `kebab-case`

**აღწერა:** სიტყვები პატარა ასოებით, გამყოფი `-`.  
**Example (REST URL):**

`GET /api/v1/user-profiles/{user-id}/audit-logs`

**Როდის ვხმარობთ**

- **URLs/Routes**, **CSS class names**, ზოგჯერ **file names** CLI/scriptებისთვის.
    

**Რას ერიდო**

- C# identifiers-_ში_ დაუშვებელია `-`. გამოიყენე მხოლოდ ტექსტურ/როუტ/ფაილ დონეზე.
    



---

## 3) `camelCase`

**აღწერა:** პირველი სიტყვა პატარა, შემდეგები – UpperCamel შიგნით.  
**Example (C#):**

`var firstName = input.FirstName; int maxRetries = 3;`

**Როდის ვხმარობთ (.NET)**

- **Local variables**, **parameters**, ზოგჯერ **private fields** (თუ `_` არ გსურს).
    
- **JSON body field-ები** ხშირად camelCase-ია ფრონტში (JS კლიენტები).
    

**Pitfalls**

- Serialization mismatch: C# property `FirstName` ↔ JSON `firstName`. მოასწორე serializer options-ით.
    



---

## 4) `PascalCase`

**აღწერა:** ყველა სიტყვა დიდი ასოთი იწყება.  
**Example (C# Public API):**

`public sealed class CustomerOrder
{    
public Guid OrderId { get; init; }   
public string FirstName { get; init; } = default!;    
public string LastName  { get; init; } = default!;     
public decimal TotalAmount { get; private set; } 
}
`

**Როდის ვხმარობთ (.NET)**

- **Classes/Records/Structs**, **Public Properties/Methods**, **Enums**, **Namespaces**.
    
