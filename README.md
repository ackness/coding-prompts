# Prompts

Personal Cursor/Windsurf/Trae coding prompts.

## MCP Tools

### Install 

```cmd
# mcp-package-version
go install github.com/sammcj/mcp-package-version/v2@HEAD
```

### Config json

```json
{
    "mcpServers": {
        "memory": {
          "command": "npx",
          "args": [
            "-y",
            "@modelcontextprotocol/server-memory"
          ],
          "env": {}
        },
        "ddg-search": {
            "command": "uvx",
            "args": [
                "duckduckgo-mcp-server"
            ],
        },
        "context7": {
            "command": "npx",
            "args": [
                "-y",
                "@upstash/context7-mcp"
            ],
        },
        "fetch": {
            "command": "uvx",
            "args": [
                "mcp-server-fetch"
            ],
        },
        "package-version": {
            "command": "mcp-package-version",
        },
        "git": {
            "command": "uvx",
            "args": [
                "mcp-server-git"
            ],
        },
        "mcp-deepwiki": {
            "command": "npx",
            "args": [
                "-y",
                "mcp-deepwiki@latest"
            ]
        }
    }
}
```
