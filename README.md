# SCRAM — Hide & Seek (prototype)

A mobile-first installable web-app prototype for a real-world hide-and-seek game.

## What works in this prototype
- Responsive mobile UI
- Create a six-character demo game code or enter one
- Choose Runner, Hunter, or Random
- Configure round length, head start, ping interval and zone size
- Round timer and head-start transition
- Simulated location ping and tag reporting
- End-of-round results screen
- PWA manifest and service-worker scaffold

## What is not connected yet
This is a front-end prototype. It does **not** provide real multiplayer: a code entered on another phone does not join the same online game. It does not collect or share GPS, send push notifications, provide voice radio, or implement geofencing / a shrinking boundary. The map is illustrative only.

## Run locally
Open `index.html` in a browser. For service-worker/PWA testing, serve this folder over HTTPS or localhost, for example:
```sh
python3 -m http.server 8080
```
Then open `http://localhost:8080` on the same computer. For phone testing, deploy the folder to an HTTPS static host and open that URL on your phone.

## Next step for real multiplayer
Connect a backend such as Firebase or Supabase for authenticated sessions, game-code lookup, realtime player state, round state and server-side timers. Add a mapping SDK and explicit foreground/background location permissions. Use short-lived location records, delete game data on schedule, and only share location during active rounds with consent. Push notifications and team voice require separate platform integrations.

## Safety requirements before real-world testing
- Restrict play to a host-defined safe area; never encourage crossing roads or entering private/restricted property.
- Require each player to explicitly opt into location sharing.
- Show a clear active-location indicator and provide an immediate stop-sharing/leave-game action.
- Keep codes unguessable enough for the player count, rate-limit joining, and let the host remove players.
- Treat out-of-zone tracking as sensitive: disclose it before joining, limit it to the active game, and show a clear warning to the player being tracked.
- Do not rely on the app alone for physical tagging or safety.
