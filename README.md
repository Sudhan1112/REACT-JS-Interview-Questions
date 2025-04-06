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
