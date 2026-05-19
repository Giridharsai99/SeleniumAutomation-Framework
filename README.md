# Selenium Automation Framework

End-to-end UI + API test automation framework built with **Java 17, Selenium 4, TestNG, and REST Assured**, demonstrating production-grade patterns: Page Object Model, thread-safe parallel execution, data-driven testing, CI integration, and rich reporting.

> 🚧 **Status:** Active development — see the [Roadmap](#roadmap) section for progress.

---

## 🛠 Tech Stack

| Layer | Tool |
|---|---|
| Language | Java 17 |
| UI Automation | Selenium WebDriver 4.21 |
| Test Runner | TestNG 7.10 |
| API Testing | REST Assured 5.4 |
| Build | Maven |
| Reporting | ExtentReports / Allure |
| Logging | Log4j2 |
| CI | Jenkins (Pipeline) |
| Version Control | Git + GitHub |

---

## 📁 Project Structure

```
Selenium-Automation-Framework/
├── pom.xml
├── testng.xml
├── README.md
├── .gitignore
├── config/
│   └── config.properties
├── src/
│   ├── main/java/com/giridhar/framework/
│   │   ├── base/           # BasePage, BaseTest
│   │   ├── driver/         # DriverFactory, ThreadLocal management
│   │   ├── pages/          # Page Object classes
│   │   ├── utils/          # ConfigReader, ExcelUtils, WaitUtils
│   │   └── listeners/      # TestNG listeners for reporting
│   └── test/java/com/giridhar/tests/
│       ├── ui/             # UI test classes
│       └── api/            # API test classes
└── test-output/            # Generated reports
```

---

## ✨ Key Features

- ✅ **Page Object Model** with fluent method chaining
- ✅ **Thread-safe parallel execution** via ThreadLocal WebDriver
- ✅ **Cross-browser** support (Chrome, Firefox, Edge) via `-Dbrowser=` system property
- ✅ **Environment switching** via `-Denv=qa|staging|prod`
- ✅ **Data-driven** tests using TestNG DataProvider + Excel (Apache POI)
- ✅ **Explicit waits only** — zero `Thread.sleep` in the codebase
- ✅ **Screenshot on failure** via custom TestNG listener
- ✅ **ExtentReports** with logs, screenshots, and execution time
- ✅ **REST Assured** integration for API state setup (faster than UI seeding)
- ✅ **Jenkins pipeline** for nightly and on-demand runs

---

## 🚀 Getting Started

### Prerequisites
- JDK 17+
- Maven 3.8+
- Chrome / Firefox / Edge installed

### Clone & Run
```bash
git clone https://github.com/<your-username>/Selenium-Automation-Framework.git
cd Selenium-Automation-Framework
mvn clean test
```

### Run a specific suite
```bash
mvn test -Dsuite=smoke
mvn test -Dsuite=regression
```

### Run on a specific browser / environment
```bash
mvn test -Dbrowser=firefox -Denv=staging
```

### View the report
After execution, open: `test-output/extent-reports/index.html`

---

## 🧪 Sample Test (Page Object Model)

```java
@Test(description = "User can log in with valid credentials")
public void validLogin() {
    DashboardPage dashboard = new LoginPage(driver)
            .open()
            .enterUsername(ConfigReader.get("validUser"))
            .enterPassword(ConfigReader.get("validPassword"))
            .submit();

    Assert.assertTrue(dashboard.isLoaded(), "Dashboard should load after login");
    Assert.assertEquals(dashboard.getWelcomeText(), "Welcome, tomsmith");
}
```

---

## 🗺 Roadmap

- [x] Project setup with Maven and dependencies
- [ ] DriverFactory + ThreadLocal driver management
- [ ] Base classes (BasePage, BaseTest)
- [ ] Page Objects for the demo app (`saucedemo.com`)
- [ ] 10 UI test scenarios with assertions
- [ ] Data-driven login tests (Excel + DataProvider)
- [ ] ExtentReports integration
- [ ] Screenshot-on-failure listener
- [ ] REST Assured API test suite
- [ ] Cross-browser parallel execution
- [ ] Jenkins pipeline (Jenkinsfile)
- [ ] Dockerised Selenium Grid setup

---

## 📊 Test Coverage Progress

| Module | UI Tests | API Tests | Status |
|---|---|---|---|
| Login & Auth | 0 / 8 | 0 / 4 | 🟡 In progress |
| Product Catalog | 0 / 6 | 0 / 3 | ⚪ Not started |
| Cart & Checkout | 0 / 10 | 0 / 5 | ⚪ Not started |

---

## 📚 What I Learned Building This

This framework is part of my transition from manual QA (4.5 years) to SDET. Key takeaways documented here:

- **Why explicit waits beat implicit waits** — coming soon as a blog post
- **ThreadLocal vs static driver** — coming soon
- **POM done right: page objects return next page, not void** — coming soon

---

## 👤 Author

**Giridhar Sai Kasula** — QA Engineer transitioning to SDET
[LinkedIn](https://www.linkedin.com/in/giridharsai-kasula-70991316a/) • [LeetCode](https://leetcode.com/u/kgssvathsav/)

---

## 📝 License

MIT
