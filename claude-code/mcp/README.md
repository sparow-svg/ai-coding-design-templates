# Claude Code MCP templates

MCP servers give Claude Code new tools: a real browser, your design files, your database, your issue tracker. You add them with a command or a .mcp.json file in your project, and Claude Code can use their tools from then on. For design work the most useful one is a browser, so Claude Code can open the page it built, take screenshots at phone and desktop width and compare them with your template. Below: how MCP setup works, a short example, and a ready-made design setup.

## Where the file goes

Project servers go in .mcp.json in the root of your repo and are shared with the team; each person approves them the first time. Servers just for you are added with claude mcp add, which stores them in your own Claude Code settings.

## Structure

- **mcpServers**: The list of servers, each under a short name you choose.
- **command and args**: How to start a local server, for example npx with the package name.
- **url**: For remote servers, the address to connect to instead of a command.
- **env**: Optional environment variables, such as API keys. Keep real keys out of the repo.
- **Scope**: Project (.mcp.json, shared), local or user (just you). Choose with the --scope flag on claude mcp add.

## Example

```
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

## Best practices

- Start with one or two servers. Every server adds tools Claude Code has to choose between.
- Use a browser server for UI work so Claude Code can see what it built.
- Keep secrets in environment variables, not in .mcp.json.
- Run /mcp in Claude Code to see which servers are connected and their status.

## Ready-made files

Complete, design-focused versions of these files are on BrowserMoon: [Claude Code MCP templates](https://www.browsermoon.com/claude-code-templates/mcp).

## FAQ

**What is MCP in Claude Code?**
The Model Context Protocol, a standard way to give Claude Code extra tools through servers, such as a browser, a database or your design files.

**How do I add an MCP server to Claude Code?**
Run claude mcp add with the server's name and command, or add it to .mcp.json in your project so the whole team gets it.

**Where is .mcp.json?**
In the root of your project. It holds project-scoped servers that are shared through the repo.

**Which MCP server helps with design?**
A browser server such as Playwright MCP. It lets Claude Code open pages, resize them and take screenshots to check its work against your template.
