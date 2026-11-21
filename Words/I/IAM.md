### Identity and Access Management

**Identity and Access Management (IAM)** არის სისტემებისა და პროცესების ერთობლიობა, რომელიც უზრუნველყოფს **მომხმარებლების, სერვისებისა და სხვა სუბიექტების იდენტობისა და მათზე წვდომის უფლებების მართვას**.

**ახსნა:**  
IAM პასუხობს ძირითადად სამ კითხვას:

1. **ვინ არის ეს?** — Identity / Authentication
2. **რისი გაკეთება შეუძლია?** — Authorization
3. **რაზე აქვს წვდომა?** — Access Control

მაგალითად:

```
User
 ↓
Authentication
 ↓
Identity
 ↓
Role / Policy
 ↓
Authorization
 ↓
Resources
```

IAM-ის სისტემები შეიძლება მართავდეს:

- მომხმარებლებს
- ჯგუფებს
- როლებს
- permissions-ს
- policies-ს
- authentication-ს
- authorization-ს