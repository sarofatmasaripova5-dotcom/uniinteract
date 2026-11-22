# UniInteract Pro V3 — real-time pilot

## What is included
Responsive teacher/student web interface; 6-digit session codes; Firestore real-time listeners; 4 working activities (multiple-choice quiz, brainstorming, formula free response, case free response); quiz feedback; live teacher responses; CSV export.

## Setup
1. Create a Firebase project at https://console.firebase.google.com/ .
2. Add a Web app in Project Settings and copy the firebaseConfig values into `firebase-config.js`.
3. Authentication → Sign-in method → enable **Anonymous**.
4. Firestore Database → create database, then Rules → paste `firestore.rules` and Publish. Choose an appropriate database region and retention policy.
5. Host both `index.html` and `firebase-config.js` via HTTPS (Firebase Hosting, GitHub Pages, or another static host). For local testing use a local HTTP server; do not open via file://.
6. Open site on teacher device and create a class. Open same URL on student device, enter name and class code.

## Important limitations
This is a pilot, **not production-ready**. Anonymous identity is not verified, so a student can choose any name. A 6-digit code is not strong access control. Current quiz scoring is calculated in the browser and is **not tamper-resistant**. Students may be able to read the quiz answer key in the session document, and can submit arbitrary `correct` values: do not use these grades for official assessments. Move answer keys and grading to a trusted backend (Cloud Functions) before production use. Open-ended answers are teacher-reviewed manually; a grade-entry interface is not yet implemented. The 13-method catalog from the earlier prototype is not all implemented here. Session data persists in Firestore until removed administratively. Set up privacy notices, access policies, abuse prevention, monitoring, backup, and data deletion before public launch. No load test or live deployment has been completed.

## Security caution
Do not publish student personal data during this prototype. Anonymous sign-in and public session-code access are suitable only for controlled demonstrations. Firestore security rules should be reviewed and tested in Firebase Emulator Suite before use with real students.
