# ADPHC Community Health Experience Passport

A standalone, single-page mobile web app for the ADPHC Community Health Sector Showcase: participants register with their name, tap through department "passport" pages, and type a short code at each activity station to collect a stamp, unlocking a gift once they reach the required number of stamps. Admin and Staff Desk views are built in and protected by access codes.

Activity stamps are collected by typing a code — there is no camera scanner or QR code for activities. The entrance/registration QR code now encodes a published address you confirm once in Admin (see step 2 below), rather than guessing it from whatever page happens to be open.

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

## 2. Find your published link, then set up the registration QR code

Still on **Settings → Pages**, once publishing finishes GitHub shows: "Your site is live at `https://<your-username>.github.io/<repository-name>/`". That is the one address participants, staff, and admin should all use.

The registration QR code is no longer generated automatically from whatever address happens to be open in your browser — you confirm it once, and it's remembered on that device. This avoids accidentally printing a QR code that points at a local file, a preview link, or an old address.

1. **Enter or confirm the public registration URL.** Sign in to **Admin** (`#/admin`, admin access code required) → **QR Codes** tab. There's a field labeled "Public registration website address," pre-filled with a guess — replace it with the exact address GitHub showed you above, then tap **Confirm address & update QR**. You only need to do this again if the site is ever redeployed to a different address.
2. **Download the registration QR code PNG.** Under the QR code itself, tap **Download high-resolution PNG for printing**. It saves as `adphc-registration-qr-print.png` — a plain black-on-white code with generous white space on all sides and no logo or text over the pattern, sized for print, not just screen viewing.
3. **Test it by scanning it with a phone camera.** Open the downloaded PNG (or the on-screen QR code) and scan it with an ordinary phone camera app, not this app's own browser.
4. **Confirm it opens the registration page for a new participant.** The scan should open your published site's entrance screen, ready to register — not a local file, not a Claude preview link, and not an activity stamp page. If it opens anything else, the address confirmed in step 1 is wrong — fix it there and re-download.

This same confirmed address is also what the "ENTRANCE / REGISTRATION" QR code on the Staff Desk screen encodes, so it stays consistent with what's printed. Activity codes are unaffected by any of this — there is still no QR code for activities, and none of this creates one.

## 3. Activity codes — give these to staff at each station

Every activity is collected by typing its code on that activity's page. No QR code, no camera, no scanning — just a text field and a Submit button, right on the passport page.

| Activity | Department | Code |
|---|---|---|
| Tips to Maintain Healthy Blood Glucose Levels | NCDs Prevention and Control | `DIABET` |
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

Whenever you replace `index.html` (or the logo) in the repository, GitHub Pages republishes automatically within a minute or two — no other steps needed. The confirmed registration address (see step 2) is remembered per device and doesn't need re-entering after a routine update — only if you move to a genuinely different address. Activity codes don't need reprinting after a routine update either; they only change if you edit the code list yourself.

## 7. Preview the stamp animation privately (your own device only)

If your laptop or phone already has stamps saved from testing and you want to see the live stamping animation again without losing that progress, there's a private preview tool for exactly this — it's never shown anywhere a participant can see it, only inside the admin area.

1. On the device with your saved passport, sign in to **Admin** (`#/admin`, admin access code required).
2. Open the **Preview Stamp** tab in the left-hand menu.
3. It shows which passport is currently signed in on that device. Choose any activity from the dropdown — including one you've already collected — and tap **Play live stamp animation**.
4. You're taken straight to that activity's real passport page and the full live stamping animation plays exactly as a participant would see it. Once it finishes, a toast confirms nothing was saved.

This never changes your registration, stamps, stamp count, or gift status — even when you preview an activity you've already collected, your real saved data is exactly what's shown once the animation finishes. If no passport is signed in on that device yet, register or resume one first, then come back to this tab.
