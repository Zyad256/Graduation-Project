# 🇨🇳⚔️ HanziHero

[![Flutter Version](https://img.shields.io/badge/flutter-v3.35.1-blue.svg)](https://flutter.dev)
[![Shorebird Enabled](https://img.shields.io/badge/OTA_updates-Shorebird-brightgreen.svg)](https://shorebird.dev)
[![Release](https://img.shields.io/badge/release-v1.1.0%2B3-orange.svg)](https://github.com/Zyad256/HanziHero/releases)

HanziHero is an immersive, gamified Chinese character (Hanzi) learning application built with Flutter. It blends retro RPG elements, interactive quest dialogue, spaced repetition (SRS), writing practice, and voice exercises to transform how you learn Chinese.

![HanziHero Banner](assets/images/readme_banner.png)

---

## 🏙️ Core Features

*   **🎮 Interactive RPG City (Zenith City)**: Built using the **Flame Game Engine**. Explore interactive districts (Old Town, Downtown), enter buildings, complete quests, and build relationships with virtual NPCs (such as the Librarian) who converse with you in Chinese.
*   **✍️ Writing & Stroke Order Practice**: Learn the correct stroke order for thousands of characters. Practice drawing directly on an interactive canvas with real-time feedback powered by `stroke_order_animator`.
*   **🗣️ Speech-to-Text & TTS**: Practice your spoken Chinese and pronunciation. The app uses Speech-to-Text (STT) for reading exercises and Text-to-Speech (TTS) for natural auditory learning.
*   **🗃️ Spaced Repetition System (SRS)**: Optimize your vocabulary retention with a local SQLite database powered by **Drift**, tracking your review schedules and progress.
*   **📊 Gamification & Stats**: Track your learning stats with interactive graphs (`fl_chart`), maintain daily login streaks, earn experience points (XP), level up, and unlock achievements.
*   **⚡ Shorebird OTA updates**: Never wait for App Store or Google Play Store reviews for critical bug fixes. The app checks for and downloads Shorebird patches over-the-air!

---

## 🛠️ Architecture & Tech Stack

HanziHero is designed with clean architecture principles, separating features, state management, and database layers:

*   **Framework**: [Flutter](https://flutter.dev) (Dart)
*   **Game Engine**: [Flame](https://flame-engine.org/)
*   **State Management**: [Riverpod & Riverpod Annotation](https://riverpod.dev)
*   **Routing**: [GoRouter](https://pub.dev/packages/go_router)
*   **Local Database**: [Drift (SQLite)](https://drift.simonbinder.eu/) for high-performance offline learning data
*   **Backend & Sync**: Firebase Auth, Cloud Firestore, Firebase Analytics, & Firebase Crashlytics
*   **OTA Updates**: [Shorebird](https://shorebird.dev)

---

## 🚀 Getting Started

### Prerequisites

*   Flutter SDK `v3.35.1` (or matching version)
*   Android Studio / Xcode (for emulation & compilation)
*   Firebase CLI (if setting up a new Firebase instance)
*   Shorebird CLI (for OTA features)

### Installation & Run

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/Zyad256/HanziHero.git
    cd HanziHero
    ```

2.  **Install dependencies**:
    ```bash
    flutter pub get
    ```

3.  **Run code generation**:
    Generate serialization models, Drift database classes, and Riverpod providers:
    ```bash
    dart run build_runner build --delete-conflicting-outputs
    ```

4.  **Run the application locally**:
    ```bash
    flutter run
    ```

---

## ⚡ Releases & Over-The-Air (OTA) Patches

HanziHero utilizes **Shorebird Code Push** to push minor hotfixes and features directly to users without needing to compile a new release build.

### Current Stable Release
The current stable build is **`v1.1.0+3`**. You can download the latest installation files from the **[GitHub Releases](https://github.com/Zyad256/HanziHero/releases)** tab:
*   `universal.apk`: Shorebird-enabled Android build.
*   `app-release.aab`: App Bundle for Google Play Store.

### Shorebird Deployment Workflow

To distribute updates to the app, use the following commands:

#### 1. Push a New Release Build
When making changes to native code (e.g., updating plugins or `AndroidManifest.xml`), you must push a new native release:
```bash
shorebird release android --flutter-version=3.35.1
```
*After creating a release, download the corresponding release APKs via `shorebird releases get-apks` and upload them to GitHub Releases.*

#### 2. Push a Hotfix Patch
For Dart-only changes (fixing bugs, updating UI, changing text), you can push an OTA patch:
```bash
shorebird patch android --flutter-version=3.35.1
```
The app will automatically download the patch in the background upon launch and notify the user to restart to apply the updates.
