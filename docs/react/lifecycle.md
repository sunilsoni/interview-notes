---
title: Lifecycle Methods
hide:
  - tags

tags:
- Lifecycle Methods
- React Hooks
- Custom Hooks
- Class Component vs Functional Component
- props
- state

---

#  Lifecycle Methods


---
## Lifecycle Methods



React lifecycle methods are special functions that allow you to hook into different stages of a component's life, from creation to deletion. They provide opportunities to perform actions like setting up initial state, making API calls, and cleaning up resources. Understanding these methods is crucial for managing component behavior effectively.



React class components have several lifecycle methods categorized into three main phases: Mounting, Updating, and Unmounting. Functional components also have similar lifecycle behaviors with the introduction of React Hooks.

#### Mounting Phase

1. **constructor:** The constructor is called when the component is initialized. It's used for setting up initial state and binding methods.

2. **render:** The render method returns the JSX representation of the component's UI. It's called each time the component needs to be re-rendered.

3. **componentDidMount:** This method is called after the component has been rendered to the DOM. It's often used for making initial API calls or setting up event listeners.

#### Updating Phase

4. **shouldComponentUpdate:** This method is called before re-rendering a component. You can use it to control whether the component should update based on the new props and state.

5. **render:** As mentioned earlier, the render method is called during updates as well when the component needs to re-render.

6. **componentDidUpdate:** After a component updates, this method is called. It's useful for performing actions after a re-render, like updating the DOM in response to state changes.

#### Unmounting Phase

7. **componentWillUnmount:** This method is invoked just before a component is removed from the DOM. It's used for cleanup tasks like removing event listeners or clearing timers.

### Example Usage

Let's illustrate the usage of these methods with a practical example:

```jsx
import React, {Component} from 'docs/react/index';

class LifecycleExample extends Component {
    constructor(props) {
        super(props);
        this.state = {count: 0};
    }

    componentDidMount() {
        // Called after component is added to the DOM
        console.log('Component mounted');
    }

    componentDidUpdate(prevProps, prevState) {
        // Called after component updates
        console.log('Component updated');
    }

    componentWillUnmount() {
        // Called before component is removed from the DOM
        console.log('Component unmounted');
    }

    render() {
        return (
            <div>
                <p>Count: {this.state.count}</p>
                <button onClick={() => this.setState({count: this.state.count + 1})}>
                    Increment
                </button>
            </div>
        );
    }
}

export default LifecycleExample;
```

In this example, we've used the `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` methods to demonstrate their respective lifecycle phases. These methods help manage the component's behavior throughout its life cycle.


### React Hooks and Functional Components

With the introduction of React Hooks, functional components can also mimic similar lifecycle behavior using hooks like `useEffect`. Here's how the above example would look in a functional component:

```jsx
import React, {useState, useEffect} from 'docs/react/index';

function LifecycleExample() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        // Called after component is added to the DOM
        console.log('Component mounted');

        return () => {
            // Called before component is removed from the DOM
            console.log('Component unmounted');
        };
    }, []); // Empty dependency array means this effect runs once, like componentDidMount

    useEffect(() => {
        // Called after every render (including initial render)
        console.log('Component updated');
    });

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

export default LifecycleExample;
```

In this functional component, we use the `useState` hook to manage state and the `useEffect` hook to mimic lifecycle methods. The empty dependency array `[]` in the first `useEffect` hook ensures it runs only once, similar to `componentDidMount`.

The second `useEffect` hook runs after every render, similar to `componentDidUpdate`. Cleanup can also be performed within `useEffect` by returning a function, similar to `componentWillUnmount`.



Understanding React's lifecycle methods (in both class and functional components) is essential for controlling the behavior of your components throughout their life cycles. Whether you're initializing state, fetching data, or cleaning up resources, these methods provide hooks into various stages of your component's existence, ensuring your components function as expected in different scenarios. React Hooks have made it easier to achieve similar behavior in functional components, making them a powerful tool for modern React development.

### Real-Life Scenario: Using React Lifecycle Methods

Let's dive deeper into a real-life scenario to showcase how React's lifecycle methods can be used effectively. Imagine you're building a social media application, and you want to load a user's posts when they visit their profile page. You can use lifecycle methods to handle data fetching and UI updates:

