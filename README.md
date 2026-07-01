# Crew Dispatch — Route Optimizer

A single-page web app that splits jobs across work crews and builds an optimized route for each crew, then reports miles, drive time, labor cost, and fuel cost.

It's one self-contained file (`index.html`) — no build step, no dependencies to install, no server code. Open it in a browser or host it anywhere static.

## Features
- Add a home base and job stops by address, lat/lng, map click, or bulk paste.
- Assign jobs across any number of crews and optimize each route.
- Balance modes: even workload (finish together), equal stop counts, or fewest total miles.
- Round-trip travel-time buffer per crew.
- Cost outputs: total miles, drive time, parallel finish time, labor ($/hr × people per crew), and fuel ($/gal ÷ MPG).
- "Compare crew counts" to see the cost-vs-time tradeoff and pick the right number of crews.

## Run locally
Just open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari).

## Host it (pick one)
- **Netlify Drop:** go to https://app.netlify.com/drop and drag `index.html` in. Instant public URL, no account required.
- **GitHub Pages:** create a repo, add `index.html`, then Settings → Pages → Deploy from branch → `main` / root. URL: `https://<user>.github.io/<repo>/`.
- **Cloudflare Pages / Vercel:** create a project from the repo (framework preset: none). It serves the file as-is.

## How distances & time work
Distances are geometric and calculated automatically: great-circle (straight-line) distance × a built-in road factor (~1.3, approximating real street mileage), converted to drive time with a built-in average speed (~35 mph). Nothing to configure — it runs entirely in the browser, offline, with no stop limit. (Those built-in assumptions can be adjusted in the code if your area differs.)

## Notes / limitations
- Optimization is fully offline. Only the optional **address search** needs the internet (OpenStreetMap Nominatim); adding stops by `lat,lng` or map click needs no connection.
- Address lookups are restricted to the San Francisco Bay Area and throttled to ~1/second (OpenStreetMap policy). Coordinates are instant.
- Distances/times are estimates, not turn-by-turn road distances (built-in road factor ~1.3 and ~35 mph).
- No backend, no data stored — everything runs client-side.
