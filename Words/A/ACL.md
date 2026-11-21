### Access Control List

**ACL** წვდომის კონტროლის მექანიზმი, რომელიც კონკრეტული რესურსისთვის ინახავს წესების ერთობლიობას და განსაზღვრავს, რომელ სუბიექტს რა უფლებები აქვს ამ რესურსზე.


მაგალითად:

```
File: report.pdf

Roma     → Read, Write
Lika     → Read
Guest    → No Access
```

ACL პირდაპირ **რესურსთან არის დაკავშირებული**.

მაგალითად:

```
File
 └── ACL
      ├── Roma → Read/Write
      ├── Lika → Read
      └── Guest → Deny
```