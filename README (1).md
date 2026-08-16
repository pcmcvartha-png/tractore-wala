# 🚜 Tractor Wala — ट्रॅक्टर वाला

**Khet-Khaloihan & Highway Nostalgia Beats**

A cinematic, single-file Indian tractor & highway music radio. Fullscreen background, glass-morphism UI, working sound effects, a real YouTube-powered music player, and an optional real-time "passengers on highway" counter.

Everything — HTML, CSS, JavaScript, and the background image — lives in **one file**: `index.html`. No build step, no `npm install`, no assets folder. Upload it anywhere and it runs.

---

## 🚀 Deploy on GitHub Pages (2 minutes)

1. Create a new GitHub repository (e.g. `tractor-wala`).
2. Upload `index.html` to the root of the repo (drag-and-drop on github.com works fine, or `git push`).
3. Go to **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then **Save**.
5. Wait 1–2 minutes. Your site goes live at:
   `https://<your-username>.github.io/<repo-name>/`

That's it — no other configuration is required for the site to load, the background to display, the soundboard to work, and the music player to play your playlist.

---

## 🎵 Music playback — how it works

The player uses the **official YouTube IFrame Player API**, so music plays *inside* the page — visitors are never redirected to YouTube.

- Default playlist: `PLYcG5OvQ0qOmVcIzktssmbTnYVUDqLAi6`
- To change it, open `index.html`, search for `PLAYLIST_ID`, and replace the ID with your own playlist's ID.
- Play, Pause, Next, Previous, Shuffle, Repeat (off → all → one), and the seek bar all control the real YouTube player.

### About browser autoplay
Browsers block audio/video from playing automatically before the visitor interacts with the page. This is normal, expected browser behavior — not a bug. Tractor Wala handles it gracefully: if playback is blocked, a **"▶ Tap to Play"** button appears near the player. One tap starts the music. Once a visitor has clicked *any* button on the page, YouTube also generally allows playback to continue normally.

### If a video won't play
Some videos in a playlist may be private, region-blocked, or age-restricted, which YouTube itself blocks from embedding — this is a YouTube-side restriction, not something the page can override. When that happens, Tractor Wala automatically skips to the next track.

---

## 🌾 Real-time "passengers on highway" counter (optional)

By default the counter honestly shows **"Firebase not configured"** — it never shows a fake or random number. To make it live:

1. Go to the [Firebase console](https://console.firebase.google.com/) and create a free project.
2. In the project, enable **Realtime Database** (start in test mode, or set rules to allow read on `/presence` and write on `/presence/$uid`).
3. Go to **Project settings → General → Your apps → Web app**, and copy the config object.
4. Open `index.html`, find this block near the top of the `<script>` section:

   ```javascript
   // ADD YOUR FIREBASE WEB CONFIG HERE
   var firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     databaseURL: "YOUR_DATABASE_URL",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_STORAGE_BUCKET",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

5. Replace the placeholder values with your real config and save.
6. Commit and push — the counter will now show real connected visitors, and automatically remove them when they close the tab (via Firebase's `onDisconnect`).

No config = no fake numbers, by design.

---

## 🎨 What's inside

| Feature | Details |
|---|---|
| Background | Your uploaded artwork, embedded directly as base64 — no image files needed |
| Day / Night mode | ☀️ दिवस / 🌙 रात्र — brighter warm daytime look vs. darker cinematic night look |
| Soundboard | 5 working sound effects (horn, tractor start, rain, village morning, highway whistle) generated live with the Web Audio API — no MP3 files |
| Music player | Real YouTube playback, custom glass UI, progress bar, shuffle/repeat |
| Playlist panel | Full-size video view, Play Playlist / Reset controls |
| Passenger counter | Real Firebase Realtime Database presence (optional setup above) |
| Responsive | Tested down to 320px wide, up through large desktop screens |
| Accessibility | Keyboard shortcuts (Space, ←, →, Esc), aria-labels, visible focus states |

---

## 🛠 Local testing

Just double-click `index.html` to open it in a browser, or run a tiny local server (recommended, since some browsers restrict certain APIs on `file://`):

```bash
# Python 3
python3 -m http.server 8000
# then open http://localhost:8000
```

---

## 📄 License / credit

Built as an original design inspired by Indian tractor, farm, and highway transport culture. Not affiliated with or copied from any existing site. Background artwork provided by the site owner.

सवारी आपल्या सामानाची स्वयं जबाबदार आहे ↻ | Tractor Wala Radio
