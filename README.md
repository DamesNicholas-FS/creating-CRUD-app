# MERN Stack CRUD Application: A Beginner's Guide
Welcome! This guide will walk you through the process of creating a CRUD application using the MERN stack. MERN stands for MongoDB, Express.js, React.js, and Node.js, a powerful combination of technologies that enables you to build scalable, robust, and complex web applications.

### Prerequisites
Before we embark on this journey, there are a few tools and technologies we need in our development environment:

* [VS Code](https://code.visualstudio.com/) - A versatile and user-friendly code editor developed by Microsoft.
* [Node.js (LTS version)](https://nodejs.org/en) - Node.js is a server-side platform that executes JavaScript code.

### Setting Up Your Project
Let's start by setting up a new Node.js project:

1) First, create a new directory for your project by running the command `mkdir crudapp` in your terminal.
2) Move into the newly created directory using the command `cd crudapp`.
3) To initialize a new Node.js project, execute `npm init -y`. This command will generate a _package.json_ file in your project directory, which serves as the manifest file containing metadata about your application.
4) To develop our application, we need to install a few Node.js packages. Install them using the following command: `npm install express cors dotenv nodemon axios`.
5) Next, we'll set up the React part of our project. Run `npx create-react-app client`. This will create a new directory called `client` and setup a new React application in it.
6)Lastly, we'll create a new file named server.js which will be the entry point for our Express.js server. Use the `touch server.js` command to create this file.

### Additional Project Structuring
Before we dive into the coding, let's set up some more files and directories:
1) Create a `.env` file that will store our environment variables: `touch .env`.
2) Set up a directory for our Express.js controllers with a `controllers.js` file inside it: `mkdir controllers && touch controllers/controllers.js.`

# Start Coding!
With the project structure ready, let's start writing code for our server.

#### Setting up `server.js`
At the top of our `server.js` file, we'll start by importing the necessary modules:
``` javascript
const express = require('express');
require('dotenv').config();
const cors = require('cors');
```
This portion of the code is importing the necessary modules for your application:

* const express = require('express'); Express.js is a web application framework for Node.js that helps in building web applications. It simplifies the process of writing server-side JavaScript code by providing numerous features and functionalities like routing, middleware support, etc. Here, require('express') is importing the Express.js module into your application, and const express = ... is declaring a constant variable to hold the Express.js module.

* require('dotenv').config(); Dotenv is a module that loads environment variables from a .env file into process.env. Calling config() reads your .env file, parses the contents, and assigns it to process.env. Environment variables are a great way to configure your application and keep sensitive data, like database credentials, secure.

* const cors = require('cors'); The cors module is a middleware that can be used to enable Cross-Origin Resource Sharing (CORS). CORS is a security measure that restricts HTTP requests from being made across different domains. By using the cors middleware, your server can accept requests from different origins.

#### Now let's create an Express app and set up our middlewares:
```javascript
const app = express();

app.use(cors());
app.use(express.json());
```
Here, we're enabling CORS and setting up Express to parse JSON request bodies.

* const app = express(); Here, you're creating an instance of an Express.js application. This instance, which we've named app, has methods for routing HTTP requests, configuring middleware, and rendering HTML views among other things.

* app.use(cors()); This line is telling your Express.js application to use the cors middleware. This allows the server to respond to requests from different origins (other domains).

* app.use(express.json()); Express.json() is a middleware function in Express.js. It parses incoming request bodies in a middleware before your handlers, available under the req.body property. This is particularly useful when you want to extract JSON data from the body of POST requests.

#### Let's set up a simple test route:
```javascript
app.get('/', (req, res) => {
  res.send('Hello, World!');
});
```
This sets up a GET route on the path '/' that sends back 'Hello, World!' when accessed.

* This code defines a route handler for GET requests made to the root path ('/'). When a GET request is made to the root path, Express.js invokes the callback function specified: (req, res) => { res.send('Hello, World!'); }. In this callback function, req represents the HTTP request and contains information about the request. res is the response object, used to send back data to the client. Here, res.send('Hello, World!'); is sending a string 'Hello, World!' back to the client.

Finally, let's make our server listen on a port:
```javascript
const PORT = process.env.PORT || 5000;

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

* const PORT = process.env.PORT || 5000; This line sets the port on which your Express.js server will run. It first checks for a 'PORT' variable in the environment variables. If it doesn't exist, it defaults to port 5000.

* app.listen(PORT, () => {...} is telling your Express.js server to start listening for incoming HTTP requests on the specified port. The second argument is a callback function that's called when the server starts successfully. Here, it logs a message to the console indicating that the server is running and on which port.

This makes our server start listening on the port specified by the PORT environment variable or port 5000 if PORT is not set.

That's it for the basic server.js setup! As we proceed, we'll add more routes and functionalities for our CRUD operations.

Next, we'll connect our server to a MongoDB database using Mongoose, a popular object modeling tool for MongoDB in Node.js. This will be followed by defining data models and routes for our application.
