---
title: React
hide:
   - tags

tags:
- React
- React Version History


---

#  React


---

##  React

React is a popular JavaScript library primarily used for building user interfaces. It was developed by Facebook and is widely adopted in the web development community. In this article, we'll delve into the main features of React, making it easy for students, developers, and others to grasp its essence.


React offers several powerful features that make it a preferred choice for developing dynamic and interactive web applications:

#### React Version History


Below is a table that outlines the React version history, including the release dates, version numbers, and notable changes. This table aims to provide a concise overview of the development and evolution of React over time. The latest version details are included based on the information available up to April 2023.

| Version Number | Release Date | Notable Changes |
| -------------- | ------------ | --------------- |
| 18.0           | March 2022   | - Introduced Concurrent React, allowing for improved performance through features like startTransition. <br> - New Suspense features and automatic batching of updates. |
| 17.0           | October 2020 | - No new features for developers, but made it easier to upgrade React itself. <br> - Event delegation changes and gradual updates adoption. |
| 16.8           | February 2019| - Introduction of Hooks, enabling state and other React features without writing a class. |
| 16.3           | March 2018   | - New context API for more efficient prop sharing. <br> - Lifecycle changes (getDerivedStateFromProps, getSnapshotBeforeUpdate). |
| 16.0           | September 2017| - Fiber rewrite for better performance and compatibility. <br> - Error boundaries for better error handling. |
| 15.0           | April 2016   | - Introduction of stateless functional components. <br> - Support for SVG attributes and other HTML5 attributes. |
| 0.14           | October 2015 | - Splitting of React and ReactDOM, separating concerns between the web and the core logic. |
| 0.13           | March 2015   | - Introduction of ES6 classes for React components. |
| 0.12           | October 2014 | - JSX syntax changes, making it more consistent. |
| 0.11           | July 2014    | - Various improvements and bug fixes. |
| 0.10           | March 2014   | - Introduction of React DevTools for debugging. |
| 0.9            | February 2013| - Improved synthetic event system. |
| 0.4            | May 2013     | - Initial public release. |





#### 1. Component-Based Architecture

React is centered around a component-based architecture, where the user interface is divided into reusable and self-contained components. This modular approach simplifies development, encourages code reusability, and facilitates collaboration among developers.

#### 2. Virtual DOM (Document Object Model)

One of React's standout features is the Virtual DOM. Instead of directly manipulating the browser's DOM, React creates a virtual representation of it in memory. When changes occur in the application's state, React calculates the most efficient way to update the virtual DOM, minimizing actual DOM manipulations. This leads to improved performance and a smoother user experience.

#### 3. Declarative Syntax

React uses a declarative syntax, which means developers specify what the UI should look like based on the application's state, rather than writing imperative code to update the UI. This makes the code more intuitive, easier to understand, and less error-prone.

#### 4. Component Lifecycle

React components have a well-defined lifecycle with methods that allow developers to control behavior at different stages, such as component creation, updates, and unmounting. This fine-grained control is valuable for managing side effects, data fetching, and optimizing performance.

#### 5. JSX (JavaScript XML)

React introduces JSX, a syntax extension that allows developers to write HTML-like code within JavaScript. This combination simplifies the creation of UI components by providing a more natural and expressive way to define the structure and appearance of the interface.

#### 6. Unidirectional Data Flow

React follows a unidirectional data flow, where data flows in a single direction, typically from parent to child components. This clear data flow pattern enhances predictability and simplifies debugging, making it easier to maintain complex applications.

#### 7. React Native

React's versatility extends beyond web development. React Native is a framework built on top of React that enables the development of mobile applications for both iOS and Android using the same codebase. This allows developers to leverage their React skills to build native mobile apps.

#### 8. Large and Active Community

React boasts a large and vibrant community of developers and libraries. This means that developers have access to a wealth of resources, third-party packages, and support, making it easier to solve problems and stay up-to-date with best practices.

In conclusion, React's component-based architecture, Virtual DOM, declarative syntax, and other features make it a powerful tool for building efficient and maintainable user interfaces. Whether you're a student learning web development or an experienced developer, React is a valuable skill to acquire for modern web application development.

### 9. One-Way Data Binding

React enforces a one-way data binding mechanism, ensuring that data flows in a predictable manner. This prevents unexpected side effects and helps maintain a clear data flow, especially in complex applications.

