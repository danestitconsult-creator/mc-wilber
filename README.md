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

## Manager dashboard (`/admin.html`)
Open `yourdomain/admin.html` (also linked in the site footer) and sign in with Google.
- **Bookings:** filter, set status, "Confirm and block date", email or WhatsApp the client, delete, export CSV.
- **Events:** add or remove public shows.
- **Blocked dates:** block or unblock days on the site calendar.
- **Subscribers:** view and export newsletter emails.

One-time setup: Firebase console > Authentication > Sign-in method > enable **Google**. Then publish `firestore.rules`.
To add a manager, add their Google email to the list in `isAdmin()` in `firestore.rules` and republish.
If the site is on a custom domain, add it under Authentication > Settings > Authorized domains.
