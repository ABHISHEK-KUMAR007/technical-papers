## 1. What is React?

**React is a JavaScript library that helps developers create interactive user interfaces.**

- Created and maintained by Meta.
- Commonly used for building Single Page Applications (SPAs).
- Helps create reusable UI components.
- Automatically updates the UI when data changes.
- Makes applications easier to organise using components.

**Example:**

``` jsx
function App() {
  return (
    <>
      <Navbar />
      <Sidebar />
      <Footer />
    </>
  );
}
```

Advantages of React
1. Reusability: Allows us to reuse components instead of writing the same code repeatedly.
2. Easy Maintenance: Makes code easier to organise, understand and manage.
3. Efficient Updates: Updates the UI when data changes.
4. One-Way Data Flow: Makes data movement between components easier to understand.
5. Large Community: Provides access to many libraries, tools and learning resources.

------------------------------------------------------------------------

## 2. What is JSX?

**JSX stands for JavaScript XML.**

JSX allows us to write HTML-like syntax inside JavaScript. It makes
describing the UI easier.

``` jsx
function App() {
  const name = "Abhishek";

  return <h1>Hello {name}</h1>;
}
```

Output:

``` text
Hello Abhishek
```

### Rules of JSX

**1. Every JSX expression must have one parent element.** If we want to return multiple elements, we can wrap them inside a parent element or use a Fragment (`<>...</>`).

```jsx
function App() {
    return (
        <>
            <h1>Hello</h1>
            <p>Welcome</p>
        </>
    );
}
```

**2. Use `className` instead of `class`** to assign CSS classes to HTML elements.

```jsx
<div className="container">Hello</div>
```

**3. Use `{}` to include JavaScript expressions inside JSX.**

```jsx
const age = 25;

return <p>{age}</p>;
```

**4. Always close JSX elements.** Elements like `img`, `input` and `br` must be self-closed.

```jsx
<img src="image.png" alt="Example" />
```


## 3. What is a Component?

A **component is a small, reusable part of a user interface** that helps us divide a large application into manageable pieces.

For example, a website can have separate components for its Header, Navbar, Sidebar and Footer.

```jsx
function Header() {
    return <h1>Welcome to React</h1>;
}

function Footer() {
    return <p>Copyright 2026</p>;
}

function App() {
    return (
        <>
            <Header />
            <Footer />
        </>
    );
}
```

Here, `Header` and `Footer` are separate components that we use inside the `App` component.

### Advantages of Components

- **Reusability:** Use the same component in multiple places.
- **Easy Debugging:** Find and fix errors more easily.
- **Easy Maintenance:** Make changes without affecting the entire application.
- **Code Organization:** Keep the application structured and organised.

------------------------------------------------------------------------

## 4. What are Props?

**Props stand for Properties.**

Props pass data from a parent component to a child component. 
Props areread-only.
a child should not directly modify them.

``` jsx
function User(props) {
  return <h1>Hello {props.name}</h1>;
}

function App() {
  return <User name="BHUMI" />;
}
```

### Using Destructuring

``` jsx
function User({ name, age }) {
  return (
    <>
      <h1>{name}</h1>
      <p>{age}</p>
    </>
  );
}

function App() {
  return <User name="BHUMI" age={20} />;
}
```
------------------------------------------------------------------------

## 5. What is Babel?

**Babel is a JavaScript compiler (transpiler).**

It transforms JSX and, when configured appropriately, modern JavaScript
syntax into JavaScript that the target environment can execute.

JSX example:

``` jsx
const element = <h1>Hello React</h1>;
```

Babel can transform it into JavaScript similar to:

``` javascript
import { jsx } from "react/jsx-runtime";

const element = jsx("h1", {
  children: "Hello React"
});
```

### What does Babel do?

1.  Converts JSX into JavaScript.
2.  Transforms modern JavaScript syntax when configured with suitable
    presets.
3.  Helps support older JavaScript environments.


------------------------------------------------------------------------

## 6. Difference Between Virtual DOM and Real DOM

### What is Real DOM?

DOM stands for **Document Object Model**. When a browser loads an HTML page, it converts the HTML elements into a tree-like structure called the DOM.

For example:

```html
<div>
    <h1>Hello</h1>
    <p>Welcome</p>
</div>
```

