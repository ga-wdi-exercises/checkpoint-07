# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
a NoSql DB is a non-relational database as to where a SQL DB it is relation based such as one-one, one to many or many to many.  SQL are also table based as to NoSQL is document based, key value pairs, graph dB, or column stores.

You would use NoSQL if you were using a hierarchial data storage and a lot of data. SQL is good for a complex query.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// var authorsController = {
show(req){
  Author.findOne({name: req.name}, (err, author) => {
    console.log(author);
  })
}
}
authorsController.show({name: "bob"});
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer..
var andy = new Instructor ({name: Andy,
description: "Resin Laying Deer Figurine, Gold"})
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
Author.create({:name => ' '})
link_to "authors"
```rb

```
## Express

### Question #5

What is module.exports and why do we use it?

```module.exports takes code from one page, encapsulates it into a small line of code. this code can then be exported to other into a fdifferent file and used by calling the module.exports

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/', function (req, res){
  res.send('')
})
app.post('/', function (req, res) {
  res.send('')
})
app.put('/', function(res,req) {
    res.send('');
}, send);

app.delete(function(req, res) {
        object.remove({
            _id: req.params.object_id
        }, function(err, ) {
            if (err)
                res.send(err);

            res.json({ message: 'Successfully deleted' });
        });
    });

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```Express allows you to write server-side applications in JS, while rails. Rails has to be built out in the files and implemented to what specific file its to be used in. the framework in Rails is opinionated in that if you work on someone elses prior work itll be easier to work with language wise.

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
this is used to parse the text as Url encoded data. Its used for the POST so we can create and update through JSON
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
