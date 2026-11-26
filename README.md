# OrangeHRM Playwright Test Suite

This project contains end-to-end UI tests written with [Playwright](https://playwright.dev/) for the OrangeHRM demo application. The suite covers login behavior and employee creation, and includes a basic Playwright documentation example.

## Test Coverage

- Valid login and dashboard visibility
- Login with a valid username and invalid password
- Add a new employee using generated Faker names
- Playwright title and navigation examples

## Prerequisites

- Node.js 20 or later
- npm
- Internet access to reach `https://opensource-demo.orangehrmlive.com`

## Installation

Clone the repository and install the dependencies:

```powershell
npm install
npx playwright install chromium
```

Use `npx playwright install --with-deps chromium` on a Linux environment if system dependencies are missing.

## Running the Tests

Run the complete suite in Chromium:

```powershell
npx playwright test
```

Run a specific test file:

```powershell
npx playwright test tests/Login.spec.js
npx playwright test tests/addemployee.spec.js
npx playwright test tests/example.spec.js
```

Open an interactive test run:

```powershell
npx playwright open
npx playwright test --ui
```

Open the latest HTML report:

```powershell
npx playwright show-report
```

Run the tests in headed mode:

```powershell
npx playwright test --headed
```

## Configuration

The main configuration is in [playwright.config.js](playwright.config.js):

- Tests are loaded from `./tests`
- The base URL is `https://opensource-demo.orangehrmlive.com`
- Chromium/Desktop Chrome is enabled
- Parallel execution is disabled
- Tests retry once locally and twice in CI
- CI runs use one worker
- HTML reporting is enabled
- Traces and videos are always recorded
- Screenshots are recorded when tests fail
- Expect assertions use a 20-second timeout

The OrangeHRM login credentials are stored in [testdata/logindata/logindata.json](testdata/logindata/logindata.json). Employee fixture data is available in [testdata/addempdata/empdata.json](testdata/addempdata/empdata.json), although the add-employee test currently generates names with Faker instead.

## Project Structure

```text
.
|-- tests/
|   |-- Login.spec.js
|   |-- addemployee.spec.js
|   `-- example.spec.js
|-- testdata/
|   |-- logindata/
|   |   `-- logindata.json
|   `-- addempdata/
|       `-- empdata.json
|-- playwright.config.js
|-- package.json
|-- package-lock.json
`-- .gitignore
```

Generated folders such as `test-results/`, `playwright-report/`, and `node_modules/` are excluded by [.gitignore](.gitignore).

## Notes

- The OrangeHRM demo environment is publicly hosted and shared; test data and availability may change.
- The demo credentials and application behavior should be verified if login or dashboard tests begin failing.
- The employee test creates a new employee on every successful run because first, middle, and last names are generated dynamically.
