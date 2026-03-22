არქიტექტურაში **touchpoint** ნიშნავს ადგილს, სადაც **ორი სისტემა ან ორი bounded context ერთმანეთთან ურთიერთობს**.

მაგალითად:

- API call
- message queue
- database integration
- webhook
- event stream

DDD-ში ხშირად ამბობენ:

> **Bounded contexts always have touchpoints.**

ანუ სხვადასხვა bounded context აუცილებლად უნდა **ინტეგრირდეს ერთმანეთთან გარკვეულ წერტილებში**.

მაგალითად:

Billing Context  →  Payment Context

მათ შორის **touchpoint** შეიძლება იყოს:

- REST API
- Event (Kafka / RabbitMQ)
- Shared contract

## DDD კონტექსტში

**Touchpoints** არის ის ადგილები, სადაც:

- სხვადასხვა **bounded context**
- სხვადასხვა **მოდელი**
- სხვადასხვა **language**

ერთმანეთთან **კონტრაქტით ინტეგრირდება**.

ამიტომ ტექსტებში ხშირად წერია:

> "There will always be touchpoints between bounded contexts."