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

Update `release.json` and this README to match. Then, from `services/watch-party` in the main Stream Lab repository, offer each APK in the in-app updater. Phone and TV APKs are separate releases:

```bash
pnpm publish-apk ~/path/to/stream-lab-v1.3.0.apk --channel production --note "What changed" --prod
pnpm publish-apk ~/path/to/stream-lab-tv-v1.3.0.apk --channel production --note "What changed" --prod
```

The updater downloads APKs from this repository's releases, so the repository must stay public and released assets must not be replaced or renamed. The script checks the hosted file against the local APK before it publishes. APKs are never uploaded to Convex.
