# Claude Code commands templates

Claude Code custom slash commands are saved prompts you run by typing / and a name, like /build-page. Each one is a markdown file in your project, so the whole team gets the same commands. They are the fastest way to turn a workflow you repeat, like building a page from your template or reviewing a change, into one short command. Below: how a command file works, a short example, and three ready-made design commands.

## Where the file goes

Project commands go in .claude/commands/<name>.md, and the file name becomes the command: build-page.md runs as /build-page. Personal commands go in ~/.claude/commands/ and work in every project. Sub-folders group related commands.

## Structure

- **File name**: Becomes the command name. build-page.md runs as /build-page.
- **description**: Optional frontmatter shown in the command menu, so people know what it does.
- **argument-hint**: Optional hint for what to type after the command.
- **$ARGUMENTS**: Replaced with whatever you type after the command, so one command works for many pages.
- **Prompt**: The instructions themselves, written like a message to Claude Code.

## Example

```
---
description: Build a new page from design/template.html
argument-hint: [page name]
---

Build this page: $ARGUMENTS
1. Read design/template.html.
2. Plan the sections, then build with existing components.
3. Check the page at 375px and 1440px.
```

## Best practices

- Turn any prompt you have typed three times into a command.
- Use $ARGUMENTS so one command covers many cases, like /build-page pricing.
- End every command with a check step and a short report.
- Commit .claude/commands so the whole team uses the same workflows.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Claude Code commands templates](https://www.browsermoon.com/claude-code-templates/commands).

## FAQ

**What are Claude Code slash commands?**
Saved prompts you run with / and a name. Custom ones are markdown files in .claude/commands, so you can share them with your team.

**Where do custom commands go?**
In .claude/commands/ in your project, or ~/.claude/commands/ for personal commands that work everywhere.

**How do I pass arguments to a command?**
Put $ARGUMENTS in the command file. Whatever you type after the command name replaces it.

**What is the difference between a command and a skill?**
You run a command yourself by typing it. A skill loads automatically when Claude Code decides a task matches its description.
