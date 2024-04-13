You are building a healthcare application and need to create a route that allows you to retrieve information about a specific patient based on their username. Implement an Express route that accepts a username as a route parameter and returns the patient's information if the username exists in the database, or a 404 error if the username is not found.

- Use Express.js for the server.
- The route should be GET /patients/:username.
- If the patient with the given username is found, return their information as JSON.
- If the patient with the given username is not found, return a 404 error with a message.

```javascript
import express from "express";
const app = express();
const PORT = 3000;

const dummy_patients = [
  { username: "u001", password: "12345678" },
  { username: "u002", password: "13579246" },
  { username: "u003", password: "24681235" },
  { username: "u004", password: "31254876" },
  { username: "u005", password: "23546718" },
];

app.get("/patients/:username", (req, res) => {
  const patientSearch = dummy_patients.find(
    (patient) => patient.username === req.params.username
  );

  if (patientSearch) res.send(patientSearch);
  else res.status(404).send("Username couldnt be found");
});

app.listen(PORT, () => {
  console.log(`running on port ${PORT}`);
});
```
