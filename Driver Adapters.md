**Driver adapters** (მოძრავი ადაპტერები) არიან სისტემის ის ნაწილები, რომლებიც **გარე სამყაროდან იძახებენ თქვენს აპლიკაციას**, ანუ **ინიციატორები** არიან — ეს შეიძლება იყოს:

- REST API Controller
    
- CLI Command
    
- Scheduler / Cron Job
    
- Message Listener (Kafka Consumer)
    
- Test harness


[HTTP Request]
     ↓
[Web Controller] ← Driver Adapter
     ↓
[Application Service]
