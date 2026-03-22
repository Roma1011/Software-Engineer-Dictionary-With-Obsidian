**Schema Registry** ნიშნავს **ცენტრალურ საცავს (registry)**, სადაც ინახება და მართულია **მონაცემთა სქემები** (schemas), რომლებსაც იყენებენ სხვადასხვა სისტემა ან სერვისი მონაცემების გაცვლისას.

**Schema Registry** არის სერვისი, რომელიც:

- ინახავს message / event / data schema-ებს (მაგ. Avro, JSON Schema, Protobuf)
    
- აკონტროლებს მათ ვერსიონირებას
    
- ამოწმებს **compatibility-ს** (backward / forward)
    

### საჭიროება

Distributed systems-ში (Kafka, Event-Driven Architecture):

- Producer აგზავნის message-ს
    
- Consumer კითხულობს message-ს
    

თუ schema შეუთანხმებლად შეიცვალა → სისტემა დაზიანდება.

### მუშაობის პრინციპი

- **Producer**
    
    - სქემას არ აგზავნის პირდაპირ
        
    - აგზავნის **schema ID-ს**
        
- **Schema Registry**
    
    - ინახავს schema-ს
        
    - ამოწმებს: ახალი schema compatible-ია თუ არა ძველთან
        
- **Consumer**
    
    - schema ID-ით იღებს სწორ schema-ს
        
    - სწორად კითხულობს message-ს


### მაგალითი


```

Schema v1
{
  "type": "record",
  "name": "UserCreated",
  "fields": [
	{ "name": "id", "type": "string" },
	{ "name": "email", "type": "string" }
  ]
}

Schema v2
{
  "type": "record",
  "name": "UserCreated",
  "fields": [
    { "name": "id", "type": "string" },
    { "name": "email", "type": "string" },
    { "name": "name", "type": ["null", "string"], "default": null }
  ]
}
```


## Schema Registry და Compatibility

Schema Registry ხშირად ამოწმებს:

- [[Backward compatibility]]
    
- [[Forward compatibility]]
    
- [[Full compatibility]]