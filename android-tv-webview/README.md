# Android TV WebView App

This module contains a minimal Android TV application that opens a single website inside a full-screen WebView optimized for D-pad navigation. The target URL is injected at build time so you can point the APK at any site you want.

## Features
- Android TV launch intent with Leanback launcher category.
- D-pad/back navigation friendly WebView.
- JavaScript, DOM storage, and mixed-content enabled for compatibility.
- Cleartext traffic allowed (configure as needed for your site).

## Configure the target URL
The WebView loads the value of `BuildConfig.WEB_URL`. By default it is `https://movhub.ws/home`. Override it at build time:

```bash
./gradlew :app:assembleDebug -PwebUrl=https://your-site.example
```

You can also set `webUrl` in `~/.gradle/gradle.properties` or via Android Studio's Gradle properties when building a release APK.

## Build
1. Open the `android-tv-webview` directory in Android Studio (Giraffe or newer) or run Gradle from the command line.
2. Build a debug or release APK:
   - Debug: `./gradlew :app:assembleDebug`
   - Release: `./gradlew :app:assembleRelease`
3. The output APK will be under `app/build/outputs/apk/<variant>/`.

> Note: Gradle wrapper files are not included. Android Studio will generate them when you open the project, or you can add one with `gradle wrapper` if you prefer CLI builds.

## Installation on Android TV
1. Enable developer mode and network debugging on your Android TV device.
2. Install the APK via ADB:

```bash
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

3. Launch the app from the TV home screen; it will immediately open the configured website.
