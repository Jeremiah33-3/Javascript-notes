# Timer module for Node.js

Some facts:
- global module (need no import)
- timer functions added to Node.js [Event Loop]([url](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick))
  - means that timer functions are scheduled and put in a queue
  - queue is processed at every iteration of the event loop
  - if a timer function is executed outside of a module, the behavior will be random (non-deterministic)

In Javascript [setTimeout()]([url](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout)):
- global function 
- asynchronous function 
- sets a timer which executes a function or specified piece of code once the timer expires.
- return a positive integer value which identifies the timer created by the call to setTimeout(). This value can be passed to clearTimeout() to cancel the timeout.
- setinterval() repeatedly calls a function
