# Ludo Royale

A no-account, room-code Ludo game using Node.js built-in HTTP and WebSocket support. No third-party npm dependencies are required.

## Run locally

- Requires Node.js 20+
- `npm start`
- Open `http://localhost:3000`
- Open a second browser/device on the same network using `http://YOUR-LAN-IP:3000` to test multiplayer.
- Run rule tests with `npm test`.

## Deployment

Deploy this folder to a Node.js host that supports long-lived WebSocket connections. Set `PORT` if required. The same process serves the frontend and WebSocket backend. Use HTTPS at the host; the client automatically selects WSS when served over HTTPS. `/health` provides a simple health check.

## Current implementation

- Duel (red/blue) and Classic (red/blue/green/yellow) game modes.
- Server-side move validation, dice rolls, captures, safe squares, home lanes, extra turns, and victory detection.
- Room codes, no-account joining, room state broadcasts, reconnect identity via browser local storage, emoji reactions, sound toggle, and a practice-vs-bots mode.
- Lightweight native WebSocket server; no npm runtime dependencies.

## Limitations to verify / harden before production

- Game rooms are held in memory and are lost on server restart; use Redis or a database for durable sessions and multi-instance hosting.
- The bot implementation is heuristic, not exhaustive search. Bot takeover after a disconnect is time-delayed and needs further multi-client testing.
- Multiplayer should be tested with real separate devices and a deployed HTTPS URL before claiming release readiness.
- Rate limiting, abuse controls, room expiry, automated reconnect/load testing, and production observability remain to be added.
