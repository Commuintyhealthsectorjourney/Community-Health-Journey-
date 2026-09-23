# ADPHC Community Health Experience Passport

A standalone, single-page mobile web app for the ADPHC Community Health Sector Showcase: participants register with their name, tap through department "passport" pages, scan or manually enter a code at each activity station to collect a stamp, and unlock a gift once they reach the required number of stamps. Admin and Staff Desk views are built in and protected by access codes.

## What's in this folder

- `index.html` — the entire application (HTML, CSS, and JavaScript in one file). This is the only file you ever need to edit or replace.
- `adphc-logo.jpg` — the ADPHC logo used throughout the app.
- `README.md` — this file.

No build step, no server-side code, no installation. It runs entirely in the participant's own browser.

## 1. Publish on GitHub Pages

1. Create a GitHub repository (or open your existing one for this project).
2. Add `index.html` and `adphc-logo.jpg` to the root of the repository — if you're updating an existing repo, replace the old versions of these two files with the ones in this ZIP.
3. In the repository, go to **Settings → Pages**.
4. Under "Build and deployment," set **Source** to "Deploy from a branch," choose your default branch (usually `main`), and folder `/ (root)`. Save.
5. GitHub publishes the site automatically — this usually takes one to two minutes, sometimes longer on the first publish.

## 2. Find your published link

Still on **Settings → Pages**, once publishing finishes GitHub shows: "Your site is live at `https://<your-username>.github.io/<repository-name>/`". That is the one address participants, staff, and admin should all use.

**Always use that exact address.** Every QR code inside the app (entrance, each activity, Admin dashboard, Staff Desk) is generated live from whatever web address is open in the browser at the moment you view or print it. If you generate QR codes from a different link — an old deploy, a local file, a preview URL — those printed codes will point to the wrong place and stop working. If you ever change the repository name or move to a custom domain, the published address changes too, and every QR code must be reprinted from the new address.

## 3. Test one activity QR and its manual backup code before printing everything

Do this on the real published link, not a local copy, since camera scanning requires a secure (HTTPS) address.

1. On your own phone, open the published link and register with a test name.
2. On a second device (or a private/incognito tab), open the same link, scroll to the bottom of the home screen and open **Staff Desk**, then sign in with the staff access code. (The default access codes are placeholders set in the source code — see the security note below before the real event.)
3. From the Staff Desk, tap **QR codes**. This screen lists every activity with its QR code and its short manual code side by side, plus a **Print staff reference sheet** button — this is the one printout meant for staff only.
4. Back on your first (participant) phone: open a department, tap an activity's empty stamp circle. Either scan that activity's QR with the in-app camera scanner, or tap **Enter activity code** and type the matching code from the staff screen.
5. Confirm the stamp appears immediately on that same activity page with the ink-stamp animation — you should not be redirected anywhere else.
6. Try entering that same code again (or rescanning). It should say the stamp is already collected and must not add a second stamp.
7. Once that one activity works end to end, print the rest:
   - **Admin → QR Codes** — the public station posters (QR only, no manual codes) to place at each activity table.
   - **Staff Desk → QR Codes → Print staff reference sheet** — your internal staff copy with every activity's QR and manual code together. Keep this one with staff only; never post it publicly.

## 4. Security note for a public GitHub repository

Anyone can view this project's source code on GitHub, including:

- The Admin and Staff Desk access codes (search the script for `ADMIN_PASSCODE` and `STAFF_PASSCODE` near the top).
- The formula used to generate each activity's manual backup code — meaning someone who reads the source could work out every code themselves.

This is fine for building and testing, but before the real event:

- Change `ADMIN_PASSCODE` and `STAFF_PASSCODE` to your own values.
- Keep the printed staff reference sheet physically with staff only — treat it the same as you would a password sheet, not something to photograph and share in a group chat.
- If your repository can be set to private instead of public, that removes this exposure entirely; GitHub Pages works the same way from a private repo on paid plans, or you can keep the repo private and publish through another static host.

## 5. Updating the site later

Whenever you replace `index.html` (or the logo) in the repository, GitHub Pages republishes automatically within a minute or two — no other steps needed. After any update, reopen the Staff Desk and Admin QR screens on the live published link and reprint every QR code from there. A QR code printed before an update can point to an old address and stop working, even if the update itself didn't change anything about that activity.
