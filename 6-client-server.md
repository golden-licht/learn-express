You have a React application running on port 3000 that needs to make an HTTP GET request to an Express server running on port 5000 on the same computer. Use axios as the HTTP client to fetch data from the server.

- In your Express server, create a route to handle the GET request:
- In your React application, use Axios to make the GET request to the Express server:

When you load your React application, it should make a GET request to the Express server, fetch the data, and display it on the page.

server.js
```javascript
const express = require('express')
const cors = require('cors');

const app = express();
const PORT = 5000;

app.use(cors());

app.get('/', (req, res) => {
    res.json({message: 'Data received from server'});
})

app.listen(PORT, () => {
    console.log(`Running server on http://localhost:${PORT}`);
});
```

App.js (from client side)
```javascript
import { useEffect, useState } from 'react';
import axios from 'axios';

const SERVER_PORT = 5000

const App = () => {
  const [data, setData] = useState('');
  useEffect(() => {
    axios.get(`http://localhost:${SERVER_PORT}`)
      .then(response => {
        setData(response.data.message);
      })
      .catch(error => {
        console.error('Error fetching data: ', error);
      }, []);
  })
  return (
    <div>
      <h1>Data from server: </h1>
      <p>{data}</p>
    </div>
  )
}

export default App;
```
