# Chicken — backendless WebRTC game

## Deploy on GitHub Pages

1. Upload `index.html`, `style.css`, and `app.js` to a GitHub repository.
2. Go to **Settings → Pages → Build and deployment → Deploy from a branch**.
3. Select `main` and `/ (root)` and save.
4. Open your GitHub Pages HTTPS URL.

## How to connect

1. Player 1 opens the site, selects **Single** or **Repeated**, then **Create game**.
2. Player 2 scans Player 1's offer QR or opens the copied offer link. On the site, Player 2 selects **Join game** then **Apply received code**.
3. Player 2 shows or sends the resulting answer QR/link to Player 1. Player 1 pastes the answer into the original tab and clicks **Apply received code**.
4. Both players choose independently. Choices are committed using SHA-256 before being revealed; scores and history are shown after both reveals.
5. For repeated games, both players press **Ready for next round**.

## Important limitations

- QR images are generated using the public `api.qrserver.com` service. The game does not have its own backend, but QR rendering **does require this third-party service**. For fully offline QR generation, vendor a browser QR encoder locally.
- WebRTC uses Google's public STUN server. Networks requiring a TURN relay may not connect.
- SDP offers/answers can exceed QR capacity. Copy/paste signaling links is the fallback.
- This is a teaching/demo app, not a secure competitive protocol: the local browser controls its own game logic. There is no persistence or authentication.
- Both players must keep their tabs open. Reloading disconnects the session.
- The WebRTC channel is encrypted in transit; the offer and answer should only be shared with intended participants.
