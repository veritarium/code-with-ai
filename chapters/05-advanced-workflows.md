# Chapter 5: Advanced Workflows

## Beyond the Basics

This chapter combines everything you've learned into powerful, real-world workflows. These patterns will help you tackle complex development tasks efficiently.

## Project Onboarding

### Rapid Codebase Understanding

When joining a new project, use this sequence:

```
Give me a high-level overview of this project's architecture and tech stack
```

```
What are the main entry points to this application?
```

```
How does data flow from the frontend to the database?
```

```
What are the key abstractions and patterns used in this codebase?
```

### Finding Your Way

```
Where would I add a new API endpoint?
```

```
Show me an example of how other features handle form validation
```

```
What's the testing strategy here? Show me a well-written test as an example.
```

### Setting Up to Contribute

```
What do I need to run this project locally? Walk me through the setup.
```

```
Are there any environment variables I need to configure?
```

```
Run the tests to verify my setup is working correctly.
```

## Feature Development Workflow

### Phase 1: Planning

Start by understanding the scope:

```
I need to add a password reset feature. What existing code can I build on? Where should the new code live?
```

### Phase 2: Scaffolding

Create the structure:

```
Create the files I'll need for the password reset feature:
- A new route in the API
- A service function for generating reset tokens
- An email template for the reset link
- A frontend page for entering a new password
```

### Phase 3: Implementation

Build incrementally:

```
Implement the token generation in the password reset service. Tokens should expire after 1 hour.
```

```
Now add the API endpoint that sends the reset email
```

```
Create the frontend form for entering and confirming the new password
```

### Phase 4: Testing

```
Write tests for the password reset service covering: valid token, expired token, invalid token, and token reuse
```

```
Run the tests and fix any failures
```

### Phase 5: Polish

```
Review the password reset feature for security issues
```

```
Add appropriate error handling and user-friendly error messages
```

## Debugging Complex Issues

### Systematic Investigation

When facing a tricky bug:

```
Users report that checkout fails intermittently. Help me investigate. Start by finding all code paths involved in the checkout process.
```

```
Show me everywhere exceptions are caught and potentially swallowed in the checkout flow
```

```
What external services does checkout depend on? Are there timeout configurations?
```

### Log-Driven Debugging

```
Search the logs for checkout-related errors from the past hour
```

```
I see a "connection reset" error. Find all places we connect to external services and check the retry logic.
```

### Reproducing Issues

```
Create a test that simulates the checkout failure scenario based on what we found
```

```
Run the test with verbose logging to see exactly where it fails
```

### Implementing the Fix

```
Add retry logic with exponential backoff to the payment service client
```

```
Add better error logging so we can diagnose this faster next time
```

```
Run the full test suite to make sure the fix doesn't break anything else
```

## Code Review Workflow

### Reviewing Your Own Code

Before submitting:

```
Review the changes I've made for this feature. Look for bugs, security issues, and code quality problems.
```

```
Are there any edge cases I'm not handling?
```

```
Check if my code follows the patterns established elsewhere in this codebase
```

### Responding to Review Feedback

```
A reviewer commented that my error handling is inconsistent. Show me all the error handling in my changes and suggest improvements.
```

```
Make the suggested changes from the review: use early returns and extract the validation logic
```

## Refactoring Patterns

### Safe Refactoring Sequence

1. **Ensure test coverage:**
   ```
   What's the test coverage for src/services/orderService.js? Write tests for any untested functions.
   ```

2. **Run baseline:**
   ```
   Run all tests and confirm they pass
   ```

3. **Make changes:**
   ```
   Refactor orderService to use dependency injection instead of direct database imports
   ```

4. **Verify:**
   ```
   Run the tests again and make sure nothing broke
   ```

### Large-Scale Refactoring

For bigger changes, work incrementally:

```
I want to migrate from callbacks to async/await across the codebase. Start by listing all files that use callbacks.
```

```
Let's start with the smallest file. Migrate it to async/await and run its tests.
```

```
That worked. Now do the next file.
```

Continue until complete, testing at each step.

### Extracting Modules

```
The utils.js file is 2000 lines. Analyze it and suggest how to split it into focused modules.
```

```
Extract all the date-related functions into a new dateUtils.js file, update all imports, and verify tests pass.
```

## Test-Driven Development

### TDD Cycle with Claude

**Red:**
```
Write a failing test for a new calculateShipping function that returns free shipping for orders over $50
```

**Green:**
```
Implement calculateShipping to make the test pass. Keep it simple.
```

**Refactor:**
```
Clean up the implementation if needed, making sure tests still pass
```

**Expand:**
```
Add tests for edge cases: exactly $50, negative amounts, international shipping
```

```
Update the implementation to handle all the new test cases
```

## Performance Optimization

### Identifying Bottlenecks

```
Profile the /api/products endpoint and identify what's slow
```

```
Show me the database queries this endpoint makes. Are there N+1 query problems?
```

### Implementing Optimizations

