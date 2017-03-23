# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational and are very structured through the use of tables and schema, whereas NoSQL databases are non-relational and data is stored in a single file.  SQL databases are useful when you already have a defined organizational structure for your data, while NoSQL databases can be used for data without a pre-determined structure.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
var results = AuthorModel.findOne({name: "Bob"}, (err, author) => {
  if(err){
    console.log(err);
  }
  else{
    console.log(author);
  }
});
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
const andy = Instructor.findBy({name: "Andy"}, (err, instructor) => {
  instructor.wishListItems.push(new wishListItem({description: "Resin Laying Deer Figurine, Gold"}));
  instructor.save((err, results) => {
    if(err){
      console.log(err);
    }
    else{
      console.log(results);
    }
  });
});
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
# Your answer...
def create
  @author = Author.new({params[:name]})
  if @author.save
    redirect_to 'authors'
  end
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports encapsulates a piece of code and allows it to be used in other parts of an application.  It can be used to implement data on any page, such as in the Emergency Compliment homework, where saving a 'colors' module.export provided the ability to save the module as a variable in index.js and randomly select a color saved in the array.
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
})

app.post("/model", (req, res) => {
  Model.create(req.body.model).then(function(model){
    res.redirect("/model" + model.name);
  })
  res.send("Create");
})

app.post("/model/:name", (req, res) => {
  Model.findOneAndUpdate({name: req.params.name}, req.body.model, {new: true}).then(function(model){
    res.redirect("/model" + model.name)
  })
  res.send("Edit")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Line 1: Configures an app to use body-parser since Express doesn't include it anymore.
Line 2: This sets up body-parser to handle JSON POST requests.
Line 3: This sets up body-parser to handle form submissions.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
