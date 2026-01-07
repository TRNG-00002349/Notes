# Unit: Javalin
# REST With Javalin

## Importance

* [Required](#importance:-required)
* [Preferred](#importance:-preferred)
* [Stretch](#importance:-stretch)

### IMPORTANCE: Required
[Back to top](#unit:-javalin)

* **What are the 3 handler types?**
  * Javalin provides three handler types to structure request handling:
  * **Before Handlers** - Executed before the main request handler
    * Used for logging, authentication, or request modifications.
  * **Endpoint Handlers** - Main request logic
    * Handles core business logic and generates responses.
  * **After Handlers** - Executed after the main request handler
    * Used for post-processing, logging, or modifying responses.

* **What are path parameters and query parameters?**
  * **Path Parameters** - They are part of the URL itself and are used to capture dynamic values in the endpoint.
  * **Query Parameters** - They are key-value pairs appended to the URL after a ?, used for optional filtering, sorting, or searching.

* **How the Context object can be used to access and manipulate request and response data?**
  * The **`Context`** object **`(ctx)`** plays a crucial role in handling requests and responses. It provides methods to access request data, modify responses, and manage session state.
    * The **`ctx`** object allows you to retrieve data from incoming HTTP requests, through **path parameters**, **query parameters** and **post** requests. 
    * The **`ctx`** object allows you to set **response headers**, **return JSON**, and **change status codes**.

* **What is a "REST"ful API?**
  * Keywords, concepts, or topics that should be in the response:
    * Architectural style for a web service
    * HTTP for communication - different verbs perform different functions
    * Endpoints to access resources, return representations of those resources
  * Possible follow-up questions:
    * **How do you communicate with a REST API? How to send/receive data from it?**
      * Through HTTP requests that are sent to a targeted endpoint.

* **Describe the process to complete an HTTP request.**
  * Keywords, concepts, or topics that should be in the response:
    * The client application generates the request, and transmits it to the server.
    * The server accepts the request, processes it, and responds.
    * The request may pass through routing or middleware to direct it to the correct endpoint, or tansform the request in some way.

* **What is the difference between the different HTTP methods/verbs? Which of these are idempotent?**
  * Keywords, concepts, or topics that should be in the response:
    * GET: Read only. Retrieves information from a database
    * POST: Allows you to add a record to the database
    * PUT: Allows you to update an existing record
    * DELETE: Allows you to remove a record from a database
  * Possible follow-up questions:
    * **Which would you use to retrieve a resource vs send a new resource vs update a resource?**
      * See above for answer.

* **What are the levels of status codes that can be sent in a response?**
  * Keywords, concepts, or topics that should be in the response:
    * 100: Informational
    * 200: OK/Successful
    * 300: Redirect
    * 400: Client Side Error
    * 500: Server Side Error
  * Possible follow up questions:
    * **Can you name some specific status codes?**
      * 404: Not Found
      * 403: Forbidden
      * 500: Internal Server Error
      * 503: Service Unavailable
      * 504: Gateway Timeout

* **What is included in an HTTP Request?**
  * Keywords, concepts, or topics that should be in the response:
    * HTTP Verb: GET, POST, PUT, DELETE
    * URI: Specifies the endpoint where the resource is located.
    * HTTP Version
    * Request Header: META-DATA (information) of the Request as key-value pairs such as format supported by the client, browser type, etc
    * Request Body: Message content or resource representation
    * Status/Response Code: Gives information on how the request was processed

* **What are the 6 constraints of a RESTful API? Explain them.**
  * Keywords, concepts, or topics that should be in the response:
    * Client-server architecture: the client (that makes requests) and the server (that gives responses) stay separate and independent.
    * Statelessness: handles calls independently of each other. Each API call has to contain the data and commands necessary to complete the desired action.
    * Uniform interface: URL endpoints
    * Cacheability: the client has the option to locally store certain pieces of data for a predetermined period of time. When they make a request for that data, instead of the server sending it again, they use the stored version.
    * Layered System: each layer does its function and then sends the data to the next one. Connected layers communicate with each other, but not with every component of the program
    * Code-on-demand (optional): allow code or applets to be sent through the API and used for the application
  * Possible follow-up questions:
    * **Can you explain [any of above] in more detail?**
      * See above for answer.


### IMPORTANCE: Preferred
[Back to top](#unit:-javalin) 

* **Explain Exception Handling Techniques in Javalin.**
  * **Global Exception Handling**: Javalin allows setting up global exception handlers using the **`exception()`** method. 
  * **Try-Catch Blocks**: Use traditional **`try-catch`** blocks inside route handlers for fine-grained control.
  * **Error Mappers for HTTP Status Codes**: Define error handlers for specific HTTP status codes using the **`error()`** method.

* **Differentiate between Authentication and Authorization**
  * **Authentication** - Verifies who the user is. Example, logging into an app.
  * **Authorization** - Determines what the user is allowed to do. Example, Checking if a user can edit a file. 

* **What is a session and why might it be important to keep track of sessions?**
  * A session is a way to store user-related data across multiple requests within a web application. 
  * It allows the server to keep track of user interactions and maintain state.
  * It is important because of following reasons, 
    * Helps identify logged-in users without requiring repeated login.
    * Stores user preferences or shopping cart data.
    * Prevents unauthorized access by managing session expiration and renewal.

* **Can you list some common HTTP request & response headers?**
  * Keywords, concepts, or topics that should be in the response:
    * Accept
    * Content-Length
    * Content-Type
    * Cookie
    * Access-Control-Allow-Origin (CORS)

* **Can you describe URL conventions when using REST.**
  * **Use Nouns, Not Verbs** 
    * URLs should represent resources (nouns) rather than actions (verbs). The HTTP method (GET, POST, PUT, DELETE) defines the action.
  * **Use Plural Resource Names**
    * Always use plural nouns for resources to indicate collections. For example, **`/users`**. 
  * **Use Hyphens (-) Instead of Underscores (_)**
    * Use hyphens (-) instead of underscores (_) or camelCase for readability.
  * **Use Lowercase Letters in URLs**
    * Use lowercase letters to keep URLs case-insensitive.
  * **Avoid File Extensions in URLs**

* **Can you describe Service Oriented Architecture, and how it uses REST?**
  * Keywords, concepts, or topics that should be in the response:
    * Client-Server application architecture
    * Separate services by function. ie. front-end, user service, order service, etc.
    * Evolution of 'separation of concerns'
    * Can be developed into Microservice 


### IMPORTANCE: Stretch
[Back to top](#unit:-javalin)

* **Where would authorization tokens be sent in an HTTP request?**
  * Keywords, concepts, or topics that should be in the response:
    * Header

* **What data formats can REST APIs support?**
  * Keywords, concepts, or topics that should be in the response:
    * Plain text, XML, JSON, etc
  * Possible follow-up questions:
    * **What is the concept of content negotiation between clients and servers? (rephrase: how do clients/servers know which data formats to send?)**
      * The client can set the Accept header to tell the server what data formats it is able to accept

* **What does the term HATEOAS mean?**
  * Keywords, concepts, or topics that should be in the response:
    * Hypertext as the Engine of Application State
    * Send links to other references for easier client navigation of the API
    * Keeps client and server loosely coupled

* **Explain the JSON Web Token structure?**
  * Keywords, concepts, or topics that should be in the response:
    * Header - contains "type" (jwt) and "algorithm" (e.g. SHA256)
    * Payload - contains data about the user, e.g. what role they are claiming
    * Signature - verifies the message has not been changed
    * JWTs are sent in the Authorization header

* **Explain the difference between REST and SOAP messaging.**
  * Keywords, concepts, or topics that should be in the response:
    * Simple Object Access Protocol - Relies on XML, is protocol agnostic, can be slower, generally larger messages, and more complex to scale. Relies on Web Service Description Language docs to define operations, types, and formats, creating a tight coupling.
    * Representational State Transfer - Is format agnostic, relies on the HTTP protocol, generally faster, with smaller messages, and easier scaling. Allows for loose coupling of services.




