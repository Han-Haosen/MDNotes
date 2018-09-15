# MongoDB notes 

relational and document databases 

SQL might need to call multiple tables for one entity

Table design can be complex

update require all kinds of operations

complex queries to join related data

keep all relavent info in the same object

easier to access 

db.users.insert()

db.users.find()

stored as BSON

using JSON

Flexible indexing capability

ID field 

Required

Unique across collection

auto assigned if not specified

documents specify parameters 

queries match against the documents

db.users.remove({first_name:"john"})

db.users.update({first_name:"joh"
},{whole object})


it will replace the whole object 

original update could be done with set


support nested objects and arrays 

determine schema for database 

embedded operations 

include by reference 

e.g

```
wiki entry

pages,authors,tags,comments


{
    "Type":"blog",
    "Title":"My blog post"
    "Author":"Kirsten Hunter",
    "Tags":["great","awesome"]
    "comments":["a"]
}


Repeated data across documents 

don't update automatically 

db.numbers.explain()
db.numbers.creatIndex({number:1})


for(i=0;i<100;i++){
    db.numbers.insert(
        {"number":i}
    )
}

```


import data into database 

mongo import command 

mongoimport --db learning_mongo --collection tours --jsonArray --file tours.json

Mongo Shell operations

CRUD 

use learning_mongo 

db.tours.find({"tourTags":"wine})

db.tours.insert({
    "tourName":"The wines of Santana",
    "tourLength":3,
    "tourDescription":"Discover Santa Cruz's wineries",
    "tourPrice":500,
    "tourTags":["a","wine"]
})

db.tours.update({"tourName:"The Wines of ..."},
{$set:{"tourRegion":"Central Coast"}}
)

db.tours.update({"tourName:"The Wines of ..."},
{$addToSet:{"tourTags":"broadwalk"}})

a lot more of set 

db.tours.remove({"tourName":"abc"})

db.tours.drop()//get rid entirely

db.tours.find({"tourPrice:{$lte:500},
"toursomethign":{$lte:300}
})
