
**Driver Port** (ასევე ცნობილი როგორც **Primary Port**) არის **ინტერფეისი**, რომელიც აღწერს **რას უნდა აკეთებდეს თქვენი აპლიკაციის ბიზნეს ლოგიკა**, ანუ — **რას შეუძლია აპლიკაციას**, როცა გარე სისტემა [[Driver Adapters]] მასზე ანხორციელებს მოთხოვნას.

ეს არის **შიდა კონტრაქტი**, რომელიც გარე სამყაროს (მაგ. controller-ს, CLI-ს, scheduler-ს) აძლევს საშუალებას **„დაუძახოს“ აპლიკაციას**, მაგრამ ისე, რომ **core-მა არაფერი იცოდეს caller-ის შესახებ**.