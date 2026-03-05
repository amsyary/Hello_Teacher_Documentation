---
sidebar_position: 2
sidebar_label: Release iOS
---

# Release iOS App (IPA)

This guide shows how to build a **release IPA** for a Flutter app.

:::info
You must use **macOS + Xcode** to build iOS releases. iOS builds cannot be produced on Windows.
:::

## Prerequisites

- macOS with Xcode installed
- Apple Developer account
- Xcode signing set up (Team, Bundle Identifier, Provisioning Profile)

## 1) Set iOS bundle identifier and signing

Open the iOS project in Xcode:

- `ios/Runner.xcworkspace`

Then:

- Set **Bundle Identifier** (Runner target)
- Select your **Team**
- Ensure **Signing & Capabilities** is valid

## 2) Build a release IPA

From your Flutter project root:

```bash
flutter clean
flutter pub get
flutter build ipa --release
```

If you need a specific export method (common values: `app-store`, `ad-hoc`, `development`):

```bash
flutter build ipa --release --export-method app-store
```

Output is typically under:

- `build/ios/ipa/`

## Notes

- For App Store distribution, ensure your bundle identifier matches the App Store Connect app.
- If build fails due to signing, fix it in Xcode (**Signing & Capabilities**) and try again.
