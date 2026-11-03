---
name: auto-command-runner
description: >-
  Automatically detects, sets up, self-heals, and executes any required shell, environment, or system commands without manual user intervention.
  Use whenever any task requires executing terminal commands, installing dependencies, running CLI tools, starting servers, or resolving command execution errors.
---

# Autonomous Command Runner & Environment Setup Skill

## Purpose
This skill empowers the agent to handle terminal operations autonomously. Whenever a command is needed to accomplish a task, the agent must configure, diagnose, install dependencies for, and execute that command directly instead of prompting the user to run it manually.

## Core Rules & Execution Flow

### 1. Autonomous Execution
- Never instruct the user to copy-paste or execute commands in their terminal.
- Execute all commands directly using `run_command`.

### 2. Dependency & Environment Pre-flight
- Before executing a tool or script, verify that required runtimes/binaries exist (e.g., `which <tool>`).
- If a dependency is missing:
  - **Node.js**: Automatically run `npm install <package>` or `npm install`.
  - **Python**: Automatically check the virtualenv and run `pip install <package>`.
  - **macOS / CLI tools**: Check availability with `which` and install via `brew` or direct download if appropriate.

### 3. Self-Healing Error Recovery
- If any command fails (non-zero exit code or error output):
  1. Inspect the error log or `stderr`.
  2. Diagnose the root cause (e.g., missing package, blocked port, missing directory, incorrect path, permission).
  3. Automatically apply the fix (e.g., install the missing package, kill lingering process on the port, create required directories).
  4. Re-run the command to confirm success.
  5. Repeat until resolved or report the specific external blocker if human credential intervention is needed.

### 4. Background and Daemon Management
- For long-running processes (e.g., web servers, dev servers, watchers):
  - Set `IsDaemon: true` and appropriate `WaitMsBeforeAsync` so execution continues smoothly without hanging.

### 5. Safety Guardrails
- Never execute irreversible data destruction (`rm -rf /`, `DROP DATABASE`, etc.) without verification.
