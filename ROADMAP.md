# Roadmap

Turn the single-page Kindle night dashboard into a small product other people
can point their own old Kindle at.

## Hard constraint

The Kindle experimental browser is ancient WebKit on grayscale e-ink: slow
repaints, no hover, unreliable swipe, flaky modern JS. Everything below must
degrade to plain `var` + `XMLHttpRequest` and survive on a 600px grayscale
screen. This constraint is a *feature* — it's what pushes the design toward
ASCII and tap zones.

---

## Phase 1 — Polish & make it feel alive (single file, no config)

Goal: same hardcoded setup, but nicer and interactive.

- **Tap zones** instead of hover. Left half / right half of the quote = prev /
  next quote. Tap the weather block = expand to 3-day forecast. Tap a corner =
  hard refresh. (Big invisible `<div>` hit targets — e-ink friendly.)
- **ASCII weather glyph** — a small multi-line drawn sun / cloud / rain /
  snow next to the conditions, picked from the WMO code.
- **Real moon phase** — computed from the date, drawn as ASCII (`( )`, `( ●`,
  full block). No API needed.
- **Temperature sparkline** — next 12h as block chars `▁▂▃▄▅▆▇`, already have
  the hourly data in the Open-Meteo call.

## Phase 2 — Make it configurable (still one URL, just params)

Goal: someone else can use it without editing code.

- **URL params**: `?lat=&lon=&place=&lang=&theme=`. Falls back to Lode/UK.
- **Quote packs**: `?pack=stoic|poetry|founders|italian` — bundle the arrays,
  select one. Default = mixed (current behaviour).
- **Themes**: `night` (black, current), `day` (white/sepia for daytime
  reading), auto-switch on local time.
- **Setup page** (`/setup.html`): pick a place from a short list, choose pack
  + theme, get a copy-paste URL + a QR code to open on the Kindle.

## Phase 3 — Distribution (it becomes a product)

Goal: discoverable, "turn your dead Kindle into a dashboard."

- **Landing page** (`index.html` becomes the pitch; dashboard moves to
  `/d/`): what it is, a screenshot, the setup flow.
- **Presets** — shareable named configs.
- **How-to**: the one annoying part is making the Kindle keep the page open
  (screensaver, sleep). Document the trick (airplane-mode + a refresh meta, or
  a known jailbreak-free workaround) — this is the real adoption blocker.
- Optional: submit to the small "old Kindle as e-ink display" communities.

---

## Creative module backlog (pick à la carte)

Daily-rotating or interactive pieces, all ASCII / text so they render on
e-ink. See the menu in chat — these are the candidates:

- Daily generative ASCII art, seeded by the date (unique pattern each day)
- Wind compass rose (ASCII)
- Sunrise → sunset arc with the sun's current position marked
- "On this day" — one history line
- Word of the day + etymology
- Visible planets tonight / stargazing line
- Second weather location (two places at once)
- Tap the poem to cycle: full → original only → translation only → fullscreen

## Open questions

- Kindle-awake problem (Phase 3) — needs real testing on the device.
- Quote/poem packs: keep curated, or allow a user-supplied list via param?
- Host stays GitHub Pages, or move to a custom domain once it's a product?
