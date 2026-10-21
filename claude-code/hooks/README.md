# Claude Code hooks templates

Claude Code hooks are commands that run automatically at set moments, like after Claude Code edits a file or before it runs a tool. Unlike instructions, hooks always run, so they are the way to enforce rules: format every file, lint every change, block off-brand colours. Below: how hooks are set up, a short example, and two ready-made hooks with their scripts.

## Where the file goes

Hooks are set in .claude/settings.json in your project (shared with the team), .claude/settings.local.json (just you) or ~/.claude/settings.json (all projects). The scripts they run usually live in .claude/hooks/.

## Structure

- **Event**: When the hook runs. PostToolUse runs after a tool, such as after an edit; PreToolUse runs before one and can block it. There are also events for prompts, session start and stop.
- **Matcher**: Which tools trigger it, for example Edit|Write for file changes.
- **Command**: The shell command to run. It receives details of the tool call as JSON on standard input.
- **Exit code**: Exit 0 to continue. Exit 2 to send your message back to Claude Code so it fixes the problem.

## Example

```
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          { "type": "command", "command": "npx prettier --write ." }
        ]
      }
    ]
  }
}
```

## Best practices

- Use hooks for rules that must always hold. Use CLAUDE.md for rules that need judgement.
- Read the file path from the JSON input and check only the changed file, so hooks stay fast.
- Exit with code 2 and a clear message to make Claude Code fix the problem itself.
- Keep hook scripts in .claude/hooks/ and commit them, so the whole team gets them.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Claude Code hooks templates](https://www.browsermoon.com/claude-code-templates/hooks).

## FAQ

**What are Claude Code hooks?**
Shell commands that run automatically at set points, like after a file edit. They enforce rules every time, which instructions cannot guarantee.

**Where are Claude Code hooks configured?**
In the hooks section of .claude/settings.json, .claude/settings.local.json or ~/.claude/settings.json.

**How does a hook send feedback to Claude Code?**
Exit with code 2 and write the message to standard error. Claude Code reads it and acts on it.

**Can hooks block an action?**
Yes. A PreToolUse hook that exits with code 2 blocks the tool call and tells Claude Code why.
