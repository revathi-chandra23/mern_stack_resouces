relationships--->
relationships in databases define how data in one collection is related to another collection.

this concept is crucial for designing databases.

why do we need relationships ?

flm exmaple

1. students
2. instructor

student collection -->document
student_code
batch
address
location

instructors collection--->document
emp_id
sub
expr
location

user collection --->document
user_id
name
email
phone
location,
gender
blood group
location

db.students.find({location:"BLR"})--->document which have location matching with blr
db.instructor.find({location:"BLR"})
db.ops.find({location:"BLR"})
db.sales.find({location:"BLR"})

db.user.find({location:"BLR"});

why

1. to avoid data redundancy

2. to enables powerful queries

3. this help readability in database collections.

types of relationships

1. one to one relationship
2. one to many relationship
3. many to many relationship

imagine you are managing a database for a system where every users has an address. you want to store this information

there are two way to store this relationship

1. embedded relationship
   here, we store the user and their address together in one document.
   {
   id:1,
   name:"flm",
   email:"abc@gmail.com",
   address:{
   street:"6-9, e-seva street",
   city:"hyd",
   zip:500458
   }
   }

advantages

1. all the data is in one place
2. easy to retrieve the user and their address in a single query.

disadvantage

1. if the address change frequently, you will need to update it multiple times if its reference else where.

2. referenced relationship.
   here , we split the user and their address into separate documents.
   the user document has a reference (Link) to the address document

user collection
{
id:1,
name:"flm",
email:"abc@gmail.com",  
 address: 101 // reference to the address document
}

address collection
{
id:101 // address document unique id
street:"6-9, e-seva street",
city:"hyd",
zip:500458
}

---

## query

1.  query for user
    const user = await User.findById(1); //user document
    console.log(user.address); // output-101

cons address= await Address.findById(user.address) // output full address details

const userWithAddress= await User.findById(1).populate("address")

example

1. imagine you have tow forms
   a. a user profile form with the user's name and email
   b. a separate address where you record the user's address.

2. one the user profile form, you write a reference number that links it to the address form.

advantages

1. better for reusable data
2. if the address changes, you only need to update it once in the address collections

disadvantage
requires an additional query to fetch the reference address

---over-view-------------------
embedded---> stores everything together (like one form with all the details)
reference relationship --> store in separate collection and link them ( like two forms with reference number connecting them)

1. one - to -one relationship
   def: each document in one collection is associated with exactly one document in another collection.

analogy: think of a passport and a person. one person can
have only one passport and one passport is assigned to only one person.

2.  one - to many relationship

def: one document in a collection is related to multiple documents in another collection.

analogy: a teacher and their students. one teach can have multiple students, but each student has only one teacher

real life example : a blog post and its comment.

3. many to many relationship
   def: each document one collection can relate to multiple documents in another collection , vice versa

analogy: students and courses, one student can enroll in multiple courses, and one course can have multiple students

//student document
{
id:1,
name:"alice",
courses:["101,"102"]
}

/courses document
{
id:101,
title:"node",
studentId:[1,2,3,4]
}

amazon products, user
1.a user can purchase or add multiple products to their cart or wishlist 2. a products can be purchased or added to the cart/ wishlist by multiple users

---

lets create a database for library where books are written by author

//author
{name,age}

{title,page,author: {
type: id,
ref:"Author"
} }

//crud
