# Mobile Application Development — Study Notes

## 1. Android Architecture

Android applications are built on a **Linux kernel** and run in the **Dalvik VM** (or ART runtime). Each app runs in its own process with a unique user ID for security isolation.

## 2. Android Application Components

1. **Activities**: represent a single screen with a user interface. Managed in an activity stack.
2. **Fragments**: reusable UI components within an activity. Modular pieces of the UI that can be combined.
3. **Services**: background processes that run without a UI (e.g., music playback, network operations).
4. **Broadcast Receivers**: respond to system-wide events (e.g., battery low, SMS received, boot completed).
5. **Content Providers**: manage access to structured data, enabling data sharing between apps.

## 3. Android Manifest

**AndroidManifest.xml**: declares app permissions, components, features, and minimum API level. Examples:
- Permissions: `ACCESS_FINE_LOCATION` (GPS), `CAMERA`, `INTERNET`, `READ_EXTERNAL_STORAGE`
- Declares all activities, services, broadcast receivers, content providers
- Specifies the launcher activity (main entry point with `MAIN`/`LAUNCHER` intent filter)

## 4. UI Components

- **Views**: basic UI building blocks (Button, TextView, EditText, ImageView)
- **ViewGroups**: containers that hold and arrange views (LinearLayout, RelativeLayout, ConstraintLayout, FrameLayout)
- **RecyclerView**: efficient scrolling list of items using view holder pattern
- **Intents**: messaging system for communication between components. Used to start activities, services, or send broadcasts.
- **Explicit Intent**: specifies the target component by class name
- **Implicit Intent**: specifies an action; system finds appropriate component

## 5. App Development Tools

**IDE**: Android Studio (official), built on IntelliJ IDEA. Includes:
- Layout editor (visual/XML)
- **Emulator**: virtual device for testing (simulates various screen sizes, API levels, hardware)
- **Physical device**: connect via USB for testing
- **APK Analyzer**, profiling tools, Logcat for debugging

## 6. Security in Mobile Apps

- **Data encryption**: encrypt sensitive data at rest (using Android Keystore) and in transit (TLS/SSL)
- **Permission model**: apps must request permissions at runtime (Android 6.0+) for dangerous permissions
- **Rooting/jailbreaking**: compromises device security; apps should detect and respond
- **Secure storage**: use EncryptedSharedPreferences or Android Keystore for sensitive data like tokens, passwords
- **Code obfuscation**: use ProGuard/R8 to prevent reverse engineering

## 7. Lifecycle

**Activity lifecycle**: `onCreate()` → `onStart()` → `onResume()` → `onPause()` → `onStop()` → `onDestroy()`. Also `onRestart()` → `onStart()`. Key: save state in `onSaveInstanceState()`, restore in `onCreate()`.

**Fragment lifecycle**: `onAttach()` → `onCreate()` → `onCreateView()` → `onActivityCreated()` → `onStart()` → `onResume()` → `onPause()` → `onStop()` → `onDestroyView()` → `onDestroy()` → `onDetach()`.
