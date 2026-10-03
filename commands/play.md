---
description: Prepare the Google Play Console answers (data safety, app access, account deletion, closed testing) from this app's code
---

Prepare this project for Google Play review using the app-review skill.

1. Read the Android manifest (or the web app manifest and TWA config for a wrapped web app) and list every permission, flagging sensitive ones and any the app does not need.
2. Read the dependencies as well as the app's own code, and draft the Data safety answers: what is collected, whether it is shared, why, whether it is encrypted in transit, and whether users can ask for deletion.
3. Check account deletion: if users can create an account, confirm there is an in-app way to delete it and a web page to request deletion. If either is missing, say so plainly, because it blocks review.
4. Write the App access instructions for reviewers, with placeholder credentials.
5. Tell me whether the closed testing rule applies (personal account created on or after 13 November 2023: 12 testers for 14 days) and what the current target API level requirement is, checked against Play Console Help.

Save it to `app-review/play-submission.md` unless I name another path, then summarise what I still need to do by hand.
