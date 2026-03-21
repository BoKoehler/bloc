<div align="center">

<br/>

# BLOC

**Personal training log. Built for me.**

[![Live App](https://img.shields.io/badge/open%20app-e8533a?style=for-the-badge)](https://yourusername.github.io/bloc)
&nbsp;
![No Dependencies](https://img.shields.io/badge/dependencies-zero-161618?style=for-the-badge)
&nbsp;
![PWA](https://img.shields.io/badge/installs%20as%20PWA-yes-e8533a?style=for-the-badge)

<br/>

</div>

---

I train six days a week and every existing app I tried was either bloated, behind a paywall, or just built for someone who goes to the gym twice a week and needs motivation notifications. None of them worked the way I think about training.

So I built my own.

BLOC is a progressive web app. Five files, zero dependencies. Install it to your iPhone home screen and it runs fullscreen like a native app. Your data never leaves your device. No backend, no account, no subscription. Just your training log.

<br/>

## What's In It

<details>
<summary><b>Session Logging</b></summary>
<br/>

Name your session, date it, add exercises. Pretty straightforward.

The part most apps mess up is set logging. They make you pick one rep count for every set but that's not how training actually works. BLOC gives you two modes per exercise:

**Uniform** — same weight and reps across every set. Three fields and you're done.

**Per Set** — individual row for each set with its own reps, weight, and rest time. For when you get 8 on your first two sets and drop to 6 on the third. That difference matters and it should be logged accurately.

Per-exercise notes too, for anything worth remembering like grip cues, variations, or why something felt off.

</details>

<details>
<summary><b>Active Workout Mode</b></summary>
<br/>

This is the most important part. After saving a session you can launch it in Active Mode, which is a full-screen UI built for actually being at the gym and using it in real time.

- Large inputs that work with your thumbs
- Tap the checkmark on each set to mark it done and it goes green
- Rest timer kicks off automatically when you complete a set
- Elapsed session clock in the header
- Any weight or rep changes you make mid-session save back to your log automatically

The difference between a logging app and a real training tool is this mode.

</details>

<details>
<summary><b>Rest Timer</b></summary>
<br/>

Set rest times when you log your session. Either one value for the whole exercise in Uniform mode, or per set in Per Set mode. When you tap a set done in Active Mode the countdown starts on its own.

Blue banner with a live countdown and a skip button. Turns green when the rest is up. Quick-tap buttons for 60 / 90 / 120 / 180 seconds so you're not typing it every time.

</details>

<details>
<summary><b>Templates</b></summary>
<br/>

Save any session structure as a template. If you run the same split week over week you shouldn't be re-entering your exercise list every single time.

Tap Use on a template and the session pre-fills with your exercises, sets, and rest periods. Weights stay blank so you fill those in fresh each session. The structure is saved, the numbers aren't.

</details>

<details>
<summary><b>Exercise History</b></summary>
<br/>

When you're logging a new session and start typing an exercise name, a dropdown shows your last five logged sessions of that lift. Date, sets breakdown, and total volume. You can see exactly what you did last week before you decide what to put on the bar.

It's inline right where you need it, no separate page to navigate to.

</details>

<details>
<summary><b>PR Book</b></summary>
<br/>

Builds itself from your session history. Every exercise you've ever logged sorted into Push / Pull / Legs / Core / Other. Shows your heaviest logged weight and an estimated 1RM next to it.

Updates every time you log. Nothing to maintain manually.

</details>

<details>
<summary><b>1RM Estimates</b></summary>
<br/>

Estimated one-rep max calculated automatically using the Epley formula anywhere you've logged weight and reps:

```
estimated 1RM = weight x (1 + reps / 30)
```

Shows in the PR Book, session detail view, and Active Mode. Not an exact number but a solid reference point for tracking strength over time without going to failure every session.

</details>

<details>
<summary><b>Body Weight Tracker</b></summary>
<br/>

Log your weight with a date. You get:

- Current weight
- Total change from your first entry, color coded green or red
- 7-day rolling average
- Full history with the delta between each entry

The 7-day average is the number that actually matters. It smooths out the noise from water weight, food timing, and sleep so you can actually see what's happening.

</details>

<details>
<summary><b>Data Backup</b></summary>
<br/>

Settings then Export Backup saves a JSON file with everything in it. All sessions, body weight history, and templates.

Import it back anytime to restore. Good for switching phones or just keeping a copy somewhere safe. The file is tiny and the whole thing takes about five seconds. Do it once a month.

</details>

<br/>

## Installing to Your Phone

BLOC is a PWA so it installs directly to your iPhone home screen and runs fullscreen like a native app. It also gets its own isolated storage that won't get cleared when you wipe your browser cache.

**Has to be Safari. Chrome on iOS doesn't support this.**

```
1. Open your GitHub Pages URL in Safari
2. Tap the Share button at the bottom of the screen
3. Add to Home Screen
4. Add
```

Open it from your home screen from that point on, not from the browser. The installed version has its own separate storage.

<br/>

## Deploy It

Five files. About two minutes.

```
bloc/
  index.html      the whole app
  manifest.json   PWA config
  sw.js           service worker for offline support
  icon-192.png    home screen icon
  icon-512.png    home screen icon, larger
```

```
1. GitHub -> New repository, set it to Public
2. Upload all five files
3. Settings -> Pages -> Deploy from branch -> main / root -> Save
4. Wait about 60 seconds and your URL is live
5. Open it in Safari on your iPhone and add to home screen
```

To update later just replace `index.html` in the repo. The PWA picks up changes automatically on the next open and your data stays untouched.

<br/>

## Backup and Restore

```
Backup   ->  gear icon (top right)  ->  Export Backup  ->  save the .json file somewhere
Restore  ->  gear icon (top right)  ->  Import Backup  ->  select the file  ->  confirm
```

Do this monthly. It takes five seconds and covers you if you factory reset your phone, switch devices, or accidentally clear your browser storage.

<br/>

## Quick Reference

| What you want | How to do it |
|---|---|
| Log a new session | Log New Session button on the Log tab |
| Launch Active Mode | Save a session, then tap Yes on the prompt |
| Mark a set complete | Tap the checkmark circle in Active Mode |
| Skip the rest timer | Tap Skip on the blue timer banner |
| Load a saved workout | Log tab -> Templates -> Use |
| See history for a lift | Start typing the exercise name while logging |
| View all PRs | PRs tab in the bottom nav |
| Back up your data | Gear icon -> Export Backup |

<br/>

## Stack

| | |
|---|---|
| Frontend | Vanilla HTML, CSS, JS. No framework. |
| Storage | localStorage |
| Fonts | Barlow Condensed, Barlow, JetBrains Mono |
| PWA | Web App Manifest + Service Worker |
| Hosting | GitHub Pages |
| Cost | $0 |

The entire app is `index.html`. Everything else is just the PWA wrapper.

<br/>

## Data and Privacy

Everything is stored in your browser's `localStorage`. Nothing is sent anywhere. No server, no account, no tracking of any kind.

The only external request is Google Fonts on first load. The service worker caches those so the app works fully offline after that.

<br/>

---

<div align="center">

Built for personal use. Works well. Sharing it.

</div>
