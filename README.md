# ServerPal

ServerPal is a small, non-commercial Fabric companion mod for a private Minecraft: Java Edition survival server shared by a group of friends. It is **not** a launcher and **not** an account manager.

## What it does

- Custom music discs and in-game media features for our server
- Server-side helpers (scheduled restarts, host reboot with automatic reconnect)
- Self-update: when the server requires a newer mod version, the client downloads it and relaunches the game automatically

## Why it needs Microsoft / Minecraft sign-in

Players start the game normally with the official launcher or the CurseForge app. After a long play session, the Minecraft access token passed at launch (valid ~24h) has expired, so when ServerPal relaunches the game after an update, the player gets "Invalid Session" and cannot rejoin.

To fix this, a player can optionally authorize **their own account once** via the Microsoft device code flow. ServerPal then refreshes **that same account's** session silently (Microsoft → Xbox Live → XSTS → Minecraft Services) before relaunching, or when the token is about to expire.

## Security & privacy

- Device code flow only — ServerPal never sees or handles passwords
- Requested scopes: `XboxLive.signin offline_access` only
- The refresh token is stored locally, encrypted with Windows DPAPI, and never leaves the player's computer
- No backend server receives any tokens
- No multi-account switching; each player can only refresh the account they signed in with
- Does not bypass any security, authentication, or license checks

## Contact

GitHub: [@future830759](https://github.com/future830759)
