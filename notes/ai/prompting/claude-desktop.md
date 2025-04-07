# Claude Desktop MCP Coding Cheatsheet

## Core MCP Servers for Development

### Essential MCP Servers

```bash
# Sequential Thinking - For better reasoning in complex tasks
npx -y @smithery/cli@latest install @smithery-ai/server-sequential-thinking --client claude

# ClaudeComputerCommander - File/system access and long-running processes
npx -y @smithery/cli install @wonderwhy-er/desktop-commander --client claude

# File System - Direct filesystem access
npx -y @modelcontextprotocol/server-filesystem /path/to/directory

# Git MCP - Repository operations
npx -y @modelcontextprotocol/server-git --repository /path/to/repo

# GitHub - API integration
npx -y @modelcontextprotocol/server-github
# (requires GITHUB_PERSONAL_ACCESS_TOKEN in env)

```

## Configuration Setup

### Claude Desktop Config

Location:

-   macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
-   Windows: `%APPDATA%\Claude\claude_desktop_config.json`

Example configuration:

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@smithery-ai/server-sequential-thinking"]
    },
    "commander": {
      "command": "npx",
      "args": ["-y", "@wonderwhy-er/desktop-commander"]
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/absolute/path/to/code"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token_here"
      }
    }
  }
}

```

## Common Workflow Prompts

### Codebase Exploration

```
Explore the codebase at /path/to/project and help me understand it:
1. Navigate through directories and examine key files
2. Create a diagram showing the architecture and component relationships
3. Summarize the main modules and their responsibilities
4. Identify any potential areas for improvement

```

### Code Migration/Refactoring

```
I need to migrate/refactor the project at /path/to/old_project to use newer technologies:
1. Analyze the current codebase structure and dependencies
2. Create a plan for updating [specific components/dependencies]
3. Implement the migration while preserving core functionality
4. Test the new implementation to ensure it works correctly

```

### Long-Running Process Management

```
Execute this long-running task for me:
1. [Describe task - e.g., video encoding, data processing]
2. Start the process and monitor its progress
3. Notify me when it's completed
4. Provide a summary of the results

```

## Tool Usage Patterns

### Sequential Thinking Pattern

Always allow Claude to use Sequential Thinking for complex tasks:

```
Use sequential thinking to solve this problem:
1. First, understand the requirements fully
2. Break down the problem into smaller, manageable steps
3. Solve each step methodically
4. Integrate the solutions of each step
5. Verify the overall solution

```

### ClaudeComputerCommander Permissions

For security, grant permissions thoughtfully:

-   Allow "for this message" - One-time permission
-   Allow "for this chat" - Session-based permission
-   Regularly review logs in `~/Library/Logs/Claude/mcp*.log`

## Debugging MCP Integrations

### Log Locations

-   macOS: `~/Library/Logs/Claude/mcp*.log`
-   Windows: `%APPDATA%\Claude\logs\mcp*.log`

### Common Troubleshooting

```bash
# Verify server is installed correctly
npx -y @smithery/cli list

# Check MCP server logs
tail -n 20 -F ~/Library/Logs/Claude/mcp*.log

# Restart Claude Desktop after config changes

```

## Advanced MCP Server Integration

### Database Connectivity

```bash
# PostgreSQL integration
npx -y @modelcontextprotocol/server-postgres "postgresql://user:pass@localhost/db"

# SQLite integration
npx -y @modelcontextprotocol/server-sqlite /path/to/database.sqlite

```

### Development Tools

```bash
# Puppeteer for web automation
npx -y @modelcontextprotocol/server-puppeteer

# API integrations (requires authentication setup)
npx -y @modelcontextprotocol/server-github
npx -y @modelcontextprotocol/server-slack

```

## Best Practices

1.  **Permission Management**: Grant minimum necessary permissions
2.  **Path Specification**: Always use absolute paths
3.  **Process Handling**: Let Claude manage long-running tasks and check status
4.  **Review Workflow**: Let Claude run the entire process, then review the working solution
5.  **Error Recovery**: If Claude gets stuck, provide clear guidance rather than taking over completely

## Sample Projects

1.  **Code Analysis**: Explore a repository, generate architecture diagrams
2.  **Codebase Migration**: Move from older frameworks to newer ones
3.  **Automation Tasks**: File processing, media conversion, data extraction
4.  **Multi-Repository Work**: Work across multiple codebases simultaneously

## Security Considerations

1.  Be cautious with personal/sensitive data directories
2.  Review code executed by tools before running in production
3.  Use environment variables for sensitive credentials
4.  Regularly update MCPs for security patches
5.  Check logs for unexpected behavior

----------
