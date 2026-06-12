# expo-react-native

Expo (React Native) starter, runs in Docker for the **web** target. Edit source on the host; Metro bundles + serves on `http://localhost:8081`.

## Run

```sh
docker compose up
```

First boot installs deps into a named Docker volume (so your host `node_modules` isn't touched). Then open http://localhost:8081 — you'll see the default Expo screen.

Edit `App.tsx`, save, and the page reloads (Fast Refresh + filesystem polling makes this work through Docker bind mounts).

## Native iOS / Android

This compose runs **Expo Web** only. For native builds:

```sh
npm install
npx expo run:ios       # requires Xcode on a Mac
npx expo run:android   # requires Android SDK
```

## Customizing

- Override the host port via `EXPO_PORT` in `.env`.
- Add packages with `npx expo install <pkg>` on the host (regenerates `package.json`); the container picks them up on next start.

## Files of note

- `App.tsx` — your app entry
- `app.json` — Expo config
- `docker-compose.yml` — bakes a Node 22 image and runs the Expo web dev server
