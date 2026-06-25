# 📚 RNCliStructure — Documentation

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Create Project](#create-project)
3. [Installation](#installation)
4. [Tech Stack](#tech-stack)
5. [Folder Structure](#folder-structure)
6. [Run on Android](#run-on-android)
7. [Run on iOS](#run-on-ios)
8. [Troubleshooting](#troubleshooting)

---

## Prerequisites

| Tool            | Version       | Purpose                        |
|----------------|---------------|-------------------------------|
| Node.js         | >= 22.11.0    | JavaScript runtime             |
| JDK             | 17            | Android builds                 |
| Xcode           | Latest        | iOS builds (macOS only)        |
| Android Studio  | Latest        | Android emulator & SDK         |
| CocoaPods       | Latest        | iOS dependency manager         |

```bash
# Install Watchman (macOS)
brew install watchman

# Install CocoaPods (macOS)
sudo gem install cocoapods

# Install JDK 17 (Android)
brew install --cask zulu@17
```

---

## Create Project

```bash
# Create a new React Native CLI project
npx @react-native-community/cli@latest init MyAppName

# Navigate into project
cd MyAppName

# Install iOS dependencies (macOS only)
bundle install
bundle exec pod install
```

---

## Installation

```bash
# Clone repo
git clone https://github.com/darshan8699/rn-cli-structure.git
cd rn-cli-structure

# Install JS dependencies
npm install

# iOS only — install native pods
bundle install
bundle exec pod install
```

---

## Tech Stack

| Library                              | Purpose                                  |
|-------------------------------------|------------------------------------------|
| `react-native` 0.86                  | Core framework                           |
| `@react-navigation/native`           | Navigation container                     |
| `@react-navigation/native-stack`     | Stack navigator (Auth flow)              |
| `@react-navigation/bottom-tabs`      | Bottom tab navigator (Main flow)         |
| `react-native-screens`               | Native screen optimization               |
| `react-native-gesture-handler`       | Gesture support for navigation           |
| `react-native-safe-area-context`     | Safe area insets                         |
| `@react-native-async-storage/async-storage` | Persistent key-value storage      |
| `react-native-mmkv`                  | High-performance synchronous storage     |
| `zustand`                            | Lightweight global state management      |
| `axios`                              | HTTP client with interceptor support     |
| `@tanstack/react-query`              | Server-state & async data fetching       |
| `react-native-vector-icons`          | Icon library for navigation & UI         |

---

## Folder Structure

```
rn-cli-structure/
├── App.tsx                         # Root component
├── index.js                        # App entry point
├── package.json
├── tsconfig.json
├── babel.config.js
├── metro.config.js
├── android/                        # Android native project
├── ios/                            # iOS native project
└── src/
    ├── apis/
    │   └── apiClient.ts            # Axios base instance with interceptors
    │
    ├── assets/                     # Static assets (fonts, images, etc.)
    │
    ├── common/
    │   ├── enums/
    │   │   ├── api.enum.ts         # API status enum (idle/loading/success/error)
    │   │   ├── gender.enum.ts      # Gender enum
    │   │   ├── storages.enum.ts    # Storage type enum (AsyncStorage / MMKV)
    │   │   └── theme.enum.ts       # Theme enum (light/dark/system)
    │   ├── theme/
    │   │   └── index.ts            # Colors, FontFamily, FontSize, Spacing, BorderRadius
    │   ├── types/
    │   │   └── index.ts            # Global TS types: User, ApiResponse, PaginatedResponse
    │   └── utils/
    │       ├── index.ts            # formatDate, capitalize, truncate, sleep, isDefined
    │       ├── delay.ts            # sleep/delay helper
    │       ├── json.ts             # JSON parse/stringify helpers
    │       ├── num.ts              # Number utilities
    │       └── promise.ts          # safePromise, promiseChain
    │
    ├── components/
    │   ├── common/
    │   │   ├── button/
    │   │   │   ├── button.tsx      # Reusable Button (primary/secondary/outline)
    │   │   │   ├── button.style.ts
    │   │   │   ├── button.type.ts
    │   │   │   └── button.test.tsx
    │   │   └── textinput/
    │   │       ├── textinput.tsx   # Reusable TextInput wrapper
    │   │       ├── textinput.style.ts
    │   │       ├── textinput.type.ts
    │   │       └── textinput.test.tsx
    │   └── modules/
    │       ├── account/
    │       │   ├── settings/       # Settings-specific components
    │       │   └── user-card/
    │       │       ├── user-card.tsx    # UserCard component
    │       │       ├── user-card.style.ts
    │       │       └── user-card.type.ts
    │       ├── auth/
    │       │   ├── components/     # Auth-specific UI components
    │       │   ├── hooks/
    │       │   │   ├── useAuthHandler.ts
    │       │   │   ├── useAuthTimeout.ts
    │       │   │   └── clearAuthData.ts
    │       │   ├── modals/         # Auth modals
    │       │   ├── requests/
    │       │   │   ├── refresh-token.request.ts
    │       │   │   └── token-exchange.request.ts
    │       │   └── stores/
    │       │       ├── auth.store.ts       # Zustand auth store
    │       │       ├── auth.provider.tsx   # Auth store provider
    │       │       ├── auth-error.map.ts   # Error message mapping
    │       │       └── index.ts
    │       └── home/
    │           └── home.tsx        # Home module component
    │
    ├── config/
    │   └── index.ts                # App-wide config (API URL, version, timeouts)
    │
    ├── data/
    │   ├── mock-users.data.ts      # Mock User[] data for development
    │   └── nav-menu-items.data.ts  # Bottom tab nav item definitions
    │
    ├── pages/
    │   ├── auth/
    │   │   ├── login/
    │   │   │   ├── login.tsx       # Login screen
    │   │   │   └── login.style.ts
    │   │   └── signup/
    │   │       ├── signup.tsx      # Signup screen
    │   │       └── signup.style.ts
    │   └── main/
    │       ├── home/
    │       │   ├── home.tsx        # Home screen (Dashboard)
    │       │   └── home.style.ts
    │       ├── account/
    │       │   ├── account.tsx     # Account/Profile screen
    │       │   └── account.style.ts
    │       └── setting/
    │           ├── setting.tsx     # Settings screen
    │           └── setting.style.ts
    │
    ├── services/
    │   ├── context/
    │   │   └── AuthContext.tsx     # React context for auth state
    │   ├── hooks/
    │   │   ├── useAuth.ts          # Login/logout hook using apiClient
    │   │   ├── use-effect-once.ts  # Run effect only on first mount
    │   │   └── use-platform-layout.ts
    │   ├── providers/
    │   │   └── AppProvider.tsx     # Wraps app with all context providers
    │   ├── redux/                  # (Reserved for Redux Toolkit if adopted)
    │   └── store/                  # (Reserved for additional stores)
    │
    └── shims/
        └── index.ts                # Polyfills (e.g. global.crypto for RN)
```

---

## Run on Android

> Requires Android Studio with an emulator running or a USB-connected device.

```bash
# Start Metro bundler
npm start

# Run on Android (new terminal)
npm run android

# Target a specific device
npx react-native run-android --deviceId <device-id>

# List connected devices
adb devices

# Port-forward for physical device
adb reverse tcp:8081 tcp:8081

# Release build
npx react-native run-android --mode=release
```

---

## Run on iOS

> macOS only. Requires Xcode installed.

```bash
# Start Metro bundler
npm start

# Run on iOS (new terminal)
npm run ios

# Target a specific simulator
npx react-native run-ios --simulator="iPhone 16 Pro"

# List available simulators
xcrun simctl list devices

# Release build
npx react-native run-ios --configuration Release
```

---

## Troubleshooting

```bash
# Clear Metro cache
npm start -- --reset-cache

# Kill Metro port
lsof -ti:8081 | xargs kill -9

# Clean Android build
cd android && ./gradlew clean && cd ..

# Clean iOS build
cd ios && xcodebuild clean && cd ..
bundle exec pod install

# Reset node_modules
rm -rf node_modules && npm install

# Re-install iOS pods from scratch
cd ios && pod deintegrate && pod install && cd ..

# MMKV / storage issues — wipe app data on emulator
adb shell pm clear com.rnclistructure
```
