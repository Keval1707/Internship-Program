# Session 11: Working with React Router & State Management

## Overview
In this session, we will explore advanced React concepts, focusing on navigation using React Router and state management with Context API.

## Topics Covered
- React Router
  - Setting up routing in a React app
  - Navigating between pages
  - Dynamic routes and URL parameters
- Context API
  - Managing global state in React
  - Creating and using a Context Provider
- Fetching Data from APIs using Axios

## Prerequisites
- Basic knowledge of React (Components, Props, State)
- Familiarity with React Hooks (`useState`, `useEffect`)

## Step-by-Step Guide

### 1. Setting Up React Router
To install React Router, use the following command:
```bash
npm install react-router-dom
```

#### Example: Creating Routes
Modify `App.js` to include routes:
```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

### 2. Dynamic Routes
You can create dynamic routes to display specific content based on the URL.
```jsx
<Route path="/user/:id" element={<UserProfile />} />
```
In `UserProfile.js`:
```jsx
import { useParams } from 'react-router-dom';
function UserProfile() {
  const { id } = useParams();
  return <h1>User ID: {id}</h1>;
}
```

### 3. Managing State with Context API
Create a `UserContext.js` file:
```jsx
import { createContext, useState } from 'react';
export const UserContext = createContext();

export const UserProvider = ({ children }) => {
  const [user, setUser] = useState(null);
  return (
    <UserContext.Provider value={{ user, setUser }}>
      {children}
    </UserContext.Provider>
  );
};
```
Wrap `App.js` with `UserProvider`:
```jsx
import { UserProvider } from './UserContext';
<UserProvider>
  <App />
</UserProvider>
```

### 4. Fetching Data with Axios
Install Axios:
```bash
npm install axios
```
Example API call:
```jsx
import axios from 'axios';
import { useEffect, useState } from 'react';

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => setUsers(response.data))
      .catch(error => console.error(error));
  }, []);

  return (
    <ul>
      {users.map(user => <li key={user.id}>{user.name}</li>)}
    </ul>
  );
}
```

## Summary
- **React Router** enables navigation between pages.
- **Context API** manages global state efficiently.
- **Axios** is used to fetch data from APIs.

---
**Next Session:** [Session 12 - Reusable Components & Deployment]