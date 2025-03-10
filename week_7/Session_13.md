
## Session 13: Calling Backend APIs from React

### Overview
In this session, students will learn how to call backend APIs from a React frontend using Axios, handle API responses, and manage loading/error states.

### Topics Covered:
- Using Axios to fetch data from a backend API
- Managing API responses
- Handling loading and error states in React
- Displaying fetched data in a React component

### Example Code:
```javascript
import React, { useEffect, useState } from 'react';
import axios from 'axios';

const FetchData = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://api.example.com/data')
      .then(response => {
        setData(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError(error.message);
        setLoading(false);
      });
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <div>
      <h1>Data from API</h1>
      <ul>
        {data.map((item) => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default FetchData;
```
