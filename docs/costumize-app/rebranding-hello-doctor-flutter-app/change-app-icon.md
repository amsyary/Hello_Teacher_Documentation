---
sidebar_position: 3
sidebar_label: Change App Icon
---

# Change App Icon

Changing the icon is handled using the Flutter package `flutter_launcher_icons`.

## Steps

1. Replace the icon file:

- `/assets/icons/ic_launcher.png`

Make sure:

- The filename stays **exactly** `ic_launcher.png`.

2. Run the icon generator command:

```bash
flutter pub run flutter_launcher_icons:main
```

3. Rebuild/reinstall the app if needed to see the new icon.
