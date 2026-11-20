# Phishing Guard

Phishing Guard is an Android application that helps detect potentially malicious URLs in real time. It monitors visible links through an Android Accessibility Service, evaluates them using on-device machine learning, heuristic checks, and Google Safe Browsing, then alerts the user when a threat is detected.

> This project is intended for educational and research purposes. Phishing detection is not guaranteed to be completely accurate.

## Features

- Real-time URL detection from supported apps, including WhatsApp and Chrome
- Android Accessibility Service-based monitoring
- On-device phishing URL classification using ONNX Runtime
- Heuristic analysis for suspicious URL patterns
- Google Safe Browsing threat checks
- Threat alerts and notifications
- Local activity logs and URL blacklist
- Firebase Authentication with Google Sign-In
- Firestore-based cloud sync for user logs and statistics
- English, Hindi, and Tamil language support
- Settings, profile, and activity-log screens

## Tech Stack

- Java
- Android SDK
- Gradle
- Firebase Authentication
- Cloud Firestore
- Google Sign-In
- Google Safe Browsing API
- ONNX Runtime for Android
- SQLite

## Requirements

- Android Studio
- JDK 11
- Android SDK with API level 36
- An Android device or emulator running Android 6.0 (API 23) or later
- Firebase project
- Google Safe Browsing API key

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/PhishingGuard.git
   cd PhishingGuard
   ```

2. Open the project in Android Studio.

3. Create a Firebase project and add an Android app using this package name:

   ```text
   com.phishingprevention.app
   ```

4. Enable the following Firebase services:

   - Firebase Authentication
   - Google Sign-In provider
   - Cloud Firestore

5. Download the Firebase configuration file and place it here:

   ```text
   app/google-services.json
   ```

6. Create or update `local.properties` with your Android SDK path and Safe Browsing API key:

   ```properties
   sdk.dir=YOUR_ANDROID_SDK_PATH
   SAFE_BROWSING_API_KEY=YOUR_GOOGLE_SAFE_BROWSING_API_KEY
   ```

7. Build and run the app from Android Studio, or use:

   ```bash
   ./gradlew assembleDebug
   ```

   On Windows:

   ```powershell
   .\gradlew.bat assembleDebug
   ```

## Enable Protection

After signing in:

1. Open **Phishing Guard**.
2. Complete the onboarding steps.
3. Enable the app's Accessibility Service when prompted.
4. Allow notification permission when requested.
5. The app can then detect visible URLs and display alerts for suspicious links.

## Project Structure

```text
PhishingGuard/
├── app/
│   ├── google-services.json
│   └── src/main/
│       ├── assets/
│       │   ├── phishguard_model_final.onnx
│       │   └── phishguard_features_final.json
│       ├── java/com/phishingprevention/app/
│       │   ├── PhishingAccessibilityService.java
│       │   ├── PhishGuardModel.java
│       │   ├── SafeBrowsingChecker.java
│       │   ├── DatabaseHelper.java
│       │   └── MainActivity.java
│       └── res/
├── gradle/
├── build.gradle
├── gradle.properties
└── settings.gradle
```

## Security Notes

- Never commit `local.properties`.
- Never hard-code API keys in Java source files.
- Restrict the Google Safe Browsing API key to the required API and Android application.
- Use restrictive Firebase Authentication and Firestore security rules before deploying.
- `google-services.json` identifies the Firebase project; ensure related API keys are properly restricted.

## Permissions

Phishing Guard uses the following permissions:

- **Accessibility Service** — detects visible URLs for real-time analysis.
- **Internet** — performs Safe Browsing and Firebase requests.
- **Notifications** — displays phishing alerts.
- **Foreground service** — supports active monitoring.
- **Boot completed** — restores monitoring behavior after device restart.

## License

This project is for educational and research use. Add a license file before distributing or publishing the project publicly.