```
Rewrite the product listing query to use a single JOIN instead of multiple queries
```

```
Add an index to improve the product search query
```

```
Implement caching for the product categories that rarely change
```

### Measuring Improvement

```
Run the performance test again and compare to our baseline
```

## Database Workflows

### Schema Changes

```
I need to add a 'deleted_at' column to the users table for soft deletes. Create the migration.
```

```
Update the User model and all queries to respect the soft delete field
```

```
Add a way to query deleted users for admin purposes
```

### Data Migrations

```
We're splitting the 'name' field into 'firstName' and 'lastName'. Create a migration that:
1. Adds the new columns
2. Migrates existing data
3. Removes the old column
```

### Query Optimization

```
This query is slow. Analyze it and suggest improvements:
SELECT * FROM orders WHERE user_id = ? ORDER BY created_at DESC
```

## Multi-Service Workflows

### API Integration

```
I need to integrate with the Stripe API for payments. Show me how similar integrations are done in this codebase.
```

```
Create a stripe service module following that pattern
```

```
Add error handling that maps Stripe errors to our application error format
```

### Webhook Handling

```
Set up a webhook handler for Stripe payment events
```

```
Add signature verification to ensure webhooks are authentic
```

```
Write tests using mocked webhook payloads
```

## Documentation Workflows

### Code Documentation

```
Add JSDoc comments to all public functions in src/services/
```

```
Generate TypeScript type definitions from this JavaScript module
```

### API Documentation

```
Create an OpenAPI spec for the user management endpoints
```

```
The API has changed. Update the documentation to match the current implementation.
```

## CI/CD Workflows

### Fixing CI Failures

```
The CI build is failing. Analyze the error log and tell me what's wrong.
```

```
Fix the issue and verify it passes locally before pushing
```

### Adding CI Steps

```
Add a linting step to the GitHub Actions workflow
```

```
Configure the CI to run tests in parallel for faster builds
```

## Emergency Debugging

### Production Issues

When something's broken in production:

```
The API is returning 500 errors. Help me find the cause quickly. Start with recent changes.
```

```
Show me the git diff between the last working deploy and current
```

```
Check if there are any obvious errors in that diff
```

### Quick Fixes

```
Create a minimal fix for the production issue
```

```
Write a test that would have caught this bug
```

```
Add the test, verify the fix works, and prepare the commit
```

### Rollback Preparation

```
Show me how to revert to the previous commit if this fix doesn't work
```

## Session Management

### Long Sessions

For extended work sessions:

```
Summarize what we've accomplished so far and what's left to do
```

```
Before we continue, remind me of the approach we decided on for error handling
```

### Context Management

When context gets complex:

```
I've lost track. Show me the current state of the auth module after all our changes.
```

```
List all the files we've modified in this session
```

### Handoff

Preparing for others to continue:

```
Summarize the current state of this feature: what's done, what's in progress, and what's left
```

```
Are there any gotchas or decisions someone picking this up should know about?
```

## Combining Workflows

### Full Feature Cycle

A complete workflow combining multiple patterns:

```
1. "Create a branch for the user profile feature"
2. "What components exist that I can reference for building profile pages?"
3. "Create the profile page component following that pattern"
4. "Add the API endpoint for fetching user profiles"
5. "Write tests for both the frontend component and API"
6. "Run all tests and fix any issues"
7. "Review the changes for security and quality"
8. "Commit with a descriptive message"
9. "Push and create a pull request"
```

## Exercise: Real-World Scenario

Practice this complete workflow:

**Scenario:** Add a "favorites" feature where users can favorite products.

1. **Plan:**
   ```
   I need to add a favorites feature. Analyze the codebase and tell me where I should add: the database model, API endpoints, and frontend components.
   ```

2. **Database:**
   ```
   Create a favorites table migration and model
   ```

3. **Backend:**
   ```
   Add API endpoints for listing, adding, and removing favorites
   ```

4. **Frontend:**
   ```
   Add a favorite button component and integrate it with the product cards
   ```

5. **Test:**
   ```
   Write tests for the favorites functionality at all layers
   ```

6. **Review:**
   ```
   Review the entire feature for completeness and quality
   ```

7. **Ship:**
   ```
   Run all tests, commit the changes, and show me a summary of what was built
   ```

## Summary

Advanced workflows combine:
- **Understanding** the codebase before making changes
- **Planning** the approach before writing code
- **Incremental development** with testing at each step
- **Review and verification** before considering work complete

Master these patterns and you'll handle complex development tasks with confidence.

## Conclusion

You've completed the Claude Code tutorial. You now know how to:

1. **Get started** with Claude Code and navigate its interface
2. **Write effective prompts** that get accurate results
3. **Work with files** for reading, creating, and editing code
4. **Use the terminal** for builds, tests, and git operations
5. **Combine skills** into powerful development workflows

The best way to improve is practice. Start using Claude Code on real projects and these patterns will become second nature.

---

[← Previous: Terminal Commands](04-terminal-commands.md) | [Home](../README.md)
