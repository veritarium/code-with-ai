# Chapter 2: Effective Prompting Techniques

## Why Prompting Matters

The quality of Claude Code's output directly correlates with the quality of your input. A well-crafted prompt can mean the difference between a perfect solution and multiple rounds of corrections.

## The Anatomy of a Good Prompt

### 1. Be Specific About What You Want

**Vague:**
```
Fix the bug
```

**Specific:**
```
Fix the null pointer exception in the getUserById function in src/services/user.js that occurs when the user ID doesn't exist in the database
```

### 2. Provide Context

Claude Code can read your files, but telling it where to look saves time.

**Without context:**
```
Add input validation
```

**With context:**
```
Add input validation to the registration form in src/components/RegisterForm.tsx. Validate that email is a valid format and password is at least 8 characters.
```

### 3. Specify the Desired Outcome

**Unclear outcome:**
```
Make the API better
```

**Clear outcome:**
```
Refactor the /api/users endpoint to return paginated results with a default page size of 20, including total count in the response
```

## Prompting Patterns

### The Task-Context-Constraints Pattern

Structure your prompts with three components:

```
[TASK]: What you want done
[CONTEXT]: Relevant background information
[CONSTRAINTS]: Limitations or requirements
```

**Example:**
```
Add a caching layer to the database queries.
The app uses PostgreSQL with the pg library.
Use Redis for caching with a 5-minute TTL, and don't modify the existing query interface.
```

### The Example-Driven Pattern

Show Claude what you want through examples:

```
Create a validation function for user input. It should work like this:

validate({ name: "" }) → { valid: false, errors: ["name is required"] }
validate({ name: "Jo" }) → { valid: false, errors: ["name must be at least 3 characters"] }
validate({ name: "John" }) → { valid: true, errors: [] }
```

### The Incremental Pattern

Break complex tasks into steps:

```
Step 1: First, show me the current structure of the authentication module

Step 2: Now add a password reset function that generates a token

Step 3: Add the API endpoint that calls this function

Step 4: Write tests for the new functionality
```

## Scoping Your Requests

### Single File Focus
```
In src/utils/format.js, add a function to format phone numbers as (XXX) XXX-XXXX
```

### Multi-File Changes
```
Rename the User model to Account across the entire codebase, updating all imports and references
```

### Project-Wide Tasks
```
Find all API endpoints that don't have error handling and list them
```

## Refinement Techniques

### Iterative Refinement
Start broad, then narrow down:

```
→ Show me how authentication works in this project
← [Claude explains the auth flow]

→ Now add rate limiting to the login endpoint
← [Claude adds rate limiting]

→ Change the limit to 5 attempts per minute instead of 10
← [Claude adjusts the limit]
```

### Correction Prompts
When Claude gets something wrong:

**Don't:**
```
That's wrong, try again
```

**Do:**
```
The function should return a Promise, not use callbacks. Also use the existing logger from src/utils/logger.js instead of console.log
```

### Building on Previous Work
Reference earlier context:

```
Take the validation function you just created and add support for custom error messages
```

## Prompts for Common Tasks

### Code Review
```
Review src/services/payment.js for security issues, particularly around input handling and data sanitization
```

### Debugging
```
The test in tests/user.test.js line 45 is failing with "expected 3 but got 2". Help me understand why and fix it
```

### Refactoring
```
Refactor the OrderProcessor class to use dependency injection instead of creating its own database connection
```

### Documentation
```
Add JSDoc comments to all exported functions in src/utils/helpers.js
```

### Testing
```
Write unit tests for the calculateTotal function in src/cart.js covering edge cases: empty cart, single item, multiple items, and items with discounts
```

### Learning a Codebase
```
Explain how data flows from the API request to the database in this project. Start from the route handlers.
```

## What to Avoid

### Ambiguous Pronouns
**Bad:**
```
Update it to handle that case
```

**Good:**
```
Update the validateEmail function to handle empty strings by returning false
```

### Assumed Knowledge
**Bad:**
```
Do it the usual way
```

**Good:**
```
Use the repository pattern that's already established in src/repositories/
```

### Multiple Unrelated Tasks
**Bad:**
```
Fix the login bug, add a logout button, and also update the README with the new API endpoints
```

**Good:** (Ask separately or be explicit)
```
I have three tasks. Let's start with fixing the login bug in src/auth/login.js where the session isn't being saved.
```

## Advanced Techniques

### Asking for Alternatives
```
Show me three different ways to implement caching for this function, with pros and cons of each
```

### Requesting Explanations with Code
```
Add retry logic to the API client and explain why you chose that retry strategy
```

### Setting Quality Standards
```
Implement the search feature following the patterns in the existing codebase. Match the error handling style in src/services/userService.js
```

### Using File References
```
Create a new service following the same pattern as src/services/emailService.js but for SMS notifications
```

## Exercise: Prompt Improvement

Take this vague prompt and improve it:

**Original:**
```
Make the app faster
```

**Improved version might be:**
```
Profile the /api/products endpoint which currently takes 3+ seconds to respond. Identify the slowest database queries and add appropriate indexes or query optimizations. The endpoint is defined in src/routes/products.js.
```

Practice rewriting these vague prompts:
1. "Add error handling"
2. "Clean up this code"
3. "Make it work with TypeScript"

## Summary

Effective prompting is a skill that improves with practice. Remember:

- Be specific about files, functions, and desired outcomes
- Provide relevant context
- Use patterns: task-context-constraints, example-driven, incremental
- Refine iteratively rather than expecting perfection on the first try
- Avoid ambiguity and assumed knowledge

---

[← Previous: Getting Started](01-getting-started.md) | [Home](../README.md) | [Next: Files and Code →](03-files-and-code.md)
