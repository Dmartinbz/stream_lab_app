# Stream Lab Android

Official Android APK releases for Stream Lab.

## Current release

- Channel: Beta
- App version: `0.1.0`
- Release tag: `v0.1.0-beta.1`
- Android version code: `10` (future EAS builds auto-increment this)
- APK name: `stream-lab-v0.1.0-beta.1.apk`

Download published builds from the [GitHub Releases](https://github.com/Dmartinbz/stream_lab_app/releases) page. APK files belong in GitHub Releases, not in the repository's Git history.

## Publishing the beta APK

Build from `stream_lab_mobile` in the main Stream Lab source repository:

```bash
npx eas-cli@latest build --platform android --profile beta
```

Download the completed build, rename it to the APK name above, then publish it:

```bash
gh release create v0.1.0-beta.1 stream-lab-v0.1.0-beta.1.apk \
  --prerelease \
  --title "Stream Lab 0.1.0 Beta 1" \
  --notes "First Stream Lab beta APK."
```

For the next beta, keep app version `0.1.0` and increment the prerelease tag (`beta.2`, `beta.3`, and so on). Change the app version to `0.2.0` when the user-facing release line changes.
