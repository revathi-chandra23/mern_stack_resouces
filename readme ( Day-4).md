Database optimisation

database (Database management system)- CRUD

optimisation:

performance-

1. amount to data
2. cpu/processor
3. storage:
   1. Ram/memory
   2. Disk - HDD/SSD/m2
4. network:

   1. latency
   2. bandwidth

5. Query

db.users.aggregate([])

50,000 data
of all age- 1,64,70
of all city- mumbai, bangalore, delhi

Find all users in the ascending of their age, who's age is less than 20 and who are from mumbai (city)

1. db.users.aggregate([
   {$sort: {age:1}}, //50,000
   {$match: {age: {lt:20}}},
   {$match:{city: "mumbai}}
   ])

2. db.users.aggregate([
   {$match:{city:"mumbai"}}, //10,000 data
   {$match: {age:{lt:20}}}, // 3000 data
   {$sort: {age:1}}
   ])
