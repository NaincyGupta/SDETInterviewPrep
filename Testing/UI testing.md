### FOR WEB BASED TESTING
- selenium with javascript
- playwright with typescript having both UI and API test for web app

---
### MIGRATION 
### 🚀 Why Move from Selenium + JS to Playwright + JS/TS
#### In short

#### 1. **Modern Architecture & Reliability**

* Playwright: Establishes a single, persistent WebSocket connection directly with the browser. All commands and responses are exchanged through this open channel, utilizing the browser's native protocol. This direct communication minimizes overhead and latency.
* Selenium: Relies on the WebDriver protocol, which involves sending commands over HTTP (typically as JSON) to a browser-specific driver (e.g., ChromeDriver). This process introduces latency for each command as it requires establishing and sending commands over a TCP connection for every action. 

#### Built-in Auto-Waiting:
Playwright automatically waits for elements to be ready before performing actions, reducing the need for explicit waits and minimizing the chances of flaky tests due due to timing issues. Selenium often requires more manual handling of waits, which can impact performance and reliability if not managed carefully.

#### 2. **UI + API Testing in One Framework**

* Selenium is only for **UI testing**.
* Playwright natively supports **API testing** (e.g., `request.newContext()` for mocking, intercepting, validating API calls).
* This enables **end-to-end workflows**: login via API, validate DB state, continue on UI seamlessly.


#### 2. **Cross-Browser & Cross-Platform Out of the Box**

* Selenium needs separate driver binaries (ChromeDriver, GeckoDriver, etc.).
* Playwright ships with all major browsers bundled and managed automatically.


#### 4. **Faster Execution & Parallelization**

* Playwright supports **parallel test execution** and **test isolation** out of the box.
* Selenium requires external libraries/test runners (Mocha/Jest/TestNG, etc.) to achieve the same.

#### 5. **Auto-Wait & Flake Reduction**

* Selenium scripts often require manual waits (explicit/implicit).
* Playwright has **auto-waiting** for elements, network stability, animations → drastically reduces flakiness.

#### 6. **TypeScript Support**

* Playwright is written in **TypeScript** with strong type definitions.
* Provides better **intellisense, compile-time error detection**, and maintainability vs plain Selenium + JS.

#### 7. **Test Generator & Inspector Tools**

* Playwright has tools like **Codegen** (record and generate tests automatically).
* Includes built-in **trace viewer, video recording, and screenshots** for debugging.
* Selenium needs third-party tools to achieve the same.

#### 8. **Network Interception & Mocking**

* Playwright allows you to **mock/stub APIs, intercept network traffic, manipulate responses** → perfect for testing negative/failure scenarios.
* Selenium cannot do this natively; you’d need tools like BrowserMob Proxy.

#### 9. **CI/CD Friendly**

* Playwright integrates easily with **GitHub Actions, Jenkins, Azure DevOps, etc.**.
* Headless, container-friendly, faster execution → better suited for modern pipelines.

#### 10. **Future Proof & Industry Trend**

* Many companies are migrating towards Playwright/Cypress because Selenium is considered **legacy** for UI automation.
* Playwright is backed by Microsoft, rapidly evolving, and gaining wide industry adoption.

PLAYWRIGHT TUTORIAL

https://www.youtube.com/watch?v=788GvvcfwTY

MOBILE TESTING FRAMEWORK

Perfect — this is a **classic interview question** and also something you can use as a real deliverable. Let’s go step by step:

---

# 📱 Mobile Test Automation Framework (Appium + WebdriverIO + TypeScript)

This setup is widely used for **cross-platform mobile automation** since:

* **Appium** → provides iOS + Android automation.
* **WebdriverIO** → modern JS/TS automation framework, easy Appium integration.
* **TypeScript** → type-safety and better maintainability.

---

## 🔹 1. Key Components of the Framework

1. **Appium Server** → interacts with iOS/Android apps.
2. **WebdriverIO (wdio)** → test runner + automation APIs.
3. **TypeScript** → ensures type-safety, reusable utilities.
4. **Page Object Model (POM)** → keeps locators & actions modular.
5. **Custom Utilities** → for waits, API calls, data setup, screenshots.
6. **Test Data Management** → JSON/YAML files for test data.
7. **Reporter/Logger** → Allure, Spec reporter.
8. **CI/CD** → GitHub Actions/Jenkins for pipeline runs.
9. **Device Cloud** → BrowserStack, SauceLabs, or local Appium servers.

---

## 🔹 2. Folder Structure (Recommended)

