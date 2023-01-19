# EXPRESS

### What is Express?

- A javascript framework written in javascript which acts as an interface to Node's server functionality. 
- Express allows us to create a robust server with more or less whatever architecture we choose.

# Using Express

Head to your terminal and install Express with this command after you've navigate to your file

``` npm 
npm install
```

- This will install all the dependencies of the project listed in the package.json file. In this case, the only dependency that will be installed is Express. If you do not download the file, this command will do nothing.

# Creating The Server

- To start we need to create a new project and create a new ```server.js``` file inside our new project folder.

- In our server.js file we need to import the express module using JavaScript's ``` require()``` statements, and then invoke express.

```js
const express = require("express");
const app = express();
const part = 8000;
```

- Now we have the ability to create our routes and send some data

``` js 
const  express = require("express");
const app = express();
const part = 8000;

// req is shorthand for request
//res is shorthand for response

app.get("/api", (req,res) => {
  res.json({ message: "Hello World" });
});
```

## *Note that the app instance has various HTTP verb methods that we can call. For example, by invoking ```app.get```, we're saying we want to handle GET requests at this paticular route ("/api"). The second argument passed to the get method is the callback function we want to run when the browser makes a request to this route.*

- Lastly ```app.listen()``` line of code that actually runs the server on a specified port.

```js 
app.listen( port, () => console.log(`listening on port: ${port}`) );
```

- Run the server by opening your terminal, navigating to the directory housing your server.js file, and typing

``` npm 
node server.js
```

- Now visit ```localhost:8000/api``` in your browser and see the response.


# NodeMon:

When we run the server using ```node server.js``` we will have to restart the server manually everytime we update our code: otherwise, the running app wil not reflect the changes. This is wher ```Nodemon``` comes in to play. 

- We can run the following command to install Nodemon globally

```npm
npm install -g nodemon
```

- Note if you're using ```MAC(or Linux)``` You may need to use ```sudo``` in order to install it globally.

``` npm
sudo npm install -g nodemon
```

- Now, instead of ```node server.js``` use ```nodemon server.js``` to run the server. Now, every change we make will save and restart the sever without us having to restart the server.