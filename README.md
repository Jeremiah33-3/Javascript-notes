# Javascript-notes

Trying to create a cheatsheet/note
for JavaScript so that I (and anyone reading) can easily 
reference to it.

// Some helpful websites
1. Backend programming: https://www.codecademy.com/courses/introduction-to-back-end-programming/articles/javascript-for-node-js 
2. Node.js blocking vs non-blocking: https://nodejs.org/en/docs/guides/blocking-vs-non-blocking 
3. Connecting node.js to react.js (express) : https://www.geeksforgeeks.org/how-to-connect-node-js-with-react-js/
4. Asynchronous JS; https://www.codecademy.com/courses/asynchronous-javascript/lessons/promises/exercises/introduction 
5. MDN JS: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
6. Iterators cheatsheet: https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-iterators/cheatsheet
7. Expressions and operators: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators
8. built-in objects: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects
9. Next.js: https://nextjs.org/learn/foundations/about-nextjs/what-is-nextjs
10. Node.js: https://www.geeksforgeeks.org/nodejs/
11. middleware vs route handlers: https://stackoverflow.com/questions/58925276/what-is-the-difference-between-a-route-handler-and-middleware-function-in-expres

// HTML DOM 
1. What is DOM(Document Object Model): https://developer.mozilla.org/en-US/docs/Glossary/DOM
2. HTMP DOM API docs: https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API

// Interesting articles
1. Callback hell: http://callbackhell.com/

## Coolest question mark

Javascript ❓ operator has 3 special functionalities ❗
1. Ternary Operator (boolExpr ? valueIfTrue : valueIfFalse)
2. Optional chaining (object.mayNotExistProp?.someOtherProp)
3. Nullish Coalescing ( ifUndefined ?? useThisDefault) **-> which is more functional than || operator since it recognises 0 and ''**

Source: https://www.freecodecamp.org/news/how-the-question-mark-works-in-javascript/

## All about array

> The Array object, as with arrays in other programming languages, enables storing a collection of multiple items under a single variable name, and has members for performing common array operations.

Some facts:
- Array constructor allows varags
- support for...in... loop
- .length property is fairly useful

[Shallow copy](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy) (of an object):
- is a copy whose properties share the same references (point to the same underlying values) as those of the source object from which the copy was made
- changing either the source or the copy may cause the other object to change too
- That behavior contrasts with the behavior of a deep copy, in which the source and copy are completely independent.

[Deep copy](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy):
- is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made.
- change either the source or the copy, you can be assured you're not causing the other object to change too

Methods:
- refer to source

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

## Destructuring assignment ❇️

> The destructuring assignment syntax is a JavaScript expression that makes it possible to _unpack values_ from arrays, or properties from objects, into distinct variables.

example:
`let a, b, rest;
[a, b] = [10, 20];

console.log(a);
// Expected output: 10

console.log(b);
// Expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// Expected output: Array [30, 40, 50]`

This assignment allows us to create ad hoc packages of data. When used on the left-hand side of the assignment, it defines what values to unpack from the sourced variable.

example: 
`const obj = { a: 1, b: 2 };
const { a, b } = obj;
// is equivalent to:
// const a = obj.a;
// const b = obj.b;`

For both object and array destructuring, there are two kinds of destructuring patterns: binding pattern and assignment pattern, with slightly different syntaxes.

1. Binding patterns 

In binding patterns, the pattern starts with a declaration keyword (var, let, or const). Then, each individual property must either be bound to a variable or further destructured.

All variables share the same declaration, so if you want some variables to be re-assignable but others to be read-only, you may have to destructure twice — once with let, once with const.

2. Assignment pattern

In assignment patterns, the pattern does not start with a keyword. Each destructured property is assigned to a target of assignment — which may either be declared beforehand with var or let, or is a property of another object — in general, anything that can appear on the left-hand side of an assignment expression.

