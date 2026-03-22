**Event-based Asynchronous Pattern (EAP)** — ეს არის .NET-ში გამოყენებული პატერნი, სადაც ასინქრონული ოპერაციის დაწყება ხდება მეთოდით, ხოლო დასრულებისას იწერება **Event** (ღონისძიება), რომლითაც კლიენტი იგებს შედეგს.


|თვისება|ახსნა|
|---|---|
|**Event-based**|Completion და Progress რეგისტრირდება Event-ებით|
|**არ ბლოკავს UI-ს**|კარგი Windows Forms/WPF UI აპებში|
|**ჭარბი boilerplate**|ბევრია Event handler-ები და delegate-ები|
|**კომპლექსური შეცდომების მართვა**|Exception უნდა შეამოწმო `EventArgs.Error`-ში|


| პატერნი                                        | აღწერა                                                     |
| ---------------------------------------------- | ---------------------------------------------------------- |
| **[[APM]] (Asynchronous Programming Model)**   | `BeginXxx` / `EndXxx` სტილი delegate-ებით (`IAsyncResult`) |
| **[[EAP]] (Event-based Asynchronous Pattern)** | Event-ებით მუშაობს, უფრო Friendly UI აპებისთვის            |
| **[[TAP]] (Task-based Asynchronous Pattern)**  | თანამედროვე სტანდარტი `Task` + `async/await` სინტაქსით     |
