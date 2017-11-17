# Express / Sequelize Review Notes

## Starting your app
* Steps
    * npm init -y
    * create app.js
    * install npm --save-dev
        * express, pg, sequelize, nodemon
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
            
    
    