```jsx
import React, {Component} from 'docs/react/index';

class UserProfile extends Component {
    constructor(props) {
        super(props);
        this.state = {
            userId: props.userId,
            userPosts: [],
            isLoading: true,
        };
    }

    componentDidMount() {
        // Simulate an API call to fetch user posts
        fetch(`/api/users/${this.state.userId}/posts`)
            .then((response) => response.json())
            .then((data) => {
                this.setState({
                    userPosts: data,
                    isLoading: false,
                });
            });
    }

    render() {
        const {userPosts, isLoading} = this.state;

        return (
            <div>
                {isLoading ? (
                    <p>Loading user posts...</p>
                ) : (
                    <div>
                        <h2>User Posts</h2>
                        <ul>
                            {userPosts.map((post) => (
                                <li key={post.id}>{post.title}</li>
                            ))}
                        </ul>
                    </div>
                )}
            </div>
        );
    }
}

export default UserProfile;
```

In this example:

1. In the constructor, we initialize the component's state with an initial `userId`, an empty array for `userPosts`, and a loading indicator (`isLoading`).

2. In `componentDidMount`, we simulate an API call to fetch the user's posts data. When the data is retrieved, we update the state with the fetched posts and set `isLoading` to `false`. This will trigger a re-render of the component with the user's posts displayed.

3. In the `render` method, we conditionally render content based on the `isLoading` flag. If data is still loading, we display a loading message; otherwise, we render the user's posts.

By utilizing lifecycle methods like `componentDidMount`, we ensure that the data fetching happens after the component is mounted, preventing unnecessary API requests during the initial rendering phase. This pattern ensures a smoother user experience and is a common use case for handling asynchronous operations in React applications.

By incorporating React's lifecycle methods into your components, you can effectively manage data fetching, UI updates, and resource cleanup, making your applications more robust and responsive.


---

## Class Component vs Functional Component

In React, there are two primary ways to create components: class components and functional components. Class components are created using ES6 classes and have a richer set of features, while functional components are simpler and use JavaScript functions. Here's a brief comparison:

- **Class Component**: Created with a class and extends `React.Component`. Used for complex state management, lifecycle methods, and class-based features.
- **Functional Component**: Created as a plain JavaScript function. Ideal for simple UI components and stateless rendering.

Now, let's dive deeper into the details.

### Class Component

Class components in React are defined as JavaScript classes that extend `React.Component`. They have been the traditional way of creating components in React and offer a wide range of features:

1. **State Management**: Class components have built-in state management using `this.state` and `this.setState()`. This allows you to store and update component-specific data.

2. **Lifecycle Methods**: Class components have lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`. These methods allow you to control component behavior at various stages of its lifecycle.

3. **Complex Logic**: They are suitable for components with complex logic, such as forms, interactive components, or components that require access to lifecycle events.

Here's an example of a class component:

```jsx
import React, {Component} from 'docs/react/index';

class ClassComponent extends Component {
    constructor(props) {
        super(props);
        this.state = {count: 0};
    }

    render() {
        return (
            <div>
                <p>Count: {this.state.count}</p>
                <button onClick={() => this.setState({count: this.state.count + 1})}>
                    Increment
                </button>
            </div>
        );
    }
}

export default ClassComponent;
```

### Functional Component

Functional components are simpler and more lightweight. They are just JavaScript functions that return JSX. Key points:

1. **No State**: Functional components do not have built-in state. They receive data through props and are primarily used for rendering UI based on those props.

2. **Hooks**: To manage state and side-effects in functional components, React introduced Hooks like `useState`, `useEffect`, and `useContext`. These hooks enable you to add state and lifecycle-like behavior to functional components.

3. **Reusability**: Functional components are highly reusable and can be composed easily into larger components.

Here's an example of a functional component using hooks:

```jsx
import React, {useState} from 'docs/react/index';

function FunctionalComponent() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

