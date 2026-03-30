1+2+3+4+5+6+7+8+9 +10 ? --> xsec


### what are key-values databases ?

NoSQL

key- value use cases

- chaching : key value databases are often used as chacing layer for more persistent data store to improve the read performance.
- session management
- distributed system
- content management
- product catalogs

key value databases list for chache

- Redis
- Berkeley DB
- Amazon Dynamo DB.
- Google cloud Bigtable
- Riak
- Azure cosmos DB.
- Rocks DB

what is chache
In computing, a cache is a hardware or software component that stores data so that future requests for that data can be served faster; the data stored in a cache might be the result of an earlier computation or a copy of data stored elsewhere

what is chached data ?
it is information stored in specific location used to speed up gathering and transfering data.
ex-
In case of website, the cache would allow you to load certain resource without downloding them from the server.
For server, chached data can be dynamic data saved as simple HTML to speed up the page load time.

## how does the cache work?

copies of data are stored in desgined location, either locally or on the server.
this saves resources trying to run difficult queries on databases on those loading large images from server everytime a website loads.

Browser will check theses locations before requesting the resources from the server, and if it is found
it will be loaded from the cache instead of having it downloaded

what is redis?
it is NoSQL database that follows the principle of key-value storage. the key-value store provides the ablitiy to store some data called a "value", inside a key.

You can receive this data later only if you know the exect key used to store it.

- Redis is flexible, open-source in-memory data structure store, used as a database cache
- it is used to store huge amount of data without the limitations of relational database.

redis supports various types of data structure like strings,hashes, list, sets, sorted set, bitmaps, logs, index with queries.

- Advantages

Expectionally fast: it is very fast and can perform about 110000 SETS per second and 81000 GETs per second.

support rich data types: strings,hashes, list, sets, sorted set, bitmaps, logs, index with queries.

operations are atomic: all redisc operations are atomic, which ensures that if two clients concurrently access, the redis server will receive the updated value.

multi- utility-tool: it can be used in a number of use cases such as caching, messaging queues and any short-lived data in your application., such as web application sessions, web page hit count etc.