### 10. React Ecosystem

React is not just a standalone library; it has a rich ecosystem of tools and libraries that complement its capabilities. Tools like Redux for state management, React Router for routing, and Axios for data fetching seamlessly integrate with React, enhancing its functionality and extending its capabilities.

### 11. Developer Tools

React provides robust developer tools, such as React DevTools and React Profiler, which assist developers in debugging and profiling their applications. These tools make it easier to identify performance bottlenecks, inspect component hierarchies, and trace data flow.

### 12. Community and Resources

React has a thriving online community where developers can seek help, share knowledge, and collaborate on projects. Countless tutorials, documentation, and online courses are available to help individuals learn React effectively, making it accessible to a wide range of skill levels.

### 13. Integration with Other Technologies

React can be seamlessly integrated with other technologies and frameworks, such as GraphQL for efficient data querying, and server-side rendering for improved SEO and initial page load times. This flexibility allows developers to build versatile and high-performance applications.

### 14. Performance Optimization

React's Virtual DOM and efficient rendering mechanism contribute to exceptional performance. With the ability to update only the parts of the UI that have changed, React minimizes unnecessary re-rendering and optimizes the application's speed and responsiveness.

### 15. Testing and Debugging

React encourages the use of testing frameworks like Jest and Enzyme, which facilitate unit testing and component testing. This built-in support for testing makes it easier to identify and fix issues, ensuring that your application remains robust and bug-free.

### 16. Server-Side Rendering (SSR)

React supports server-side rendering, allowing you to render your components on the server and send a fully rendered HTML page to the client. SSR improves SEO, initial page load times, and the user experience, particularly for content-heavy websites.

### 17. Accessibility (a11y) Support

React emphasizes accessibility, making it easier to create web applications that are usable by people with disabilities. A wide range of accessibility-friendly libraries and tools are available to assist developers in ensuring their applications are inclusive and compliant with accessibility standards.

### 18. Code Reusability

With React's component-based architecture and the ability to create custom components, you can achieve high levels of code reusability. Reusing components across different parts of your application or even in entirely different projects can significantly reduce development time and maintenance efforts.

### 19. Strong Developer Tooling

React benefits from a robust set of developer tools that enable you to inspect component hierarchies, track component state, and monitor performance. These tools are invaluable for debugging and optimizing React applications during development and beyond.

### 20. Progressive Web App (PWA) Support

React can be used to build Progressive Web Apps (PWAs), which are web applications that offer a native app-like experience, including offline capabilities, push notifications, and smooth performance. This extends the reach of your web applications to various platforms and devices.

In conclusion, React's expansive feature set, coupled with its focus on performance, testing, accessibility, and code reusability, positions it as a top choice for developing modern web and mobile applications. Whether you're a student, a developer looking to enhance your skills, or someone interested in creating user-friendly and efficient applications, React provides the tools and resources to help you succeed in your endeavors.



---

## Virtual DOM
 
The Virtual DOM is a lightweight, in-memory representation of the real DOM. In a React application, instead of directly manipulating the actual DOM elements when changes occur, React creates and uses a Virtual DOM to keep track of the desired UI state. This Virtual DOM is a tree-like structure of JavaScript objects that mirrors the structure of the actual UI.

### How does it work?
When you make changes to your React component's state or props, React doesn't immediately update the real DOM. Instead, it goes through a process known as reconciliation, which involves comparing the current Virtual DOM with the previous one.

1. **Rendering the Virtual DOM:** When you initially render a React component, it creates a Virtual DOM representation of your UI.

2. **Updating the Virtual DOM:** When changes occur, React constructs a new Virtual DOM tree to represent the updated state.

3. **Reconciliation:** React efficiently compares the new Virtual DOM with the previous one. It identifies the differences (called "diffing") between the two trees.

4. **Re-rendering:** Only the specific parts of the Virtual DOM that have changed are updated in the actual DOM. This selective update process minimizes the need for costly and time-consuming direct DOM manipulation.

### Advantages
The Virtual DOM provides several advantages:

#### 1. Performance Optimization:
By reducing the number of actual DOM updates, React significantly improves the performance of web applications. Since modifying the real DOM is a slow operation, the Virtual DOM's ability to batch changes and update only what's necessary results in faster rendering.

