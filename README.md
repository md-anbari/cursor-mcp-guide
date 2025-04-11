# 🚀 Understanding MCP (Model Context Protocol) in Cursor

## 🤔 What is MCP?

MCP (Model Context Protocol) is a standardized way for AI agents to communicate with various tools, similar to how REST APIs standardize web communication. Just as REST APIs enable consistent communication between web clients and servers, MCP provides a standard protocol for AI agents to interact with different tools and services.

### 💡 Why MCP Matters

Think of it like this: If you had ten experts who all spoke different languages (Portuguese, English, Mandarin, Indonesian, etc.), communication would be challenging. MCP is like establishing English as the common language - it makes communication seamless and standardized.

## 🛠️ MCP Architecture

MCP servers can run in two ways:
1. **Standard Input/Output**: Running locally in your terminal
2. **E Transport**: Communication over the network (similar to REST APIs)

## 📦 Installation Guide for macOS

### Prerequisites
1. Install Node.js:
   ```bash
   # Using Homebrew
   brew install cursor
   ```
   
2. Visit [Node.js website](https://nodejs.org):
   - Select macOS ARM64 (for M1/M2 Macs)
   - Download and run the installer

### Setting Up MCP in Cursor

1. **Open Cursor Settings**:
   - Option 1: File → Preferences → Cursor Settings
   - Option 2: `⌘ + Shift + P` → Type "cursor" → Select "Cursor Settings"

2. **Configure MCP**:
   - Navigate to MCP section
   - Click "Add new global MCP server"
   - This creates/opens `~/.cursor/mcp.json`

3. **Basic MCP Configuration Structure**:
   ```json
   {
     "mcp_servers": {
       "server_name": {
         "command": "your_mcp_command_here"
       }
     }
   }
   ```

## 🔧 Installing MCP Servers

### Method 1: Using Smithery CLI
```bash
# Install GitHub MCP integration
npx -y @smithery/cli@latest install @smithery-ai/github \
  --client cursor \
  --config '{"githubPersonalAccessToken":"your_token_here"}'
```

### Method 2: Manual Configuration
1. Open `~/.cursor/mcp.json`
2. Add server configuration:
   ```json
   {
     "mcp_servers": {
       "github": {
         "command": "npx @smithery/github-mcp --token your_token_here"
       }
     }
   }
   ```

## 🔍 Using MCP Tools

### Example: GitHub Integration
```json
{
  "mcp_servers": {
    "github": {
      "command": "npx @smithery/github-mcp --token your_github_token"
    }
  }
}
```

### Auto-Run Mode (YOLO Mode)
Enable automatic tool execution:
1. Go to Cursor Settings → Features
2. Enable "Auto Run Mode"
3. Configure safety settings:
   ```json
   {
     "autoRun": {
       "denyList": ["rm", "delete"],
       "allowList": ["git", "npm"],
       "prompt": "Only perform safe operations"
     }
   }
   ```

## 🚨 Troubleshooting

1. **Client Not Connected**:
   - Close and reopen Cursor
   - Check terminal for MCP server process

2. **Windows-Specific Issues**:
   - Add `cmd /C` before commands:
   ```json
   {
     "command": "cmd /C your_command_here"
   }
   ```

3. **Terminal Process Issues**:
   - Keep MCP terminal running
   - Check for error messages
   - Verify API keys and tokens

## 🔐 Security Best Practices

1. **API Keys**:
   - Store securely
   - Never share or commit tokens
   - Regularly rotate keys

2. **Auto-Run Mode**:
   - Use with caution
   - Configure deny lists
   - Set appropriate permissions

## 📚 Finding MCP Servers

1. **Official Sources**:
   - [Smithery Directory](https://smithery.dev)
   - [Awesome MCP Servers](https://github.com/awesome-mcp/servers)

2. **Popular Servers**:
   - GitHub Integration
   - Web Crawling
   - Database Access
   - File Operations

## 🤝 Contributing

Feel free to:
1. Report issues
2. Share configurations
3. Suggest improvements
4. Add new MCP server examples

## 📄 License

This guide is licensed under the MIT License.