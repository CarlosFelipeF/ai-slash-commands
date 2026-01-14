# AI Slash Commands

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A library of reusable slash commands for AI coding assistants (Claude, Cursor, GitHub Copilot, etc.).

## What are Slash Commands?

Slash commands are predefined prompts that standardize common development workflows. Instead of writing detailed instructions each time, you invoke a command like `/mvp prd.md` and the AI follows a structured process.

## Available Commands

| Command | Description | File |
|---------|-------------|------|
| `/mvp <spec-file>` | Tracer bullet MVP planning from a product spec | [commands/mvp.md](commands/mvp.md) |

## How to Use

### Option 1: Copy and Paste

1. Open the command file (e.g., `commands/mvp.md`)
2. Copy the contents
3. Paste into your AI assistant as a prompt prefix
4. Follow with your specific request

### Option 2: Reference in Custom Instructions

**Claude Code:** Add to project instructions:
```
When I use /mvp, follow the instructions in commands/mvp.md
```

**Cursor:** Add to `.cursorrules`:
```
@commands/mvp.md defines the /mvp command workflow
```

### Option 3: Direct File Reference

If your AI assistant can read files, simply say:
```
/mvp prd.md
```
And reference the command file when the assistant asks for clarification.

## Command: /mvp

**Purpose:** Transform a product specification into a phased implementation plan using tracer bullet methodology.

**Usage:**
```
/mvp prd.md
/mvp path/to/spec-file.md
```

**What it does:**
- Identifies critical path features
- Applies TDD methodology
- Creates modular documentation structure
- Outputs phased plan with dependencies

**Output:** A `plan.md` file with numbered phases, deliverables, and test scenarios.

[Full command details](commands/mvp.md)

---

## Contributing

Have a useful slash command? Contributions welcome!

1. Create a new file in `commands/` (e.g., `commands/your-command.md`)
2. Follow the existing format
3. Update this README with the new command
4. Submit a pull request

## Related Projects

- [AgenticDevelopment](https://github.com/CarlosFelipeF/AgenticDevelopment) — Governance framework for AI coding agents

## License

MIT License — see [LICENSE](LICENSE) for details.
