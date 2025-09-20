100 Continue – სერვერი ეუბნება კლიენტს, რომ მოთხოვნა შეიძლება გაგრძელდეს (დიდი body).
101 Switching Protocols – პროტოკოლის შეცვლა (HTTP → WebSocket).
102 Processing – მიღებულია, მაგრამ დამუშავება არ დასრულებულა (WebDAV).
103 Early Hints – წინასწარი headers, სანამ ძირითადი response მოვა.

2xx – წარმატებული
200 OK – მოთხოვნა წარმატებით შესრულდა.
201 Created – რესურსი შეიქმნა (POST /users).
202 Accepted – მიღებულია, დამუშავება გაგრძელდება (async).
204 No Content – წარმატებული, მაგრამ ცარიელი response (DELETE).
206 Partial Content – მხოლოდ ნაწილი დაბრუნდა (Range requests).

3xx – გადამისამართება
301 Moved Permanently – რესურსი სამუდამოდ სხვა მისამართზეა.
302 Found / Redirect – დროებითი გადამისამართება.
303 See Other – POST-ის შემდეგ გადამისამართება GET-ით.
307 Temporary Redirect – დროებითი redirect, მეთოდი უცვლელი.
308 Permanent Redirect – მუდმივი redirect, მეთოდი უცვლელი.

4xx – კლიენტის შეცდომები
400 Bad Request – მოთხოვნა არასწორია (არასწორი JSON).
401 Unauthorized – საჭიროა ავტორიზაცია.
403 Forbidden – წვდომა აკრძალულია.
404 Not Found – რესურსი არ არსებობს.
405 Method Not Allowed – მეთოდი არაა დაშვებული (POST GET-ზე).
409 Conflict – კონფლიქტი (მაგ. დუბლირებული Email).
410 Gone – რესურსი სამუდამოდ წაშლილია.
415 Unsupported Media Type – მიუღებელი Content-Type.
422 Unprocessable Entity – ვალიდაციის შეცდომა (მაგ. მოკლე პაროლი).
429 Too Many Requests – Rate limiting (გადაჭარბებული მოთხოვნები).
451 Unavailable for Legal Reasons – იურიდიული მიზეზით დაბლოკილი.

5xx – სერვერის შეცდომები
500 Internal Server Error – სერვერზე გაუთვალისწინებელი შეცდომა.
501 Not Implemented – ფუნქცია არ არის იმპლემენტირებული.
502 Bad Gateway – გარე სერვერის არასწორი response.
503 Service Unavailable – დროებით მიუწვდომელია (Overload / Maintenance).
504 Gateway Timeout – proxy-მ ვერ მიიღო პასუხი.
507 Insufficient Storage – სერვერს სივრცე არ ჰყოფნის.
511 Network Authentication Required – ქსელის ავტორიზაციაა საჭირო (Captive Portal).

გამოყენების წესები:
- 2xx წარმატებული ოპერაციებისთვის.
- 3xx რესურსის მისამართის ცვლილებისთვის.
- 4xx კლიენტის შეცდომებისთვის (ვალიდაცია, ავტორიზაცია).
- 5xx სერვერის შეცდომებისთვის.