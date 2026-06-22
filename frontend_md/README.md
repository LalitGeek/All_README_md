# ⚛️ React.js — Beginner to Expert Guide

> A complete, production-ready reference for building modern React applications.  
> **Author:** Lalit Tomer · **Organization:** Popup Core Technology

---

## 📋 Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Project Setup](#project-setup)
4. [Project Structure](#project-structure)
5. [Core Concepts — Beginner](#core-concepts--beginner)
   - [JSX](#jsx)
   - [Components](#components)
   - [Props](#props)
   - [State with useState](#state-with-usestate)
   - [Event Handling](#event-handling)
   - [Conditional Rendering](#conditional-rendering)
   - [Lists and Keys](#lists-and-keys)
6. [Intermediate Concepts](#intermediate-concepts)
   - [useEffect Hook](#useeffect-hook)
   - [useRef Hook](#useref-hook)
   - [Custom Hooks](#custom-hooks)
   - [Context API](#context-api)
   - [React Router](#react-router)
   - [Forms and Controlled Inputs](#forms-and-controlled-inputs)
   - [Component Lifecycle](#component-lifecycle)
7. [Advanced Concepts](#advanced-concepts)
   - [useReducer Hook](#usereducer-hook)
   - [useMemo and useCallback](#usememo-and-usecallback)
   - [Code Splitting and Lazy Loading](#code-splitting-and-lazy-loading)
   - [Error Boundaries](#error-boundaries)
   - [Portals](#portals)
   - [Forwarding Refs](#forwarding-refs)
8. [Expert Level](#expert-level)
   - [State Management with Redux Toolkit](#state-management-with-redux-toolkit)
   - [React Query (TanStack Query)](#react-query-tanstack-query)
   - [Performance Optimization](#performance-optimization)
   - [Testing](#testing)
   - [Server-Side Rendering with Next.js](#server-side-rendering-with-nextjs)
9. [Project Architecture & Best Practices](#project-architecture--best-practices)
10. [Useful Commands](#useful-commands)
11. [Recommended VS Code Extensions](#recommended-vs-code-extensions)
12. [Resources](#resources)

---

## Introduction

React.js is a **declarative, component-based JavaScript library** developed by Meta for building fast and interactive user interfaces. It uses a Virtual DOM to efficiently update only the parts of the UI that change.

**Why React?**
- Component reusability reduces code duplication
- Unidirectional data flow makes debugging predictable
- Massive ecosystem and community support
- Powers large-scale apps at Facebook, Netflix, Airbnb, and more

---

## Prerequisites

Before starting, ensure the following are installed:

| Tool | Minimum Version | Check Command |
|------|----------------|---------------|
| Node.js (LTS) | 18.x+ | `node -v` |
| npm | 9.x+ | `npm -v` |
| Git | Any | `git --version` |

```bash
# Verify your environment
node -v    # e.g., v20.11.0
npm -v     # e.g., 10.2.4
```

---

## Project Setup

### Using Vite (Recommended)

Vite offers blazing-fast HMR (Hot Module Replacement) and modern build tooling.

```bash
# Create a new React project
npm create vite@latest my-react-app -- --template react

# Navigate into the project
cd my-react-app

# Install dependencies
npm install

# Start development server
npm run dev
```

Your app will be live at: **http://localhost:5173**

### Using Create React App (Alternative)

```bash
npx create-react-app my-app
cd my-app
npm start
```

> ⚠️ CRA is no longer actively maintained. Vite is strongly preferred for new projects.

---

## Project Structure

```
my-react-app/
├── public/                   # Static assets served as-is
├── src/
│   ├── assets/               # Images, fonts, icons
│   ├── components/           # Reusable UI components
│   │   ├── common/           # Shared elements (Button, Input, Modal)
│   │   └── layout/           # Header, Footer, Sidebar
│   ├── pages/                # Page-level components
│   ├── hooks/                # Custom React hooks
│   ├── context/              # React Context providers
│   ├── services/             # API calls (axios, fetch)
│   ├── store/                # Redux / Zustand state (advanced)
│   ├── utils/                # Helper functions
│   ├── App.jsx               # Root component
│   ├── main.jsx              # Entry point
│   └── index.css             # Global styles
├── .env                      # Environment variables (never commit)
├── .gitignore
├── package.json
├── vite.config.js
└── README.md
```

---

## Core Concepts — Beginner

### JSX

JSX (JavaScript XML) lets you write HTML-like syntax inside JavaScript. Babel compiles it to `React.createElement()` calls under the hood.

```jsx
// JSX
const element = <h1 className="title">Hello, World!</h1>;

// What JSX compiles to
const element = React.createElement('h1', { className: 'title' }, 'Hello, World!');
```

**JSX Rules:**
- Every component must return a **single root element** (use `<>...</>` Fragment if needed)
- Use `className` instead of `class`
- Self-close tags: `<img />`, `<br />`
- JavaScript expressions go inside `{}`

```jsx
const name = "Lalit";
const element = <p>Hello, {name}! Today is {new Date().toDateString()}</p>;
```

---

### Components

Components are the **building blocks** of React. They are reusable, self-contained pieces of UI.

```jsx
// Functional Component (recommended)
function Greeting({ name }) {
  return <h2>Welcome, {name}!</h2>;
}

export default Greeting;
```

```jsx
// Arrow function style (also common)
const Greeting = ({ name }) => <h2>Welcome, {name}!</h2>;

export default Greeting;
```

---

### Props

Props (properties) are how parent components **pass data down** to child components. They are read-only.

```jsx
// Parent
function App() {
  return <UserCard name="Lalit Tomer" role="CEO" company="Popup Core Technology" />;
}

// Child
function UserCard({ name, role, company }) {
  return (
    <div className="card">
      <h3>{name}</h3>
      <p>{role} at {company}</p>
    </div>
  );
}
```

**Default Props:**
```jsx
function Button({ label = "Click Me", variant = "primary" }) {
  return <button className={variant}>{label}</button>;
}
```

---

### State with useState

`useState` lets you add **reactive state** to functional components. When state changes, React re-renders the component.

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

> 💡 Always use the setter function — **never mutate state directly**.

---

### Event Handling

```jsx
function Form() {
  const [value, setValue] = useState("");

  const handleChange = (e) => setValue(e.target.value);

  const handleSubmit = (e) => {
    e.preventDefault(); // Prevent page reload
    alert(`Submitted: ${value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={value} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

### Conditional Rendering

```jsx
function Notification({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in.</p>}

      {/* Render only if true */}
      {isLoggedIn && <button>Logout</button>}
    </div>
  );
}
```

---

### Lists and Keys

Always provide a **stable, unique `key`** when rendering lists so React can track changes efficiently.

```jsx
const projects = [
  { id: 1, name: "VideoVault" },
  { id: 2, name: "Antigravity" },
  { id: 3, name: "Roop Rang Studio" },
];

function ProjectList() {
  return (
    <ul>
      {projects.map((project) => (
        <li key={project.id}>{project.name}</li>
      ))}
    </ul>
  );
}
```

> ⚠️ Avoid using array index as key when the list can be reordered or filtered.

---

## Intermediate Concepts

### useEffect Hook

`useEffect` handles **side effects**: API calls, subscriptions, DOM manipulation, timers.

```jsx
import { useState, useEffect } from "react";

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // Runs after every render where userId changes
    setLoading(true);
    fetch(`https://api.example.com/users/${userId}`)
      .then((res) => res.json())
      .then((data) => {
        setUser(data);
        setLoading(false);
      });

    // Cleanup function (runs before next effect or unmount)
    return () => {
      console.log("Cleanup: cancelling request");
    };
  }, [userId]); // Dependency array

  if (loading) return <p>Loading...</p>;
  return <p>{user?.name}</p>;
}
```

**Dependency Array Rules:**
| Pattern | Behavior |
|---------|----------|
| `useEffect(() => {})` | Runs after every render |
| `useEffect(() => {}, [])` | Runs once on mount |
| `useEffect(() => {}, [id])` | Runs when `id` changes |

---

### useRef Hook

`useRef` gives you a **mutable reference** that persists across renders without causing re-renders. Commonly used to access DOM nodes.

```jsx
import { useRef } from "react";

function SearchInput() {
  const inputRef = useRef(null);

  const focusInput = () => inputRef.current.focus();

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Search..." />
      <button onClick={focusInput}>Focus</button>
    </div>
  );
}
```

---

### Custom Hooks

Extract reusable stateful logic into custom hooks (functions starting with `use`).

```jsx
// hooks/useFetch.js
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData)
      .catch(setError)
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}

export default useFetch;
```

```jsx
// Usage
import useFetch from "./hooks/useFetch";

function Posts() {
  const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/posts");

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;
  return <ul>{data.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
}
```

---

### Context API

Share data globally across components **without prop drilling**.

```jsx
// context/ThemeContext.js
import { createContext, useContext, useState } from "react";

const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");
  const toggle = () => setTheme((t) => (t === "light" ? "dark" : "light"));

  return (
    <ThemeContext.Provider value={{ theme, toggle }}>
      {children}
    </ThemeContext.Provider>
  );
}

export const useTheme = () => useContext(ThemeContext);
```

```jsx
// App.jsx
import { ThemeProvider } from "./context/ThemeContext";

function App() {
  return (
    <ThemeProvider>
      <Navbar />
      <Main />
    </ThemeProvider>
  );
}

// Any nested component
function Navbar() {
  const { theme, toggle } = useTheme();
  return (
    <nav className={theme}>
      <button onClick={toggle}>Toggle Theme</button>
    </nav>
  );
}
```

---

### React Router

Install React Router for client-side navigation:

```bash
npm install react-router-dom
```

```jsx
// App.jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import ProjectDetail from "./pages/ProjectDetail";
import NotFound from "./pages/NotFound";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/projects/:id" element={<ProjectDetail />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```

```jsx
// Programmatic navigation
import { useNavigate, useParams } from "react-router-dom";

function ProjectDetail() {
  const { id } = useParams();
  const navigate = useNavigate();

  return (
    <div>
      <h2>Project #{id}</h2>
      <button onClick={() => navigate(-1)}>Go Back</button>
    </div>
  );
}
```

---

### Forms and Controlled Inputs

```jsx
import { useState } from "react";

function ContactForm() {
  const [form, setForm] = useState({ name: "", email: "", message: "" });
  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const validate = () => {
    const errs = {};
    if (!form.name) errs.name = "Name is required";
    if (!form.email.includes("@")) errs.email = "Invalid email";
    return errs;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const errs = validate();
    if (Object.keys(errs).length > 0) {
      setErrors(errs);
    } else {
      console.log("Form submitted:", form);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input name="name" value={form.name} onChange={handleChange} placeholder="Name" />
      {errors.name && <span className="error">{errors.name}</span>}

      <input name="email" value={form.email} onChange={handleChange} placeholder="Email" />
      {errors.email && <span className="error">{errors.email}</span>}

      <textarea name="message" value={form.message} onChange={handleChange} />
      <button type="submit">Send</button>
    </form>
  );
}
```

---

### Component Lifecycle

In functional components, the lifecycle maps to `useEffect`:

| Class Lifecycle | Functional Equivalent |
|----------------|----------------------|
| `componentDidMount` | `useEffect(() => {}, [])` |
| `componentDidUpdate` | `useEffect(() => {}, [dep])` |
| `componentWillUnmount` | `return () => {}` inside useEffect |

---

## Advanced Concepts

### useReducer Hook

For **complex state logic** with multiple sub-values, use `useReducer` instead of `useState`.

```jsx
import { useReducer } from "react";

const initialState = { count: 0, step: 1 };

function reducer(state, action) {
  switch (action.type) {
    case "INCREMENT": return { ...state, count: state.count + state.step };
    case "DECREMENT": return { ...state, count: state.count - state.step };
    case "SET_STEP":  return { ...state, step: action.payload };
    case "RESET":     return initialState;
    default: throw new Error(`Unknown action: ${action.type}`);
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count} (step: {state.step})</p>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>+</button>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>-</button>
      <input
        type="number"
        value={state.step}
        onChange={(e) => dispatch({ type: "SET_STEP", payload: Number(e.target.value) })}
      />
      <button onClick={() => dispatch({ type: "RESET" })}>Reset</button>
    </div>
  );
}
```

---

### useMemo and useCallback

Prevent expensive recalculations and unnecessary re-renders with memoization.

```jsx
import { useMemo, useCallback, useState } from "react";

function DataGrid({ data }) {
  const [filter, setFilter] = useState("");

  // useMemo: memoize expensive computation
  const filteredData = useMemo(
    () => data.filter((item) => item.name.includes(filter)),
    [data, filter]
  );

  // useCallback: memoize a function reference
  const handleSort = useCallback((key) => {
    console.log("Sorting by:", key);
  }, []); // Empty deps: function never recreated

  return (
    <>
      <input value={filter} onChange={(e) => setFilter(e.target.value)} />
      {filteredData.map((item) => (
        <Row key={item.id} item={item} onSort={handleSort} />
      ))}
    </>
  );
}
```

> 💡 Don't over-optimize. Only use `useMemo`/`useCallback` when there's a measured performance problem.

---

### Code Splitting and Lazy Loading

Split your bundle to load components only when needed, improving initial load time.

```jsx
import { Suspense, lazy } from "react";
import { Routes, Route } from "react-router-dom";

// Instead of: import Dashboard from "./pages/Dashboard"
const Dashboard = lazy(() => import("./pages/Dashboard"));
const Settings = lazy(() => import("./pages/Settings"));
const Analytics = lazy(() => import("./pages/Analytics"));

function App() {
  return (
    <Suspense fallback={<div className="spinner">Loading...</div>}>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />} />
        <Route path="/settings" element={<Settings />} />
        <Route path="/analytics" element={<Analytics />} />
      </Routes>
    </Suspense>
  );
}
```

---

### Error Boundaries

Catch JavaScript errors in the component tree and show a fallback UI. Must be a class component.

```jsx
import { Component } from "react";

class ErrorBoundary extends Component {
  state = { hasError: false, error: null };

  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }

  componentDidCatch(error, info) {
    console.error("ErrorBoundary caught:", error, info);
  }

  render() {
    if (this.state.hasError) {
      return (
        <div className="error-page">
          <h2>Something went wrong.</h2>
          <p>{this.state.error?.message}</p>
          <button onClick={() => this.setState({ hasError: false })}>Try Again</button>
        </div>
      );
    }
    return this.props.children;
  }
}

// Usage
function App() {
  return (
    <ErrorBoundary>
      <Dashboard />
    </ErrorBoundary>
  );
}
```

---

### Portals

Render a component **outside its parent DOM hierarchy** — useful for modals, tooltips, and overlays.

```jsx
import { createPortal } from "react-dom";

function Modal({ isOpen, onClose, children }) {
  if (!isOpen) return null;

  return createPortal(
    <div className="modal-overlay" onClick={onClose}>
      <div className="modal-content" onClick={(e) => e.stopPropagation()}>
        <button className="close-btn" onClick={onClose}>✕</button>
        {children}
      </div>
    </div>,
    document.getElementById("modal-root") // Render into this DOM node
  );
}
```

```html
<!-- index.html -->
<body>
  <div id="root"></div>
  <div id="modal-root"></div>  <!-- Add this -->
</body>
```

---

### Forwarding Refs

Pass a `ref` through a component to a DOM node inside it.

```jsx
import { forwardRef, useRef } from "react";

const TextInput = forwardRef(({ label, ...props }, ref) => (
  <div className="input-group">
    <label>{label}</label>
    <input ref={ref} {...props} />
  </div>
));

function App() {
  const inputRef = useRef(null);

  return (
    <div>
      <TextInput label="Username" ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
}
```

---

## Expert Level

### State Management with Redux Toolkit

For large apps with **complex global state**, Redux Toolkit is the modern, opinionated approach.

```bash
npm install @reduxjs/toolkit react-redux
```

```jsx
// store/authSlice.js
import { createSlice, createAsyncThunk } from "@reduxjs/toolkit";
import axios from "axios";

export const loginUser = createAsyncThunk("auth/login", async (credentials) => {
  const { data } = await axios.post("/api/auth/login", credentials);
  return data;
});

const authSlice = createSlice({
  name: "auth",
  initialState: { user: null, loading: false, error: null },
  reducers: {
    logout: (state) => { state.user = null; },
  },
  extraReducers: (builder) => {
    builder
      .addCase(loginUser.pending, (state) => { state.loading = true; })
      .addCase(loginUser.fulfilled, (state, { payload }) => {
        state.loading = false;
        state.user = payload;
      })
      .addCase(loginUser.rejected, (state, { error }) => {
        state.loading = false;
        state.error = error.message;
      });
  },
});

export const { logout } = authSlice.actions;
export default authSlice.reducer;
```

```jsx
// store/index.js
import { configureStore } from "@reduxjs/toolkit";
import authReducer from "./authSlice";

export const store = configureStore({
  reducer: { auth: authReducer },
});

// main.jsx
import { Provider } from "react-redux";
import { store } from "./store";

ReactDOM.createRoot(document.getElementById("root")).render(
  <Provider store={store}><App /></Provider>
);
```

```jsx
// Component usage
import { useSelector, useDispatch } from "react-redux";
import { loginUser, logout } from "./store/authSlice";

function AuthButton() {
  const { user, loading } = useSelector((state) => state.auth);
  const dispatch = useDispatch();

  if (loading) return <p>Logging in...</p>;
  if (user) return <button onClick={() => dispatch(logout())}>Logout {user.name}</button>;
  return <button onClick={() => dispatch(loginUser({ email: "test@test.com", password: "123" }))}>Login</button>;
}
```

---

### React Query (TanStack Query)

The best tool for **async server state** — fetching, caching, synchronizing, and updating data.

```bash
npm install @tanstack/react-query
```

```jsx
// main.jsx
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById("root")).render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);
```

```jsx
// services/api.js
import axios from "axios";
export const getProjects = () => axios.get("/api/projects").then((r) => r.data);
export const createProject = (data) => axios.post("/api/projects", data).then((r) => r.data);

// Component
import { useQuery, useMutation, useQueryClient } from "@tanstack/react-query";
import { getProjects, createProject } from "./services/api";

function Projects() {
  const qc = useQueryClient();

  const { data, isLoading, error } = useQuery({
    queryKey: ["projects"],
    queryFn: getProjects,
    staleTime: 5 * 60 * 1000, // Cache for 5 minutes
  });

  const mutation = useMutation({
    mutationFn: createProject,
    onSuccess: () => qc.invalidateQueries({ queryKey: ["projects"] }),
  });

  if (isLoading) return <p>Loading projects...</p>;
  if (error) return <p>Error loading projects.</p>;

  return (
    <div>
      {data.map((p) => <p key={p.id}>{p.name}</p>)}
      <button onClick={() => mutation.mutate({ name: "New Project" })}>
        {mutation.isPending ? "Creating..." : "Add Project"}
      </button>
    </div>
  );
}
```

---

### Performance Optimization

```jsx
import { memo } from "react";

// React.memo: prevent re-render if props haven't changed
const ExpensiveComponent = memo(({ data, onAction }) => {
  console.log("Only renders when data or onAction changes");
  return <div>{data.title}</div>;
});
```

**Performance Checklist:**
- Use React DevTools Profiler to find bottlenecks
- `React.memo` for components with stable props
- `useCallback` for event handlers passed as props
- `useMemo` for expensive data transformations
- Virtualize long lists with `react-window` or `react-virtual`
- Lazy-load images and components
- Avoid anonymous functions in JSX when children re-render often

```bash
# Virtualization for large lists
npm install react-window
```

```jsx
import { FixedSizeList } from "react-window";

const Row = ({ index, style }) => (
  <div style={style}>Row #{index}</div>
);

function VirtualList() {
  return (
    <FixedSizeList height={400} width="100%" itemCount={10000} itemSize={35}>
      {Row}
    </FixedSizeList>
  );
}
```

---

### Testing

```bash
# Install testing libraries
npm install --save-dev @testing-library/react @testing-library/jest-dom @testing-library/user-event vitest jsdom
```

```jsx
// components/Counter.test.jsx
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import { describe, it, expect } from "vitest";
import Counter from "./Counter";

describe("Counter Component", () => {
  it("renders with initial count of 0", () => {
    render(<Counter />);
    expect(screen.getByText(/count: 0/i)).toBeInTheDocument();
  });

  it("increments count on button click", async () => {
    const user = userEvent.setup();
    render(<Counter />);
    await user.click(screen.getByRole("button", { name: /increment/i }));
    expect(screen.getByText(/count: 1/i)).toBeInTheDocument();
  });
});
```

```jsx
// Testing async components
import { waitFor } from "@testing-library/react";

it("loads and displays user data", async () => {
  render(<UserProfile userId="1" />);
  expect(screen.getByText(/loading/i)).toBeInTheDocument();
  await waitFor(() => expect(screen.getByText(/Leanne Graham/i)).toBeInTheDocument());
});
```

---

### Server-Side Rendering with Next.js

Next.js is the **production-grade React framework** for SSR, SSG, and full-stack apps.

```bash
npx create-next-app@latest my-next-app
cd my-next-app
npm run dev
```

```jsx
// app/projects/[id]/page.jsx — App Router (Next.js 13+)

// Server Component: runs on server, no hooks
async function ProjectPage({ params }) {
  const project = await fetch(`https://api.example.com/projects/${params.id}`).then((r) => r.json());

  return (
    <div>
      <h1>{project.name}</h1>
      <p>{project.description}</p>
    </div>
  );
}

export default ProjectPage;
```

```jsx
// Metadata for SEO
export async function generateMetadata({ params }) {
  const project = await fetch(`/api/projects/${params.id}`).then((r) => r.json());
  return {
    title: `${project.name} | Popup Core Technology`,
    description: project.description,
  };
}
```

---

## Project Architecture & Best Practices

### Folder Structure (Scalable)

```
src/
├── components/
│   ├── ui/             # Primitive components (Button, Input, Badge)
│   └── modules/        # Feature modules (ProjectCard, UserAvatar)
├── pages/              # Route-level components
├── hooks/              # Custom hooks (useFetch, useAuth, useForm)
├── context/            # Global providers
├── store/              # Redux slices or Zustand stores
├── services/           # API layer (all fetch/axios calls live here)
├── utils/              # Pure helper functions
├── types/              # TypeScript interfaces (if using TS)
└── constants/          # App-wide constants (API URLs, enums)
```

### Environment Variables

```bash
# .env
VITE_API_BASE_URL=https://api.yourapp.com
VITE_RAZORPAY_KEY=your_key_here
```

```jsx
// Access in code (Vite)
const API_URL = import.meta.env.VITE_API_BASE_URL;
```

> ⚠️ Never expose secrets. Variables prefixed with `VITE_` are bundled into the client.

### Best Practices Summary

| ✅ Do | ❌ Avoid |
|-------|---------|
| Use functional components | Class components (unless needed for Error Boundaries) |
| Co-locate state close to usage | Lifting state unnecessarily |
| Extract logic into custom hooks | Putting all logic directly in components |
| Use TypeScript for large projects | `any` type if using TypeScript |
| Memoize only when needed | Premature optimization |
| Use `key` prop correctly | Using array index as key |
| Handle loading/error states | Ignoring async edge cases |
| Use environment variables for config | Hardcoding API URLs |
| Validate forms (React Hook Form + Zod) | Manual, repetitive validation |
| Write tests for critical paths | Skipping tests entirely |

---

## Useful Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Install dependencies
npm install

# Add a package
npm install <package-name>

# Remove a package
npm uninstall <package-name>

# Run tests
npm test

# Lint code
npm run lint

# Format with Prettier
npx prettier --write src/
```

---

## Recommended VS Code Extensions

| Extension | Purpose |
|-----------|---------|
| **ES7+ React/Redux Snippets** | Fast component scaffolding |
| **Prettier** | Auto code formatting |
| **ESLint** | Catch bugs and bad patterns |
| **Auto Rename Tag** | Rename matching JSX tags |
| **Path Intellisense** | Autocomplete import paths |
| **GitLens** | Inline Git blame and history |
| **Tailwind CSS IntelliSense** | Autocomplete for Tailwind classes |
| **Error Lens** | Inline error highlighting |

---

## Resources

| Resource | Link |
|----------|------|
| React Official Documentation | https://react.dev |
| Vite Documentation | https://vitejs.dev |
| React Router Documentation | https://reactrouter.com |
| TanStack Query | https://tanstack.com/query |
| Redux Toolkit | https://redux-toolkit.js.org |
| Next.js Documentation | https://nextjs.org/docs |
| React Testing Library | https://testing-library.com/react |
| TypeScript + React | https://react-typescript-cheatsheet.netlify.app |

---

<div align="center">

**Built with ❤️ by [Lalit Tomer](https://github.com/lalittomer)**  
[Popup Core Technology](https://www.popupcore.in) · WeWork Cyberhub, Gurgaon

</div>
