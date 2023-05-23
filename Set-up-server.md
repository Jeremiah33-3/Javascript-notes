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

Some useful functions in http module:
- http.createServer(callback)


**[URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL)**
> Uniform Resource Locator: the mechanism used by browsers to retrieve any published resource on the web.

Which mainly is made up of Protocol, Domain, Path, Query 
