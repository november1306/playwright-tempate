# Page Object Model Rules

## 📚 **GOLDEN RULE: Existing Page Objects as Library**
- **ONLY add missing locators** you need for your test
- **ONLY fix broken locators** that don't work
- **NO refactoring** working methods or renaming for "consistency"

## ✅ **Page Objects Should Contain:**

### 1. **Locators (Primary Purpose)**
```typescript
readonly submitButton: Locator;
readonly usernameInput: Locator;
readonly errorMessage: Locator;
```

### 2. **Complex Multi-Step Operations**
```typescript
// ✅ 3+ steps worth abstracting
async fillCheckoutInfo(firstName: string, lastName: string, zip: string) {
  await this.firstNameInput.fill(firstName);
  await this.lastNameInput.fill(lastName);
  await this.zipInput.fill(zip);
}
```

### 3. **Essential Flow Validations**
```typescript
// ✅ Critical for test stability only
async isLoaded() {
  await expect(this.page).toHaveURL(/checkout/);
  await expect(this.pageTitle).toBeVisible();
}
```

## ❌ **Page Objects Should NOT Contain:**

### 1. **Test Data**
```typescript
// ❌ BAD: Hardcoded data
async fillStandardUser() {
  await this.input.fill('john.doe');  // NO!
}

// ✅ GOOD: Parameters
async fillUser(username: string) {
  await this.input.fill(username);
}
```

### 2. **Validations/Expects**
```typescript
// ❌ BAD: Hidden in page object
async verifySuccess() {
  await expect(this.message).toContainText('Success!');
}

// ✅ GOOD: Explicit in test
await expect(pageObject.message).toContainText('Success!');
```

### 3. **One-Liner Wrappers**
```typescript
// ❌ BAD: Pointless wrapper
async clickSubmit() {
  await this.submitButton.click();
}

// ✅ GOOD: Direct usage
await pageObject.submitButton.click();
```

## ⚡ **Quick Decision: Include in Page Object?**

| Action | Include? | Why |
|--------|----------|-----|
| Single `.click()` or `.fill()` | ❌ NO | Use locator directly |
| 3+ steps together | ✅ YES | Complex operation |
| Has hardcoded values | ❌ NO | Test data in test |
| Contains `expect()` | ❌ NO | Validations in test |
| Page load check | ✅ YES | Flow stability |

## 📂 **File Structure**
```
tests/[feature]/
├── pageObject/
│   ├── index.ts
│   ├── loginPage.ts
│   └── checkoutPage.ts
├── scenarios.md
└── [feature]-test.spec.ts
```

## 📋 **Template**
```typescript
import { Page, Locator, expect } from '@playwright/test';

export class ExamplePage {
  readonly page: Page;
  readonly submitButton: Locator;
  readonly usernameInput: Locator;

  constructor(page: Page) {
    this.page = page;
    this.submitButton = page.locator('[data-test="submit"]');
    this.usernameInput = page.locator('[data-test="username"]');
  }

  async isLoaded() {
    await expect(this.page).toHaveURL(/expected-pattern/);
  }
}
```

**Remember: Page objects are for LOCATORS and COMPLEX OPERATIONS only!**