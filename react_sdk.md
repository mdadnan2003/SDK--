# ⚛️ React Master SDK

> A reusable React reference for building modern frontend applications.

---

# 📚 Table of Contents

1. React Basics
2. React + Vite Setup
3. Project Structure
4. JSX
5. Components
6. Props
7. State
8. Events
9. Conditional Rendering
10. Lists & Keys
11. Forms
12. Controlled Components
13. useState
14. useEffect
15. useRef
16. useMemo
17. useCallback
18. useContext
19. Custom Hooks
20. Component Communication
21. API Calls
22. CRUD
23. Loading & Error States
24. React Router
25. Protected Routes
26. Authentication
27. LocalStorage
28. Reusable UI Components
29. Navbar
30. Sidebar
31. Cards
32. Modal
33. Tables
34. Pagination
35. Search & Filter
36. Debouncing
37. File Upload
38. Image Preview
39. Dark Mode
40. Toast Notifications
41. Context API
42. Redux Toolkit
43. Zustand
44. TanStack Query
45. React Hook Form
46. Zod Validation
47. React + TypeScript
48. TypeScript Props
49. TypeScript Hooks
50. Performance Optimization
51. Error Boundaries
52. React Security
53. Testing
54. React + Flask
55. React + FastAPI
56. Full-Stack Architecture
57. Environment Variables
58. Production Build
59. Deployment
60. Recommended Folder Structure
61. Complete Project Pattern
62. React Cheat Sheet

---

# 1. React Basics

React is a JavaScript library for building user interfaces.

Main idea:

```text
UI
 ↓
Components
 ↓
State
 ↓
User Interaction
 ↓
State Update
 ↓
UI Re-render
```

Example:

```jsx
function App() {
  return <h1>Hello React</h1>;
}

export default App;
```

---

# 2. React + Vite Setup

Create project:

```bash
npm create vite@latest my-app
```

Select:

```text
Framework → React
Variant   → JavaScript
```

Then:

```bash
cd my-app
npm install
npm run dev
```

For TypeScript:

```bash
npm create vite@latest my-app
```

Select:

```text
React
TypeScript
```

---

# 3. Important npm Commands

```bash
npm install
npm run dev
npm run build
npm run preview
```

Install package:

```bash
npm install axios
```

Remove package:

```bash
npm uninstall axios
```

---

# 4. React Project Structure

Simple project:

```text
src/
│
├── assets/
├── components/
├── pages/
├── hooks/
├── services/
├── context/
├── utils/
├── App.jsx
├── main.jsx
└── index.css
```

Large application:

```text
src/
│
├── assets/
│
├── components/
│   ├── Navbar.jsx
│   ├── Sidebar.jsx
│   ├── Button.jsx
│   └── Modal.jsx
│
├── pages/
│   ├── Home.jsx
│   ├── Login.jsx
│   ├── Dashboard.jsx
│   └── Profile.jsx
│
├── hooks/
│   └── useAuth.js
│
├── services/
│   ├── api.js
│   └── auth.js
│
├── context/
│   └── AuthContext.jsx
│
├── utils/
│   └── helpers.js
│
├── App.jsx
├── main.jsx
└── index.css
```

---

# 5. JSX

JSX allows HTML-like syntax inside JavaScript.

```jsx
const name = "Adnan";

function App() {
  return <h1>Hello {name}</h1>;
}

export default App;
```

JavaScript expression:

```jsx
<h1>{2 + 3}</h1>
```

```jsx
<p>{user.name}</p>
```

---

# 6. JSX Rules

Use `className`:

```jsx
<div className="card">
  Hello
</div>
```

Not:

```jsx
<div class="card">
```

Inline CSS:

```jsx
<div style={{ color: "red", fontSize: "20px" }}>
  Hello
</div>
```

Multiple elements need a parent:

```jsx
return (
  <>
    <h1>Hello</h1>
    <p>React</p>
  </>
);
```

---

# 7. Components

Functional component:

```jsx
function Welcome() {
  return <h1>Welcome</h1>;
}

export default Welcome;
```

Use:

```jsx
import Welcome from "./Welcome";

function App() {
  return <Welcome />;
}
```

---

# 8. Component Naming

Correct:

```text
Navbar.jsx
UserCard.jsx
LoginForm.jsx
Dashboard.jsx
```

Avoid:

```text
navbar.jsx
usercard.jsx
```

Use PascalCase.

---

# 9. Props

Props = parent se child ko data.

Parent:

```jsx
function App() {
  return <User name="Adnan" age={22} />;
}
```

Child:

```jsx
function User({ name, age }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>{age}</p>
    </div>
  );
}

export default User;
```

---

# 10. Multiple Props

```jsx
<User
  name="Adnan"
  age={22}
  city="Bihar"
  role="Developer"
/>
```

```jsx
function User({ name, age, city, role }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>{age}</p>
      <p>{city}</p>
      <p>{role}</p>
    </div>
  );
}
```

---

# 11. children Prop

```jsx
function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}
```

Use:

```jsx
<Card>
  <h2>Hello</h2>
  <p>This is a card.</p>
</Card>
```

---

# 12. State

State = component ka changing data.

Example:

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        +
      </button>
    </div>
  );
}

export default Counter;
```

Flow:

```text
count
 ↓
setCount()
 ↓
React re-render
 ↓
