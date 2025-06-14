IaaS — ეს არის ღრუბლოვანი კომპიუტერული მომსახურების მოდელი, რომელიც მომხმარებლებს უზრუნველყოფს IT ინფრასტრუქტურის ძირითადი კომპონენტებით (ვირტუალური სერვერები, ქსელები, შენახვის სივრცე და ა.შ.) როგორც სერვისით, ინტერნეტის მეშვეობით. მომხმარებელი მართავს ოპერაციულ სისტემებს, აპლიკაციებს და მონაცემებს, ხოლო პროვაიდერი მართავს ფიზიკურ ინფრასტრუქტურას.

**მახასიათებლები:**

- რესურსების დინამიური provision და scale
    
- მომხმარებელი აკონტროლებს VM-ებს, ქსელებს, სტორეიჯს
    
- მოქნილი და დროში ეფექტური გარემო DevOps და CI/CD პროცესებისთვის
    
- “Pay-as-you-go” ფასების მოდელი
    

**მომსახურება ჩვეულებრივ მოიცავს:**

- ვირტუალური მანქანები (VMs)
    
- ბლოკური/ობიექტური შენახვა
    
- ვირტუალური ქსელები
    
- Load Balancing და Firewalls
    
- IP მისამართები, DNS, VPN
    

**პოპულარული IaaS პროვაიდერები:**

- **Amazon EC2 (AWS)**
    
- **Google Compute Engine (GCP)**
    
- **Microsoft Azure Virtual Machines**
    
- **DigitalOcean Droplets**
    
- **OpenStack (ღია კოდის ალტერნატივა)**
    

**სარგებელი:**

- არ საჭიროებს ფიზიკური სერვერების შენახვას ან მართვას
    
- სწრაფი გაშვება და ტესტირება სხვადასხვა გარემოში
    
- მარტივი რესურსების გაზრდა/შემცირება მოთხოვნის მიხედვით
    

**მაგალითი:**  
სტარტაპს სჭირდება დროებითი სერვერული ინფრასტრუქტურა აპლიკაციის ტესტირებისთვის. ისინი იყენებენ AWS EC2-ს, ქმნიან ვირტუალურ მანქანებს, აყენებენ საკუთარ ოპერაციულ სისტემას და იწყებენ ტესტირებას რამდენიმე წუთში.


### შეჯამება: IaaS vs PaaS vs SaaS

|მახასიათებელი|IaaS|PaaS|SaaS|
|---|---|---|---|
|მიზანი|ინფრასტრუქტურის გაქირავება|აპლიკაციების პლატფორმა|მზა პროგრამული სერვისი|
|მომხმარებელი მართავს|VM-ებს, OS-ს, DB-ს|მხოლოდ კოდს და აპლიკაციას|მხოლოდ კონფიგურაციას და მონაცემს|
|მაგალითები|AWS EC2, Google Compute|Heroku, GAE, Elastic Beanstalk|Gmail, Google Docs, Zoom|