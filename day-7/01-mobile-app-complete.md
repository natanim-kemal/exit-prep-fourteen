# Day 7 — Mobile Application Development (78 Items)

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

## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Android components & mobile computing | 2 | 1 Rem, 1 Und |
| 2 | IDE skills & development | 4 | 2 Und, 2 App |
| 3 | Security concerns | 3 | 1 App, 1 Ana, 1 Eva |
| 4 | Legal & ethical principles | 3 | 1 App, 1 Ana, 1 Eva |
| **Total** | | **6** *(LO totals may overlap)* | |


## Practice Questions (from Question Bank)

Answer: A
### Q464. Android method called when activity becomes visible?

- A) onResume
- B) onRestart
- C) onCreate
- D) onStart
  **Answer: D**

### Q465. Consider a system where androidManifest.xml declares?

- A) Key-value pairs
- B) UI layout
- C) DB schema
- D) App components, permissio
  **Answer: D**

### Q466. Background component with no UI in Android?

- A) Service
- B) ContentProvider
- C) Activity
- D) Fragment
  **Answer: A**

### Q467. MVVM in Android uses ViewModel and?

- A) SharedPreferences
- B) LiveData
- C) Intent
- D) SQLite
  **Answer: B**

### Q468. When designing for high performance, why not store sensitive data in SharedPreferences?

- A) Stores as plaintext
- B) Deleted on update
- C) Doesn't support strings
- D) Too slow
  **Answer: A**

### Q469. Certificate pinning prevents?

- A) DDoS attacks
- B) XSS attacks
- C) Man-in-the-Middle attacks
- D) SQL injection
  **Answer: C**

### Q470. Most flexible Android layout avoiding nesting?

- A) FrameLayout
- B) RelativeLayout
- C) ConstraintLayout
- D) LinearLayout
  **Answer: C**

### Q471. In a resource-constrained environment, intent in Android is?

- A) DB manager
- B) Background thread
- C) Messaging object to
- D) Layout definition
  **Answer: C**

### Q472. Explicit vs Implicit Intent?

- A) Explicit names target
- B) Implicit names target
- C) Explicit for Services only
- D) No difference
  **Answer: A**

### Q473. Android Activity lifecycle first method called?

- A) onResume
- B) onCreate
- C) onStart
- D) onBind
  **Answer: B**

### Q474. When designing for high performance, identify the correct statement about Fragment in Android.

- A) Background service
- B) Data access layer
- C) Reusable UI portion that
- D) Intent type
  **Answer: C**

### Q475. What is the primary function of is?

- A) Playing media
- B) Efficiently displaying
- C) Displaying images
- D) Handling permissions
  **Answer: B**

### Q476. Which description of Room library in Android is accurate?

- A) UI component library
- B) Dependency injection
- C) Networking library
- D) Abstraction layer over
  **Answer: D**

### Q477. Consider a system where identify the correct statement about BroadcastReceiver.

- A) Manages audio output
- B) Receives network data
- C) Listens for system-wide events
- D) Sends broadcasts to external apps
  **Answer: C**

### Q478. Identify the correct statement about ContentProvider used for.

- A) Providing UI layouts
- B) Sharing data between apps using URI
- C) Providing network access
- D) Managing app lifecycle
  **Answer: B**

### Q479. Android runtime permissions (Android 6+) require?

- A) Only manifest declaration
- B) Root access
- C) App restart to grant
- D) Explicit user approval at
  **Answer: D**

### Q480. In a resource-constrained environment, what does ProGuard/R8 do in Android?

- A) Manages dependencies
- B) Obfuscates/shrinks code to
- C) Compresses images
- D) Encrypts SharedPreferences
  **Answer: B**

### Q481. Which description of purpose of ViewModel in MVVM is accurate?

- A) Hold and manage UI-related
- B) Handle network calls
- C) Render UI components
- D) Store files on disk
  **Answer: A**

### Q482. LiveData in Android is?

