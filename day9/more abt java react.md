# React Notes - Props, State & Hooks

## 1. Props in React

### What are Props?

Props (Properties) are used to pass data from a parent component to a child component.

- Props make components reusable.
- Props are passed as attributes.
- Props are read-only (cannot be modified by child components).

### Example

```jsx
function App() {
  return <User name="Krish" age={20} />;
}

function User(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>{props.age}</p>
    </div>
  );
}
```

---

### Passing Different Types of Props

#### String

```jsx
<User name="Krish" />
```

#### Number

```jsx
<User age={20} />
```

#### Boolean

```jsx
<User isLoggedIn={true} />
```

#### Array

```jsx
<User skills={["React", "JavaScript", "CSS"]} />
```

#### Object

```jsx
<User details={{ city: "Kanpur", age: 20 }} />
```

#### Function

```jsx
function greet() {
  alert("Hello");
}

<User sayHello={greet} />
```

---

### Props are Read-Only

❌ Wrong

```jsx
function User(props) {
  props.name = "New Name";
}
```

✅ Correct

Props should only be used to read data.

---

### Props Destructuring

```jsx
function User({ name, age }) {
  return (
    <>
      <h2>{name}</h2>
      <p>{age}</p>
    </>
  );
}
```

---

### Props Flow

```text
Parent Component
       ↓
      Props
       ↓
Child Component
```

Props always flow from Parent → Child.

---

## Props vs State

| Props | State |
|---------|---------|
| Passed from parent | Managed inside component |
| Read-only | Can be updated |
| Used for communication | Used for dynamic data |
| External data | Internal data |

---

# 2. State in React

## What is State?

State is data stored inside a component that can change over time.

Whenever state changes, React re-renders the component.

---

### Why State is Used?

Without state:

```jsx
let count = 0;
```

Updating `count` will not update the UI.

With state:

```jsx
const [count, setCount] = useState(0);
```

Updating state automatically updates the UI.

---

## useState Hook

### Syntax

```jsx
const [state, setState] = useState(initialValue);
```

Example:

```jsx
const [count, setCount] = useState(0);
```

- `count` → current value
- `setCount` → updates value
- `0` → initial value

---

### Example: Counter

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h2>{count}</h2>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
}
```

---

## Updating State Correctly

### Wrong

```jsx
count = count + 1;
```

React won't re-render.

### Correct

```jsx
setCount(count + 1);
```

---

## State with Different Data Types

### String

```jsx
const [name, setName] = useState("Krish");
```

### Number

```jsx
const [age, setAge] = useState(20);
```

### Boolean

```jsx
const [isLoggedIn, setIsLoggedIn] = useState(false);
```

### Array

```jsx
const [skills, setSkills] = useState([
  "HTML",
  "CSS"
]);
```

Add item:

```jsx
setSkills([...skills, "React"]);
```

---

### Object

```jsx
const [user, setUser] = useState({
  name: "Krish",
  age: 20
});
```

Update object:

```jsx
setUser({
  ...user,
  age: 21
});
```

---

## How State Updates UI

```jsx
const [theme, setTheme] = useState("light");
```

When:

```jsx
setTheme("dark");
```

React:

1. Updates state
2. Re-renders component
3. Updates UI

---

# 3. React Hooks

## What are Hooks?

Hooks are special functions that allow functional components to use React features like:

- State
- Lifecycle methods
- Context
- Refs

Before Hooks, these features were mainly available in class components.

---

## Why Hooks Were Introduced?

Problems with Class Components:

- More code
- Hard to understand
- Complex lifecycle methods
- Difficult state management

Hooks provide:

- Cleaner code
- Reusable logic
- Easier state management

---

## Rules of Hooks

### Rule 1

Only call hooks at the top level.

✅ Correct

```jsx
const [count, setCount] = useState(0);
```

❌ Wrong

```jsx
if (true) {
  useState(0);
}
```

---

### Rule 2

Only call hooks inside React components or custom hooks.

✅ Correct

```jsx
function App() {
  useState(0);
}
```

❌ Wrong

```jsx
function test() {
  useState(0);
}
```

---

# useState Hook

Used for managing state.

```jsx
const [count, setCount] = useState(0);
```

Example:

```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h2>{count}</h2>

      <button onClick={() => setCount(count + 1)}>
        Add
      </button>
    </>
  );
}
```

---

# useEffect Hook

Used for handling side effects.

Examples:

- API calls
- Timers
- Event listeners
- DOM updates

---

### Syntax

```jsx
useEffect(() => {
  // code

  return () => {
    // cleanup
  };
}, []);
```

---

### Run Once

```jsx
useEffect(() => {
  console.log("Component Mounted");
}, []);
```

Runs only once.

---

### Run on State Change

```jsx
useEffect(() => {
  console.log("Count changed");
}, [count]);
```

Runs whenever `count` changes.

---

### Cleanup Function

```jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Running");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
```

Used to prevent memory leaks.

---

# Other Common React Hooks

## useRef

Stores values without re-rendering.

Used for:

- Accessing DOM elements
- Persisting values

```jsx
const inputRef = useRef();
```

Example:

```jsx
inputRef.current.focus();
```

---

## useMemo

Memoizes expensive calculations.

```jsx
const result = useMemo(() => {
  return expensiveCalculation(data);
}, [data]);
```

Purpose:

- Improves performance
- Prevents unnecessary recalculations

---

## useCallback

Memoizes functions.

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

Purpose:

- Prevents unnecessary function recreation
- Useful when passing functions to child components

---

## useContext

Used to access global state without prop drilling.

```jsx
const value = useContext(MyContext);
```

Common Uses:

- Theme
- Authentication
- User data

---

## useReducer

Alternative to useState for complex state logic.

```jsx
const [state, dispatch] = useReducer(
  reducer,
  initialState
);
```

Best For:

- Multiple state updates
- Complex applications

---

## useLayoutEffect

Similar to useEffect but runs before browser paint.

```jsx
useLayoutEffect(() => {
  // code
}, []);
```

Used when immediate DOM measurements are required.

---

## useId

Generates unique IDs.

```jsx
const id = useId();
```

Example:

```jsx
<label htmlFor={id}>Name</label>
<input id={id} />
```

Useful for accessibility.

---

# Quick Revision

### Props

- Parent → Child data transfer
- Read-only
- Reusable components

### State

- Internal component data
- Can change
- Triggers re-render

### useState

- Manages state
- Updates UI automatically

### useEffect

- Handles side effects
- API calls
- Timers
- Event listeners

### Other Hooks

| Hook | Purpose |
|--------|---------|
| useRef | DOM access, store values |
| useMemo | Memoize calculations |
| useCallback | Memoize functions |
| useContext | Global state |
| useReducer | Complex state |
| useLayoutEffect | Before paint |
| useId | Unique IDs |

---

## Most Important Interview Question

### Props vs State

| Props | State |
|---------|---------|
| Passed from parent | Managed inside component |
| Immutable | Mutable |
| External data | Internal data |
| Read-only | Can be updated |
| Used for communication | Used for UI updates |
