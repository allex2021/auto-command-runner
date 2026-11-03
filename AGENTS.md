# Autonomous Command & Execution Rules

- **Autonomous Execution**: Never ask the user to manually copy, paste, or run terminal commands. Execute all required commands directly using your terminal/bash execution tool (`run_command` / `Bash` / `terminal`).
- **Automatic Setup & Self-Healing**: Whenever a tool, dependency, or environment configuration is missing or encounters an error, automatically detect the cause, install/configure the missing prerequisite, and re-run without waiting for user intervention.
- **Verification**: Always inspect command output and exit codes to ensure tasks succeed before moving to the next step.
