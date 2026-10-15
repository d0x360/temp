Build & tooling

Changed Gradle to 8.2.1, then 8.9 — required for current Android Gradle Plugin

Changed Android Gradle Plugin to 8.1.4, then 8.7.3 — AGP 8 DSL (namespaces, packaging, lint)

Changed Kotlin to 1.7.22, then 1.9.22 — supports current libraries and removes deprecated plugins

Changed build JDK to 17 — required by AGP 8

Changed compileSdk 30 → 33 → 34 → 35 — matches newer AndroidX and targetSdk

Removed kotlin-android-extensions — plugin is discontinued; replaced synthetics with findViewById helpers

Added GitHub Actions workflow to build a debug APK on demand and upload it as an artifact

Updated CI actions to Node 24 majors (checkout, setup-java, setup-gradle, upload-artifact)

Android compatibility

Changed targetSdk 30 → 35 — app follows Android 15 rules

Added POST_NOTIFICATIONS request on Android 13+ — so the clipboard notification can show

Changed clipboard foreground service to specialUse type — required on Android 14+

Added android:exported and RECEIVER_NOT_EXPORTED where needed — required on Android 12+

Capped READ_EXTERNAL_STORAGE at API 32 — on 13+ files use content URIs

Opted out of edge-to-edge enforcement for now — keeps the existing layout until insets are handled

Libraries

Updated AndroidX, Material, and related support libraries — compatibility with compileSdk 34+

Updated Firebase BoM to 32.8.1 and FirebaseUI to 8.0.2 — current Firebase stack

Updated Hilt to 2.51.1 and ObjectBox to 4.0.3 — build and runtime compatibility

Updated Glide, OkHttp, Retrofit, Gson, jsoup, ZXing, Jackson — security and API fixes

Updated Play Billing 4.0.0 → 6.2.1 — old billing receiver broke launch on Android 14+ with targetSdk 35

Aligned androidx.lifecycle to 2.6.2 — fixed version clash after core/activity updates

Settings redesign

Changed settings into named sections (Copy Capture, Writing & Lists, Gestures, Look & Language, Privacy Lock, Floating Panel, Your Data, Help & About) — clearer layout

Made the sectioned settings list the default settings screen — drawer gear opens it instead of Runes

Added language, notification sound, link preview, and floating panel rows to Settings — same options, easier to find

Left preference keys unchanged — existing installs keep their settings

TESTING!
All features and functions, except for sync between the Windows app and the Android app, do work. That will be addressed shortly.

Compatibility tested on multiple Samsung Galaxy devices and various generations of Pixels.

App speed is significantly faster. There are less UI errors. Every function works as good or better than before.


