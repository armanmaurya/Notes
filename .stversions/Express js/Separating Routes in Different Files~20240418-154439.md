By separating routes in different files we can make out code more professional and organizable and out code code look clean and easy to debug.

## Steps to make routes in different files:-
### Step-1:-
Make a example route file in `src/routes/example.js`. To use the routes we make in different file we have to use the `express.Router()` to link route to out app.

`class: text-center`
**Approach-1 (Not For Large Projects)** 

It you want to run the function in same file the you can you this but this is not good approach.
```js
const express = require('express');
const router = express.Router();

router.get("/", (req, res) => {
	res.send({
		data:"User Get"
	})
})

router.post("/", (req, res) => {
	res.send({
		data:"Registerd"
	})
})

module.exports = router;
```

`class: text-center`
**Approach-2 (For Large and Collaborative Projects)**

Above approach is good by it is good for testing purpose we have to separate the response function in different files for organization. We will create the the file in `src/controllers/example.js` this file will contain all the function that will run based on the route defines in `src/routes/example.js`.

```js
const express = require('express');
const router = express.Router();


router.get("/", (req, res) => {
	res.send({
		data:"User Get"
	})
})

router.post("/", (req, res) => {
	res.send({
		data:"Registerd"
	})
})

module.exports = router;
```

#### Step-2:-
In `src/index.js` start a `expressjs` server on you preferred port. 
```js
const express = required('express'); 
const app = express();
const PORT = 3000; // Define the port you want to listen.


// Listen to that port
app.listen(PORT, () => {
	console.log(`App listening on port ${PORT}$`)
})
```



****