# Vue Tutorial Project

## 1. Introduction

This project demonstrates a simple Todo application built with Vue 3. It is designed as a beginner-friendly tutorial to help developers understand the core concepts of Vue.

## 2. Why Vue?

Vue is a progressive JavaScript framework that focuses on simplicity and ease of use. Compared to React, Vue uses a template-based syntax, which can be easier for beginners to understand.

## 3. Features

- Add new todos
- Delete existing todos
- Mark todos as completed
- Edit todo text
- Filter todos by All / Active / Completed
- Show remaining active task count
- Persist data using localStorage
- Navigate between pages using Vue Router

## 4. Project Structure

* components/: reusable UI components
* views/: page-level components
* router/: routing configuration

## 5. Key Concepts

### Reactivity

Vue uses reactive state with `ref()`.

### Directives

* v-model: two-way binding
* v-for: list rendering
* v-if: conditional rendering

### Components

The app is split into small reusable components.

### Routing

Vue Router is used to manage multiple pages.

## 6. React vs Vue

| Feature    | Vue      | React         |
| ---------- | -------- | ------------- |
| Syntax     | Template | JSX           |
| State      | ref()    | useState      |
| Binding    | Two-way  | One-way       |
| Complexity | Simpler  | More flexible |

In React, developers need to manually manage state updates and event handling.  
In Vue, features like v-model simplify two-way data binding.

Vue's template syntax is closer to HTML, making it more beginner-friendly,  
while React’s JSX provides more flexibility but has a steeper learning curve.

## 7. Setup Instructions

```bash
npm install
npm run dev
```

## 8. Conclusion

Vue provides a simple and intuitive way to build modern web applications, especially for beginners.

## 9. Design Decisions
- Why using component-based structure
- Why using localStorage instead of backend
- Why Vue instead of React

## 10. Challenges
- Understanding reactivity
- Handling component communication
- Debugging issues

## 11. Limitations and Future Work
- Could integrate backend API
- Could use Pinia for state management
- Could add authentication