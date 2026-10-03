---
description: Write the Meta App Review submission (permissions, screencast script, reviewer notes) from this app's code
---

Prepare a Meta App Review submission for this project using the app-review skill.

1. Search the code for every Meta Graph API call and login scope. List each permission with the file and line where it is used.
2. Flag any permission that is requested but never used, and any used but not requested. Recommend removing the unused ones before submitting.
3. For each permission that stays, write:
   - the use description for the review form, in plain language from the user's side
   - the steps the reviewer follows to see it working
4. Write one screen recording script that starts logged out and shows every permission being granted and then used, in the order a real user would meet them.
5. List the settings that must be ready before submitting: privacy policy URL, data deletion URL or callback, business verification if needed, app mode, test login.
6. Check the current requirements at https://developers.facebook.com/docs/app-review before finishing, and note anything that changed.

Save it to `app-review/meta-submission.md` unless I name another path, then summarise what I still need to do by hand.
