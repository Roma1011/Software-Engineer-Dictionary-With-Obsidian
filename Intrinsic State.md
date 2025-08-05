**Intrinsic State** — ობიექტის **შიდა, მუდმივი და გაზიარებადი მდგომარეობა**, რომელიც არ იცვლება კონტექსტის მიხედვით და შეიძლება გამოყენებულ იქნას მრავალი ობიექტის მიერ მეხსიერების დაზოგვის მიზნით.

ეს არის ის ნაწილი ობიექტის მონაცემებისა, რომელიც **ყველა კონტექსტში ერთნაირია**.

|ტიპი|ახსნა|
|---|---|
|**Intrinsic State**|მუდმივი მონაცემი, რომელიც შეიძლება ბევრმა ობიექტმა გაზიაროს. ინახება Flyweight ობიექტში.|

```csharp
public class Character
{
    private char _symbol; // Intrinsic State
    private string _font; // Intrinsic State

    public Character(char symbol, string font)
    {
        _symbol = symbol;
        _font = font;
    }

    public void Draw(int x, int y) // Extrinsic State
    {
        Console.WriteLine($"Drawing {_symbol} with {_font} at ({x}, {y})");
    }
}
```


- **Intrinsic State** = ობიექტის „შიგნით ჩაშენებული“ და უცვლელი მონაცემი
    
- ინახება Flyweight ობიექტში და შეიძლება გაიზიაროს ბევრი კონტექსტი
    
- ამით მცირდება მეხსიერების ხარჯი