export default FunctionalComponent;
```

### Choosing Between Class and Functional Components

- Use class components when you need advanced features like state management and lifecycle methods.
- Prefer functional components for simple UI rendering or when hooks can fulfill your state and logic requirements.
- As of React 16.8, functional components with hooks are the recommended way of building components in React due to their simplicity and flexibility.



---

## React Hooks

Hooks are a feature in React, a popular JavaScript library for building user interfaces. They allow developers to add state and lifecycle features to functional components, which were previously only available in class components. Hooks provide a cleaner and more concise way to manage component logic, making it easier for developers to write and maintain React applications.



React Hooks were introduced in React version 16.8 and have since become a fundamental part of React development. They come in various flavors, but the most commonly used ones are `useState`, `useEffect`, `useContext`, and `useRef`.

### useState
`useState` is used to manage state within a functional component. It lets you declare a state variable and provides a way to update it. Here's an example:

```javascript
import React, {useState} from 'docs/react/index';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```

### useEffect
`useEffect` allows you to perform side effects in your components, such as data fetching, DOM manipulation, or setting up subscriptions. It runs after the component renders. Example:

```javascript
import React, {useState, useEffect} from 'docs/react/index';

function ExampleComponent() {
    const [data, setData] = useState([]);

    useEffect(() => {
        // Fetch data from an API
        fetch('https://api.example.com/data')
            .then((response) => response.json())
            .then((result) => setData(result));
    }, []); // Empty dependency array means it runs once on mount

    return (
        <div>
            {data.map((item) => (
                <p key={item.id}>{item.name}</p>
            ))}
        </div>
    );
}
```

### useContext
`useContext` is used to access a React context within a functional component. It allows you to share data between components without the need for prop drilling. Example:

```javascript
import React, {useContext} from 'docs/react/index';

const ThemeContext = React.createContext('light');

function ThemedButton() {
    const theme = useContext(ThemeContext);

    return <button style={{background: theme}}>Themed Button</button>;
}
```

### useRef
`useRef` provides a way to create mutable references to elements or values that persist across renders. It's often used to interact with the DOM or manage previous values. Example:

```javascript
import React, {useRef, useEffect} from 'docs/react/index';

function FocusInput() {
    const inputRef = useRef();

    useEffect(() => {
        inputRef.current.focus();
    }, []);

    return <input ref={inputRef}/>;
}
```

 
React Hooks have revolutionized the way developers work with React components. They offer a more straightforward and functional approach to managing state and side effects, making code cleaner and more maintainable. By understanding and using hooks effectively, developers can create more efficient and readable React applications.


## Custom Hooks
Apart from the built-in hooks mentioned earlier, developers can create their custom hooks. Custom hooks are reusable pieces of logic that can be shared across different components. Let's create a custom hook to illustrate this concept.

```javascript
import {useState, useEffect} from 'docs/react/index';

function useFetchData(url) {
    const [data, setData] = useState([]);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        fetch(url)
            .then((response) => response.json())
            .then((result) => {
                setData(result);
                setLoading(false);
            });
    }, [url]);

    return {data, loading};
}
```

Now, you can use `useFetchData` in multiple components to fetch data from various URLs without duplicating the fetch logic.

```javascript
import React from 'docs/react/index';
import useFetchData from './useFetchData';

function MyComponent() {
    const {data, loading} = useFetchData('https://api.example.com/data');

    if (loading) {
        return <p>Loading...</p>;
    }

    return (
        <div>
            {data.map((item) => (
                <p key={item.id}>{item.name}</p>
            ))}
        </div>
    );
}
```

## Rules of Hooks
While using hooks, it's essential to follow the Rules of Hooks:

1. Only call hooks at the top level of a function component or a custom hook.
2. Only call hooks from React functions (not regular JavaScript functions).
3. Ensure that hooks are called in the same order on every render.

Adhering to these rules ensures that your components behave predictably and that hooks work as expected.

## Benefits of Hooks
1. Improved code organization: Hooks allow you to organize your code based on the logic it represents, rather than by lifecycle methods.
2. Reusability: Custom hooks make it easy to share logic between components.
3. Cleaner code: Hooks often lead to shorter and more readable component code.
4. Easier testing: Since hooks are just functions, they are easier to test compared to class components.

In conclusion, React Hooks are a powerful addition to React that simplify component logic and make it more maintainable. By understanding and mastering the different hooks available, you can become a more effective React developer and create better user interfaces.



---


## props and state 



React is a popular JavaScript library for building user interfaces, and understanding the concepts of props and state is fundamental to working with React components effectively. In this guide, we will delve into what props and state are, how they differ, and how to use them in your React applications.

### Props (Properties)

Props, short for properties, are a way to pass data from parent components to child components in React. They are read-only and allow you to configure and customize child components. Props are essential for making components reusable and dynamic.

Here's how you define and use props in React:

1. **Defining Props in Parent Component:** In the parent component, you specify props as attributes when rendering a child component.

```jsx
   // ParentComponent.js
   import ChildComponent from './ChildComponent';

   function ParentComponent() {
     const greeting = "Hello, React!";
     
     return (
       <div>
         <ChildComponent message={greeting} />
       </div>
     );
   }