The browser represents these HTML elements as nodes in the DOM tree, which JavaScript can access and modify.

### What is Virtual DOM?

The Virtual DOM is an in-memory representation of the UI used internally by React.

Whenever the state or props change, React creates a new UI description and compares it with the previous one to identify the required changes.

### Difference Between Real DOM and Virtual DOM

| Real DOM | Virtual DOM |
|---|---|
| Represents the actual webpage. | Represents the UI in memory. |
| Managed by the browser. | Used internally by React. |
| Contains actual DOM elements. | Contains descriptions of UI elements. |
| Changes directly affect the webpage. | Helps React determine which updates are required. |

### How Does React Update the UI?

Let's understand with a simple counter example:

```jsx
import { useState } from "react";

function App() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h1>{count}</h1>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>
        </div>
    );
}
```

When we click the button:

1. The state value changes.
2. React renders the component again.
3. React creates a new UI description.
4. React compares it with the previous result.
5. React updates the necessary parts of the actual DOM.

This process is known as **Reconciliation**.

------------------------------------------------------------------------

## 7. What is a Bundler?

A **bundler is a tool that collects and processes different files used in an application and prepares them for the browser.**

A React project usually contains different types of files, such as:

- JavaScript files.
- JSX files.
- CSS files.
- Images and other assets.
- External libraries and dependencies.

### Popular Bundlers and Build Tools

1. Webpack
2. Parcel
3. Rollup
4. Vite

### Example

```text
src/
 ├── App.jsx
 ├── Header.jsx
 ├── Footer.jsx
 └── style.css
```

A bundler analyses how these files depend on each other and processes them to prepare the application.

### Why Do We Need a Bundler?

- Converts JSX into browser-compatible JavaScript through the build toolchain.
- Manages imports and dependencies between files.
- Handles CSS, images and other assets.
- Optimises files to improve production performance.
- Provides development features like Hot Module Replacement (HMR).
------------------------------------------------------------------------

## 8. Why Do We Use Vite Instead of Create React App?

**Vite is a modern frontend build tool that helps us create, run and build React applications quickly.**

Earlier, developers commonly used Create React App (CRA) to set up React projects. However, CRA is now deprecated, and Vite is a popular choice for new React projects.

### Difference Between Vite and CRA

| Vite | Create React App |
|---|---|
| Modern frontend build tool. | Older React setup tool. |
| Faster development server startup. | Generally slower startup. |
| Uses native ES modules during development. | Uses Webpack. |
| Provides fast Hot Module Replacement (HMR). | Supports hot updates. |
| Uses modern tools for production builds. | Uses Webpack for production builds. |
| Actively maintained. | Deprecated. |

### Advantages of Vite

1. **Fast Startup:** Starts the development server quickly.
2. **Quick Updates:** Reflects code changes without reloading the entire page in many cases.
3. **Easy Setup:** Requires minimal configuration.
4. **React Support:** Works smoothly with React applications.
5. **Optimised Builds:** Prepares efficient files for production.

### Creating a React Project with Vite

```bash
npm create vite@latest react-dashboard -- --template react

cd react-dashboard

npm install

npm run dev
```

These commands create a new React project, install the required packages and start the development server.

---

## 9. Understanding the React Folder Structure

When we create a React application using Vite, it generates a basic folder structure to organise our project files.

For example, let's consider a simple **Employee Dashboard** project.

```text
react-dashboard/
│
├── node_modules/
│
├── public/
│   └── logo.png
│
├── src/
│   ├── assets/
│   │   └── profile.png
│   │
│   ├── components/
│   │   ├── Navbar.jsx
│   │   ├── Sidebar.jsx
│   │   └── EmployeeCard.jsx
│   │
│   ├── App.jsx
│   ├── App.css
│   ├── index.css
│   └── main.jsx
│
├── index.html
├── package.json
├── package-lock.json
└── vite.config.js
```

Here, the `components` folder and the example images are files we can add ourselves as the project grows.

### Explanation of Important Files and Folders

| File / Folder | Purpose |
|---|---|
| `node_modules` | Contains installed libraries and packages. |
| `public` | Stores static files like logos and icons. |
| `src` | Contains the main application code. |
| `assets` | Stores images and other imported assets. |
| `components` | Contains reusable UI components. |
| `App.jsx` | Main component of our application. |
| `App.css` | Contains styles for the App component. |
| `index.css` | Contains global styles. |
| `main.jsx` | Starting point of the React application. |
| `index.html` | Main HTML page. |
| `package.json` | Stores dependencies and project scripts. |
| `package-lock.json` | Records the installed dependency versions. |
| `vite.config.js` | Contains Vite configuration settings. |

