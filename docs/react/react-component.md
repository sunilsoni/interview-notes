---
title: React Component
hide:
  - tags

tags:
  - React Component
  - Controlled Components
  - Uncontrolled Components
  - Virtual DOM
  - Higher Order Component (HOC)
  - Passing Data from Parent Components to Deeply Nested Child Components


---

# React Component

---

## React Component


---------

## Controlled & Uncontrolled Components

### Controlled Components

Controlled components in React are components that control the state of the input form elements. The input form element's state is handled by the React component using the `useState` hook or by class component's state. The data for these elements is controlled by React, as the source of truth remains within the state of the component.

#### How do they work?

- **State Management:** In a controlled component, the React state controls the value of the input element. This means any change to the input field is updated via state, making the React state the single source of truth.

- **Event Handling:** The onChange event listener is used to update the state and reflect the input value. Each keystroke updates the state, and the value of the input is updated to reflect this change.

#### Example

```jsx
import React, { useState } from 'react';

function ControlledForm() {
  const [value, setValue] = useState('');

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  const handleSubmit = (event) => {
    alert('A name was submitted: ' + value);
    event.preventDefault();
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={value} onChange={handleChange} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}
```

#### Why use them?

- **Predictability:** Since the form data is handled by the component's state, the data flow is more predictable and easier to debug.
- **Validation:** Can easily validate user input before submitting it.
- **Consistency:** Ensures consistency of the input value throughout the component.

### Uncontrolled Components


Uncontrolled components are another way to handle form inputs in React. Instead of using the component's state to manage the form's input value, they use the DOM itself to get the current value of the input.

#### How do they work?

- **Ref to Access:** Uncontrolled components use `ref` to directly access the DOM element, and you use the `defaultValue` attribute to set the initial value of the input.

- **Less Code:** They require less code for simple forms since you don't need to write an event handler for every way your data can change.

#### Example

```jsx
import React, { useRef } from 'react';

function UncontrolledForm() {
  const inputRef = useRef();

  const handleSubmit = (event) => {
    alert('A name was submitted: ' + inputRef.current.value);
    event.preventDefault();
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" ref={inputRef} defaultValue="Bob" />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}
```

#### Why use them?

- **Simplicity:** Easier to integrate with non-React code as it uses the DOM to manage form data.
- **Less Boilerplate:** Reduces the need for state management boilerplate code for the form inputs.



The choice between controlled and uncontrolled components depends on the specific needs of your application. Controlled components offer more predictability and control, making them suitable for complex forms with dynamic inputs. Uncontrolled components, on the other hand, are easier to use and integrate with external libraries, making them a good choice for simpler forms or when you need direct access to the DOM elements.

### Best Practices

#### When to Use Controlled Components

- **Dynamic Forms:** When your form needs to dynamically update other UI elements based on the input's state.
- **Instant Input Validation:** To provide instant feedback to the user as they type or select options.
- **Form Submission Handling:** When you need to pre-process the data before submitting it to the server.

Controlled components give you complete control over the form's behavior and state, making it easier to manipulate form data according to the application's needs.

#### When to Use Uncontrolled Components

- **Non-Interactive Forms:** For simple forms where you just need to retrieve the value at submit time without needing to control the input's state throughout the form's lifecycle.
- **Integrating with Third-Party DOM Libraries:** When you're using React with other libraries that manipulate the DOM, uncontrolled components can be a better choice as they allow the DOM to directly manage the form data.

Uncontrolled components are useful for simplifying the component's code by reducing the need for state management and event handling.

#### Mixing Controlled and Uncontrolled

It's possible to mix controlled and uncontrolled components in the same form, but it's generally recommended to stick to one pattern to maintain consistency in your form handling logic.

#### Transitioning Between Controlled and Uncontrolled

React gives a warning if a component switches from controlled to uncontrolled (or vice versa) during its lifecycle. This usually happens due to bugs in the code where the value prop is sometimes undefined or null. It's important to ensure that inputs are consistently controlled or uncontrolled throughout their lifecycle.

