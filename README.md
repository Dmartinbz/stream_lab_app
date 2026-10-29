# Stream Lab Android

Official Android APK releases for Stream Lab, for phones and Android TV.

## Current release

- Channel: Production
- App version: `1.3.0`
- Release tag: `v1.3.0`
- Phone APK: `stream-lab-v1.3.0.apk` (version code `24`)
- Android TV APK: `stream-lab-tv-v1.3.0.apk` (version code `25`)

Download published builds from the [GitHub Releases](https://github.com/Dmartinbz/stream_lab_app/releases) page. APK files belong in GitHub Releases, not in the repository's Git history.

## Publishing a release

Build from a clean copy of `stream_lab_mobile` (plus `packages`) from the main Stream Lab source repository. Version codes come from EAS and increase with every build.

```bash
npx eas-cli@latest build --platform android --profile production
npx eas-cli@latest build --platform android --profile production-tv
```

Download both builds, rename them to the APK names above, then publish them:

```bash
gh release create v1.3.0 stream-lab-v1.3.0.apk stream-lab-tv-v1.3.0.apk \
  --title "Stream Lab 1.3.0" \
  --notes-file notes.md
```

Update `release.json` and this README to match. The phone APK is also published to the in-app updater (`pnpm publish-apk … --channel production --prod` in `services/watch-party`); the TV APK is not, because the updater has one `production` channel for both.
