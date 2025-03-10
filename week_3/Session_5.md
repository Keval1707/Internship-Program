# 📂 Session 5 - Introduction to MongoDB & CRUD Operations

## 📌 Topics Covered
- What is MongoDB?
- NoSQL vs SQL
- Installing MongoDB & Compass
- Connecting MongoDB with Node.js
- Basic CRUD Operations (Create, Read, Update, Delete)

## 🛠 Prerequisites
- **Install MongoDB & Compass**: [Download MongoDB](https://www.mongodb.com/try/download/community)
- **Install Node.js**: [Download Node.js](https://nodejs.org/)
- Basic knowledge of JavaScript

---

## 📥 Installing MongoDB & Setting Up

```bash
# Install MongoDB globally
sudo apt update && sudo apt install -y mongodb

# Start MongoDB service
sudo systemctl start mongodb
sudo systemctl enable mongodb
```

---

## 🔗 Connecting MongoDB with Node.js

```javascript
const { MongoClient } = require("mongodb");

const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function run() {
  try {
    await client.connect();
    console.log("Connected to MongoDB!");
  } finally {
    await client.close();
  }
}

run().catch(console.error);
```

---

## 📝 CRUD Operations

```javascript
const db = client.db("internshipDB");
const collection = db.collection("students");

// Insert Data
await collection.insertOne({ name: "John Doe", age: 21 });

// Read Data
const data = await collection.find().toArray();

// Update Data
await collection.updateOne({ name: "John Doe" }, { $set: { age: 22 } });

// Delete Data
await collection.deleteOne({ name: "John Doe" });
```

---

### 🎯 Happy Coding! 🚀
