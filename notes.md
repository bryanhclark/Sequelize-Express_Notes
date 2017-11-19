# Express / Sequelize Review Notes

## Starting your app
* Steps
    * npm init -y
    * create app.js
    * install npm --save-dev
        * express, pg@6 DO NOT INSTALL ANY OTHER VERSION OF pg, sequelize, nodemon
    * require 
        * express, 
        * innvoke app = express()
    * make '/' .get route
    * app.listen, create port
    * in package json, create "start" : nodemon app.js



## Models
* Steps
    * create models folder
    * one file per model (your preference)
    * require dependencies for models
        * sequelize
    * create new instance of sequelize 
        * pass in database adress
    *  make sure you createdb in postgress


*  Models
    *  name model and use db.define (3 params)
        *  name
        *  attributes
            *  can pass in object to add different props Ex: allowNull
        * 'options'
    * set relations between multiple models (tables)
        * Ex. One to Many, Many to Many
        * Ex. Category.hasMany(Todo);
        * Todo.belongsTo('Category')
        * !!Create relationship both ways to create methods in both directions of relationship!!
        * export you models to you express app!!
            *  in your export model, if key and value have the same string, just type once
*  App
    * require models in app
    * sync db in app.listen
        *  returns promise -> you can console log 'listening on port' here
        *  put a catch on the app.listen to check for errors
*   error handler in route
    *  use a middlewhere
        *  app.use (err, req, res, next)
            *  res.status(500).send('error message')


*  Show db info
    *  use models
        *  models, db, Page, User, task
    * Get all todos
       *   Todo.findAll (class method)
       *  render your html files
       * use nunjucks to set up rendering your html files with sequelize queries

* Nunjucks Setup
    * require nunjucks
    * 3 other things:
        * const env = nunjucks.configure('views', {noCache: true})
        * app.engine('html', nunjucks.render)
        * app.set('view engine', 'html')
            * this allows you to not need to add .html to your res.render arguments
    * create views folder
        * index.html 
        * use nunjucks looping method to render your sequelize query
        * {{ this is the nunjucks bracket notation }}
        *  look at wikistack code for nunjucks boilplate for importing variables into html files
        * res.render appropriate html file and include your query object as 2nd argument in res.render
    * ERROR HANDLING
        * Ex: checking for single Todo
            * check if(todo) -> res.render like normal
            *  else
                * create new error 
* Forms
    * all based on action field
    * look at wikistack for form example
    * get values out of POST forms with req.body (body-parser)

*  Router File
    * in app.js import routes file
    * app.use(routes)
    * can't make a second app in router file
        * require express
        * have to make a express.Router()

* Getters and Setters
    * Getter: when the user wants to get info from the DB, when they want to look up a value
        * runs when you want to fetch something to the db
            * Ex: Get a fullName from FirstName + LastName
        * in-class example: get title of Todo all in uppercase
        * use .getDataValue()
        *  get(){} is the same as get: function(){}
            * when a property points to a function

    * Setter: when the user tries to set some value
        * when you want to input something to the db

* Things to remember
    * .findOrCreate()
        * returns an array
        * [0] is the actual data
        * [1] is a boolean stating if the data was created or not
            * check documentation to make sure [1] is was created or wasFound   
    * association objects
        * use .build -> then setAssociation -> save()
        * {as: ''} sets an alias for the association
            * don't need to pass this
    
    
    


        
            
    
    