### Understanding App.jsx

The `App.jsx` file is where we can combine different components to build our application's interface.

```jsx
import Navbar from "./components/Navbar";
import Sidebar from "./components/Sidebar";
import EmployeeCard from "./components/EmployeeCard";

function App() {
    return (
        <>
            <Navbar />
            <Sidebar />
            <EmployeeCard />
        </>
    );
}

export default App;
```

Here, we are importing three separate components and displaying them inside the `App` component.

### Understanding main.jsx

The `main.jsx` file is the entry point of our React application. It connects React to the HTML page.

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

const root = createRoot(
    document.getElementById("root")
);

root.render(
    <StrictMode>
        <App />
    </StrictMode>
);
```

**How does it work?**

1. `document.getElementById("root")` finds the HTML element where React will run.
2. `createRoot()` creates a React root inside that element.
3. `render()` displays the `App` component.
4. `StrictMode` helps detect potential issues during development.

### Understanding index.html

The `index.html` file is the main HTML page loaded by the browser.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Employee Dashboard</title>
</head>

<body>
    <div id="root"></div>

    <script type="module" src="/src/main.jsx"></script>
</body>
</html>
```

**How does it work?**

- The browser loads `index.html`.
- The script loads `main.jsx`.
- React finds the element with `id="root"`.
- React renders our application inside that element.

------------------------------------------------------------------------

## 10. Difference Between Class and Functional Components

React provides two ways to create components: Functional Components and Class Components.

### Functional Component

A functional component is a JavaScript function that returns JSX to display the UI.

```jsx
function Welcome() {
    return <h1>Hello React</h1>;
}
```

### Class Component

A class component is created using a JavaScript class that extends `React.Component`. It uses a `render()` method to return JSX.

```jsx
import React from "react";

class Welcome extends React.Component {
    render() {
        return <h1>Hello React</h1>;
    }
}
```

### Difference Between Them

| Functional Component | Class Component |
|---|---|
| Created using functions. | Created using classes. |
| Uses Hooks for state and effects. | Uses state and lifecycle methods. |
| Does not require `this`. | Uses `this` to access props and state. |
| Requires less code. | Usually requires more code. |
| Supports custom Hooks for logic reuse. | Uses class-based patterns. |
| Commonly used in modern React. | Mostly found in older projects. |

**Important:** Functional components can manage state and handle side effects using Hooks, just like class components use state and lifecycle methods.

---

## 11. What are Hooks in React?

Hooks are special functions provided by React that allow functional components to use features like state management, references and effects.

Hooks were introduced in React 16.8 to make it easier to use React features without writing class components.

### Commonly Used React Hooks

| Hook | Purpose |
|---|---|
| `useState` | Stores and updates component state. |
| `useEffect` | Handles synchronisation with external systems. |
| `useRef` | Accesses DOM elements and stores mutable values. |
| `useContext` | Shares data between components. |


### Rules of Hooks

1. Always call Hooks at the top level of a component.
2. Never call Hooks inside loops, conditions or nested functions.
3. Hooks should only be called inside React function components or custom Hooks.

---

## 12. Understanding the useState Hook

`useState` is a React Hook used to store and update data inside a functional component.

Whenever the state changes, React renders the component again to display the updated value.

### Syntax

```jsx
const [state, setState] = useState(initialValue);
```

- `state`: Holds the current value.
- `setState`: Updates the state value.
- `initialValue`: Sets the starting value.

### Example: Counter Application

```jsx
import { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <>
            <h1>Count: {count}</h1>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>

            <button onClick={() => setCount(count - 1)}>
                Decrease
            </button>
        </>
    );
}

export default Counter;
```

### How Does It Work?

1. Initially, the count value is `0`.
2. Clicking Increase calls `setCount()` and increases the value.
3. React updates the state.
4. The component renders again with the updated value.

### Functional State Updates

Sometimes, the new state depends on the previous state. In such cases, we can use a function to calculate the next value.

```jsx
setCount(prev => prev + 1);
```

