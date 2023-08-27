writeCode

Write code to execute below expressions.

1. Create a database named `blog`.
   mountains> use blog
   switched to db blog

2. Create a collection called 'articles'.
   blog> db.createCollection('articles')
   { ok: 1 }
   blog> show collections
   articles

3. Insert multiple documents(at least 3) into articles. It should have fields

- title as string
- createdAt as date
- details as String
- author as nested object
  - author should have
    - name
    - email
    - age
    - example author: {name: 'abc', email: 'abc@gmail', age: 25}
- tags : Array of strings like ['html', 'css']

```js
// An article should look like in the database
{
  _id: 'some_random_id',
  title: '',
  details: '',
  author: {
    name: '',
    email: '',
    age: ''
  },
  tags: ['js', 'mongo']
}
```

let articlesArray = [
{
\_id: '003',
title: 'Article-3',
date: 2021,
details: 'Reptiles',
author: { name: 'kb', email: 'kb@gmail.com', age: 30 },
tags: ['React', 'Express'],
},
{
\_id: '002',
title: 'Article-2',
date: 2022,
details: 'Mamals',
author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
tags: ['HTML', 'css'],
},
{
\_id: '001',
title: 'Article-1',
date: 2023,
details: 'Birds',
author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
tags: ['NodeJS', 'mongoDB'],
},
];

blog> db.articles.insterMany(articlesArray)

4. Find all the articles using `db.COLLECTION_NAME.find()`
   blog> db.articles.find().pretty()
   [
   {
   \_id: '003',
   title: 'Article-3',
   date: 2021,
   details: 'Reptiles',
   author: { name: 'kb', email: 'kb@gmail.com', age: 30 },
   tags: [ 'React', 'Express' ]
   },
   {
   \_id: '002',
   title: 'Article-2',
   date: 2022,
   details: 'Mamals',
   author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
   tags: [ 'HTML', 'css' ]
   },
   {
   \_id: '001',
   title: 'Article-1',
   date: 2023,
   details: 'Birds',
   author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
   tags: [ 'NodeJS', 'mongoDB' ]
   }
   ]

5. Find a document using \_id field.
   blog> db.articles.findOne({\_id: '001'})
   {
   \_id: '001',
   title: 'Article-1',
   date: 2023,
   details: 'Birds',
   author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
   tags: [ 'NodeJS', 'mongoDB' ]
   }

6. 1. Find documents using title
      blog> db.articles.find({title: 'Article-3'})
      [
      {
      \_id: '003',
      title: 'Article-3',
      date: 2021,
      details: 'Reptiles',
      author: { name: 'kb', email: 'kb@gmail.com', age: 30 },
      tags: [ 'React', 'Express' ]
      }
      ]

7. 2. Find documents using author's name field.
      blog> db.articles.find({title: 'Article-3'}, {author: {name: 'kb'}})
      [ { _id: '003', author: { name: 'kb' } } ]

8. Find document using a specific tag.
   blog> db.articles.find({ tags: { $in: ['css'] } })
   [
   {
   \_id: '002',
   title: 'Article-2',
   date: 2022,
   details: 'Mamals',
   author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
   tags: [ 'HTML', 'css' ]
   }
   ]

9. Update title of a document using its \_id field.
   blog> db.articles.update({\_id: '001'}, {$set: {title: 'Article-0'}})
   {
   acknowledged: true,
   insertedId: null,
   matchedCount: 1,
   modifiedCount: 1,
   upsertedCount: 0
   }

   blog> db.articles.findOne({title: 'Article-0'})
   {
   \_id: '001',
   title: 'Article-0',
   date: 2023,
   details: 'Birds',
   author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
   tags: [ 'NodeJS', 'mongoDB' ]
   }

10. Update a author's name using article's title.

    blog> db.articles.update({title: 'Article-3'}, {$set: {author: {name: 'baby'}}})
    {
    acknowledged: true,
    insertedId: null,
    matchedCount: 1,
    modifiedCount: 1,
    upsertedCount: 0
    }

    blog> db.articles.find()
    [
    {
    \_id: '003',
    title: 'Article-3',
    date: 2021,
    details: 'Reptiles',
    author: { name: 'baby' },
    tags: [ 'React', 'Express' ]
    },
    {
    \_id: '002',
    title: 'Article-2',
    date: 2022,
    details: 'Mamals',
    author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
    tags: [ 'HTML', 'css' ]
    },
    {
    \_id: '001',
    title: 'Article-0',
    date: 2023,
    details: 'Birds',
    author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
    tags: [ 'NodeJS', 'mongoDB' ]
    }
    ]

11. rename details field to description from all articles in articles collection.

blog> db.articles.find({details: {$exists: true}})

12. Add additional tag in a specific document.
    blog> db.articles.update({\_id: '001'}, {$set: {animal: "Horse"}})
    {
    acknowledged: true,
    insertedId: null,
    matchedCount: 1,
    modifiedCount: 1,
    upsertedCount: 0
    }
    blog> db.articles.find().pretty()
    [
    {
    \_id: '003',
    title: 'Article-3',
    date: 2021,
    details: 'Reptiles',
    author: { name: 'baby' },
    tags: [ 'React', 'Express' ]
    },
    {
    \_id: '002',
    title: 'Article-2',
    date: 2022,
    details: 'Mamals',
    author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
    tags: [ 'HTML', 'css' ]
    },
    {
    \_id: '001',
    title: 'Article-0',
    date: 2023,
    details: 'Birds',
    author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
    tags: [ 'NodeJS', 'mongoDB' ],
    animal: 'Horse'
    }
    ]

