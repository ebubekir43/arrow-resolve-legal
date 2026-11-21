# Arrow Resolve Original — GitHub Pages Legal Center

Files: `index.html`, `privacy.html`, `terms.html`, `delete-account.html`, `style.css`.

Developer: **Kygsz / Ebubekir Kaygısız**  
Support: **skyg66210@gmail.com**  
Draft prepared: **21 November 2026**.

## IMPORTANT — REVIEW BEFORE PUBLISHING

**These are draft legal texts for the intended release features, not a verified audit of the current APK.** Before making the GitHub Pages site public, verify actual Flutter dependencies and flows against the wording, especially:

- Actual sign-in provider, Google user data fields and guest-mode behavior.
- Supabase project configuration, which data is uploaded and when, retention, and true account deletion behavior.
- AdMob ad ID/advertising identifiers, consent/UMP, child-directed settings, diagnostic SDKs and disclosures.
- Google Play Billing products and purchase restoration mechanisms.
- Notification SDKs and other analytics/crash/attribution tools that may be installed.
- Actual advertised account-deletion path in Settings: required for Google Play where account creation exists. The page contains a working `mailto:` request route but this alone does not implement in-app deletion.
- Data Safety form must truthfully match the production SDK and privacy policy.
- Suitable wording for intended age group and jurisdiction (including Türkiye KVKK / GDPR where relevant).

Do **not** publish statements about unimplemented features as though they are live. Revise both language sections after auditing the app.

## Publish via GitHub Pages

1. Log into the correct GitHub account **ebubekir43**.
2. Create a **public** repository named `arrow-resolve-legal` (or another name if preferred).
3. Upload the five HTML/CSS files to the default branch root.
4. Repository **Settings → Pages → Deploy from a branch → main → /(root) → Save**.
5. Verify live URLs. The following are **EXPECTED URL PATTERNS ONLY, NOT VERIFIED LIVE**:
   - `https://ebubekir43.github.io/arrow-resolve-legal/privacy.html`
   - `https://ebubekir43.github.io/arrow-resolve-legal/terms.html`
   - `https://ebubekir43.github.io/arrow-resolve-legal/delete-account.html`
6. Put privacy URL in Play Console privacy policy field and in-app Settings; delete-account URL in the Play Console account deletion field and in-app Settings. Add Terms URL to Settings.
7. Open the public pages from a logged-out browser and on Android.

## Supabase native Google sign-in prerequisites

1. New Supabase Free project → Project URL + publishable/anon key (never `service_role` in Flutter).
2. Google Cloud Auth Platform consent screen (app name, support email and legal-site URLs, audience and test users as needed).
3. OAuth client **Web** plus OAuth client **Android**, with actual Android applicationId + correct SHA-1 fingerprints for debug and Play App Signing.
4. Supabase Dashboard → Authentication → Providers → Google, configure accepted client IDs (consult current official documentation).
5. Flutter: `supabase_flutter` + native `google_sign_in` as documented for installed versions; authenticate by securely exchanging the Google ID token with Supabase Auth, or use the supported OAuth deep-link flow. Avoid inventing client IDs/redirect URLs.
6. Configure per-user row-level security (RLS); keep local-first game saves; merge account cloud progress non-destructively.
7. Hints and ad-removal entitlements must not be freely client-editable; protect through server-validated operations and Google Play purchase verification.
8. Add accessible account deletion in Settings and secured backend account+associated-data deletion; test separately from signing out.
9. Test first install, login cancellation, sign-out, offline play, two Android devices, save merge, deletion, and purchase restore.

## Extra Play Console work

Complete app content declarations (Data safety, Ads, target audience, content rating, app access and others applicable); app listing text/screenshots, support email, signed release AAB, testers/release process, and purchase configuration. Never upload demo/test AdMob IDs as final production IDs.

No passwords, OAuth client secrets or Supabase service role keys belong in this public repository.
