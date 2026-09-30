---
name: app-review
description: Prepare an app for platform review and write the submission text from the code itself. Covers Meta App Review (Facebook, Instagram, WhatsApp permissions), TikTok for Developers app review, and Google Play Console (data safety, account deletion, app access, closed testing, sensitive permissions). Use whenever someone is submitting or resubmitting for review, was rejected and needs to fix it, needs permission justifications, a screen recording script, reviewer test instructions, or data safety answers, or asks which permissions they actually need.
---

# Getting through app review the first time

Reviewers are not trying to reject you. They have a few minutes, a checklist, and no idea what your app does. Almost every rejection comes down to one of three things: asking for a permission the reviewer cannot see being used, a recording that skips a step, or a reviewer who could not get in.

This skill writes the submission from the code, so every claim is something the app really does.

## The method, for every platform

1. **Read the code before writing anything.** List every permission, scope or sensitive API the app actually calls, with the file where each is used. This list is the truth; the developer's memory is not.
2. **Cut what is not used.** Every extra permission is a reason to reject. If something is requested but never called, recommend removing it before submitting.
3. **One story per permission:** who the user is, what they tap, what the app does with the permission, and what the user sees as a result. Plain language, no marketing.
4. **Write the recording script** step by step, starting logged out, so it shows each permission being granted and then used.
5. **Write the reviewer instructions:** how to get in, test account details (as placeholders, never real passwords in files), and exactly where each feature is.
6. **Check the current rules before finalising.** Platforms change their forms often. Fetch the official page linked below and adjust if anything has moved.

Save the result as a markdown file the developer can copy from (default `app-review/<platform>-submission.md`). Tell them to keep it out of a public repository if it will ever contain real test credentials.

## Meta (Facebook, Instagram, WhatsApp)

Official guide: https://developers.facebook.com/docs/app-review

- **Only request what the recording shows.** Each permission needs its own use description and must appear in the screen recording.
- **The recording** must start logged out, show the full login, show the user granting the permission in Meta's dialog, then show the feature that uses it. Use English for the app's interface where possible, or add captions. Explain any button whose meaning is not obvious. Record at 1080p or better.
- **Descriptions** say what the user does and gets, not what the API does. "A shop owner connects their Page so customers who comment 'price' get the price by private message" beats "we use pages_messaging to send messages".
- **Reviewer access:** give a working test login, or clear steps for creating one. A reviewer who cannot sign in rejects.
- **Business verification** is required for some permissions and for Advanced Access. Check it is done before submitting.
- **Required settings:** privacy policy URL, a data deletion URL or callback, app icon, category. All URLs must load for a logged-out visitor.
- **Webhooks:** apps only receive webhooks for people without a role on the app once the app is Live. If testing works for you but not for a real user, check the app mode first.
- **Instagram has two different APIs.** Instagram Login (permissions start `instagram_business_`) needs no Facebook Page. Facebook Login (Page-based, `instagram_manage_*` and `pages_*`) does. Make sure the requested permissions match the login the code uses.

## TikTok for Developers

Official guide: https://developers.tiktok.com/docs/en/app-review-guidelines

- **Demo video:** at least one, up to five, 50 MB each. It must show the complete flow for every product and scope selected. Anything not shown should be removed from the request.
- **Finished app only.** Beta, test or incomplete versions are generally not approved.
- **Policy pages** (privacy policy and terms) must load and must describe what the app does with TikTok data.
- **Publishing content:** the user must see and approve the caption, privacy level and interaction settings before anything is posted. A one-tap publish with no review screen fails.
- Complete any URL or domain verification the portal asks for before submitting.

## Google Play

Official policy centre: https://support.google.com/googleplay/android-developer

- **Closed testing (personal accounts):** a personal developer account created on or after 13 November 2023 must run a closed test with at least 12 testers, opted in for 14 continuous days, before applying for production. Organisation accounts are exempt. Google also checks the testers really used the app.
- **Account deletion:** if the app lets people create an account, it must offer deletion inside the app and a web page where people can request deletion without reinstalling. The web link goes in the Data safety form. Deactivating is not deleting.
- **Data safety form:** must match what the app and every SDK in it actually collect and share. Read the dependencies, not just your own code: analytics, crash reporting, ads and payment SDKs all collect data.
- **App access:** if anything is behind a login, give reviewers working credentials and steps in App content, App access.
- **Sensitive permissions** (SMS, call log, all files access, background location, installed apps list, accessibility, exact alarms) need a declaration and a real core use. If the manifest has one the app does not need, remove it.
- **Target API level:** new apps and updates must target a recent Android version. Check the current requirement in Play Console before building.
- **Privacy policy URL** is required and must load.

## After a rejection

Read the rejection word for word and map each point to one fix. Reply to the reviewer with what changed and where to see it. Resubmitting the same thing with a longer explanation almost never works; a new recording that shows the missing step almost always does.
