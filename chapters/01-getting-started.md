# Chapter 1: Getting Started with Claude Code

## What is Claude Code?

Claude Code is Anthropic's official command-line interface (CLI) tool that brings Claude's AI capabilities directly into your terminal. It's designed for software engineering tasks: writing code, debugging, refactoring, exploring codebases, and automating development workflows.

Unlike chat-based interfaces, Claude Code operates directly in your development environment with access to your files, terminal, and tools.

## Installation

### Prerequisites
- Node.js 18 or higher
- A terminal (bash, zsh, PowerShell, etc.)

### Install via npm
```bash
npm install -g @anthropic-ai/claude-code
```

### Verify Installation
```bash
claude --version
```

## First Launch

Start Claude Code by running:
```bash
claude
```

On first launch, you'll be prompted to authenticate with your Anthropic account. Follow the browser-based authentication flow.

## Your First Interaction

Once authenticated, you're in an interactive session. Try these starter commands:

**Ask a question:**
```
What files are in this directory?
```

**Request a task:**
```
Create a simple Python hello world script
```

**Get help:**
```
/help
```

## Understanding the Interface

### The Prompt
Claude Code presents a prompt where you type natural language requests. There's no special syntax required - just describe what you want.

### Tool Usage
Claude Code has access to tools that let it:
- Read and write files
- Execute terminal commands
- Search through codebases
- Make web requests

When Claude uses a tool, you'll see what it's doing. For sensitive operations (like running commands or editing files), you may be asked to approve the action.

### Slash Commands
Built-in commands start with `/`:
- `/help` - Show available commands
- `/clear` - Clear conversation history
- `/model` - Change the AI model
- `/cost` - Show token usage and costs

## Key Concepts

### Context Awareness
Claude Code understands your working directory. When you start it in a project folder, it can:
- Read your source files
- Understand project structure
- Run your build commands
- Execute tests

### Conversation Memory
Your conversation persists throughout the session. Claude remembers what you've discussed and can reference earlier context.

### CLAUDE.md Files
Projects can include a `CLAUDE.md` file with project-specific instructions. Claude Code reads this automatically to understand project conventions, build commands, and architecture.

## Best Practices for Beginners

1. **Start in your project directory** - Launch Claude Code from the root of your project for best context.

2. **Be specific** - "Fix the bug in the login function" works better than "fix it."

3. **Review changes** - Always review file modifications before accepting them.

4. **Use iterative refinement** - If the first result isn't right, provide feedback and ask for adjustments.

## Exercise: Your First Task

Try this hands-on exercise:

1. Create a new directory for practice:
   ```bash
   mkdir claude-practice && cd claude-practice
   ```

2. Launch Claude Code:
   ```bash
   claude
   ```

3. Ask Claude to create a simple project:
   ```
   Create a Python script that takes a name as a command-line argument and prints a personalized greeting
   ```

4. Run the created script to verify it works.

5. Ask Claude to enhance it:
   ```
   Add error handling for when no name is provided
   ```

## Summary

You've learned:
- What Claude Code is and how to install it
- How to start an interactive session
- The basic interface and slash commands
- Key concepts: context awareness, conversation memory, and CLAUDE.md
- Best practices for effective usage

---

[Home](../README.md) | [Next: Prompting Techniques →](02-prompting-techniques.md)
