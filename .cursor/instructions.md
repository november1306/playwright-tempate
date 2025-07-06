# Project AI Instructions

## UI Test Creation Protocol

**MANDATORY**: When creating any UI test, the AI assistant MUST automatically follow this workflow:

### 1. Auto-Reference Pipeline
- Always reference `.cursor/rules/playwright-test-pipeline.md`
- Create todo list with the 4-phase pipeline before starting any UI test work

### 2. Required 4-Phase Process
```
Phase 1: Manual Exploration → Phase 2: Locator Discovery → Phase 3: Test Generation → Phase 4: Validation
```

### 3. Trigger Conditions
Execute this pipeline when user requests:
- "create a test"
- "create UI test"
- "test this scenario"
- "automate this flow"
- Any test creation request

### 4. Non-Negotiable Requirements
- ✅ Use `todo_write` tool to create 4-phase checklist
- ✅ Use MCP browser tools for manual exploration
- ✅ Use `mcp_playwright_browser_hover` on ALL interactive elements
- ✅ Document recommended locators before writing code
- ✅ Follow locator hierarchy: getByRole > getByTestId > getByText > CSS
- ✅ Run tests multiple times for validation

### 5. Quality Gates
- Test must pass 90%+ success rate
- Must use proper Playwright locator hierarchy
- Must complete full 4-phase pipeline
- No skipping of locator discovery phase

**This configuration travels with the project and applies to all AI assistants working on this codebase.**