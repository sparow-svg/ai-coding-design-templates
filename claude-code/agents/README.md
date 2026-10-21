# Claude Code agents templates

Claude Code agents, also called subagents, are specialist assistants Claude Code can hand a task to. Each one has its own instructions, its own context window and its own set of tools, so it can review or research without cluttering your main session. They are perfect for reviews: a UI reviewer, an accessibility auditor, a copy editor. Below: how an agent file is built, a short example, and three ready-made review agents.

## Where the file goes

Project agents go in .claude/agents/<agent-name>.md. Personal agents go in ~/.claude/agents/. You can also create and edit them with the /agents command in Claude Code.

## Structure

- **name**: The agent's identifier, lowercase and hyphenated.
- **description**: When Claude Code should use the agent. Specific triggers make it delegate at the right moments.
- **tools**: Optional. Limit a review agent to reading tools so it reports instead of editing.
- **Instructions**: The agent's role, what to check, in what order, and the exact format of its report.

## Example

```
---
name: ui-reviewer
description: Reviews UI changes against design/template.html. Use after building a page, before saying it is done.
tools: Read, Grep, Glob
---

You are a senior product designer. Check spacing, type,
colour tokens, states and mobile layout. Return a fix list
grouped by severity, with file and line for each item.
```

## Best practices

- Give review agents read-only tools. They should report; the main session decides what to change.
- Define the output format precisely, such as a list grouped by severity with file and line.
- Say "use after..." in the description so Claude Code calls the agent at the right time.
- Use agents for work that needs a fresh context: reviews, audits and research across many files.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Claude Code agents templates](https://www.browsermoon.com/claude-code-templates/agents).

## FAQ

**What are Claude Code agents?**
Subagents: specialist assistants with their own instructions, context and tools. Claude Code hands them a task and gets back a result, keeping the main session focused.

**Where do Claude Code agent files go?**
In .claude/agents/ in your project, or ~/.claude/agents/ for personal agents. Each agent is one markdown file.

**How do I create a Claude Code agent?**
Write a markdown file with name, description and optional tools in the frontmatter, and the instructions below. Or run /agents in Claude Code.

**When should I use an agent instead of a skill?**
Use an agent when the task benefits from a separate context, like a review or audit across many files. Use a skill when you want extra instructions in the current session.
