# Podium — Speaking & Pitch Practice

A personal practice tool for public speaking and business pitching. Fully client-side — no backend, no account, works offline once installed.

## What works in this version
- Public Speaking mode: random topic, record, transcript, stats (duration, WPM, filler words), playback, audio download
- Business Pitch mode: random pitch scenario, live spoken interjections during recording, same stats/transcript/playback
- History: saved locally on your device (browser `localStorage`), with full detail view per session
- Principles reference page

**Not included in this version:** AI-generated coaching feedback (the "what you did wrong / how to improve" writeup). That required a Claude API call, which only works inside claude.ai. It's disabled here so the app can run standalone — you still get the transcript and objective stats.

## Browser support (important)
- **Recording + playback**: works everywhere.
- **Live transcript**: needs the browser's built-in speech recognition.
  - ✅ Chrome / Edge — desktop and Android
  - ❌ Safari (iPhone/iPad) — not supported by Safari at all. On iPhone you'll get audio only, no transcript, no filler/WPM stats.
  - If iPhone transcription matters to you, the workaround is opening the app in Chrome on iOS (which still uses Apple's WebKit under the hood, so it *also* won't work — Safari's lack of support is an iOS-wide limitation, not a Safari-only one). There's no real fix without adding a paid transcription API.

## Setting it up on GitHub Pages (free hosting)

1. Create a new GitHub repository (e.g. `podium-practice`).
2. Upload these four files to the repo root: `index.html`, `manifest.json`, `sw.js`, `icon.png`.
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`. Save.
5. Wait a minute or two, then GitHub will give you a URL like `https://yourusername.github.io/podium-practice/`.
6. Open that link on your phone.

## Installing it like an app

- **Android (Chrome)**: open the link → tap the ⋮ menu → "Add to Home screen" (or Chrome may prompt automatically). It'll behave like a standalone app and cache itself for offline use after the first load.
- **iPhone (Safari)**: open the link → tap the Share icon → "Add to Home Screen". Remember: no transcript on iPhone, per above — you'll get recording/playback/history only.

## A note on "fully offline"

Once installed, the app shell (the interface itself) is cached and will open with no internet connection. The **speech recognition** feature, when it works (Chrome/Android), still sends audio to Google's servers to transcribe — that part specifically needs an internet connection even though the rest of the app doesn't. Recording, playback, stats math, and history are all 100% local regardless of connection.

## Local history storage

Each session (transcript, stats, timestamp) is saved in your browser's local storage, per-device. It is **not synced** between your phone and any other device — a session recorded on your Android phone won't show up if you open the same GitHub Pages link on your iPhone. If cross-device history matters later, that would need a real backend.
