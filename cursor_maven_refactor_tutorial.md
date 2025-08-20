# Learning Cursor AI for Context Engineering an Unknown Codebase

## Tutorial Objective

This guide will help you learn how to **use Cursor AI** to context/vibe engineer an existing codebase you’re not familiar with—either due to unfamiliarity with the **programming language**, the **domain**, or the **project scale**.

We’ll explore a real-world example using [MehrabRahman/JavaServer](https://github.com/MehrabRahman/JavaServer), a basic Java web server. Your goal: **Refactor the project for better maintainability**, **add proper logging**, **add documentation**, and **transition to a modern build system like Maven**.

> **This tutorial is designed for students and beginners**, so every step is explained with examples and learning tips. It’s okay if you don’t know Java!

---

## Part 1: Import and Explore the Codebase with Cursor AI

### 1.1 Clone the Project

Open Cursor and clone the project using:

```
git clone https://github.com/MehrabRahman/JavaServer
```

### 1.2 Open the Project in Cursor

Once open, Cursor will index the files and offer a **code-aware chat window** in the sidebar.

### 1.3 Begin Exploration: Ask Cursor to Summarize

Start with these prompts to understand the project:

```text
What is the purpose of this codebase?
Can you give me an overview of the major components?
What external libraries are used?
Can you explain the main entry point?
```

💡 Cursor will parse code, infer structure, and reply based on its understanding of files and symbols.

### 1.4 Ask for File and Folder Maps

```text
Chart the folder structure and describe what each folder or file does.
```

You’ll start seeing diagrams like:

```
JavaServer/
├── server/        # core HTTP server logic
├── client/        # client interaction logic
├── utils/         # helper functions
└── tests/         # test cases
```

### 1.5 Trace Data and Flow

Ask Cursor to chart the application’s flow:

```text
How does an HTTP request move through the code?
Can you follow a request from start to finish?
What classes are involved?
```

Let Cursor explain how classes or functions call one another.

---

## Part 2: Create Instruction Templates from Requirements

We’ll now turn goals into actionable steps.

### 2.1 Translate Requirements into Goals

Given the task:

> “Refactor the JavaServer codebase for maintainability and move to Maven.”

Ask Cursor:

```text
Break this requirement into broad goals.
```

Expected Output:

- Restructure the project for better readability.
- Add structured logging.
- Replace manual build system with Maven.
- Add Javadoc-style comments.
- Improve or add unit tests.

### 2.2 Break into Small Steps

Use this prompt:

```text
For each goal, break it into sub-tasks that are small and testable.
Add checkpoints for validation.
```

Example output for logging:

- Identify where logs are needed.
- Replace print statements with logger.
- Choose a logging library (e.g., `java.util.logging`).
- Add config file for logging level.
- Test with sample HTTP request.

### 2.3 Use AI to Generate Templates

Prompt Cursor:

```text
Create a reusable template to turn user stories or tasks into small, testable goals with clear exit criteria and checkpoints.
```

This creates a reusable workflow like:

```
[Goal]: Add structured logging

[Subtasks]:
1. Identify current output methods.
2. Choose and configure logging framework.
3. Replace system prints.
4. Test output with example requests.

[Checkpoints]:
[] Logger initialized
[] Console shows correct info/debug logs
[] Errors appear in logs with stack traces
```

---

## Part 3: Execute, Test, and Iterate with AI

### 3.1 Ask Cursor to Begin a Task

Pick a small task and ask:

```text
Implement step 1 of our plan: replace print statements with logger.
```

Cursor will modify files directly. You can monitor these changes in the **diff view**.

### 3.2 Validate the Output

Ask:

```text
What did you change?
Can you summarize the edits?
Show me a diff.
```

Use Cursor’s side-by-side comparison to **review changes before committing**.

### 3.3 Run Tests (Or Create Them)

If tests exist:

```bash
java -cp . tests/TestMain.java
```

Otherwise, ask:

```text
Can you create a unit test for the new logging behavior?
```

Cursor can help scaffold JUnit or similar test cases.

### 3.4 Use Version Control and Breakpoints

Always commit after successful checkpoints:

```bash
git add .
git commit -m "Replaced print statements with logger"
```

Ask Cursor:

```text
Pause here and add debug logs at all HTTP entry points.
```

This sets **manual breakpoints** using log statements before major operations.

---

## 🧰 Additional Tips

### 🔎 Use the Logging Template

```text
Create a logging config using java.util.logging for file-based and console-based logs.
```

### 📦 Setup Maven

Ask Cursor:

```text
Create a `pom.xml` for this project using Maven. Include dependencies for logging and testing.
```

Then ask:

```text
Move the codebase to follow standard Maven structure.
```

Resulting structure:

```
src/
  main/
    java/
      [your packages]
  test/
    java/
pom.xml
```

### 📓 Add Documentation

```text
Add Javadoc comments to all public classes and methods in server/
```

---

## 🧠 Learning While You Go

If you don’t understand something, ask Cursor directly:

```text
What does this method do?
Explain this Java syntax.
What's a static method?
```

It’s like having a tutor in your editor. Don’t hesitate to ask basic questions.

---

## ✅ Summary

By using Cursor AI and this workflow, you can:

- Explore unfamiliar codebases quickly
- Break complex tasks into manageable pieces
- Execute with precision using AI-assisted editing
- Learn the language and architecture as you go
- Keep your changes modular, documented, and testable
