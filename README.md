# YIHUI Team Calibration

GitHub Pages frontend for the YIHUI Team Calibration management app, connected to Firebase project `q-team-cali`.

## GitHub Pages
In repository Settings → Pages → Build and deployment select **Deploy from a branch**, branch **main**, folder **/(root)**.
Site: https://yhcoffee.github.io/q-team-cali/

## Required Firebase setup (admin only)
1. [Firebase Console](https://console.firebase.google.com/project/q-team-cali/overview): Authentication → Sign-in method → enable **Email/Password**.
2. Authentication → Users: create each manager's account; copy the UID.
3. Firestore Database: create a Firestore database, then paste **firestore.rules** into Firestore → Rules and publish. Committing rules here does **not** apply them to Firebase.
4. Firestore → Data: create `authorizedManagers` collection and a document for each manager, document ID = their Firebase Auth UID, field `active` (boolean) = `true`.
5. Authentication → Settings → Authorized domains: add `yhcoffee.github.io` (hostname only).

## Migrating old assessments
Export JSON from the local v16 app using the same browser where your prior data is saved. After the hosted app authenticates successfully, import that JSON once. Import **replaces** the shared dataset. Keep a private backup; do not commit real staff assessment data to GitHub.

## Privacy
GitHub Pages serves frontend code publicly; Firestore permissions must protect employee data. Do not place private employee data or admin service-account keys in this repo. Firebase web API keys in frontend config are public identifiers, not privileged credentials. The shared dataset is stored in one Firestore document; managers should avoid concurrent editing because the latest save can overwrite another's changes.
