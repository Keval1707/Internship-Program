## Session 15: Planning & Structuring a Full Stack Project

### Overview
In this session, students will learn how to structure a full-stack project, create database models, and set up API endpoints.

### Topics Covered:
- Planning the full-stack application
- Designing database models and relationships
- Setting up backend API endpoints with Express and MongoDB
- Creating the initial React UI structure

### Example Code:
#### Backend (Express + MongoDB)
```javascript
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
app.use(express.json());
app.use(cors());

mongoose.connect('mongodb://localhost:27017/fullstack_project', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const UserSchema = new mongoose.Schema({
  name: String,
  email: String,
  password: String,
});

const User = mongoose.model('User', UserSchema);

app.post('/register', async (req, res) => {
  try {
    const user = new User(req.body);
    await user.save();
    res.status(201).send(user);
  } catch (error) {
    res.status(400).send(error);
  }
});

app.listen(5000, () => console.log('Server running on port 5000'));
```

#### Frontend (React - Setting Up UI)
```javascript
import React, { useState } from 'react';
import axios from 'axios';

const Register = () => {
  const [formData, setFormData] = useState({ name: '', email: '', password: '' });
  const handleChange = (e) => setFormData({ ...formData, [e.target.name]: e.target.value });

  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const response = await axios.post('http://localhost:5000/register', formData);
      console.log('User Registered:', response.data);
    } catch (error) {
      console.error('Error registering user', error);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type='text' name='name' placeholder='Name' onChange={handleChange} />
      <input type='email' name='email' placeholder='Email' onChange={handleChange} />
      <input type='password' name='password' placeholder='Password' onChange={handleChange} />
      <button type='submit'>Register</button>
    </form>
  );
};

export default Register;
```
