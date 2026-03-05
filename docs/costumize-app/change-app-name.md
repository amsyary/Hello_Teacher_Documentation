---
sidebar_position: 1
sidebar_label: Change App Name
---

# Change App Name

This guide explains how to change the **display name** (the name shown under the app icon) for both **Android** and **iOS**.

## Android (AndroidManifest.xml)

1. Open `android/app/src/main/AndroidManifest.xml`.
2. Find the `<application>` tag and update the `android:label` value.

Example:

```xml
<application
    android:label="Hello Teacher"
    ...>
</application>
```

## iOS (Info.plist)

1. Open `ios/Runner/Info.plist`.
2. Find `CFBundleDisplayName` and change its value.

Example:

```xml
<key>CFBundleDisplayName</key>
<string>Hello Teacher</string>
```

### If `CFBundleDisplayName` does not exist

Add it (recommended) or update `CFBundleName`.

## Apply the changes

After updating the files above, rebuild the app:

```bash
flutter clean
flutter pub get
flutter run
```

## Change platform label (Login title)

Besides the Android/iOS display name, the app may show a **platform label/title inside the UI** (for example on the login screen).

To change it, update this widget file:

- `lib/app/modules/login/views/widgets/title_app.dart`

Typical change:

1. Open the file and find the text used for the title (usually a `Text(...)` widget).
2. Replace the string with your new label.

Example:

```dart
// Before
Text('Hello Teacher'),

// After
Text('My New App Name'),
```

Then run the app again (or use hot reload) to see the updated label.