13. Update an article's title using $set and without $set.

- Write the differences here ?

With using $SET:

blog> db.articles.update({\_id: '003'}, {$set: {animal: "Lion"}})
{
acknowledged: true,
insertedId: null,
matchedCount: 1,
modifiedCount: 1,
upsertedCount: 0
}
blog> db.articles.find().pretty()
[
{
\_id: '003',
title: 'Article-3',
date: 2021,
details: 'Reptiles',
author: { name: 'baby' },
tags: [ 'React', 'Express' ],
animal: 'Lion'
},
{
\_id: '002',
title: 'Article-2',
date: 2022,
details: 'Mamals',
author: { name: 'Arvind', email: 'arv@gmail.com', age: 24 },
tags: [ 'HTML', 'css' ]
},
{
\_id: '001',
title: 'Article-0',
date: 2023,
details: 'Birds',
author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
tags: [ 'NodeJS', 'mongoDB' ],
animal: 'Horse'
}
]

Without using $SET:-
It just puts that replaced value and removes existing fields.

13. find an article using title and increment it's auhtor's age by 5.

blog> db.articles.update({title: 'Article-2'}, {$set: {author: {age: 10}}})
{
acknowledged: true,
insertedId: null,
matchedCount: 1,
modifiedCount: 1,
upsertedCount: 0
}
blog> db.articles.find().pretty()
[
{
\_id: '003',
title: 'Article-3',
date: 2021,
details: 'Reptiles',
author: { name: 'baby' },
tags: [ 'React', 'Express' ],
animal: 'Lion'
},
{
\_id: '002',
title: 'Article-2',
date: 2022,
details: 'Mamals',
author: { age: 10 },
tags: [ 'HTML', 'css' ]
},
{
\_id: '001',
title: 'Article-0',
date: 2023,
details: 'Birds',
author: { name: 'Anand', email: 'anand@gmail.com', age: 27 },
tags: [ 'NodeJS', 'mongoDB' ],
animal: 'Horse'
}
]

14. Delete a document using \_id field with `db.COLLECTION_NAME.remove()`.

// Sample data

```js
db.users.insertMany([
  {
    age: 49,
    name: 'Maurice Brock',
    email: 'wuk@hibpiz.ch',
    gender: 'Female',
    sports: ['cricket', 'football'],
    scores: [24, 35, 18, 16],
    weight: 45,
  },
  {
    age: 37,
    birthday: '7/15/1986',
    name: 'Virgie Cunningham',
    email: 'ezogafa@de.gm',
    gender: 'Male',
    sports: ['football'],
    scores: [17, 35, 43],
    weight: 52,
  },
  {
    age: 48,
    birthday: '5/14/1961',
    name: 'Alexander Holt',
    email: 'han@mu.pe',
    gender: 'Male',
    sports: ['cricket', 'football', 'TT'],
    scores: [24, 30, 16],
    weight: 55,
  },
  {
    age: 53,
    birthday: '11/15/1963',
    name: 'Derek Dawson',
    email: 'polril@now.de',
    gender: 'Male',
    sports: ['cricket', 'hockey'],
    scores: [20, 15, 38, 23],
    weight: 49,
  },
  {
    age: 34,
    birthday: '7/24/1964',
    name: 'Cynthia Cobb',
    email: 'wujjarpob@jecimpar.gu',
    gender: 'Female',
    sports: ['cricket'],
    scores: [41, 17, 28],
    weight: 51,
  },
  {
    age: 33,
    birthday: '10/26/1982',
    name: 'Isabella Atkins',
    email: 'ononuzas@givhoz.ca',
    gender: 'Female',
    sports: ['cricket', 'football', 'hockey', 'TT'],
    scores: [14, 38, 29, 45, 20],
    weight: 49,
  },
  {
    age: 47,
    birthday: '10/12/1978',
    name: 'Katharine Bryan',
    email: 'zo@pebi.sa',
    gender: 'Male',
    sports: ['TT', 'hockey', 'khokho'],
    scores: [27, 20, 34],
    weight: 58,
  },
  {
    age: 41,
    birthday: '1/28/1991',
    name: 'Beatrice Fleming',
    email: 'ufufsa@pujizren.tk',
    gender: 'Female',
    sports: ['football', 'khokho'],
    scores: [30, 20, 15, 29, 43],
    weight: 47,
  },
  {
    age: 26,
    birthday: '3/23/1998',
    name: 'Tom Fields',
    email: 'wasodjow@ofaba.gf',
    gender: 'Female',
    sports: ['khokho'],
    scores: [37, 29, 18, 43, 49],
    weight: 50,
  },
  {
    age: 33,
    birthday: '11/14/1960',
    name: 'Steve Ortega',
    email: 'dupus@ca.ls',
    gender: 'Female',
    sports: ['cricket', 'football', 'hockey'],
    scores: [12, 15, 20],
    weight: 51,
  },
  {
    age: 24,
    birthday: '1/5/1994',
    name: 'Suraj Kumar',
    weight: 50,
    gender: 'Male',
    sports: ['football', 'cricket', 'TT'],
  },
]);
```

Insert above data into database to perform below queries:-

- Find all males who play cricket.
- Update user with extra golf field in sports array whose name is "Steve Ortega".
- Find all users who play either 'football' or 'cricket'.
- Find all users whose name includes 'ri' in their name.
