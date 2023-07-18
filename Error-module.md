# Error Module and relevant information

**1 The Error Module**

Resource: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error

Error objects are thrown when runtime errors occur. 
The Error object can also be used as a base object for user-defined exceptions. 
Javascript has several built-in error types. 
- Can be instantiated (Error class -- Error instance)
- Handle errors by try-catch block
- asynchronous Node API uses error-first callback functions as traditional try-catch statements may not work for asynchronous operations
- Error objects are serializable

**2 Serializable**

Resource: https://developer.mozilla.org/en-US/docs/Glossary/Serializable_object 

Defintiion:
>  Serialization means to convert an object into that string, and deserialization is its inverse operation (convert string -> object).

Serializable objects are objects that can be serialized and later deserialized in any JavaScript environment ("realm").
Use: Able to be stored on disk and later restored, or cloned with structuredClone(), or shared between workers using DedicatedWorkerGlobalScope.postMessage(). All primitive types are serialisable, but not all objects are serialisable. The structured clond algorithm has a list of serialisable objects: https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm#supported_types.

**3 Transferable objects**

Resource: https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Transferable_objects

Definition:
> Transferable objects are objects that own resources that can be transferred from one context to another, ensuring that the resources are only available in one context at a time. Following a transfer, the original object is no longer usable; it no longer points to the transferred resource, and any attempt to read or write the object will throw an exception.

**4 Control flow and Error handling** 

Resource: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling 

Quite a germane topic w.r.t. Error class.
- Can throw exceptions using `throw` keyword
- handle exceptions using the try..catch statements + finally
- good way extend Error in JS: https://stackoverflow.com/questions/1382107/whats-a-good-way-to-extend-error-in-javascript

Difference between error and exception:
- https://stackoverflow.com/questions/16142583/whats-the-difference-between-error-and-exception-in-javascript 
- no massive difference in js, virtually the same except some nuances here and there by convention 

**5 Additional stuffs**

- Error.property.stack: https://www.geeksforgeeks.org/javascript-error-prototype-stack-property/
- Error handling in promises: https://lucymarmitchell.medium.com/using-then-catch-finally-to-handle-errors-in-javascript-promises-6de92bce3afc
