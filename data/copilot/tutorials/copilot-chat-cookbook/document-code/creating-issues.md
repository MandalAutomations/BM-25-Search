# Creating issues

Copilot Chat can help you quickly create issues without filling out every field manually.

Creating issues manually can be time-consuming. Copilot Chat lets you create issues from natural language, and automatically fills in the title, body, labels, and other metadata based on your prompt.

## Example scenario

You're working on an API service and need to add server-side validation to the `createUser` endpoint. Instead of drafting the issue manually, you use Copilot Chat to generate a detailed issue description that includes an example implementation of the validation middleware.

The following snippet shows the current implementation of the `createUser` route, before validation is added:

```javascript
// Route
app.post('/users', validateCreateUser, (req, res) => {
  const { username, email } = req.body;
  // Simulate user creation
  res.status(201).json({ message: 'User created', user: { username, email } });
});
```

## Example prompt

`In octo-org/octo-repo, create an issue to add server-side validation for the createUser API endpoint. Include an example of how to validate the request body using an existing middleware pattern. Label it with "backend" and "enhancement".`

## Example response

> [!NOTE] The following response is an example. Copilot Chat responses are non-deterministic, so you may get a different response from the one shown here.

When you submit the prompt, Copilot Chat generates a draft issue based on your description and includes a code snippet. You can review and edit the draft before creating the issue.

```markdown
## Problem
The `createUser` API endpoint currently lacks robust server-side validation for incoming requests. To ensure data integrity and security, we should validate the request body before proceeding with user creation.

**Current API endpoint:**
// Route
app.post('/users', validateCreateUser, (req, res) => {
  const { username, email } = req.body;
  // Simulate user creation
  res.status(201).json({ message: 'User created', user: { username, email } });
});

## Proposal
- Add server-side validation for the request body using the existing middleware pattern.
- Ensure required fields (`username`, `email`) are present and valid.
- Return a 400 Bad Request response if validation fails.

**Example (middleware pattern):**
function validateCreateUser(req, res, next) {
  const { username, email } = req.body;
  if (!username || !email) {
    return res.status(400).json({ error: 'Username and email are required.' });
  }
  // Additional validation logic here
  next();
}

app.post('/users', validateCreateUser, (req, res) => {
  // ...
});

## Acceptance Criteria
- Server-side validation middleware is added to the `createUser` endpoint.
- Request body is properly validated.
- Appropriate error responses are returned for invalid requests.
```