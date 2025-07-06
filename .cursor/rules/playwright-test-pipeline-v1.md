# UI Test Creation Pipeline v1

## ⚠️ ITERATIVE WORKFLOW - Not Strictly Sequential

1. **Todo lists** to track all phases
2. **Early page object analysis** - know what exists before discovering locators
3. **Gap-based locator discovery** - only find missing elements
4. **Iterative test implementation** - may require additional locator discovery
5. **Surgical page object updates** - minimal additions only

## 🔄 **Iterative Pipeline**

### Phase 1: Manual Exploration
- [ ] Navigate with MCP: `mcp_playwright_browser_navigate`
- [ ] Take snapshot and manually execute scenario steps
- [ ] Document GWT steps in scenarios.md

### Phase 2: Framework Analysis ⚡ **CRITICAL - DO FIRST**
- [ ] **Analyze existing page objects** - what locators already exist?
- [ ] **Map scenario elements** to existing locators
- [ ] **Identify gaps** - which elements are missing from page objects?
- [ ] **Document reuse plan** - what can be reused vs what needs discovery

### Phase 3: Gap-Based Locator Discovery ⚡ **ITERATIVE**
- [ ] **Only hover on missing elements**: `mcp_playwright_browser_hover`
- [ ] Document recommended locators for gaps only
- [ ] Prioritize: getByRole > getByTestId > getByText > CSS
- [ ] **Cross-reference with existing patterns** in page objects

### Phase 4: Test Implementation ⚡ **ITERATIVE**
- [ ] Create test file with imports for existing page objects
- [ ] **Implement test.step() calls using existing locators first**
- [ ] **Use discovered locators for gaps**
- [ ] Add assertions for expected outcomes
- [ ] **↻ Return to Phase 3** if additional elements needed

### Phase 5: Validation ⚡ **ITERATIVE**
- [ ] Run test multiple times for reliability
- [ ] Achieve 90%+ success rate
- [ ] **Verify test.step() names match scenario documentation**
- [ ] **↻ Return to Phase 3/4** if locators fail or additional elements needed

### Phase 6: Surgical Page Object Updates ⚡ **FINAL**
- [ ] **Add ONLY missing locators** to existing page objects
- [ ] **NO refactoring** of working methods or locators
- [ ] **Update test imports** if new page objects created
- [ ] **Final validation** - test still passes

## 🔄 **Iterative Dependencies**

```
Phase 1 (Exploration)
    ↓
Phase 2 (Framework Analysis) ⚡ BLOCKING
    ↓
Phase 3 (Gap Discovery) ⟷ Phase 4 (Implementation) ⟷ Phase 5 (Validation)
    ↓
Phase 6 (Surgical Updates)
```

## 📋 **Phase 2 Framework Analysis Checklist**
- [ ] List all page objects in `pageObject/` folder
- [ ] **Inventory existing locators** for each page
- [ ] **Match scenario elements** to existing locators
- [ ] **Create gap list** - elements not covered by existing locators
- [ ] **Document reuse strategy** before any new discovery

## 🛠️ **MCP Commands**
- Navigate: `mcp_playwright_browser_navigate`
- Snapshot: `mcp_playwright_browser_snapshot`
- Hover for locators: `mcp_playwright_browser_hover`
- Click: `mcp_playwright_browser_click`
- Type: `mcp_playwright_browser_type`

## ✅ **Success Criteria**
- **Framework analysis completed before locator discovery**
- **Maximum reuse** of existing page object locators
- **Minimal additions** to page objects (surgical updates only)
- Test passes consistently (90%+ success rate)
- test.step() calls match scenario structure

## 🚫 **Critical Violations**
- ❌ Discovering locators before analyzing existing page objects
- ❌ Creating duplicate locators that already exist
- ❌ Not documenting the gap analysis
- ❌ Making test implementation changes to existing page objects
- ❌ Linear execution instead of iterative refinement

**This pipeline is enforced automatically via `.cursor/instructions.md`**