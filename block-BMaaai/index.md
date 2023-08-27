writeCode

#### Import data from json file to mongodb database using `mongoimport`

```
mongoimport --host <host_name> --username <user_name> --password <password> --db
DB_NAME --collection COLLECTION_NAME --file cities.json(file location) --jsonArray
(an array of json data)
```

host, username and password are optional fields.

- --host : hostname // defaults to localhost:27017
- --username and --password: optional username and password for db user
- --db: database name
- --collection: Collection name
- --file: file location
- --jsonArray: Passed an array of json objects

<!--
Mongo Import done from CMD terminal. and then go to mongo shell and look at the data inside the collection -->

<!-- PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin>
  .\mongoimport.exe  --jsonArray --db country --collection cities --file F:\AltCampus\MongoDB\TA-AC-BACKEND-mongodb-basics-TMaaaa\block-BMaaai\cities.json
2023-08-27T13:48:29.338-0400    connected to: mongodb://localhost/
2023-08-27T13:48:29.413-0400    5 document(s) imported successfully. 0 document(s) failed to import. -->

<!-- Output: -->

```js
country >
  db.cities.find().pretty()[
    ({
      _id: ObjectId('64eb8c6dce066a44184e5ad8'),
      name: 'Cairo',
      location: 'Egypt',
      weather: 'Hot desert',
      toDo: [
        'Visit the Pyramids',
        'Explore Egyptian Museum',
        'Cruise the Nile River',
      ],
      isPopular: true,
    },
    {
      _id: ObjectId('64eb8c6dce066a44184e5ad9'),
      name: 'Paris',
      location: 'France',
      weather: 'Mild',
      toDo: [
        'Visit the Eiffel Tower',
        'Explore Louvre Museum',
        'Stroll along the Seine River',
      ],
      isPopular: true,
    },
    {
      _id: ObjectId('64eb8c6dce066a44184e5ada'),
      name: 'Tokyo',
      location: 'Japan',
      weather: 'Temperate',
      toDo: [
        'Explore Shibuya Crossing',
        'Visit Tokyo Skytree',
        'Experience Akihabara',
      ],
      isPopular: true,
    },
    {
      _id: ObjectId('64eb8c6dce066a44184e5adb'),
      name: 'Sydney',
      location: 'Australia',
      weather: 'Mild',
      toDo: [
        'Visit Sydney Opera House',
        'Explore Bondi Beach',
        'Climb the Sydney Harbour Bridge',
      ],
      isPopular: true,
    },
    {
      _id: ObjectId('64eb8c6dce066a44184e5adc'),
      name: 'New York City',
      location: 'USA',
      weather: 'Temperate',
      toDo: [
        'Visit Times Square',
        'Explore Central Park',
        'See the Statue of Liberty',
      ],
      isPopular: true,
    })
  ];
```

## BLOCK-writeCode

Go to `https://www.json-generator.com/`

- generate 40 random json document using the format

```js
// paste this on left panel
[
  '{{repeat(30)}}',
  {
    _id: '{{objectId()}}',
    age: '{{integer(20, 40)}}',
    name: '{{firstName()}} {{surname()}}',
    gender: '{{gender()}}',
    company: '{{company().toUpperCase()}}',
    email: '{{email()}}',
    phone: '+1 {{phone()}}',
    tags: ['{{repeat(2)}}', '{{lorem(1, "words")}}'],
  },
];
```

- download it on `Desktop`
- import it into mongodb `test` database into a collection named `users`

#### Export data from mongodb server to local system in json format using

`mongoexport`command.

```
mongoexport --db state --collection cities --out ~/Desktop/states/city.json --jsonArray
```

First imported cities.json into test db -> users collection (from windows CMD)

Then exported into a file called exportJson.json in my Downloads folder as shown below:

<!-- PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin>

  .\mongoexport.exe --jsonArray --db test --collection users --out C:\Users\anand\Downloads\exportJson.json

2023-08-27T14:13:11.147-0400    connected to: mongodb://localhost/
2023-08-27T14:13:11.156-0400    exported 5 records
PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin> -->

