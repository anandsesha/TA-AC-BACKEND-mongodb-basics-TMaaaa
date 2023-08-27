writeCode

Write code to:-

- create a database named `mountains`
  test> use mountains
  switched to db mountains
  mountains>

- a collection inside that database named `himalayas`
  mountains> db.createCollection('himalayas')
  { ok: 1 }
  mountains> show collections
  himalayas

- insert 1 document into that collection `{name: 'Dhauldhar range', height: '4000 mtrs'}`
  mountains> db.himalayas.insert({name: 'Dhauldhar range', height: '4000 mtrs'})
  {
  acknowledged: true,
  insertedIds: { '0': ObjectId("64ea91fe58ef41669adad33e") }
  }

  mountains> db.himalayas.find().pretty()
  [
  {
  _id: ObjectId("64ea91fe58ef41669adad33e"),
  name: 'Dhauldhar range',
  height: '4000 mtrs'
  }
  ]

- insert multiple document using insertMany command
  let ranges = [
  {
  name: 'Xyz range',
  height: '5000 mtrs'
  },
  {
  name: 'abc range',
  height: '6000 mtrs'
  }
  ]

mountains> db.himalayas.insertMany(ranges)
{
acknowledged: true,
insertedIds: {
'0': ObjectId("64ea927558ef41669adad33f"),
'1': ObjectId("64ea927558ef41669adad340")
}
}

mountains> db.himalayas.find().pretty()
[
{
_id: ObjectId("64ea91fe58ef41669adad33e"),
name: 'Dhauldhar range',
height: '4000 mtrs'
},
{
_id: ObjectId("64ea927558ef41669adad33f"),
name: 'Xyz range',
height: '5000 mtrs'
},
{
_id: ObjectId("64ea927558ef41669adad340"),
name: 'abc range',
height: '6000 mtrs'
}
]

- find all documents from mountains
  mountains> db.himalayas.find({})
  [
  {
  _id: ObjectId("64ea91fe58ef41669adad33e"),
  name: 'Dhauldhar range',
  height: '4000 mtrs'
  },
  {
  _id: ObjectId("64ea927558ef41669adad33f"),
  name: 'Xyz range',
  height: '5000 mtrs'
  },
  {
  _id: ObjectId("64ea927558ef41669adad340"),
  name: 'abc range',
  height: '6000 mtrs'
  }
  ]

- find a single document using name

mountains> db.himalayas.find({name: "Xyz range"})
[
{
_id: ObjectId("64ea927558ef41669adad33f"),
name: 'Xyz range',
height: '5000 mtrs'
}
]
