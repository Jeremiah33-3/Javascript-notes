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
