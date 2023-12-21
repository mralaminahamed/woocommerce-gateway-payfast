## E2E Tests

This directory contains end-to-end tests for the project, utilizing [Playwright](https://playwright.dev) to run tests in Chromium browser.

### Pre-requisites
- Create [sandbox PayFast](https://sandbox.payfast.co.za/) account which used for test payments.

### Dependencies for local testing
- Add `.env` file with PayFast credentials in `./tests/e2e/config` directory.
```
PAYFAST_MERCHANT_ID=********
PAYFAST_MERCHANT_KEY=********
PAYFAST_PASSPHRASE=********
```

### Run E2E tests in local
1. Run `npm install`.
2. Run `npx playwright install`.
3. Run `npm run env:start-local`  (Note: Please start Docker before executing this command).
4. Add environment variables to the `/tests/e2e/config/.env` file (as mentioned above).
5. Run `npm run test:e2e-local`.

### Dependencies for Github Action testing
- Add bot token to Github,
```
gh secret set BOT_GITHUB_TOKEN --app actions --repo=woocommerce/woocommerce-gateway-payfast
```
- Add PayFast credentials to Github.
```
gh secret set PAYFAST_MERCHANT_ID --app actions --repo=woocommerce/woocommerce-gateway-payfast
gh secret set PAYFAST_MERCHANT_KEY --app actions --repo=woocommerce/woocommerce-gateway-payfast
gh secret set PAYFAST_PASSPHRASE --app actions --repo=woocommerce/woocommerce-gateway-payfast
```

**Note**:
- Add the GitHub secret only if it doesn't already exist. Utilize the following command to check if the secret exists:
```
gh secret list --app actions --repo=woocommerce/woocommerce-gateway-payfast
```
### Run E2E tests in the pull request

- Add the `needs: e2e testing` label to the pull request; it will initiate the E2E test GitHub action to run tests against the PR.