- A) Thread manager
- B) Observable data holder
- C) JSON parser
- D) Real-time database
  **Answer: B**

### Q483. Identify the correct statement about Kotlin primarily used for in Android.

- A) Database queries
- B) CSS-like styling
- C) Primary language for
- D) Backend services only
  **Answer: C**

### Q484. Which description of difference between Activity and Fragment is accurate?

- A) Fragment has full screen
- B) No difference
- C) Activity is a full screen with
- D) Fragments run in background
  **Answer: C**

### Q485. Which of the following best describes APK?

- A) Android Program Kit
- B) App Permission Key
- C) Application Programming Kit
- D) Android Package Kit
  **Answer: D**

### Q486. Identify the correct statement about purpose of AndroidManifest permissions.

- A) Declare what sensitive
- B) Style the app
- C) Define UI layouts
- D) Configure database
  **Answer: A**

### Q487. Which description of Retrofit in Android is accurate?

- A) UI component
- B) Image loader
- C) Database ORM
- D) HTTP client library for
  **Answer: D**

### Q488. Identify the correct statement about Glide/Picasso used for in Android.

- A) Efficient image loading
- B) Network requests
- C) JSON parsing
- D) Database management
  **Answer: A**

### Q489. Which description of dependency injection in Android context is accurate?

- A) Injecting SQL
- B) Adding libraries manually
- C) Injecting UI layouts
- D) Providing objects a class
  **Answer: D**

### Q490. Identify the correct statement about Hilt in Android.

- A) UI framework
- B) Dependency injection
- C) Testing framework
- D) Database library
  **Answer: B**

### Q491. EncryptedSharedPreferences is preferred over SharedPreferences because?

- A) Supports more data types
- B) Syncs to cloud
- C) Encrypts stored data
- D) Faster access
  **Answer: C**

### Q492. In a resource-constrained environment, what is the primary function of is?

- A) Securely storing cryptographic
- B) Storing app keys in Play Store
- C) App signing for release
- D) Encrypting APK files
  **Answer: A**

### Q493. Identify the correct statement about onPause() lifecycle method for.

- A) Activity fully invisible
- B) Activity partially obscured
- C) Activity first created
- D) Activity destroyed
  **Answer: B**

### Q494. Which of the following best describes onDestroy() called for?

- A) App installed
- B) Activity being destroyed
- C) Screen rotated always
- D) App backgrounded
  **Answer: B**

### Q495. Which of the following best describes back stack in Android?

- A) Network request queue
- B) Stack of downloaded files
- C) Stack of Activities that user
- D) Database transaction log
  **Answer: C**

### Q496. Identify the correct statement about purpose of onSaveInstanceState().

- A) Save app to SD card
- B) Save user preferences
- C) Save database
- D) Save UI state before
  **Answer: D**

### Q497. What does 'implicit intent' allow?

- A) Accessing system databases
- B) Starting components in other apps
- C) Running background services
- D) Starting only your app's activities
  **Answer: B**

### Q498. In a resource-constrained environment, which description of minSdkVersion in manifest is accurate?

- A) Minimum storage needed
- B) Minimum Android API level
- C) Minimum RAM required
- D) Minimum app size
  **Answer: B**

### Q499. Identify the correct statement about targetSdkVersion.

- A) API level app is designed and
- B) Maximum supported version
- C) Minimum version
- D) Version app was tested against
  **Answer: A**

### Q500. Identify the correct statement about Gradle in Android development.

- A) Version control system
- B) Emulator manager
- C) Build automation tool
- D) UI design tool
  **Answer: C**

### Q501. Which of the following best describes purpose of build.gradle file?

- A) Configures build
- B) Manages permissions
- C) Defines UI layouts
- D) Stores user data
  **Answer: A**

### Q502. Identify the correct statement about n Android emulator.

- A) Software simulating Android
- B) APK compression tool
- C) Performance profiler
- D) Physical test device
  **Answer: A**

### Q503. Which description of ADB (Android Debug Bridge) is accurate?

