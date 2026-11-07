# MC Wilber website

Single-file site (`index.html`) hosted on Firebase, source on GitHub.

## Set up
1. Edit the `SITE` block at the top of the script in `index.html` (email, WhatsApp, socials, services, reviews, videos).
2. Firebase console: create a project, add a Web app, enable **Firestore**, and paste the config into `FIREBASE` in `index.html`.
3. Replace `YOUR-FIREBASE-PROJECT-ID` in `.firebaserc` and `.github/workflows/deploy.yml`.

## Deploy by hand
```
npm i -g firebase-tools
firebase login
firebase deploy
```

## Deploy from GitHub
Run `firebase init hosting:github` once, or add a `FIREBASE_SERVICE_ACCOUNT` secret. Every push to `main` then goes live.

## Managing content (Firebase console > Firestore)
- `events`: docs with `title`, `date` (YYYY-MM-DD), `place`. Shows in Upcoming events.
- `busyDates`: doc ID = a date (e.g. `2026-12-05`). That date shows as booked in the form.
- `subscribers`: newsletter emails.
- `bookings`: new requests land here. Only you can read them, in the console.
