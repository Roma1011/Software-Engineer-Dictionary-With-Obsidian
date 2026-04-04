**Plain Old Objects** ნიშნავს **მარტივ ობიექტებს**, რომლებიც არ არიან დამოკიდებული სპეციალურ framework-ზე, ბიბლიოთეკაზე ან რთულ ინფრასტრუქტურულ მექანიზმებზე.

## ტერმინის წარმოშობა

ეს ტერმინი პირველად გაჩნდა **Java-ში**:

**POJO — Plain Old Java Object**

შემდეგ იგივე იდეა გავრცელდა სხვა ენებშიც:

- **POCO** — Plain Old CLR Object (C#)
- **POPO** — Plain Old PHP Object
- **POJO/POCO მსგავსი ობიექტები** სხვა ენებშიც

## რას ნიშნავს პრაქტიკაში

Plain Old Object არის კლასი, რომელიც:

- არ არის დამოკიდებული framework-ზე
- არ მემკვიდრეობს framework-ის base class-ს
- არ საჭიროებს სპეციალურ lifecycle-ს
- არ იყენებს framework-ის სპეციფიკურ annotation-ებს ან attributes-ებს (ან მინიმალურად იყენებს)