New UI
```

---

# 13. useState

Basic:

```jsx
const [name, setName] = useState("");
```

Number:

```jsx
const [count, setCount] = useState(0);
```

Boolean:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

Array:

```jsx
const [users, setUsers] = useState([]);
```

Object:

```jsx
const [user, setUser] = useState({
  name: "",
  email: ""
});
```

---

# 14. Updating Objects

```jsx
setUser({
  ...user,
  name: "Adnan"
});
```

Multiple fields:

```jsx
setUser({
  ...user,
  name: "Adnan",
  email: "adnan@example.com"
});
```

---

# 15. Updating Arrays

Add:

```jsx
setUsers([
  ...users,
  newUser
]);
```

Remove:

```jsx
setUsers(
  users.filter(user => user.id !== id)
);
```

Update:

```jsx
setUsers(
  users.map(user =>
    user.id === id
      ? { ...user, name: "New Name" }
      : user
  )
);
```

---

# 16. Events

Click:

```jsx
<button onClick={handleClick}>
  Click
</button>
```

Function:

```jsx
function handleClick() {
  console.log("Clicked");
}
```

Input:

```jsx
<input onChange={handleChange} />
```

Submit:

```jsx
<form onSubmit={handleSubmit}>
```

---

# 17. Event Object

```jsx
function handleChange(event) {
  console.log(event.target.value);
}
```

---

# 18. Conditional Rendering

```jsx
{isLoggedIn ? (
  <Dashboard />
) : (
  <Login />
)}
```

Using `&&`:

```jsx
{isAdmin && <AdminPanel />}
```

---

# 19. Lists

```jsx
const users = [
  { id: 1, name: "Adnan" },
  { id: 2, name: "Irfan" }
];

function Users() {
  return (
    <div>
      {users.map(user => (
        <p key={user.id}>
          {user.name}
        </p>
      ))}
    </div>
  );
}
```

---

# 20. key

Correct:

```jsx
key={user.id}
```

Avoid:

```jsx
key={index}
```

when list order can change.

---

# 21. Forms

```jsx
function Login() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  function handleSubmit(e) {
    e.preventDefault();

    console.log(email);
    console.log(password);
  }

  return (
    <form onSubmit={handleSubmit}>

      <input
        type="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
      />

      <input
        type="password"
        value={password}
        onChange={e => setPassword(e.target.value)}
      />

      <button type="submit">
        Login
      </button>

    </form>
  );
}
```

---

# 22. Controlled Component

React state controls input.

```jsx
const [name, setName] = useState("");

<input
  value={name}
  onChange={e => setName(e.target.value)}
/>
```

Flow:

```text
Input
 ↓
onChange
 ↓
setState
 ↓
React
 ↓
value updated
```

---

# 23. Checkbox

```jsx
const [accepted, setAccepted] = useState(false);

<input
  type="checkbox"
  checked={accepted}
  onChange={e => setAccepted(e.target.checked)}
/>
```

---

# 24. Select

```jsx
const [role, setRole] = useState("");

<select
  value={role}
  onChange={e => setRole(e.target.value)}
>
  <option value="">Select Role</option>
  <option value="student">Student</option>
  <option value="developer">Developer</option>
</select>
```

---

# 25. useEffect

`useEffect` side effects ke liye use hota hai.

Examples:

```text
API call
Timer
Event listener
Document title
Subscriptions
```

Basic:

```jsx
useEffect(() => {
  console.log("Component mounted");
}, []);
```

---

# 26. useEffect Dependencies

Only mount:

```jsx
useEffect(() => {
  console.log("Mounted");
}, []);
```

Every render:

```jsx
useEffect(() => {
  console.log("Rendered");
});
```

When count changes:

```jsx
useEffect(() => {
  console.log(count);
}, [count]);
```

---

# 27. API Call with useEffect

```jsx
import { useEffect, useState } from "react";