#### Performance Considerations

- **Controlled Components:** Since every keystroke updates the state and causes a re-render, this might lead to performance issues on larger forms or on slower devices. Techniques like debouncing input can mitigate performance concerns.
- **Uncontrolled Components:** Since they do not involve state updates on every input change, they can be more performant for simple forms. However, they might complicate the application's data flow, making debugging more challenging.



- **Controlled Components:** Offer more control and flexibility for complex forms and dynamic input validations.
- **Uncontrolled Components:** Provide a simpler approach for accessing form values, suitable for quick form implementations and when direct DOM access is required.

Choosing between controlled and uncontrolled components in React forms depends on the specific requirements of your application, such as the complexity of the form, the need for real-time validation, and the preference for either React state management or direct DOM manipulation.


---

## Higher Order Component (HOC)

Higher Order Component, often abbreviated as HOC, is a design pattern in React, a popular JavaScript library for building user interfaces. It is a way to reuse component logic in a more abstract and modular manner. HOCs are not components themselves but functions that take a component as input and return a new enhanced component with additional props or behavior.

### How HOCs Work

1. **Input Component**: You start with a React component that you want to enhance or modify in some way.

2. **Higher Order Component**: You create a higher order component function. This function takes the input component as an argument and may also take other configuration options.

3. **Enhanced Component**: The HOC function returns a new component that wraps the input component. This new component can provide additional props, state, or behavior to the input component.

### Example

Let's say you have a simple `UserComponent` that displays user information:

```javascript
function UserComponent(props) {
  return (
    <div>
      <h1>Hello, {props.name}</h1>
      <p>Email: {props.email}</p>
    </div>
  );
}
```

Now, you want to add authentication to this component using a HOC:

```javascript
function withAuthentication(WrappedComponent) {
  return function WithAuth(props) {
    const user = getCurrentUser(); // Assume there's a function to get the current user.
    if (user) {
      return <WrappedComponent {...props} user={user} />;
    } else {
      return <p>Please log in to view this content</p>;
    }
  };
}
```

Now, you can enhance your `UserComponent` using the `withAuthentication` HOC:

```javascript
const UserWithAuth = withAuthentication(UserComponent);
```

By doing this, `UserWithAuth` will receive the `user` prop, and it will only render the `UserComponent` if a user is authenticated.

### Benefits of HOCs

- Reusability: You can apply the same logic or behavior to multiple components without duplicating code.

- Separation of Concerns: HOCs allow you to separate different concerns (e.g., authentication, data fetching) from your components.

- Cleaner Code: Your components can focus on rendering UI, making them cleaner and easier to maintain.

- Composition: You can compose multiple HOCs together to build complex behaviors.

Higher Order Components are a powerful tool in React's ecosystem, providing a flexible way to extend and enhance the capabilities of your components.

### Drawbacks of HOCs

While HOCs offer many advantages, they also come with some potential drawbacks:

- **Wrapper Component Nesting**: When you use multiple HOCs on a component, it can lead to a nesting of wrapper components, making the component tree more complex.

- **Prop Collisions**: If HOCs add props to the wrapped component without careful naming conventions, you may encounter prop name collisions.

- **Readability**: A component enhanced with multiple HOCs can become less readable if not well-structured.

- **Inversion of Control**: HOCs introduce an inversion of control, where the wrapped component relies on props provided by the HOC, making the component less self-contained.

### Common Use Cases for HOCs

1. **Authentication**: As shown in the example, HOCs can be used to conditionally render components based on user authentication status.

2. **Data Fetching**: You can use HOCs to fetch data from an API and pass it as props to a component.

3. **Logging and Analytics**: HOCs can log user actions or send data to analytics services without cluttering the component code.

4. **Redux Integration**: In Redux-based applications, HOCs are often used to connect components to the Redux store.

