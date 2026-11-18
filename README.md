<div>
    <img src="readmeAssets/noticeboard.svg" align=left height=40>
    <h1>Noticeboard Mobile App</h1>
</div>

<div>
    <img src="readmeAssets/ds1.png" width=85> &emsp;
    <img src="readmeAssets/ds2.png" width=85> &emsp;
    <img src="readmeAssets/ds3.png" width=85> &emsp;
    <img src="readmeAssets/ds4.png" width=85> &emsp;
    <img src="readmeAssets/ds5.png" width=85> &emsp;
    <img src="readmeAssets/ds6.png" width=85> &emsp;
    <img src="readmeAssets/ds7.png" width=85 height=178.256> &emsp;
</div>
</br>

## Download the app!
Click the below links to download.
- Android: https://play.google.com/store/apps/details?id=com.img.noticeboard
- iOS: https://apps.apple.com/in/app/channel-i-noticeboard/id6443708603

## About the app
The official digital noticeboard of IITR. Provides easy access to the Channel i notices, even from outside the campus or without intranet. You must have a Channel i account to use the app.

## Features
- View notices without having to open Channel i, just login and you are set!
- Get notified about the latest notices.
- A separate tab for the ever important placement and intern notices.
- Use that search bar or filter for more fine results.
- Bookmark notices on the go!
- Now after many demands from the iPhone users, noticeboard finally comes on the app store!

## Terms of Service
Terms to Service: https://docs.google.com/document/d/1vsbooZi9PIiVIMaLts2wv0tODEJafCaRT41zsENYN3I/edit

## Privacy Policy
Privacy Policy: https://docs.google.com/document/d/1IPibdlVJNO8IZVQqOjBk7m4mFRXOD8RJFvrlRAMeV3s/edit

## Tech Stack
- `Flutter` for app code.
- `Firebase` for notifications.

## Contributing
- Fork the repository to your account.
- Branch out to `a_meaningful_branch_name`.
- Commit your changes.
- Add your name to `CONTRIBUTORS.md`.
- File a `Pull request`.
- Get your pull request merged.

It's that simple!

## Credits
<img src=readmeAssets/img.svg>

## Updates by HUKA_Taro

> [!IMPORTANT]
> **Live Noticeboard push notifications are currently unavailable.** The app supports Firebase Cloud Messaging (FCM), and Channel i accepted the device token during testing. Channel i’s backend is currently not sending Noticeboard pushes for new or updated notices. Live alerts require a fix to the backend’s Firebase sending integration.

This version includes notification improvements and Android testing tools:

- Requests notification permission and registers the current Firebase Cloud Messaging (FCM) token with the backend.
- Listens for FCM token refreshes and attempts to register the replacement token.
- Displays incoming FCM notification messages while the Android app is open, using a high-importance notification channel. Banners and sound depend on Android notification settings.
- Adds **Test notification now** and **Test notification in 30 seconds** to the profile menu in Android debug builds.
- Schedules the delayed test using Android's alarm scheduler so it can fire after the app is removed from Recents. The test receiver and alarm permissions are declared only in the debug manifest.
- Updates the Android Gradle Plugin to 9.1.1 and limits Gradle memory and parallel workers for local builds on machines with limited available memory.

### Testing notifications

1. Install a debug build, sign in, and allow notification permission.
2. Tap your profile picture and choose **Test notification now** to check local notification display.
3. Choose **Test notification in 30 seconds**, then remove Noticeboard from Recents. Wait for the scheduled notification. Do not use Android's **Force stop**, which prevents this test from running until the app is reopened.

On a Pixel 7, Channel i accepted token registration with HTTP 201. The immediate and delayed debug notifications also appeared, including after removing the app from Recents. The debug buttons generate local notifications. Live Firebase delivery still needs to be tested once backend sending is restored.

To build an Android debug APK from the `noticeboard` directory:

```sh
flutter build apk --debug
```

The APK is written to `noticeboard/build/app/outputs/flutter-apk/app-debug.apk` relative to the repository root. The notification test menu is excluded from release builds.
