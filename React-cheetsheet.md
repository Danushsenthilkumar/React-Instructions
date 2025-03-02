# 📘 React Cheat Sheet

## 🏁 Getting Started

**Install React:**
```bash
# Using create-react-app
npx create-react-app my-app
cd my-app
npm start
```

**Basic Component:**
```jsx
function App() {
  return <h1>Hello, World!</h1>;
}
export default App;
```

---

## ⚛️ Components

### Functional Components
```jsx
function Greeting() {
  return <p>Hello!</p>;
}
```

### Class Components (Less common now)
```jsx
import React, { Component } from 'react';
class Greeting extends Component {
  render() {
    return <p>Hello!</p>;
  }
}
```

---

## 📦 Props

### Passing Props
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Welcome name="Alice" />;
}
```

### Destructuring Props
```jsx
function Welcome({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

---

## 🎯 State

### useState Hook
```jsx
import React, { useState } from 'react';

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

### Updating State with Previous State
```jsx
<button onClick={() => setCount(prevCount => prevCount + 1)}>Increment</button>
```

---

## 🔄 Lifecycle (with useEffect)

### useEffect Hook
```jsx
import React, { useState, useEffect } from 'react';

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(data => setUsers(data))
      .catch(error => console.error('Error:', error));
  }, []); // Runs only on mount

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  );
}
```

**Dependencies:**
- `[]`: Runs only on mount (componentDidMount)
- `[count]`: Runs when `count` changes (componentDidUpdate)
- No array: Runs on every render

---

## 🔍 Conditional Rendering

### Using Ternary Operator
```jsx
function Message({ isLoggedIn }) {
  return isLoggedIn ? <h1>Welcome!</h1> : <h1>Please log in.</h1>;
}
```

### Using &&
```jsx
function Message({ isLoggedIn }) {
  return isLoggedIn && <h1>Welcome!</h1>;
}
```

---

## 📋 Lists and Keys

### Rendering Lists
```jsx
function UsersList() {
  const users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" }
  ];

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

### Index as Key (Anti-pattern)
Avoid using array indices as keys unless necessary.
```jsx
<li key={index}>{user.name}</li>
```

---

## 🌉 Forms and Controlled Components

```jsx
import React, { useState } from 'react';

function Form() {
  const [name, setName] = useState('');

  return (
    <form>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>Your name is: {name}</p>
    </form>
  );
}
```

---

## 📦 Refs

```jsx
import React, { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}
```

---

## 🚪 Portals

Render a component outside its parent DOM tree.
```jsx
ReactDOM.createPortal(
  <Modal />,
  document.getElementById('modal-root')
);
```

---

## 🎩 Higher-Order Components (HOC)

```jsx
const withAuth = (WrappedComponent) => {
  return (props) => {
    if (!props.isAuthenticated) {
      return <p>Please log in to continue.</p>;
    }
    return <WrappedComponent {...props} />;
  };
};
```

**Usage:**
```jsx
const SecretPage = (props) => <h1>Secret Info</h1>;
const ProtectedPage = withAuth(SecretPage);
```

---

## 🔄 Render Props

```jsx
const DataFetcher = ({ render }) => {
  const data = "Hello from DataFetcher";
  return render(data);
};

function App() {
  return (
    <DataFetcher render={(data) => <p>{data}</p>} />
  );
}
```

---

## 🔥 React.memo

```jsx
const Greeting = React.memo(({ name }) => {
  console.log("Greeting component re-rendered!");
  return <h1>Hello, {name}!</h1>;
});
```

---

## 🌐 Context API

### Creating Context
```jsx
const ThemeContext = React.createContext('light');
```

### Providing Context
```jsx
<ThemeContext.Provider value="dark">
  <App />
</ThemeContext.Provider>
```

### Consuming Context
```jsx
const theme = useContext(ThemeContext);
```

---

## 🚀 HTTP Requests

### Fetching Data
```jsx
useEffect(() => {
  fetch('https://jsonplaceholder.typicode.com/users')
    .then(response => response.json())
    .then(data => setUsers(data));
}, []);
```

### POST Request
```jsx
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ title: 'foo', body: 'bar', userId: 1 })
});
```

---

## 🏎️ React with TypeScript

```tsx
interface Props {
  name: string;
}

const Greeting: React.FC<Props> = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};
```

---

This cheat sheet captures the core concepts of React. Let me know if you'd like me to add anything more specific!


