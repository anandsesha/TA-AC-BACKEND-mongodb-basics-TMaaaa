writeCode

Run these shell commands in mongo shell:

- db.version()
  test> db.version()
  7.0.0

- db.stats()
  test> db.stats()
  {
  db: 'test',
  collections: Long("0"),
  views: Long("0"),
  objects: Long("0"),
  avgObjSize: 0,
  dataSize: 0,
  storageSize: 0,
  indexes: Long("0"),
  indexSize: 0,
  totalSize: 0,
  scaleFactor: Long("1"),
  fsUsedSize: 0,
  fsTotalSize: 0,
  ok: 1
  }

- db.help()
  test> db.help()

  Database Class:

      getMongo                                   Returns the current database connection
      getName                                    Returns the name of the DB
      ....
      ...
      ..

Write code to

- create a database of your country name.
  test> use india
  switched to db india

- check list of databases to see newly created database.
  india> db.createCollection('Mumbai')
  { ok: 1 }

india> show dbs
admin 40.00 KiB
config 108.00 KiB
india 8.00 KiB // shows created db now!
local 40.00 KiB

- check which database you are currently connected to ?
  test> db.getName()
  test
