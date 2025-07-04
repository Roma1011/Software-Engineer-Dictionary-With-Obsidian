**Tight coupling** არის პროგრამული კომპონენტების (მაგ. კლასი, მოდული, სერვისი) **ერთმანეთზე ძლიერი დამოკიდებულება**, რაც იმას ნიშნავს, რომ ერთის ცვლილება აუცილებლად ითხოვს მეორის ცვლილებას.  
ეს არღვევს მოქნილობას, ზრდის კოდური ცვლილების რისკს და აფერხებს სკალირებას.

- მოდულ A-ს კარგად ესმის მოდულ B-ის შიდა ლოგიკა
    
- თუ B-ს შევცვლით — A **გატყდება**
    
- დამოუკიდებელი ტესტირება რთულდება
    
- Refactor / Replace ერთ კომპონენტს? — მთელ სისტემას ეშლება

|ტერმინი|აღწერა|
|---|---|
|**Tight coupling**|„ყველა იცნობს ერთმანეთის შიგნეულობას – ცვლილება ყველას ეხება“|
|**Loose coupling**|„კომუნიკაცია კონტრაქტის ფარგლებში – შიგნით რაც ხდება, სხვის საქმე არ არის“|