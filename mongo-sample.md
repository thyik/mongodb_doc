# mongodb sample

-   create database

```
use db-yikth
```

-   Create collection

```
db.createCollection("users")
```

-   add data to collection

```
db.users.insertMany([
  {
    Id: 100,
    userName: "John",
    mail: "John@gmail.com" ,
    mobile: 123456789,
    Transaction: [
                    {
                    ItemId:"a100",
                    price: 200
                    },
                    {
                    ItemId:"a110",
                    price: 200
                    }
                  ],
    Payment: {
                Type: "Credit-Card",
                Total: 400,
                Success: true
                },
    Remarks: "1st Complete Record, payment successful"
  },
  {
    Id: 102,
    userName: "Alice",
    mail: "Alice@gmail.com" ,
    mobile: 987654321,
    Transaction: [
                    {
                      ItemId:"a100",
                      price: 200
                    },
                    {
                      ItemId:"a110",
                      price: 200
                    }
                  ],
    Payment: {
      Type: "Credit-Card",
      Total: 400,
      Success: true
    },
    Remarks:""
  }
])

db.users.insert([
{
    Id: 103,
    userName: "Tom",
    mail: "Tom@gmail.com" ,
    mobile: 92919999,
    Transaction: [
                    {
                      ItemId:"a100",
                      price: 100
                    },
                    {
                      ItemId:"a110",
                      price: 200
                    }
                  ],
    Payment: {
      Type: "Credit-Card",
      Total: 300,
      Success: true
    },
    Remarks:""
  }
])

db.users.insert([
{
    Id: 104,
    userName: "Jenny",
    mail: "Jenny@gmail.com" ,
    mobile: 92919999,
    Transaction: [
                    {
                      ItemId:"a100",
                      price: 100
                    },
                    {
                      ItemId:"a111",
                      price: 2000
                    }
                  ],
    Payment: {
      Type: "Credit-Card",
      Total: 1300,
      Success: true
    },
    Remarks:""
  }
])
```

-   Search for total payment > 700

```
db.users.find({Payment: {$gt:700}})
```

-   Find total payment of all records

```
db.users.aggregate([{$group:{_id:"", Total: {$sum:"$Payment.Total"}}}])
```

-   Find total Transaction price per record

```
db.users.aggregate([{$group:{_id:"$userName", Transactions: {$sum:"$Transaction.price"}}}])
```

-   Find max Transaction price

```
// individual record max-min transaction price
db.users.aggregate([{
            $project:{
                      Maximun: { $max:"$Transaction.price"},
                      Minimun: { $min:"$Transaction.price"}
                      }
                  }])

// ? how to which record have the max-min transaction price?
db.users.aggregate([{
            $project:{
                      Maximun: { $max:"$Transaction.price"},
                      Minimun: { $min:"$Transaction.price"}
                      }
                  },
                  {$group: {_id:"", maximun:{$max:"$Maximun"}}}
                  ])

db.users.aggregate([
                  {$group: {_id:"", transactionPrice:{$push:"$Transaction.price"}}}])

db.users.aggregate([
                  {$group: {_id:"", transactionPrice:{$push:"$Transaction.price"}}}
                  ,{$project:{
                      Maximun: { $max:"$transactionPrice"},
                      Minimun: { $min:"$transactionPrice"}
                      }}
                  ,
])

db.users.aggregate([
                  {$group: {_id:"", transactionPrice:{$addToSet:"$Transaction.price"}}}])

db.users.aggregate([
                  {$project: {transactionPrice:{$max:"$Transaction.price"}}}])
```

-   Find record having highest payment and record with lowest payment

```
db.users.aggregate([{$group:{_id:"", Total: {$max:"$Payment.Total"}}}])
db.users.aggregate([{$group:{_id:"", Total: {$min:"$Payment.Total"}}}])

```

-   Find record having username either "John" or "Alice"

```
db.users.find({userName:{$in:["John", "Alice"]}})
```

-   Delete record using Id

```
db.users.remove({Id:102})
```

-   Arrange name of users in ascending order

```
db.users.find().sort({userName:1})
```
