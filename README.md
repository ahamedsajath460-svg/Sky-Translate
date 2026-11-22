# Sky Translate – website

The Android app, rebuilt as a plain static website (HTML + CSS + JS, no build step, no backend).
The look, screens, animations and flows are the same as the app; everything that was native Android now uses the browser.

## Run it

Locally (any static server; `localhost` counts as secure, so mic/camera work):

```bash
cd SkyTranslate-Web
python3 -m http.server 8080      # then open http://localhost:8080
```

Online: upload the folder to any static host (GitHub Pages, Netlify, Cloudflare Pages, Vercel, your own server).
It must be served over **HTTPS** for the microphone, camera and clipboard to work.

## API keys

Keys are preset (encoded) inside `index.html`. There is no key-entry screen for visitors. Classic translation (MyMemory) works without a key.

## Features (all kept)

Text translation (Advanced AI + Classic) · auto-detect language · Tamil romanization · more translations · dictionary
definitions · AI explanation · grammar correction note · web search · voice translate (mic) · live translate
(conversation + text-only) · camera translate (live overlay, photo, gallery, select lines, copy / search / listen /
send to translate) · handwriting input · 240+ languages with search, pinned and recent · history (swipe to delete, star)
· saved phrases · 35 AI voices + device voice · all 9 AI translation settings · dark theme · Tap to Translate
(floating button).

## What changed because it is a website now

| App | Website |
|---|---|
| ML Kit OCR (native) | Tesseract.js in the browser (loaded from a CDN on first camera use, needs internet) |
| Native speech / clipboard bridges | The browser's own Web Speech API and Clipboard API |
| Keys injected at build time | Keys entered in Settings (or `ai-keys.js`) |
| Android back button | Browser Back button and **Esc** close the top-most screen |
| Tap to Translate notification | Floating button inside the site (reads your clipboard) |
| – | Theme and last language pair are remembered; installable (manifest + icons); framed card on wide screens |

Right-click a language row = pin/unpin (long-press on touch).

## Browser notes

- Voice input (mic, live translate) needs Chrome, Edge or Safari. Firefox has no speech recognition; the app says so.
- Handwriting uses Google's input-tools endpoint; if the browser blocks it you get a "Couldn't read that" hint.
- The offline-language download screen from the app was a visual mock-up that was never reachable in the app UI, so it was not carried over.
