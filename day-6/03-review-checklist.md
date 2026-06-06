# Day 6 — Internet / Web Programming Review Checklist

## Mastery Checklist

### LO1: Web Protocols & Fundamentals (4 items)
- [ ] Client-server architecture model
- [ ] URI components: scheme, host, port, path, query, fragment (query is optional)
- [ ] HTTP methods: GET (default), POST (body), PUT, DELETE
- [ ] HTTP request: request line + headers (+ body)
- [ ] HTTP response: status line + headers + body
- [ ] Status codes: 200, 201, 301, 400, 401, 403, 404, 500
- [ ] Protocol ports: HTTP(80), HTTPS(443), SSH(22), FTP(21), SMTP(25), DNS(53)
- [ ] Cookies (client-side, transient, persists across sessions)
- [ ] Sessions (server-side, identified by session ID)
- [ ] OAuth flow: Authorization Server validates identity → issues token → Resource Server validates token
- [ ] Stateless protocol nature

### LO2: Modern Tools & Techniques (3 items)
- [ ] REST: multiple endpoints, fixed structure, HTTP caching, over-fetching possible
- [ ] GraphQL: single endpoint, client-specified fields, flexible queries, no over-fetching
- [ ] AJAX: asynchronous requests, `XMLHttpRequest` or `fetch()`, partial page updates
- [ ] JSON: `JSON.stringify()` (obj→string), `JSON.parse()` (string→obj)
- [ ] Frontend frameworks: React, Angular, Vue
- [ ] Backend frameworks: Node.js/Express, Django, Laravel, Spring Boot

### LO3: HTML, CSS, JavaScript, AJAX & Server-Side (3 items)
- [ ] HTML form: `<form action="URL" method="GET|POST">`
- [ ] `<input type="text">` = single-line text input
- [ ] `<textarea>` = multi-line text input
- [ ] `<abbr>` = abbreviation/acronym tag
- [ ] CSS class selector: `.className` (dot prefix)
- [ ] CSS ID selector: `#idName` (hash prefix)
- [ ] `text-decoration: none` removes hyperlink underline
- [ ] `opacity: 0.0–1.0` controls transparency
- [ ] Box model: content → padding → border → margin
- [ ] JS variable keywords: `let` (block, mutable), `const` (block, immutable), `var` (function)
- [ ] `substring(start, end)` — end is **exclusive**
- [ ] String literals vs. function calls (the quoted string trap!)
- [ ] Set iteration: mixed types + number → string concatenation / number addition
- [ ] Type coercion: `==` coercion vs `===` strict equality
- [ ] `+` with strings causes concatenation
- [ ] Server-side: PHP, JSP, ASP.NET, Node.js

### LO4: Dynamic Pages & DB Connectivity (3 items)
- [ ] Client-side vs server-side rendering tradeoffs
- [ ] Database connection from web: PHP + MySQL, Node.js + MongoDB
- [ ] Dynamic content: server generates HTML OR client fetches JSON via AJAX
- [ ] SQL injection prevention: prepared statements, parameterized queries

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Form default method** | "GET it by default" — forms submit via GET unless POST specified |
| **CSS class selector** | "Dot for class, hash for ID" — `.class` `#id` |
| **Remove underline** | `text-decoration: none` — "decoration none" |
| **substring(end exclude)** | "End is the **exit** — exclusive" |
| **HTTP request parts** | "RL + H + (B)" — Request Line + Headers + optional Body |
| **URI parts scheme** | "Scheme is **she**-protocol" (always required) |
| **Cookie nature** | "Cookies are **crumb**-like — transient, can clear anytime" |
| **OAuth validator** | "Auth Server does the Auth" — Authorization Server validates |
| **Port 22 = SSH** | "22 = two swans singing **Shhh**" |
| **GraphQL benefit** | "GraphQL gives you **exactly** what you ask for" — flexible queries |

## 1-Page Cram Sheet

```
HTML
════
<form action="URL" method="GET|POST">
<input type="text">   → one-line text
<textarea>            → multi-line text
<abbr>                → abbreviation
Default method: GET

CSS
═══
. = class selector
# = ID selector
text-decoration: none   → removes underline
opacity: 0.5            → 50% transparency

Box Model: Content → Padding → Border → Margin

JAVASCRIPT
══════════
substring(start, end)  → end is EXCLUSIVE
"a.substring(2,6)"     → STRING LITERAL (not executed!)

let  = block scope, mutable
const = block scope, immutable
var = function scope

JSON.stringify(obj) → serializes
JSON.parse(str)     → deserializes

==   → loose (coerces types)
===  → strict (no coercion)

HTTP
════
GET  → data in URL, cached, default
POST → data in body, not cached

PORTS: HTTP=80, HTTPS=443, SSH=22, FTP=21

URI: scheme://host/path?query#fragment
                     ← query optional

OAuth: User → Auth Server (validates) → Token → Resource Server

REST vs GraphQL
═══╦═══
REST ║ fixed endpoints, over-fetching
GraphQL ║ flexible queries, no over-fetching

STATUS CODES: 200 OK, 404 Not Found, 500 Error
```