```
mobile-automation/
│── config/
│   ├── wdio.android.conf.ts
│   ├── wdio.ios.conf.ts
│   └── wdio.shared.conf.ts   # shared config (reporters, timeouts, etc.)
│
│── src/
│   ├── pages/
│   │   ├── android/          # platform-specific pages if needed
│   │   ├── ios/
│   │   └── common/           # cross-platform page objects
│   │       └── Login.page.ts
│   │       └── Home.page.ts
│   │
│   ├── tests/
│   │   ├── login.e2e.ts
│   │   ├── checkout.e2e.ts
│   │   └── profile.e2e.ts
│   │
│   ├── utils/
│   │   ├── wait.ts           # custom wait helpers
│   │   ├── logger.ts         # logger wrapper
│   │   ├── apiClient.ts      # axios-based API utility
│   │   └── device.ts         # device-specific helpers (orientation, reset)
│   │
│   ├── data/
│   │   ├── users.json        # test data
│   │   └── config.json
│   │
│   └── typings/
│       └── global.d.ts       # custom TypeScript typings
│
│── reports/                  # allure, junit, screenshots
│── .env                      # env variables (app package, activity, etc.)
│── package.json
│── tsconfig.json
```

---

## 🔹 3. Sample Code Snippets

### **Page Object (Login.page.ts)**

```typescript
import { ChainablePromiseElement } from 'webdriverio';

class LoginPage {
  get usernameField(): ChainablePromiseElement<WebdriverIO.Element> {
    return $('~username');
  }
  get passwordField() { return $('~password'); }
  get loginButton() { return $('~loginBtn'); }

  async login(username: string, password: string) {
    await this.usernameField.setValue(username);
    await this.passwordField.setValue(password);
    await this.loginButton.click();
  }
}

export default new LoginPage();
```

### **Test (login.e2e.ts)**

```typescript
import LoginPage from '../pages/common/Login.page';
import HomePage from '../pages/common/Home.page';

describe('Login Tests', () => {
  it('should login with valid credentials', async () => {
    await LoginPage.login('testuser', 'password123');
    await expect(await HomePage.welcomeMessage).toBeDisplayed();
  });
});
```

### **Custom Wait Utility (wait.ts)**

```typescript
export async function waitForDisplayed(
  element: WebdriverIO.Element, timeout = 10000
) {
  await element.waitForDisplayed({ timeout });
}
```

### **Custom Device Utility (device.ts)**

```typescript
export async function resetApp() {
  await driver.reset();
}

export async function changeOrientation(orientation: 'LANDSCAPE' | 'PORTRAIT') {
  await driver.setOrientation(orientation);
}
```

---

## 🔹 4. Custom Utilities to Include

* **Wait helpers** → avoid flakiness (e.g., waitForDisplayed, waitForEnabled).
* **API client** → use `axios` for backend validation (before/after tests).
* **Logger** → `winston` or `pino` for structured logging.
* **Screenshot utility** → take screenshots on failure (`afterTest` hook).
* **Device utils** → reset app, toggle network, change orientation.
* **Test data loader** → read JSON/YAML for data-driven tests.

---

## 🔹 5. Execution & CI/CD

* Run **Android tests**:

  ```bash
  npx wdio config/wdio.android.conf.ts
  ```
* Run **iOS tests**:

  ```bash
  npx wdio config/wdio.ios.conf.ts
  ```
* Integrate with **GitHub Actions** or **Jenkins** → run on BrowserStack or SauceLabs.

---

✅ **Summary:**
You’ll build a **cross-platform framework** in **TypeScript using WebdriverIO + Appium**, follow **Page Object Model**, maintain **separate configs for iOS & Android**, and add **custom utilities for waits, device control, API validation, and logging**.

---
MOBILE TESTING

Perfect 👌 You’re asking exactly what a **hiring manager** wants to hear when they say “tell me how you’d build a mobile automation framework.” Let’s break it down **folder by folder** with reasoning, examples, and what lives inside.

---

# 📂 Mobile Test Automation Framework (Appium + WebdriverIO + TypeScript)

```
mobile-automation/
├── configs/
│   ├── wdio.android.conf.ts
│   ├── wdio.ios.conf.ts
│   ├── wdio.staging.conf.ts
│   ├── wdio.prod.conf.ts
│   └── wdio.shared.conf.ts
│
├── test/
│   ├── specs/
│   │   ├── login.spec.ts
│   │   ├── checkout.spec.ts
│   │   └── subscription.spec.ts
│   │
│   ├── pageobjects/
│   │   ├── LoginScreen.ts
│   │   ├── CheckoutScreen.ts
│   │   ├── SubscriptionScreen.ts
│   │   └── BaseScreen.ts
│   │
│   ├── data/
│   │   ├── users.json
│   │   ├── subscriptions.json
│   │   └── payments.json
│   │
│   ├── utils/
│   │   ├── waits.ts
│   │   ├── gestures.ts
│   │   ├── snapshot.ts
│   │   ├── recorder.ts
│   │   ├── apiHelper.ts
│   │   └── dataSetup.ts
│   │
│   └── locators/
│       ├── login.locators.ts
│       ├── checkout.locators.ts
│       └── subscription.locators.ts
│
├── reports/                # Test reports (Allure/HTML)
├── ci/
│   ├── regression.yml       # GitHub Actions workflow
│   ├── smoke.yml
│   └── nightly.yml
│
├── package.json
└── tsconfig.json
```

---