Here, `prev` represents the previous state value.

**Why use this approach?**

It ensures that state updates are calculated using the latest previous state, especially when multiple updates are scheduled together.

------------------------------------------------------------------------

## 13. `useEffect` Hook

**`useEffect` is used to synchronize a component with external
systems.**

Examples:

-   API calls.
-   Event listeners.
-   Timers.
-   Subscriptions.
-   Updating external browser APIs.

### Syntax

``` jsx
useEffect(() => {
  // Side-effect logic

  return () => {
    // Cleanup logic
  };
}, [dependencies]);
```

### 1. Without a Dependency Array

``` jsx
useEffect(() => {
  console.log("Component rendered");
});
```

Runs after every committed render.

### 2. With an Empty Dependency Array

``` jsx
useEffect(() => {
  console.log("Component mounted");
}, []);
```

Runs after the initial mount. In development, React StrictMode may run
an extra setup and cleanup cycle to help find bugs.

### 3. With Dependencies

``` jsx
useEffect(() => {
  console.log("Count changed");
}, [count]);
```

Runs after the initial mount and when `count` changes.

### Example: API Call

``` jsx
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    async function fetchUsers() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );

      const data = await response.json();
      setUsers(data);
    }

    fetchUsers();
  }, []);

  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}
```

### Cleanup in `useEffect`

Cleanup removes resources when they are no longer needed.

``` jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

Here, `clearInterval()` stops the timer during cleanup.

------------------------------------------------------------------------

## 14. Understanding the useRef Hook

`useRef` is a React Hook that allows us to store values between renders without triggering a re-render when the value changes.

### Common Uses of useRef

1. Accessing HTML elements directly.
2. Storing timer IDs.
3. Remembering previous values.
4. Storing values that don't need to update the UI.

### Syntax

```jsx
const myRef = useRef(initialValue);
```

### Example 1: Accessing a DOM Element

```jsx
import { useRef } from "react";

function App() {
    const inputElement = useRef(null);

    function handleClick() {
        inputElement.current.focus();
    }

    return (
        <>
            <input ref={inputElement} />
            <button onClick={handleClick}>
                Click to Focus
            </button>
        </>
    );
}
```

**How does it work?**

- `useRef(null)` creates a reference.
- We attach that reference to the input using `ref`.
- `inputElement.current` gives us access to the actual input element.
- Calling `focus()` places the cursor inside the input.

### Example 2: Storing the Previous Value

```jsx
import { useEffect, useRef, useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);
    const previousCount = useRef(0);

    useEffect(() => {
        previousCount.current = count;
    }, [count]);

    return (
        <>
            <h2>Current Value: {count}</h2>
            <h2>Previous Value: {previousCount.current}</h2>

            <button onClick={() => setCount(prev => prev + 1)}>
                Increase
            </button>
        </>
    );
}
```

Here, `useRef` remembers the previous count without causing another render when its value changes.

### Difference Between useState and useRef

| useState | useRef |
|---|---|
| Used to manage component state. | Used to store mutable values. |
| Updating state triggers a re-render. | Updating `.current` does not trigger a re-render. |
| Commonly used for UI updates. | Commonly used for DOM access and storing values. |
| Updated using a setter function. | Updated using `.current`. |

---

## 15. How to Pass Data Between Components?

React allows components to communicate with each other in different ways.

### 1. Parent to Child (Using Props)

A parent component can send information to a child component through props.

```jsx
function Child({ username }) {
    return <h2>Welcome, {username}</h2>;
}

function Parent() {
    return <Child username="Rahul" />;
}
```

Here, the parent passes `username` to the child.

### 2. Child to Parent (Using Callback Functions)

A child can send information to its parent by calling a function received through props.

```jsx
function Child({ sendMessage }) {
    return (
        <button onClick={() => sendMessage("Hello from Child")}>
            Send Message
        </button>
    );
}

function Parent() {
    function receiveMessage(message) {
        console.log(message);
    }

    return <Child sendMessage={receiveMessage} />;
}
```

**Output:**

```text
Hello from Child
```

### 3. Communication Between Sibling Components

Sibling components cannot directly share props with each other. Instead, we can use their common parent to exchange data.

```jsx
import { useState } from "react";

function FirstChild({ updateMessage }) {
    return (
        <button onClick={() => updateMessage("Message received!")}>
            Send Message
        </button>
    );
}

