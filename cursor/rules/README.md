# Cursor rules template

Cursor rules are instructions saved in your project that Cursor adds to its requests, so Agent and chat follow your conventions without being told. Modern Cursor rules are .mdc files in .cursor/rules, each with a description, the files it applies to and the rules themselves. Below: the format, a short example, and three ready-made rules: design, Next.js with Tailwind, and component reuse.

## Where the file goes

Put rule files in .cursor/rules/ in your project, one topic per file, with the .mdc extension. The older single .cursorrules file in the project root still works, but split rules are easier to manage.

## Structure

- **description**: What the rule is for. Cursor uses it to decide when a rule is relevant.
- **globs**: File patterns the rule applies to, such as all .tsx files. The rule is attached when those files are involved.
- **alwaysApply**: Set to true for rules that apply to every request; keep most rules false and scoped with globs.
- **Rules**: Short, specific instructions. You can reference files with @ inside a rule.

## Example

```
---
description: Design rules for all UI work.
globs: ["**/*.tsx", "**/*.css"]
alwaysApply: false
---

- Follow @design/template.html for every component.
- Use only the colour tokens in tailwind.config.
- Reuse components in components/ before creating new ones.
```

## Best practices

- One topic per rule file: design, framework, testing. Small rules are applied more reliably.
- Scope rules with globs so they only load for the files they are about.
- Write rules as commands and keep them short.
- Reference your design template with @ inside the design rule, so Cursor reads the real file.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Cursor rules template](https://www.browsermoon.com/cursor-templates/cursor-rules).

## FAQ

**What are Cursor rules?**
Saved instructions in your project that Cursor includes with relevant requests, so it follows your conventions automatically.

**Where do Cursor rules go?**
In .cursor/rules/ as .mdc files. The older .cursorrules file in the project root is still read for compatibility.

**What is the .mdc format?**
Markdown with a small header that sets the description, the file globs and whether the rule always applies.

**How many Cursor rules should I have?**
A few small, focused files, such as design, framework and testing, work better than one long file.
