# HB-028 — Link bridge release checks

Status: PENDING manual mobile browser QA. Do not merge until confirmed.

1. Open `https://vadimzavershinskii.github.io/health-bridge-link/#name=Test%20meal&kcal=100&protein=10&fat=3&carbs=8&meal=Lunch&id=hb028-link-test-01` on Android after PR is deployed. Button should open Health Bridge and create one nutrition record if automatic save and permissions are enabled.
2. Reopen the same link. Confirm only one record exists in Health Connect.
3. Open `https://vadimzavershinskii.github.io/health-bridge-link/?name=Test%20meal&kcal=100&id=hb028-legacy-test`. The button should display `Invalid nutrition link` and must not open the app.
4. Open the base URL without fragment. The button should be inactive.
5. Open a valid fragment with parameters reordered. It should work.
6. Open a fragment with an unexpected parameter or a fragment longer than 3500 characters. It should be rejected.
7. Inspect address bar and network requests: meal data must not be in the query string of the web request. Full URL remains visible to the browser and AI provider.

These checks require deployment to a test URL or the published GitHub Pages site; PR branch code review alone does not establish a PASS. Use test data only, then remove the test record from Health Connect.