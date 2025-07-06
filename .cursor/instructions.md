# Project AI Instructions

## UI Test Creation Protocol

**MANDATORY**: When creating any UI test, the AI assistant MUST automatically follow this workflow:

### 1. Auto-Reference Pipeline
- Always reference `.cursor/rules/playwright-test-pipeline-v2.md`
- Create initial simple todo list before starting any UI test work

### 2. Required Initial Todo Structure
```
- Do manual testing
- Create test steps to automate
- **temp** implement test steps
- Run test and verify all done
```

**Note:** The actual test case steps (Step 1: login, Step 2: verify inventory, etc.) will be merged as todo steps ONLY AFTER manual testing when you define the specific test steps to automate.

**Implementation Flow:** For each test step, follow the rigorous **Define → Check → Gap → Implement → Validate → Next** flow from the pipeline.

**Test Step Guidelines:** Focus on user flow and automation actions, not technical details.
- ✅ **Good steps:** "login with standard user", "add item to cart", "verify item was added"
- ❌ **Avoid:** "GIVEN: I am on the inventory page with products displayed" (too detailed/technical)

### 3. Trigger Conditions
Execute this pipeline when user requests:
- "create a test"
- "create UI test"
- "test this scenario"
- "automate this flow"
- Any test creation request

### 4. Non-Negotiable Requirements
- ✅ Use `todo_write` tool to create initial simple checklist
- ✅ Use MCP browser tools for manual exploration
- ✅ Use `mcp_playwright_browser_hover` on ALL interactive elements
- ✅ Document recommended locators before writing code
- ✅ Follow locator hierarchy: getByRole > getByTestId > getByText > CSS
- ✅ **STEP-BY-STEP IMPLEMENTATION**: After manual testing, merge specific test steps as todos and implement each individually
- ✅ Run tests multiple times for validation

### 5. Quality Gates
- Test must pass 90%+ success rate
- Must use proper Playwright locator hierarchy
- Must complete manual testing → test steps → implementation → validation flow
- **Each individual test step validated** before moving to next step
- Maximum reuse discovery through incremental step-by-step approach

**This configuration travels with the project and applies to all AI assistants working on this codebase.**