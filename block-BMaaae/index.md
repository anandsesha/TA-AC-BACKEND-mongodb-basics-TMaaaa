writeCode

Write code to:-

- create a database named `sports`.
  weather> use sports
  switched to db sports

- list all databases present in local mongod server.
  sports> show dbs
  admin 40.00 KiB
  config 108.00 KiB
  india 16.00 KiB
  local 40.00 KiB
  weather 112.00 KiB

- create 3 collections named `cricket`, `football`, `TT` in sports databse.
  sports> db.createCollection('Cricket')
  { ok: 1 }
  sports> db.createCollection('Football')
  { ok: 1 }
  sports> db.createCollection('TT')
  { ok: 1 }

- add multiple players in those collections which should have fields like `name`, `age` and `email` and `bid_price`.
  sports> db.Cricket.insertMany([{name: "Anand",age: 27,email:"anand@gmail.com",bid_price: 100},{name: "Arvind",age: 24,email:"arv@gmail.com",bid_price: 500}])
  {
  acknowledged: true,
  insertedIds: {
  '0': ObjectId("64ea78ca58ef41669adad338"),
  '1': ObjectId("64ea78ca58ef41669adad339")
  }
  }
  sports> db.Cricket.find()
  [
  {
  _id: ObjectId("64ea78ca58ef41669adad338"),
  name: 'Anand',
  age: 27,
  email: 'anand@gmail.com',
  bid_price: 100
  },
  {
  _id: ObjectId("64ea78ca58ef41669adad339"),
  name: 'Arvind',
  age: 24,
  email: 'arv@gmail.com',
  bid_price: 500
  }
  ]

- list all collections in sports database.
  sports> show collections
  Cricket
  Football
  TT

- rename `TT` collection to `tennis`.
  sports> db.TT.renameCollection('Tennis')
  { ok: 1 }
  sports> show collections
  Cricket
  Football
  Tennis

- create a capped collection called `khokho` which should have max 3 documents.
  sports> db.createCollection('khokho',{capped: true, size: 1024,max: 3})
  { ok: 1 }
  sports> show collections
  Cricket
  Football
  khokho
  Tennis

  Try inserting more than 3 and see what happens?
  sports> db.khokho.insertMany([{a:1},{b:2},{c:3},{d:4}])
  {
  acknowledged: true,
  insertedIds: {
  '0': ObjectId("64ea797258ef41669adad33a"),
  '1': ObjectId("64ea797258ef41669adad33b"),
  '2': ObjectId("64ea797258ef41669adad33c"),
  '3': ObjectId("64ea797258ef41669adad33d")
  }
  }
  sports> db.khokho.find()
  [
  { _id: ObjectId("64ea797258ef41669adad33b"), b: 2 },
  { _id: ObjectId("64ea797258ef41669adad33c"), c: 3 },
  { _id: ObjectId("64ea797258ef41669adad33d"), d: 4 }
  ]

<!-- Thereore only 3 inserted above. Since kokho is capped at 3 -->

- check whether a collection is capped or not?
  sports> db.khokho.isCapped()
  true

- drop all documents from `football` collection.
  sports> db.Football.drop()
  true
  sports> show collections
  Cricket
  khokho
  Tennis

- delete cricket collection completely.
  sports> db.Cricket.drop()
  true
  sports> show collections
  khokho
  Tennis

- delete sports database.
  sports> db.dropDatabase()
  { ok: 1, dropped: 'sports' }
  sports> show dbs
  admin 40.00 KiB
  config 108.00 KiB
  india 16.00 KiB
  local 40.00 KiB
  weather 112.00 KiB

- check which database you are connected to ?
  sports> db
  sports

- connect to test database
  sports> use test
  switched to db test
  test>
