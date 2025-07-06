# UI Test Creation Pipeline v2

## ⚠️ STEP-BY-STEP ITERATIVE WORKFLOW

1. **Manual testing** and GWT scenario documentation
2. **For each test step**: Define → Check Reuse → Find Gaps → Implement → Validate → Next Step

## 🔄 **2-Phase Pipeline**

### Phase 1: Manual Exploration & Test Case Preparation
- [ ] Navigate with MCP: `mcp_playwright_browser_navigate`
- [ ] **Manually execute complete scenario** - document all steps
- [ ] **Document detailed GWT steps** in scenarios.md
- [ ] **Break down into individual test steps** for implementation

### Phase 2: Step-by-Step Implementation ⚡ **FOR EACH TEST STEP**

#### 2.1 Define Step Requirements
- [ ] **What elements** does this specific step need?
- [ ] **What actions** need to be performed?
- [ ] **What validations** are expected?

#### 2.2 Check Existing Framework
- [ ] **Scan existing page objects** for this step's elements
- [ ] **Identify reusable locators** for this step
- [ ] **Document what can be reused** immediately

#### 2.3 Gap Analysis for This Step
- [ ] **List missing elements** for this step only
- [ ] **Hover on missing elements**: `mcp_playwright_browser_hover`
- [ ] **Document new locators** needed for this step

#### 2.4 Implement This Step
- [ ] **Use existing locators** where available
- [ ] **Add missing locators** to appropriate page objects
- [ ] **Implement test.step()** matching GWT scenario text
- [ ] **Add assertions** for this step

#### 2.5 Validate This Step
- [ ] **Run test up to this step** - verify it passes
- [ ] **Fix any locator issues** immediately
- [ ] **Confirm step works reliably**

#### 2.6 Proceed to Next Step
- [ ] **Move to next GWT step**
- [ ] **Repeat 2.1-2.6** for next step

## 📋 **Step Implementation Template**

```typescript
// Step: "Click Add to Cart button for Bolt T-Shirt"

// 2.1 Define: Need to click specific product's add-to-cart button
// 2.2 Check: Does homePage have addToCartButton(productName)?
// 2.3 Gap: Need product-specific locator if missing
// 2.4 Implement:
await test.step('Click Add to Cart button for Bolt T-Shirt', async () => {
  await homePage.addToCartBoltTshirt.click(); // Use existing or new locator
});
// 2.5 Validate: Run test, confirm button click works
// 2.6 Next: Move to "Verify cart badge shows 1 item"
```

## 🔄 **Per-Step Dependencies**

```
Manual Testing & GWT Documentation
    ↓
Step 1: Define → Check → Gap → Implement → Validate
    ↓
Step 2: Define → Check → Gap → Implement → Validate
    ↓
Step 3: Define → Check → Gap → Implement → Validate
    ↓
... continue for each GWT step ...
    ↓
Final Validation: Complete test run
```

## 🛠️ **MCP Commands**
- Navigate: `mcp_playwright_browser_navigate`
- Snapshot: `mcp_playwright_browser_snapshot`
- Hover for locators: `mcp_playwright_browser_hover`
- Click: `mcp_playwright_browser_click`
- Type: `mcp_playwright_browser_type`

## ✅ **Success Criteria**
- **Each step implemented and validated** before moving to next
- **Maximum reuse** discovered incrementally per step
- **Minimal page object additions** - only what each step needs
- **Complete test passes** after all steps implemented
- **test.step() names match GWT scenario** text exactly

## 🚫 **Critical Violations**
- ❌ Trying to implement multiple steps at once
- ❌ Adding locators without checking existing page objects first
- ❌ Moving to next step before current step validates
- ❌ Bulk analysis instead of step-by-step discovery
- ❌ Implementing test.step() that doesn't match GWT text

## 🎯 **Benefits of Step-by-Step Approach**
- ✅ **Immediate feedback** - catch issues early per step
- ✅ **Natural reuse discovery** - find opportunities as you go
- ✅ **Reduced complexity** - focus on one step at a time
- ✅ **Incremental validation** - build confidence step by step
- ✅ **Better debugging** - isolate issues to specific steps
- ✅ **Flexible iteration** - adjust approach based on each step's needs

## 📊 **v2 vs v1 Comparison Summary**

### v2 Advantages:
- **Incremental validation** - catch issues immediately
- **Natural workflow** - matches how developers actually work
- **Lower cognitive load** - focus on one step at a time
- **Flexible iteration** - adapt as you learn
- **Better debugging** - isolate problems to specific steps

### v1 Advantages:
- **Comprehensive planning** - see full picture upfront
- **Systematic analysis** - methodical approach to reuse
- **Documentation** - detailed gap analysis

**v2 optimizes for development efficiency and practical workflow**