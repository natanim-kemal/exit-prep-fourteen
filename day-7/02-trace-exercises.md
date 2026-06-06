# Day 7 — Mobile App Development Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: Android Architecture Trace

### Problem 1 — Layer Ordering
Put these Android architecture layers in order (bottom to top):
- [ ] Application Framework
- [ ] Libraries & Android Runtime
- [ ] Applications
- [ ] Linux Kernel

**Solution:** 1. Linux Kernel → 2. Libraries & Android Runtime → 3. Application Framework → 4. Applications

---

### Problem 2 — Lowest Layer
Which is the lowest layer of Android architecture?
a) Database
b) Application Framework
c) Linux Kernel
d) Application

**Solution:** c) Linux Kernel — it handles hardware abstraction, drivers, memory management, and security at the lowest level

---

## Set 2: Component Identification

### Problem 3 — Match Android Components
Match the component with its description:
1. Activity      a. Background processing without UI
2. Service       b. Responds to system-wide announcements
3. BroadcastReceiver  c. Manages shared app data
4. ContentProvider    d. Single screen with UI

**Solution:** 1-d, 2-a, 3-b, 4-c

---

### Problem 4 — Manifest Purpose
If a developer asks: "Where do I declare my app's permissions?"
**Solution:** `AndroidManifest.xml` — declares all app components, permissions, features, and minimum SDK

---

## Set 3: Activity Lifecycle Trace (Exam Priority!)

### Problem 5 — Lifecycle Order
```java
// User opens app for the first time
// Activity A starts
// Sequence of callbacks?
```

**Solution:**
1. `onCreate()` — Activity created, initialize
2. `onStart()` — Activity becomes visible
3. `onResume()` — Activity gains focus

---

### Problem 6 — Lifecycle — User Presses Home
```java
// Activity A is running (user is interacting)
// User presses the Home button
// Sequence of callbacks?
```

**Solution:**
1. `onPause()` — Activity losing focus
2. `onStop()` — Activity no longer visible

*(Not destroyed — can be resumed later)*

---

### Problem 7 — Lifecycle — User Returns
```java
// Activity A was stopped (user pressed Home)
// User opens app again
// Sequence of callbacks?
```

**Solution:**
1. `onRestart()` — Activity restarting
2. `onStart()` — Activity visible
3. `onResume()` — Activity in foreground

---

### Problem 8 — Rotation Trace
```java
// User is viewing Activity A in portrait
// User rotates phone to landscape
// Sequence of callbacks?
```

**Solution:**
1. `onPause()` — Activity pausing
2. `onStop()` — Activity stopping
3. `onDestroy()` — Activity destroyed
4. `onCreate()` — Activity recreated
5. `onStart()` — Activity visible
6. `onResume()` — Activity in foreground

(The activity is **destroyed and recreated** on configuration change by default)

---

### Problem 9 — Dialog Appears
```java
// Activity A is running
// A dialog appears (partially obscures the activity)
// Which callback is invoked?
```

**Solution:** `onPause()` — the activity is partially obscured (still visible but lost focus). If dialog covered full screen, it would go to `onStop()`.

---

## Set 4: Intent & Data Passing

### Problem 10 — Intent Trace
```java
// In Activity A:
Intent intent = new Intent(this, ProfileActivity.class);
intent.putExtra("userId", 42);
intent.putExtra("isAdmin", true);
startActivity(intent);
```

a) What type of intent is this?
b) How would ProfileActivity retrieve the data?

**Solution:**
a) **Explicit Intent** — specifies the exact component class (`ProfileActivity.class`)
b) In ProfileActivity:
```java
int userId = getIntent().getIntExtra("userId", 0);
boolean isAdmin = getIntent().getBooleanExtra("isAdmin", false);
```

---

### Problem 11 — Implicit vs Explicit
Classify each Intent as Explicit or Implicit:
a) `new Intent(this, SettingsActivity.class)`
b) `new Intent(Intent.ACTION_VIEW, Uri.parse("http://example.com"))`
c) `new Intent(Intent.ACTION_DIAL, Uri.parse("tel:123"))`
d) `new Intent(this, MainActivity.class)`

**Solution:**
a) Explicit — targets a specific class
b) Implicit — declares action; system chooses handler (browser)
c) Implicit — declares action; system chooses handler (phone dialer)
d) Explicit — targets a specific class

---

## Set 5: Layout & View Hierarchy

