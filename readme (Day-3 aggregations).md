find the state with largest population in the give zip collection
db.zips.aggregate([{$group: {_id:"$state", total_pop: {$sum:"$pop"}}}, {$sort:{total_pop:-1}},{$limit:1}])

---

relationships

blog
user

user -{
name,
email --- unique
}

blog - {
\_id --- unique
title,
content,
date,
author_email
}

1. user email inside blog collection
1. blog \_id inside user collection

BlogModel
AuthorModel
Auth- api/blogs/delete/:blog_id

const {blog_id} = req.params;
const email = /from token/- req.body

<!-- const author_email = BlogModel.find(blog_id).author_email;
if(email === author_email) {

    BlogModel.findByIDandDelete(blog_id);
} -->

BlogModel.findOneAndDelete({blog_id:blog_id,author_email: email})

---

$lookup operator
it is used to perform a join operation between two collection, it allows you to combine data from different collection by matching values from fields in one collection with field another.
This is particularly useful in cases where you have related data stored in separate collections and nee dto retrieve the combined result in single query.

db.authors.aggregate([{$lookup:{from:"blogs",localField:"email",foreignField:"author_email",as:"myblogs"}}])

Home work----------------------------------------------------------------------
create two collections
posts - 5 posts

users - 2 users

try creating relationships and run a lookup operator

---

$out operator;
Takes the documents returned by the aggregation pipeline and writes them to a specified collection. You can specify the output database.

[{},{},{$out}]

$out stage----> will be at the last

{$out : {coll: "collection name"}}

count
set
graphlookup
unwind

database optimization