## BLOCK-writeCode

Export `users` collection from `test` database onto `Desktop` in a file named `exported.json`.

<!-- Exported steps done above -->

Same below

<!-- PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin>

  .\mongoexport.exe --jsonArray --db test --collection users --out C:\Users\anand\OneDrive\Desktop\exported.json

2023-08-27T14:17:15.957-0400    connected to: mongodb://localhost/
2023-08-27T14:17:15.964-0400    exported 5 records
PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin> -->

#### Import from csv file

```
mongoimport -d DB_NAME -c COLLECTION_NAME --type csv --file elections.csv(file location) --headerline(including header)
```

<!--
PS F:\AltCampus\MongoDB\mongodb-database-tools-windows-x86_64-100.8.0\bin>

  .\mongoimport.exe -d test -c students --type csv --file C:\Users\anand\Downloads\students.csv --headerline

2023-08-27T14:28:30.531-0400    connected to: mongodb://localhost/
2023-08-27T14:28:30.588-0400    100 document(s) imported successfully. 0 document(s) failed to import. -->

```js
test> db.createCollection('students')
{ ok: 1 }
test> show collections
students
users
test> db.students.find().pretty()
[
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005ffa"),
    seq: 1,
    'name/first': 'Jon',
    'name/last': 'Walker',
    age: 32,
    street: 'Velnaz Park',
    city: 'Vegutza',
    state: 'DE',
    zip: 74843,
    dollar: '$1304.38',
    pick: 'YELLOW',
    date: '10/10/1928'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005ffb"),
    seq: 4,
    'name/first': 'Matilda',
    'name/last': 'Craig',
    age: 41,
    street: 'Curaj Pass',
    city: 'Heciefi',
    state: 'NJ',
    zip: 51133,
    dollar: '$1401.32',
    pick: 'YELLOW',
    date: '08/13/1907'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005ffc"),
    seq: 3,
    'name/first': 'Antonio',
    'name/last': 'Curry',
    age: 32,
    street: 'Ipohi Trail',
    city: 'Rojhunfe',
    state: 'CA',
    zip: 68886,
    dollar: '$5513.77',
    pick: 'GREEN',
    date: '12/29/2052'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005ffd"),
    seq: 8,
    'name/first': 'Mable',
    'name/last': 'Bowman',
    age: 24,
    street: 'Sarzu Path',
    city: 'Amulovpu',
    state: 'IA',
    zip: 5363,
    dollar: '$4742.77',
    pick: 'WHITE',
    date: '02/13/2007'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005ffe"),
    seq: 9,
    'name/first': 'Emma',
    'name/last': 'Ray',
    age: 31,
    street: 'Ribu Junction',
    city: 'Zatfikpu',
    state: 'IN',
    zip: 77225,
    dollar: '$7392.36',
    pick: 'YELLOW',
    date: '09/15/2037'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1005fff"),
    seq: 10,
    'name/first': 'Cora',
    'name/last': 'Santiago',
    age: 32,
    street: 'Saod Pike',
    city: 'Rojtavac',
    state: 'LA',
    zip: 54332,
    dollar: '$4937.31',
    pick: 'GREEN',
    date: '04/19/1954'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006000"),
    seq: 7,
    'name/first': 'Norman',
    'name/last': 'Paul',
    age: 62,
    street: 'Vujvuh Lane',
    city: 'Imivarul',
    state: 'CT',
    zip: 70185,
    dollar: '$658.63',
    pick: 'RED',
    date: '04/02/2034'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006001"),
    seq: 11,
    'name/first': 'Bobby',
    'name/last': 'Owen',
    age: 40,
    street: 'Cudri River',
    city: 'Abobuul',
    state: 'CA',
    zip: 62669,
    dollar: '$1083.81',
    pick: 'BLUE',
    date: '05/03/1936'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006002"),
    seq: 5,
    'name/first': 'Nora',
    'name/last': 'Barrett',
    age: 46,
    street: 'Doke Avenue',
    city: 'Uravuvsik',
    state: 'WA',
    zip: 68382,
    dollar: '$7033.12',
    pick: 'WHITE',
    date: '09/16/1961'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006003"),
    seq: 12,
    'name/first': 'Mattie',
    'name/last': 'Hudson',
    age: 27,
    street: 'Lafe Lane',
    city: 'Ituwirhe',
    state: 'TX',
    zip: 69339,
    dollar: '$3978.96',
    pick: 'RED',
    date: '10/16/2017'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006004"),
    seq: 6,
    'name/first': 'Ora',
    'name/last': 'Bates',
    age: 39,
    street: 'Jazput Point',
    city: 'Tevrekpi',
    state: 'MS',
    zip: 37612,
    dollar: '$588.56',
    pick: 'BLUE',
    date: '03/24/1955'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006005"),
    seq: 13,
    'name/first': 'Tom',
    'name/last': 'Hernandez',
    age: 34,
    street: 'Razsa Avenue',
    city: 'Mucoghas',
    state: 'FL',
    zip: 1651,
    dollar: '$7975.66',
    pick: 'RED',
    date: '02/08/1923'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006006"),
    seq: 14,
    'name/first': 'Christine',
    'name/last': 'Farmer',
    age: 54,
    street: 'Oche Parkway',
    city: 'Zudruhsof',
    state: 'NC',
    zip: 9980,
    dollar: '$3802.55',
    pick: 'GREEN',
    date: '11/01/1997'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006007"),
    seq: 15,
    'name/first': 'Jorge',
    'name/last': 'Lindsey',
    age: 34,
    street: 'Uladob Drive',
    city: 'Didigma',
    state: 'GA',
    zip: 16717,
    dollar: '$4713.75',
    pick: 'GREEN',
    date: '08/13/1998'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006008"),
    seq: 16,
    'name/first': 'Jeff',
    'name/last': 'Rodgers',
    age: 28,
    street: 'Ifve Place',
    city: 'Idvabof',
    state: 'VT',
    zip: 14032,
    dollar: '$6992.07',
    pick: 'GREEN',
    date: '03/17/1931'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e1006009"),
    seq: 17,
    'name/first': 'Marian',
    'name/last': 'Kim',
    age: 64,
    street: 'Sago Circle',
    city: 'Zolnovi',
    state: 'MI',
    zip: 66881,
    dollar: '$2458.58',
    pick: 'BLUE',
    date: '01/17/1947'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e100600a"),
    seq: 18,
    'name/first': 'Willie',
    'name/last': 'Pratt',
    age: 20,
    street: 'Howcol Mill',
    city: 'Totevotog',
    state: 'DC',
    zip: 68627,
    dollar: '$8960.50',
    pick: 'GREEN',
    date: '05/09/1935'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e100600b"),
    seq: 19,
    'name/first': 'Donald',
    'name/last': 'Hall',
    age: 45,
    street: 'Notod Key',
    city: 'Wofkome',
    state: 'TN',
    zip: 4316,
    dollar: '$8029.47',
    pick: 'YELLOW',
    date: '06/03/1938'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e100600c"),
    seq: 21,
    'name/first': 'Verna',
    'name/last': 'Estrada',
    age: 55,
    street: 'Lomet River',
    city: 'Apinowine',
    state: 'ND',
    zip: 43236,
    dollar: '$294.19',
    pick: 'BLUE',
    date: '12/25/2027'
  },
  {
    _id: ObjectId("64eb95ceb64aa4e2e100600d"),
    seq: 20,
    'name/first': 'Derrick',
    'name/last': 'Mathis',
    age: 28,
    street: 'Nuhu Junction',
    city: 'Kaderso',
    state: 'SD',
    zip: 18357,
    dollar: '$2383.29',
    pick: 'GREEN',
    date: '09/17/1919'
  }
]
```

## BLOCK-writeCode

Generate mock csv data from `https://www.convertcsv.com/generate-test-data.htm`

- insert this mock csv data into `test` database into a collection named `students`

<!-- mock csv downloaded into C:\Users\anand\Downloads and imported this csv file data into students collection in test DB-->
