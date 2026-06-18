# FAQ Accordion

A reusable FAQ Accordion built using React.

## Features

* Expand and collapse FAQ answers
* Reusable Accordion component
* Dynamic rendering using `map()`
* Clean and simple UI
* Built with React Hooks

## Concepts Covered

### Components

The project is divided into reusable components:

* FAQ
* FAQItem

### Props

Props are used to pass data from parent to child components.

```jsx
<FAQItem
  question={faq.question}
  answer={faq.answer}
/>
```

### State (useState)

The `useState` hook is used to manage the open/close state of each FAQ item.

```jsx
const [open, setOpen] = useState(false);
```

### Conditional Rendering

Answers are displayed only when the corresponding question is expanded.

```jsx
{open && <p>{answer}</p>}
```

### Event Handling

The `onClick` event is used to toggle the answer visibility.

```jsx
onClick={() => setOpen(!open)}
```

### Reusability

A single `FAQItem` component is reused for multiple questions.

### Component Hierarchy

```text
App
 └── FAQ
      └── FAQItem
```

## Learning Outcomes

Through this project, I learned:

* React Components
* Props
* useState Hook
* Conditional Rendering
* Event Handling
* Component Reusability
* Component Hierarchy
* Dynamic Rendering using map()

## Technologies Used

* React
* JavaScript (ES6+)
* CSS
* Vite
