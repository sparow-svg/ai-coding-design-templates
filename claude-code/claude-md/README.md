# CLAUDE.md template

CLAUDE.md is a file Claude Code reads at the start of every session. It tells Claude Code what the project is, how to run it, how the code is organised and the rules to follow, so you stop repeating yourself. A good CLAUDE.md is short, specific and written as instructions. Below is the structure that works, a short example, and two complete templates: a full project file and a design rules section.

## Where the file goes

Put CLAUDE.md in the root of your repo. Claude Code also reads CLAUDE.md files in parent folders and in sub-folders when it works there, and a personal one in ~/.claude/CLAUDE.md that applies to all your projects.

## Structure

- **Project**: One or two lines: what the product is, who it is for, and the main stack.
- **Commands**: The exact commands to run, build, lint and test. Claude Code runs them to check its work.
- **Folders**: A short map of where things live, so Claude Code edits the right files.
- **Code style**: The conventions that are not obvious from the code: server or client components, where data fetching goes, naming.
- **Design rules**: Which template to follow, colour tokens, type scale and spacing. This is what keeps the UI consistent.
- **Never**: A short list of hard rules: secrets, migrations, generated files.

## Example

```
# Project
[Product] is a [type of app] for [audience]. Next.js, TypeScript, Tailwind.

## Commands
- npm run dev / npm run build / npm test

## Folders
- app/ routes · components/ shared UI · lib/ data and helpers

## Rules
- Reuse components in components/ before creating new ones.
- Follow design/template.html for all UI.

## Never
- Never commit .env files.
```

## Best practices

- Keep it under about 150 lines. Claude Code reads all of it every session, so every line should earn its place.
- Write instructions, not documentation: "Use server components by default", not a paragraph about React.
- Put the commands first. Claude Code uses them to check its own work.
- Add rules when you correct Claude Code twice for the same thing.
- Use # in Claude Code to add a line to CLAUDE.md as you work.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [CLAUDE.md template](https://www.browsermoon.com/claude-code-templates/claude-md).

## FAQ

**What is CLAUDE.md?**
A markdown file Claude Code reads at the start of every session. It holds project context and rules, so Claude Code knows how your project works without being told each time.

**Where does CLAUDE.md go?**
In the root of your repo. You can add more in sub-folders for rules that only apply there, and a personal one in ~/.claude/CLAUDE.md for all projects.

**What should I put in CLAUDE.md?**
What the project is, the commands to run and test it, a folder map, code style rules, design rules and a short list of things to never do.

**How long should CLAUDE.md be?**
Short. Under about 150 lines works well. Long files cost context every session and bury the rules that matter.

**Can I generate a CLAUDE.md automatically?**
Yes. Run /init in Claude Code to create a first version from your codebase, then edit it with the structure on this page.