**Default value** used when value is not present or is undefined 
`const { b = console.log("hey") } = { b: 2 };
// Does not log anything, because `b` is defined and there's no need
// to evaluate the default value.`

**swapping value** is also possible via the [XOR swap trick](https://en.wikipedia.org/wiki/XOR_swap_algorithm)

**unpacking object properties passed into function parameter**
Objects passed into function parameters can also be unpacked into variables, which may then be accessed within the function body. As for object assignment, the destructuring syntax allows for the new variable to have the same name or a different name than the original property, and to assign default values for the case when the original object does not define the property.

Example:
`const user = {
  id: 42,
  displayName: "jdoe",
  fullName: {
    firstName: "Jane",
    lastName: "Doe",
  },
};

function userDisplayName({ displayName: dname }) {
  return dname;
} // define the name of unpacked variable 

console.log(userDisplayName(user)); // "jdoe"

function userId({ id }) {
  return id;
}

console.log(userId(user)); // 42
`

Nested objects can also be unpacked. The example below shows the property fullname.firstName being unpacked into a variable called name.

`function whois({ displayName, fullName: { firstName: name } }) {
  return `${displayName} is ${name}`;
}

console.log(whois(user)); // "jdoe is Jane"`

Source/Reading:
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment
- block scope and destructuring: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let

## OOP

Object-oriented programming is about modeling a system as a collection of objects, where each object represents some particular aspect of the system. Can contain both functions (methods) and properties (attributes). 

Class is a template/blueprint that can help in instance creation. Object is an instance of a class. Class can have consturctors which are special functions whose parameters define the properties of an object created. 

The four main concepts of OOP: inheritance, encapsulation, composition, abstraction. (a [link to OOP notes](https://nus-cs2030s.github.io/2223-s2/00-overview.html) )

JS supports [constructors](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics) as well as object [prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes). Yet JS is distinct from the classical OOP in 2 ways:
1. JS can create objects without a separate class definition. either using a function or object literal
2. prototype chain behaviour is less like inheritance but more like delegation

You can declare a class like [this](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Classes_in_JavaScript).

Source/Readings:
- https://www.geeksforgeeks.org/introduction-object-oriented-programming-javascript/
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_programming

## Promise, async, and arrow expressions

1. Synxtax (from stackoverflow)

Async arrow functions:

`const foo = async () => {`
  `// do something`
`}`

Async arrow functions for a single argument passed to it:

`const foo = async evt => {`
  `// do something with evt`
`}`

Async arrow functions for multiple arguments passed to it:

`const foo = async (evt, callback) => {`
  `// do something with evt`
  /`/ return response with callback`
`}`

The anonymous form:

`const foo = async function() {`
  `// do something`
`}`

An async function declaration:

`async function foo() {`
  `// do something`
`}`

Using async function in a callback:

`const foo = event.onCall(async () => {`
  `// do something`
`})`

Using async method inside of a class:

`async foo() {`
  `// do something`
`}`

2. How to use Promises

 A promise is an object returned by an asynchronous function, which represents the current state of the operation, (pending, rejected, fulfilled), and the eventual completion (or failure) of an asynchronous operation and its resulting value. The promise object provides methods to handle the eventual success or failure of the operation.
![flow of Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/promises.png)

3. Arrow functions vs async

Firstly, arrow functions are not automatically async (tho there is a sense of delayedness). Arrow function is an alternative to the traditional function expr. But arrow functions have some differences with the traditional function declaration:
- Arrow functions don't have their own bindings to this, arguments, or super, and should not be used as methods.
- Arrow functions cannot be used as constructors. Calling them with new throws a TypeError. They also don't have access to the new.target keyword.
- Arrow functions cannot use yield within their body and cannot be created as generator functions.


Async functions, meanwhile, enable asynchronous execution and allows the `await` keyword to be used within itself.

Source/Readings:
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Promises#asyncawait_class_methods
- https://stackoverflow.com/questions/42964102/syntax-for-an-async-arrow-function
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function
