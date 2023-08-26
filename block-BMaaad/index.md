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
  weather> db.createCollection('temprature',3)
  { ok: 1 }
  weather> show collections
  temprature

weather> db.temprature.insert({temp: 23})
{
acknowledged: true,
insertedIds: { '0': ObjectId("64ea64f358ef41669adad32d") }
}
weather> db.temprature.find()
[
{ _id: ObjectId("64ea64c058ef41669adad32c"), temp: 21 },
{ _id: ObjectId("64ea64f358ef41669adad32d"), temp: 23 }
]
weather> db.temprature.insert({temp: 28})
{
acknowledged: true,
insertedIds: { '0': ObjectId("64ea64f958ef41669adad32e") }
}
weather> db.temprature.find()
[
{ _id: ObjectId("64ea64c058ef41669adad32c"), temp: 21 },
{ _id: ObjectId("64ea64f358ef41669adad32d"), temp: 23 },
{ _id: ObjectId("64ea64f958ef41669adad32e"), temp: 28 }
]
weather> db.temprature.insert({temp: 32})
{
acknowledged: true,
insertedIds: { '0': ObjectId("64ea64fe58ef41669adad32f") }
}
weather> db.temprature.find()
[
{ _id: ObjectId("64ea64c058ef41669adad32c"), temp: 21 },
{ _id: ObjectId("64ea64f358ef41669adad32d"), temp: 23 },
{ _id: ObjectId("64ea64f958ef41669adad32e"), temp: 28 },
{ _id: ObjectId("64ea64fe58ef41669adad32f"), temp: 32 }
]

- create a simple collection named `humidity`
  weather> db.createCollection('humidity')
  { ok: 1 }
  weather> show collections
  humidity
  temprature

- check whether `temperature` collection is capped or not ?

- Delete `humidity` collection and then the entire database(weather).
  weather> db.humidity.drop()
  true
  weather> show collections
  temprature
