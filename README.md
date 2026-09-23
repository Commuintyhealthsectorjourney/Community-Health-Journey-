# ADPHC Community Health Experience Passport

A standalone, single-page mobile web app for the ADPHC Community Health Sector Showcase: participants register with their name, tap through department "passport" pages, and type a short code at each activity station to collect a stamp, unlocking a gift once they reach the required number of stamps. Admin and Staff Desk views are built in and protected by access codes.

Activity stamps are collected by typing a code — there is no camera scanner or QR code for activities. The entrance/registration QR code is unchanged and still works exactly as before.

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

**Always use that exact address.** The entrance QR code is generated live from whatever web address is open in the browser at the moment you view or print it. If you generate it from a different link — an old deploy, a local file, a preview URL — the printed code will point to the wrong place and stop working. If you ever change the repository name or move to a custom domain, the published address changes too, and the entrance QR must be reprinted from the new address.

## 3. Activity codes — give these to staff at each station

Every activity is collected by typing its code on that activity's page. No QR code, no camera, no scanning — just a text field and a Submit button, right on the passport page.

| Activity | Department | Code |
|---|---|---|
| Diabetes Prevention Interactive Game | NCDs Prevention and Control | `DIABET` |
| Spirometry Testing | NCDs Prevention and Control | `SPIRO` |
| Muscle Strength Testing | NCDs Surveillance and Screenings | `MUSCLE` |
| Nutrition Interactive Game | Health Behavior Promotion | `NUTRI` |
| Physio + Ergonomics Booth | Occupational Safety and Health | `PHYSIO` |

Codes are accepted in any mix of upper/lowercase and ignore accidental leading or trailing spaces — a participant typing `spiro `, `Spiro`, or `SPIRO` all work the same.

**This table is also visible inside the app** at Staff Desk → "Entrance QR & activity codes" (staff access code required) and at Admin → "QR & activity codes" (admin access code required), in case a code ever needs to be changed or looked up without opening this file.

**Security note:** because this repository is public, anyone who opens `index.html` can find these same codes in the source (search for `ACTIVITY_SHORT_CODE`), and this README now lists them directly too. That's an acceptable tradeoff for short, easy-to-say words handed out verbally at a staffed station, but if you'd rather keep them out of a public README, delete the table above before publishing this file, and give codes to staff by another channel instead — the app itself still shows the same table to anyone signed in as staff or admin.

## 4. Test the full flow before the event

Do this on the real published link, not a local copy.

1. On your phone, open the published link and register with a test name.
2. Open a department, and on an activity's empty stamp circle, type its code from the table above into the field and tap **Submit code** (or just press Enter).
3. Confirm the stamp appears immediately on that same activity page with the ink-stamp animation — you should not be redirected anywhere else, and the activity now shows as collected.
4. Try the same code again. It should say the stamp is already collected and must not add a second stamp. Try a wrong code on a different activity — it should show an inline error and add nothing.
5. Repeat for two more activities to confirm the gift pop-up appears once you reach the required number of stamps.
6. Sign in to Staff Desk and Admin to confirm the activity code table displays there too, and that the entrance QR still shows and downloads correctly.

## 5. Security note for the access codes

The Admin and Staff Desk access codes are placeholder values set in the source code (search for `ADMIN_PASSCODE` and `STAFF_PASSCODE` near the top) — change these to your own before the real event, since anyone can view them in this public repository. If your repository can be set to private instead of public, that removes this exposure entirely; GitHub Pages works the same way from a private repo on paid plans, or you can keep the repo private and publish through another static host.

## 6. Updating the site later

Whenever you replace `index.html` (or the logo) in the repository, GitHub Pages republishes automatically within a minute or two — no other steps needed. After any update, reopen the entrance QR on the live published link and reprint it if it changed — a QR code printed before an update can point to an old address and stop working. Activity codes don't need reprinting after a routine update; they only change if you edit the code list yourself.
