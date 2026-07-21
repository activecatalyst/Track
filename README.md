# Track

A small, private web app for logging bowel movements so you have real data to bring to a gastroenterology appointment. It's built to feel warm, discreet, and non-shaming — a quick medical aid, not a chore.

**Track is a tracking aid, not medical advice or a diagnosis.** If you're worried about a symptom, talk to a doctor.

## What it does

The whole app is a single file (`track.html`). Open it in a browser and it works. Everything you log stays on your own device — nothing is uploaded anywhere.

- **One-tap logging.** If everything was unremarkable, one tap on "Log a normal one" records a normal entry and bumps today's count. This is the main way to use it.
- **Detail when you need it.** Bristol stool type (1–7), color, urgency, pain, blood, mucus, smell, and an optional context/note field — every symptom field defaults to "normal / not sure," so adding detail is opt-in.
- **Smart flagging.** Entries that are worth mentioning to a doctor (constipation/diarrhea types, concerning colors, blood or mucus, severe urgency or pain) are flagged automatically and collected in one place. Color is treated as authoritative — dark or red coloring flags an entry even if you weren't sure about blood.
- **A clean summary.** Rolling stats over 7 / 30 / 90 days, including Bristol distribution, time-of-day pattern, and a simple trend — printable as a one-page sheet for your appointment.
- **Your data stays yours.** Export or import a JSON backup, and wipe everything with a confirm step.

## Getting started

### Just open it
Double-click `track.html`, or drag it into any modern browser (Chrome, Safari, Firefox, Edge). That's it — no install, no account, no internet needed after the first load.

### Install it on your phone (optional)
It's a Progressive Web App, so you can add it to your home screen and it opens like a native app, fully offline.

1. Host `track.html` somewhere with HTTPS — [GitHub Pages](https://pages.github.com) is free and works well. (Rename it to `index.html` so it loads at the root.)
2. Open that URL on your phone.
3. **iPhone (Safari):** Share button → "Add to Home Screen."
   **Android (Chrome):** menu (⋮) → "Install app" / "Add to Home Screen."

The home-screen icon and browser tab show a small sage-green target mark on charcoal — deliberately plain, so it gives nothing away on your device.

## How the data works

- All entries live in your browser's `localStorage` under keys prefixed `ac_track_`.
- Because it's tied to that browser on that device, clearing site data or switching devices/browsers means the data won't follow automatically — use **Export** (in the gear menu) to keep a backup or move it. **Import** merges a file back in without creating duplicates.
- Nothing is ever sent to a server. There is no server.

## The four tabs

- **Log** — the default screen. Logging plus today's count only; it deliberately does not show a running list of past entries, for privacy and to keep logging clean.
- **Flags for review** — only the entries the app flagged, each with a plain-language reason. Printable to bring to a doctor.
- **Summary** — the rolling stats and patterns described above.
- **History** — your full log, grouped by day, collapsed behind its own tab. Days with no entries are shown as a quiet marker — a gap is data, and there are no nagging notifications.

## Deliberately left out

Hydration, calorie/food logging, weight, mood scales, streaks or gamification, social sharing, and pushy notifications. Each of those turns a quick medical aid into a chore, so they're intentionally absent.

## Technical notes

- Single-file vanilla HTML / CSS / JavaScript — no build step, no dependencies, no frameworks.
- PWA support via an inline manifest and a small service worker (both embedded as data URIs) for offline use.
- Mobile-first, dark, high-contrast interface with generous touch targets.

## Privacy

Track collects no analytics and makes no network requests. Your log never leaves your device unless you explicitly export it. Treat exported JSON files like any other personal medical record.
