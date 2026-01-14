# Contributing to AI Slash Commands

Thank you for your interest in contributing! This guide will help you add new commands or improve existing ones.

## Table of Contents

- [How to Report Issues](#how-to-report-issues)
- [How to Submit New Commands](#how-to-submit-new-commands)
- [Command Naming Conventions](#command-naming-conventions)
- [Command Structure Requirements](#command-structure-requirements)
- [Testing Checklist](#testing-checklist)
- [Pull Request Process](#pull-request-process)

## How to Report Issues

1. **Check existing issues** to avoid duplicates
2. **Use a clear title** describing the problem
3. **Include details:**
   - Which command is affected?
   - Which AI tool are you using? (Claude Code, Cursor, etc.)
   - What did you expect to happen?
   - What actually happened?
   - Steps to reproduce

## How to Submit New Commands

1. **Fork the repository**
2. **Create a new branch:** `git checkout -b add-command-name`
3. **Copy the template:** `cp commands/_template.md commands/your-command.md`
4. **Fill in all sections** of the template
5. **Test your command** with at least one AI tool
6. **Submit a pull request**

## Command Naming Conventions

- **Use kebab-case:** `code-review`, `test-plan`, `api-design`
- **Start with action verbs:** `generate-`, `review-`, `plan-`, `analyze-`
- **Be descriptive but concise:** 2-3 words maximum
- **Avoid generic names:** `helper`, `util`, `misc`

### Good Examples
- `/mvp` - Plans minimum viable product
- `/code-review` - Reviews code for issues
- `/test-plan` - Creates testing strategy

### Bad Examples
- `/do-stuff` - Too vague
- `/comprehensive-detailed-code-analysis-tool` - Too long
- `/cr` - Too abbreviated (unless widely known)

## Command Structure Requirements

Every command file must include:

### 1. Header Section
```markdown
# /command-name

> One-line description of what this command does

**Usage:** `/command-name <input-file>`
```

### 2. Methodology Section
Explain the approach/framework used:
- What principles guide this command?
- Why is this methodology effective?
- What are the key steps?

### 3. Instructions Section
Clear, actionable instructions for the AI:
- What should the AI do first?
- What questions should it ask?
- What format should the output be?

### 4. Output Section
Define the expected output:
- File name (if applicable)
- Structure/format
- Required sections

## Testing Checklist

Before submitting, verify your command works with:

- [ ] **Claude Code** - Test in Claude Code IDE
- [ ] **Cursor** - Test via .cursorrules or direct paste
- [ ] **Other AI tools** - Test with at least one other tool if possible

For each test, verify:
- [ ] AI understands the command purpose
- [ ] AI asks appropriate clarifying questions
- [ ] Output matches expected format
- [ ] Output is useful and actionable

## Pull Request Process

1. **Title format:** `Add /command-name command`
2. **Description must include:**
   - What does this command do?
   - Why is it useful?
   - Which AI tools did you test with?
   - Example input and output (brief)

3. **Review process:**
   - Maintainers will review within 1 week
   - Address any feedback
   - Once approved, your command will be merged

## Style Guidelines

### Writing Style
- Use clear, imperative language
- Be specific, not vague
- Include examples where helpful
- Keep instructions concise but complete

### Formatting
- Use proper Markdown formatting
- Include code blocks for examples
- Use tables for structured data
- Add horizontal rules to separate sections

## Questions?

- Open an issue for questions about contributing
- Check existing commands for examples
- Review the [README](README.md) for project context

---

Thank you for helping make AI Slash Commands better!
