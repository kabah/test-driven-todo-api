<!--
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Todo App - Test Driven RESTful JSON API

By the end of the challenges, **you should have** a JSON API with a full set of RESTful routes:

| RESTful Route             | Description                         |
| :------------------------ | :---------------------------------- |
| `POST`   `/todos`         | Create a new todo record ("create") |
| `GET`    `/todos`         | Fetch a list of todos ("index")     |
| `GET`    `/todos/10`      | Fetch a specific todo ("show")      |
| `PUT`    `/todos/11`      | Change a specific todo ("update")   |
| `DELETE` `/todos/11`      | Remove a specific todo ("destroy")  |
| `GET`    `/todos/search`  | **Bonus**: Search todos ("search")  |

## Getting Started

1. Fork this repo, and clone it into your `dev` folder on your local machine.
2. Follow the instructions to setup your test suite (below)
3. Run the tests, and try to make the _red_ (failing) tests turn _green_ (passing). Then move on to bonuses.

## Test Driven Development (TDD)
For this challenge, we'll be testing our JSON API using a testing framework called [Mocha](http://mochajs.org/) and assertion library called [Chai](http://chaijs.com/).

The tests have already been written for us! Our goal is to try to understand the **test output** so that we can write _server-side code_ that will make the *red* (failing) tests turn *green* (passing).

The tests will help guide our development process, and keep us focused on our end goal: a RESTful, full-CRUD, JSON API.

#### Test Setup
From inside your cloned directory, run:

``` bash
npm install -g mocha    # globally install the mocha test framework
npm install             # download package.json dependencies for this project
```

Next, run your server:
``` bash
node server.js
# or better yet
nodemon server.js
# or just
nodemon
```

Finally, _open a new teminal tab/window_, and run the test suite (you'll need to switch back and forth between your server output and your test output a lot):
``` bash
mocha test/todosTest.js
# or just
mocha
```

> Your server _must_ be running in order for the Mocha tests to be able to make API requests to your API endpoints.

By the end of this assignment you'll hopefully see this glorious output:

    Todos API
       GET /api/todos (index)
         ✓ should respond with status 200
         ✓ should respond with a JSON object
         ✓ should respond with a JSON object containing a list of todos
         ✓ todo objects should have properities: _id, description, task
       GET /api/todos/:id (show)
         ✓ should respond with status 200 - Success
         ✓ should respond with JSON
         ✓ should fetch one specific todo by _id
       POST /api/todos (create)
         ✓ should respond with status 200 - Success
         ✓ should respond with JSON
         ✓ should respond with the new todo object
         ✓ should assign an _id to the new todo object
         ✓ should increment the _id number by one each time a todo is created
       DELETE /api/todos/:id (destroy)
         ✓ should respond with 200 or 204 on success
         ✓ should delete one specific todo from the list of todos
       PUT /api/todos/:id (update)
         ✓ should respond with status 200 - Success
         ✓ should respond with JSON
         ✓ should update the properities of one specific todo
       GET /api/todos/search (search)
         ✓ should list all todos that contain the search term from the query parameter (e.g. `?q=discover`) in the task field

But for starters you'll see output that looks like this:

    0 passing (84ms)
    9 failing

    1) Todos API GET /api/todos (index) should respond with status 200:

        Uncaught AssertionError: expected 404 to equal 200
        + expected - actual

        -404
        +200

> You can think of each failing test as being like a trail of breadcrumbs. If you pay close attention to the error messages, it should give you a clue about what to do next!

Why is the server responding with status `404 - Not Found` when we try to `GET /api/todos`?

Take a look at `server.js` and see if you can figure it out!

## Bonuses
1. Build a way for a user to search for todos. You'll need:
    * A new html page called `views/search.html` that's served from your application.
        * Make sure to connect it to `styles/main.css` and `scripts/main.js`!
    * Can you consume the `/api/search` endpoint and display search results on the page? Can you get it to work with queries the user enters into an input field?

2. Build a way for a user to mark a todo as "done". You'll need:
  * A styling change on the client to indicate the todo is "done" (this should be persistent if the user refreshes the page)
  * A request (AJAX) to mark the todo as done (update it) on the server

## Submission

* As you make code changes, commit frequently and push to your fork on GitHub.

### Self Evaluation

During the previous exercise, rate your progress on a scale of 1-5 (5 being the highest) for the following criteria:

- **Persistence:** Do you handle frustration well? Do you independently pursue understanding?
- **Organization:** Do you thoughtfully implement best coding patterns and practices?
- **Collaboration:** Do you make an effort solve problems and share your ideas with others?
- **Communication:** Do you clearly convey your thoughts to others in illustrative and clear ways?
- **Self-compassion:** Do you make productive use of turning failures into learning opportunities?
- **Resourcefulness:** Do make an effort to compare and contrast new ideas with ones you already know?
