
# Session 9 - Introduction to React.js & Components

## 📌 Topics Covered
- What is React.js?
- Why use React?
- Setting up a React project
- Understanding JSX
- Components in React (Functional & Class Components)
- Props & Component Communication

## 🛠 Prerequisites
- Install Node.js & npm
- Basic knowledge of HTML, CSS, JavaScript
- Install React globally (Optional)

```bash
npx create-react-app my-app
cd my-app
npm start
```

## 🔹 Understanding JSX
JSX allows writing HTML inside JavaScript.
```javascript
const element = <h1>Hello, React!</h1>;
```

## 🔹 Functional vs. Class Components
### Functional Component
```javascript
const Welcome = (props) => {
  return <h1>Hello, {props.name}!</h1>;
};
```

### Class Component
```javascript
import React, { Component } from "react";

class Welcome extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Welcome;
```

## 🔹 Props & Component Communication
Passing props from parent to child.
```javascript
const Greeting = ({ name }) => <h1>Hello, {name}!</h1>;

const App = () => <Greeting name="Keval" />;
```

---
