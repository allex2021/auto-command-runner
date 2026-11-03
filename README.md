# Antigravity Auto-Command Runner 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Antigravity Plugin](https://img.shields.io/badge/Antigravity-Plugin-green.svg)](https://github.com/allex2021/antigravity-auto-command-runner)

An autonomous execution and self-healing environment setup plugin for **Google Antigravity**, **Claude Code**, and **Codex**.

---

## ⚡ What it Does

By default, coding agents often hesitate when executing terminal commands or ask users to copy-paste commands manually into their terminal.

**Auto-Command Runner** equips your agent with:
1. **Fully Autonomous Execution**: Commands are automatically executed via `run_command` without bothering the user.
2. **Pre-flight Dependency Detection**: Automatically identifies missing CLI tools, packages, or runtimes and installs them.
3. **Self-Healing Error Recovery**: If a command fails (e.g. port collision, missing library, broken path), the agent analyzes the stack trace, fixes the root cause, and retries automatically.
4. **Daemon & Background Process Management**: Starts long-running processes (e.g. dev servers, watchers) properly in the background.

---

## 📦 Installation

### Antigravity CLI
Install directly with the Antigravity CLI:
```bash
agy plugin install https://github.com/allex2021/antigravity-auto-command-runner
```

### Manual Installation (Antigravity Global)
Clone into your global Antigravity plugins directory:
```bash
git clone https://github.com/allex2021/antigravity-auto-command-runner.git ~/.gemini/config/plugins/antigravity-auto-command-runner
```

### Local Project (Workspace Scope)
Add it directly to your project:
```bash
mkdir -p .agents/plugins
git clone https://github.com/allex2021/antigravity-auto-command-runner.git .agents/plugins/antigravity-auto-command-runner
```

---

## 🛠️ Structure

```text
antigravity-auto-command-runner/
├── plugin.json
├── LICENSE
├── README.md
├── rules/
│   └── AGENTS.md
└── skills/
    └── auto-command-runner/
        └── SKILL.md
```

---

## 📄 License
This project is licensed under the [MIT License](LICENSE).
