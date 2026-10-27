# macspy Drive Transfer — personal Rclone / Google Drive OAuth configuration

This repository hosts the public documentation, privacy policy, and terms for a **personal-use Google Drive OAuth client** used with [Rclone](https://rclone.org/).

This is **not a fork of the Rclone codebase** and **not a hosted download service**. Rclone runs on the user's own computer and downloads authorized Google Drive files locally. The goal is to preserve large directory structures, retry transfers, and verify copied footage without relying on browser ZIP downloads.

**Public site (once GitHub Pages is enabled):**
- Home: https://macspy.github.io/rclone/
- Privacy Policy: https://macspy.github.io/rclone/privacy.html
- Terms of Use: https://macspy.github.io/rclone/terms.html

## Publish the website (one-time)

1. In this repository, open **Settings → Pages**.
2. In **Build and deployment**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/(root)**, then click **Save**.
4. Visit the three links above in a private/incognito window. Confirm they are publicly visible without signing in and not returning a 404. GitHub Pages may take a few minutes to deploy.

All website content is static HTML. No backend, install, or JavaScript is required.

## Google Cloud OAuth branding values

Under **Google Auth Platform → Branding** (or OAuth consent screen), use:

| Field | Value |
| --- | --- |
| Application name | macspy Drive Transfer (or the actual name of your Google OAuth app; keep it consistent with the homepage) |
| Homepage | `https://macspy.github.io/rclone/` |
| Privacy policy | `https://macspy.github.io/rclone/privacy.html` |
| Terms of service | `https://macspy.github.io/rclone/terms.html` |
| Authorized domain | `macspy.github.io` (if accepted and ownership is verified) |

**Keep the OAuth client type as `Desktop app` if configuring Rclone on your Mac.** Request only the Google Drive permissions necessary for your use, preferably Drive read-only (`https://www.googleapis.com/auth/drive.readonly`) when downloads are all you need.

**Do not add OAuth credentials, refresh tokens, or client secrets to this repository.** Enter your own Google OAuth client ID and secret into Rclone locally.

## Fix the "homepage URL is not registered to you" issue

Code changes alone **cannot complete ownership verification**. You must prove site control through [Google Search Console](https://search.google.com/search-console).

1. Confirm GitHub Pages is publicly serving the homepage.
2. Sign in to Search Console using a Google account that is an **Owner or Editor** of the associated Google Cloud project.
3. Add an appropriate **URL-prefix** property, e.g. `https://macspy.github.io/rclone/`, and choose **HTML file** verification if offered.
4. Download the exact Google verification HTML file (usually named `google<token>.html`) and upload it to this repository's **root**, on the published `main` branch. Then confirm the corresponding URL under `https://macspy.github.io/rclone/` serves the expected HTML file.
5. Complete the verification step in Search Console. Confirm the verified property covers the homepage / authorized domain Google is validating. If Google requires verification of `https://macspy.github.io/` itself (rather than the `/rclone/` prefix), you will need to control that **site root**, typically by creating a separate `macspy/macspy.github.io` GitHub Pages repository or using a domain you own. A project repository cannot publish files at the account's root URL.
6. Return to Google Auth Platform's branding verification and request another review only once all listed issues are fixed.

**Important:** A Search Console verification token cannot be generated or guessed in this repository. It must come from your Google account. Do not paste secrets here; the Search Console verification HTML file is intended to be publicly accessible.

## Personal-use Rclone: verification may not be necessary

[Google's verification exception](https://support.google.com/cloud/answer/13464323) generally allows personal-use apps with fewer than 100 users to run without full OAuth verification, although an unverified-app warning may appear. The [official Rclone Google Drive guide](https://rclone.org/drive/#making-your-own-client_id) recommends a personal OAuth client and explains publishing versus testing. In testing mode, Drive-scope refresh grants commonly expire after seven days; publishing the app to production can avoid that inconvenience even if you do not complete full brand/scope verification.

Google's policies still apply. The Google Cloud project's configured scopes, account status, and actual requested scopes can affect behavior.

## Files in this repository

- `index.html` — public, login-free homepage identifying what the configuration does.
- `privacy.html` — accessible privacy policy explaining data access, use, storage, retention, sharing, deletion, and Google API Limited Use.
- `terms.html` — terms and independence notice.
- `README.md` — publication and Google configuration steps.

## Important notes

- This repository does not store or process personal Google Drive data.
- You must keep the privacy policy truthful if you later add a hosted service, sharing, telemetry, or other processing.
- Rclone is a third-party open-source project and this repository is not affiliated with Rclone or Google.
- For private technical or authentication problems, avoid posting credentials in public GitHub Issues.
