---
sidebar_position: 1
sidebar_label: Release Android
---

# Release Android App (APK / App Bundle)

This guide covers Android release signing, generating the **release SHA1**, and building a release **APK** or **AAB (App Bundle)**.

## Prerequisites

- Flutter SDK installed
- Android Studio + Android SDK installed
- Java JDK installed (so `keytool` works)

:::info
If you get an error like `keytool is not recognized`, ensure your JDK is installed and added to PATH.
:::

## 1) Generate a release keystore (`.jks`)

From your Flutter project root, create a keystore file (example path: `android/app/upload-keystore.jks`).

```bash
keytool -genkeypair -v -keystore android/app/upload-keystore.jks -alias upload -keyalg RSA -keysize 2048 -validity 10000
```

During the prompts, set:

- **Keystore password**
- **Key password** (can be same as keystore password)
- Identity information (CN, OU, O, L, ST, C)

:::caution
Do not commit the keystore to a public repository. Keep a secure backup. If you lose it, you cannot update the same Play Store app signing identity.
:::

## 2) Create `key.properties`

Create a file at `android/key.properties`.

```properties
storePassword=YOUR_STORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=upload
storeFile=upload-keystore.jks
```

### Windows example (absolute path)

On Windows, you can also point `storeFile` to an **absolute** keystore path.

```properties
# Example (Windows)
# Use your own passwords and keep them private.
storePassword=YOUR_STORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=upload
storeFile=C:/Users/Amsyari/upload-keystore.jks
```

Notes:

- If possible, prefer a **relative** path (example: `storeFile=upload-keystore.jks`) and keep the keystore inside the `android/` folder.
- Keep this file private (avoid committing it). Add it to `.gitignore` if needed.

## 3) Configure signing in `android/app/build.gradle`

In this project, the `build.gradle` signing setup is usually **already prepared**. After you create `android/key.properties`, you should be good to go.

If you still get signing errors (or if your `build.gradle` is different), make sure you have a `signingConfigs.release` configuration like this.

Open `android/app/build.gradle` and:

1. Load `key.properties`
2. Add `signingConfigs.release`
3. Attach it to `buildTypes.release`

Example configuration:

```gradle
// android/app/build.gradle

def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties')
if (keystorePropertiesFile.exists()) {
    keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}

android {
    // ... existing android config

    signingConfigs {
        release {
            keyAlias keystoreProperties['keyAlias']
            keyPassword keystoreProperties['keyPassword']
            storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
            storePassword keystoreProperties['storePassword']
        }
    }

    buildTypes {
        release {
            signingConfig signingConfigs.release
            // Optional (only if your project needs it):
            // minifyEnabled true
            // shrinkResources true
            // proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}
```

## 4) Get the **Release SHA1** (for Firebase / Google Sign-In)

If your app uses Google Sign-In / Firebase, you may need to register the **release SHA1** in Firebase.

Run:

```bash
keytool -list -v -keystore android/app/upload-keystore.jks -alias upload
```

Copy the **SHA1** value from the output, then add it in:

- Firebase Console → **Project settings** → **Your Android app** → **SHA certificate fingerprints**

Then re-download `google-services.json` and place it in:

- `android/app/google-services.json`

:::tip
You already have a debug SHA1 tutorial in [`docs/setup-google-signin/android-google-sign-in.md:1`](docs/setup-google-signin/android-google-sign-in.md:1). The command above is the same idea, but uses your **release keystore**.
:::

## 5) Build a release APK

```bash
flutter build apk --release
```

Output:

- `build/app/outputs/flutter-apk/app-release.apk`

## 6) Build a release App Bundle (AAB)

Google Play recommends App Bundles.

```bash
flutter build appbundle --release
```

Output:

- `build/app/outputs/bundle/release/app-release.aab`

## Common notes

- If you enabled Play App Signing, you may have:
  - **Upload key** (your keystore) for uploading builds
  - **App signing key** managed by Google Play
- Keep backups of:
  - `upload-keystore.jks`
  - the passwords / alias
  - `key.properties` values
