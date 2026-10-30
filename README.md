# SCRAM — location-enabled prototype

This build adds a real OpenStreetMap/Leaflet map, a pre-game zone-centre picker, an adjustable 100 m–1.5 km radius, an explicit **Use my location** permission action, GPS tracking during the local round, and a working local Hunter ping timer/status.

## Publish update
1. Extract the ZIP.
2. In the GitHub `scram` repository, choose **Add file → Upload files**.
3. Upload/replace all files inside this folder, including `index.html`, `styles.css`, `app.js`, `manifest.json`, `sw.js`, and `README.md`.
4. Commit changes. GitHub Pages should redeploy automatically.
5. Open the HTTPS website, create a game, tap the map to choose the centre, set the radius, then start the round. Use **Use my location** to request GPS permission.

## What works now
- Real interactive street map (requires internet access).
- Tap or drag a marker to select the play-zone centre before the round.
- Set the radius from 100 m to 1.5 km.
- Browser geolocation permission and local GPS tracking while a round is active; tracking stops when the round ends.
- Zone circle drawn on the setup and game maps; local out-of-zone warning.
- Local round timer, head start, and Hunter ping schedule.

## Still requires a shared backend
Game codes currently do not create a cross-device lobby. Location pings and tags are local UI actions, not delivered to other players. To launch real multiplayer, connect a Supabase project, add authenticated game membership, and enforce server-side role-based access for every location read/write. Never put a Supabase service-role/secret key in this public website. Use only a publishable/anon client key with strict RLS or secure Edge Functions.

## Safety and privacy
- The browser only requests GPS when the player presses the location button or starts a round.
- Location is not intentionally saved to a remote server by this build.
- This is not ready for real-world multiplayer play until backend access controls and cross-device testing are completed.
- Use an agreed safe area; stay out of roads and private/restricted property. Never play while driving.

## Map attribution
Map tiles are provided by OpenStreetMap contributors. See https://www.openstreetmap.org/copyright. Leaflet is loaded from unpkg CDN.
