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

---

sharding- it is a method of partitioning data across multiple servers to improve performance, scalability and availability.

scaling- vertical and horizontal scaling

10GB, 8GBRAM--->15GB, 16RAM --->20GB, 18RAM : vertical

10GB, 8GBRAM / 10GB, 8GBRAM / 10GB, 8GBRAM : horizontal scaling

---

Query optimisation

indexing in mongoDB : default is \_id

100 user;
flm_id:1,
flm_id:2,
flm_id:3,
.....
...
flm_id:100

db.users.find({flm_id:95}) : O(n)

time complexity
1-10 --->10min -->O(1)-->constant time

1-n--->nmin --->O(n) ---> n time complexity

\_id:1,
\_id:2,
\_id:3,
.....
...
\_id:100

db.users.find({\_id:87}) : O(1)

\_id address
1 1 address
2 2 address

indexing- makes query super fast-O(n) to O(1)

1. should we index all the keys?
   No,
2. which key should we index?
   {
   \_id: Object("ljsdlkfjl"),
   name: Mahesh,
   course: NXM,
   city:"hyd",
   pan:1234,
   flm_code: flm_123
   ....
   }

Read query will be fast

disadvantage of indexing.

1.  space
2.  write/create/insert query will be slower.
3.  indexing - B+ tree - balance

Book1 -armstrong --index
4 page,2page -- "armstrong",

index;
armstrong-20,40,22,32

new page--->55 -armstrong

index;
armstrong-20,40,22,32,55

collScan
IXScan

Explain: explain()

firstName:
{lastName: address}
