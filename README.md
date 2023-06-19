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
