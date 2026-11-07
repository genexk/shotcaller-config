# shotcaller-config

Public, read-only configuration for the Shotcaller app (iOS and Android). It holds no code and no secrets.

The app fetches `https://genexk.github.io/shotcaller-config/config.json` to learn:

- `latestVersion`: show "update available".
- `minimumVersion`: below this, the app requires an update, for example after a La Marzocco firmware change breaks an older version. `updateMessage` explains why.
- `machines.<model>.verifiedFirmware`: firmware known to work. `blockedFirmware` lists firmware known to break brew by weight; the app warns and disables stopping on it.
- `features`: same-day switches for every platform. Each one is on when its key is missing or not a `true`/`false` value.
  - `stoppingEnabled`: `false` turns brew by weight off from the next shot (a shot already running is never changed). `stoppingMessage` (string or `null`) replaces the default "Brew by weight is paused remotely." on Home.
  - `cloudEnabled`: `false` stops the app using the La Marzocco account (sign-in, machine status, token fetch, remote controls). `cloudMessage` (string or `null`) replaces the default "La Marzocco account features are paused."
  - Keep messages short (the app cuts them at 120 characters). Apps pick up a change the next time they open, at most every 6 hours; an offline phone keeps its last copy.

Bump `updatedAt` on every change.
