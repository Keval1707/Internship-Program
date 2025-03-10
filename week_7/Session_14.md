
## Session 14: Protected Routes & Role-Based UI Rendering

### Overview
In this session, students will learn how to implement protected routes in React using `react-router-dom` and role-based UI rendering based on authentication status.

### Topics Covered:
- Authentication logic in React
- Implementing protected routes using `react-router-dom`
- Role-based UI rendering

### Example Code:
```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Navigate } from 'react-router-dom';

const isAuthenticated = () => {
  return localStorage.getItem('token') !== null;
};

const ProtectedRoute = ({ children }) => {
  return isAuthenticated() ? children : <Navigate to="/login" />;
};

const Dashboard = () => <h1>Dashboard - Protected</h1>;
const Login = () => <h1>Login Page</h1>;

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
      </Routes>
    </Router>
  );
};

export default App;
```
