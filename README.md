# CCIS-673 Cloud OS Lab Dashboard

A public-data-only three-page static site for Azure Static Web Apps Free.

## Layout
- `index.html`: introduction
- `progress.html`: accessible local-only checklist
- `architecture.html`: request path and shared-responsibility analysis
- `404.html`: custom error page
- `staticwebapp.config.json`: 404 override and security headers
- `assets/`: CSS and JavaScript

## Local testing
From the repository root, run `python -m http.server 8000` and visit `http://localhost:8000/`. Open each navigation link. Check and reset tasks on the progress page. Try `http://localhost:8000/not-real` (the basic Python server gives a 404 status but does **not** apply Azure's custom error configuration). The custom 404 page must be verified after Azure deployment.

## Deploy (Azure portal)
1. Confirm Azure for Students eligibility, remaining credit, spending limit, supported region and Static Web Apps **Free** plan. Do not add a payment method or upgrade.
2. Create a GitHub repository and upload the files **at repository root**. Commit to `main`.
3. Azure portal > Create > Static Web Apps; select the student subscription, a dedicated lab resource group, Free plan, GitHub source, repository and `main` branch.
4. For this root-level no-framework site use **Custom** build settings: app location `/`, API location blank, output location blank. Inspect the generated workflow; for a static site with no build, its `skip_app_build` may be `true`, with `app_location: '/'` and `output_location: ''`. Do not overwrite the portal-generated deployment token or workflow blindly.
5. Verify the GitHub Actions deployment run and open the HTTPS URL. Test `/not-real` and inspect HTTP 404 and response headers using browser DevTools or `curl -I https://YOUR-APP.azurestaticapps.net/not-real`.
6. Create a branch, visibly change site copy, commit, open a PR, inspect preview if available, merge and verify production. Revert the change using `git revert COMMIT_SHA`, verify the prior behavior, then restore the desired text in another commit. Capture commit IDs and screenshots.
7. Capture subscription offer, Free tier, cost/credit view, workflow, 404 status, response header, update/rollback, and cleanup. Redact all identifiers.

## Privacy and cost
No login, student IDs, subscription IDs, tokens, private course files, or credentials belong in the repo. The checklist uses browser localStorage only. Budget alerts are not hard caps. Keep only the Free site needed for Assignment 2.
