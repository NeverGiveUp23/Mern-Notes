# Faker API Example using Express, Routing and Faker Api.

- First I created a new folder in my desktop environment
  ```npm
  mkdir <folder name>
  ```
  - Next, cd into your new file and run this command
  ```npm
  npm install
  ```
  - Next, install ```Nodemon```, and enter your password(if needed)
  ```npm
  sudo npm i -g nodemon
  ``` 
  - Create a new ```package.json``` file using:
  ```
  npm init -y
  ``` 
  - Install Express & Faker (For this project):
  ```
  npm i express 
  ```
  ```
  npm install --save-dev @faker-js/faker
  ```
  - Finally, use ```code . ``` to open vs code window with your file, it shoould look like this:
  ```
  user@user-device "folder-name" % code .
  ```

  # Server.js

  Import express and faker:

  ```js
  const express = require("express");
  const app = express();
  const { faker } = require('@faker-js/faker');
  ```
  - In order to post data, we need to pull it off of the request object, add this:
  ```js
  // for POST Requests
  app.use(express.json());
  app.use(express.urlencoded({ extended: true }));
  ```

  # Creating Functions

  ### These functions return new random array of objects each time

  - I created a ```createUser()``` function that creates new users:
  ```js
  const createUser = () => {
    const newFakeUser = [
      {
        fullName: faker.name.fullName(),
        email: faker.vehicle.vehicle(),
        phoneNumber: faker.phone.number()
      },
      {
        fullName: faker.name.fullName(),
        email: faker.vehicle.vehicle(),
        phoneNumber: faker.phone.number()
      },
      {
        fullName: faker.name.fullName(),
        email: faker.vehicle.vehicle(),
        phoneNumber: faker.phone.number()
      }
    ];
    return newFakeUser();
  };
  ```

  - I created a ```createCompany()``` function that creates new companies:
  ```js
  const createCompany = () => {
    const newFakeCompany = [
      {
      companyName: faker.company.name(),
      companyPhrase: faker.company.catchPhraseDescriptor(),
      company: faker.company.bsAdjective()
      },
      {
      companyName: faker.company.name(),
      companyPhrase: faker.company.catchPhraseDescriptor(),
      company: faker.company.bsAdjective()
      },
      {
        companyName: faker.company.name(),
        companyPhrase: faker.company.catchPhraseDescriptor(),
        companyAbj: faker.company.bsAdjective()
      }
    ];
    return newFakeCompany();
  };
  ```

# Routes
### USERS
- The route that will show ```json``` data for creating new users looks like this:
  ```js
  app.get("/api/users/new", (req, res) => {
  res.json( { user: createUser() } );
  });
  ```

  - This is how that ```json``` data for new users will show on the browser:
  ```json
  {
    "user": [
          {
          "fullName": "Archie Hodkiewicz",
          "email": "Tesla Sentra",
          "phoneNumber": "(239) 647-3158 x8730"
          },
          {
          "fullName": "Erik Stroman",
          "email": "Toyota Explorer",
          "phoneNumber": "(558) 253-2644 x11643"
          },
          {
          "fullName": "Stuart Deckow",
          "email": "Porsche Model X",
          "phoneNumber": "868.313.9288"
          }
    ]
  }
  ```

### Companies
- The route that will show ```json``` data for creating new companies looks like this:
  ```js
  app.get("/api/companies/new", (req, res) => {
  res.json( { company: createCompany() } );
  });
  ```
- This is how that ```json``` data for new companies will show on the browser:
  ```json
  {
    "company": [
            {
            "companyName": "Pouros - Reynolds",
            "companyPhrase": "client-driven",
            "company": "front-end"
            },
            {
            "companyName": "Hane Inc",
            "companyPhrase": "impactful",
            "company": "end-to-end"
            },
            {
            "companyName": "King, Deckow and Mohr",
            "companyPhrase": "web-enabled",
            "companyAbj": "robust"
            }
    ]
  }
  ```

  # Company And Users

  - The route that will show ```json``` data for creating new companies & Users looks like this:
  ```js
  app.get("/api/user/company", (req, res) => {
  res.json( { 
    // creating an object for user and company
    // assigning key value pairs, value will pass in the functions 
    user: createUser(),
    company: createCompany() } );
  });
  ```
  - This is how that ```json``` data for new companies and users will show on the browser:

```json
  {

      "user": [
            {
            "fullName": "Kristen Cormier",
            "email": "Mercedes Benz Element",
            "phoneNumber": "709.299.3850 x97207"
            },
            {
            "fullName": "Danny Schultz",
            "email": "Ford Escalade",
            "phoneNumber": "536-499-0320 x783"
            },
            {
            "fullName": "Dr. Fernando Dibbert",
            "email": "Kia Mustang",
            "phoneNumber": "(612) 991-7479 x827"
            }
        ],

      "company": [
              {
              "companyName": "Anderson Group",
              "companyPhrase": "asymmetric",
              "company": "dot-com"
              },
              {
              "companyName": "Romaguera LLC",
              "companyPhrase": "well-modulated",
              "company": "customized"
              },
              {
              "companyName": "Fadel Inc",
              "companyPhrase": "modular",
              "companyAbj": "efficient"
              }
        ]
  };
```

### Finally at the bottom of our file to run our server

```js
const server = app.listen(8000, () =>
  console.log(`Server is locked and loaded on port ${server.address().port}!`)
);

```