5. **Routing**: HOCs can be employed to protect routes or add route-specific data to components.

### Using HOCs in React

To use a Higher Order Component in React, you simply wrap your component with the HOC function, like this:

```javascript
const EnhancedComponent = withSomeHOC(BaseComponent);
```

The `EnhancedComponent` will have the additional behavior or props provided by the HOC.

In recent versions of React, you can also use the `useMemo` hook or the `React.forwardRef` function to achieve similar effects as HOCs with a more functional approach.

Remember that while HOCs are a powerful tool, you should use them judiciously and consider other options like Render Props or Hooks when appropriate, as React's ecosystem has evolved with alternative patterns for code organization and reusability.



### Higher Order Component (HOC) vs. Functional Component

#### Higher Order Component (HOC)

- **Nature**: HOC is not a component itself; it's a function that takes a component as input and returns a new component with additional props or behavior.

- **Composition**: HOCs encourage a composition approach where you wrap your base component with multiple HOCs to add various functionalities.

- **Usage**: HOCs are typically used in class-based components, although they can be used with functional components as well.

- **State Management**: HOCs can manage state, access context, and use lifecycle methods since they wrap class components.

- **Code Reusability**: HOCs promote code reusability by abstracting away common logic and behavior.

- **Example**: As shown earlier, a common use case is adding authentication or data fetching logic to a component.

#### Functional Component

- **Nature**: Functional components are JavaScript functions that take props as arguments and return JSX to describe the UI.

- **Composition**: Functional components are composed together using function calls, and logic can be extracted into custom hooks for code reuse.

- **Usage**: Functional components are the preferred way of building UI in modern React, especially with the introduction of React Hooks.

- **State Management**: Functional components can manage state using hooks like `useState` and `useEffect`, making them more versatile.

- **Code Reusability**: Functional components promote code reusability by utilizing custom hooks and function composition.

- **Example**: A functional component is a simple function that returns JSX, such as:

  ```javascript
  function FunctionalComponent(props) {
    return <div>{props.message}</div>;
  }
  ```

#### Key Differences


| Aspect                        | Higher Order Component (HOC) | Functional Component |
|-------------------------------|-----------------------------|----------------------|
| **Nature**                    | Function that wraps components | JavaScript function that returns JSX |
| **Composition**               | Encourages composition with other HOCs | Composed using function calls and custom hooks |
| **Usage**                     | Initially used with class components; can also be used with functional components | Preferred for new code in modern React |
| **State Management**          | Can manage state, access context, and use lifecycle methods when applied to class components | Can manage state using hooks like `useState` and `useEffect` |
| **Code Reusability**          | Promotes code reusability by abstracting common logic | Promotes code reusability through custom hooks and function composition |

This table provides a concise overview of the differences between HOCs and Functional Components in React.

1. **Nature**: HOCs are functions that wrap existing components, while functional components are the fundamental building blocks of a React application.

2. **Composition**: HOCs encourage the composition of multiple higher-order components, which can lead to a nested structure, whereas functional components promote function composition, making it more straightforward.

3. **Usage**: HOCs were traditionally used with class components but can also be applied to functional components. Functional components are the standard choice for new React code.

4. **State Management**: Functional components can manage state using hooks, while HOCs can manage state and lifecycle methods when applied to class components.

5. **Code Reusability**: Both HOCs and functional components promote code reusability, but functional components offer a more modern and concise approach with hooks and custom hooks.

In summary, functional components are the preferred way to build UI in modern React due to their simplicity, readability, and the power of hooks. HOCs, on the other hand, are a more traditional pattern that can still be useful in certain situations, especially when working with existing class-based components or when you need to apply complex logic to multiple components.

---



## Reusable Components in React

### What Are Reusable Components?

Reusable components are building blocks of your React application that can be used across different parts of your project. By creating reusable components, you can improve code maintainability, reduce duplication, and enhance collaboration among teams.

### Example: Button Component

