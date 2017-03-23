# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database is a relational database, that is, the types of data that it stores have built in relations (one to one, one to many, many to many etc) whereas a NoSQL database does not have those relations built in (although, they can be built in to it). You might use a NOSQL database when you are worried that the format of the data might change, (i.e. new fields will be added to data, etc.) this is easy to accommodate in a NOSQL but not in a SQL database. In contrast, NOSQL doesn't scale well so large scale projects might be better undertaken with a SQL database.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.findOne({name: "Bob"}, (results) => {
  console.log(results);
})


// find will return an array, not a particular result, also no callback function here, possibility that console.log fires before the request to mongoose is complete.
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
InstructorModel.findOne({name: "Andy"}).then((result) => {
  let newOne = WishlistModel.create({description: "Resin Laying Deer Figurine, Gold"}).then((newOne) => {
    result.wishlist_items.push(newOne)
  })
})
// Im not super sure about nesting the promises here but that code looks otherwise right to me
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
Author.create(:name => params[:name])
 redirect_to "index"
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is the method we use to expose the contents of a js file to other js files in node.js. I believe we use this method of exposing files to other files in order to increase modularity and dryness of our code. (better than having all the contents of every file available to the contents of every other file)
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', (req, res) => {
  res.send("Read")
})
app.post('/', (req, res) => {
  res.send("Create")
})
app.put('/', (req, res) => {
  res.send("Update")
})
app.delete('/', (req, res) => {
  res.send("Destroy")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express runs in the Node.js runtime environment meaning it operates *asynchronously*, in contrast, rails runs in ruby meaning it is synchronous (no need to muck about with callbacks or promises, you can just write your code programmatically), also, Express is Configuration over Convention, Rails is Convention over Configuration.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line requires the body-parser dependency and stores it in a variable (which drives me crazy, should have used a const, not a var), the second line sets body-parser as your default program to deal with json (probably received from your backend api), the third line (as far as I know) is the line that sets body-parser to interpret data received from form inputs and query strings
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
