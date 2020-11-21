# cat-cafe-express-lab
FS1020 - Express Introduction Exercise

This lab walks through the setup of a basic RESTful API setup using Express.js and also leveraging esm modules. 

## Setup
1. Make sure you are logged into `gitlab.com` and then click on `New Project`. Name the project: `cat-cafe-express-lab`. Before you click `Create Project`, ensure you have checked off the box: `Initialize repository with a README`
2. Clone the repository locally to continue.
3. Locally, make sure you in the folder of your repository and then initialize npm: `npm init`. Follow the given prompts. At the end you should have a `package.json` file.
4. Install esm and Express
```console
npm install express esm --save
```

5. Install Nodemon
```console
npm install nodemon --save-dev
```
The `--save-dev` flag means that install this dependency as a development dependency, meaning it should not be installed for production use. 

6. Lastly, let's create a a start and dev script in `package.json`.
```json
"scripts": {
    "start": "node -r esm index.js",
    "dev": "nodemon -r esm index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  }
  ```

7. Create a new file called `index.js`. In this file, we'll add the following code:
```javascript
import express from 'express'
const app = express()

// allows us to parse json 
app.use(express.json())

app.listen(3000, () => console.log("Express server is running"))
```

## Router Setup

 8. Make a new file `router.js`, let's set it up with the following code:
 ```javascript
 import express from 'express'
 const router = express.Router()

router.get('/', (req, res) => res.send('Hello world'))

 export default router
 ```
 
 
 9. In `index.js`, import your router 
 ```javascript
 import router from "./src/router.js";
 ```
 
 After the `app.use(express.json());`, let's mount our new routes, by adding a new route:
 ```javascript
 app.use(router);
 ```
 
10. Run `npm run dev` to test the server and see if route is working

 ## Database Setup

 11. Create a new folder called `src`
 12. In the `src` folder, create a file called `cats.js`.
 13. Insert the following array in cats.js
 
 ```json
let cats = [
  {
    id: 1,
    name: "Tuna",
    breed: "Siamese",
  },
  {
    id: 2,
    name: "Chester",
    breed: "Tabby",
  },
  { id: 3, name: "Blue", breed: "Naked" },
];

export default cats;
 ```
 
  14. Let make sure we have access to our cats database. In `router.js`, add the following import statement after the other import statements:
 ```javascript
 import catsDB from './cats.js'
```

15. Setup complete! Let's start making our routes!

TODO: PLEASE SEE link for what a full website would look like
https://www.figma.com/file/PXnLz4Suyfg4R3yxwHnlc4/Cat-Cafe-Express-Lab?node-id=3%3A81

TODO 1: create a GET route for landing page


TODO 2: create a GET route for all cats


TODO 3: create a POST route to add a cat to the database

BONUS: if any fields are blank, send a 400 error

BONUS: if all fields are filled out, show the list of cats


TODO 4:create a delete route that can delete one cat then shows the updated list of cats


TODO 5: create a put request to be able to edit one cat (hint: array splice)

BONUS: if cat is not found in database, send 404 error "Cannot find cat"

BONUS: if ID in body doesn't match the ID in the URI, send 400 error "Bad Request"



