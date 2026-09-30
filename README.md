# app-review

A Claude Code plugin that writes your Meta, TikTok and Google Play review submissions from your code.

I have been through Meta App Review, TikTok's app review and Google Play review for my own products. Each rejection taught me the same lesson: reviewers only approve what they can see. Ask for a permission your recording does not show and you are rejected. Skip one step in the video and you are rejected. Leave the reviewer unable to log in and you are rejected. This plugin reads what your app actually does and writes the submission around it.

## What it does

- Lists every permission or scope your code really uses, with the file it is used in, and flags the ones you request but never use.
- Writes the use description for each permission in plain language, from the user's side.
- Writes the screen recording or demo video script, starting logged out, so every permission is granted and then used on camera.
- Writes the reviewer instructions and the checklist of settings that must be ready first.
- For Google Play, drafts the Data safety answers from your code and dependencies, and checks account deletion, app access, sensitive permissions and the closed testing rule.

## Install

```
/plugin marketplace add degordonstech/app-review
/plugin install app-review@app-review
```

## Using it

- `/app-review:meta` for Facebook, Instagram and WhatsApp permissions.
- `/app-review:tiktok` for TikTok for Developers products and scopes.
- `/app-review:play` for the Google Play Console forms.

Each one saves its draft to `app-review/<platform>-submission.md` in your project. That folder is in this plugin's own `.gitignore` for a reason: if you ever paste real test logins into it, add it to your project's `.gitignore` too.

The skill also switches on by itself when you mention a review, a rejection or a permission you are unsure about. It checks each platform's current guidelines before finishing, because the forms change.

## License

MIT
