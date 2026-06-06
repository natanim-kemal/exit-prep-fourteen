# Day 7 — Mobile Application Development Review Checklist

## Mastery Checklist

### LO1: Android Components & Mobile Computing (2 items)
- [ ] Android architecture layers (bottom→top): Linux Kernel → Libraries/ART → Framework → Apps
- [ ] **Linux Kernel** is the lowest layer
- [ ] APK = **Android Package Kit** (not Phone Kit, Platform Kit, Page Kit)
- [ ] **Activity** = a single screen with Java/Kotlin code
- [ ] 4 app components: Activity, Service, BroadcastReceiver, ContentProvider
- [ ] `AndroidManifest.xml` = **all info about the app** (components, permissions, features)
- [ ] Layout XML files stored in `/res/layout/`
- [ ] Layout classes extend **`android.view.ViewGroup`**
- [ ] Valid Android layouts: LinearLayout, RelativeLayout, FrameLayout, ConstraintLayout
- [ ] Invalid: **CardLayout** (Java Swing, not Android)

### LO2: IDE Skills & Development
- [ ] Activity lifecycle order: **onCreate → onStart → onResume → onPause → onStop → onDestroy**
- [ ] **onCreate() is the FIRST callback** invoked
- [ ] Activity destroyed and recreated on **rotation** (config change)
- [ ] **Intent** used to pass data between activities (putExtra / getIntent)
- [ ] **Explicit Intent**: names exact class; **Implicit Intent**: declares action
- [ ] **SharedPreferences** for basic data persistence
- [ ] **Emulator in Android SDK** (plus all other testing methods)
- [ ] **View** = displays part of activity on screen (extends View)

### LO3: Security Concerns
- [ ] OWASP Mobile Top 10 awareness
- [ ] Insecure data storage risks (plain text in SharedPreferences)
- [ ] Encrypted data at rest and in transit
- [ ] Android permission model (normal vs dangerous, runtime requests)
- [ ] Code tampering and reverse engineering risks

### LO4: Legal & Ethical Principles
- [ ] Privacy by Design principle
- [ ] GDPR compliance (consent, right to delete)
- [ ] Accessibility requirements
- [ ] App store guidelines compliance
- [ ] Avoid dark patterns and over-collection of data

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **APK** | "Android **Package** Kit" — packages the app |
| **Architecture layers** | "**L**inux **L**oves **F**ancy **A**pps" (bottom→top: Linux, Libraries, Framework, Apps) |
| **Lifecycle order** | "**C**all **S**tar **R**esume, **P**ause **S**top **D**estroy" — C-S-R-P-S-D |
| **onCreate first** | "**C**reate comes **C**hronologically **F**irst" |
| **ViewGroup parent** | "Layouts are **Group** containers" — ViewGroup |
| **Manifest** | "**All** you need to know about the app" |
| **Activity** | "One **screen** at a time" — a single screen |
| **Intent** | "**I**nformation **T**ransport" — carries data between components |
| **CardLayout** | "**Card** is a **C**ard game, not Android" — Java Swing |
| **Layout directory** | "**res/layout** = **re**source **l**ayouts" |
| **Rotation destroys** | "**R**otation = **R**ecreate" — activity rebuilt from scratch |

## 1-Page Cram Sheet

```
ANDROID ARCHITECTURE (bottom→top)
═══════════════════════════════════
Application                    ← your app
Application Framework         ← Activity Manager, Content Providers
Libraries + Android Runtime   ← SQLite, WebKit, ART
Linux Kernel (LOWEST)         ← drivers, memory, security

APK = Android Package Kit

ACTIVITY LIFECYCLE
══════════════════
onCreate()  ← FIRST! Initialize UI
    ↓
onStart()   ← Visible
    ↓
onResume()  ← Interactive
    ↓
onPause()   ← Losing focus (save state)
    ↓
onStop()    ← Hidden
    ↓
onDestroy() ← Dead

Rotation: destroyed & recreated!

4 COMPONENTS
════════════
Activity        → Single screen
Service         → Background work
BroadcastReceiver → System events
ContentProvider → Shared data

KEY FACTS
═════════
Layouts → /res/layout/
Layout classes → extend ViewGroup
Pass data → Intent + putExtra
Persist data → SharedPreferences
Manifest → all app info
Testing → SDK emulator + physical + third-party
NOT CardLayout, NOT MS SQL, NOT Phone Kit
```
