# Jazz Guitar Academy — Android APK kit

The `www/` folder contains the complete offline app (`index.html`), plus a web manifest,
service worker and icons so it also installs as an offline Progressive Web App (PWA).

## Option A — Build the APK on GitHub (nothing to install)
1. Create a new **empty** repository on github.com (e.g. `jazz-guitar-academy`).
2. Upload **all files of this kit** (keep the `.github` folder) — “Add file → Upload files”, or `git push`.
3. Open the repository’s **Actions** tab → “Build Android APK” runs automatically (or click *Run workflow*).
4. When it finishes (~5 min), open the run → **Artifacts** → download `JazzGuitarAcademy-apk` → unzip → `app-debug.apk`.
5. Copy the APK to your phone and open it (allow “Install unknown apps” for your file manager/browser).

## Option B — Build locally with Android Studio
```
npm install
npx cap add android
npx cap sync android
npx cap open android      # then Build ▸ Build APK(s)
```
Add `<uses-permission android:name="android.permission.RECORD_AUDIO"/>` to
`android/app/src/main/AndroidManifest.xml` for the Tuner and live Chord Recognition.

## Option C — Install as an offline web app (no APK)
Host the `www/` folder on any HTTPS host (e.g. GitHub Pages, Netlify, or a Lovable project),
open it in Chrome on Android → menu → **Install app**. It then works fully offline.
From a hosted URL you can also generate a signed APK/AAB at **pwabuilder.com**.

## Updating
The APK is signed with the key in `android-debug.keystore`, so every new build installs **over** the previous one (keeping your progress). Builds before version 2.0 used a random key: uninstall that old version once before installing 2.0.

Replace `www/index.html` with a newer version and push again — the workflow rebuilds the APK.

The debug APK is fine for personal use. For the Google Play Store, build a signed release
(Android Studio ▸ Build ▸ Generate Signed Bundle / APK).