```

2. **Accessing Props in Child Component:** In the child component, you can access props using the `props` object.

```jsx
   // ChildComponent.js
   function ChildComponent(props) {
     return <p>{props.message}</p>;
   }
```

   In this example, the `message` prop is passed from the parent to the child component.

### State

State is used to manage data that can change over time within a component. Unlike props, which are read-only and passed from parent to child, state is managed internally by a component. When the state of a component changes, React will re-render the component to reflect those changes in the UI.

Here's how you define and use state in React:

1. **Initializing State in a Component:** You can initialize state in a class component using the `constructor` method or in a functional component using the `useState` hook.

```jsx
   // Class Component
   class MyComponent extends React.Component {
     constructor(props) {
       super(props);
       this.state = {
         count: 0,
       };
     }

     render() {
       return <p>Count: {this.state.count}</p>;
     }
   }
```

```jsx
   // Functional Component
   import React, { useState } from 'react';

   function MyComponent() {
     const [count, setCount] = useState(0);

     return (
       <div>
         <p>Count: {count}</p>
       </div>
     );
   }
```

2. **Updating State:** To update the state, you use the `setState` method in class components or the updater function returned by `useState` in functional components.

```jsx
   // Class Component
   this.setState({ count: this.state.count + 1 });

   // Functional Component
   setCount(count + 1);
```

   State updates trigger a re-render of the component with the new state values.

### Key Differences

- Props are passed from parent to child, while state is managed within a component.
- Props are read-only and cannot be modified by the child component, whereas state can be updated by the component itself.
- Changes in props trigger a re-render of the child component, and changes in state trigger a re-render of the component itself.

Understanding and effectively using props and state is crucial for building dynamic and interactive React applications. They enable you to create reusable and responsive components that make your UIs come to life.


### Key Considerations

When working with props and state in React, there are some key considerations to keep in mind:

1. **Props Are Immutable:** As mentioned earlier, props should be treated as immutable. Child components should not modify their props directly. If a change in props is needed, it should be handled by the parent component, and the new value should be passed down.

2. **State Updates Are Asynchronous:** State updates in React are batched and asynchronous. This means that calling `setState` (in class components) or using the state updater function (in functional components) doesn't immediately update the state. React may batch multiple updates together for performance reasons. To work with the latest state, you can use the `setState` callback or the functional form of `setState`.

```jsx
   // Class Component
   this.setState(
     { count: this.state.count + 1 },
     () => {
       // This callback is called after the state has been updated
       console.log("Updated count:", this.state.count);
     }
   );
```

3. **Props Validation:** It's a good practice to validate the props your component receives to ensure they meet the expected criteria. You can use PropTypes or TypeScript for type checking to catch potential issues early.

```jsx
   import PropTypes from 'prop-types';

   function ChildComponent(props) {
     return <p>{props.message}</p>;
   }

   ChildComponent.propTypes = {
     message: PropTypes.string.isRequired,
   };
```

4. **State Management Libraries:** As your React application grows in complexity, you might consider using state management libraries like Redux or Mobx to manage the state of your application in a more organized and centralized manner.

5. **Functional Components and Hooks:** With the introduction of React hooks, you can manage state and side effects in functional components using hooks like `useState`, `useEffect`, and `useContext`. Hooks provide a more concise and readable way to handle state in functional components.




---

---

---

---

 