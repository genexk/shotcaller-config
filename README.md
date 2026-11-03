# shotcaller-config

Public, read-only configuration for the Shotcaller app (iOS and Android). It holds no code and no secrets.

The app fetches `https://genexk.github.io/shotcaller-config/config.json` to learn:

- `latestVersion`: show "update available".
- `minimumVersion`: below this, the app requires an update, for example after a La Marzocco firmware change breaks an older version. `updateMessage` explains why.
- `machines.<model>.verifiedFirmware`: firmware known to work. `blockedFirmware` lists firmware known to break brew by weight; the app warns and disables stopping on it.

Bump `updatedAt` on every change.
