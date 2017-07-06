# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL databases are non-relational and relatively light weight. They work well with data or models that don't interact with each other alot. SQL databases are relational and can handle complex relationships with ease.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.find({name: "Bob"},function(err, author){
	console.log(author)
})
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}).then((person)=>{
	person.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
})
```

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("/authors")
  }
})
```

```rb
@author = Author.new(params[author_params])
if @author.save
	redirect @authors
else
	#error funtion here
end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
It allows a js file to access some of the code from another js file. We use it to seperated concerns and still be able to use that data else where in the app
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/post",function(req,res){
	Post.find({}).then((posts)=>{
		res.send("GET")
	})
})
app.post("/post",function(req,res){
	Post.create(req.params.body).then((post)=>{
		res.send("POST")
	})
})
app.post("/post/:id",function(req,res){
	Post.findOneAndUpdate({Params to find},{params to update},{new:true}).then((post)=>{
		res.send("PUT")
	})
})
app.post("/post/:id/delete",function(req,res){
	Post.findOneAndRemove({parmas to find},function(){}).then(()=>{
		res.send("DELETE")
	})
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is very lightweight and features only the basics "out of the box". It has little convention to it so it allows one to customize and use what they wish. Rails is convention heavy but also features a lot of built in functionality.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line imports the use of "body-parser" to the app.
The JSON and urlencoded lines tell the app what functions of body-parse to make available and use
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