### Problem 12 — ViewGroup Hierarchy
```xml
<LinearLayout>           <!-- ViewGroup -->
    <TextView />         <!-- View -->
    <Button />           <!-- View -->
    <RelativeLayout>     <!-- ViewGroup (child of LinearLayout) -->
        <EditText />     <!-- View -->
    </RelativeLayout>
</LinearLayout>
```

What is the parent class of LinearLayout and RelativeLayout?

**Solution:** `android.view.ViewGroup` — both LinearLayout and RelativeLayout extend ViewGroup, which extends View

---

### Problem 13 — Not an Android Layout
Which is NOT a valid Android layout?
a) LinearLayout
b) FrameLayout
c) CardLayout
d) RelativeLayout

**Solution:** c) CardLayout — this is a Java Swing/AWT layout, not available in Android. (Note: `CardView` exists as a widget, not a layout type)

---

### Problem 14 — Layout Directory
Where should `activity_main.xml` be placed in an Android project?
a) `/src/activity_main.xml`
b) `/res/layout/activity_main.xml`
c) `/assets/activity_main.xml`
d) `/res/values/activity_main.xml`

**Solution:** b) `/res/layout/activity_main.xml`

---

## Set 6: Data Persistence

### Problem 15 — Right Tool for the Job
Which storage option fits each scenario?
1. Save user's font size preference → ________
2. Store a list of products for offline browsing → ________
3. Cache images downloaded from network → ________
4. Store user credentials securely → ________

**Solution:**
1. SharedPreferences (simple key-value pair)
2. SQLite / Room database (structured data with queries)
3. Internal file storage (cache directory)
4. EncryptedSharedPreferences / Android Keystore

---

### Problem 16 — SharedPreferences Example
```java
// Save user's name
SharedPreferences prefs = getSharedPreferences("MyPrefs", MODE_PRIVATE);
SharedPreferences.Editor editor = prefs.edit();
editor.putString("username", "Alice");
editor.apply();  // or editor.commit()
```
What happens with `apply()` vs `commit()`?

**Solution:**
- `apply()`: asynchronous (writes to memory immediately, disk later)
- `commit()`: synchronous (writes to disk immediately, returns boolean)

---

## Set 7: Multiple Choice Analysis

### Problem 17 — Identify Incorrect Statement
Which statement about APK is FALSE?
a) APK stands for Android Package Kit
b) APK contains compiled code and resources
c) APK stands for Android Phone Kit ← FALSE
d) APK files have .apk extension

---

### Problem 18 — Identify Correct Statement
Which statement about Activity is TRUE?
a) An Activity is a background service
b) An Activity is a single screen with UI
c) An Activity manages database operations
d) An Activity is the Android manifest file

**Solution:** b) An Activity is a single screen with UI

---

### Problem 19 — Security Analysis
An app stores user passwords in plain text in SharedPreferences. What security issue does this cause?

**Solution:**
- Violates OWASP Mobile Top 10 (insecure data storage)
- SharedPreferences are stored as XML files, readable by anyone with rooted device access
- Passwords should be hashed (bcrypt, PBKDF2) or stored using EncryptedSharedPreferences/Keystore
- Also violates ethical data protection principles

---

## Common Exam Traps — Mobile App Development

| Trap | Explanation |
|------|-------------|
| **APK meaning** | Android **Package** Kit, NOT Phone Kit or Platform Kit |
| **onCreate is FIRST** | First lifecycle callback, NOT onStart |
| **CardLayout** | NOT an Android layout (it's Java Swing) |
| **ViewGroup parent** | Layout classes extend `ViewGroup`, not `View`, `Layout`, or `Widget` |
| **Lowest layer** | Linux Kernel is lowest, NOT Application Framework |
| **Manifest content** | "All info about app" — not just layout or activity info |
| **Activity definition** | "A single screen with Java code" — NOT a configuration class |
| **Layout directory** | `/res/layout/` — NOT `/assets/`, `/src/`, or `/res/values/` |
| **Data persistence** | SharedPreferences for key-value — NOT MS SQL or MongoDB |
| **Intent purpose** | Pass data between activities — NOT ContentProvider or PostgreSQL |
| **Rotation** | Activity is DESTROYED and RECREATED on rotation |
| **apply vs commit** | `apply()` = async, `commit()` = sync |
| **Testing** | **All** options are valid (SDK emulator, third-party, physical device) |
