# Session 8 - Role-Based Access Control & Security

## 📌 Topics Covered
- Middleware for Authentication
- Protecting Routes using JWT
- Role-Based Access Control
- Security Best Practices

## 🔍 Middleware for JWT Authentication
```javascript
const jwt = require("jsonwebtoken");

const authMiddleware = (req, res, next) => {
  const token = req.header("Authorization");
  if (!token) return res.status(401).json({ message: "Access Denied" });

  try {
    const verified = jwt.verify(token, process.env.JWT_SECRET);
    req.user = verified;
    next();
  } catch (err) {
    res.status(400).json({ message: "Invalid Token" });
  }
};

module.exports = authMiddleware;
```

## 🛡 Protecting Routes
```javascript
const express = require("express");
const authMiddleware = require("../middleware/authMiddleware");
const router = express.Router();

router.get("/dashboard", authMiddleware, (req, res) => {
  res.json({ message: "Welcome to the dashboard!", user: req.user });
});

module.exports = router;
```

## 🛠 Role-Based Access Control
```javascript
const roleMiddleware = (roles) => {
  return (req, res, next) => {
    if (!roles.includes(req.user.role)) {
      return res.status(403).json({ message: "Forbidden: You don't have access" });
    }
    next();
  };
};

router.get("/admin", authMiddleware, roleMiddleware(["admin"]), (req, res) => {
  res.json({ message: "Welcome Admin!" });
});
```

## ⚡ Security Best Practices
### ✅ Use helmet and cors for security
```bash
npm install helmet cors
```
```javascript
const helmet = require("helmet");
const cors = require("cors");

app.use(helmet());
app.use(cors());
```
### ✅ Hash passwords before saving (Already used bcrypt)
### ✅ Use environment variables for secrets (.env)
### ✅ Limit login attempts to prevent brute force attacks

