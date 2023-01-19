# MongoDB Commands
---
Here are 3 basic comparisons alongside a SQL database

| Database Type: | SQL | Mongo |
| -------------- |-----| ------|
| Database       | Schema | Database (db) |
| Collection of related records | Tables | Collections |
| Each one record in the collection of records | Row/ Record | Document |

---
###### Some MongoDB Database(db) Commands

Note that from our Mongo shell, we have access to all the database stored on our Mongo server.
* CollectionName in the examples should be replaced with your actual DB name*

| Show all databases available in out MongoDB server | ```show dbs``` | 
| -------------- |-----| 
| Create a new colection      | ```db.createCollection("collection_name")``` |
| destroy a collection       | ```db.collection_name.drop()``` |
| Delete database(in file)     | ```db.dropDatabase()``` |
| Change to another database Note: if database does not exist, Mongo will create a new database and switch to it | ```use DB_NAME``` |
| Find all documents in a collection      | ```db.collectionName.find()``` |
| Find documents that match a specific condition | ```db.collectionName.find({fieldName: "value"})``` | 
|Sort the result of a query| ```db.collectionName.find().sort({ fieldName: 1})``` | 
|Limit the number of documents returned     | ```db.collectionName.find().limit(number)``` |
| Update a specific document     | ```db.collectionName.update({fieldName: "value"}, {$set: {newFieldName: "newValue"}})``` |
| Update multiple documents      | ```db.collectionName.updateMany({fieldName: "value"}, {$set: {newFieldName: "newValue"}})``` |
| Delete a specific document    | ```db.collectionName.deleteOne({fieldName: "value"})``` |
| Delete multiple documents      | ```db.collectionName.deleteMany({fieldName: "value"})``` |
|Not sure if a database exist| ```db.getCollection("user").find()```|

##### Here are more examples using a fake collection name for you to better understand.

  1. Find all documents in the ```users``` collection:
  ```js
  db.users.find()
  ```
  2. Find all documents in the ```users``` collection that have an ```age``` field equal to 25:
  ```js
  db.users.find({age: 25})
  ```
  3. Sort the documents in the ```users``` collection by ```name``` in ascending order:
  ```js
  db.users.find().sort({"name": 1})
  ```
  4. Limit the number of documents returned from the ```users``` collection to 5:
  ```js
  db.users.find().limit(5)
  ```
  5. Update the ```location``` field for the document in the ```users``` collection with the ```name``` field to ```john``` to ```new york```:
  ```js
  db.users.update({"name": "John"}, {$set: {"location": "new york"}})
  ```
  6. Update the ```location``` field for all documents in the ```users``` collection that have a ```location``` field equal to ```Los Angeles``` to ```LA```:
  ```js
  db.users.updateMany({"location": "Los Angeles"}, {$set: {"location": "LA"}})
  ```
  7. Delete the document in the ```users``` collection with the ```name``` field equal to ```Jane```:
  ```js
  db.users.deleteOne({"name": "Jane"})
  ```
  8. Delete all documents in the ```users``` collection that have an ```age``` field equal to ```30```.
  ```js
  db.user.deleteMany({"age": 30})
  ```
  9. Group the documents in the ```users``` collection by ```location``` and count the number of occurrences of each location:
  ```js
  db.users.aggregate([{$group: {"$location", total: {$sum: 1}}}])
  ```
  1.  Join the ```users``` collection with a collection named ```orders``` on the ```name``` field, creating a new array field named ```orders``` in the documents of the ```users``` collection:
  ```js
  db.users.aggregate([{$lookup: {from: "orders", localField: "name", foreignField: "name", as: "orders"}}])
  ```
