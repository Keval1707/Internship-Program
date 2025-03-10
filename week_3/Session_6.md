# 📂 Session 6 - Mongoose & Data Validation

## 📌 Topics Covered
- What is Mongoose?
- Creating a Schema & Model
- Data Validation
- Relationships in MongoDB
- Error Handling

---

## 📥 Installing Mongoose

```bash
npm install mongoose
```

---

## 🔗 Connecting MongoDB with Mongoose

```javascript
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/internshipDB", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});
```

---

## 📝 Creating a Schema & Model

```javascript
const studentSchema = new mongoose.Schema({
  name: { type: String, required: true },
  age: { type: Number, min: 18 },
  email: { type: String, unique: true },
});

const Student = mongoose.model("Student", studentSchema);
```

---

## 📝 CRUD Operations using Mongoose

```javascript
// Insert Data
const student = new Student({ name: "Alice", age: 20, email: "alice@gmail.com" });
await student.save();

// Read Data
const students = await Student.find();

// Update Data
await Student.findOneAndUpdate({ name: "Alice" }, { age: 21 });

// Delete Data
await Student.findOneAndDelete({ name: "Alice" });
```

---

## 🔍 Error Handling in MongoDB

```javascript
try {
  await student.save();
} catch (error) {
  console.error("Error:", error.message);
}
```

---

### 🎯 Happy Coding! 🚀
