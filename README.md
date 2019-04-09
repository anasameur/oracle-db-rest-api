# oracle-db-rest-api
Creating a REST API with Node.js and Oracle Database 


I like to organize my REST APIs into four core components or layers. Incoming HTTP requests will usually touch each of these layers in turn. There may be a lot more going on depending on the features an API supports, but these components are required.

## Web Server:
 The role of the web server is to accept incoming HTTP requests and send responses. There are many options for web servers in Node.js. At the lowest level, you could use the built-in modules, such as http, https, and http2. For most folks, those modules will be too low level. I like to use Express for the web server as it’s very popular, flexible, and easy to use. There are many other options, such as restify, kracken, and hapi. You might consider some of these options as you experiment more with APIs over time.
## Router:
 Routing logic is used to define the URL endpoints and HTTP methods that the API will support. At runtime, this layer will map incoming requests to the appropriate controller logic. The implementation of the routing logic is almost always tied to the choice web server as most include a means to define routes. I’ll use the Router class that comes with Express to create a single router for the app.
## Controllers:
 The controller layer will be comprised of one JavaScript function for each URL path/HTTP method combination defined in the router. The function will inspect the request and pull data from it (URL, body, and HTTP headers) as needed, interact with appropriate database APIs to fetch or persist data, and then generate the HTTP response.
## Database APIs:
 The database APIs will handle the interactions with the database. This layer will be isolated from the HTTP request and response. Some developers will prefer to use an Object Relational Mapper (ORM), such as Sequelize, to abstract away the database as much as possible. For those folks, this layer is often called the model layer because ORMs work by defining models in the middle tier. I’m going to start at a lower level and work directly with the Oracle Database driver for Node.js (node-oracledb).
