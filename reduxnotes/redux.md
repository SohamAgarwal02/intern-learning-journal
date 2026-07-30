# Redux Toolkit Notes (React)

> 📌 Beginner-friendly notes for React + Redux Toolkit

---

# What is Redux?

Redux is a **state management library** used to manage and share data across different components in a React application.

Without Redux:
- Data is passed using props.
- Prop drilling becomes difficult in large applications.

With Redux:
- Data is stored in one central place called the **Store**.
- Any component can access or update the data.

---

# Why Redux Toolkit?

Redux Toolkit (RTK) is the official and recommended way to write Redux.

Advantages:
- Less code
- Easier to understand
- Built-in best practices
- Includes Redux DevTools support
- Uses Immer internally

---

# Installation

```bash
npm install @reduxjs/toolkit react-redux
```

---

# Folder Structure

```
src/
│
├── app/
│   └── store.js
│
├── features/
│   └── counter/
│       └── counterSlice.js
│
├── components/
│   └── Counter.jsx
│
├── App.jsx
└── main.jsx
```

---

# Redux Flow

```
Component
    │
dispatch(action)
    │
    ▼
Reducer (Slice)
    │
Updates State
    │
    ▼
Store
    │
useSelector()
    │
    ▼
Component Re-renders
```

---

# Important Terms

## Store

The central place where all application state is stored.

Example:

```js
const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

---

## Slice

A Slice contains:

- Initial State
- Reducers
- Actions

Example:

```js
const counterSlice = createSlice({
  name: "counter",
  initialState: {
    value: 0,
  },
  reducers: {
    increment: (state) => {
      state.value++;
    },
  },
});
```

---

## Reducer

Reducer updates the state.

Example

```js
increment: (state) => {
    state.value++;
}
```

---

## Action

Action tells Redux what needs to happen.

Example

```js
dispatch(increment())
```

---

## Dispatch

Dispatch sends an action to Redux.

```js
dispatch(increment())
```

---

## Selector

Selector reads data from the store.

```js
const count = useSelector((state) => state.counter.value);
```

---

# Step 1: Create Store

```js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "../features/counter/counterSlice";

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

---

# Step 2: Create Slice

```js
import { createSlice } from "@reduxjs/toolkit";

const initialState = {
  value: 0,
};

const counterSlice = createSlice({
  name: "counter",
  initialState,
  reducers: {
    increment: (state) => {
      state.value++;
    },

    decrement: (state) => {
      state.value--;
    },

    reset: (state) => {
      state.value = 0;
    },
  },
});

export const { increment, decrement, reset } = counterSlice.actions;

export default counterSlice.reducer;
```

---

# Step 3: Provide Store

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";
import { store } from "./app/store";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

---

# Step 4: Use Redux

```jsx
import { useSelector, useDispatch } from "react-redux";
import { increment, decrement, reset } from "./counterSlice";

function Counter() {
  const count = useSelector((state) => state.counter.value);

  const dispatch = useDispatch();

  return (
    <>
      <h1>{count}</h1>

      <button onClick={() => dispatch(increment())}>
        +
      </button>

      <button onClick={() => dispatch(decrement())}>
        -
      </button>

      <button onClick={() => dispatch(reset())}>
        Reset
      </button>
    </>
  );
}

export default Counter;
```

---

# Hooks Used

## useSelector()

Used to read data from Redux Store.

```js
const count = useSelector((state) => state.counter.value);
```

---

## useDispatch()

Used to send actions.

```js
const dispatch = useDispatch();
```

---

# createSlice()

Creates:

- State
- Reducers
- Actions

```js
createSlice({
    name,
    initialState,
    reducers
})
```

---

# configureStore()

Creates Redux Store.

```js
configureStore({
    reducer:{
        counter:counterReducer
    }
})
```

---

# Initial State

Default state stored initially.

```js
const initialState = {
    value:0
}
```

---

# Multiple Reducers

```js
configureStore({
    reducer:{
        counter:counterReducer,
        user:userReducer,
        todo:todoReducer
    }
})
```

---

# Payload

Payload sends extra data.

```js
addByAmount: (state, action) => {
    state.value += action.payload;
}
```

Dispatch

```js
dispatch(addByAmount(10))
```

---

# Async Redux (Thunk)

Redux Toolkit includes Redux Thunk.

Example

```js
export const fetchUsers = createAsyncThunk(
    "users/fetchUsers",
    async () => {
        const response = await fetch(url);
        return response.json();
    }
);
```

---

# Redux DevTools

Install browser extension.

Automatically works with Redux Toolkit.

Helps to

- Inspect State
- View Actions
- Debug

---

# Data Flow

```
Button Click
      │
dispatch(action)
      │
Reducer
      │
State Updated
      │
Store
      │
useSelector
      │
Component Re-render
```

---

# Common Interview Questions

### What is Redux?

Redux is a state management library used to manage global state in React applications.

---

### Why Redux Toolkit?

- Less boilerplate
- Easier syntax
- Better performance
- Official Redux approach

---

### Difference between Redux and Context API?

| Redux | Context API |
|--------|-------------|
| Global state management | Data sharing |
| Better for large apps | Better for small apps |
| DevTools support | No DevTools |
| Middleware support | No middleware |

---

### What is Store?

Central storage of application state.

---

### What is Slice?

A collection of state, reducers, and actions.

---

### What is Reducer?

Function that updates the state.

---

### What is Action?

An object describing what should happen.

---

### What is Dispatch?

Sends actions to the Redux store.

---

### What is Payload?

Extra data passed with an action.

---

### What is useSelector?

Reads data from the Redux store.

---

### What is useDispatch?

Sends actions to update the Redux store.

---

# Best Practices

- Keep state minimal.
- Use Redux Toolkit instead of plain Redux.
- Create separate slices for different features.
- Avoid mutating state manually (Immer handles immutable updates).
- Use `useSelector` only where needed.
- Organize slices inside the `features/` folder.

---

# Summary

- Redux manages global state.
- Redux Toolkit simplifies Redux development.
- Store holds the application state.
- Slice contains state, reducers, and actions.
- Reducers update the state.
- Actions describe what happened.
- Dispatch sends actions.
- useSelector reads data.
- useDispatch updates data.
- Redux Toolkit uses Immer for easier state updates.
- Redux DevTools help debug state changes.

---

⭐ These notes are ideal for React beginners, interview preparation, and quick GitHub revision.
