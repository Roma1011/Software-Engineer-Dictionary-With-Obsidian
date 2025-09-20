
- **DRY (Don’t Repeat Yourself) — „არ გაიმეორო თავი“**  
    ერთი ცოდნა/ლოგიკა უნდა არსებობდეს ერთ ადგილას.  
    _რჩევა:_ საერთო ინფრა ლოგიკა გადაიტანე `DomainService`/`SharedKernel`-ში, გამოიყენე Extension-ები და Reusable Middleware. Over-abstraction თავიდან აიცილე.
    
- **KISS (Keep It Simple, Stupid) — „სულელი simplicity დაამარცხე“**  
    უმარტივესი სამუშაო გამოსავალი ჯობია ზედმეტ ფენებს.  
    _რჩევა:_ თავიდან ერთი Handler/Service საკმარისია; Pipeline/Decorator მხოლოდ მაშინ დაამატე, როცა სჭირდება.
    
- **YAGNI (You Aren’t Gonna Need It) — „ახლა არ გჭირდება — არ წერ“**  
    ჰიპოთეტურ ფუნქციებს ნუ აშენებ წინასწარ.  
    _რჩევა:_ feature toggle/backlog, მაგრამ კოდი მხოლოდ მიმდინარე საჭიროებაზე.
    
- **LOD (Law of Demeter) — „მეზობლის კანონი“**  
    ობიექტი კითხულობს მხოლოდ უშუალო მეზობლებს; არ გააკეთო `a.B().C().D`.  
    _რჩევა:_ მიეცი Facade/Service, ან გაატარე DTO; ხელს უშლის brittle „ჯაჭვებს“.
    
- **SRP (Single Responsibility Principle) — „ერთი პასუხისმგებლობა“**  
    კლასს უნდა ჰქონდეს ცვლილების ერთი მიზეზი.  
    _რჩევა:_ CommandHandler ცალკეა, Validator/Mapper/Repository ცალკე. არ აურიო ტრანზაქცია, ლოგიკა და I/O.
    
- **OCP (Open/Closed Principle) — „გახსნილი გაფართოებაზე, დახურული მოდიფიკაციაზე“**  
    ახალი ქცევა ემატება გაფართოებით/ინექციით, არა ძველი კოდის შეხებით.  
    _რჩევა:_ Strategy/Policy კლასები + DI, `IOptions<>`, `IEnumerable<TStrategy>`.
    
- **LSP (Liskov Substitution) — „შვილები მშობლის ადგილას“**  
    subtype-მა არ უნდა დაარღვიოს parent კონტრაქტი.  
    _რჩევა:_ ინტერფეისების კონტრაქტები მკაფიოდ განსაზღვრე; არ ჩააგდო `NotSupportedException` ძირითად გზაზე.
    
- **ISP (Interface Segregation) — „დაპირდაპირე მცირე ინტერფეისები“**  
    ბევრ პატარა ინტერფეისს უპირატესობა აქვს ერთ დიდზე.  
    _რჩევა:_ დაშალე `IPrinter` → `IPrint`, `IScan`, `IFax`; Handlers/Ports იყვნენ ფოკუსირებული.
    
- **DIP (Dependency Inversion) — „დამოკიდებულება აბსტრაქციებზე“**  
    მაღალი დონე არ უნდა იყოს დაბალზე დამოკიდებული; ორივე — აბსტრაქციებზე.  
    _რჩევა:_ ყველა Infra კოდი Domain/Application-ში მოდის ინტერფეისებით; ასწორებს ტესტირებისა და შეცვლის ფასს.