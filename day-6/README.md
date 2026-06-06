# Day 6 — Internet / Web Programming (10 Items)

## Files in this directory

| File | Content |
|------|---------|
| `01-web-programming-complete.md` | Full theory: web protocols (HTTP/HTTPS/SSH), URI decomposition, HTML forms & tags, CSS selectors & box model, JavaScript (substring, Set, JSON, coercion, var/let/const), AJAX, REST vs GraphQL, OAuth 2.0, cookies vs sessions, server-side scripting, dynamic DB connectivity + 22 exam Q&As from real model exams |
| `02-trace-exercises.md` | 20 exam-style problems: HTML form behavior, CSS specificity & box model, JavaScript substring trace (with string literal trap!), Set iteration, JSON ops, var vs let hoisting, type coercion, HTTP port matching, status codes, URI decomposition, OAuth flow, REST vs GraphQL scenarios, cookie/session decisions |
| `03-review-checklist.md` | Mastery checklist by LO, mnemonics, 1-page cram sheet |

## How to use today

1. **Read** `01-web-programming-complete.md` (2.5 hrs) — focus on: substring behavior (exam favorite!), CSS class/ID selectors, HTML form default method, HTTP port numbers, OAuth flow
2. **Practice** `02-trace-exercises.md` (1.5 hrs) — especially the JavaScript traces (substring, Set, string literal trap appear repeatedly in real exams)
3. **Self-test** `03-review-checklist.md` (30 min)

## Key exam focus (from 24 actual questions extracted)

- **JavaScript substring** — appears in BOTH Model 2 and AAU 2015; end index is exclusive
- **String literal trap** — `"a.substring(2,6)"` in quotes returns the literal, not executed
- **CSS class selector** — `.` (dot) prefix, NOT `#` (that's ID)
- **text-decoration: none** — removes hyperlink underline (not `text-style`, not `text`)
- **HTML form default method** = GET (model exam confirms this)
- **OAuth** — Authorization Server validates user identity
- **Ports**: SSH=22, HTTP=80, HTTPS=443
- **HTTP request structure**: request line + headers (+ optional body)
- **URI**: query string is the optional component
- **GraphQL benefit**: flexible querying/responses
- **Cookies**: transient (client-side, can be cleared)
- **Set iteration**: type coercion with `+` (number addition vs string concatenation)

## Source mapping
| Exam File | Web Questions Found |
|-----------|-------------------|
| Model moee.docx | Q13, Q34, Q52, Q55, Q61 (5 questions) |
| Model 2.docx | W1-W10 (10 questions) |
| AAU Exit Exam 2015.docx | 9 questions |

## Next: Day 7 — Mobile Application Development (6 items)
