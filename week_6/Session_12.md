**Session 12**:

### 1. `Button.js` - Reusable Button Component
```jsx
import React from 'react';

const Button = ({ text, onClick, className }) => {
  return (
    <button className={className} onClick={onClick}>
      {text}
    </button>
  );
};

export default Button;
```

**Usage in another component:**
```jsx
import React from 'react';
import Button from './Button';

function App() {
  return (
    <div>
      <h1>Reusable Button Example</h1>
      <Button text="Click Me" onClick={() => alert('Button clicked!')} className="btn-primary" />
    </div>
  );
}

export default App;
```

---

### 2. `Card.js` - Reusable Card Component
```jsx
import React from 'react';

const Card = ({ title, content }) => {
  return (
    <div className="card">
      <h2>{title}</h2>
      <p>{content}</p>
    </div>
  );
};

export default Card;
```

**Usage in another component:**
```jsx
import React from 'react';
import Card from './Card';

function App() {
  return (
    <div>
      <h1>Reusable Card Example</h1>
      <Card title="Card Title" content="This is a reusable card component." />
    </div>
  );
}

export default App;
```

---

### 3. Adding CSS for Styling (Optional)
**`styles.css`**
```css
.card {
  border: 1px solid #ddd;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
}

.btn-primary {
  background-color: #007bff;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn-primary:hover {
  background-color: #0056b3;
}
```