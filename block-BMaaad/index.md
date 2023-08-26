writeCode

Write command to

- List collections from a database.
  india> use india
  Switched to db india

india> show collections
Mumbai

- create a new collection in your country database which you created recently.
  india> db.createCollection('new-collection')
  { ok: 1 }

Write code to:-

- crate a database named `weather`
  india> use weather
  switched to db weather

- create a capped collection named `temperature` with maximum of 3 documents and try inserting more than 3 to see the result.
  weather> db.createCollection('sound',{capped: true, size: 1024, max: 3})
  { ok: 1 }
  weather> show collections
  sound
  temprature
  weather> db.sound.insertMany([{a: 1},{b: 2},{c: 3},{d: 4}])
  {
  acknowledged: true,
  insertedIds: {
  '0': ObjectId("64ea6fe558ef41669adad334"),
  '1': ObjectId("64ea6fe558ef41669adad335"),
  '2': ObjectId("64ea6fe558ef41669adad336"),
  '3': ObjectId("64ea6fe558ef41669adad337")
  }
  }
  weather> db.sound.find()
  [
  { _id: ObjectId("64ea6fe558ef41669adad335"), b: 2 },
  { _id: ObjectId("64ea6fe558ef41669adad336"), c: 3 },
  { _id: ObjectId("64ea6fe558ef41669adad337"), d: 4 }
  ]

- create a simple collection named `humidity`
  weather> db.createCollection('humidity')
  { ok: 1 }
  weather> show collections
  humidity
  temprature

- check whether `temperature` collection is capped or not ?
  > db.temperature.isCapped()
  > true
- Delete `humidity` collection and then the entire database(weather).
  weather> db.humidity.drop()
  true
  weather> show collections
  temprature
