A SQL database is relational and a noSQL is non relational. In a noSQL database data is denormalized
so it all sits in one place unlike relational where we need to query data through a database

Student.find({name: Andy})

@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")

var studentsController = {
  index(){
    Student.find({}, (err, students) => {
      console.log(students);
    });
  }
};

EXPRESS

5. Module exports allows us to move functions and variables from one page to another.

6. app.get("/", (req,res) => {
  res.render('index', {
    a:a,
    b:b,
  })
})

  app.post("/", (req,res) =>{
    res.render("index", {
    player_name: req.body.player_name
    })
  })

  app.get("/:name", (req,res =>){
      Candidate.findOne({name: req.params.name}).then(candidate =>{
      res.render("show", {
      x:x,
      })
      })
  })


7. Rails is opinionated and Express isn't

8. var bodyParser = require("body-parser") --This declares a variable allowing us to use the npm installed body parser
   app.use(bodyParser.json()) --this line handles json post requests
   app.use(bodyParser.urlencoded({extended: true})) this line handles form submissions