Let's create a simple reusable `Button` component:

1. **Button.js** (Reusable Component):

```jsx
// Button.js
import React from 'react';
import PropTypes from 'prop-types';

const Button = ({ label, onClick, disabled }) => {
  return (
    <button
      className="my-button"
      onClick={onClick}
      disabled={disabled}
    >
      {label}
    </button>
  );
};

Button.propTypes = {
  label: PropTypes.string.isRequired,
  onClick: PropTypes.func.isRequired,
  disabled: PropTypes.bool,
};

export default Button;
```

2. **Usage in Different Pages or Components**:

    - In your various pages or components, import and use the `Button` component:

   ```jsx
   // LoginPage.js
   import React from 'react';
   import Button from './Button';

   const LoginPage = () => {
     const handleLogin = () => {
       // Handle login logic
     };

     return (
       <div>
         <h1>Login Page</h1>
         <Button label="Login" onClick={handleLogin} />
       </div>
     );
   };

   export default LoginPage;
   ```

   ```jsx
   // UserProfilePage.js
   import React from 'react';
   import Button from './Button';

   const UserProfilePage = () => {
     const handleLogout = () => {
       // Handle logout logic
     };

     return (
       <div>
         <h1>User Profile Page</h1>
         <Button label="Logout" onClick={handleLogout} />
       </div>
     );
   };

   export default UserProfilePage;
   ```



### Example: Card Component

 
A common reusable component in React applications is a Card component, typically used to display information in a visually appealing manner. This Card component can be reused across different teams or pages within an application.

####  Implementation
```jsx
import React from 'react';

const Card = ({ title, content }) => {
  return (
    <div className="card">
      <h2>{title}</h2>
      <p>{content}</p>
    </div>
  );
};

export default Card;
```

#### How to Reuse
1. **Team Collaboration**: Different teams working on various sections of the application can utilize the Card component to maintain consistency in design and functionality. For example, the marketing team might use it to showcase product features, while the development team might use it to display error messages or user notifications.

2. **Multiple Pages**: The Card component can be reused across different pages of the application. For instance, it could be used on the homepage to highlight key content, on the product page to display product details, and on the contact page to showcase team members or testimonials.

3. **Customization**: The Card component can be easily customized by passing props such as title, content, background color, or styles. This flexibility allows teams to adapt the component to various contexts without having to rewrite the code.

 
### Benefits of Reusable Components:

1. **Consistency**: Using the same `Button` component ensures consistent styling and behavior across your app.
2. **Maintenance**: If you need to update the button style or behavior, you only need to do it in one place (the `Button` component).
3. **Collaboration**: Different teams can work on different parts of the app, knowing they're using the same components.
4. **Testing**: Reusable components can be thoroughly tested independently.

Remember to keep your reusable components focused and generic. Avoid adding too much specific logic to them; instead, handle that in the parent components.


---

## Passing Data from Parent Components to Deeply Nested Child Components 

### 1. Prop Drilling

Manual Passing Through Each Level
Prop drilling involves passing data from parent components down to deeply nested child components through each level of the component tree. This method requires you to manually pass props at every level until you reach the target component.

- **What It Is**: Props are a way to pass data from parent components to child components.
- **How It Works**:
    - In the parent component, define a prop (e.g., `myData`) and assign it a value.
    - Pass this prop to the child component as an attribute (e.g., `<ChildComponent myData={someValue} />`).
    - In the child component, access the prop using `props.myData`.

### Pros & Cons

* **Concept:** The most basic method involves passing data down the component tree as props through each intermediate component.

**Pros:**

* Simple to implement for shallow nesting.
* Clear understanding of data flow.

**Cons:**

* Can become cumbersome and error-prone with deep nesting, leading to "prop drilling."
* Changes in parent data require updates to all components in the chain.

**Example:**

