# Week 10


## Mongoose


### Question #1


Describe the differences between a SQL and NoSQL database, and when you might use each.


```text
SQL is a relational database, while NoSQL are non relational.  You would use SQL if your data is more structured, while you would use NoSQL if you had a short development cycle.
```


### Question #2


What's wrong with this Mongoose code and how might we fix it?


```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```


> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?


```js
var results = AuthorModel.find({name: "Bob"}).then(author)=>{;
console.log(results);
}
```


### Question #3


Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:


```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```


```js
var instructorsController = {
  index(){
    Instructor.find({}, (err, instructors) => {
      console.log(instructors);
    })
  },
  show(req){
    Instructor.findOne({name: req.name}, (err, instructors) => {
      console.log(instructor)
    })
  }
}


instructorsController.show({name: "Andy"})


var wishlist1 = new Wishlist({description: "Resin Laying Deer Figurine, Gold" })


andy.wishlist_items.push(wishlist1)


```


### Question #4


Convert the following create method in Mongoose to ActiveRecord.


```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("authors")
  }
})
```


```rb
# Your answer..


author1 = Author.create({name: params[:name]})
redirect_to author_path(@author)
```


## Express


### Question #5


What is module.exports and why do we use it?


```text
It's so we can reference these models in other files by requiring 'schema.js'
```


### Question #6


Write one Express route for each of the four HTTP methods.


Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.


```js
var express = require("express");
var app = express();


// Your code starts here...


app.get("/", (req, res) => {
  res.send("Get");
});


app.post("/object", (req, res) => {
  res.send("Create")
})


app.post("/object/:id", (req, res)=>{
  console.log("Update")
})


 app.delete("/object/:id", (req, res)=>{
   console.log("Delete")
})
```


### Question #7


Describe the differences between Express and Rails as backend frameworks.


```text
Express is much less opinionated then rails.  It's also light in weight.  
```


### Question #8


What do the following lines of code do?


```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```


```text
body-parser is a middleware that runs in between recieving the request and responding.


the first 'App.use' handles json post reqeusts, while the second 'app.use' handles form submissions.
```


### If You Finish Early...


Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
