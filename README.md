# TaskFlow

A mobile to-do app with Firebase-backed accounts and cross-device task sync.

## Overview

TaskFlow is a React Native (Expo) task/to-do management app. Users sign up and log in via Firebase Authentication, then create, edit, filter, and complete tasks that sync to the cloud so the same task list is available across devices. State is managed with Redux Toolkit, and tasks are also cached locally so the app stays usable offline.

## Problem it solves

Simple to-do apps often either lack accounts (so the list is stuck on one device) or require a heavy custom backend. TaskFlow keeps the task-management UX lightweight (add/edit/delete/filter tasks, due dates, search) while relying on Firebase for authentication and storage, so tasks persist per-user and sync across devices without the project needing to run its own server.

## Key features

- **Firebase-authenticated accounts** — sign up, sign in, and forgot-password flows backed by Firebase Auth (`Screens/AllScreens/Signin.js`, `Signup.js`, `ForgetPassword.js`)
- **Full task CRUD** — dedicated Add, Edit, and Task Details screens, plus an All Tasks view for browsing every task
- **Search and filtering** — `SearchBar` and `FilterChips`/`FilterModal` components for narrowing down the task list
- **Custom UI kit** — hand-built `Button`, `Input`, `CustomAlert`, `CustomHeader`, `CustomTabBar`, `EmptyState`, and `TaskCard` components rather than relying on a third-party UI library
- **Local caching for offline access** — tasks cached via `@react-native-async-storage/async-storage` alongside the Firebase sync
- **Redux-managed state** — `TodoSlice` and `loginSlice` (Redux Toolkit) drive task and auth state across the app
- **Settings screen** for account/app-level preferences

## What's unique about it

- **Hand-rolled component library instead of a UI framework**: every interactive element (buttons, inputs, tab bar, alerts, filter chips) is a custom component under `components/`, giving the app a consistent bespoke look rather than a stock Material/iOS design system.
- **Config-driven backend wiring**: Firebase setup is isolated in `services/Config.js`, keeping cloud credentials/config separate from the screen and Redux logic.

## Tech stack

- React Native 0.81 / React 19, via **Expo SDK 54**
- **Firebase** (Authentication + data storage)
- **Redux Toolkit / react-redux** for state management
- **React Navigation** (stack + bottom-tabs)
- **@react-native-async-storage/async-storage** for local/offline caching
- **@react-native-community/datetimepicker** for due-date selection
- **react-native-dropdown-select-list** for filter/select inputs

## Setup / running instructions

Requires Node.js and the Expo CLI toolchain, plus a Firebase project configured in `services/Config.js`.

```bash
npm install
npm start        # opens Expo dev tools / Metro bundler
npm run android   # run on Android emulator/device
npm run ios       # run on iOS simulator (macOS only)
npm run web       # run in a browser
```
