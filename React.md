# Some interesting functionalities about React

1. Create Custom Hook

Source: https://react.dev/learn/reusing-logic-with-custom-hooks

2. State sharing between components

Source: https://react.dev/learn/sharing-state-between-components

Common react technique 1 -- lifting state up
- want the state of two components to always change together
- solution: remove state from both of them, move it to their closest common parent, and then pass it down to them via props

3. Passing props to a component

Source: https://react.dev/learn/passing-props-to-a-component

Some information about props:
- used by react to allow components to communicate with one another
- can be passed from parent component to child component
- props resemble HTML attributes (e.g. className, class)
- props allowed to be passed into each tag is predefined, which conforms to the [HTML specification](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)
- can pass props to your _own_ components 
- can pass object to props
- props are like arguments to functions, they adjust the output 
- declare props (a form of object) by using the {...}; and props objects can be destructured 
- spread syntax usable but refrain from using it all the time 
- a component may receive different props over time but props itself are immmutable, so need to set state if we want to change it 

3. React context

> React Context is a method to pass props from parent to child component(s), by storing the props in a store. and using these props from the store by child component(s) without actually passing them manually at each level of the component tree.

Source/Readings:
- https://www.geeksforgeeks.org/context-in-react/
- https://react.dev/reference/react/useContext
- https://react.dev/learn/passing-data-deeply-with-context
- https://www.freecodecamp.org/news/react-context-for-beginners/

4. React Effect and useEffect

Effects let you run some code after rendering so that you can synchronize your component with some system outside of React, so that you can synchronise some componenets with external systems.

Code that may cause side effects to DOM during render can also consider useEffect

3 factors to consider: declaring an effect, setting dependencies(when to re-render effect), and cleanup function if needed. 
 
Source/Reading: 
- https://react.dev/reference/react/useEffect
- https://react.dev/learn/synchronizing-with-effects

5. createRoot

Call createRoot to create a React root for displaying content inside a browser DOM element.
React will create a root for the domNode, and take over managing the DOM inside it. After you’ve created a root, you need to call root.render to display a React component inside of it.
An app fully built with React will usually only have one createRoot call for its root component. A page that uses “sprinkles” of React for parts of the page may have as many separate roots as needed.

Can call render more than once on the same root. As long as the component tree structure matches up with what was previously rendered, React will [preserve the state](https://react.dev/learn/preserving-and-resetting-state). 

**root.render()**
parameter: A React node that you want to display. This will usually be a piece of JSX like <App />, but you can also pass a React element constructed with createElement(), a string, a number, null, or undefined
returns: undefined 

**root.unmount()**
Call root.unmount to destroy a rendered tree inside a React root.
An app fully built with React will usually not have any calls to root.unmount. Used mostly if your React root’s DOM node (or any of its ancestors) may get removed from the DOM by some other code.

Source/Readings:
- https://react.dev/reference/react-dom/client/createRoot
