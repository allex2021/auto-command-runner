# Auto-Command Runner 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub release](https://img.shields.io/badge/Release-v1.0.0-green.svg)](https://github.com/allex2021/auto-command-runner)
[![Compatible with](https://img.shields.io/badge/Compatible%20With-Antigravity%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20Cursor-purple.svg)](https://github.com/allex2021/auto-command-runner)

Universal autonomous command execution and self-healing environment setup plugin for **Google Antigravity**, **Anthropic Claude Code**, **OpenAI Codex**, and **Cursor**.

---

## ⚡ What it Does

By default, coding agents often hesitate when executing terminal commands or ask users to copy-paste commands manually into their terminal.

**Auto-Command Runner** equips your agent with:
1. **Fully Autonomous Execution**: Commands are automatically executed via the agent's native bash/terminal tool without bothering the user.
2. **Pre-flight Dependency Detection**: Automatically identifies missing CLI tools, packages, or runtimes (npm, pip, brew, etc.) and installs them.
3. **Self-Healing Error Recovery**: If a command fails (port collision, missing package, wrong path, etc.), the agent diagnoses the root cause, fixes the issue, and retries automatically.
4. **Daemon & Background Management**: Spawns long-running servers and watchers without freezing the agent session.

---

## 📦 Installation Guide

### 1. Google Antigravity
Install with the Antigravity CLI:
```bash
agy plugin install https://github.com/allex2021/auto-command-runner
```
Or clone globally into `~/.gemini/config/plugins/`:
```bash
git clone https://github.com/allex2021/auto-command-runner.git ~/.gemini/config/plugins/auto-command-runner
```

### 2. Anthropic Claude Code
Add the marketplace and install:
```bash
claude plugin marketplace add allex2021/auto-command-runner
claude plugin install auto-command-runner@auto-command-runner
```

### 3. OpenAI Codex
Add the plugin repository:
```bash
codex plugin marketplace add allex2021/auto-command-runner
codex plugin add auto-command-runner@auto-command-runner
```

### 4. Cursor / Any Coding Agent (Workspace Scope)
Simply clone into your project's `.agents` directory:
```bash
git clone https://github.com/allex2021/auto-command-runner.git .agents/plugins/auto-command-runner
```
The included `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, and `.cursorrules` are automatically detected and loaded.

---

## 🛠️ Repository Architecture

```text
auto-command-runner/
├── plugin.json                 # Universal Open Plugins manifest
├── .claude-plugin/             # Anthropic Claude Code manifest & marketplace
│   ├── marketplace.json
│   └── plugin.json
├── .codex-plugin/              # OpenAI Codex manifest
│   └── plugin.json
├── AGENTS.md                   # Codex / Universal agent rules
├── CLAUDE.md                   # Claude Code rules
├── GEMINI.md                   # Antigravity / Gemini rules
├── .cursorrules                # Cursor AI rules
├── LICENSE                     # MIT License
├── README.md                   # Universal documentation
├── rules/
│   └── AGENTS.md
└── skills/
    └── auto-command-runner/
        └── SKILL.md            # Universal portable skill
```

---

## 📄 License
This project is licensed under the [MIT License](LICENSE).
