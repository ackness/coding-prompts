# Prompts

Personal Cursor/Windsurf/Trae coding prompts.

## MCP Tools

```json
{
    "mcpServers": {
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
        },
        "mas-sequential-thinking": {
            "command": "uvx",
            "args": [
                "mcp-server-mas-sequential-thinking"
            ],
            "env": {
                "LLM_PROVIDER": "deepseek",
                "DEEPSEEK_API_KEY": "your ds api key if needed",
                "DEEPSEEK_BASE_URL": "your ds base url if needed",
                "EXA_API_KEY": ""
            }
        },
    }
}
```
