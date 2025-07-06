# AI Configuration for Playwright Testing

This directory contains **environment-agnostic AI configuration** that ensures consistent behavior across all developers and AI assistants working on this project.

## 📁 Configuration Files

### `.cursor/instructions.md`
- **Purpose**: Automatically enforces UI test creation pipeline
- **Scope**: Applies to ALL AI assistants (Claude, GPT, etc.)
- **Triggers**: Activates when user requests test creation

### `.cursor/rules/playwright-test-pipeline.md`
- **Purpose**: Detailed 4-phase pipeline documentation
- **Content**: Step-by-step workflow with MCP browser tools
- **Requirements**: Mandatory hover-based locator discovery

## 🚀 How It Works

When ANY developer says **"create a test"**, the AI will automatically:

1. 📋 Create a 4-phase todo list
2. 🌐 Use MCP browser tools for exploration
3. 🎯 Hover on elements to get recommended locators
4. 🧪 Generate tests with proper Playwright practices
5. ✅ Validate with 90%+ success rate

## 🔧 Setup Requirements

### For AI Assistants (Cursor, Continue, etc.)
- Ensure MCP Playwright tools are available
- Load project context from `.cursor/` directory
- Follow instructions.md automatically

### For Developers
- No setup required!
- Configuration travels with the codebase
- Just clone and start creating tests

## 📊 Expected Behavior

```bash
Developer: "create a test for login flow"

AI Response:
✅ Creating todo list with 4-phase pipeline...
✅ Phase 1: Opening browser for manual exploration...
✅ Phase 2: Hovering on elements for locator discovery...
✅ Phase 3: Generating test with discovered locators...
✅ Phase 4: Running validation tests...
```

## 🛠️ Customization

To modify the pipeline:
1. Edit `.cursor/instructions.md` for automation rules
2. Edit `.cursor/rules/playwright-test-pipeline.md` for detailed steps
3. Changes apply project-wide immediately

## ✅ Benefits

- **Consistent**: Same AI behavior for all developers
- **Portable**: Configuration travels with repository
- **Quality**: Enforces best practices automatically
- **Efficient**: No need to remember/explain pipeline each time

**This setup ensures high-quality, consistent UI test creation regardless of who's working on the project.**