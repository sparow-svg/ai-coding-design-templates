# AGENTS.md template

AGENTS.md is a plain markdown file in your repo that tells AI coding agents how to work on the project: how to set it up, run the checks, where things live and the rules to follow. OpenAI Codex reads it for every task, and a growing list of other agents read it too. Below: the structure, a short example, and two complete templates: a full project file and a design rules section.

## Where the file goes

Put AGENTS.md in the root of your repo. In a monorepo you can add more in sub-folders; the nearest one to the files being changed applies.

## Structure

- **Overview**: What the project is and the stack, in two lines.
- **Setup and checks**: Install, build, lint and test commands. Agents run them to prove their change works.
- **Project map**: Where routes, components and helpers live.
- **Code style and design**: The conventions and design rules every change must follow.
- **Pull requests**: How to scope a change and what to put in the description.

## Example

```
# AGENTS.md

## Setup and checks
- npm install · npm run build · npm test (all must pass)

## Project map
- app/ routes · components/ shared UI · lib/ helpers

## Rules
- Reuse components before creating new ones.
- One task per pull request.
```

## Best practices

- Put the check commands near the top. Codex runs them before it finishes a task.
- Keep it short and specific; it is read on every task.
- Add a definition of done so agents know when to stop.
- If you also use Claude Code, keep CLAUDE.md and AGENTS.md in step, or point one at the other.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [AGENTS.md template](https://www.browsermoon.com/chatgpt-codex-templates/agents-md).

## FAQ

**What is AGENTS.md?**
A markdown file in your repo with instructions for AI coding agents: setup, checks, project map and rules. Codex reads it on every task.

**Which tools read AGENTS.md?**
OpenAI Codex reads it, and many other coding agents support it too. Claude Code reads CLAUDE.md instead, so many teams keep both.

**Where does AGENTS.md go?**
In the repo root, with optional extra files in sub-folders for parts of a monorepo.

**What is the difference between AGENTS.md and README.md?**
README is for people: what the project is and how to start. AGENTS.md is for agents: exact commands, rules and a definition of done.
