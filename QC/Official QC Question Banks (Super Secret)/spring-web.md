## Unit

# Spring Web

## Links

* [Required Questions](#required-questions)
* [Preferred Questions](#preferred-questions)
* [Stretch Questions](#stretch-questions)

## Required Questions

* **Explain the MVC architecture and how HTTP requests are processed in Spring MVC:**
    * **Model-View-Controller (MVC)** is a design pattern that separates the application into three components:
      * **Model**: Holds data and business logic.
      * **View**: Renders the data to the user (e.g., JSP, Thymeleaf).
      * **Controller**: Processes user input and interacts with the Model and View.
    * In Spring Web (Spring MVC), the **DispatcherServlet** acts as the **Front Controller**, receiving all incoming HTTP requests.
    * It delegates to the correct **Controller** based on handler mappings.
    * The controller processes the request, interacts with the **Model**, and returns a logical view name.
    * The **ViewResolver** maps the logical view name to an actual view technology (like JSP or Thymeleaf).
    * Finally, the View is rendered with the model data and sent back to the client.

    * In **Spring Boot**, `DispatcherServlet` and `ViewResolver` are auto-configured. You don’t need to declare them manually in `web.xml`.

* **What concerns is the controller layer supposed to handle vs the service layer?**
    * the controller is the manager, while the service is the worker
    * *Controller* handles incoming requests, does some checking/validation to figure out to which service(s) should the data from the request be sent to, and orchestrates those service calls
    * *Service* handles the business logic/algorithms/database calls/etc and returns the information back to the controller

* **What is the difference between `@Controller` and `@RestController`?**
    * `@Controller`: Marks class as Spring Web controller
    * `@RestController`: Combination of `@Controller` and `@ResponseBody` for RESTful web services.

* **How would you extract query and path parameters from a request URL in your controller?**
    * `@RequestParam` and `@PathVariable` can both be used to extract values from the request URI
    * `@RequestParam` bindings are similar to `@PathVariable` binding, however the query string mapping is not included in the handler mapping path attribute. The bindings are included in the parameter list much like `@PathVariable`

      * ```java
          public class MyController {
          @GetMapping(path="my_data") // query parameters aren't included in the mapping
          public ResponseEntity getData(@RequestParam LocalDateTime createdOn){...} // @RequestParam extracts values from query parameters (e.g., /my_data?createdOn=2023-01-01T12:00:00)
          }
        ```

    * `@PathVariable` is a two step process. First the variable path segment must be identified in the url path of the handler request mapping, then the segment is bound to a parameter in the handler's parameter list using `@PathVariable`

      * ```java
          public class MyController {
          @GetMapping(path="my_data/{id}") // {id} is the path variable
          public ResponseEntity getDataById(@PathVariable Integer id){...}
          }
        ```

* **How would you specify HTTP status codes to return from your controller?**
    * Use the `@ResponseStatus` annotation

* **How do you insert status codes, headers, and cookies into HTTP responses?**

  * Use `ResponseEntity` to set custom status codes and headers:

    * ```java
      return ResponseEntity.status(HttpStatus.CREATED)
                           .header("X-Custom-Header", "value")
                           .body(responseBody);
      ```

  * Add cookies using `HttpServletResponse`:

    * ```java
      Cookie cookie = new Cookie("session", "abc123");
      cookie.setHttpOnly(true);
      cookie.setMaxAge(3600);
      response.addCookie(cookie);
      ```

* **How do you handle exceptions thrown in your code from your controller? What happens if you don’t set up any exception handling?**
  * Using HTTP Status Codes

    * ```java
      @ResponseStatus(value=HttpStatus.NOT_FOUND, reason="No such Order")  // 404
      public class OrderNotFoundException extends RuntimeException {
      // ...
      }
      ```

  * Using `@ExceptionHandler`

    * ```java
      @ExceptionHandler(DataIntegrityViolationException.class)
      public void conflict() {
      // Nothing to do
      }
      ```

## Preferred Questions

* **Explain the MVC design pattern, and how it differs from modern Spring web development**

  * **MVC (Model-View-Controller)** is a design pattern that separates an application into:
    * **Model** – business logic and data representation
    * **View** – user interface or output representation
    * **Controller** – handles input and updates model/view
  * In **classic Spring MVC**:
    * Controllers return `ModelAndView` objects
    * Views are rendered via `ViewResolvers` (e.g., JSP or Thymeleaf)
    * Focus is on server-side rendering and HTML generation
  * In **modern Spring development (Spring Web)**:
    * Often uses `@RestController` to build **REST APIs**
    * Returns JSON or XML instead of HTML
    * **Frontend (React, Angular, etc.) is decoupled** and consumes the API
    * Focus shifts from MVC rendering to RESTful services and microservices architecture

* **How would you declare which HTTP requests you would like a controller to process?**
    * `@GetMapping`: mapping HTTP GET requests onto specific handler methods. Specifically, `@GetMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. GET)
    * `@PostMapping`: mapping HTTP Post requests onto specific handler methods. Specifically, `@PostMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. POST)
    * `@PutMapping`: mapping HTTP PUT requests onto specific handler methods. Specifically, `@PutMapping` is a composed annotation that acts as a shortcut for `@RequestMapping`(method = RequestMethod. PUT)

* **What is the control flow of the `DispatcherServlet`?**
    * Receives all requests as Front Controller  and provides a single entry point to the application
    * Mapping requests to correct Spring Web controller
    * Consulting ViewResolvers to find correct View
    * Forwarding request to chosen View for rendering
    * Returning the response to the client
    * Creates web-context to initialize the web-specific beans like controllers, view resolvers, and handler mapping

* **How to declare the data format your controller expects from requests or will create in responses?**
    * Using the @RequestMapping annotation, you can specify what type of data format the controller will take by using the `consumes=""` parameter.
      * `@RequestMapping(value = "/clients", method = RequestMethod.POST, consumes="application/json")`
    * Using the `@ResponseBody` annotation, you can specify what you will get in the response by using the `ContentType type` parameter **OR** using the `@RequestMapping` and set a `produces=""` parameter.
      * `public void addClient(@RequestBody ContentType type, Model model) {}`
      * `@RequestMapping(value = "/clients-with-response-body", method = RequestMethod.GET, produces="application/json")`

* **What is CORS and how do you resolve CORS errors**
  * **CORS (Cross-Origin Resource Sharing)** is a browser security feature that restricts web pages from making requests to a different origin (domain/port/protocol).
  * CORS errors occur when the frontend (e.g., `localhost:3000`) tries to access a backend (e.g., `localhost:8080`) without permission.
  * **To fix CORS errors in Spring:**
    * Use `@CrossOrigin` on controller or method:

        ```java
        @CrossOrigin(origins = "http://localhost:3000")
        @GetMapping("/api/data")
        public ResponseEntity<?> getData() { ... }
        ```

    * Or configure globally using `WebMvcConfigurer`:

        ```java
        @Configuration
        public class WebConfig implements WebMvcConfigurer {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedOrigins("http://localhost:3000")
                        .allowedMethods("GET", "POST", "PUT", "DELETE");
            }
        }
        ```

## Stretch Questions
* **How would you consume an external web service using Spring?**
    * By using the `RestTemplate` which acts as a web client to make requests to web services. RestTemplate offers 3 types of methods for exchanging data with web service:
      * *ForEntity:* Request for the native exchange format returned by the server (JSON, XML, Text)
        * `getForEntity(...)`
      * *ForObject:* Deserialize the response into a Java pojo
        * `getForObject(...)`
      * *exchange:* Generic API for making web requests
        * `exchange(...)`
    * Possible follow-up questions:
    * **What are the advantages of using RestTemplate?**
        * It simplifies the interaction of RESTful Web Services on the client-side

* **How do you implement authorization with JWT cookies in Spring?**
  * After login, generate a JWT and store it in an `HttpOnly` cookie:

    * ```java
      Cookie cookie = new Cookie("jwt", jwtToken);
      cookie.setHttpOnly(true);
      cookie.setPath("/");
      response.addCookie(cookie);
      ```

  * On each request, extract and validate the JWT from the cookie:
    * Use a filter (e.g., `OncePerRequestFilter`) to check the JWT before allowing access.
  * JWT contains claims like user roles, ID, expiration, and is signed using a secret key.

* **What is digital signing and how does HTTPS use certificates?**
  * **Digital signing** uses a private key to create a cryptographic signature ensuring the message wasn't tampered with.
  * **HTTPS** uses SSL/TLS certificates to:
    * Verify the identity of the server via a Certificate Authority (CA)
    * Establish an encrypted connection using public-key cryptography.
  * Spring Boot apps can use HTTPS by configuring a `keystore` in `application.properties`:

      ```properties
      server.port=8443
      server.ssl.key-store=classpath:keystore.p12
      server.ssl.key-store-password=secret
      server.ssl.key-store-type=PKCS12
      server.ssl.key-alias=tomcat
      ```
