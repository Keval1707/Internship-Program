

## Session 16: Implementing CRUD Operations in Full Stack App

### Overview
In this session, students will learn how to implement **CRUD (Create, Read, Update, Delete)** operations in a full-stack application.

### Topics Covered:
- Creating, reading, updating, and deleting records from MongoDB
- Handling API requests in the frontend
- Debugging and testing API calls
- Managing loading states in UI

### Example Code:
#### Backend (Express + MongoDB CRUD API)
```javascript
app.get('/users', async (req, res) => {
  try {
    const users = await User.find();
    res.send(users);
  } catch (error) {
    res.status(500).send(error);
  }
});

app.put('/users/:id', async (req, res) => {
  try {
    const user = await User.findByIdAndUpdate(req.params.id, req.body, { new: true });
    res.send(user);
  } catch (error) {
    res.status(400).send(error);
  }
});

app.delete('/users/:id', async (req, res) => {
  try {
    await User.findByIdAndDelete(req.params.id);
    res.send({ message: 'User deleted' });
  } catch (error) {
    res.status(500).send(error);
  }
});
```

#### Frontend (React - Fetching & Displaying Users)
```javascript
import React, { useEffect, useState } from 'react';
import axios from 'axios';

const UserList = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios.get('http://localhost:5000/users')
      .then((response) => setUsers(response.data))
      .catch((error) => console.error('Error fetching users', error));
  }, []);

  return (
    <div>
      <h2>User List</h2>
      <ul>
        {users.map((user) => (
          <li key={user._id}>{user.name} - {user.email}</li>
        ))}
      </ul>
    </div>
  );
};

export default UserList;
```

---
