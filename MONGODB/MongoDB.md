# MongoDB

##### What is Mongo DB?

Mongo db is a NoSQL database. NoSQL stands for ```Not only SQL```. What that means is that while NoSQL does support a ```structured query language(SQL)``` there is more flexibility in the storage of the data other than just basic ```tabular storage```(aka housing data in tables). Most importantly, the concept of ```noSQL``` database emphasizes that there are no relations between the data. Think of it this way:

##### In a NoSQL envirnment, every piece of data is unaware of the pieces.

To be more conise:

#### No JOINS

The ideal envirnment to use a ```NoSQL``` database in is one that focuses on speed while having little to no need of relationships between tables (or objects in this case). Reason being: Joins are an expensive operation. 
- Think about the concept of join:
  ```mySQL
  SELECT * FROM users LEFT JOIN address ON users.id = address.user_id
  ```
  For every user we have to find the address that matches specifically one piece of information in the address table. Doing this for every entry in your table would take a lot of time.

  - With the ability of Node servers to use socket connections, we now have the ability to communicate in real-time between clients and servers. But if we need to do an expensive operation on the server side with the database, we'll negate all the speed advantages we've gained using a Node server. 

### Why MongoDB?

- Everything stored in ```MongoDB```  database is a ```JSON``` object.
- ```High scalability and performance```: MOngoDB is designed for horizontal scalabilty, which means it can easily handle large amounts of data and a high number of concurrent users.
- ```Flexible schema```: MongoDB uses a ```document-based model```, which allows for a more ```flexible schema``` and easy changes to the structure of the data without affecting the overall database.
- ```Rich Query Language```: MongoDB supports a ```rich query language``` that allows for powerful and efficient querying of data.
- ```Ease of use```: MongoDB's document-based data model and rich query language make it easy to learn and use, even for devs who have no exp with databases

J.S.O.N is a JavaScript object Notation. Here is an example

```js
{
 'first_name': 'James',
 'last_name': 'Johnson',
 'age': 32
}

```

# Installing MongoDB

##### There is no GUI(Grapghical user interface) for MongoDB(at least not yet); anytime we want to query you MongoDB, you ,ust access it through the command line.

These are command lines to run to access you MongoDB

```npm
brew tap mongodb/brew
```
We are using version 5.0
```npm
brew install mongodb-community@5.0
```

##### Running the MongoDB Server:
```npm
brew services start mongodb-community@5.0
```
###### Connect to your database:

To connect to your MongoDB databases, in your terminal, type...
```npm 
mongosh
```

##### Shutting down if your mongod window got closed:

Open a terminal window and type:
```npm
ps -ax | grep mongosh
```
then copy the number on the left of the row that shows 'sudo mongo' (or if that's not there, just 'mongo')  This is the process ID of the mongod command you ran.  Take that number and type

```npm
sudo kill *that_number*
```
And you'll be good.  The kill command tells a process ID to terminate.