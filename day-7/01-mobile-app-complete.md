# Day 7 — Mobile Application Development Complete Theory (6 Items)

## LO1: Basic Components of Android & Mobile Computing (2 items)

### 1.1 Android Architecture (4 layers — bottom to top)
```
┌─────────────────────────────────────┐
│         Application Layer           │ ← Apps (Phone, Browser, Your App)
├─────────────────────────────────────┤
│       Application Framework         │ ← Activity Manager, Content Providers,
│                                     │   Notification Manager, Resource Manager
├─────────────────────────────────────┤
│         Libraries & Android Runtime  │ ← SQLite, WebKit, Media, OpenGL
│                                     │   Dalvik/ART (runtime)
├─────────────────────────────────────┤
│         Linux Kernel (Lowest)       │ ← Drivers, Memory, Process, Power
└─────────────────────────────────────┘
```
- **Lowest layer**: Linux Kernel (hardware abstraction, drivers, security)
- **Middle layer**: Libraries + Android Runtime (ART/Dalvik)
- **Upper layer**: Application Framework (Activity Manager, Content Providers, etc.)
- **Top layer**: Applications

### 1.2 APK (Android Package Kit)
- **APK** = Android Package Kit — the package file format for Android apps
- Contains compiled code (DEX), resources, manifest, assets
- Extension: `.apk`
- **Not** "Android Phone Kit", "Android Platform Kit", or "Android Page Kit"

### 1.3 Manifest (AndroidManifest.xml)
- **All info about the app**: package name, components (activities, services, receivers), permissions, min SDK version
- Located at root of the project
- Declares every component, required permissions, hardware features
- **Not just** "layout info" or "activity info" — it's the complete app descriptor

### 1.4 Activity Definition
- **Activity** = **a single screen with Java/Kotlin code**
- Each activity has a window (usually full screen)
- Examples: MainActivity, LoginActivity, SettingsActivity
- **Not**: "Android class to configure app", "package file", or "intent"

### 1.5 Android App Components (4 core components)
| Component | Purpose |
|-----------|---------|
| **Activity** | Single screen UI |
| **Service** | Background processing (no UI) |
| **BroadcastReceiver** | Responds to system-wide broadcasts (battery low, boot complete) |
| **ContentProvider** | Manages shared app data (contacts, media) |

### 1.6 Layouts
- XML layout files stored in: **`/res/layout/`** directory
- **Not**: `/assets`, `/src`, `/res/values`

