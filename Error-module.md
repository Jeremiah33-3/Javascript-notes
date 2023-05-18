# Error Module and relevant information

**1 The Error Module**

Resource: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error

Error objects are thrown when runtime errors occur. 
The Error object can also be used as a base object for user-defined exceptions. 
Javascript has several built-in error types. 
- Can be instantiated (Error class -- Error instance)
- Handle errors by try-catch block
- asynchronous Node API uses error-first callback functions as traditional try-catch statements may not work for asynchronous operations

**2 Serializable**

Resource: https://developer.mozilla.org/en-US/docs/Glossary/Serializable_object 

Defintiion:
>  Serialization means to convert an object into that string, and deserialization is its inverse operation (convert string -> object).

Serializable objects are objects that can be serialized and later deserialized in any JavaScript environment ("realm").
Use: Able to be stored on disk and later restored, or cloned with structuredClone(), or shared between workers using DedicatedWorkerGlobalScope.postMessage().
