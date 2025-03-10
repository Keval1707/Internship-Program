# 📂 Session 7 - User Authentication & JWT

## 📌 Topics Covered
- What is Authentication & Authorization?
- Introduction to JWT (JSON Web Token)
- Implementing Login & Signup API with Node.js & Express
- Storing Passwords Securely using bcrypt

---

## 🛠 Prerequisites
- Install Node.js and MongoDB
- Basic understanding of Express.js
- Install required dependencies

```bash
npm install express mongoose dotenv bcrypt jsonwebtoken cors
```

---

## 🔗 Setting Up Express & MongoDB

```javascript
const express = require("express");
const mongoose = require("mongoose");
const dotenv = require("dotenv");

dotenv.config();
const app = express();
app.use(express.json());

mongoose.connect(process.env.MONGO_URI, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log("MongoDB Connected"))
  .catch(err => console.log(err));

app.listen(5000, () => console.log("Server running on port 5000"));
```

---

## 🔐 User Model with Password Hashing

```javascript
const mongoose = require("mongoose");
const bcrypt = require("bcrypt");

const userSchema = new mongoose.Schema({
  name: String,
  email: { type: String, unique: true },
  password: String,
});

// Hash password before saving
userSchema.pre("save", async function (next) {
  if (!this.isModified("password")) return next();
  this.password = await bcrypt.hash(this.password, 10);
  next();
});

module.exports = mongoose.model("User", userSchema);
```

---

## 📝 Signup API

```javascript
const express = require("express");
const User = require("../models/User");
const router = express.Router();

router.post("/signup", async (req, res) => {
  try {
    const user = await User.create(req.body);
    res.status(201).json({ message: "User registered successfully", user });
  } catch (error) {
    res.status(400).json({ error: error.message });
  }
});

module.exports = router;
```

---

## 🔑 Login API with JWT Token

```javascript
const jwt = require("jsonwebtoken");
const bcrypt = require("bcrypt");

router.post("/login", async (req, res) => {
  const { email, password } = req.body;

  const user = await User.findOne({ email });
  if (!user) return res.status(400).json({ message: "User not found" });

  const isMatch = await bcrypt.compare(password, user.password);
  if (!isMatch) return res.status(400).json({ message: "Invalid password" });

  const token = jwt.sign({ userId: user._id }, process.env.JWT_SECRET, { expiresIn: "1h" });
  res.json({ token });
});

module.exports = router;
```

---

### 🎯 Happy Coding! 🚀
