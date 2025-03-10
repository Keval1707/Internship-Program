## Session 3: Introduction to Node.js & Express

### **1. What is Node.js?**
Node.js is a runtime environment that allows JavaScript to run outside the browser. It is built on the **V8 engine** and is used for server-side applications.

### **2. Why Use Node.js?**
- Non-blocking, event-driven architecture
- Fast execution
- Uses JavaScript for both frontend and backend
- Large community and package ecosystem (NPM)

### **3. Setting Up a Node.js Project**
1. Install Node.js from [https://nodejs.org](https://nodejs.org)
2. Check installation:
```sh
node -v  # Check Node.js version
npm -v   # Check NPM version
```
3. Create a new project:
```sh
mkdir my-backend
cd my-backend
npm init -y  # Initialize package.json
```

### **4. Understanding Modules in Node.js**
- Built-in modules: `fs`, `http`, `path`
- Third-party modules: Installed using `npm install`

#### **Example: Using the `fs` module**
```js
const fs = require('fs');
fs.writeFileSync('test.txt', 'Hello, Node.js!');
console.log('File created!');
```

### **5. Creating a Simple Express Server**
Express is a lightweight framework for building APIs and web applications.

#### **Installation:**
```sh
npm install express
```

#### **Basic Express Server:**
```js
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
    res.send('Hello, Express!');
});

app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```