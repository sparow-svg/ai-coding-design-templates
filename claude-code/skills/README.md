# Claude Code skills templates

A Claude Code skill is a folder with a SKILL.md file that teaches Claude Code how to do one kind of task. Claude Code reads each skill's name and description, and loads the full instructions only when a task matches. That makes skills the right place for detailed, repeatable workflows, like building a landing page or checking a page on mobile. Below: how a skill is built, a short example, and three ready-made design skills.

## Where the file goes

Project skills go in .claude/skills/<skill-name>/SKILL.md in your repo, so everyone on the project gets them. Personal skills go in ~/.claude/skills/<skill-name>/SKILL.md. A skill folder can also hold scripts and reference files the skill points to.

## Structure

- **name**: Short, lowercase, hyphenated. It becomes the skill's identifier.
- **description**: The most important line. Say what the skill does and exactly when to use it; Claude Code decides whether to load the skill from this.
- **Instructions**: The steps, rules and checks, written as instructions. Loaded only when the skill is used, so they can be detailed.
- **Extra files**: Optional scripts, templates or reference docs in the same folder, linked from SKILL.md.

## Example

```
---
name: responsive-check
description: Use after changing a page, or when the user mentions mobile or layout bugs. Checks 375, 768 and 1440 px and fixes what breaks.
---

# Responsive check
1. Open the page at each width.
2. Fix horizontal scroll, tiny tap targets and broken stacks.
3. Report what you fixed.
```

## Best practices

- Write the description as a trigger: "Use when...". Vague descriptions mean the skill never loads.
- One skill, one job. Split big workflows into several skills.
- End every skill with a check step, so Claude Code verifies its own work.
- Keep reference material in separate files in the skill folder and link to it, so it loads only when needed.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Claude Code skills templates](https://www.browsermoon.com/claude-code-templates/skills).

## FAQ

**What are Claude Code skills?**
Folders with a SKILL.md file that give Claude Code instructions for a specific kind of task. Claude Code loads a skill when your request matches its description.

**Where do Claude Code skills go?**
In .claude/skills/<name>/SKILL.md in your project, or in ~/.claude/skills for personal skills that work in every project.

**What is the difference between a skill and CLAUDE.md?**
CLAUDE.md is always loaded and holds short, project-wide rules. A skill loads only when needed, so it can hold long, detailed instructions for one task.

**What is the difference between a skill and an agent?**
A skill adds instructions to the current conversation. An agent (subagent) is a separate assistant with its own context and tools that Claude Code hands a task to.

**How do I make Claude Code use my skill?**
Write a clear description that says when to use it. You can also ask for it by name.
