# Chapter 4: Terminal and Bash Commands

## Claude Code and the Terminal

Claude Code can execute terminal commands directly in your shell. This enables running builds, tests, git operations, package management, and any other command-line tasks—all through natural language.

## Running Basic Commands

### Simple Execution

Ask Claude to run commands naturally:

```
Run npm install
```

```
Check the git status
```

```
List all running Docker containers
```

### Understanding Output

Claude reads command output and can interpret it:

```
Run the tests and tell me which ones failed
```

```
Run npm outdated and summarize which packages need updates
```

## Permission and Safety

### Command Approval

For potentially impactful commands, Claude will ask for approval before executing. You'll see:
- The exact command to be run
- Option to approve or reject

This protects against:
- Accidental file deletion
- Unintended system changes
- Running commands you didn't expect

### Trust Levels

As you work, you can adjust how Claude handles permissions:
- Approve individual commands one at a time
- Allow specific command patterns
- Trust certain categories of operations

## Package Management

### npm / yarn / pnpm

```
Install lodash as a dependency
```

```
Add jest as a dev dependency
```

```
Update all packages to their latest versions
```

```
Remove the unused moment package
```

### pip (Python)

```
Install requests and pandas
```

```
Create a requirements.txt from the current environment
```

### Other Package Managers

```
Add the serde crate to Cargo.toml
```

```
Install the gin-gonic package for Go
```

## Build and Development

### Running Builds

```
Build the project
```

```
Run the production build and tell me if there are any warnings
```

```
Build the Docker image for this project
```

### Development Servers

```
Start the development server
```

```
Run the app on port 4000 instead of the default
```

### Watch Mode

```
Start the TypeScript compiler in watch mode
```

```
Run the tests in watch mode
```

## Testing

### Running Tests

```
Run all tests
```

```
Run only the tests in the auth/ directory
```

```
Run tests matching "user login"
```

### Test Analysis

```
Run the tests and explain any failures
```

```
Run tests with coverage and tell me which files have low coverage
```

### Fixing Test Failures

```
Run the tests, and for any that fail, show me the failing test and the relevant code
```

Then:

```
Fix the failing tests
```

## Git Operations

### Status and Information

```
Show me the git status
```

```
What commits have been made today?
```

```
Show the diff of staged changes
```

### Branching

```
Create a new branch called feature/user-auth
```

```
Switch to the main branch
```

```
List all branches and show which one I'm on
```

### Committing

```
Stage all changed files and commit with message "Add user authentication"
```

```
Amend the last commit to include the files I just changed
```

### Remote Operations

```
Pull the latest changes from origin
```

```
Push this branch to origin
```

```
Fetch all remote branches
```

### History and Logs

```
Show the last 10 commits
```

```
Who last modified src/auth/login.js?
```

```
Show all commits that touched the payment module
```

## Environment and Configuration

### Environment Variables

```
Show me what environment variables are set
```

```
Run the app with NODE_ENV set to production
```

### System Information

```
What version of Node is installed?
```

```
Check if Redis is running
```

```
Show available disk space
```

## Docker Operations

### Containers

```
List all running containers
```

```
Stop the postgres container
```

```
Show logs from the api container
```

### Images

```
Build the Docker image with tag myapp:latest
```

```
List all Docker images
```

### Compose

```
Start all services with docker-compose
```

```
Restart just the web service
```

```
Tear down all containers and volumes
```

## Chaining Commands

### Sequential Tasks

Ask for multi-step operations:

```
Pull the latest changes, install dependencies, and run the tests
```

```
Build the project, run linting, and then run tests
```

### Conditional Workflows

```
Run the tests, and if they pass, build the production bundle
```

```
Check if port 3000 is in use, and if so, kill the process using it
```

## Debugging with Terminal

### Process Inspection

```
What's using port 8080?
```

```
Show me the most CPU-intensive processes
```

```
Is the node process still running?
```

### Log Analysis

```
Show the last 50 lines of the application log
```

```
Search the logs for any errors from today
```

### Network Debugging

```
Test if the API at localhost:3000 is responding
```

```
Check if I can reach the database host
```

## Long-Running Commands

### Background Processes

For commands that run continuously:

```
Start the server in the background
```

### Timeouts

Claude handles commands that might hang:

```
Run the database migration (this might take a few minutes)
```

### Stopping Processes

```
Stop the running development server
```

## Scripting and Automation

### Running Scripts

```
Run the deployment script in scripts/deploy.sh
```

```
Execute the database seed script
```

### Creating Scripts

```
Create a shell script that backs up the database and uploads it to S3
```

Then:

```
Run the backup script you just created
```

## Best Practices

### Be Explicit About Intent

**Vague:**
```
Clean up
```

**Clear:**
```
Remove all node_modules directories and clear the npm cache
```

### Understand Before Running

For unfamiliar commands:

```
What would this command do: find . -name "*.log" -delete
```

### Check State First

Before destructive operations:

```
Show me what files would be deleted by git clean -fd
```

Then if satisfied:

```
Go ahead and run git clean -fd
```

### Use Dry Runs

When available:

```
Run rsync with --dry-run first to show what would be synced
```

## Common Workflows

### Starting a New Feature

```
Create a new branch called feature/shopping-cart, then install dependencies and start the dev server
```

### Preparing for Commit

```
Run the linter, fix any issues, then run tests to make sure everything passes
```

### Deployment Preparation

```
Build the production bundle, run all tests, and show me the bundle size
```

### Debugging a Problem

```
Check if the database is running, show recent error logs, and test the API health endpoint
```

## Exercise: Terminal Mastery

Practice these terminal workflows:

1. **Project Setup:**
   ```
   Clone a git repository, install dependencies, and verify it runs
   ```

2. **Git Workflow:**
   ```
   Create a branch, make a change, commit it, and show the diff against main
   ```

3. **Debug Scenario:**
   ```
   The app won't start. Check if required services are running, verify environment variables, and look for errors in recent logs
   ```

4. **Build Pipeline:**
   ```
   Run linting, then tests, then build—stopping if any step fails
   ```

## Summary

Claude Code's terminal integration lets you:

- **Execute** any shell command through natural language
- **Analyze** command output for errors, warnings, and information
- **Chain** multiple commands for complex workflows
- **Manage** git, Docker, packages, and builds conversationally

Key principles:
- Claude asks permission for impactful commands
- Be explicit about what you want to achieve
- Use dry runs and previews for destructive operations
- Chain related commands for efficient workflows

## Next Chapter

In Chapter 5, we'll explore advanced workflows—combining everything you've learned into powerful development patterns.
