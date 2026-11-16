# SSC PrepX Style Learning Portal

A mobile-first learning app + admin panel (similar to redesigned-fiesta-ryus.vercel.app).

Uses **Firebase Realtime Database** for courses, lectures, settings, and user stats.

## Features

- Student side: Unlock courses, browse subjects → chapters → lectures/notes, favourites, downloads
- Video support (including HLS/.m3u8 via hls.js)
- Admin panel (password protected) to manage courses, subjects, chapters, lectures, broadcast messages, etc.
- Device-based "login" (no phone/password required for students)
- Local caching for offline-ish experience

## Tech Stack

- Pure HTML + CSS + Vanilla JS (single page)
- Firebase Realtime Database (compat SDK)
- HLS.js for adaptive video

## Setup

1. Clone this repo
2. The Firebase config is already set to:
   ```
   https://dora-dora-2e0e6-default-rtdb.asia-southeast1.firebasedatabase.app
   ```
3. Open `index.html` locally or deploy (see below)

### Important: Firebase Security Rules

Your Realtime Database must have rules that allow the app to work.  
**Do not leave rules completely open in production.**

Example (adjust according to your needs):

```json
{
  "rules": {
    "courses": {
      ".read": true,
      ".write": true
    },
    "settings": {
      ".read": true,
      ".write": true
    },
    "users": {
      ".read": true,
      ".write": true
    },
    "installations": {
      ".read": true,
      ".write": true
    },
    ".read": false,
    ".write": false
  }
}
```

Better approach: protect admin writes with a secret or move admin to a separate authenticated flow.

## Deploy on Vercel (recommended)

1. Push this folder to a **GitHub** repository
2. Go to [vercel.com](https://vercel.com) → New Project → Import the GitHub repo
3. Framework Preset: **Other**
4. Root Directory: leave blank (or set to the folder containing index.html)
5. Deploy

Vercel will serve `index.html` as the homepage automatically.

## Deploy on Netlify / GitHub Pages

Also works — just drag & drop the folder or connect the GitHub repo.

## Customization

- Change branding: search for "SSC PrepX", logo text, colors (`#7c5cff`, red accents)
- Admin password: search for the admin password gate logic in `index.html`
- Telegram / WhatsApp links: look for `BRAND_TELEGRAM_LINK` and `BRAND_WHATSAPP_LINK`

## Legal Note

The original site contains educational content. Only upload / link content that you have rights to distribute. Respect copyrights of educators and coaching institutes.

## Local Development

Just open `index.html` in a browser, or use a simple static server:

```bash
npx serve .
# or
python -m http.server 3000
```

---

Made for easy GitHub + Vercel deployment with your Firebase.
