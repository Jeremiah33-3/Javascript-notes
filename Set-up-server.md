# About HTTP requests and how to set up server

Helpful resource: 
- setting up a server with http:https://www.codecademy.com/courses/learn-nodejs-setting-up-a-server/lessons/setting-up-a-server-with-http/exercises/the-movement-of-http
- cheatsheet: https://www.codecademy.com/learn/learn-nodejs-setting-up-a-server/modules/nodejs-setting-up-a-server/cheatsheet

What is [HTTP?](https://developer.mozilla.org/en-US/docs/Web/HTTP)
> Hypertext Transfer Protocol (HTTP) is an application-layer protocol for transmitting hypermedia documents, such as HTML.

The movement of HTTP by different transport protocols
- Transmission Control Protocol TCP
- User Datagram Protocol UDP (less commonly used)
- Transport Layer Security TLS

There are also different versions of HTTP
- HTTP/1.1
- HTTP/2
- HTTP/3

**The HTTP module is built-in in JS and Node.js**
HTTP methods:
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

HTTP Response status code
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- indicate whether a specific HTTP request has been successfully completed

Some useful functions in http module:
- http.createServer(callback)


**[URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL)**
> Uniform Resource Locator: the mechanism used by browsers to retrieve any published resource on the web.

Which mainly is made up of Protocol, Domain, Path, Query 

Node.js [URL module](https://nodejs.org/api/url.html):
- built-in 
- helps to parse the individual components of URL easier
- We can handle query strings using the [querystring module](https://nodejs.org/api/querystring.html#querystring_querystring_decode) as well, but need some prepocessing of the url. 


**Routing**
> The process of handling requests in specific ways based on the information provided within the request is known as routing.

- internally, server needs to maintain a way to handle each request based on the specific criteria like method, pathname
- this is how server process and respond request 
- so we have routing to help

Method:
- each HTTP request contains a method such as `GET` and `POST`
- method is an important piece of info to route request 
- is an action the server is required to carry out
- the different requests will then be routed to different functions for handling 

Pathname:
- to distinguish requests with the same methods from one another
- allow server to understand what resource is targeted by the request 

## connect to Database

 In real-world applications, servers are responsible for helping to persist and retrieve data, usually through interaction with a database.
 
 Databases are remote resources to which the server must make a request.
 - server function as client when requesting data from DB, send HTTP message
 -  Databases usually have their own Software Development Kits (SDKs) and Object-Relational Mapping (ORMs) that can be used to connect to them easily
 -  requests could potentially be made in a raw form directly from your server using something like the HTTP .request() method
 -  [Illustrative diagram](https://static-assets.codecademy.com/Courses/Learn-Node/http/data-web-flow.png?_gl=1*1qgtg6o*_ga*Mjk1NTQ5MDY5Mi4xNjg0MTUwMjE3*_ga_3LRZM6TM9L*MTY4NDg0MjY0MS4zLjEuMTY4NDg0NDE3MS41MS4wLjA.)

## interacting with another backend API

- servers need to make requests to external APIs to accomplish some goal (e.g. payment processsing, integration with other products...)
- can be done using http.request method in http module 
- there is a .get() method too in http which automatically sets the method to GET and calls req.end() automatically.
- this fact opens up possibilities for different architecture designs for back-ends, e.g. [microservices](https://en.wikipedia.org/wiki/Microservices)


## REST API

> REpresentational State Transfer is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other.

Sources/Reading:
- How to use REST API: https://www.freecodecamp.org/news/how-to-use-rest-api/
- Introduction to REST API: https://www.geeksforgeeks.org/rest-api-introduction/

**Properties**
- stateless

Meaning that server does not need to know the state of the client is in and vice versa. Both understand the message received without seeing previous message. Constraint enforced thorugh use of resources, the nouns of the Web that describe an object, document.., rather than commands.

- separate the concerns of client and server

Meaning that code on the client side can be changed without affecting the opration of the server and vice versa. Implementation can be done without them knowing each other, independently. Just need to know format of message, then each side can be kept modular and separate. We can improve flexibility of th einterface across platforms and improve scalability by simplifying the server components. 

** REST Architecture [link](https://www.codecademy.com/courses/learn-nodejs-setting-up-a-server/articles/what-is-rest)**

- clients send requests to retrieve or modify resources
- servers send responses to these requests

A request consists of:
1. HTTP verb/method -> defines the kind of opeation to perform 
2. a header -> allows client to pass along info about the request
3. a path to resource
4. an optional msg body containing the data 

HTTP headers:
- `Accept` field: type of content able to receive (prevent receiving un-understandable data) e.g. [MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types)
   - MIME types consts of a type and subtype
   - e.g. test/html, application/xhtml

Paths
- should be designed to help clients know what is going on
- Conventionally, the first part of the path should be the plural form of the resource. This keeps nested paths simple to read and easy to understand.
- need id to identity but no need when creating a new resource 


**Sending response**

- server sending -> must include a content type in the header, which is in MIME type
- responses contain status codes to alert the client to information about the success of the operation.

## Connecting frontend and backend

1. Rendering 

Rendering is the aspect of web development concerned with translating code into a visual and interactive website. 

- browser build a render tree using html and css
- different ways of rendering a web app
- client side rendering: the content of the page is dynamically generated in the browser as the user navigates the app
- server-side rendering: the server generates the content and sends it to the browser, on-demand
- hybrid-rendering: static content is generated on the server, while dynamic content is generated on the client-side as the user navigates the site.


2. [MVC Architecture](https://developer.mozilla.org/en-US/docs/Glossary/MVC)

- Model–view–controller (MVC) is a software design pattern commonly used for developing user interfaces that divides the related program logic into three interconnected elements.
- popular for web dev

## Fetching data from servers 

1. CORS

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS 
- Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.
- enabled Fetch API 
- works by adding new [HTTP header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) (additional information with an HTTP request for response)
- servers can inform clients whether 'credentials' like [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies) or [HTTP Authetication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication) should be sent with the requests
- some requests trigger [CORS Preflight](https://developer.mozilla.org/en-US/docs/Glossary/Preflight_request)

Example of a simple request: 
`const xhr = new XMLHttpRequest();
const url = "https://bar.other/resources/public-data/";

xhr.open("GET", url);
xhr.onreadystatechange = someHandler;
xhr.send();

2. Fetch API

- an interface for fetching resources across networks
- method: fetch(resource, option)  -> a global method in both `Window` and `Worker`
- make use of `Request` and `Response` objects 
- a `Headers` object for representing response/request headers, allowing developers to query them and take different actions
- Response object returns a `Promise` which the body content can be resolved to 
  - ArrayBuffer
  - Blob
  - Response (clone)
  - FormData
  - JSON
  - text

tutorials:
- https://www.youtube.com/watch?v=drK6mdA9d_M
  
`