#### 2. Cross-Platform Compatibility:
React's Virtual DOM abstraction makes it easier to support multiple platforms and environments. Whether your app runs in a web browser, on mobile devices, or even on the server (using Node.js), the Virtual DOM ensures a consistent development model.

#### 3. Developer-Friendly:
React's use of the Virtual DOM simplifies the development process. Developers can focus on describing how the UI should look in different states, and React takes care of efficiently updating the DOM.


Let's see a simple example of how the Virtual DOM works in React:

```jsx
import React, {useState} from 'docs/react/index';

function Counter() {
    const [count, setCount] = useState(0);

    const handleClick = () => {
        setCount(count + 1);
    };

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={handleClick}>Increment</button>
        </div>
    );
}

export default Counter;
```

In this example, when the button is clicked, React updates the Virtual DOM and then only modifies the part of the actual DOM displaying the count value, resulting in a smooth and efficient user experience.




### Virtual DOM Reconciliation Process
To provide a more detailed understanding, let's dive deeper into the Virtual DOM reconciliation process with an example:

Suppose you have a list of items in your React component, and you want to update one item's text when a button is clicked:

```jsx
import React, {useState} from 'docs/react/index';

function ItemList() {
    const [items, setItems] = useState([
        {id: 1, text: 'Item 1'},
        {id: 2, text: 'Item 2'},
        {id: 3, text: 'Item 3'},
    ]);

    const handleUpdate = () => {
        const updatedItems = [...items];
        updatedItems[1].text = 'Updated Item 2';
        setItems(updatedItems);
    };

    return (
        <div>
            <ul>
                {items.map((item) => (
                    <li key={item.id}>{item.text}</li>
                ))}
            </ul>
            <button onClick={handleUpdate}>Update Item 2</button>
        </div>
    );
}

export default ItemList;
```

When you click the "Update Item 2" button, React performs the following steps:

1. It updates the Virtual DOM with the new state of the `items` array.

2. It compares the new Virtual DOM with the previous one, identifying that only one `<li>` element text has changed.

3. Instead of re-rendering the entire list, React intelligently updates only the specific `<li>` element whose text has changed in the real DOM.

This process minimizes unnecessary DOM manipulations and results in faster and more efficient updates.

### React Reconciliation Strategies
React uses several strategies during reconciliation to optimize updates further:

#### 1. Key Prop:
In the example above, you may have noticed the `key` prop in the `<li>` elements. Keys help React identify which items have changed, moved, or been added or removed in lists. Providing unique keys to each element helps React efficiently update the Virtual DOM.

#### 2. Batched Updates:
React batches multiple state updates and Virtual DOM comparisons into a single pass, reducing the number of times the reconciliation process occurs. This batched approach enhances performance.

#### 3. Component Lifecycle Methods:
React provides lifecycle methods like `shouldComponentUpdate` and `PureComponent` that allow you to control when a component should or should not update, preventing unnecessary rendering.

 
The Virtual DOM is a powerful concept in React, optimizing the way user interfaces are built and updated. By using a Virtual DOM representation and a smart reconciliation process, React ensures that changes are made efficiently, resulting in high-performance web applications.


### Virtual DOM vs. Actual DOM

Let's compare the Virtual DOM to the Actual DOM to highlight the benefits of using a Virtual DOM:

#### Actual DOM:
- The Actual DOM is the real representation of a web page's structure.
- Whenever there's a change in the data or state, the Actual DOM is directly updated, leading to potentially slow and inefficient operations, especially for complex web applications.
- Frequent updates to the Actual DOM can cause performance bottlenecks and a poor user experience.

#### Virtual DOM:
- The Virtual DOM is a lightweight copy of the Actual DOM.
- React updates the Virtual DOM instead of the Actual DOM when there are changes in the application's data or state.
- The Virtual DOM allows React to batch multiple updates and perform a single, optimized update to the Actual DOM, reducing the rendering time and improving performance.

### React's Philosophy

React's philosophy is to make the development process more predictable and developer-friendly while ensuring high-performance user interfaces. The Virtual DOM aligns with these principles by abstracting away the complexities of direct DOM manipulation and providing a structured, efficient way to update the UI.

### Use Cases for the Virtual DOM

Understanding when and why to use the Virtual DOM is crucial:

#### 1. Complex User Interfaces:
When building applications with a complex user interface that frequently changes, React's Virtual DOM shines. It minimizes the performance impact of frequent updates.