function Users() {

  const [users, setUsers] = useState([]);

  useEffect(() => {

    fetch("https://api.example.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));

  }, []);

  return (
    <div>
      {users.map(user => (
        <p key={user.id}>
          {user.name}
        </p>
      ))}
    </div>
  );
}
```

---

# 28. Async API Pattern

```jsx
useEffect(() => {

  async function loadUsers() {
    const response = await fetch(
      "https://api.example.com/users"
    );

    const data = await response.json();

    setUsers(data);
  }

  loadUsers();

}, []);
```

---

# 29. Loading State

```jsx
const [loading, setLoading] = useState(true);

useEffect(() => {

  async function loadData() {

    try {
      const response = await fetch("/api/users");
      const data = await response.json();

      setUsers(data);

    } finally {
      setLoading(false);
    }

  }

  loadData();

}, []);
```

UI:

```jsx
{loading ? (
  <p>Loading...</p>
) : (
  <UserList users={users} />
)}
```

---

# 30. Error State

```jsx
const [error, setError] = useState("");

async function loadUsers() {

  try {

    const response = await fetch("/api/users");

    if (!response.ok) {
      throw new Error("Failed to fetch users");
    }

    const data = await response.json();

    setUsers(data);

  } catch (err) {

    setError(err.message);

  }
}
```

---

# 31. useRef

DOM element access:

```jsx
const inputRef = useRef(null);

function focusInput() {
  inputRef.current.focus();
}

return (
  <>
    <input ref={inputRef} />
    <button onClick={focusInput}>
      Focus
    </button>
  </>
);
```

---

# 32. useRef for Mutable Value

```jsx
const countRef = useRef(0);

countRef.current += 1;
```

Changing `ref.current` does not cause re-render.

---

# 33. useMemo

Expensive calculation ko cache karne ke liye.

```jsx
const filteredUsers = useMemo(() => {

  return users.filter(user =>
    user.name
      .toLowerCase()
      .includes(search.toLowerCase())
  );

}, [users, search]);
```

Use only when useful.

---

# 34. useCallback

Function ko memoize karne ke liye.

```jsx
const handleDelete = useCallback((id) => {
  deleteUser(id);
}, []);
```

Useful when passing functions to memoized child components.

---

# 35. React.memo

```jsx
const UserCard = React.memo(function UserCard({
  user
}) {
  return <h2>{user.name}</h2>;
});
```

Component unnecessary re-render se bach sakta hai.

---

# 36. useContext

Create context:

```jsx
import { createContext } from "react";

export const AuthContext = createContext(null);
```

Provider:

```jsx
<AuthContext.Provider value={{ user }}>
  {children}
</AuthContext.Provider>
```

Consume:

```jsx
const { user } = useContext(AuthContext);
```

---

# 37. Custom Hook

Example:

```jsx
function useToggle(initialValue = false) {

  const [value, setValue] = useState(initialValue);

  const toggle = () => {
    setValue(prev => !prev);
  };

  return [value, toggle];
}
```

Use:

```jsx
const [isOpen, toggleOpen] = useToggle();
```

---

# 38. Custom API Hook

```jsx
function useFetch(url) {

  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {

    async function fetchData() {

      try {

        const response = await fetch(url);

        if (!response.ok) {
          throw new Error("Request failed");
        }

        const result = await response.json();

        setData(result);

      } catch (err) {

        setError(err);

      } finally {

        setLoading(false);

      }
    }

    fetchData();

  }, [url]);

  return {
    data,
    loading,
    error
  };
}
```

---

# 39. Component Communication

Parent → Child:

```text
Props
```

Child → Parent:

```text
Callback function
```

Sibling → Sibling:

```text
Common parent state
```

Global:

```text
Context / Redux / Zustand
```

---

# 40. Child → Parent

Parent:

```jsx
function App() {

  function handleMessage(message) {
    console.log(message);
  }

  return (
    <Child onMessage={handleMessage} />
  );
}
```

Child:

```jsx
function Child({ onMessage }) {

  return (
    <button onClick={() => onMessage("Hello Parent")}>
      Send
    </button>
  );
}
```

---

# 41. Axios

Install:

```bash
npm install axios
```

Basic:

```jsx
import axios from "axios";

const response = await axios.get(
  "http://localhost:5000/api/users"
);

console.log(response.data);
```

POST:

```jsx
await axios.post(
  "/api/users",
  {
    name: "Adnan",
    email: "adnan@example.com"
  }
);
```

PUT:

```jsx
await axios.put(
  `/api/users/${id}`,
  data
);
```

DELETE:

```jsx
await axios.delete(
  `/api/users/${id}`
);
```

---

# 42. API Service

`services/api.js`

```jsx
import axios from "axios";

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL
});

export default api;
```

Use:

```jsx
import api from "../services/api";

const response = await api.get("/users");
```

---

# 43. CRUD Flow

```text
React UI
   ↓
Event
   ↓
Service Function
   ↓
Axios / Fetch
   ↓
Backend API
   ↓
Database
   ↓
JSON Response
   ↓
React State
   ↓
UI
```

---

# 44. CRUD Service

```jsx
export const getUsers = () =>
  api.get("/users");

export const createUser = (data) =>
  api.post("/users", data);

export const updateUser = (id, data) =>
  api.put(`/users/${id}`, data);

export const deleteUser = (id) =>
  api.delete(`/users/${id}`);
```

---

# 45. React Router

Install:

```bash
npm install react-router-dom
```

Routes:

```jsx
import {
  BrowserRouter,
  Routes,
  Route
} from "react-router-dom";

function App() {

  return (
    <BrowserRouter>

      <Routes>

        <Route
          path="/"
          element={<Home />}
        />

        <Route
          path="/login"
          element={<Login />}
        />

        <Route
          path="/dashboard"
          element={<Dashboard />}
        />

      </Routes>

    </BrowserRouter>
  );
}
```

---

# 46. Navigation

```jsx
import { Link } from "react-router-dom";

<Link to="/login">
  Login
</Link>
```

Programmatic navigation:

```jsx
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();

navigate("/dashboard");
```

---

# 47. Dynamic Route

```jsx
<Route
  path="/users/:id"
  element={<UserDetails />}
/>
```

Read ID:

```jsx
import { useParams } from "react-router-dom";

const { id } = useParams();
```

---

# 48. Nested Routes

```jsx
<Route path="/dashboard" element={<Dashboard />}>

  <Route
    path="profile"
    element={<Profile />}
  />

  <Route
    path="settings"
    element={<Settings />}
  />

</Route>
```

---

# 49. Protected Routes

Concept:

```text
User
 ↓
ProtectedRoute
 ↓
Authenticated?
 ├── YES → Dashboard
 └── NO  → Login