- A) Application Debug Bundle
- B) Command-line tool for
- C) App Distribution Build
- D) Android Database Backend
  **Answer: B**

### Q504. In a resource-constrained environment, what does WCAG stand for in mobile accessibility?

- A) Web Content Accessibility Guidelines
- B) Wireless Content Accessibility Group
- C) Web Component Application Guide
- D) Worldwide Content Access Guidelines
  **Answer: A**

### Q505. Identify the correct statement about GDPR relevance to mobile apps.

- A) GPU driver regulation
- B) Data protection law requiring
- C) Graphics rendering standard
- D) Google Play review requirement
  **Answer: B**

### Q506. Which description of multi-threading in Android used for is accurate?

- A) Managing multiple databases
- B) Handling multiple users
- C) Running operations off main
- D) Rendering multiple screens
  **Answer: C**

### Q507. Which description of AsyncTask (deprecated) / Coroutines used for in Android is accurate?

- A) Database schema migration
- B) UI animation
- C) Manifest declaration
- D) Performing background
  **Answer: D**

### Q508. Which of the following best describes Coroutine in Kotlin/Android?

- A) Lightweight concurrency
- B) A UI component
- C) Database query type
- D) Layout manager
  **Answer: A**

### Q509. Which of the following best describes purpose of a RecyclerView adapter?

- A) Binds data to views and
- B) Manages database access
- C) Converts data types
- D) Handles user clicks
  **Answer: A**

### Q510. Which of the following best describes LiveData's advantage over regular data?

- A) Lifecycle-aware: only
- B) Faster
- C) Persistent
- D) Encrypted
  **Answer: A**

### Q511. Identify the correct statement about Navigation Component in Android.

- A) Map rendering engine
- B) Framework for managing
- C) HTTP routing library
- D) GPS library
  **Answer: B**

### Q512. Which of the following best describes purpose of ConstraintLayout flat view hierarchy?

- A) Supports more widget types
- B) Reduces nested layouts
- C) Enables 3D effects
- D) Better animations
  **Answer: B**

### Q513. Which description of ProGuard's role in release builds is accurate?

- A) Manages permissions
- B) Compresses images
- C) Signs the APK
- D) Shrinks and other mechanisms
  **Answer: D**

### Q514. Which description of content URI in Android is accurate?

- A) Deep link URL
- B) Image resource path
- C) Website URL
- D) Unique identifier for
  **Answer: D**

### Q515. Which description of purpose of the Google Play Developer Policy is accurate?

- A) SDK installation guide
- B) Hardware requirements
- C) Rules apps must follow to be
- D) Kotlin coding standards
  **Answer: C**

### Q516. Which of the following best describes deep linking in Android?

- A) URL that opens specific
- B) Database nested queries
- C) Nested fragment navigation
- D) Network tunneling
  **Answer: A**

### Q517. Which description of difference between permissions at install time vs runtime is accurate?

- A) Runtime requires explicit approval for
- B) No difference in Android 6+
- C) Install-time is more restrictive
- D) Runtime permissions are permanent
  **Answer: A**

### Q518. Identify the correct statement about n activity's 'task' in Android.

- A) Background thread
- B) Stack of activities user
- C) Scheduled job
- D) Gradle build task
  **Answer: D**

### Q519. In a resource-constrained environment, what happens when device rotates in Android by default?

- A) Nothing
- B) App crashes
- C) Fragment is destroyed only
- D) Activity is recreated
  **Answer: D**

### Q520. Identify the correct statement about ViewBinding in Android.

- A) MVVM binding
- B) Data binding to server
- C) Type-safe way to
- D) XML layout parser
  **Answer: C**

### Q521. Which of the following best describes DataBinding in Android?

- A) Database ORM
- B) Network data parser
- C) Framework binding UI
- D) SharedPreferences wrapper
  **Answer: C**

### Q522. Identify the correct statement about WorkManager used for in Android.

