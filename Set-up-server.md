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
