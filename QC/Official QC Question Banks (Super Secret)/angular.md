# Unit: Angular

There are two units here - the standard Angular unit, and Angular with OWASP and ADK. The extra modules for the non-standard unit are in a [separate section](#angular-17)

## IMPORTANCE: CRITICAL

[Back to top](#unit-angular)

* **What are some features of the Angular framework?**
  * Keywords, concepts, or topics that should be in the response:
    * Single page application
    * Framework for web applications
    * Component based architecture
    * Routing, dependency injection, data binding, built-in services
  * Possible follow-up questions
    * When or why would you choose to use Angular instead of vanilla JS for a project?

* **What is a component? How would you create one?**
  * Keywords, concepts, or topics that should be in the response:
    * Reusable part of the application
    * Contains view, style, and logic (HTML/CSS/TS), plus a `.spec` file for testing (optionally)
    * Use `ng generate component <componentName>` which will create the above files
    * Typescript file should contain class with `@Component` decorator
  * Possible follow-up questions
    * **What else can be created with the Angular CLI?**
      * Services, modules, pipes

* **What is a service? How is it different from a component?**
  * Keywords, concepts, or topics that should be in the response:
    * Reusable business logic
    * No view (HTML)
    * Dependency injection - inject into components where needed
  * Possible follow-up questions
    * Why would you declare a function in a service instead of a component?
    * How have you used services in your application?

* **What is a directive and what are the different types? How to tell these directives apart with syntax?**
  * Keywords, concepts, or topics that should be in the response:
    * Directives affect the DOM
    * Structural directive: `*ngFor`, `*ngIf`, `*ngSwitch`
    * Attribute directive: `ngClass`, `ngStyle`
  * Possible follow-up questions
    * How is `*ngIf="false"` different from the `hidden` attribute?
    * Can `*ngIf` take advantage of truthy/falsy values?
    * Why would you use `*ngFor` in a component?
    * Why would you use `ngClass` or `ngStyle`?

* **What are the different types of data binding in Angular?**
  * Keywords, concepts, or topics that should be in the response:
    * 1 way binding:
      * Interpolation - `{{this.variableName}}`
      * Event Binding - `(click)="callAMethod()"`
      * Property Binding - `[ngClass]="this.classString"`
    * Optional 1 way binding (have same syntax as property binding and some people call them Property Binding):
      * Attribute Binding - `[src]="this.imageString"`
      * Class Binding - `[class]="this.classString"`
      * Style Binding - `[style]="this.styleString"`
    * 2 way binding:
      * Two-Way Data Binding - `[(ngModel)]="this.passwordString"`
  * Possible follow-up questions
    * Why are they called 1-way or 2-way data binding?
    * From where does the data start and where does the data go to?
    * What's a real world example for using 2 way data binding?

## IMPORTANCE: HIGH

[Back to top](#unit-angular)

* **What makes a "single page application" (SPA) different from a normal web page?**
  * Keywords, concepts, or topics that should be in the response:
    * SPAs use client side rendering, so all HTML/CSS/JS is loaded on the first visit to the page
    * Client side routing is used to make the application appear as though there are multiple pages even though there is only 1 single HTML file
    * Components are displayed or hidden depending on the route
    * Data is retrieved from server as needed via asynchronous HTTP calls and loaded into the HTML template
    * No whole page reloads needed when traversing the views within the application
  * Possible follow-up questions
    * Explain how routing relates to creating single page applications? (see above)

* **How have you used the `HttpClient`? What methods does it have and what do they return?**
  * Keywords, concepts, or topics that should be in the response:
    * Angular service for sending HTTP requests asynchronously, built on top of fetch API
    * Call any of standard HTTP methods: `.get()`, `.post()`, `.put()`, or `.delete()`
    * Provide URL and optional data for HTTP body
    * Returns an Observable that is updated with the data from the response body

* **How would you implement routing in your project?**
  * Keywords, concepts, or topics that should be in the response:
    * Typically define a separate routing module that exports an array of routes
    * Each route is defined by a string path and a component that is mapped to it
    * Use the `<router-outlet>` tag to define the boundaries of where routing works
    * Use `routerLink` attribute in the HTML to change the route string, causing routing to execute
    * You could also change the route string through the `Router` object in the TS file
  * Possible follow-up questions
    * How would you handle path parameters, for example a `/books/1` route?

* **What is the lifecycle of a component? List some lifecycle hooks**
  * Keywords, concepts, or topics that should be in the response:
    * Crucial: `ngOnInit()`, `ngOnChanges()`, `ngOnDestroy()`
    * Good to know: `ngDoCheck()`, `ngAfterContentInit()`, `ngAfterContentChecked()`, `ngAfterViewInit()`, `ngAfterViewChecked()`
  * Possible follow-up questions
    * When does `ngOnInit()` get called? Before constructors are called, before first loaded onto page, or each time loaded onto page? (Can repeat for other methods)
    * When might you want to use the `ngOnDestroy()` method?

* **How does dependency injection work in Angular?**
  * Keywords, concepts, or topics that should be in the response:
    * Use `@Injectable` annotation above service class
    * List the service in the `providers` array in the `@NgModule` decorator in the module to make it available within the module
    * Constructor injection: declare service as parameter within component constructor

## IMPORTANCE: REGULAR

[Back to top](#unit-angular)

* **How would you create a new Angular project?**
  * Keywords, concepts, or topics that should be in the response:
    * Angular CLI: `ng new <myproject>`
  * Possible follow-up questions

* **Explain the difference between server-side and client-side rendering**
  * Keywords, concepts, or topics that should be in the response:
    * Client-side rendering: initial HTML/CSS/JS assets loaded first; subsequent HTTP requests for data from backend
    * Server-side rendering: server sends back full HTML page in response to every request
  * Possible follow-up questions
    * What are the advantages of client side rendering?
      * Cons: slower initial page load, more front-end data processing
      * Pros: faster subsequent loading, graceful UI when server unavailable

* **What is a pipe? Explain this syntax: `<p>My birthday is {{ birthday | date }}</p>`**
  * Keywords, concepts, or topics that should be in the response:
    * Transforms a value to the proper format for displaying on the view
    * Can use built-in Angular pipes or create your own

* **Explain the relevance of npm to Angular projects.**
  * Keywords, concepts, or topics that should be in the response:
    * Tracks external dependencies for the project
    * Manages versions of these dependencies
    * Can install new packages via `npm install`
  * Possible follow-up questions
    * Which file does npm use to track dependencies?
      * `package.json`

* **What is a decorator? List some decorators for Angular apps.**
  * Keywords, concepts, or topics that should be in the response:
    * Decorators provide metadata for Angular
    * `@Component`, `@Injectable`, `@NgModule`, `@Pipe`

* **What is the benefit of using a directive like NgClass over the class attribute, or even property binding to the class attribute?**

* **How would you create a custom pipe?**
  * Use the `@Pipe` decorator

* **What is an Angular module? What properties should you set inside it?**
  * A module is a logical container for components, services, and pipes that relate to each other
  * Can be lazy loaded to improve performance
  * Possible follow-up questions
    * How would you lazy load a module?

* **What's the difference between a JavaScript module and Angular module? What are some common Angular modules?**

* **What is an `Observable`? What's the difference between it and a `Promise`?**
  * Part of RxJS, it is like a Promise because it is asynchronous and is a wrapper for future values
  * Unlike a Promise, it can handle multiple events and is cancellable
  * Must `.subscribe()` to an Observable to provide your callback function

* **What does Webpack do for your Angular project?**
  * Bundles all of your HTML, CSS, and JavaScript together and serves it locally

* **What is an `EventEmitter` and when would you use one?**
  * Used for component communication between nested components
  * Can define custom events to respond to when the event is emitted from a child component

* **How would you run your unit tests for an Angular project?**
  * Use `ng test` to run all the `.spec` files (Jasmine is the test library)

## Angular 17

* **What are Signals?**
  * Signals are a tool to help build applications in a reactive style. Signals have an API for reporting data changes to Angular, allowing the framework to optimize change detection and re-rendering. Angular determines exactly what parts of the page need to be updated and only updates that part.
  * Increase performance and speed
  * Signals are a lightweight wrapper or container for a value
  * Get notified when the signal value changes so you can *react* to it

* **Are signals writable or read-only?**
  * They may be either

* **What are the new declarative control flow statements with Angular 17?**
  * `@for`, `@if`, `@switch`, `@empty`

* **What is an `effect`?**
  * An operation that runs whenever one or more signal values change
  * Effects always run at least once
  * They always execute asynchronously during the change detection process

## Angular OWASP Security

* **What are common security vulnerabilities to web applications?**
  * Vulnerable and Outdated Components
  * Cross-Site Scripting (XSS)
  * Cross-Site Request Forgery (CSRF)
  * Insecure Storage

* What are some best practices to prevent the above problems?
  * Keep current with the latest Angular library releases - updates might fix security defects discovered in previous versions. Check the Angular change log for security-related updates.
  * Don't alter your copy of Angular - private, customized versions of Angular tend to fall behind the current version and might not include important security fixes and enhancements. Instead, share your Angular improvements with the community and make a pull request.
  * Avoid Angular APIs marked in the documentation as "Security Risk" - For more information, see the Trusting safe values section of this page.
  * To block XSS attacks, prevent malicious code from entering the DOM. For example, if attackers can trick you into inserting a `<script>` tag in the DOM, they can run arbitrary code on your website. Many elements and properties in the DOM allow code execution, for example, `<img alt="" onerror="...">` and `<a href="javascript:...">`. Always sanitize user input.
  * To systematically block XSS bugs, Angular treats all values as untrusted by default.
