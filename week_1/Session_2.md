# Session 2: JavaScript ES6+ & DOM Manipulation

## JavaScript ES6+ Features
Modern JavaScript (ES6+) introduces several new features for cleaner and more efficient code.

### **1. Arrow Functions**
```js
const add = (a, b) => a + b;
console.log(add(5, 3));
```

### **2. Spread and Rest Operator**
```js
let numbers = [1, 2, 3];
let newNumbers = [...numbers, 4, 5];
console.log(newNumbers);
```

### **3. Destructuring**
```js
const person = { name: "Alice", age: 22 };
const { name, age } = person;
console.log(name, age);
```

## DOM Manipulation Basics
The Document Object Model (DOM) allows JavaScript to interact with HTML elements.

### **Selecting Elements**
```js
let title = document.getElementById("title");
console.log(title.textContent);
```

### **Modifying Elements**
```js
title.textContent = "Updated Title";
```

### **Event Handling**
```js
document.getElementById("btn").addEventListener("click", () => {
    alert("Button Clicked!");
});
```

## Callbacks, Promises, and Async/Await

### **1. Callbacks**
```js
function fetchData(callback) {
    setTimeout(() => {
        callback("Data received");
    }, 2000);
}
fetchData(data => console.log(data));
```

### **2. Promises**
```js
let fetchData = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Data received"), 2000);
});
fetchData.then(data => console.log(data));
```

### **3. Async/Await**
```js
async function fetchData() {
    let response = await new Promise(resolve => setTimeout(() => resolve("Data received"), 2000));
    console.log(response);
}
fetchData();
