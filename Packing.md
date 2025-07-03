**Packing** არის **კომპილატორის ან რანტაიმის ინსტრუქცია**, რომ **არ გამოიყენოს ან მინიმუმამდე დაიყვანოს Padding** მეხსიერებრივ სტრუქტურაში.  
ანუ, გაანაწილოს ველები **მიმდევრობით**, _რაც შეიძლება მჭიდროდ_, თუნდაც ეს დაარღვიოს ოპტიმალური alignment წესები.


[StructLayout(LayoutKind.Sequential, Pack = 1)]
public struct PackedCustomer {
    public byte Flag;         // 1 byte
    public int Balance;       // 4 bytes
    public short Year;        // 2 bytes
}

| Pack Value     | Alignment                                    |
| -------------- | -------------------------------------------- |
| `Pack = 1`     | No padding — ყველაზე მკაცრი                  |
| `Pack = 2/4/8` | ეტაპობრივი alignment-ზე დაფუძნებული          |
| default        | პლატფორმის alignment წესები (ზოგადად 4 ან 8) |

| რისკი                          | ახსნა                                                          |
| ------------------------------ | -------------------------------------------------------------- |
| **Performance degradation**    | CPU ვერ კითხულობს misaligned მონაცემებს ისე სწრაფად            |
| **Crash in native interop**    | Misaligned pointer access შეიძლება გამოიწვიოს access violation |
| **შეცდომები serialization-ში** | თუ შესაბამისი პლატფორმა packing-ს არ იცავს                     |