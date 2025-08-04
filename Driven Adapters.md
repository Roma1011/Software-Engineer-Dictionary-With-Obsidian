**Driven adapters** არიან ის კომპონენტები, რომლებსაც **თქვენი აპლიკაცია იძახებს**  ისინი **შეასრულებენ რეალურ სამუშაოს გარე სამყაროში**: მონაცემების შენახვა, ფაილის წერა, სერვისთან კავშირი და სხვ.

იგი „მართულია“ აპლიკაციის ბირთვისგან (core logic) — hence _driven_.


[Application Service]
     ↓
[UserRepository (Interface)]
     ↓
[MongoUserRepo] ← Driven Adapter
     ↓
[MongoDB]


