**Software Architecture**–ის კონტექსტში **Volatility** ნიშნავს **იმის სიხშირეს და ალბათობას, რომ სისტემის კონკრეტული ნაწილი შეიცვლება**.

ანუ, რომელი მოდული/კომპონენტი **უფრო ხშირად შეიცვლება მომავალში** ბიზნესის, ტექნოლოგიის ან გარემოს ცვლილების გამო.

### მაგალითები:

- **High-volatility areas**
    
    - Business rules (ხშირად იცვლება რეგულაციების ან ბიზნესის სტრატეგიის გამო)
        
    - UI layer (მომხმარებლის მოთხოვნების ცვლილებით)
        
    - Integration adapters (რადგან გარე API-ები იცვლება)
        
- **Low-volatility areas**
    
    - Core algorithms (მაგ., კრიპტოგრაფიული ბიბლიოთეკა)
        
    - Database fundamentals (primary keys, identity concepts)
        
    - Stable protocols (TCP/IP stack)


### რატომ არის მნიშვნელოვანი

არქიტექტორი ცდილობს **ცვლილებების იზოლაციას**:

- მაღალი volatility-ით ზონები **გამოეყოს დამოუკიდებელ bounded context–ებში ან მოდულებში**,
    
- შეიქმნას **დამაბალანსებელი abstraction-ები (interfaces, ports, adapters)**,
    
- და არ მოხდეს volatility propagation (ანუ რომ ცვლილებამ ერთ მოდულში მთელი სისტემა არ "გატეხოს").