**Layout classes** are subclasses of **`android.view.ViewGroup`**
- ViewGroup = invisible container holding Views and other ViewGroups
- Layout types:
  - **LinearLayout**: arranges children in single row/column
  - **RelativeLayout**: positions children relative to each other/parent
  - **FrameLayout**: stacks children (top-left by default)
  - **ConstraintLayout**: flexible, flat hierarchy with constraints
  - **CardLayout** — **NOT an Android layout** (it's a Java Swing layout)
- **View** = individual UI widget (Button, TextView, ImageView)

---

## LO2: IDE Skills & Development (Part of 4 items)

### 2.1 Activity Lifecycle (Exam Priority!)
```
onCreate()   ← FIRST callback (when activity is created)
    ↓
onStart()    ← activity becomes visible
    ↓
onResume()   ← activity gains focus (user can interact)
    ↓
onPause()    ← activity partially obscured (e.g., dialog appears)
    ↓
onStop()     ← activity no longer visible
    ↓
onDestroy()  ← activity destroyed
```

**Key rule**: `onCreate()` is the **first callback method invoked** during activity lifecycle.

Full lifecycle order:
1. **onCreate()** — First! Initialize, setContentView, bind data
2. onStart() — Activity visible
3. onResume() — Activity in foreground, interactive
4. onPause() — Activity losing focus (save state here)
5. onStop() — Activity hidden
6. onDestroy() — Activity finishing

**Rotation cycle** (portrait ↔ landscape):
```
onPause() → onStop() → onDestroy() → onCreate() → onStart() → onResume()
```
(The activity is destroyed and recreated on rotation!)

### 2.2 Intents — Passing Data Between Activities
- **Intent** = messaging object for communication between components
- Used to: start activities, start services, deliver broadcasts
- **Explicit Intent**: specifies exact component class name
- **Implicit Intent**: declares action, system finds appropriate component

```java
// Explicit: Start SecondActivity
Intent intent = new Intent(this, SecondActivity.class);
intent.putExtra("key", "value");  // pass data
startActivity(intent);

// In SecondActivity:
String data = getIntent().getStringExtra("key");
```

**Not**: ContentProvider, BroadcastReceiver, or PostgreSQL

### 2.3 Data Persistence on Android
- **SharedPreferences**: key-value pairs for simple data (settings, preferences)
- SQLite database (via Room or raw SQLite)
- Internal/External file storage
- Firebase/Firestore (cloud)
- **Not**: MS SQL Client, MongoDB (too heavy for mobile)

### 2.4 Testing Android Apps
- **Emulator in Android SDK** (part of Android Studio)
- Physical device (USB debugging)
- Third-party emulators (Genymotion)
- **All of these** are valid testing options

### 2.5 Views
- **View** = displays part of an activity on screen
- All UI widgets are subclasses of `android.view.View`
- ViewGroup extends View (contains children)
- Each activity's UI is a tree of Views and ViewGroups

### 2.6 Project Structure
```
MyApp/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/          ← source code
│   │   │   ├── res/
│   │   │   │   ├── layout/    ← XML layout files
│   │   │   │   ├── values/    ← strings, colors, themes
│   │   │   │   ├── drawable/  ← images, icons
│   │   │   │   └── ...
│   │   │   └── AndroidManifest.xml
│   │   └── test/              ← unit tests
│   └── build.gradle
├── build.gradle
└── settings.gradle
```

---

## LO3: Security Concerns (Part of remaining items)

### 3.1 Mobile Security Risks
- **OWASP Mobile Top 10**: Improper platform usage, insecure data storage, insecure communication, insecure authentication, insufficient cryptography, insecure authorization, client code quality, code tampering, reverse engineering, extraneous functionality
- **Data at rest**: encrypt sensitive data stored on device
- **Data in transit**: use HTTPS/TLS, certificate pinning
- **Authentication**: biometric, OAuth, token-based
- **Side-loading risk**: installing APKs from unknown sources

### 3.2 Android Permissions
- **Normal permissions**: granted automatically (INTERNET)
- **Dangerous permissions**: user must approve (CAMERA, LOCATION, READ_CONTACTS)
- **Runtime permission model** (Android 6.0+): request at time of use
- Declared in `AndroidManifest.xml`

---

## LO4: Legal & Ethical Principles (Part of remaining items)

### 4.1 Ethical Mobile Development
- **Privacy by Design**: minimize data collection, be transparent
- **GDPR compliance**: user consent, right to delete data
- **Accessibility**: support screen readers, sufficient contrast, touch targets
- **App store guidelines**: no deceptive behavior, respect user privacy
- **Informed consent**: explain what data is collected and why

### 4.2 Common Ethical Issues
- Over-collection of user data
- Hidden tracking/analytics
- Dark patterns (tricking users)
- Battery/memory abuse
- Unsecured data storage leading to breaches

---

## Exam-Style Q&A (From Actual Model Exams)

**Q1:** APK stands for?
- a. Android Phone Kit
- b. Android Platform Kit
- c. **Android Package Kit** ✓
- d. Android Page Kit

**Q2:** What is an Activity in Android?
- a. Android class to configure app
- b. Package file holding packages
- c. **A single screen with Java code** ✓
- d. None of the above

**Q3:** Layout classes are subclasses of?
- a. android.view.Widget
- b. android.view.Layout
- c. android.view.RelativeLayout
- d. **android.view.ViewGroup** ✓

**Q4:** The lowest layer of Android architecture is?
- a. Database
- b. Application Framework
- c. Application
- d. **Linux Kernel** ✓

**Q5:** First callback method invoked during the activity lifecycle?
- a. onStart()
- b. onClick()
- c. **onCreate()** ✓
- d. onRestart()

**Q6:** Which can be used to persist data in Android?
- a. MS SQL Client
- b. **SharedPreferences** ✓
- c. MongoDB
- d. PostgreSQL

**Q7:** How to pass data between activities?
- a. Content Provider
- b. Broadcast Receiver
- c. **Intent** ✓
- d. PostgreSQL

**Q8:** Where are XML layout files stored?
- a. /assets
- b. /src
- c. /res/values
- d. **/res/layout** ✓

**Q9:** What is Manifest.xml?
- a. Layout info
- b. Activity info
- c. **All info about the app** ✓
- d. None

**Q10:** Which Android component displays part of an activity on screen?
- a. **View** ✓
- b. Manifest
- c. Intent
- d. Fragment

**Q11:** Which is **NOT** among the layouts available in Android?
- a. Relative Layout
- b. Frame Layout
- c. **Card Layout** ✓
- d. Linear Layout

**Q12:** Where can developers test Android apps during development?
- a. Third-party emulators
- b. Emulator in Android SDK
- c. Physical phone
- d. **All of the above** ✓

---

---

## Question Bank Study Notes

### Android Components
**Activity**: single screen. **Fragment**: reusable UI within activity. **Service**: background processing. **Broadcast Receiver**: respond to system events. **Content Provider**: share data between apps.

### Manifest & UI
**AndroidManifest.xml**: declares permissions (GPS, Camera, Storage), components, intents. **Views**: Button, TextView. **ViewGroups**: LinearLayout, RelativeLayout. **RecyclerView**: efficient scrolling lists. **Intents**: messaging between components (explicit = by class, implicit = by action).

### Lifecycle & Security
Activity: onCreate → onStart → onResume → onPause → onStop → onDestroy. Emulator = virtual device for testing. Security: encrypt data, permission model (runtime), use Android Keystore.


## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Android components & mobile computing | 2 | 1 Rem, 1 Und |
| 2 | IDE skills & development | 4 | 2 Und, 2 App |
| 3 | Security concerns | 3 | 1 App, 1 Ana, 1 Eva |
| 4 | Legal & ethical principles | 3 | 1 App, 1 Ana, 1 Eva |
| **Total** | | **6** *(LO totals may overlap)* | |
