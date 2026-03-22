ნიშნავს არქიტექტურულ მიდგომას, სადაც ერთი აპლიკაცია ემსახურება მრავალ კლიენტს (tenant-ს) ისე, რომ მათი მონაცემები და კონფიგურაცია ერთმანეთისგან იზოლირებულია.

### ერთი სისტემა → ბევრი კლიენტი → იზოლირებული მონაცემები

Tenant არის დამოუკიდებელი Entity რომელიც იყენებს ერთსა და იმავე აპლიკაციას.

მაგალითად:

- NPS სისტემა → სხვადასხვა ბრენდი
    
- SaaS CRM → სხვადასხვა კლიენტი

## Multitenancy-ის ძირითადი მოდელები

###  1. Shared Database, Shared Tables (ყველაზე გავრცელებული)

	ყველა tenant ერთ DB-შია, ერთ table-ებში, მაგრამ აქვთ `TenantId`.

### 2. Shared Database, Separate Schemas

	`tenant1.Orders tenant2.Orders`

### 3. Separate Database per Tenant
	DB_Tenant1
	DB_Tenant2
