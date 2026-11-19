# Season Sorter (Android)

Signs in to Google Drive, lists your mp4 files, groups them by season, plays them, and moves them into
"Sorted Seasons / Season 01", "Season 02" … in My Drive.

- **TV season** mode reads S02E05, 2x05 or "Season 2" from the file name.
- **Time of year** mode groups by each file's modified date (Winter, Spring, Summer, Autumn).
- Files with no detectable season are never moved.

## Build it

1. Install Android Studio and open this folder (File > Open). Let Gradle sync.
2. Get your debug SHA-1: in Android Studio's terminal run
   `keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android`
   (on Windows the keystore is in `%USERPROFILE%\.android`).
3. In https://console.cloud.google.com : create a project, then
   - APIs & Services > Library > enable **Google Drive API**.
   - OAuth consent screen: User type External, add your own Google account under **Test users**,
     add the scope `.../auth/drive`.
   - Credentials > Create credentials > OAuth client ID > **Android**. Package name
     `com.example.seasonsorter`, paste the SHA-1. No ID needs copying into the code.
4. Plug in your phone (USB debugging on) and press Run, or Build > Build APK(s) and install the APK.

## Notes

- Google shows an "unverified app" warning because the app is in testing mode. Tap Advanced > continue.
  In testing mode Google may ask you to sign in again about once a week.
- The full `drive` scope is needed to move files you didn't create with this app.
- Changing the package name means updating it in the OAuth client too.
