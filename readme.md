
## Files used and their importance: 

## variables.env [ LIKE database.php]
 	- has all the variables which are important and confidential

## app.js
	- to load external packages and other helpful libraries eg: mongoose, express, connect-flash, es6-promisify etc

## start.js 
	- site starts in start.js
	- import environmental variables from our vriables.env
	- connect to our Database and handle any bad connections
	- import all of our models
	- start app, define port

## helpers.js
	- has custom helpers which can be used all over the project eg: exports.dump, exports.staticMap etc

## ROUTES:

- index.js
	- load files so that their functions/methods can be used
		``` 
		eg: const express = require('express');
			const router = express.Router();
			const storeController = require('../controllers/storeController');
			const { catchErrors } = require('../handlers/errorHandlers');
 	- set all the routes and join them with the respective controllers
 		eg:	router.get('/', catchErrors(storeController.getStores));
			router.get('/stores', catchErrors(storeController.getStores));
			router.get('/add', storeController.addStore);
			router.post('/add', catchErrors(storeController.createStore));
		```
## CONTROLLERS:

- storeController
	- load views using 
		``` res.render('editStore', { title: 'Add Store'}); ```
	- get and insert data from db using the following:
		- [insert] 
			``` const store = await (new Store(req.body)).save(); ```
		- [select specific]
			``` const stores = await Store.find(); ```
		- [select all]
			``` const store = await Store.findOne({ _id: req.params.id}); ```
	
## MODELS: (model name should start with an uppercase letter)

- Store.js
	- load mongoose, promise etc
	- define table schema
	- have to confirm on the use of slug

## VIEWS

- layout.pug
	- a basic template which contains a div named "content" which can be filled by other views by extending this view

## MIXINS: 
- a sub element of a view which may be used multiple times in a view eg: form, div cards etc
