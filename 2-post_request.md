You are building a web application that allows users to submit feedback. Implement an Express route that accepts POST requests to submit feedback from users. The route should expect JSON data in the request body with the following format:

```javascript
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "message": "This is my feedback"
}
```

The route should validate that the name, email, and message fields are present in the request body. If any of these fields are missing, the route should respond with a 400 status code and a message indicating which field is missing. If all fields are present, the route should store the feedback and respond with a success message.

- Use Express.js for the server.
- Use the POST method for the route.
- Validate that the name, email, and message fields are present in the request body.
- If any field is missing, respond with a 400 status code and a message indicating which field is missing.
- If all fields are present, store the feedback and respond with a success message.

```javascript
import express from "express";
const app = express();
const PORT = 3000;

const dummy_feedbacks = [
  {
    name: "Math Cigar",
    email: "mat.cigar@gmail.com",
    message: "sonmething shoudl somethign",
  },
  {
    name: "Alex Endo",
    email: "endo.alex@twitter.com",
    message: "where is the someone",
  },
  {
    name: "Carlos Andre",
    email: "carlos.andre@yahoo.com",
    message: "you sure about that",
  },
];

app.use(express.json());

app.post("/feedback", (req, res) => {
  const { name, email, message } = req.body;

  if (name && email && message) {
    dummy_feedbacks.push(req.body);
    res.status(200).send("Feedback submitted successfully");
  } else {
    let missingFields = [];
    if (!name) missingFields.push("name");
    if (!email) missingFields.push("email");
    if (!message) missingFields.push("message");
    res.status(400).json({ "Missing fields": missingFields });
  }
});

app.listen(PORT, () => {
  console.log(`running on port ${PORT}`);
});
```
