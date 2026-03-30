sql---> mysql, postgresql, ms sql etc
nosql---> mongodb, cassandra

CRUD

database
collection
document

### comparison

<= lte
< -->lt

> = -->gte
> --->gt
> == --->et
> != --->ne

### logical operators

and
or

db.users.find({"org":"flm", "country":"india"});

<!-- ===> it will give you result combo of flm and india -->

db.users.find($and : [{"org":"flm"}, {"country":"india"}]);

db.users.find($or : [{"org":"flm"}, {"country":"india"}]);

<!-- it will give you result of any of the matching flm or india  -->
