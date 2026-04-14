# Vue Tutorial Project

## 1. Introduction

This project demonstrates a Todo application built with Vue 3.
The goal is to provide a beginner-friendly tutorial that explains how to build a small but complete application using core Vue features.

The project focuses on practical concepts such as component-based architecture, reactivity, and basic state management.

---

## 2. Why Vue?

Vue is a progressive JavaScript framework designed to be approachable and easy to integrate.

Compared to React, Vue provides a template-based syntax that separates structure and logic more clearly. This makes it easier for beginners to understand how the UI is connected to the data.

In this project, Vue was chosen to explore how quickly a functional application can be built with minimal setup and clear structure.

---

## 3. Features

* Add new todos
* Delete existing todos
* Mark todos as completed
* Edit todo text
* Filter todos by All / Active / Completed
* Show remaining active task count
* Persist data using localStorage
* Navigate between pages using Vue Router

---

## 4. Project Structure

* `components/` – reusable UI components (TodoInput, TodoList, TodoItem)
* `views/` – page-level components (HomeView, AboutView)
* `router/` – routing configuration
* `App.vue` – root component

This structure follows a common Vue project pattern, separating reusable logic from page-level views.

---

## 5. Key Concepts

### Reactivity

Vue uses a reactive system based on `ref()`.
When the state changes, the UI updates automatically without manually manipulating the DOM.

### Directives

Vue provides built-in directives to simplify UI logic:

* `v-model` → two-way data binding between input and state
* `v-for` → rendering lists dynamically
* `v-if` → conditional rendering

These directives reduce the amount of boilerplate code needed.

### Components

The application is split into small reusable components:

* Input handling (TodoInput)
* List rendering (TodoList)
* Individual item logic (TodoItem)

This improves readability and maintainability.

### Routing

Vue Router is used to manage multiple pages in a single-page application (SPA).
It allows navigation between the main Todo page and an additional About page.

---

## 6. React vs Vue

| Feature    | Vue      | React         |
| ---------- | -------- | ------------- |
| Syntax     | Template | JSX           |
| State      | ref()    | useState      |
| Binding    | Two-way  | One-way       |
| Complexity | Simpler  | More flexible |

In React, developers typically manage state updates and event handling manually.
In Vue, features like `v-model` simplify data binding by automatically syncing input values with state.

Vue’s template syntax is closer to HTML, which can be easier for beginners to read.
React’s JSX combines logic and UI, offering more flexibility but requiring a deeper understanding of JavaScript.

---

## 7. Setup Instructions

Clone the repository and install dependencies:

```bash
npm install
npm run dev
```

Then open the local development server in your browser.

---

## 8. Design Decisions

### Component-based structure

The application is divided into small components to separate concerns and improve code reuse.
Each component has a clear responsibility, making the project easier to understand and extend.

### Using localStorage

Instead of connecting to a backend, localStorage is used to persist data.
This keeps the project simple while still demonstrating real-world behavior (data persistence).

### Choosing Vue

Vue was selected because of its simplicity and clear syntax.
It allows rapid development of small applications without requiring complex configuration.

---

## 9. Challenges

### Understanding reactivity

At the beginning, it was not immediately clear how `ref()` works and why `.value` is needed.
This required some experimentation to understand how Vue tracks changes.

### Component communication

Passing data between components using props and emitting events required careful structuring.
This became more complex when adding editing functionality.

### Debugging state updates

Managing multiple states (editing, completed, filtering) introduced bugs that needed debugging.
Using Vue DevTools helped identify and fix these issues.

---

## 10. Limitations and Future Work

* The project currently uses localStorage instead of a real backend API
* State management is handled locally and could be improved using Pinia
* No authentication or user system is implemented
* UI design is minimal and could be improved with a component library

Future improvements could include integrating a backend service and expanding the application into a full-stack project.

---

## 11. Conclusion

This project demonstrates how Vue can be used to quickly build a functional application with clear structure and minimal complexity.

It highlights Vue’s strengths in simplicity, readability, and rapid development, especially for developers who are new to frontend frameworks.
