# 🚀 Cursor GitHub MCP Setup Guide for macOS

A focused guide on setting up GitHub MCP integration with Cursor IDE on macOS, including step-by-step installation and configuration instructions.

## 📋 Prerequisites

- macOS operating system
- Node.js and npm installed
- GitHub account with personal access token
- Cursor IDE installed

## 🛠️ Installation Steps

### 1. Install Cursor on macOS

```bash
# Using Homebrew
brew install cursor
```

### 2. Install GitHub MCP Integration

```bash
# Install Smithery CLI with GitHub integration
npx -y @smithery/cli@latest install @smithery-ai/github \
  --client cursor \
  --config '{"githubPersonalAccessToken":"your_token_here"}'
```

### 3. Configure MCP in Cursor

The MCP configuration file is located at:
```
~/.cursor/mcp.json
```

Example configuration:
```json
{
  "github": {
    "personalAccessToken": "your_token_here"
  }
}
```

## 🖥️ Cursor Interface Layout

After installation, you'll see the following changes in your Cursor IDE:

1. **Command Palette** (⌘ + Shift + P)
   - New GitHub commands available
   - MCP-related commands listed

2. **Sidebar**
   - GitHub icon in the activity bar
   - Repository explorer
   - Pull request viewer

3. **Status Bar**
   - MCP connection status
   - Current GitHub context

## 🔑 GitHub Personal Access Token Setup

1. Go to GitHub Settings:
   - Profile picture → Settings → Developer settings → Personal access tokens → Tokens (classic)

2. Required token permissions:
   ```
   repo            ✓ Full control of private repositories
   read:org        ✓ Read org and team information
   read:user       ✓ Read user information
   user:email      ✓ Access user email addresses
   ```

## 🛠️ Available GitHub MCP Features

### 1. Repository Management
```javascript
// Create a new repository
mcp.github.createRepository({
  name: "my-new-repo",
  description: "Repository created via MCP",
  private: false
});

// Delete a repository
mcp.github.deleteRepository({
  owner: "username",
  repo: "repo-name"
});
```

### 2. File Operations
```javascript
// Create or update file
mcp.github.createOrUpdateFile({
  owner: "username",
  repo: "repo-name",
  path: "path/to/file",
  content: "file content",
  message: "commit message"
});

// Get file contents
mcp.github.getFileContents({
  owner: "username",
  repo: "repo-name",
  path: "path/to/file"
});
```

### 3. Repository Search
```javascript
// Search repositories
mcp.github.searchRepositories({
  query: "language:javascript stars:>1000"
});

// Search code
mcp.github.searchCode({
  query: "filename:README.md"
});
```

### 4. Issue and PR Management
```javascript
// Create an issue
mcp.github.createIssue({
  owner: "username",
  repo: "repo-name",
  title: "Issue title",
  body: "Issue description"
});

// Create a pull request
mcp.github.createPullRequest({
  owner: "username",
  repo: "repo-name",
  title: "PR title",
  head: "feature-branch",
  base: "main"
});
```

## 🔍 Verifying Installation

1. Check MCP Status:
```bash
# View MCP configuration
cat ~/.cursor/mcp.json

# Check Smithery installation
npx @smithery/cli@latest list
```

2. Test GitHub Integration:
```bash
# In Cursor's command palette (⌘ + Shift + P):
> GitHub: View Repository
```

## 🚨 Troubleshooting

1. **Token Issues**
```bash
# Regenerate token and update configuration
npx -y @smithery/cli@latest install @smithery-ai/github \
  --client cursor \
  --config '{"githubPersonalAccessToken":"new_token_here"}'
```

2. **Connection Issues**
```bash
# Reset MCP configuration
rm ~/.cursor/mcp.json
# Then reinstall GitHub integration
```

3. **Common Error Messages**:
   - `Authentication failed`: Check your token
   - `Connection refused`: Restart Cursor
   - `Resource not found`: Verify repository access

## 📝 Tips for Daily Use

1. **Quick Commands**:
   - ⌘ + Shift + P: Open command palette
   - Type 'GitHub' to see all available commands

2. **Keyboard Shortcuts**:
   - ⌘ + K G: Open GitHub view
   - ⌘ + K P: Open pull requests
   - ⌘ + K I: Open issues

3. **Best Practices**:
   - Keep your token secure
   - Use environment variables when possible
   - Regularly update Cursor and MCP

## 🔄 Updating

To update the GitHub MCP integration:
```bash
npx -y @smithery/cli@latest update @smithery-ai/github
```

## 🆘 Getting Help

- Visit [Cursor Documentation](https://cursor.sh/docs)
- Join [Cursor Discord](https://discord.gg/cursor)
- Check [GitHub Status](https://www.githubstatus.com/)

## 📄 License

This guide is licensed under the MIT License.