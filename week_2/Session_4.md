
## Session 4: Express Routing & API Development

### **1. Handling GET and POST Requests**
#### **GET Request:**
```js
app.get('/users', (req, res) => {
    res.json([{ id: 1, name: 'John' }, { id: 2, name: 'Alice' }]);
});
```

#### **POST Request:**
```js
app.use(express.json()); // Middleware to parse JSON
app.post('/users', (req, res) => {
    const newUser = req.body;
    res.status(201).json({ message: 'User created', user: newUser });
});
```

### **2. Middleware in Express**
Middleware functions are used to modify request and response objects.

#### **Example Middleware:**
```js
app.use((req, res, next) => {
    console.log(`${req.method} ${req.url}`);
    next();
});
```

### **3. Error Handling in Express**
```js
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send('Something went wrong!');
});
```

### **4. Building a Simple REST API**
```js
const users = [
    { id: 1, name: 'John Doe' },
    { id: 2, name: 'Jane Doe' }
];

app.get('/api/users', (req, res) => {
    res.json(users);
});

app.post('/api/users', (req, res) => {
    const newUser = { id: users.length + 1, ...req.body };
    users.push(newUser);
    res.status(201).json(newUser);
});
```

### **5. Running the Server**
Start the server using:
```sh
node server.js
```