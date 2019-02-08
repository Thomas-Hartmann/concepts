# Mongo db
Mongo db is a no-sql database.
It uses documents instead of tables.
Tables are called collections
Collections do not describe or enforce the structure of its documents.
[This document is based on this resource](https://docs.mongodb.com/manual/reference/sql-comparison/)

### Terminoligy

|SQL Terms/Concepts |	MongoDB Terms/Concepts|
|----------|-------------|
|database |	database|
|table |	collection|
|row |	document or BSON document|
|column |	field|
|index |	index|
|table joins |	$lookup, embedded documents|

|primary key:Specify any unique column or column combination as primary key.

|primary key:In MongoDB, the primary key is automatically set to the _id field.|

#### Database server
`mongod`

#### Database client
`mongo`

#### `create` statement
Like in sql a collection (table) can be created:
`db.createCollection("people")`.  
But we can also create a collection just by inserting to it (it will the be created automatically)
```
db.people.insertOne( {
    user_id: "abc123",
    age: 55,
    status: "A"
 } )
 ```
 - The primary key in mongodb is always _id. If not explicitly given it will be created anyway.
- Create new database: `use <dbname>` this will create a new database and switch context to it. 

### See number of open connections
- `db.serverStatus().connections;`
- 
db.quotes.insertOne( {
    name: "yoda",
    quote: "May the force be with you my young paddiwan"
} );