Integration Strength = რამდენად დამოკიდებულია ერთი სისტემა მეორეზე ინტეგრაციისას.

ანუ ზომავს:

- რამდენად ძლიერი კონტრაქტებია მათ შორის,
    
- რამდენად რთულია შეცვლა/ჩანაცვლება,
    
- რამდენად tight vs loose coupling–ია კავშირისას.


### Integration Strength–ის დონეები

1. **Weak Integration (Loose coupling)**
    
    - ორი სისტემა მინიმალურად იცნობს ერთმანეთს
        
    - ურთიერთობს მხოლოდ abstraction–ის (interface, message contract) დონეზე
        
    - შეცვლა/ჩანაცვლება ადვილია
        
    - მაგალითი: Event-driven integration (Kafka, RabbitMQ, Domain Events)
        
2. **Moderate Integration**
    
    - უკვე იციან ერთმანეთის სქემა/კონტრაქტი
        
    - მაგრამ მაინც abstraction-ით გამოყოფილია
        
    - მაგალითი: REST API ინტეგრაცია Swagger/OpenAPI კონტრაქტით
        
3. **Strong Integration (Tight coupling)**
    
    - ერთი სისტემა პირდაპირ ეყრდნობა მეორის კონკრეტულ იმპლემენტაციას
        
    - Schema ან API ცვლილება შეიძლება სისტემას გატეხოს
        
    - მაგალითი: პირდაპირი DB access shared database–ით