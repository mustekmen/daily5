# Daily5 — Focus Tracker

## Overview
A single-page web app for tracking up to 5 daily focus areas with sub-tasks and progress tracking. Built with vanilla HTML/CSS/JS and Firebase (Auth, Firestore).

## Tech Stack
- **Frontend**: Single `index.html` file (no build step, no framework)
- **Backend**: Firebase (Auth for login/signup, Firestore for data persistence with offline support)
- **Notifications**: Web Push via Service Worker (`sw.js`)
- **Hosting**: GitHub Pages at `https://mustekmen.github.io/daily5/`

## Key Architecture
- All app logic is in a single IIFE inside `index.html`
- Firebase config is inline (public project: `daily5-app`)
- Firestore structure: `users/{uid}/dailyData/{date}` for daily focuses, `users/{uid}/settings/notifications` for notification preferences
- Service worker (`sw.js`) handles showing OS notifications and notification click events
- Main page communicates with SW via `postMessage`

## Features
- 5 focus cards per day with up to 3 sub-tasks each
- Manual progress (0/25/50/75/100%) for focuses without sub-tasks
- Date navigation with calendar picker
- Yesterday's incomplete items reminder banner
- Confetti animation on 100% completion
- Push notifications at 11:00 AM and 4:00 PM Istanbul time

## Recent Changes
- **Feb 2026**: Replaced EmailJS email reminders with Web Push Notifications via Service Worker. Removed all EmailJS dependencies. Settings UI simplified to a single toggle + test button.

## Running Locally
```
python3 -m http.server 8080 -d /Users/M_EKMEN1/daily5
# Open http://localhost:8080/index.html
```

## Deploying
```
git push  # GitHub Pages auto-deploys from main branch
```
