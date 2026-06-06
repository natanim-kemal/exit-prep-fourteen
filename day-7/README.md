# Day 7 — Mobile Application Development (6 Items)

## Files in this directory

| File | Content |
|------|---------|
| `01-mobile-app-complete.md` | Full theory: Android architecture (4 layers), APK definition, Activity definition, 4 core components, Manifest, Layouts & ViewGroup hierarchy, Activity lifecycle (C-R-S-P-S-D), Intents (explicit/implicit), SharedPreferences, project structure, mobile security (OWASP), ethical principles + 12 exam Q&As from real model exams |
| `02-trace-exercises.md` | 19 exam-style problems: Android layer ordering, component matching, lifecycle traces (first launch, home button, return, rotation, dialog), Intent classification, ViewGroup hierarchy, layout directory, data persistence selection, error detection |
| `03-review-checklist.md` | Mastery checklist by LO, mnemonics, 1-page cram sheet |

## How to use today

1. **Read** `01-mobile-app-complete.md` (1.5 hrs) — focus on: APK acronym, activity lifecycle (onCreate is first), layout directory (/res/layout/), ViewGroup as parent, Android architecture layers
2. **Practice** `02-trace-exercises.md` (1 hr) — especially lifecycle traces and intent classification
3. **Self-test** `03-review-checklist.md` (20 min)

## Key exam focus (from 18 actual questions extracted)

- **APK = Android Package Kit** — appears in ALL 3 exam files (~4 questions!)
- **onCreate() is first callback** — confirmed in moee and Model 2
- **Activity = single screen with Java code** — appears in both Model 2 and AAU 2015
- **Layout classes extend ViewGroup** — confirmed in both Model 2 and AAU 2015
- **Intent** passes data between activities — appears in both Model 2 and AAU 2015
- **Linux Kernel** is the lowest layer of Android — AAU 2015
- **Manifest = all info about app** — Model 2
- **/res/layout/** for XML layout files — Model 2
- **CardLayout is NOT Android** — moee
- **SharedPreferences** for data persistence — Model 2
- **Emulator in Android SDK** for testing — Model 2

## Source mapping
| Exam File | Mobile Questions Found |
|-----------|---------------------|
| Model moee.docx | Q59, Q60, Q69 (3 questions) |
| Model 2.docx | Q1–Q10 (10 questions) |
| AAU Exit Exam 2015.docx | 5 questions |

## Important note
All 18 extracted mobile questions are **Android-only**. No Flutter, Dart, Kotlin, iOS/Swift, React Native, or cross-platform questions appear in any of the 3 model exams. However, the repo contains 20 MobApp PDFs covering Flutter + Kotlin, so a basic awareness is useful.

## Next: Day 8 — Software Engineering (8 items)
