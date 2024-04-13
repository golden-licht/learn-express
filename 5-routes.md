Create an Express application that demonstrates the importance of organizing endpoints into routes using routers. The application will have two sets of endpoints: one for managing users and another for managing products. Use routers to separate these endpoints into different modules.

- Create a folder structure for your project:

  ```
  /src
  ├── /routes
  │ ├── users.js
  │ └── products.js
  ├── app.js
  └── package.json
  ```

- Create users.js to define routes for managing users:
- Create products.js to define routes for managing products:
- Create app.js to use the routers:

users.mjs

```javascript
import { Router } from "express";
const router = Router();

// Route to get all users
router.get("/", (req, res) => {
  res.send("Get all users");
});

// Route to add a new user
router.post("/", (req, res) => {
  res.send("Add a new user");
});

export default router;
```

products.mjs

```javascript
import { Router } from "express";
const router = Router();

// Route to get all products
router.get("/", (req, res) => {
  res.send("Get all products");
});

// Route to add a new product
router.post("/", (req, res) => {
  res.send("Add a new product");
});

export default router;
```

app.mjs

```javascript
import express from "express";
import usersRouter from "./routes/users.mjs";
import productsRouter from "./routes/products.mjs";

const app = express();
// Use routers
app.use("/users", usersRouter);
app.use("/products", productsRouter);

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```
