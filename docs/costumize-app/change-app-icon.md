---
sidebar_position: 1
sidebar_label: Change App Icon
---

# Change App Icon

to change the icon in this app is very easy, because `Helo Teacher Client and Teacher App` use the https://pub.dev/packages/flutter_launcher_icons library which makes it easier for us to change the app icon

to change the icon :

- just change the icon file at `/assets/icons/ic_launcher.png` with your icon, and make sure the name is same which is `ic_launcher.png`

- after you change the icon, run this command on your terminal

```
flutter pub run flutter_launcher_icons:main
```

- the icon in your app should have been replaced with a new one
