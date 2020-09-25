# mongo

## installation for windows

-   Download Community Server Version. [Download](https://www.mongodb.com/try/download/community)

-   set environment path for mongo bin folder

```
path = C:\Program Files\MongoDB\Server\4.4\bin
```

-   Open command prompt. Run mongo

```
c:\> mongo
```

## installation for Linux

-   For Linux, install the mongo server

```
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mongodb

// optional : enable auto start server (execute if mongo server don't auto start)
$ sudo systemctl enable mongod
$ sudo systemctl start mongod

$ mongo
```

## In Mongo Shell

```mongo

// select database
> use db-yikth

// create collection users
> db.createCollection("users")

//
>

//
> db.users.insert({name:"Reshma", age:10, salary:5000})

> db.users.insertMany([{name:"Reshma", age:10, salary:5000}, {name:"Paul", age:10, salary:5000}])

> db.users.find()

// update only 1st record found
> db.users.update({name:"Reshman"}, {$set:{name:"John"}})

// remove all name "John"
> db.users.remove({name:"John"})

// show record with age greater than 10
> db.users.find({age: {$gt:10}})

// show record with age with 10 and 20
> db.users.find({age: {$in:[10, 20]}})

//find salary > 1000 and <5000
> db.users.find({$and:[{salary:{$gt:1000}}, {salary:{$lt:5000}}]})

// limit to 2 records
> db.users.find().limit(2)

// show record sorted by age descending (decreasing)
> db.users.find().sort({"age":-1})
```
