Create an Express application that allows users to register with a username and password. Use express-validator to define the schema to be used to validate the registration inputs in a separate file (example validators.js). The validation rules should include checking for non empty username and requiring a minimum password length.

- Install express-validator
- Create a file named validators.js for the validation schema
- Create your Express app (app.js):

Use a tool like Postman to send a POST request to http://localhost:3000/register with a JSON body containing username and password.

validator.mjs

```javascript
import express from "express";
import { validationResult } from "express-validator";
import { registrationSchema } from "./validators.mjs";

const app = express();
const PORT = 3000;

app.post("/register", registrationSchema, (req, res) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(400).json({ errors: errors.array() });
  }
  // Proceed with registration logic if validation passes
  res.json({ message: "User registered successfully" });
});

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`);
});
```

app.mjs

```javascript
import express from "express";
import { validationResult } from "express-validator";
import { registrationSchema } from "./validators.mjs";

const app = express();
const PORT = 3000;

app.post("/register", registrationSchema, (req, res) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(400).json({ errors: errors.array() });
  }
  // Proceed with registration logic if validation passes
  res.json({ message: "User registered successfully" });
});

app.listen(PORT, () => {
  console.log(`Listening on port ${PORT}`);
});
```