function SecondChild({ message }) {
    return <h2>{message}</h2>;
}

function Parent() {
    const [message, setMessage] = useState("");

    return (
        <>
            <FirstChild updateMessage={setMessage} />
            <SecondChild message={message} />
        </>
    );
}
```

Here, the first child updates the state through a function provided by the parent, and the second child displays the updated value.

### 4. Using Context API

Context API allows us to share data across multiple components without passing props through every intermediate component.

It is useful for sharing:

- User authentication details.
- Theme settings (dark/light mode).
- User information.
- Common application data.

---

## 16. What is Lifting State Up?

Lifting State Up means moving state from a child component to its nearest common parent when multiple components need to access or update the same data.

### Example

Suppose we have two components:

- `InputComponent`: Takes a username from the user.
- `DisplayComponent`: Displays the entered username.

Instead of maintaining separate states, we can move the state into their common parent.

```jsx
import { useState } from "react";

function InputComponent({ setUsername }) {
    return (
        <input
            type="text"
            placeholder="Enter username"
            onChange={(e) => setUsername(e.target.value)}
        />
    );
}

function DisplayComponent({ username }) {
    return <h2>Welcome, {username}</h2>;
}

function App() {
    const [username, setUsername] = useState("");

    return (
        <>
            <InputComponent setUsername={setUsername} />
            <DisplayComponent username={username} />
        </>
    );
}

export default App;
```

### How Does It Work?

1. The parent component maintains the username state.
2. The input component updates the state using the function received through props.
3. The parent receives the updated value.
4. The display component receives the new value through props.
5. React updates the displayed username.

### Advantages of Lifting State Up

1. **Single Source of Truth:** Shared data is maintained in one place.
2. **Easy Data Sharing:** Multiple components can access the same state.
3. **Better Synchronisation:** Components display consistent information.
4. **Simpler State Management:** Avoids maintaining duplicate states.

------------------------------------------------------------------------

## 17. How to Handle Events in React Components?

Events allow users to interact with our application. For example, clicking a button, entering text or submitting a form.

React provides built-in event handlers to manage these interactions.

### Common React Events

- `onClick` – Handles button clicks.
- `onChange` – Detects changes in input fields.
- `onSubmit` – Handles form submission.
- `onMouseEnter` – Detects when the mouse enters an element.
- `onKeyDown` – Detects keyboard key presses.
- `onFocus` – Detects when an element receives focus.
- `onBlur` – Detects when an element loses focus.

### 1. onClick Event

Used when a user clicks an element.

```jsx
function App() {
    function handleClick() {
        alert("Button was clicked!");
    }

    return (
        <button onClick={handleClick}>
            Click Me
        </button>
    );
}
```

### 2. onChange Event

Used to track changes in input fields.

```jsx
import { useState } from "react";

function App() {
    const [email, setEmail] = useState("");

    return (
        <>
            <input
                type="email"
                value={email}
                onChange={(e) => setEmail(e.target.value)}
                placeholder="Enter email"
            />

            <p>Email: {email}</p>
        </>
    );
}
```

### 3. onSubmit Event

Used to handle form submissions.

```jsx
function App() {
    function handleSubmit(e) {
        e.preventDefault();
        alert("Form submitted successfully!");
    }

    return (
        <form onSubmit={handleSubmit}>
            <input placeholder="Enter username" />
            <button type="submit">Submit</button>
        </form>
    );
}
```

Here, `preventDefault()` prevents the browser from performing its default form submission behaviour.

### 4. onMouseEnter Event

Triggered when the mouse pointer enters an element.

```jsx
function App() {
    return (
        <div onMouseEnter={() => console.log("Mouse entered!")}>
            Hover over me
        </div>
    );
}
```

### 5. onKeyDown Event

Used to detect keyboard key presses.

```jsx
function App() {
    return (
        <input
            onKeyDown={(e) => console.log("Pressed:", e.key)}
            placeholder="Press any key"
        />
    );
}
```

### React Event Handlers vs JavaScript Event Listeners

In React, we generally handle events using JSX event props like `onClick`, `onChange` and `onSubmit`.

However, sometimes we need to listen to browser events directly, such as window resizing or scrolling.

In such cases, we can use `addEventListener()` inside `useEffect`.

