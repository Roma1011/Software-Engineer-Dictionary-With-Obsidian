**Debt Log** არის **ჟურნალი/რეგისტრი**, სადაც ინახება და აღირიცხება სისტემაში არსებული **ტექნიკური ვალები**.  
ის მსგავსია როგორც ფინანსურ ბუღალტერიაში „ვალის წიგნი“ — მაგრამ აქ საუბარია პროგრამული სისტემის ისეთ პრობლემებზე, რომლებსაც _ახლა დროებით გვერდს ვუვლით_, მაგრამ მოგვიანებით უნდა მოვაგვაროთ.


## რატომ არის საჭირო?

- ტექნიკური ვალები („shortcuts“) ხშირად „იბნევიან“ პროექტის სისწრაფის გამო.
    
- თუ ეს არ აღირიცხა, გუნდი ავიწყდება და მერე დიდ პრობლემად იქცევა.
    
- Debt Log გვაძლევს:
    
    - **გამჭვირვალობას** — ყველამ იცის სად არის დავალიანება.
        
    - **პრიორიტიზაციას** — შეიძლება ზოგიერთი ვალი სასწრაფოა, ზოგი კი გაწელვადი.
        
    - **გეგმურობას** — ვალების დახურვა შეიძლება ჩავდოთ sprint backlog-ში ან tech improvement roadmap-ში.

## Debt Log-ის ტიპური ჩანაწერი

Debt Log შეიძლება იყოს უბრალო **Excel/Confluence/Jira board**.  
ჩანაწერი შეიცავს:

-  **ID** — უნიკალური ნომერი
    
-  **Description** — რა ტექნიკური ვალია (მაგ. „OrderService-ში hardcoded Stripe API key“)
    
-  **Category** — კოდი, ინფრასტრუქტურა, ტესტირება, უსაფრთხოება და სხვ.
    
-  **Impact** — როგორ აზიანებს სისტემას (performance, maintainability, risk…)
    
-  **Priority** — მაღალი / საშუალო / დაბალი
    
-  **Target Resolution** — როდის ვგეგმავთ დახურვას

|ID|Description|Category|Impact|Priority|Target Resolution|
|---|---|---|---|---|---|
|D-1|No unit tests for PaymentService|Testing|High risk of failure|High|Next sprint|
|D-2|Hardcoded config values in OrderService|Code|Hard to maintain|Medium|Q4|
|D-3|Legacy API integration without retry|Resilience|System instability|High|ASAP|
|D-4|Old library version with security issues|Security|Vulnerability risk|High|Q3|