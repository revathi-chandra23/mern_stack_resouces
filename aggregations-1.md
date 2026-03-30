1. server up
2. crud operator
3. database connection
4. frontend + backend connection
5. mongodb atlas
6. relationships

## next topics

# mongoDB

1. advance mongo queries
2. aggregation
3. database optimisation

# caching

Redis

# Auth

Oauth
refresh token, blacklisting
authorization

# websockets

socket.io

# intro to cloud

aws

client <---> server +database

-----Learned-------------

queries

student collection --->500 students

get api/students ---> send 500 data as response.

GET api/students?city=hyd --->StudentModel.find({city:req.query.city}) =40 students

Filtering the data

1. 500 data a response --->filtering on the frontend.
2. 40 data as response ---> - a) const students = StudentModel.find({}) - b) const finalStudents= students.filter((stu)=>stud.city=== req.query.city)

3. 40 data a response ---> StudentModel.find({city:req.query.city})

## advance mongo queries

        crud, filter, data- types

{
key: value
}

1. find a hero who's health is 40
   db.heros.find({"health":40}) -->batman
   {
   key: string/number
   }

2. find a hero who's fav color = red and age = 44
   db.heros.find({"metadata":{favouriteColor:"red", age:44}}).pretty()

{
key: object
}

find a hero who's fav age = 44 and fav color = red

exact ORDER matters

3. find a hero who's fav color =red

api/hero?favouriteCOlor = red;

let object = {name: "xyz"};

console.log(object.name); //xyz

db.heros.find({"metadata.favouriteColor": "red"}).pretty();

4. find all the hero's who's age is less than 50
   db.heros.find({"metadata.age":{$lt:50}}).pretty()

{
\_id: ObjectId('678081d8e772586f20fd69f7'),
name: 'IronMan',
powers: [ 'robot', 'money' ],
health: 33,
villains: [
{ name: 'Mandarin', health: 50 },
{ name: 'Titanium Man', health: 54 }
],
metadata: { favouriteColor:
{
"summer":
{
"day_time":"yellow",
"night_time":"blue"

                        }
                        "rainy:"red"
                    }


    , age: 13 }

},

all heros who's fav color in summer night is blue

"metadata.favouriteColor.summer.night_time": "blue"

5.  find all hero's who's powers are intelligence and money

db.heros.find({"powers":["intelligence", "money"]}).pretty()

6. find all the heros who's power is intelligence and money , irrespective of the order

$all --> all the values should be present (and)
db.heros.find({"powers":{$all: ["money", "intelligence"]}}).pretty()

7. all heros who's having any of power--> intelligence, money ( or)
   db.heros.find({"powers":{$in: ["money", "intelligence"]}}).pretty()

{
key:value,
key:object
key: string/number/boolean
key: array $all, $in, "direct element"
key: embedded object---> object inside object --> dot after dot.
key: array of object
}

8. find all heros who have a villain of name hela

db.heros.find({"villains":{"name":"Hela"}}).pretty();

{
id:1,
"colors:["red", "blue", "green"]
},
{
id:2,
"colors":["green"]
},
{
id:3,
"colors":["red"]
}

colors:["red"]--3
colors:"red" ---1,3

---

projection

find doc whose health is less than 50 and only get name and health
db.heros.find({"health":{$lt:50}},{name:1,health:1});

1 means---> true -->on
\_id is projected by default
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
