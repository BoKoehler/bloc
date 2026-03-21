<div align="center">

<br/>

```
██████╗ ██╗      ██████╗  ██████╗
██╔══██╗██║     ██╔═══██╗██╔════╝
██████╔╝██║     ██║   ██║██║
██╔══██╗██║     ██║   ██║██║
██████╔╝███████╗╚██████╔╝╚██████╗
╚═════╝ ╚══════╝ ╚═════╝  ╚═════╝
```

**Personal training log. Built for me. Shared because it's good.**

[![Live App](https://img.shields.io/badge/live-app-e8533a?style=flat-square)](https://yourusername.github.io/bloc)
![No dependencies](https://img.shields.io/badge/dependencies-0-161618?style=flat-square)
![Vanilla](https://img.shields.io/badge/framework-none-161618?style=flat-square)
![PWA](https://img.shields.io/badge/PWA-yes-e8533a?style=flat-square)

<br/>

</div>

---

I train six days a week. Every app I tried was either bloated with features I didn't need, wanted a subscription, or just didn't work the way I think about training. So I built my own.

BLOC is a progressive web app — five files, zero dependencies, installs to your iPhone home screen and runs exactly like a native app. Your data never leaves your device. There's no backend, no account, no analytics. Just your training log.

<br/>

## Overview

```
Log sessions  →  Active workout mode  →  PR book builds itself
     ↓                   ↓                        ↓
Templates         Rest timer + history       1RM estimates
     ↓                   ↓                        ↓
     └──────── Body weight tracker ───────────────┘
                         ↓
                  Export backup anytime
```

<br/>

## What's in it

<details>
<summary><strong>Session Logging</strong></summary>
<br/>

Name your session, date it, add exercises. Simple.

The thing most apps get wrong is set logging. Most force you to pick one rep count for every set — but that's not how it works when you're actually training. BLOC gives you two modes per exercise:

**Uniform** — same weight and reps across every set. Three fields, done in seconds.

**Per Set** — individual row per set with its own reps, weight, and rest time. For when you hit 8 on your first two sets and 6 on the third. That difference matters and it should be logged accurately.

Per-exercise notes for anything you want to remember — grip cues, variations, why something felt off.

</details>

<details>
<summary><strong>Active Workout Mode</strong></summary>
<br/>

This is where the app actually earns its keep. After saving a session, you can launch it in Active Mode — a full-screen UI designed for use while you're standing in the gym.

- Large inputs built for thumbs
- Tap ✓ on each set to mark it done — it goes green
- Rest timer starts automatically when you complete a set
- Elapsed session clock in the header
- Any weight or rep changes you make mid-session save back to your log

The difference between a logging app and a training tool is this mode.

</details>

<details>
<summary><strong>Rest Timer</strong></summary>
<br/>

Set rest periods when you log — either one value for the whole exercise (Uniform mode) or per set (Per Set mode). When you tap a set done in Active Mode, the countdown starts.

Blue banner with a live countdown and a skip button. Pulses green when the rest is up. Quick-select chips for 60 / 90 / 120 / 180 seconds so you're not typing every time.

</details>

<details>
<summary><strong>Templates</strong></summary>
<br/>

Save any session structure as a template. If you're running the same split week over week — Push, Pull, Lower, Upper, whatever — you shouldn't be re-entering your exercise list every time.

Tap **Use** on a template and the session pre-fills with your exercises, sets, and rest periods. Weights are blank — you fill those in fresh each session. The structure is saved, the numbers aren't.

</details>

<details>
<summary><strong>Exercise History</strong></summary>
<br/>

When logging a new session and you start typing an exercise name, a dropdown shows your last 5 logged sessions of that lift — date, sets breakdown, and total volume. You can see what you did last week before deciding what to put on the bar today.

No separate history page to navigate to. It's inline, right where you need it.

</details>

<details>
<summary><strong>PR Book</strong></summary>
<br/>

Builds itself from your session history. Every exercise you've ever logged, sorted by movement category — Push / Pull / Legs / Core / Other. Shows your heaviest logged weight next to an estimated 1RM.

Updates every time you log a new session. Nothing to maintain.

</details>

<details>
<summary><strong>1RM Estimates</strong></summary>
<br/>

Estimated 1-rep max calculated automatically via the Epley formula wherever weight and reps are logged:

```
estimated 1RM = weight × (1 + reps / 30)
```

Shows in the PR Book, session detail view, and Active Mode per exercise. Not gospel, but a useful reference point for tracking strength over time without always going to failure.

</details>

<details>
<summary><strong>Body Weight Tracker</strong></summary>
<br/>

Log weight with a date. See:

- Current weight
- Total change from your first entry (green if down, red if up)
- 7-day rolling average
- Full history with delta between each entry

The 7-day average is the one that actually matters — it smooths out day-to-day noise from water, food timing, sleep.

</details>

<details>
<summary><strong>Data Backup</strong></summary>
<br/>

Settings → Export Backup → saves a JSON file of everything: sessions, body weight history, templates.

Import it back anytime to restore. Useful when switching phones or if you ever need to recover. The file is small. The whole process takes about five seconds. Do it once a month.

</details>

<br/>

## Install

BLOC runs as a PWA — installs to your iPhone home screen, runs fullscreen, gets its own storage that won't get wiped when you clear your browser cache.

**Has to be Safari. Chrome on iOS won't do it.**

1. Open your GitHub Pages URL in **Safari**
2. Tap the share button at the bottom of the screen
3. **Add to Home Screen**
4. **Add**

Open it from your home screen from that point on — not from the browser. The installed version has isolated storage.

<br/>

## Deploy

Five files. Two minutes.

```
bloc/
├── index.html        ← the whole app
├── manifest.json     ← PWA config
├── sw.js             ← service worker for offline
├── icon-192.png      ← home screen icon
└── icon-512.png      ← home screen icon (large)
```

**Steps:**

```
1. GitHub → New repository (Public)
2. Upload all 5 files
3. Settings → Pages → Deploy from branch → main / root → Save
4. Wait ~60 seconds → your URL is ready
5. Open in Safari on iPhone → Add to Home Screen
```

> Updating later: replace `index.html` in the repo. The PWA updates automatically on next open. Your data is untouched.

<br/>

## Backup & Restore

```
Backup  →  ⚙ Settings  →  Export Backup  →  save the .json somewhere
Restore →  ⚙ Settings  →  Import Backup  →  select the file  →  confirm
```

Do this monthly. It takes five seconds and covers you if you ever clear your browser storage, factory reset your phone, or switch devices.

<br/>

## Reference

| What you want to do | How |
|---|---|
| Log a new session | **Log New Session** button on the Log tab |
| Start Active Mode | Save a session → tap Yes on the prompt |
| Mark a set complete | Tap **✓** in Active Mode |
| Skip the rest timer | Tap **Skip** on the blue banner |
| Load a saved workout | Log tab → Templates → **Use** |
| See past history for a lift | Start typing the exercise name while logging |
| View all PRs | **PRs** tab in the bottom nav |
| Back up everything | ⚙ Settings → **Export Backup** |

<br/>

## Stack

| | |
|---|---|
| Frontend | Vanilla HTML / CSS / JS — no framework |
| Storage | `localStorage` |
| Fonts | Barlow Condensed, Barlow, JetBrains Mono |
| PWA | Web App Manifest + Service Worker |
| Hosting | GitHub Pages |
| Cost | $0 |

The whole app is `index.html`. Everything else is PWA infrastructure.

<br/>

## Data & Privacy

Everything lives in your browser's `localStorage`. Nothing is sent anywhere. No server. No account. No tracking.

The only external call is Google Fonts on first load — cached by the service worker after that, so it works fully offline.

<br/>

---

<div align="center">

Built for personal use. Works well. Sharing it.

</div>