#### 2. Real-Time Applications:
Real-time applications like chat applications, stock market dashboards, or online gaming benefit from the Virtual DOM's ability to handle rapid data changes and updates.

#### 3. Cross-Platform Development:
If you plan to develop for multiple platforms (web, mobile, desktop) using technologies like React Native, React's Virtual DOM abstraction ensures consistency and ease of development across platforms.

 

In summary, the Virtual DOM is a crucial concept in React that enhances the performance and developer experience when building web applications. By providing a structured approach to updating the UI and minimizing direct DOM manipulations, React ensures that your applications are both efficient and maintainable.



---

## Props vs State

In React, props and state are fundamental concepts for managing and passing data within your components. Props are used to pass data from parent to child components, while state is used for managing a component's internal data and reactivity. Understanding the difference between them is crucial for building effective and maintainable React applications.

### Props

Props, short for "properties," are a way to pass data from a parent component to a child component in React. They are read-only and help in making your components reusable. Here's a breakdown of key points:

- **Passing Data:** Props allow you to pass data or values (strings, numbers, objects, functions, etc.) from a parent component to a child component.

- **Immutable:** Props are immutable, which means once they are set in a child component, they cannot be changed from within that component.

- **Example:** Suppose you have a `User` component that displays user information, and you pass the user's name and email as props from a parent component:

```jsx
function ParentComponent() {
  const user = { name: 'John Doe', email: 'johndoe@example.com' };

  return <User name={user.name} email={user.email} />;
}

function User(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>Email: {props.email}</p>
    </div>
  );
}
```

### State

State is used to manage a component's internal data that can change over time and trigger re-renders when updated. Here are the key points about state:

- **Internal Data:** State is used to store and manage data within a component. It's mutable and can be changed using the `setState` method.

- **Reactivity:** When state data changes, React automatically re-renders the component to reflect those changes in the UI.

- **Example:** Suppose you have a `Counter` component that displays and updates a count value:

```jsx
import React, {Component} from 'docs/react/index';

class Counter extends Component {
    constructor() {
        super();
        this.state = {
            count: 0,
        };
    }

    incrementCount = () => {
        this.setState({count: this.state.count + 1});
    };

    render() {
        return (
            <div>
                <p>Count: {this.state.count}</p>
                <button onClick={this.incrementCount}>Increment</button>
            </div>
        );
    }
}

export default Counter;
```

### Differences Between Props and State

To further clarify the distinctions between props and state, let's delve into their differences in more detail:

1. **Source of Data:**

    - **Props:** Data in props is passed from parent components to child components. It flows in one direction, from top to bottom in your component hierarchy.

    - **State:** State is internal to a component and is managed within that component itself. It doesn't depend on external sources and can change over time.

2. **Mutability:**

    - **Props:** Props are immutable, meaning that child components cannot modify the data received via props. They are essentially read-only.

    - **State:** State is mutable, and components can modify their own state using the `setState` method. When state changes, it triggers a re-render of the component.

3. **Use Cases:**

    - **Props:** They are primarily used for passing data and configuration to child components. For example, passing user information, settings, or configuration data.

    - **State:** State is used for managing dynamic and changing data within a component. It's ideal for handling user input, toggling UI elements, or maintaining data that can change during the component's lifecycle.

4. **Updates and Re-renders:**

    - **Props:** Changes in props are not controlled by the component that receives them. They are updated externally by the parent component. Changes in props can cause the child component to re-render, but it's not directly controlled by the child component.

    - **State:** A component can control its own state and trigger re-renders when the state changes. This gives you fine-grained control over how and when your component updates in response to data changes.

5. **Default Values:**

    - **Props:** You can set default values for props using PropTypes or default function parameters in functional components.

    - **State:** You initialize state in class components within the constructor or use the `useState` hook in functional components with an initial value.

6. **Accessing Data:**

    - **Props:** Data from props is accessed using the `props` object in functional components or `this.props` in class components.

    - **State:** State data is accessed using `this.state` in class components or the state variable returned by the `useState` hook in functional components.


Understanding these differences is crucial for effectively designing and building React applications. Using props for passing data and state for managing component-specific dynamic data helps maintain a clear and predictable flow of information within your application.


####  Best Practices for Props:

