# AJAX To-Do List Lab
We're going to create a To-Do List website. Users will be able
to add items to a list and their items will be stored on the
server. Items will stay in the list when the user refreshes
the page.

Items will be destroyed if the server restarts! Nodemon will
make it restart every time nodemon detects you saving the file.

We will make data able to survive server restarts when we learn
how to use databases later.

## Project Setup

Install all of the project dependencies with `npm install`. The dependencies are
stored inside the `package.json` file that's created when someone runs `npm init`.

Run the server with `nodemon index.js`.

## body-parser

We're using a new library to read data passed to us from the server
from forms. It's called `body-parser`. There's some new configuration
code added to the top of our server that allows us to read data submitted
by a form.

```
// include the library using `require`
var bodyParser = require('body-parser')

// this is mandatory configuration that we just need to put in.
app.use( bodyParser.json() );       // to support JSON-encoded bodies
app.use(bodyParser.urlencoded({     // to support URL-encoded bodies
  extended: true
}));
```

Here's where we can handle a new route that accepts POST requests.
Notice how it uses two new things:

1. `req.body.item` reads the new todo item defined by input name="item"
   from the form in the HTML.
2. our post route redirects people to the root route
   where they can see the new list.

```
app.post('/todos', function(req, res) {
  console.log(req.body.item);
  todoList.push(req.body.item);
  res.redirect('/');
});

```

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

