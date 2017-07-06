# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database is structured around associations. For instance, a post can have many comments and a comment can belong to one post. A NoSQL database is more loosely structured and does not base itself on associations, though there can be relationships between models.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, results)
console.log(results)

```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.find({name: "Andy"}).then((description)=>{
  wishlist_items.create({description: "Resin Laying deer Figurine, Gold"})
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
# new
  def new
    @author = Author.new
  end

  # create
  def create
    author = Author.create!(author_params)
    redirect_to "/authors"
  end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
Module.exports defines objects that are to be exported with that file is 'required'
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get('/', (req, res) => {
  res.send('hello world')
})

app.post('/quotes', (req, res) => {
  console.log('Hello!')
})

app.post('/quotes/:title', (req,res)=>{
  quote.findOneandUpdate({req.params.title}), req.body.quote, {new: true})
  res.redirect('/quotes/' + quote.title);
})

app.post("/quotes/:title/delete", function(req,res){
  quote.findOneAndRemove({req.params.name}).then(function(){
    res.redirect("/quotes")
  });
});

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is based more on convention in that it comes prepackaged with a lot of structure and tools. Express developers liked more minimalism and allows the user to create more structure to the backend.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line requires bodyParser as middleware. The second line allows json post requests. The third line handles form submissions.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
