---
projection

find doc whose health is less than 50 and only get name and health
db.heros.find({"health":{$lt:50}},{name:1,health:1});

1 means---> true -->on
_id is projected by default
0 mean ---> false -->OFF

you cannot include both 1 and 0 in a single query.
---

### aggregation

- aggregate:
  to collect something together
  to accumulate

1. find something from the db , then you process (filter, sorting etc) on the server.
2. you write the query in such a way that all the processing happens at the db level itself (recommanded)

aggregation
very powerful
aggregation operator

pipeline:

- consists of stages
- the input of each stage, depends the output of previous stage

syntax

- db.orders.find({price:{$lt:500}}).limit()

-db.orders.aggregate([{},{},{},{}])

the nth stage works on the output of the n-1th stage

operators

- starts with $
- learning curve - it is different from what we have learnt so far.

db.orders.insertMany([
{_id:0, name:"Pepperoni", size:"small", price:19,quantity:10},
{_id:1, name:"Pepperoni", size:"medium", price:20,quantity:20},
{_id:2, name:"Pepperoni", size:"large", price:21,quantity:30},
{_id:3, name:"Cheese", size:"small", price:12,quantity:15},
{_id:4, name:"Cheese", size:"medium", price:13,quantity:50},
{_id:5, name:"Cheese", size:"large", price:14,quantity:10},
{_id:6, name:"Vegan", size:"small", price:17,quantity:10} ,
{_id:7, name:"Vegan", size:"medium", price:18,quantity:10},
])

1. $limit
2. $sort (1(desc), -1(asc))
3. mix and match sort and limit
4. $skip
5. $match

find all the large sized pizzas in increasing order for their price
db.orders.aggregate([{$match:{size:"large"}},{$sort:{price:1}}]).pretty();

find all the small size pizzas with price >=16
db.orders.aggregate([{$match:{size:"small"}}, {$match:{price:{$gte :16}}}]).pretty()

db.orders.find({size:"small",price:{$gte:16}}) --basic
db.orders.aggregate([{$match:{size:"small",price:{$gte:16}}]) -- alternate 2

find all smallest pizza with highest price

db.orders.aggregate([{$match:{size:"small"}},{$sort:{price:-1}},{$limit:1}])

6. group

- it is used to group "something", like course, batch etc
- we need to give \_id mandatorily.

group by size
db.orders.aggregate([{$group:{_id:"$size"}}])

group by name
db.orders.aggregate([{$group:{_id:"$name"}}])

find the total number of small size pizzas
db.orders.aggregate([{$group:{_id:"$size",totalqty:{$sum:"$quantity"}}}])

<!-- api/total_small_pizzas

const total_small_pizzas=0;
const small_pizzas = OrderModel.find({size:"small"});

small_pizzas.forEach((ele)=>{
total_small_pizzas += ele.quantity;
});

res.send(total_small_pizzas) -->

find total number of vegan name pizzas
db.orders.aggregate([{$group:{_id:"$name",totalQuantity:{$sum:"$quantity"}}}]);

find the total cost of small size pizzas
db.orders.aggregate([{$match:{size:"small"}},{$group:{\_id:null, totalCost:{$sum:{$multiply:["$price","$quantity"]}}}},{$project:{\_id:0,totalCost:1}}])

find the state with largest population in the give zip collection