1. **Keep Props Simple:** Props should ideally contain simple data or functions to maintain a clear and understandable interface between parent and child components.

2. **Documentation:** Document the props your components accept, including their data types and descriptions, using tools like PropTypes or TypeScript.

3. **Immutable Props:** Treat props as read-only. If a child component needs to modify data received via props, consider lifting the state to a higher-level component.

4. **Destructuring Props:** In functional components, use object destructuring to simplify the access to props. For example, `function MyComponent({ prop1, prop2 }) { /* ... */ }`.

#### Best Practices for State:

1. **Initialize State Correctly:** In class components, initialize state in the constructor. In functional components, use the `useState` hook and ensure that it receives an initial value.

2. **Avoid Direct State Mutations:** Never directly modify state using `this.state` in class components. Use `setState` to update state to ensure proper reactivity.

3. **Functional setState:** When updating state that depends on the previous state value, use the functional form of `setState` to prevent race conditions.

```javascript
   this.setState((prevState) => ({
     count: prevState.count + 1,
   }));
```

4. **State Consolidation:** If multiple state values are closely related, consider consolidating them into a single state object to simplify management.

5. **Avoid Excessive State:** Don't overuse state within components. Keep state localized to the minimal amount needed to maintain the component's functionality.

6. **Consider Using State Management Libraries:** For complex applications, consider using state management libraries like Redux or Mobx to manage application-wide state.

#### When to Choose Props vs. State:

- Use props when data needs to flow from parent to child components.
- Use state when dealing with dynamic, component-specific data that can change over time.
- Consider using a combination of props and state when building complex UI components.

By following these best practices and understanding the nuances of props and state in React, you can build more maintainable and predictable applications that efficiently manage and display data.


---



## Local Storage for React

Local storage provides a way to store data locally within the user's browser. It's useful for persisting user preferences, authentication tokens, or application state that doesn't require frequent updates or server interaction. Here's how to use local storage to save and retrieve objects in React:

**Saving Objects:**

###   1. **Stringify the Object:** 
Local storage can only store strings. Use `JSON.stringify()` to convert your JavaScript object into a JSON string before saving it.

```javascript
const dataToSave = {
  name: "Alice",
  todos: ["Buy milk", "Walk the dog"],
};

const serializedData = JSON.stringify(dataToSave);
```

###   2. **Set the Item:** 
Use the `localStorage.setItem()` method to store the serialized data under a specific key.

```javascript
localStorage.setItem("userData", serializedData);
```

###  3. **Retrieving Objects:**

1. **Get the Item:** Use `localStorage.getItem()` to retrieve the JSON string associated with the key.

```javascript
const retrievedData = localStorage.getItem("userData");
```

2. **Parse the JSON:** Convert the retrieved JSON string back into a JavaScript object using `JSON.parse()`.

```javascript
if (retrievedData) {
  const parsedData = JSON.parse(retrievedData);
  console.log(parsedData.name); // Output: "Alice"
  console.log(parsedData.todos); // Output: ["Buy milk", "Walk the dog"]
}
```

###   4. **Example (React Component):**

Here's a basic example demonstrating how to save and retrieve user data (name and todos) using local storage within a React component:

```jsx
import React, { useState, useEffect } from 'react';

const MyComponent = () => {
  const [userData, setUserData] = useState({ name: "", todos: [] });

  useEffect(() => {
    const storedData = localStorage.getItem("userData");
    if (storedData) {
      setUserData(JSON.parse(storedData));
    }
  }, []);

  const handleChange = (event) => {
    const { name, value } = event.target;
    setUserData((prevData) => ({ ...prevData, [name]: value }));
  };

  const handleSave = () => {
    localStorage.setItem("userData", JSON.stringify(userData));
  };

  return (
    <div>
      <input
        type="text"
        name="name"
        value={userData.name}
        onChange={handleChange}
      />
      <br />
      <textarea
        name="todos"
        value={userData.todos.join(", ")} // Convert array to comma-separated string
        onChange={handleChange}
      />
      <br />
      <button onClick={handleSave}>Save</button>
    </div>
  );
};

export default MyComponent;
```

**Important Considerations:**

* Local storage has limited storage capacity (typically 5MB).
* Data stored in local storage is accessible to client-side scripts, so avoid storing sensitive information.
* Consider alternative storage solutions like cookies or IndexedDB for more complex data persistence requirements.
 

---


---
