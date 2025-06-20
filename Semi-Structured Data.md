Semi-Structured Data არის მონაცემების ტიპი, რომელსაც არ აქვს მკაცრი, ფიქსირებული სქემა როგორც რელაციურ მონაცემებში (structured), მაგრამ მაინც შეიცავს გარკვეულ ნიშნებს, რომლებიც საშუალებას აძლევს სტრუქტურის ან შინაარსის ანალიზს. ხშირად გამოიყენება დინამიურ ან კომპლექსურ მონაცემებთან მუშაობისას, განსაკუთრებით ვებ და აპლიკაციურ გარემოში.

**მახასიათებლები:**

- არ აქვს მკაცრი სვეტები და მონაცემთა ტიპები (როგორც RDBMS-ში)
    
- შეიცავს ტეგებს, მარკერებს ან სტრუქტურულ ელემენტებს
    
- შესაძლებელია ნაწილობრივ ან დინამიურად გაშიფვრა და დამუშავება
    
- მოქნილია და მარტივად ერგება ცვალებად მონაცემთა მოდელებს
    

**მაგალითები:**

- **JSON** (`{"name": "Ana", "age": 27}`)
    
- **XML** (`<user><name>Ana</name><age>27</age></user>`)
    
- **YAML**
    
- ზოგიერთი **CSV**, რომელსაც თან ერთვის მეტა-ინფორმაცია
    
- **მომხმარებლის ლოგები**, **სესიის მონაცემები**, **sensor data**
    

**შედარება:**

|ტიპი|სტრუქტურა|შენახვის ფორმატი|გამოყენების მაგალითები|
|---|---|---|---|
|**Structured**|მკაცრი სქემა|RDBMS, SQL|ბანკის ტრანზაქციები, CRM|
|**Semi-Structured**|ნაწილობრივ სტრუქტურული|JSON, XML, BSON|API-responses, log ფაილები|
|**Unstructured**|არაორგანიზებული|ტექსტი, ფოტოები, ვიდეოები|ელფოსტა, დოკუმენტები, მედია|

**სარგებელი:**

- მოქნილი სქემის thanks to schema-on-read
    
- მარტივად ტრანსფერული ვებსა და APIs-ში
    
- იდეალურია NoSQL ბაზებისთვის (MongoDB, Couchbase, Elasticsearch)