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

## react router 

React Router enable client-side rendering. They couple URL segments to components, data loading and data mutations. Routes are objects passed to the router creation function. Client-side rendering preclude re-rendering and request an entire new document when we want to change page thus enhancing the UI. Few things to note:

1. Nested routes

Nested Routing is the general idea of coupling segments of the URL to component hierarchy and data. [Visualisation](https://remix.run/_docs/routing)

2. Dynamic segments

Segments of the URL can be dynamic placeholders that are parsed and provided to various apis.

3. Ranked route matching

When matching URLs to routes, React Router will rank the routes according to the number of segments, static segments, dynamic segments, splats, etc. and pick the most specific match.

4. Active links

Most web apps have persistent navigation sections at the top of the UI, the sidebar, and often multiple levels. Styling the active navigation items so the user knows where they are (isActive) or where they're going (isPending) in the app is done easily with <NavLink>.

5. Relative links

Like HTML <a href>, <Link to> and <NavLink to> can take relative paths, with enhanced behavior with nested routes. E.g., at a project folder, instead of referring to a path to a file inside the project folder by starting from the root, we can just refer in to the file name 

6. Data loading

Because URL segments usually map to your app's persistent data, React Router provides conventional data loading hooks to initiate data loading during a navigation. Combined with nested routes, all of the data for multiple layouts at a specific URL can be loaded in parallel. 

7. Redirects

While loading or changing data, it's common to [redirect](https://reactrouter.com/en/main/fetch/redirect) the user to a different route. Can be done using the redirect(path) function.

**Some useful componenets**

1. Route

Route couple URL segments to components, data loading and data mutations. Through route nesting, complex application layouts and data dependencies become simple and declarative.

Routes are objects passed to router creation function such as createBrowserRouter() 

- `path`: The path pattern to match against the URL to determine if this route matches a URL, link href, or form action.
- optional segments and dynamic segements are possible (URL pattern matching)
- `index` detemrines if the route is the [index route](https://reactrouter.com/en/main/start/concepts#index-routes). Index routes render into their parent's [Outlet](https://reactrouter.com/en/main/components/outlet) at their parent's URL (like a default child route).
- `loader` : Each route can define a "loader" function to provide data to the route element before it renders. The route loader is called before the route renders and provides data for the element through useLoaderData. [more info](https://reactrouter.com/en/main/route/loader)

2. Link

A [<Link>](https://reactrouter.com/en/main/components/link) is an element that lets the user navigate to another page by clicking or tapping on it. In react-router-dom, a <Link> renders an accessible <a> element with a real href that points to the resource it's linking to. This means that things like right-clicking a <Link> work as you'd expect. You can use <Link reloadDocument> to skip client side routing and let the browser handle the transition normally (as if it were an <a href>).

3. NavLink

[NavLink](https://reactrouter.com/en/main/components/nav-link) is a special kind of <Link> that knows whether or not it is "active" or "pending". This is useful when building a navigation menu, such as a breadcrumb or a set of tabs where you'd like to show which of them is currently selected. It also provides useful context for assistive technology like screen readers.

4. Navigate

[Navigate](https://reactrouter.com/en/main/components/navigate) is an element that changes the current location when it is rendered. It's a component wrapper around useNavigate, and accepts all the same arguments as props.

5. Routes
