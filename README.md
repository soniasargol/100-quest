# 100 Days of Guitar

A personal 100-day practice tracker: three songs, zero prior background, one small logged day at a time.

Live site: https://soniasargol.github.io/100-quest/

Inspired by Struthless's ["Transform your life in 100 days"](https://www.youtube.com/watch?v=vfHlp4xd-aU) framework.

## How it works

This is a single static page (`index.html`), no build step or backend.

- **Public / view mode**: anyone visiting the site sees a read-only map of the 100 days, current streak, total time practiced, and per-day entries, loaded from `data/logs.json`.
- **Owner / edit mode**: visiting with `?edit=1` once unlocks logging, reset, export, and import for that browser (stored in a `localStorage` flag). Visiting with `?view=1` clears that flag and returns to the public view.

## Data flow

- While logging practice as the owner, entries are saved to that browser's `localStorage`, not to GitHub.
- **"back up my progress"** downloads a full JSON snapshot of local state (useful as a personal backup / restore point).
- **"publish log to site"** downloads `logs.json` in the public format; that file replaces `data/logs.json` in this repo and gets committed and pushed to update the live site for everyone else.

So `data/logs.json` in the repo is the durable, shared record; `localStorage` is just the owner's working copy on one device.

## Local dev

No dependencies. To preview locally:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser.

## Credit

Song-tracking structure and "vs. procrastination / self-doubt / etc." framing borrowed from Struthless's video ["Transform your life in 100 days"](https://www.youtube.com/watch?v=vfHlp4xd-aU).
