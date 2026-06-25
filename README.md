# RNCliStructure

A production-ready **React Native CLI** project template with a scalable folder structure, state management, navigation, and typed API layer — ready to clone and build on.

> Built with React Native 0.86 · TypeScript · Zustand · React Query · React Navigation

---

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/darshan8699/rn-cli-structure.git
cd rn-cli-structure

# 2. Install dependencies
npm install

# 3a. Run on Android
npm run android

# 3b. Run on iOS (macOS only — install pods first)
bundle install && bundle exec pod install
npm run ios
```

---

## 🧱 Tech Stack

| Category           | Library                                              |
|-------------------|------------------------------------------------------|
| Framework          | `react-native` 0.86                                  |
| Language           | TypeScript                                           |
| Navigation         | `@react-navigation/native`, `native-stack`, `bottom-tabs` |
| State (global)     | `zustand`                                            |
| State (server)     | `@tanstack/react-query`                              |
| HTTP client        | `axios`                                              |
| Storage (async)    | `@react-native-async-storage/async-storage`          |
| Storage (fast)     | `react-native-mmkv`                                  |
| Icons              | `react-native-vector-icons`                          |
| Safe area          | `react-native-safe-area-context`                     |

---

## 📁 Folder Structure

```
src/
├── apis/               # Axios base client & interceptors
├── assets/             # Fonts, images, and other static files
├── common/
│   ├── enums/          # App-wide enums (API status, theme, storage, gender)
│   ├── theme/          # Colors, typography, spacing, border radius tokens
│   ├── types/          # Global TypeScript interfaces (User, ApiResponse…)
│   └── utils/          # Pure helper functions (formatDate, sleep, safePromise…)
├── components/
│   ├── common/         # Shared UI components (Button, TextInput)
│   └── modules/        # Feature-specific components, hooks, stores, requests
│       ├── auth/
│       ├── account/
│       └── home/
├── config/             # App-wide config values (API URL, version, timeouts)
├── data/               # Static mock data & nav menu item definitions
├── pages/
│   ├── auth/           # Login, Signup screens
│   └── main/           # Home, Account, Settings screens
├── services/
│   ├── context/        # React Context providers (AuthContext)
│   ├── hooks/          # Shared custom hooks (useAuth, useEffectOnce…)
│   ├── providers/      # AppProvider (wraps all context providers)
│   ├── redux/          # Reserved for Redux Toolkit (if adopted)
│   └── store/          # Reserved for additional Zustand stores
└── shims/              # Polyfills for React Native compatibility
```

For a detailed breakdown of every file, see [docs.md](./docs.md).

---

## 📜 Scripts

| Command              | Description                    |
|---------------------|-------------------------------|
| `npm start`          | Start Metro bundler            |
| `npm run android`    | Build & run on Android         |
| `npm run ios`        | Build & run on iOS             |
| `npm run lint`       | Run ESLint                     |
| `npm test`           | Run Jest unit tests            |

---

## ⚙️ Requirements

| Tool            | Version      |
|----------------|--------------|
| Node.js         | >= 22.11.0   |
| JDK             | 17           |
| Xcode           | Latest       |
| Android Studio  | Latest       |
| CocoaPods       | Latest       |

---

## 🔧 Troubleshooting

```bash
# Clear Metro cache
npm start -- --reset-cache

# Clean Android build
cd android && ./gradlew clean && cd ..

# Re-install iOS pods
cd ios && pod deintegrate && pod install && cd ..

# Reset node_modules
rm -rf node_modules && npm install
```

See [docs.md](./docs.md) for more detailed troubleshooting steps.

---

## 📖 Learn More

- [React Native Docs](https://reactnative.dev/docs/getting-started)
- [React Navigation](https://reactnavigation.org)
- [Zustand](https://zustand-demo.pmnd.rs)
- [TanStack Query](https://tanstack.com/query/latest)
- [React Native MMKV](https://github.com/mrousavy/react-native-mmkv)