```

Example:

```jsx
function ProtectedRoute({ children }) {

  const token = localStorage.getItem("token");

  if (!token) {
    return <Navigate to="/login" replace />;
  }

  return children;
}
```

Use:

```jsx
<Route
  path="/dashboard"
  element={
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

---

# 50. Authentication Flow

```text
Login Form
    ↓
POST /login
    ↓
Backend
    ↓
Verify credentials
    ↓
Token / Session
    ↓
Frontend
    ↓
Authenticated state
    ↓
Dashboard
```

---

# 51. Login Example

```jsx
async function handleLogin(e) {

  e.preventDefault();

  try {

    const response = await api.post(
      "/login",
      {
        email,
        password
      }
    );

    localStorage.setItem(
      "token",
      response.data.token
    );

    navigate("/dashboard");

  } catch (error) {

    console.error(error);

  }
}
```

> Production authentication should consider secure cookies/session-based approaches rather than automatically putting sensitive tokens in `localStorage`.

---

# 52. Axios Interceptor

```jsx
api.interceptors.request.use(config => {

  const token = localStorage.getItem("token");

  if (token) {
    config.headers.Authorization =
      `Bearer ${token}`;
  }

  return config;
});
```

---

# 53. Logout

```jsx
function logout() {

  localStorage.removeItem("token");

  navigate("/login");
}
```

---

# 54. LocalStorage

Save:

```jsx
localStorage.setItem(
  "theme",
  "dark"
);
```

Read:

```jsx
const theme =
  localStorage.getItem("theme");
```

Remove:

```jsx
localStorage.removeItem("theme");
```

Clear:

```jsx
localStorage.clear();
```

---

# 55. Reusable Button

```jsx
function Button({
  children,
  onClick,
  type = "button"
}) {

  return (
    <button
      type={type}
      onClick={onClick}
      className="btn"
    >
      {children}
    </button>
  );
}
```

Use:

```jsx
<Button>
  Login
</Button>
```

---

# 56. Reusable Card

```jsx
function Card({ title, children }) {

  return (
    <div className="card">

      <h2>{title}</h2>

      <div>
        {children}
      </div>

    </div>
  );
}
```

---

# 57. Navbar

```jsx
function Navbar() {

  return (
    <nav className="navbar">

      <div className="logo">
        MyApp
      </div>

      <div className="nav-links">
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
        <Link to="/dashboard">Dashboard</Link>
      </div>

    </nav>
  );
}
```

---

# 58. Sidebar

```jsx
function Sidebar() {

  return (
    <aside className="sidebar">

      <Link to="/dashboard">
        Dashboard
      </Link>

      <Link to="/users">
        Users
      </Link>

      <Link to="/settings">
        Settings
      </Link>

    </aside>
  );
}
```

---

# 59. Dashboard Layout

```jsx
function DashboardLayout({ children }) {

  return (
    <div className="dashboard-layout">

      <Sidebar />

      <main className="dashboard-content">
        {children}
      </main>

    </div>
  );
}
```

---

# 60. Modal

```jsx
function Modal({
  isOpen,
  onClose,
  children
}) {

  if (!isOpen) {
    return null;
  }

  return (
    <div className="modal-overlay">

      <div className="modal">

        <button onClick={onClose}>
          ×
        </button>

        {children}

      </div>

    </div>
  );
}
```

Use:

```jsx
const [isOpen, setIsOpen] = useState(false);

<button onClick={() => setIsOpen(true)}>
  Open
</button>

<Modal
  isOpen={isOpen}
  onClose={() => setIsOpen(false)}
>
  <h2>Hello</h2>
</Modal>
```

---

# 61. Table

```jsx
function UserTable({ users }) {

  return (
    <table>

      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Role</th>
        </tr>
      </thead>

      <tbody>

        {users.map(user => (

          <tr key={user.id}>

            <td>{user.name}</td>
            <td>{user.email}</td>
            <td>{user.role}</td>

          </tr>

        ))}

      </tbody>

    </table>
  );
}
```

---

# 62. Search

```jsx
const [search, setSearch] = useState("");

const filteredUsers = users.filter(user =>
  user.name
    .toLowerCase()
    .includes(search.toLowerCase())
);
```

Input:

```jsx
<input
  type="search"
  placeholder="Search users..."
  value={search}
  onChange={e => setSearch(e.target.value)}
/>
```

---

# 63. Filter

```jsx
const filteredUsers = users.filter(user => {

  const matchesSearch =
    user.name
      .toLowerCase()
      .includes(search.toLowerCase());

  const matchesRole =
    role === "all" ||
    user.role === role;

  return matchesSearch && matchesRole;
});
```

---

# 64. Pagination

Basic logic:

```jsx
const [page, setPage] = useState(1);

const itemsPerPage = 10;

const start =
  (page - 1) * itemsPerPage;

const currentItems =
  users.slice(
    start,
    start + itemsPerPage
  );
```

---

# 65. Debouncing

Useful for:

```text
Search
API requests
Autocomplete
```

Example:

```jsx
useEffect(() => {

  const timer = setTimeout(() => {

    searchUsers(search);

  }, 500);

  return () => clearTimeout(timer);

}, [search]);
```

Flow:

```text
User types
 ↓
wait 500ms
 ↓
No new input?
 ↓
API call
```

---

# 66. File Upload

```jsx
function Upload() {

  const [file, setFile] = useState(null);

  function handleFile(e) {
    setFile(e.target.files[0]);
  }

  return (
    <input
      type="file"
      onChange={handleFile}
    />
  );
}
```

---

# 67. Upload to Backend

```jsx
const formData = new FormData();

formData.append("file", file);

await api.post(
  "/upload",
  formData,
  {
    headers: {
      "Content-Type": "multipart/form-data"
    }
  }
);
```

---

# 68. Image Preview

```jsx
const [preview, setPreview] = useState("");

function handleImage(e) {

  const file = e.target.files[0];

  if (!file) return;

  setPreview(
    URL.createObjectURL(file)
  );
}
```

```jsx
<input
  type="file"
  accept="image/*"
  onChange={handleImage}
/>

{preview && (
  <img
    src={preview}
    alt="Preview"
  />
)}
```

---

# 69. Dark Mode

```jsx
const [dark, setDark] = useState(false);

useEffect(() => {

  document.documentElement
    .classList.toggle("dark", dark);

}, [dark]);
```

Toggle:

```jsx
<button onClick={() => setDark(prev => !prev)}>
  Toggle Theme
</button>
```

---

# 70. Toast Notification

Simple state:

```jsx
const [message, setMessage] = useState("");

function showToast(text) {

  setMessage(text);

  setTimeout(() => {
    setMessage("");
  }, 3000);
}
```

UI:

```jsx
{message && (
  <div className="toast">
    {message}
  </div>
)}
```

For production apps, a dedicated toast library can be used.

---

# 71. Context API

Create:

```jsx
const AuthContext = createContext(null);
```

Provider:

```jsx
function AuthProvider({ children }) {

  const [user, setUser] = useState(null);

  return (
    <AuthContext.Provider
      value={{
        user,
        setUser
      }}
    >
      {children}
    </AuthContext.Provider>
  );
}
```

Use:

```jsx
const {
  user,
  setUser
} = useContext(AuthContext);
```

---

# 72. Redux Toolkit

Install:

```bash
npm install @reduxjs/toolkit react-redux
```

Store:

```jsx
import { configureStore } from "@reduxjs/toolkit";

export const store = configureStore({
  reducer: {}
});
```

Provider:

```jsx
<Provider store={store}>
  <App />
</Provider>
```

---

# 73. Redux Slice

```jsx
import {
  createSlice
} from "@reduxjs/toolkit";

const counterSlice = createSlice({

  name: "counter",

  initialState: {
    value: 0
  },

  reducers: {

    increment: state => {
      state.value += 1;
    },

    decrement: state => {
      state.value -= 1;
    }

  }

});

export const {
  increment,
  decrement
} = counterSlice.actions;

export default counterSlice.reducer;
```

---

# 74. Redux useSelector

```jsx
const count = useSelector(
  state => state.counter.value
);
```

Dispatch:

```jsx
const dispatch = useDispatch();

dispatch(increment());
```

---

# 75. Zustand

Install:

```bash
npm install zustand
```

Store:

```jsx
import { create } from "zustand";

const useCounterStore = create(set => ({

  count: 0,

  increment: () =>
    set(state => ({
      count: state.count + 1
    })),

  decrement: () =>
    set(state => ({
      count: state.count - 1
    }))

}));
```

Use:

```jsx
const count =
  useCounterStore(state => state.count);

const increment =
  useCounterStore(state => state.increment);
```

---

# 76. TanStack Query

Install:

```bash
npm install @tanstack/react-query
```

Provider:

```jsx
const queryClient =
  new QueryClient();

<QueryClientProvider
  client={queryClient}
>
  <App />
</QueryClientProvider>
```

Query:

```jsx
const {
  data,
  isLoading,
  error
} = useQuery({
  queryKey: ["users"],
  queryFn: getUsers
});
```

Benefits:

```text
Caching
Refetching
Loading state
Error state
Server-state management
```

---

# 77. React Hook Form

Install:

```bash
npm install react-hook-form
```

Example:

```jsx
import { useForm } from "react-hook-form";

function Login() {

  const {
    register,
    handleSubmit
  } = useForm();

  function onSubmit(data) {
    console.log(data);
  }

  return (
    <form onSubmit={handleSubmit(onSubmit)}>

      <input
        {...register("email")}
      />

      <input
        type="password"
        {...register("password")}
      />

      <button type="submit">
        Login
      </button>

    </form>
  );
}
```

---

# 78. Zod Validation

Install:

```bash
npm install zod
```

Schema:

```jsx
import { z } from "zod";

const userSchema = z.object({

  name: z
    .string()
    .min(2),

  email: z
    .email(),

  age: z
    .number()
    .min(18)

});
```

Validate:

```jsx
const result =
  userSchema.safeParse(data);

if (!result.success) {

  console.log(
    result.error.issues
  );

}
```

---

# 79. React + TypeScript

Component:

```tsx
type UserProps = {
  name: string;
  age: number;
};

function UserCard({
  name,
  age
}: UserProps) {

  return (
    <div>
      <h2>{name}</h2>
      <p>{age}</p>
    </div>
  );
}
```

---

# 80. TypeScript State

```tsx
const [count, setCount] =
  useState<number>(0);
```

Array:

```tsx
const [users, setUsers] =
  useState<User[]>([]);
```

Object:

```tsx
const [user, setUser] =
  useState<User | null>(null);
```

---

# 81. TypeScript Event

Input:

```tsx
function handleChange(
  e: React.ChangeEvent<HTMLInputElement>
) {

  console.log(e.target.value);

}
```

Button:

```tsx
function handleClick(
  e: React.MouseEvent<HTMLButtonElement>
) {

  console.log("Clicked");

}
```

Form:

```tsx
function handleSubmit(
  e: React.FormEvent<HTMLFormElement>
) {

  e.preventDefault();

}
```

---

# 82. TypeScript children

```tsx
import { ReactNode } from "react";

type Props = {
  children: ReactNode;
};

function Card({ children }: Props) {

  return (
    <div>
      {children}
    </div>
  );
}
```

---

# 83. Performance Optimization

Main techniques:

```text
React.memo
useMemo
useCallback
Code splitting
Lazy loading
Virtualization
Image optimization
Avoid unnecessary state
Avoid unnecessary effects
```

---

# 84. Lazy Loading

```jsx
import { lazy, Suspense } from "react";

const Dashboard = lazy(
  () => import("./pages/Dashboard")
);
```

Use:

```jsx
<Suspense fallback={<p>Loading...</p>}>

  <Dashboard />

</Suspense>
```

---

# 85. Code Splitting

Instead of loading everything:

```text
App
 ├── Home
 ├── Dashboard
 ├── Admin
 └── Settings
```

Load pages when needed.

```jsx
const Admin = lazy(
  () => import("./pages/Admin")
);
```

---

# 86. Error Boundary

Error boundary catches rendering errors.

Concept:

```text
Application
 ↓
Error Boundary
 ↓
Component Error
 ↓
Fallback UI
```

Example with class component:

```jsx
class ErrorBoundary extends React.Component {

  constructor(props) {

    super(props);

    this.state = {
      hasError: false
    };

  }

  static getDerivedStateFromError() {

    return {
      hasError: true
    };

  }

  render() {

    if (this.state.hasError) {

      return (
        <h1>
          Something went wrong.
        </h1>
      );

    }

    return this.props.children;
  }
}
```

---

# 87. React Security

Never:

```jsx
<div
  dangerouslySetInnerHTML={{
    __html: userInput
  }}
/>
```

unless the HTML has been properly sanitized and the use case requires it.

Important:

```text
Validate user input
Sanitize untrusted HTML
Use HTTPS
Protect authentication
Avoid exposing secrets
Validate API responses
Use secure cookies where appropriate
Configure CORS correctly
Use CSRF protection when applicable
```

---

# 88. Environment Variables

Vite:

`.env`

```env
VITE_API_URL=http://localhost:5000/api
```

Use:

```jsx
const API_URL =
  import.meta.env.VITE_API_URL;
```

Never expose secrets:

```env
VITE_SECRET_KEY=...
```

Anything prefixed with `VITE_` can be exposed to browser-side code.

---

# 89. React + Flask

Architecture:

```text
React
   ↓
Axios / Fetch
   ↓
Flask REST API
   ↓
Service Layer
   ↓
SQLAlchemy
   ↓
PostgreSQL
```

Example:

```jsx
const response = await api.get("/users");
```

Flask:

```python
@app.get("/api/users")
def get_users():
    return jsonify(users)
```

---

# 90. React + FastAPI

Architecture:

```text
React
 ↓
Axios
 ↓
FastAPI
 ↓
Pydantic
 ↓
Service
 ↓
SQLAlchemy / SQL
 ↓
PostgreSQL
```

React:

```jsx
const response =
  await api.get("/users");
```

FastAPI:

```python
@app.get("/users")
def get_users():
    return users
```

---

# 91. CORS

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:5000
```

Different origins require correct CORS configuration.

Flask:

```bash
pip install flask-cors
```

```python
from flask_cors import CORS

CORS(app)
```

In production, configure allowed origins explicitly.

---

# 92. Full-Stack Architecture

```text
                 USER
                   │
                   ▼
              React App
                   │
          ┌────────┴────────┐
          │                 │
       Router             State
          │                 │
          └────────┬────────┘
                   │
                API Layer
                   │
              Axios/Fetch
                   │
                   ▼
             Backend API
          ┌────────┴────────┐
          │                 │
       Auth              Services
          │                 │
          └────────┬────────┘
                   │
                   ▼
              PostgreSQL
```

---

# 93. Recommended React Architecture

```text
src/
│
├── app/
│   ├── App.jsx
│   └── routes.jsx
│
├── components/
│   ├── ui/
│   │   ├── Button.jsx
│   │   ├── Modal.jsx
│   │   └── Input.jsx
│   │
│   └── layout/
│       ├── Navbar.jsx
│       └── Sidebar.jsx
│
├── pages/
│   ├── Home.jsx
│   ├── Login.jsx
│   └── Dashboard.jsx
│
├── features/
│   ├── auth/
│   └── users/
│
├── hooks/
│
├── services/
│
├── store/
│
├── utils/
│
├── assets/
│
└── main.jsx
```

---

# 94. Feature-Based Architecture

Large project:

```text
src/
│
├── features/
│
│   ├── auth/
│   │   ├── Login.jsx
│   │   ├── Register.jsx
│   │   ├── authApi.js
│   │   └── authSlice.js
│   │
│   ├── users/
│   │   ├── UserList.jsx
│   │   ├── UserCard.jsx
│   │   ├── userApi.js
│   │   └── userHooks.js
│   │
│   └── products/
│       ├── ProductList.jsx
│       ├── ProductCard.jsx
│       └── productApi.js
```

This becomes useful as applications grow.

---

# 95. Service Layer

Bad:

```jsx
function Dashboard() {

  fetch("/api/users");

  fetch("/api/orders");

  fetch("/api/products");

}
```

Better:

```text
Dashboard
   ↓
usersService
ordersService
productsService
   ↓
API
```

Example:

```jsx
export async function getUsers() {

  const response =
    await api.get("/users");

  return response.data;
}
```

---

# 96. Generic API Response

```ts
type ApiResponse<T> = {
  success: boolean;
  message: string;
  data: T;
};
```

Example:

```ts
type User = {
  id: number;
  name: string;
};

type UserResponse =
  ApiResponse<User>;
```

---

# 97. Pagination API

Typical response:

```json
{
  "data": [],
  "page": 1,
  "limit": 10,
  "total": 100,
  "totalPages": 10
}
```

Frontend:

```text
Page 1
Page 2
Page 3
...
```

---

# 98. React State Categories

```text
Local State
    ↓
useState

Shared State
    ↓
Context / Zustand / Redux

Server State
    ↓
TanStack Query

URL State
    ↓
React Router

Form State
    ↓
React Hook Form
```

---

# 99. When to Use What?

| Requirement | Tool |
|---|---|
| Small local state | useState |
| DOM reference | useRef |
| Side effects | useEffect |
| Derived expensive value | useMemo |
| Stable callback | useCallback |
| Small global state | Context |
| Complex global state | Redux Toolkit |
| Simple global state | Zustand |
| API/server state | TanStack Query |
| Complex forms | React Hook Form |
| Validation | Zod |
| Navigation | React Router |

---

# 100. Common Mistakes

## Mistake 1

Mutating state directly:

```jsx
user.name = "Adnan";
```

Correct:

```jsx
setUser({
  ...user,
  name: "Adnan"
});
```

---

## Mistake 2

Calling function immediately:

```jsx
<button onClick={handleClick()}>
```

Correct:

```jsx
<button onClick={handleClick}>
```

Or:

```jsx
<button
  onClick={() => handleClick(id)}
>
```

---

## Mistake 3

Missing key:

```jsx
users.map(user => (
  <div>{user.name}</div>
))
```

Correct:

```jsx
users.map(user => (
  <div key={user.id}>
    {user.name}
  </div>
))
```

---

# 101. useEffect Mistake

Avoid unnecessary effects.

Bad:

```jsx
useEffect(() => {
  setFullName(`${firstName} ${lastName}`);
}, [firstName, lastName]);
```

Better:

```jsx
const fullName =
  `${firstName} ${lastName}`;
```

Derived values generally do not need state + effect.

---

# 102. API State Pattern

Recommended:

```jsx
const [data, setData] = useState(null);
const [loading, setLoading] = useState(false);
const [error, setError] = useState(null);
```

Flow:

```text
Request
 ↓
loading = true
 ↓
API
 ├── Success → data
 └── Error → error
 ↓
loading = false
```

---

# 103. Reusable Fetch Function

```jsx
async function request(url, options = {}) {

  const response =
    await fetch(url, options);

  if (!response.ok) {
    throw new Error(
      `HTTP Error: ${response.status}`
    );
  }

  return response.json();
}
```

Use:

```jsx
const users =
  await request("/api/users");
```

---

# 104. Promise.all

Parallel API calls:

```jsx
const [
  users,
  products,
  orders
] = await Promise.all([

  getUsers(),
  getProducts(),
  getOrders()

]);
```

Useful when requests independent hain.

---

# 105. Abort Fetch Request

```jsx
useEffect(() => {

  const controller =
    new AbortController();

  async function load() {

    const response = await fetch(
      "/api/users",
      {
        signal: controller.signal
      }
    );

    const data =
      await response.json();

    setUsers(data);
  }

  load();

  return () => {
    controller.abort();
  };

}, []);
```

---

# 106. React Testing

Common tools:

```text
Vitest
Jest
React Testing Library
Playwright
```

Example:

```jsx
import {
  render,
  screen
} from "@testing-library/react";

render(<Button>Login</Button>);

expect(
  screen.getByText("Login")
).toBeInTheDocument();
```

---

# 107. Unit Testing Idea

Test:

```text
Component
 ↓
Input
 ↓
User action
 ↓
Expected UI
```

Example:

```text
Click Login
 ↓
API request
 ↓
Success
 ↓
Dashboard appears
```

---

# 108. Production Build

```bash
npm run build
```

Vite generates:

```text
dist/
```

Preview:

```bash
npm run preview
```

---

# 109. Deployment

Common frontend deployment options:

```text
Vercel
Netlify
Cloudflare Pages
AWS
Docker
Nginx
```

Build:

```bash
npm run build
```

Deploy:

```text
dist/
```

depending on the hosting platform.

---

# 110. Docker Concept

```text
Developer
   ↓
React Source
   ↓
npm build
   ↓
dist/
   ↓
Nginx
   ↓
Internet
```

---

# 111. Complete React + Backend Project

Example:

```text
my-project/
│
├── frontend/
│   ├── src/
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   ├── app/
│   ├── routes/
│   ├── services/
│   ├── models/
│   ├── config/
│   └── requirements.txt
│
├── .gitignore
└── README.md
```

---

# 112. Full Request Flow

Example Login:

```text
User
 │
 ▼
React Login Form
 │
 ▼
handleSubmit()
 │
 ▼
authService.login()
 │
 ▼
Axios
 │
 ▼
POST /api/login
 │
 ▼
Flask/FastAPI
 │
 ▼
Validate User
 │
 ▼
PostgreSQL
 │
 ▼
Authentication Result
 │
 ▼
JSON Response
 │
 ▼
React
 │
 ▼
Auth State
 │
 ▼
Protected Dashboard
```

---

# 113. React Development Checklist

Before creating a page:

```text
□ Page ka purpose
□ Components identify
□ Data identify
□ API endpoints
□ State identify
□ Loading state
□ Error state
□ Empty state
□ Form validation
□ Responsive design
□ Authentication
□ Authorization
```

---

# 114. Component Design Rule

A component should ideally have one clear responsibility.

Bad:

```text
Dashboard.jsx
 ├── Navbar
 ├── Sidebar
 ├── Users
 ├── Products
 ├── Orders
 ├── Modal
 ├── Forms
 └── API calls
```

Better:

```text
Dashboard
 ├── Navbar
 ├── Sidebar
 ├── Stats
 ├── UserTable
 ├── OrderTable
 └── Modal
```

---

# 115. React Mental Model

React ko is tarah samjho:

```text
Component
    ↓
Props + State
    ↓
JSX
    ↓
Virtual DOM / React rendering
    ↓
Browser UI
```

User action:

```text
Click / Input
      ↓
Event Handler
      ↓
setState()
      ↓
React renders
      ↓
UI updates
```

---

# 116. React Learning Roadmap

## Level 1 — Basics

```text
JavaScript
 ↓
JSX
 ↓
Components
 ↓
Props
 ↓
State
 ↓
Events
```

## Level 2 — Core React

```text
useState
useEffect
useRef
useContext
Custom Hooks
```

## Level 3 — Real Apps

```text
Forms
API
CRUD
Router
Authentication
Protected Routes
```

## Level 4 — State Management

```text
Context
Redux Toolkit
Zustand
TanStack Query
```

## Level 5 — Production

```text
TypeScript
Testing
Performance
Security
Docker
CI/CD
Deployment
```

---

# 117. React Cheat Sheet

## Component

```jsx
function App() {
  return <h1>Hello</h1>;
}
```

## Props

```jsx
function User({ name }) {
  return <h1>{name}</h1>;
}
```

## State

```jsx
const [count, setCount] = useState(0);
```

## Event

```jsx
<button onClick={handleClick}>
```

## Effect

```jsx
useEffect(() => {}, []);
```

## Ref

```jsx
const ref = useRef(null);
```

## Context

```jsx
const value = useContext(MyContext);
```

## Router

```jsx
<Route path="/dashboard" element={<Dashboard />} />
```

## Navigation

```jsx
navigate("/dashboard");
```

## API

```jsx
const response = await api.get("/users");
```

## POST

```jsx
await api.post("/users", data);
```

## Delete

```jsx
await api.delete(`/users/${id}`);
```

---

# 118. React Master Architecture

```text
                         REACT APPLICATION
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
           ROUTING           COMPONENTS         STATE
              │                 │                 │
        React Router       UI Components      ┌────┴────┐
                                              │         │
                                           Client     Server
                                            State      State
                                              │         │
                                         Zustand/    TanStack
                                          Redux       Query
              │                 │                 │
              └─────────────────┼─────────────────┘
                                │
                            API LAYER
                                │
                         Fetch / Axios
                                │
                                ▼
                         BACKEND API
                                │
                     ┌──────────┴──────────┐
                     │                     │
                   Flask                FastAPI
                     │                     │
                     └──────────┬──────────┘
                                │
                             Database
                                │
                           PostgreSQL
```

---

# 119. Golden Rules

```text
1. Components small rakho.
2. State ko minimum rakho.
3. Derived data ko state mat banao.
4. API logic ko components se separate rakho.
5. Reusable components banao.
6. Loading/Error/Empty states handle karo.
7. User input validate karo.
8. Sensitive secrets frontend mein mat rakho.
9. Large apps mein feature-based architecture use karo.
10. Server state aur client state ko alag samjho.
11. Performance optimization tab karo jab actual need ho.
12. TypeScript use karo as project complexity grows.
```

---

# 120. Final React Stack

```text
React
│
├── Vite
├── React Router
├── Axios / Fetch
├── TypeScript
│
├── Context
├── Zustand / Redux Toolkit
├── TanStack Query
│
├── React Hook Form
├── Zod
│
├── Tailwind CSS / CSS
│
├── Vitest
├── React Testing Library
├── Playwright
│
└── Backend
    ├── Flask
    ├── FastAPI
    └── PostgreSQL
```

---

# 🚀 React Project Formula

For almost every real-world application:

```text
1. Plan UI
      ↓
2. Create components
      ↓
3. Setup routing
      ↓
4. Create state
      ↓
5. Connect API
      ↓
6. Add forms
      ↓
7. Add validation
      ↓
8. Add authentication
      ↓
9. Add loading/error/empty states
      ↓
10. Test
      ↓
11. Optimize
      ↓
12. Build
      ↓
13. Deploy
```

# END
