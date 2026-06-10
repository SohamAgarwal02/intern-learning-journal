# React Concepts Learned

## React Fundamentals

### React

React is a JavaScript library used to build user interfaces using reusable components.

### SPA (Single Page Application)

A web application that loads a single page and updates content dynamically without reloading the entire page.

### Virtual DOM

A lightweight copy of the real DOM that helps React update the UI efficiently.

### React vs Vanilla JavaScript

* Vanilla JavaScript: Manual DOM manipulation
* React: Automatic UI updates using components and state

---

## Project Setup

### Vite

A fast build tool used to create React applications.

```bash
npm create vite@latest .
```

### App.jsx

The main/root component of a React application.

### main.jsx

The entry point that renders the React application to the browser.

---

## JSX

### What is JSX?

JSX (JavaScript XML) allows writing HTML-like syntax inside JavaScript.

```jsx
<h1>Hello React</h1>
```

### Embedding JavaScript in JSX

```jsx
<h1>{name}</h1>
```

### Expressions in JSX

```jsx
<p>{10 + 5}</p>
```

### className

```jsx
<div className="container"></div>
```

React uses `className` instead of `class`.

### Self-Closing Tags

```jsx
<img />
<input />
<br />
```

---

## Components

### Component

A reusable piece of UI.

```jsx
function Card() {
  return <h2>Hello</h2>;
}
```

### Functional Component

A JavaScript function that returns JSX.

### Naming Convention

```jsx
function ProfileCard() {}
```

Component names should start with a capital letter.

### Exporting Components

```jsx
export default ProfileCard;
```

### Importing Components

```jsx
import ProfileCard from "./ProfileCard";
```

### Component Hierarchy

```text
App
├── Navbar
├── ProfileCard
└── Footer
```

---

## Reusable Components

A component can be used multiple times.

```jsx
<Card />
<Card />
<Card />
```

Benefits:

* Reusability
* Less code duplication
* Easier maintenance

---

## Props

Props are used to pass data from a parent component to a child component.

### Passing Props

```jsx
<MemberCard
  name="Vansh"
  role="Frontend"
  experience="1 Year"
/>
```

### Receiving Props

```jsx
function MemberCard(props) {
  return <h2>{props.name}</h2>;
}
```

Benefits:

* Dynamic content
* Reusable components
* Better code organization

---

## CSS in React

### Import CSS

```jsx
import "./ProfileCard.css";
```

### Apply CSS

```jsx
<div className="profile-card">
```

Example:

```css
.profile-card {
  border: 1px solid black;
}
```

---

## Images in React

### Import Image

```jsx
import heroImg from "../assets/hero.png";
```

### Use Image

```jsx
<img src={heroImg} alt="Profile" />
```

---

## Projects Completed

### Profile Card Project

Concepts Used:

* React Application Setup
* JSX
* Functional Components
* CSS Styling
* Image Import
* Component Import/Export

### Member Card Project

Concepts Used:

* Reusable Components
* Props
* Multiple Component Instances
* Dynamic Data Rendering

---

## Key Concepts Summary

1. React
2. SPA
3. Virtual DOM
4. JSX
5. Components
6. Functional Components
7. Props
8. Import & Export
9. className
10. Self-Closing Tags
11. CSS Styling
12. Image Import
13. Reusable Components
14. Component Hierarchy
15. Vite Setup