## 🔹 **1. Configs Folder**

* `wdio.shared.conf.ts` → base config (timeouts, reporters, log levels).
* `wdio.android.conf.ts` → Android capabilities.
* `wdio.ios.conf.ts` → iOS capabilities.
* `wdio.staging.conf.ts`, `wdio.prod.conf.ts` → env-specific base URLs.

👉 **Example (Android config)**:

```ts
export const config = {
  ...shared,
  capabilities: [{
    platformName: 'Android',
    deviceName: 'Pixel_5',
    automationName: 'UiAutomator2',
    app: './apps/android/MyApp.apk'
  }]
};
```

---

## 🔹 **2. Specs Folder (Test cases)**

* Each `.spec.ts` represents an E2E flow.
* Follow BDD-style naming for readability.

👉 Example: `login.spec.ts`

```ts
import LoginScreen from '../pageobjects/LoginScreen';

describe('Login Tests', () => {
  it('should login with valid credentials', async () => {
    await LoginScreen.login('testUser', 'testPass');
    expect(await $('~welcomeMessage')).toBeDisplayed();
  });

  it('should show error for invalid login', async () => {
    await LoginScreen.login('wrong', 'wrong');
    expect(await $('~errorMessage')).toHaveText('Invalid credentials');
  });
});
```

---

## 🔹 **3. PageObjects Folder**

* Encapsulates screens + methods.
* Inherits from a `BaseScreen` class with generic methods (tap, wait, swipe).

👉 Example: `LoginScreen.ts`

```ts
import locators from '../locators/login.locators';

class LoginScreen {
  get username() { return $(locators.username); }
  get password() { return $(locators.password); }
  get loginBtn() { return $(locators.loginBtn); }

  async login(user: string, pass: string) {
    await this.username.setValue(user);
    await this.password.setValue(pass);
    await this.loginBtn.click();
  }
}
export default new LoginScreen();
```

---

## 🔹 **4. Locators Folder**

* Keeps Android and iOS locators separate.
* Use `platformName` check inside locators.

👉 Example: `login.locators.ts`

```ts
export default {
  username: driver.isAndroid ? 'android=new UiSelector().resourceId("username")' : '~username',
  password: driver.isAndroid ? 'android=new UiSelector().resourceId("password")' : '~password',
  loginBtn: driver.isAndroid ? 'android=new UiSelector().text("Login")' : '~loginBtn'
};
```

---

## 🔹 **5. Data Folder**

* Test data in JSON/TS for reusability.

👉 Example: `users.json`

```json
{
  "validUser": { "username": "testUser", "password": "testPass" },
  "invalidUser": { "username": "wrong", "password": "wrong" }
}
```

---

## 🔹 **6. Utils Folder**

* `waits.ts` → explicit waits.
* `gestures.ts` → swipe, scroll, drag/drop.
* `snapshot.ts` → take screenshot after each failure.
* `recorder.ts` → start/stop screen recording (Appium APIs).
* `apiHelper.ts` → REST calls for setup/teardown.
* `dataSetup.ts` → create test users/subscriptions before test run.

👉 Example: `waits.ts`

```ts
export async function waitForDisplayed(element, timeout = 10000) {
  await element.waitForDisplayed({ timeout });
}
```

👉 Example: `snapshot.ts`

```ts
export async function takeScreenshot(testName: string) {
  await driver.saveScreenshot(`./reports/screenshots/${testName}.png`);
}
```

---

## 🔹 **7. CI Folder (Automation Pipelines)**

* `regression.yml` → full regression suite nightly.
* `smoke.yml` → smoke tests on each PR.
* `nightly.yml` → run on device cloud (BrowserStack/Sauce).

👉 Example snippet from `regression.yml`

```yml
jobs:
  regression:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install dependencies
        run: npm install
      - name: Run Android regression
        run: npx wdio ./configs/wdio.android.conf.ts
      - name: Run iOS regression
        run: npx wdio ./configs/wdio.ios.conf.ts
```

---

## 🔹 **8. Package.json Scripts**

```json
"scripts": {
  "test:android": "wdio ./configs/wdio.android.conf.ts",
  "test:ios": "wdio ./configs/wdio.ios.conf.ts",
  "test:smoke": "wdio ./configs/wdio.staging.conf.ts --suite smoke",
  "test:regression": "wdio ./configs/wdio.prod.conf.ts --suite regression",
  "report:allure": "allure generate ./reports/allure-results --clean && allure open"
}
```

---

## 🔹 **9. Performance, Load, Stress**

* **Mobile app performance** → Appium + `adb` (Android) or Xcode Instruments (iOS).
* **API layer performance** → Integrate **JMeter or k6** in parallel for load/stress tests.
* Report latency, memory, CPU usage alongside functional test reports.

---

✅ This structure covers:

* **Scalable design** (POM, configs per env/platform)
* **Maintainability** (locators & data separate)
* **Utilities** for common tasks
* **CI/CD** ready with regression/smoke pipelines
* **Performance/load testing** extensions

---



