
# Session 10 - React Hooks & State Management

## 📌 Topics Covered
- What is State?
- Using useState Hook
- Handling Events in React
- useEffect Hook
- Fetching API data in React

## 🔹 Using useState for Managing State
```javascript
import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default Counter;
```

## 🔹 Using useEffect for Side Effects
Fetching API data when the component mounts.
```javascript
import { useEffect, useState } from "react";

const Users = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};

export default Users;
```
