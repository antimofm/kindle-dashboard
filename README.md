# kindle-dashboard

A static night dashboard for a Kindle's web browser. Black background, white
monospace, sized for a 600px viewport.

Shows, for the current day:

- Date
- Verbose shipping-forecast-style weather for Lode, UK (Open-Meteo API)
- A rotating quote (one per day of month)
- A rotating haiku in the original Japanese/Chinese with translation

Live: https://antimofm.github.io/kindle-dashboard/

## Editing

Everything is in `index.html` — no build step. Edit, commit, push; GitHub
Pages redeploys.

Quotes and poems are arrays in the inline `<script>`; the day of month
indexes into them (`now.getDate() % arr.length`).
