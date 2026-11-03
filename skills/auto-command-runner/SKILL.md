---
name: auto-command-runner
description: >-
  Automatically detects, sets up, self-heals, and executes any required shell, environment, or system commands without manual user intervention.
  Compatible with Antigravity, Claude Code, OpenAI Codex, and Cursor.
  Use whenever any task requires executing terminal commands, installing dependencies, running CLI tools, starting servers, or resolving command execution errors.
---

# Autonomous Command Runner & Environment Setup Skill

## Purpose
This skill empowers AI coding agents across **Antigravity**, **Claude Code**, **Codex**, and **Cursor** to handle terminal and environment operations autonomously. Whenever a command is needed to accomplish a task, the agent must configure, diagnose, install dependencies for, and execute that command directly instead of prompting the user to run it manually.

## Core Rules & Execution Flow

### 1. Autonomous Execution
- Never instruct the user to copy-paste or execute commands in their terminal.
- Execute all commands directly using your harness terminal tool:
  - **Antigravity**: `run_command`
  - **Claude Code**: `Bash`
  - **Codex / OpenCode**: `bash` / `terminal`
  - **Cursor**: background / terminal executor

### 2. Dependency & Environment Pre-flight
- Before executing a tool or script, verify that required runtimes/binaries exist (e.g., `which <tool>`).
- If a dependency is missing:
  - **Node.js**: Automatically run `npm install <package>` or `npm install`.
  - **Python**: Automatically check virtualenv/environment and run `pip install <package>` or `uv pip install`.
  - **macOS / Linux CLI tools**: Check availability with `which` and install via package managers (`brew`, `apt`) or direct download when appropriate.

### 3. Self-Healing Error Recovery
- If any command fails (non-zero exit code or error output):
  1. Inspect the error log or `stderr`.
  2. Diagnose the root cause (e.g., missing package, blocked port, missing directory, incorrect path, permission).
  3. Automatically apply the fix (e.g., install the missing package, terminate lingering process on the port, create required directories).
  4. Re-run the command to confirm success.
  5. Repeat until resolved, or report the specific blocker if external human credential input is needed.

### 4. Background and Daemon Management
- For long-running processes (e.g., web servers, dev servers, watchers):
  - Start the process in the background / daemon mode so the agent session continues smoothly without hanging.

### 5. Safety Guardrails
- Never execute irreversible data destruction (`rm -rf /`, broad disk wipes, `DROP DATABASE`, etc.) without explicit verification.
