BrightDay Version 8 — Family Sync (Firebase Spark)
=================================================
No Node.js required. No OpenAI API or AI image cost.

BEFORE UPDATE: In BrightDay V7 on your original Windows PC, go to Parent Mode -> Save backup, and keep that JSON backup safely.

1. Keep the Firebase project on the Spark (no-cost) plan. Do not enable billing.
2. Go to https://console.firebase.google.com/ and create a project (example: brightday-family).
3. In Project Overview -> add a Web app (</> icon). Register it. Copy the public firebaseConfig object. Do not copy any service-account credentials.
4. Build -> Authentication -> Sign-in method -> Email/Password -> Enable.
5. Authentication -> Settings -> Authorized domains -> add cagdaskaval-blip.github.io if it is not already listed.
6. Build -> Firestore Database -> Create database -> choose a suitable region -> use Production mode. Use the default database.
7. Firestore Database -> Rules -> REPLACE the rules with ALL the contents of firestore.rules in this ZIP and Publish. Never leave test-mode public access enabled.
8. In GitHub repo cagdaskaval-blip/brightday upload the contents of this ZIP EXCEPT README-FIRST.txt and firestore.rules. Replace existing index.html, sw.js, manifest.webmanifest and icons as needed, add family-sync.js in the same ROOT folder as index.html. Commit the changes.
9. Wait for GitHub Pages to redeploy, then reload https://cagdaskaval-blip.github.io/brightday/ (you may need a hard refresh because of old service worker cache).
10. Open Family Sync -> paste Firebase web config JSON -> Save -> create your account using email/password -> Create my family. This is your parent account.
11. Click Upload my current offline tasks & stars ONCE, from the device with the correct data. Confirm shared tasks are present on the calendar. Alternatively restore backup through Parent Mode when cloud sync is connected, taking care that restore imports data into the shared family.
12. Your wife opens the same BrightDay URL on her phone, pastes the SAME web config, creates her OWN Firebase email/password account, chooses Join, pastes your family code, asks to join as Parent. You approve under Family Sync -> Pending requests.
13. Your son should use a separate email/password Firebase account (managed by a parent, with age and account policies respected). Sign in from tablet; ask to join as Child; parent approves. A TV box can use that same child account, or a dedicated Child account approved separately.
14. Try adding a task from one parent's phone; watch it appear on another signed-in device; then mark it complete on the child's tablet, and check stars on parents' phones and TV.

HOW IT WORKS
- The public GitHub site stores only the app CODE. Private tasks live in Firestore and are protected by security rules based on authenticated account membership.
- Parent accounts create/edit/delete tasks; child accounts can view activities and record/undo completions. The existing local PIN is for local parent-mode convenience, not your actual Firebase password.
- Individual task and completion records sync rather than overwriting the whole family data on every update.
- Your original local data and downloaded backup remain available. Remote data is authoritative once you're connected to a family.
- New device offline state and sign-in can require internet. Speech playback relies on installed voices.
- On Android TV, browser navigation support depends on the box model. Avoid leaving a parent's signed-in session on the TV.
- Cloud Firestore free quotas are limited; Spark plan avoids billing but may stop serving requests if a quota is exhausted.

IMPORTANT LIMITATIONS
- No automatic account-recovery or full admin management screen yet; approved members cannot be removed from the BrightDay UI (use Firebase console or later version).
- Offline changes made while disconnected may conflict with updates from other devices. For best results, make changes while online, and take regular backups.
- Picture files embedded in Firestore task records must fit Firestore's document size limit. Prefer built-in cartoons or small images.
- This is a prototype; JavaScript syntax/ZIP checks are possible without a Firebase project, but live multi-device sync and rules need hands-on testing after Firebase setup.
- Never upload private backup JSON, child account credentials, or service-account files to your public GitHub repository.
