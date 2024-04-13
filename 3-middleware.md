Create an Express application with a single route /secret that requires a secret key to access. Implement a middleware function that logs the incoming requests to the /secret route, including the request method and timestamp. Use this middleware function to authenticate requests by checking if the request contains a specific secret key in the headers. If the key is missing or incorrect, respond with a 401 status code (Unauthorized). If the key is correct, allow the request to proceed and respond with a success message.

```javascript
import express from "express";
const app = express();
const PORT = 3000;

const mySecretKey = "321";

// Middleware function to log incoming requests
app.use((req, res, next) => {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
  next();
});

// Middleware function to authenticate requests
app.use((req, res, next) => {
  const secretKey = req.headers["x-secret-key"];
  if (secretKey != mySecretKey) {
    return res.status(401).json({ message: "Unauthorized" });
  }
  next();
});

// Route that requires authentication
app.get("/secret", (req, res) => {
  res.json({ message: "Access granted" });
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```
