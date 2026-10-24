# PAAR Systems app — app.paarsystems.com

This folder is a small "app shell": your logo, an app icon and a loading screen, wrapped
around the staffing tool you already run in Google Apps Script. Your data stays exactly
where it is (the Google Sheet). Nothing to migrate.

About 20 minutes, once.

---

## 1. Put your tool's link in `config.js`

1. Open the Apps Script editor → **Deploy → Manage deployments**.
2. Copy the **Web app** URL (ends in `/exec`).
3. Check **Who has access** says **Anyone**. (Your passcodes still protect it. If it says
   "Anyone with a Google account" or "only paarsystems.com", Google's sign-in page refuses
   to open inside the app and you'll see a blank screen.)
4. Open `config.js` in Notepad and paste the link between the quotes:

   ```js
   window.PAAR_APP_URL = 'https://script.google.com/macros/s/AKfy..../exec';
   ```

> From now on, always update the tool with **Manage deployments → ✎ Edit → Version: New version**.
> That keeps the same link. A "New deployment" creates a new link and the app would need updating.

## 2. Put it online (free) — Netlify

1. Go to **app.netlify.com/drop** and sign up (free; "Sign up with email" is fine).
2. Drag the whole **paar-app** folder onto the page.
3. In a few seconds you get an address like `https://wonderful-name-123.netlify.app`.
   Open it — you should see the PAAR logo, then your login screen.
4. **Site configuration → Change site name** → e.g. `paar-systems` (→ `paar-systems.netlify.app`).

To update later (new logo, new link): **Deploys → drag the folder again**.

## 3. Use your own address: app.paarsystems.com

1. In Netlify: **Domain management → Add a domain** → type `app.paarsystems.com` → Verify → Add.
2. Netlify shows a record to add. Log in where paarsystems.com's DNS is managed
   (GoDaddy, Crazy Domains, VentraIP, Google Workspace/Squarespace, Cloudflare …) and add:

   | Type  | Name / Host | Value / Points to             |
   |-------|-------------|-------------------------------|
   | CNAME | `app`       | `paar-systems.netlify.app`    |

   (Use your own Netlify site name in the Value.) Leave your website and email records alone —
   this only adds the `app.` sub-address.
3. Back in Netlify, wait for **HTTPS → certificate provisioned** (minutes to a few hours).

Open **https://app.paarsystems.com**.

## 4. Install it

| Device | How |
|---|---|
| **iPhone / iPad** | Safari → app.paarsystems.com → Share → **Add to Home Screen** |
| **Android** | Chrome → app.paarsystems.com → **Install app** (or ⋮ → Add to Home screen) |
| **Windows / Mac** | Chrome or Edge → app.paarsystems.com → install icon in the address bar (⊕) |

It opens full-screen with the PAAR icon, like any other app. Send your recruiters the same
address and the team passcode.

---

### Good to know

- **Updates to the tool** (new Code.gs / Index.html) appear in the app automatically — no need
  to touch this folder.
- **Offline**: the app opens and says "You're offline"; it needs internet because the data is in Google.
- **Downloads and links** (PDF offers, Drive files, Gmail drafts, CSV exports) open in a new tab
  as before.
- **iPhone note**: if a file download does nothing inside the installed app, open
  app.paarsystems.com in Safari itself for that download.
- **Google banner**: if the account running the script isn't a Google Workspace account, Google
  shows a thin "created by a Google Apps Script user" bar at the top. Deploying from your
  paarsystems.com Workspace account avoids it.
- **Sharper icon**: the icon is cut from your logo file. Send a high-resolution (or SVG) logo and the
  icons in `icons/` can be regenerated crisper.

### Prefer another free host?
The folder is plain files and works anywhere: **Firebase Hosting**, **GitHub Pages**,
**Cloudflare Pages**. Netlify is just the easiest drag-and-drop.
