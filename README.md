# React Interview Questions & Answers

### ⚠️ Without strong communication, even the perfect answer can shatter like glass.

## 📑 Table of Contents

| No. | Questions |
|-----|-----------|
| 1. | [What is React?](#1-what-is-react) |
| 2. | [What are the major features of React JS?](#2-what-are-the-major-features-of-react-js) |
| 3. | [What is JSX?](#3-what-is-jsx) |
| 4. | [What is the difference between Element and Component?](#4-what-is-the-difference-between-element-and-component) |
| 5. | [How to create components in React?](#5-how-to-create-components-in-react) |
| 6. | [When to use a Class Component over a Function Component?](#6-when-to-use-a-class-component-over-a-function-component) |
| 7. | [What are Pure Components?](#7-what-are-pure-components) |
| 8. | [What is State?](#8-what-is-state) |
| 9.  | [What is Props?](#9-what-is-props)                                   |
| 10. | [Difference Between State and Props](#10-difference-between-state-and-props) |
---

## 1. What is React?

**React** is an **open-source JavaScript library** used to build **user interfaces**, especially for **Single Page Applications (SPAs)**.  
It was created by **Jordan Walke**, a software engineer at **Facebook**.  
React was first deployed on Facebook's **News Feed** in **2011**, and later on **Instagram** in **2012**.

⬆️ [Back to Top](#react-interview-questions--answers)
---

## 2. What are the major features of React JS?

- Uses **JSX syntax**, which allows writing **JavaScript inside HTML**, making the code more readable and intuitive.
- Utilizes a **Virtual DOM** instead of manipulating the **Real DOM**, improving performance.
- Supports **Server-Side Rendering (SSR)**, which helps with **Search Engine Optimization (SEO)**.
- Follows a **unidirectional data flow** (also known as **one-way data binding**), making data management more predictable.
- Encourages the use of **reusable UI components**, which speeds up development and ensures consistency.

⬆️ [Back to Top](#react-interview-questions--answers)
---

## 3. What is JSX?

**JSX** stands for **JavaScript XML**.  
It's a syntax extension to **JavaScript** that allows writing **HTML-like code** within React components.  
JSX is supported by **ECMAScript (ES)** standards and makes the code more expressive and easier to write.

### ✅ With JSX:
```jsx
const myElement = <h1>React is {5 + 5} times better with JSX</h1>;
```

### ❌ Without JSX:
```js
const myElement = React.createElement(
  "h1",
  null,
  "React is " + (5 + 5) + " times better with JSX"
);
```
⬆️ [Back to Top](#react-interview-questions--answers)
---

## 4. What is the difference between Element and Component?

#### **Element**  
- A Element is a **plain JavaScript object** describing what should appear on the screen.  
- It Represents a **virtual DOM node** (e.g., HTML tag or component instance).  
- Element is a **Immutable** object (cannot be changed after creation).  
- Created using `React.createElement()` or **JSX**:  
  ```jsx
  const element = <div id="login-btn">Login</div>;
  ```
- **Structure**:  
  ```js
  {
    type: 'div',
    props: { 
      id: 'login-btn',
      children: 'Login' 
    }
  }
  ```

#### **Component**  
- A **function or class** that accepts `props` and returns a **React element tree (JSX)**.  
- It is **Reusable** and **composable (Mutable)**.  
- **Two types**:  
  1. **Function Component**:  
     ```jsx
     const Button = ({ handleLogin }) => (
       <div id="login-btn" onClick={handleLogin}>Login</div>
     );
     ```  
  2. **Class Component**:  
     ```jsx
     class Button extends React.Component {
       render() {
         return <div id="login-btn" onClick={this.props.handleLogin}>Login</div>;
       }
     }
     ```  
⬆️ [Back to Top](#react-interview-questions--answers)
---

## 5. How to create components in React?

There are two type of component declaration: 
### **i. Function Components**  
Simplest way to create a **stateless** component:  
```jsx
function Greeting({ message }) {
  return <h1>{`Hello, ${message}`}</h1>;
}
```

### **ii. Class Components**  
Used for **stateful** components or lifecycle methods:  
```jsx
class Greeting extends React.Component {
  render() {
    return <h1>{`Hello, ${this.props.message}`}</h1>;
  }
}
```
⬆️ [Back to Top](#react-interview-questions--answers)
---

## 6. When to use a Class Component over a Function Component?
After the addition of **hooks** in functional component it is always recommended to use **functional component** over **class component** in React. Because you could use **State**, **lifecycle methods** and other features that were only available in class components it is also now available in functional component.

But there are two reasons to use class component over functional components.

i.) If you need a React functionality whose functional component is not equivalent to the level of class components, in this scenario you can use class component over functional component.

ii.) Class components are Used to maintain backward compatibility. 
## Summary:

### Use functional component:
- If you don't need state or lifecycle methods.
- For **simplicity**, **readablity**, and need to follow **modern code practices**, especially with the use of **React Hooks** for state management and side effects etc. You can go for functional component.

### Use Class component:
- If you need to manage state or need to use **lifecycle methods**. you can go for class components
- Class components are used for maintain backward compatability. 
- Some advanced **error handling** scenarios (using Error Boundaries)

### Evolution of Components in React

#### Class Components
```jsx
class Welcome extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
  
  componentDidMount() {
    console.log('Component mounted');
  }

  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

#### Function Components with Hooks
```jsx
function Welcome(props) {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    console.log('Component mounted');
  }, []);

  return <h1>Hello, {props.name}</h1>;
}
```
⬆️ [Back to Top](#react-interview-questions--answers)

---

## 7. What are Pure Components?

**Pure components** are components that render the **same output** for the **same `state` and `props`**. They help with **performance optimization** by preventing **unnecessary re-renders**.

---

## Function Components

- Use `React.memo()` to create **pure function components**.
- Prevents re-renders by comparing previous and new `props` using **shallow comparison**.
- Doesn't compare `state` since function components already avoid re-renders when setting the **same state**.

### ✅ Example:
```jsx
const MemoizedComponent = memo(SomeComponent, arePropsEqual?);
```

---

## Class Components

- Extend `React.PureComponent` instead of `React.Component`.
- Automatically implements `shouldComponentUpdate()` with **shallow `props` and `state` comparison**.

---

## Example
```jsx
import { memo, useState } from "react";

const EmployeeProfile = memo(function EmployeeProfile({ name, email }) {
  return (
    <>
      <p>Name: {name}</p>
      <p>Email: {email}</p>
    </>
  );
});

export default function EmployeeRegForm() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  
  return (
    <>
      <label>
        Name: <input value={name} onChange={(e) => setName(e.target.value)} />
      </label>
      <label>
        Email: <input value={email} onChange={(e) => setEmail(e.target.value)} />
      </label>
      <hr />
      <EmployeeProfile name={name} />
    </>
  );
}
```

> **Note:** In this example, `EmployeeProfile` won’t re-render when the `email` changes in the parent component since it’s not passed as a `prop`.

**Pure components** help optimize performance by:
- Making output **predictable**
- Reducing **unnecessary renders**

⬆️ [Back to Top](#react-interview-questions--answers)
---

## 8. What is State?

`State` is an **object** that holds information which may **change over the lifetime** of a component.  
When the `state` object changes, the component **re-renders**.

![State in React](https://github.com/sudheerj/reactjs-interview-questions/raw/master/images/state.jpg)

> *State is used for internal communication inside a component.*
---

## Key Characteristics

-  **Private** to the component that owns it  
-  Causes component **re-rendering** when updated  
-  Should be kept as **simple as possible**  
-  Provides a **snapshot** for each render  

---

##  Function Components Example

```jsx
import { useState } from "react";

function User() {
  const [message, setMessage] = useState("Welcome to React world");

  return (
    <div>
      <h1>{message}</h1>
    </div>
  );
}
```

---

##  Class Components Example

```jsx
import React, { Component } from "react";

class User extends Component {
  constructor(props) {
    super(props);
    this.state = {
      message: "Welcome to React world"
    };
  }

  render() {
    return (
      <div>
        <h1>{this.state.message}</h1>
      </div>
    );
  }
}
```

---

##  Best Practices for Using State

-  Minimize the number of **stateful components**
-  Keep `state` as **simple** as possible
-  `State` is **private** and **fully controlled** by the component
-  `State` is **not accessible** to other components unless **explicitly passed down**

⬆️ [Back to Top](#react-interview-questions--answers)
---
## 9. What is Props?

Props (short for "properties") are inputs passed to components from their parent component. They are read-only and help make components reusable.

## Key Characteristics

- Read-only values passed from parent to child components  
- Similar to HTML attributes in syntax  
- Cannot be modified by the receiving component  

## Purpose of Props

- Pass custom data to components  
- Trigger state changes  
- Enable component reusability  

## Basic Usage

```jsx
<Element reactProp={"1"} />
```

### Example

```jsx
import React from "react";
import ReactDOM from "react-dom";

const ChildComponent = (props) => {
  return (
    <div>
      <p>{props.name}</p>
      <p>{props.age}</p>
      <p>{props.gender}</p>
    </div>
  );
};

const ParentComponent = () => {
  return (
    <div>
      <ChildComponent name="John" age="30" gender="male" />
      <ChildComponent name="Mary" age="25" gender="female" />
    </div>
  );
};
```

### Using Destructuring

```jsx
const ChildComponent = ({ name, age, gender = "male" }) => {
  return (
    <div>
      <p>{name}</p>
      <p>{age}</p>
      <p>{gender}</p>
    </div>
  );
};
```

**Note**: Default values (like `gender = "male"`) are only used when the prop is `undefined`, not when `null` or `0` is passed.

---

## 10. Difference Between State and Props?

| Props                                   | State                                         |
|----------------------------------------|----------------------------------------------|
| Passed from parent component           | Managed within the component                 |
| Read-only                              | Can be modified using `setState()`           |
| Make components reusable               | Acts as component's memory                   |
| Acts like function arguments           | Acts like component's private variables      |
| Can be used to configure behavior      | Used to manage internal component data       |
| Cannot cause re-renders on their own   | Changes trigger component re-rendering       |
| Flow downward from parent to child     | Contained and managed by specific components |

---