```jsx
// Parent.jsx
const Parent = () => {
  const data = { message: "Hello from Parent!" };
  return (
    <div>
      <Child1 data={data} />
    </div>
  );
};

// Child1.jsx
const Child1 = ({ data }) => {
  return (
    <div>
      <Child2 data={data} />
    </div>
  );
};

// Child2.jsx (Deeply Nested)
const Child2 = ({ data }) => {
  return (
    <div>
      <p>{data.message}</p>
    </div>
  );
};
```

### 2. React Context (Ideal for Shared Data)

Providing and Consuming Data Easily
The Context API allows you to share values between components without explicitly passing a prop through every level of the tree. It's ideal for global data like themes, user information, or preferences.

**Creating a Context:** First, create a context using React.createContext().
**Providing a Context Value:** Use a Provider to pass the context to deeply nested components.
**Consuming the Context:** Use the useContext hook or Consumer component to access the context in any nested component.

- **What It Is**: Context provides a way to share data across the component tree without explicitly passing props down the hierarchy.
- **How It Works**:
    - Create a context using `React.createContext`.
    - In the parent component, wrap the child components that need access to the shared data with the `Context.Provider`.
    - In the child components, use `Context.Consumer` or `useContext` to access the shared data.

 
* **Concept:** Create a global context to provide data to any component within the provider tree, regardless of nesting depth.

**Pros:**

* Ideal for managing data shared across various parts of the application.
* Avoids prop drilling for deeply nested components.

**Cons:**

* Adds some overhead in setting up context.
* May lead to unintended data consumption if not used carefully.

**Example:**

```jsx
// DataContext.jsx
import React, { createContext, useState } from 'react';

const DataContext = createContext();

const DataProvider = ({ children }) => {
  const [data, setData] = useState({ message: "Hello from Context!" });

  return (
    <DataContext.Provider value={{ data, setData }}>
      {children}
    </DataContext.Provider>
  );
};

// Parent.jsx
const Parent = () => {
  return (
    <DataProvider>
      <Child1 />
    </DataProvider>
  );
};

// Child2.jsx (Deeply Nested)
const Child2 = () => {
  const { data } = useContext(DataContext);
  return (
    <div>
      <p>{data.message}</p>
    </div>
  );
};
```

### 3. Redux (State Management for Complex Apps)

- **What It Is**: Redux is a state management library for managing global application state.
- **How It Works**:
    - Define a global state using Redux.
    - Dispatch actions to update the state.
    - Connect child components to the Redux store using `connect` or hooks like `useSelector`.


 

* **Concept:** For large-scale applications with intricate data flows, Redux offers a centralized state management solution.

**Pros:**

* Provides a single source of truth for application state.
* Predictable state updates and easier debugging.
* Scalable for complex data interactions.

**Cons:**

* Introduces additional complexity with setup and learning curve.
* Might be overkill for smaller applications.

**Choosing the Right Method:**

* **Shallow Nesting:** Prop drilling is sufficient.
* **Shared Data Across Components:** Opt for React Context.
* **Complex State Management:** Consider Redux for large-scale applications.


### 4. **Event Callbacks**

- **What It Is**: Pass callback functions from parent to child components.
- **How It Works**:
    - In the parent component, define a function (e.g., `handleDataChange`).
    - Pass this function as a prop to the child component (e.g., `<ChildComponent onDataChange={handleDataChange} />`).
    - In the child component, call `props.onDataChange(newValue)` to update the data.

### 5. **React Router Params**

- **What It Is**: When using React Router, you can pass data via route parameters.
- **How It Works**:
    - Define a route with a parameter (e.g., `"/user/:userId"`).
    - In the child component, access the parameter using `props.match.params.userId`.

Remember to choose the approach that best fits your application's needs. Whether it's simple props, context, Redux, or route parameters, passing data efficiently ensures a well-organized and maintainable React application! 

 
In React applications, there are several approaches to effectively pass data from parent components to deeply nested child components. Here's a breakdown of the common methods:





 ---



---


---

