# UI Test Creation Pipeline

## ⚠️ MANDATORY WORKFLOW - NO EXCEPTIONS

**This pipeline is REQUIRED for ALL UI test creation in this project.**

## Core Rules
1. **Always use todo lists** to track the 4-phase pipeline
2. **Use MCP browser tools** for manual exploration and locator discovery
3. **Hover to get locators** - use `mcp_playwright_browser_hover` on elements to get recommended Playwright locators
4. **Follow locator hierarchy**: getByRole > getByTestId > getByText > CSS selectors
5. **GWT Scenarios**: Always populate scenarios with Given-When-Then steps for manual reproduction
6. **Test.Step Matching**: Use `test.step()` calls that match scenario GWT structure

## 🔄 AUTOMATED 4-Phase Test Creation Pipeline

### Phase 1: Manual Exploration
- [ ] Open browser with MCP: `mcp_playwright_browser_navigate`
- [ ] Take snapshot to understand page structure
- [ ] Manually execute the scenario steps
- [ ] Identify all interactive elements needed
- [ ] Document GWT steps in scenarios.md for manual reproduction traceability
- [ ] Document suspicios behavior and bug candidates as a separate file

### Phase 2: Locator Discovery ⚡ **CRITICAL PHASE - DO NOT SKIP**
- [ ] Hover on each element with `mcp_playwright_browser_hover`
- [ ] Document recommended locators from hover results
- [ ] Prioritize: getByRole > getByTestId > getByText
- [ ] Define elements with locators in autotest, required for test implementation

### Phase 3: Test Generation
- [ ] Create test file with proper imports
- [ ] **Implement test.step() calls that match GWT scenario structure**
- [ ] Implement each step using discovered locators
- [ ] Add assertions for expected outcomes
- [ ] Include mathematical verifications if needed

### Phase 4: Validation
- [ ] Run test multiple times to verify reliability
- [ ] Check test follows Playwright best practices
- [ ] **Ensure mapping between scenario steps and test.step() calls**
- [ ] Document any edge cases discovered
- [ ] Achieve 90%+ success rate
- [ ] **Verify test.step() names match scenario documentation for traceability**


## 🛠️ Quick Commands Reference
- Navigate: `mcp_playwright_browser_navigate`
- Snapshot: `mcp_playwright_browser_snapshot`
- Hover for locators: `mcp_playwright_browser_hover`
- Click: `mcp_playwright_browser_click`
- Type: `mcp_playwright_browser_type`

## 📊 Success Criteria
- ✅ Test passes consistently (90%+ success rate)
- ✅ Uses proper locator hierarchy
- ✅ Completes in 2-3 hours
- ✅ No manual intervention after setup
- ✅ All phases documented in todo list
- ✅ **GWT scenarios documented for manual reproduction**
- ✅ **Test.step() calls match scenario structure exactly**

## 🚫 Common Violations to Avoid
- ❌ Skipping Phase 2 locator discovery
- ❌ Not using hover tool on elements
- ❌ Using CSS selectors without trying semantic locators first
- ❌ Not creating todo list to track progress
- ❌ **Missing GWT scenario documentation**
- ❌ **Test.step() calls that don't match scenario structure**
- ❌ **Generic test.step() names instead of scenario-specific descriptions**

## 🎯 Traceability Benefits
- **Manual Testing**: Scenarios can be executed manually by QA team
- **Automation**: Test steps directly correspond to manual steps
- **Maintenance**: Easy to update both manual and automated tests together
- **Documentation**: Clear requirements and expected behavior
- **Debugging**: Failed test steps map directly to scenario requirements

**This pipeline is enforced automatically via `.cursor/instructions.md`**