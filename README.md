# Clipto too

An unofficial community revival of the original **ClipTo Pro** Android clipboard manager, kept running on modern Android.

Based on Clipto 7.3.8 by Alex Trashler of Ukraine. Current version: **0.1.0-beta** (0.x betas until 1.0).

Clipto too installs alongside the original ClipTo Pro, so you can keep both. It works fully on your device. No account, no sign-in, and no limits.

## Testing

All features and functions, except for sync between the Windows app and the Android app, do work. That will be addressed shortly.

Compatibility tested on multiple Samsung Galaxy devices and various generations of Pixels.

App speed is significantly faster. There are fewer UI errors. Every function works as good or better than before.

## Highlights

- **No account needed.** Folders, snippet kits, attachments and every other on-device feature work without signing in.
- **No limits.** The free-tier note limit is gone, and clipboard history defaults to unlimited.
- **Original look restored.** The Default theme uses the original charcoal grey and amber again, and follows your phone's dark mode instantly.
- **Better floating panel.** Open it from Settings or the notification, collapse it like a shade, and it reliably reopens.
- **Working link tools.** Link previews, Shorten link and Play link work again, and Save to Internet Archive is new.
- **Fuller backups.** Folders are included, and there's an optional switch to include attachments.
- **New help pages** covering every feature, linked from Settings → Help & FAQ.
- **A cleaner Settings screen** with named sections, replacing the old Runes menu.

## Help

New help pages were written from scratch, because the original clipto.pro help site is gone. They cover getting started and clipboard capture, notes and organizing, the companion panel, snippets and kits, link actions, attachments, backup and restore, themes and passcode, and an FAQ. In the app, open Settings → Help & FAQ. The app's "Learn more" links also open the matching page.

## What's changed

### No account, no limits
- Folders work without signing in. They're stored on your device.
- Snippet kits are fully local. You can create, edit, use and install them without an account.
- Attachments work without an account. You can add files, take photos and record videos. They're stored privately on your device and can be viewed, opened, shared and deleted.
- Google Keep imports now bring their attachments along.
- The attachments filter works without an account.
- Removed the note limit. The free tier capped notes because the original servers cost money. Now everyone gets unlimited notes.
- Clipboard history defaults to unlimited on fresh installs. You can still set a cap in Settings.
- Removed the cap on how many notes you can select for bulk actions.

### Floating panel (keyboard companion)
- Added "Open panel" in Settings → Floating panel and as a button on the app's notification, so you don't need the accessibility button. If the accessibility service is off, both send you to Accessibility settings.
- Added a collapse button to the panel's top bar. It rolls the panel up so only the bar shows, and you can still drag it.
- Fixed the panel getting stuck after two windows opened at once, and not reopening after you close it.

### Links
- Fixed link previews. They now load straight from the web page instead of the old offline servers.
- Fixed "Shorten link". It now uses is.gd, with TinyURL as a backup.
- Added "Save to Internet Archive", which opens the Wayback Machine to save the note's link.
- "Play link" now hands the link to Android. Media links open in your default player, and anything else opens in the browser. The old built-in player hung on a black screen.

### Snippet kits
- Added "Export kit to file" on a kit's details screen.
- Added "Import snippet kit from file" in Settings → Your data.
- Hid kit public links, installing kits from links, and the public kit library, because they needed the old servers. The code is kept for later.

### Backup and restore
- Backups now include your folders and which folder each note belongs to. Restoring the same backup twice doesn't create duplicate folders.
- Added an "Include attachments" option to Backup, off by default. When it's on, the backup is a .zip that holds your notes and their files. Restore accepts both the .zip and the usual .json, and older backups still restore.
- Fixed the loading spinner that kept spinning forever after a restore.

### Appearance
- Fixed the Default theme showing OLED black with a blue accent in dark mode. The original charcoal grey and amber are back.
- Fixed the Default theme not switching when your phone changes dark mode while the app is open.
- Restored the yellow ClipTo logo in the side menu.
- Every action in a note's General tab now uses the same icon style.
- Fixed the version and "Based on" lines overlapping at the bottom of Settings.

### Settings redesign
- Settings are now in named sections: Copy Capture, Writing & Lists, Gestures, Look & Language, Privacy Lock, Floating Panel, Your Data, and Help & About. The sectioned list replaces the Runes screen as the main settings, and Runes is still available.
- Language, notification sound, link preview and floating panel options are easier to find.
- Existing installs keep their settings.

### Cleanup
- Removed dead links: the bottom of Settings (rate, feedback, translate, report an issue, FAQ, share, community, changelog, terms, privacy), the Settings three-dot menu (FAQ, Report an issue) and "App guide" in the side menu. They pointed to the original developer's offline site and accounts.

### App identity
- The app is named **Clipto too** and has its own app ID (`com.d0x360.cliptotoo`), so it installs alongside the original instead of replacing it.
- It has a distinct launcher icon, so the two are easy to tell apart.

### Android compatibility
- Updated targetSdk from 30 to 35, so the app follows Android 15 rules.
- On Android 13 and newer, the app asks for notification permission, so the clipboard notification can show.
- The clipboard foreground service uses the `specialUse` type, which Android 14 requires.
- Added the exported flags Android 12 requires on components and receivers.
- Limited storage permission to older Android versions. Android 13 and newer use content links.
- Opted out of edge-to-edge for now, which keeps the existing layout.

### Libraries
- Updated AndroidX, Material, Firebase (BoM 32.8.1), FirebaseUI 8.0.2, Hilt 2.51.1, ObjectBox 4.0.3, Glide, OkHttp, Retrofit, Gson, jsoup, ZXing and Jackson.
- Updated Play Billing from 4.0.0 to 6.2.1. The old billing code crashed the app at launch on Android 14 and newer.
- Pinned `androidx.lifecycle` to 2.6.2 to fix a launch crash caused by mismatched versions.

### Build and tooling
- Updated Gradle to 8.9, the Android Gradle Plugin to 8.7.3 and Kotlin to 1.9.22, and builds now use JDK 17.
- compileSdk went from 30 to 35.
- Replaced the discontinued `kotlin-android-extensions` with `findViewById` helpers.
- Added a GitHub Actions workflow that builds a debug APK on demand.

### Fixes
- Fixed three launch crashes on modern Android, caused by Play Billing, Crashlytics and the lifecycle library.
- Fixed a crash when opening the three-dot menu inside a note.
- Fixed "Attach a file", "Save as note" and "Save as file" doing nothing.

## Disabled for now

These features depended on the original Firebase servers, which are offline. They're hidden, and their code is kept so they can come back later:

- Sign-in and cloud sync, including Universal Clipboard and Universal Copy between your phone and PC
- Public links for notes and kits, and the public kit library
- Crashlytics crash reporting

## Known limitations

- There's no cloud sync. Use local backup and restore instead.
- Builds are debug-signed only. Release signing isn't set up yet.
- Edge-to-edge layout isn't fully handled yet.

## Build

Debug APKs are built with the GitHub Actions workflow **Android debug APK** (Actions → Run workflow).

To build locally with JDK 17:

```bash
./gradlew :app:assembleDebug
```

The APK is saved in `app/build/outputs/apk/debug/`.
