# AI Slash Commands

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Commands](https://img.shields.io/badge/commands-1-purple.svg)](#available-commands)

> Reusable slash commands for AI coding assistants — stop repeating yourself, start shipping faster.

## Table of Contents

- [Why Slash Commands?](#why-slash-commands)
- [Quick Start](#quick-start)
- [Available Commands](#available-commands)
- [Installation & Setup](#installation--setup)
  - [Claude Code](#claude-code)
  - [Cursor](#cursor)
  - [GitHub Copilot](#github-copilot)
  - [Any AI Assistant](#any-ai-assistant)
- [Command Reference: /mvp](#command-reference-mvp)
- [Examples](#examples)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Project Status & Roadmap](#project-status--roadmap)
- [Contributing](#contributing)
- [Related Projects](#related-projects)
- [License](#license)

---

## Why Slash Commands?

### The Problem

Every time you ask an AI to help with development, you write detailed instructions:

> "I need you to analyze this spec and create an implementation plan. Make sure to identify the critical path, break it into phases, consider dependencies, use TDD principles, and output a structured plan file..."

You repeat this. Every. Single. Time.

### The Solution

Slash commands are **reusable prompt templates** that encapsulate best practices:

```
/mvp product-spec.md
```

One command. The AI knows exactly what methodology to follow, what output to produce, and what questions to ask.

### Benefits

| Benefit | Description |
|---------|-------------|
| **Consistency** | Same high-quality process every time |
| **Efficiency** | No more writing detailed instructions |
| **Best Practices** | Methodology baked into commands |
| **Shareable** | Team-wide standards via version control |
| **Extensible** | Add your own commands for your workflows |

### How It Works

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Your Request   │ ──▶ │  Slash Command   │ ──▶ │  Structured     │
│  /mvp spec.md   │     │  (Methodology +  │     │  Output         │
│                 │     │   Instructions)  │     │  (plan.md)      │
└─────────────────┘     └──────────────────┘     └─────────────────┘
```

---

## Quick Start

**1. Clone this repo:**
```bash
git clone https://github.com/CarlosFelipeF/ai-slash-commands.git
```

**2. Pick a command** (e.g., `/mvp`)

**3. Use it with your AI assistant:**
```
/mvp my-product-spec.md
```

That's it. See [Installation & Setup](#installation--setup) for detailed integration options.

---

## Available Commands

| Command | Description | Category | File |
|---------|-------------|----------|------|
| `/mvp <spec-file>` | Transform product specs into phased implementation plans using tracer bullet methodology | Planning | [commands/mvp.md](commands/mvp.md) |

*More commands coming soon! See [Roadmap](#project-status--roadmap) or [contribute your own](CONTRIBUTING.md).*

---

## Installation & Setup

### Claude Code

Add to your project's Claude instructions (`.claude/settings.json` or project settings):

```json
{
  "instructions": "When I use /mvp, follow the instructions in commands/mvp.md from the ai-slash-commands repository."
}
```

Or reference the file directly in conversation:
```
Read commands/mvp.md and apply it to my-spec.md
```

### Cursor

Add to your `.cursorrules` file:

```
# Slash Commands
When the user invokes /mvp, read and follow the instructions in commands/mvp.md

@commands/mvp.md defines the /mvp command workflow
```

### GitHub Copilot

In Copilot Chat, you can:

1. **Copy the command content** directly into chat as context
2. **Reference the file** if working in a repo that includes these commands:
   ```
   Follow the /mvp process from commands/mvp.md for this spec
   ```

### Any AI Assistant

**Universal method — works everywhere:**

1. Open the command file (e.g., `commands/mvp.md`)
2. Copy the entire contents
3. Paste into your AI assistant
4. Follow with your specific file/request

```
[Paste contents of commands/mvp.md]

Now apply this to: product-requirements.md
```

---

## Command Reference: /mvp

### Overview

The `/mvp` command transforms a product specification into a phased implementation plan using **tracer bullet methodology**.

**Usage:**
```
/mvp prd.md
/mvp path/to/spec-file.md
```

### Methodology

The command applies four key principles:

| Principle | Description |
|-----------|-------------|
| **Critical Path Planning** | Identify essential features and dependencies first — what MUST exist before anything else works |
| **TDD Methodology** | Define tests/requirements before implementation — know what "done" looks like |
| **Tracer Bullet Approach** | Build the simplest working version first, then iterate — prove the path works end-to-end |
| **Modular Context Architecture** | Split documentation by concern to optimize AI context windows — load only what's relevant |

### What It Does

1. **Reads** your product specification
2. **Asks** clarifying questions (doesn't assume)
3. **Identifies** core MVP features (absolute minimum to work)
4. **Maps** critical path order (what must happen first)
5. **Defines** test scenarios for each step
6. **Proposes** modular documentation structure
7. **Outputs** a `plan.md` with numbered phases

### Output: plan.md

The command generates a structured plan file:

```markdown
# Implementation Plan

> Note: When loaded in a new conversation, ask which phase to implement.

## Phase 1: Foundation
**Deliverables:** Core data models, basic project structure
**Dependencies:** None
**Tests:** Unit tests for data validation

## Phase 2: Core Backend
**Deliverables:** API endpoints, database integration
**Dependencies:** Phase 1
**Tests:** Integration tests for API responses

## Phase 3: Basic UI
**Deliverables:** Main user interface components
**Dependencies:** Phase 2
**Tests:** Component tests, E2E happy path

...
```

### Technology Selection

Unless specified in your spec file, the command will:
- Research current best practices online
- Prefer AWS free tier / cost-effective solutions
- Favor serverless architecture when appropriate

---

## Examples

### Example Input: Product Spec

```markdown
# Task Manager App

## Overview
A simple task management application for personal use.

## Features
- Users can create tasks with titles and descriptions
- Tasks have due dates and priority levels
- Users can mark tasks as complete
- Tasks can be organized into projects
- Basic search and filtering
```

### Example Output: plan.md (excerpt)

```markdown
# Task Manager - Implementation Plan

> When starting a new conversation, ask which phase to implement.

## Modular Documentation Structure
- `docs/data-models.md` — Task, Project schemas
- `docs/api.md` — REST endpoints
- `docs/components.md` — UI component specs
- Load relevant doc when working on that area

## Phase 1: Data Foundation
**Deliverables:**
- Task entity (id, title, description, dueDate, priority, completed)
- Project entity (id, name, tasks[])
- Database schema (DynamoDB or PostgreSQL)

**Dependencies:** None

**Tests:**
- Create task with all fields
- Validate required fields
- Task-Project relationship

## Phase 2: Core API
**Deliverables:**
- CRUD endpoints for Tasks
- CRUD endpoints for Projects
- Task completion toggle

**Dependencies:** Phase 1

**Tests:**
- Create/read/update/delete task
- List tasks with filters
- Assign task to project
```

---

## Troubleshooting

### "The AI doesn't follow the command structure"

**Solutions:**
- Ensure you're providing the full command file content
- Add explicit instruction: "Follow this EXACTLY as specified"
- Break into smaller requests if the AI seems overwhelmed

### "Output is incomplete or cut off"

**Solutions:**
- Ask the AI to continue: "Please continue from Phase X"
- Request specific sections: "Now detail Phase 3"
- Use a model with larger context window

### "Command not recognized"

**Solutions:**
- The AI doesn't natively know these commands — you must provide the command file
- Copy/paste the command content or reference the file path
- See [Installation & Setup](#installation--setup) for integration options

### "AI makes assumptions instead of asking questions"

**Solutions:**
- Emphasize: "Ask clarifying questions before proceeding"
- The /mvp command includes this instruction, but you can reinforce it

---

## FAQ

### Can I modify commands for my needs?

**Yes!** Fork the repo and customize. Commands are just markdown files — edit the methodology, add sections, remove what you don't need.

### What AI tools are supported?

Any AI that can read text: Claude, ChatGPT, Copilot, Cursor, Gemini, etc. The commands are tool-agnostic prompts.

### What file format should my spec be?

Markdown (`.md`) works best, but any text format works. The AI just needs to read your requirements.

### How do I contribute a new command?

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines. In short:
1. Copy `commands/_template.md`
2. Fill in your command
3. Test with at least one AI tool
4. Submit a PR

### Why "tracer bullet" methodology?

From *The Pragmatic Programmer*: Build a thin slice through all layers first to prove the architecture works, then flesh it out. This reduces risk and provides early feedback.

### Can I use this commercially?

Yes — MIT License. Use it, modify it, sell products built with it. See [LICENSE](LICENSE).

---

## Project Status & Roadmap

**Current Version:** 0.1.0 (Beta)

### Available Now
- ✅ `/mvp` — Tracer bullet MVP planning

### Planned Commands
- 🔜 `/code-review` — Structured code review process
- 🔜 `/generate-tests` — Test case generation
- 🔜 `/api-design` — API design methodology
- 🔜 `/refactor` — Systematic refactoring approach
- 🔜 `/debug` — Structured debugging workflow

### Future Ideas
- `/document` — Documentation generation
- `/security-review` — Security audit checklist
- `/performance` — Performance optimization

**Want to help?** [Contribute a command](CONTRIBUTING.md) or [suggest one](https://github.com/CarlosFelipeF/ai-slash-commands/issues).

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for:

- How to submit new commands
- Command naming conventions
- Template structure requirements
- Testing checklist
- Pull request process

**Quick start:**
```bash
cp commands/_template.md commands/your-command.md
# Edit your command
# Test with an AI assistant
# Submit PR
```

Please review our [Code of Conduct](CODE_OF_CONDUCT.md).

---

## Related Projects

- **[AgenticDevelopment](https://github.com/CarlosFelipeF/AgenticDevelopment)** — Governance framework for AI coding agents

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Acknowledgments

- Inspired by *The Pragmatic Programmer* (tracer bullets concept)
- Built for the AI-assisted development community

---

**Found this useful?** Star the repo and share with your team!
