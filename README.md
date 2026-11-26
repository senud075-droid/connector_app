# Connector – simple messaging app (Flutter + Firebase)

## 1. Firebase setup (one time, in the browser)
1. https://console.firebase.google.com → Add project.
2. Project settings → Add app → **Android**. Package name: `com.example.connector_app`.
   Skip the "download google-services.json" step – not needed.
3. From Project settings → Your apps, note: **API key**, **App ID**,
   **Project ID**, **Project number** (= sender ID).
4. Build → Authentication → Sign-in method → enable **Phone**.
   Add a **test phone number** (e.g. +8801700000000, code 123456) to test without SMS.
5. Build → Firestore Database → Create database → then Rules tab →
   paste contents of `firestore.rules` → Publish.

## 2. GitHub
1. Create a new repository, upload ALL files of this folder (keep `.github/workflows/build.yml`).
2. Repo → Settings → Secrets and variables → Actions → New secret. Add 4 secrets:
   - `FIREBASE_API_KEY`
   - `FIREBASE_APP_ID`
   - `FIREBASE_SENDER_ID`  (project number)
   - `FIREBASE_PROJECT_ID`
3. Repo → Actions tab → "Build Android APK" → Run workflow.
4. When finished, open the run → Artifacts → download `connector-apk` → unzip → install `app-release.apk` on your phone.

## Notes
- If OTP fails on a real device with an "app verification" error, add your
  app's SHA-1 in Firebase → Project settings → your Android app.
- Photo sending (Firebase Storage) and group chat are not included yet.
