# Chapter 3: Working with Files and Code

## How Claude Code Interacts with Your Files

Claude Code has direct access to your filesystem within your working directory. It can read files, create new ones, edit existing code, and search through your entire codebase. Understanding these capabilities helps you leverage them effectively.

## Reading Files

### Automatic File Reading

When you reference a file, Claude Code reads it automatically:

```
What does src/utils/helpers.js do?
```

Claude will read the file and explain its contents.

### Explicit Read Requests

Be explicit when you want to examine specific files:

```
Read the package.json and tell me what dependencies this project uses
```

```
Show me the contents of src/config/database.js
```

### Reading Multiple Files

You can ask Claude to read several files at once:

```
Read all the files in src/models/ and explain the data schema
```

```
Compare src/services/oldAuth.js and src/services/newAuth.js
```

### Partial File Reading

For large files, focus on what you need:

```
Show me the first 50 lines of src/app.js
```

```
Find the handleSubmit function in src/components/Form.tsx and show it to me
```

## Creating Files

### New File Creation

Ask Claude to create files with specific content:

```
Create a new file src/utils/validation.js with functions for email and phone validation
```

```
Create a React component in src/components/Button.tsx that accepts label and onClick props
```

### Creating Multiple Files

Claude can scaffold multiple files at once:

```
Create a new Express route for /api/products with the controller in src/controllers/productController.js and the route definition in src/routes/products.js
```

### File from Template

Reference existing patterns:

```
Create a new service file src/services/orderService.js following the same structure as src/services/userService.js
```

## Editing Files

### Targeted Edits

Specify exactly what to change:

```
In src/api/users.js, change the default page size from 10 to 25
```

```
Replace all console.log statements in src/services/ with calls to the logger utility
```

### Function-Level Changes

Focus on specific functions:

```
Rewrite the calculateDiscount function in src/pricing.js to handle percentage and fixed amount discounts
```

```
Add error handling to the fetchUser function in src/api/client.js
```

### Adding to Existing Files

Insert new code in the right place:

```
Add a new method called findByEmail to the User class in src/models/User.js
```

```
Add input validation at the beginning of the createOrder function in src/services/orderService.js
```

### Bulk Edits

Make consistent changes across files:

```
Rename the variable 'userData' to 'userProfile' in all files under src/components/
```

```
Add TypeScript types to all functions in src/utils/
```

## Searching Your Codebase

### Finding Files

Locate files by name or pattern:

```
Find all test files in this project
```

```
Where is the database configuration file?
```

### Searching Content

Search for specific code patterns:

```
Find all places where we call the deprecated getUserData function
```

```
Show me all files that import from src/legacy/
```

### Understanding Code Flow

Trace how code connects:

```
Find where the handlePayment function is called from
```

```
What components use the useAuth hook?
```

### Finding Patterns

Identify code patterns across your project:

```
Find all API endpoints that don't have authentication middleware
```

```
List all React components that use local state instead of the global store
```

## File Operations Best Practices

### Always Verify Before Large Changes

For significant modifications, ask Claude to show you first:

```
Show me all the files that would be affected if I rename the User model to Account
```

Then proceed:

```
Go ahead and make those changes
```

### Use Relative Paths

Reference files relative to your project root:

```
Edit src/components/Header.tsx
```

Not:

```
Edit /home/user/projects/myapp/src/components/Header.tsx
```

### Be Specific About Locations

When a filename might exist in multiple places:

```
Edit the index.js in the src/routes/ folder, not the one in src/
```

### Review Changes

After Claude makes edits, verify them:

```
Show me the changes you just made to src/api/users.js
```

## Working with Different File Types

### Source Code

Claude handles most programming languages:

```
Add type annotations to the Python functions in src/utils.py
```

```
Convert this JavaScript file to TypeScript
```

### Configuration Files

Edit configs with understanding of their format:

```
Add a new script called "test:coverage" to package.json that runs jest with coverage
```

```
Update the .env.example to include the new REDIS_URL variable
```

### Documentation

Work with markdown and other docs:

```
Update the API documentation in docs/api.md to include the new /products endpoint
```

### Data Files

Handle JSON, YAML, and other data formats:

```
Add a new entry to the fixtures/users.json test data
```

```
Update the docker-compose.yml to add a Redis service
```

## Common File Tasks

### Refactoring Across Files

```
Extract the validation logic from src/controllers/userController.js into a separate src/validators/userValidator.js file and update the import
```

### Moving and Reorganizing

```
Move all utility functions from src/helpers.js into separate files under src/utils/ organized by category
```

### Cleaning Up

```
Find and remove all unused imports in the src/components/ directory
```

### Adding Tests

```
Create a test file for src/services/authService.js in the tests/ directory with tests for the login and logout functions
```

## Understanding Project Structure

### Initial Exploration

When starting with a new codebase:

```
Give me an overview of this project's structure and architecture
```

```
What framework is this project using and how is it organized?
```

### Deep Dives

Once you understand the basics:

```
Explain how the authentication flow works, starting from the login form
```

```
How does data get from the API to the UI components?
```

## Exercise: File Operations Practice

Try these tasks in a practice project:

1. **Explore:**
   ```
   List all JavaScript files in this project and categorize them by their purpose
   ```

2. **Create:**
   ```
   Create a new utility file src/utils/strings.js with functions for capitalizing, truncating, and slugifying strings
   ```

3. **Edit:**
   ```
   Add JSDoc comments to all functions in the file you just created
   ```

4. **Search:**
   ```
   Find all TODO comments in the codebase
   ```

5. **Refactor:**
   ```
   The strings utility is getting big. Split it into separate files: capitalize.js, truncate.js, and slugify.js, with an index.js that re-exports them all
   ```

## Summary

Claude Code's file capabilities let you:

- **Read** any file in your project instantly
- **Create** new files with proper structure and content
- **Edit** existing code with surgical precision or broad refactoring
- **Search** across your entire codebase for patterns and references

Key principles:
- Be specific about file paths and locations
- Verify before making large-scale changes
- Use Claude's understanding of code to make smart, contextual edits
- Leverage search to understand unfamiliar codebases

## Next Chapter

In Chapter 4, we'll explore using the terminal and bash commands through Claude Code for running builds, tests, and other development tasks.
