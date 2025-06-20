Load Balancing — ეს არის ტექნიკა, რომელიც ანაწილებს შემომავალ ტრაფიკს ან სამუშაოს მრავალ სერვერსა თუ რესურსზე, რათა უზრუნველყოს სისტემის სტაბილურობა, ეფექტურობა, მაღალ ხელმისაწვდომობა და სწრაფი რეაგირება. იგი კრიტიკულია მასშტაბირებად და განაწილებულ სისტემებში.

**მიზნები:**

- მომხმარებელთა მოთხოვნების ოპტიმალური გადანაწილება
    
- გადატვირთვის თავიდან აცილება
    
- სისტემის გამტარობის ზრდა
    
- ხელმისაწვდომობის და წარმადობის შენარჩუნება, თუნდაც ზოგიერთი კვანძი ჩავარდეს
    

**ტიპები:**

- **Layer 4 Load Balancing:** ბალანსირება TCP/UDP დონეზე (მაგ. IP, პორტის მიხედვით)
    
- **Layer 7 Load Balancing:** ბალანსირება აპლიკაციის დონეზე (მაგ. URL, cookie, header-ის მიხედვით)
    
- **Round Robin:** მოთხოვნები რიგობითად ნაწილდება
    
- **Least Connections:** მოთხოვნა მიეწოდება სერვერს, რომელსაც ნაკლები კავშირი აქვს
    
- **IP Hashing:** მომხმარებლის IP-ზე დაყრდნობით ხდება გადანაწილება
    

**ტექნოლოგიები და სერვისები:**

- **ცნობილი ინსტრუმენტები:** NGINX, HAProxy, AWS Elastic Load Balancer (ELB), Azure Load Balancer, Kubernetes Ingress
    
- **Hardware Load Balancers:** F5, Citrix ADC
    

**მაგალითი:**  
თუ ვებსაიტს 3 სერვერი ემსახურება და ერთდროულად 1000 მომხმარებელი შედის, Load Balancer ანაწილებს ამ მომხმარებლებს ამ სერვერებზე ისე, რომ არცერთი არ გადატვირთდეს და ყველა მიიღოს სწრაფი რეაგირება.