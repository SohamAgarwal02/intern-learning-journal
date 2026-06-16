# # React Hooks Cheat Sheet

## What are Hooks?

Hooks are special functions introduced in React 16.8 that allow functional components to use React features such as state, lifecycle methods, context, refs, and more.

### Rules of Hooks

1. Only call Hooks at the top level.
2. Only call Hooks from React function components or custom Hooks.
3. Never call Hooks inside loops, conditions, or nested functions.

---

# 1. useState

Used to manage component state.

## Syntax

```jsx
const [state, setState] = useState(initialValue);
```

## Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
}
```

---

# 2. useEffect

Performs side effects such as API calls, subscriptions, timers, etc.

## Syntax

```jsx
useEffect(() => {
  // side effect

  return () => {
    // cleanup
  };
}, [dependencies]);
```

## Example

```jsx
useEffect(() => {
  console.log("Component Mounted");
}, []);
```

### Dependency Cases

```jsx
// Runs after every render
useEffect(() => {});

// Runs once after mount
useEffect(() => {}, []);

// Runs when count changes
useEffect(() => {}, [count]);
```

---

# 3. useContext

Consumes values from React Context without prop drilling.

## Syntax

```jsx
const value = useContext(MyContext);
```

## Example

```jsx
const ThemeContext = createContext();

function Header() {
  const theme = useContext(ThemeContext);

  return <h1>{theme}</h1>;
}
```

---

# 4. useRef

Stores mutable values without causing re-renders.

## Syntax

```jsx
const ref = useRef(initialValue);
```

## Example

```jsx
const inputRef = useRef();

function focusInput() {
  inputRef.current.focus();
}

<input ref={inputRef} />
```

### Uses

- DOM access
- Store previous values
- Store timers/IDs

---

# 5. useMemo

Memoizes expensive calculations.

## Syntax

```jsx
const memoizedValue = useMemo(
  () => computeValue(),
  [dependencies]
);
```

## Example

```jsx
const total = useMemo(() => {
  return items.reduce((a, b) => a + b.price, 0);
}, [items]);
```

---

# 6. useCallback

Memoizes functions.

## Syntax

```jsx
const memoizedFn = useCallback(() => {
  // logic
}, [dependencies]);
```

## Example

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

### Difference

| Hook | Memoizes |
|--------|----------|
| useMemo | Value |
| useCallback | Function |

---

# 7. useReducer

Alternative to useState for complex state logic.

## Syntax

```jsx
const [state, dispatch] = useReducer(
  reducer,
  initialState
);
```

## Example

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    default:
      return state;
  }
}

const [state, dispatch] = useReducer(
  reducer,
  { count: 0 }
);
```

Dispatch:

```jsx
dispatch({ type: "increment" });
```

---

# 8. useLayoutEffect

Runs synchronously after DOM mutations but before painting.

## Syntax

```jsx
useLayoutEffect(() => {
  // DOM measurements
}, []);
```

### Use Cases

- Measure DOM size
- Prevent visual flickering

---

# 9. useImperativeHandle

Customizes instance values exposed via refs.

## Syntax

```jsx
useImperativeHandle(ref, () => ({
  focus() {
    inputRef.current.focus();
  }
}));
```

## Example

```jsx
const CustomInput = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    focus() {
      inputRef.current.focus();
    }
  }));
});
```

---

# 10. useId

Generates unique IDs.

## Syntax

```jsx
const id = useId();
```

## Example

```jsx
const id = useId();

<label htmlFor={id}>Name</label>
<input id={id} />
```

---

# 11. useTransition

Marks state updates as non-urgent.

## Syntax

```jsx
const [isPending, startTransition] =
  useTransition();
```

## Example

```jsx
startTransition(() => {
  setSearchResults(results);
});
```

---

# 12. useDeferredValue

Defers updating a value.

## Syntax

```jsx
const deferredValue =
  useDeferredValue(value);
```

## Example

```jsx
const deferredSearch =
  useDeferredValue(searchText);
```

### Use Case

- Search optimization
- Large lists rendering

---

# 13. useSyncExternalStore

Subscribes to external stores safely.

## Syntax

```jsx
const value = useSyncExternalStore(
  subscribe,
  getSnapshot
);
```

## Example

```jsx
const onlineStatus =
  useSyncExternalStore(
    subscribe,
    getSnapshot
  );
```

---

# 14. useDebugValue

Displays custom labels for custom hooks in React DevTools.

## Syntax

```jsx
useDebugValue(value);
```

## Example

```jsx
function useUser() {
  useDebugValue("User Hook");
}
```

---

# 15. Custom Hooks

Reusable logic built using React Hooks.

## Example

```jsx
function useCounter(initial = 0) {
  const [count, setCount] =
    useState(initial);

  const increment = () =>
    setCount(c => c + 1);

  return { count, increment };
}
```

Usage:

```jsx
const { count, increment } =
  useCounter();
```

---

# Hooks Summary

| Hook | Purpose |
|--------|----------|
| useState | Manage state |
| useEffect | Side effects |
| useContext | Context access |
| useRef | Mutable values / DOM refs |
| useMemo | Memoize values |
| useCallback | Memoize functions |
| useReducer | Complex state |
| useLayoutEffect | DOM measurements |
| useImperativeHandle | Custom ref methods |
| useId | Unique IDs |
| useTransition | Non-urgent updates |
| useDeferredValue | Deferred rendering |
| useSyncExternalStore | External stores |
| useDebugValue | DevTools debugging |
| Custom Hooks | Reusable logic |

---

# Interview Tips

### useState vs useReducer

| useState | useReducer |
|-----------|------------|
| Simple state | Complex state |
| Less boilerplate | More scalable |
| Small components | Large components |

### useEffect vs useLayoutEffect

| useEffect | useLayoutEffect |
|------------|----------------|
| After paint | Before paint |
| Non-blocking | Blocking |
| Most common | DOM measurements |

### useMemo vs useCallback

| useMemo | useCallback |
|----------|------------|
| Returns value | Returns function |
| Optimize calculations | Optimize callbacks |
