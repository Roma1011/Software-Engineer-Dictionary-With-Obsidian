დროებითი მეხსიერება შესრულებისთვის\

|ტიპი|Volatile Storage 🧠|Non-Volatile Storage 💾|Random Access|Byte Addressable|Block Addressable|Sequential Access|
|---|---|---|---|---|---|---|
|**განსაზღვრება**|ინახავს მონაცემს მხოლოდ მაშინ, როცა ჩართულია დენი|ინახავს მონაცემს მუდმივად, დენის გარეშეც|||||
|**მონაცემის დაცვა**|დროებითია|მუდმივია|||||
|**სიჩქარე**|სწრაფია (ns/µs)|ნელა (µs/ms და მეტიც)|||||
|**მაგალითები**|CPU Register, Cache, RAM|SSD, HDD, Flash, NVMe, ROM|||||
|**გამოყენება**|პროგრამის დროებითი შესრულება|ფაილებისა და სისტემების გრძელვადიანი შენახვა|||||
|**Random Access**|✅|⚠️ (SSD, NVMe)|✅|⚠️ (SSD)|✅ (SSD, HDD)|⚠️ HDD/Tape|
|**Byte Addressable**|✅ (RAM, Cache)|❌ (ბლოკური მოწყობილობები)|✅ (RAM)|❌|❌|❌|
|**Block Addressable**|❌|✅ (SSD, HDD, Flash)|❌|❌|✅|✅ (in HDD/Tape)|
|**Sequential Access**|❌|✅ (HDD, Tape, Flash)|❌|❌|✅ (mostly)|✅|