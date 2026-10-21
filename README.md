# Dr. Samavia – Clinical Psychologist

GitHub-ready source for one responsive client/admin booking website. **This is not live until Firebase is configured and deployed.**

## Client
Direct access without a visible login/OTP; background Firebase anonymous identity. Online/physical booking requests, Easypaisa/Meezan details, receipt upload, own booking status, admin-confirmed appointment time, on-page real-time status updates and optional browser notifications while the page is open.

## Admin
Firebase email/password login restricted to a single UID in both Firestore and Storage rules. See booking requests and receipt, verify payment, confirm/decline, assign date/time (Pakistan local time), and add note.

## Upload from a phone to GitHub
Create a new repository. Extract this ZIP first. In GitHub choose **Add file > Upload files** and select all extracted files, keeping them at the repository root (not inside an extra folder). Commit changes. GitHub does not automatically make the app live.

## Next: Firebase setup
1. Create Firebase project, register Web app and paste its web config in `firebase-config.js`.
2. Enable Authentication: Anonymous and Email/Password. Create admin email/password in Firebase Console. Copy the admin user's UID into `ADMIN_UID` in `firebase-config.js` and replace `REPLACE_WITH_ADMIN_UID` in **both** rules files. Never commit an admin password.
3. Create Firestore database and Cloud Storage bucket (billing may be required). Publish the included Firestore and Storage rules.
4. Deploy using Firebase CLI: `npm install -g firebase-tools`, `firebase login`, `firebase use --add`, `firebase deploy --only hosting,firestore:rules,storage` from the folder containing these files. The included `firebase.json` already points to the correct files.
5. Test client receipt upload, admin login and confirmation, and client status from separate browsers. Use HTTPS. Configure Firebase Auth authorized domains. Add a privacy policy and abuse protection before public launch.

**Limitations:** Browser notifications require permission and an open page; background push notifications are NOT implemented. Payment verification is manual, not linked to bank APIs. Anonymous client history may be lost when browser storage is cleared or device changes. Do not advertise as production-ready before configuring Firebase and testing access rules.