- A) Scheduling deferrable
- B) Coroutine management
- C) UI work scheduling
- D) Managing worker threads
  **Answer: A**

### Q523. Identify the correct statement about purpose of onResume() lifecycle method.

- A) First creation of activity
- B) Activity foregrounded and
- C) Activity hidden completely
- D) Activity being destroyed
  **Answer: B**

### Q524. Identify the correct statement about purpose of onStop() lifecycle method.

- A) Activity no longer visible to user
- B) Activity receiving focus
- C) Activity partially visible
- D) Activity being created
  **Answer: A**

### Q525. Identify the correct statement about n Intent filter in Android.

- A) Declares what implicit
- B) Validates intent data
- C) Blocks certain intents
- D) Filters log messages
  **Answer: A**

### Q526. Identify the correct statement about Pending Intent.

- A) Cancelled intent
- B) Intent waiting for network
- C) Deferred intent allowing
- D) Broadcast intent only
  **Answer: C**

### Q527. Which of the following best describes Jetpack Compose?

- A) Testing framework
- B) Dependency injection
- C) Modern declarative UI
- D) Gradle plugin
  **Answer: C**

### Q528. Which description of difference between Serializable and Parcelable in Android is accurate?

- A) Serializable is faster on Android
- B) No difference
- C) Parcelable is Android-specific and more
- D) Only Serializable works with Intents
  **Answer: C**

### Q529. Identify the correct statement about Material Design.

- A) CSS framework for Android
- B) Android hardware standard
- C) XML layout language
- D) Google's design system for
  **Answer: D**

### Q530. Identify the correct statement about purpose of a SplashScreen.

- A) Crash recovery screen
- B) Login screen
- C) Initial branding screen
- D) Error display screen
  **Answer: C**

### Q531. Identify the correct statement about memory leak risk in Android context.

- A) Too many threads
- B) Holding reference to
- C) Using too much CPU
- D) Large images
  **Answer: B**

### Q532. Which description of purpose of FLAG_ACTIVITY_NEW_TASK in Intent is accurate?

- A) Clears back stack
- B) Creates new instance always
- C) Starts activity in new task
- D) Sends broadcast
  **Answer: C**

### Q533. What does 'clear top' flag do in Activity navigation?

- A) Creates new task
- B) Clears screen
- C) Closes current activity
- D) Clears activities above
  **Answer: D**

### Q534. Identify the correct statement about use of SharedViewModel in MVVM.

- A) Shared database connection
- B) Shares data between multiple
- C) Shared network client
- D) Shared preferences manager
  **Answer: B**

### Q535. Identify the correct statement about Service's started vs bound type.

- A) Both always run in background
- B) Started runs independently
- C) No difference
- D) Bound runs independently
  **Answer: B**

### Q536. Which of the following best describes role of onCreate() in a Service?

- A) Called every time service starts
- B) Called once when service is first created
- C) Called when service stops
- D) Called when service is bound
  **Answer: B**

### Q537. Identify the correct statement about Foreground Service in Android.

- A) Service with highest priority thread
- B) Service running with visible
- C) Service bound to Activity
- D) Service running in UI thread
  **Answer: B**

### Q538. Which of the following best describes Android's permission group concept?

- A) Grouping apps by permission
- B) Permissions shared between apps
- C) Related permissions grouped so user
- D) Restricting permissions by group policy
  **Answer: C**

### Q539. Which of the following best describes purpose of FLAG_SECURE in Android?

- A) Enables HTTPS
- B) Prevents screenshots and
- C) Enables biometric auth
- D) Secures SQLite database
  **Answer: B**

### Q540. Which description of role of content resolver in Android is accurate?

- A) Client-side interface for
- B) Resolves IP addresses
- C) Handles DNS for app
- D) Resolves intent conflicts
  **Answer: A**

### Q541. Which of the following best describes JobScheduler in Android used for?

- A) Scheduling UI updates
- B) Managing Gradle tasks
- C) Scheduling jobs to run under
- D) Background animations
