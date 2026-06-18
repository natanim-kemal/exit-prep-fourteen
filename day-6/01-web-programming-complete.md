# Day 6 — Internet / Web Programming Complete Theory (10 Items)

## LO1: Web Protocols, Design & Development of Web-Based Applications (4 items)

### 1.1 How the Web Works
- **Client-Server Architecture**: Browser (client) sends HTTP request → Web server processes → Returns HTTP response
- **URL/URI**: `scheme://host:port/path?query#fragment`
  - Scheme: protocol (http, https, ftp)
  - Host: domain name or IP
  - Port: optional (80 for HTTP, 443 for HTTPS)
  - Path: resource location
  - Query string: optional key=value pairs after `?`
  - Fragment: optional section identifier after `#`

### 1.2 HTTP Protocol
- **HTTP Methods**:
  - **GET**: retrieve data (data visible in URL, cached, bookmarked)
  - **POST**: submit data (data in body, not cached, not bookmarked)
  - PUT: update/replace
  - DELETE: remove
  - PATCH: partial update
- **HTTP Request Structure**: Request line + Headers + Body (optional)
- **HTTP Response Structure**: Status line (e.g., HTTP/1.1 200 OK) + Headers + Body
- **Common Status Codes**: 200 OK, 201 Created, 301 Moved, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error
- **Stateless**: each request is independent; state maintained via cookies/sessions

### 1.3 Web Protocols
| Protocol | Port | Purpose |
|----------|------|---------|
| HTTP | 80 | Web page transfer |
| HTTPS | 443 | Encrypted web transfer |
| FTP | 21 | File transfer |
| SSH | 22 | Secure remote shell |
| Telnet | 23 | Unsecured remote terminal |
| SMTP | 25 | Email sending |
| DNS | 53 | Domain name resolution |

### 1.4 Cookies vs Sessions
- **Cookies**: stored client-side, persistent, size-limited (~4KB), sent with every request
- **Sessions**: stored server-side, more secure, can store more data, identified by session ID (usually in cookie)

### 1.5 OAuth 2.0
- **Authorization Server**: validates user identity, issues tokens
- **Resource Server**: hosts protected resources, validates tokens
- **Client**: application requesting access
- **Flow**: User → Client → Authorization Server (login) → Token → Resource Server

---

## LO2: Modern Tools & Techniques for Web-Based Applications (3 items)

### 2.1 REST vs GraphQL

| Feature | REST | GraphQL |
|---------|------|---------|
| Data fetching | Multiple endpoints, fixed structure | Single endpoint, client specifies exactly what it needs |
| Over-fetching | Common (gets entire resource) | None (only requested fields) |
| Under-fetching | Common (needs multiple requests) | None (nested queries in one request) |
| Versioning | /v1/, /v2/ | No versioning needed |
| Caching | Built-in (HTTP caching) | Manual setup |
| Learning curve | Gentle | Steeper |

### 2.2 AJAX (Asynchronous JavaScript and XML)
- Enables partial page updates without full reload
- Uses `XMLHttpRequest` object or `fetch()` API
- Can send/receive JSON, XML, HTML, text
- `fetch()` is modern, Promise-based alternative

### 2.3 JSON
- Lightweight data-interchange format
- Key-value pairs, arrays, nested objects
- `JSON.stringify(obj)` → serialize to JSON string
- `JSON.parse(str)` → parse JSON string to object

### 2.4 Web Frameworks
- **Frontend**: React, Angular, Vue.js (SPAs)
- **Backend**: Node.js/Express, Django (Python), Laravel (PHP), Spring Boot (Java)
- **Full-stack**: Next.js, Nuxt.js, Remix

---

## LO3: HTML, CSS, JavaScript, AJAX & Server-Side Scripting (3 items)

### 3.1 HTML Core

**Document Structure:**
```html
<!DOCTYPE html>
<html>
<head><title>Page Title</title></head>
<body>Content</body>
</html>
```

**Common Tags:**
| Tag | Purpose |
|-----|---------|
| `<h1>`-`<h6>` | Headings |
| `<p>` | Paragraph |
| `<a href="url">` | Hyperlink (anchor) |
| `<img src="url" alt="text">` | Image |
| `<ul>`/`<ol>`/`<li>` | Unordered/Ordered lists |
| `<table>`/`<tr>`/`<td>`/`<th>` | Table |
| `<div>` | Block-level container |
| `<span>` | Inline container |
| `<abbr title="...">` | Abbreviation |
| `<form>` | Form container |
| `<input>` | Input field |
| `<textarea>` | Multi-line text input |
| `<select>`/`<option>` | Dropdown |
| `<button>` | Clickable button |

**HTML Forms:**
```html
<form action="/submit" method="GET">
  <input type="text" name="username">
  <input type="password" name="password">
  <input type="submit" value="Login">
</form>
```
- `action`: URL where form data is sent
- `method`: HTTP method (GET is default, POST for sensitive data)
- `input type="text"`: single-line text input
- Each input needs a `name` attribute for data submission

### 3.2 CSS Core

**Ways to apply CSS:** Inline (`style` attribute), Internal (`<style>` in `<head>`), External (`.css` file linked via `<link>`)

**Selectors:**
```css
/* Element selector */
p { color: red; }

/* Class selector */
.myClass { font-size: 16px; }      /* Uses . (dot) */

/* ID selector */
#myId { background: blue; }         /* Uses # (hash) */

/* Descendant selector */
div p { margin: 5px; }

/* Pseudo-class */
a:hover { text-decoration: underline; }
```

**Common Properties:**
```css
/* Text */
color, font-size, font-family, text-align, text-decoration

/* Box Model */
width, height, margin, padding, border

/* Display & Positioning */
display: block/inline/flex/grid/none;
position: static/relative/absolute/fixed;
float: left/right;

/* Visual */
background-color, opacity, border-radius, box-shadow
```

**Key CSS Facts from Exams:**
- **Hyperlinks**: displayed with underline by default → `text-decoration: none` removes it
- **Class selector**: `.` (dot) prefix
- **Opacity**: `opacity: 0.5` for 50% transparency (value 0.0–1.0)

**Box Model** (inside → out):
```
Content → Padding → Border → Margin
```

### 3.3 JavaScript Core

**Variable Declaration:**
| Keyword | Scope | Can be reassigned? | Hoisted? |
|---------|-------|-------------------|----------|
| `var` | Function | Yes | Yes (undefined) |
| `let` | Block | Yes | Yes (TDZ) |
| `const` | Block | No | Yes (TDZ) |

**Key Exam Concepts:**
```javascript
// String methods
var a = "exercise";
a.substring(3, 5);   // "rc"  (start=3, end=5, exclusive end)
a.substring(2, 6);   // "xerc" (from index 2 to 5)

// IMPORTANT: "a.substring(2,6)" as a STRING literal
"a.substring(2,6)"   // just the literal string, NOT executed!

// Set iteration
const set = new Set();
set.add(7);
set.add('java');
set.add({ name: 'script' });
for (let item of set) {
  console.log(item + 5);
}
// Output: 12, "java5", "[object Object]5"
// Number + Number → addition
// String + anything → concatenation "java5"
// Object + Number → "[object Object]5"

// JSON serialization
JSON.stringify(obj);   // object → JSON string
JSON.parse(str);       // JSON string → object

// DOM manipulation
document.getElementById("id");
document.querySelector(".class");
element.innerHTML = "new content";
element.style.color = "red";
```

**Event Handling:**
```javascript
button.onclick = function() { alert("Clicked!"); };
button.addEventListener("click", handlerFunc);
```

### 3.4 Server-Side Scripting
- **PHP**: embedded in HTML, runs on server, `$_GET`, `$_POST` for form data, `mysqli_connect()` for DB
- **ASP.NET**: Microsoft's framework, C# or VB.NET, Web Forms or MVC
- **JSP**: Java-based, embedded in HTML, runs on servlet container
- **Node.js**: JavaScript on server, Express framework common

---

## LO4: Dynamic Interactive Web Pages & Database Connectivity (3 items)

### 4.1 Client-Side vs Server-Side

| Aspect | Client-Side | Server-Side |
|--------|-------------|-------------|
| Where code runs | Browser | Web server |
| Languages | HTML, CSS, JS | PHP, Python, Java, C#, Node.js |
| DB access | Limited (e.g., IndexedDB) | Full database connectivity |
| Security | Exposed to user | Hidden from user |
| Page reload | Not needed (AJAX/DOM) | Usually needed |

### 4.2 Database Connectivity Patterns
```php
// PHP + MySQL example
$conn = mysqli_connect("localhost", "user", "pass", "database");
$result = mysqli_query($conn, "SELECT * FROM users");
while ($row = mysqli_fetch_assoc($result)) {
    echo $row['username'];
}
```

```javascript
// Node.js + MongoDB example
const users = await db.collection('users').find({}).toArray();
```

### 4.3 Dynamic Content Generation
- Server-side: generate HTML with embedded data (PHP, JSP, ASP.NET)
- Client-side: fetch JSON from API, render via JavaScript (React, Vue)
- AJAX: `fetch('/api/users').then(r => r.json()).then(data => render(data))`

---

## Exam-Style Q&A (From Actual Model Exams)

**Q1:** Action attribute in HTML forms specifies?
- a. Where to submit form ✓
- b. The auto completion of form
- c. Which action is going on
- d. Which HTTP method is used

**Q2:** Default method while submitting a form is?
- a. Post method
- b. GET method ✓
- c. PUT method
- d. SET method

**Q3:** In HTML form, `<input type="text">` is used for?
- a. One line text ✓
- b. Block of text
- c. One paragraph
- d. None of the above

**Q4:** Which HTML tag is used to define an abbreviation?
- a. `<abbreviation>`
- b. `<abbr>` ✓
- c. `<acronym>`
- d. `<acr>`

**Q5:** By default, hyperlinks display with underline. How to remove it?
- a. `a { text: no-underline; }`
- b. `a { text-decoration: none; }` ✓
- c. `a { text-style: no-underline; }`
- d. `a { text-decoration: no-underline; }`

**Q6:** The CSS property to specify transparency of an element is?
- a. Background
- b. Alpha
- c. Opacity ✓
- d. Transparency

**Q7:** How to select an element with a specific class in CSS?
- a. `^`
- b. `#`
- c. `.` ✓
- d. `>`

**Q8:** Which keyword is used to define a variable in JavaScript?
- a. const
- b. val
- c. let ✓
- d. int
*(Note: both `const` and `let` are valid, but `let` is the modern standard for mutable variables)*

**Q9:** What will be the output of `"exercise".substring(3, 5)`?
- a. erc
- b. rc ✓
- c. er
- d. rcis

**Q10:** What will be the output of `"exitexam".substring(2, 6)`?
- a. texam
- b. xite ✓
- c. itex
- d. xitex

**Q11:** What happens with `"a.substring(2,6)"` as a string literal?
*(Output is the literal string itself, NOT the function result)*

**Q12:** Which function serializes an object into a JSON string?
- a. stringify() ✓
- b. parselson()
- c. parse()
- d. tojson()

**Q13:** Which request URI component is optional?
- a. URI host
- b. URI scheme
- c. Query string ✓
- d. Resource path

**Q14:** Which URI component specifies the protocol?
- a. URI host
- b. URI scheme ✓
- c. Resource path
- d. GET

**Q15:** An HTTP request message always contains?
- a. A status line, a header, and a body
- b. A header only
- c. A header and a body
- d. A request line and a header ✓

**Q16:** Which describes Cookie's nature?
- a. Non volatile
- b. Volatile
- c. Intransient
- d. Transient ✓
*(Cookies are transient/volatile in that they can be cleared; but they persist across sessions unlike session data)*

**Q17:** Within OAuth, what component validates the user's identity?
- a. Client
- b. Authorization Server ✓
- c. Resource Server
- d. Browser

**Q18:** What is one benefit of GraphQL over REST?
- a. More stable APIs
- b. Flexible querying/responses ✓
- c. Compatible with more gateways
- d. More secure by default

**Q19:** Which refers to unauthorized disclosure of information?
- a. Authorization
- b. Authentication
- c. Integrity
- d. Confidentiality ✓

**Q20:** A TCP/IP port number used by SSH is?
- a. 20
- b. 23
- c. 22 ✓
- d. 21

**Q21:** The TCP/IP layer responsible for addressing, path selection, and routing is?
- a. Application layer
- b. Internet layer ✓
- c. Transport layer
- d. Network Access layer

**Q22:** Console output of the Set iteration snippet:
```javascript
for (let item of set) console.log(item + 5);
// 7 + 5 = 12
// "java" + 5 = "java5"
// {name:'script'} + 5 = "[object Object]5"
```

---

---

## Question Bank Study Notes

### Protocols
**HTTP**: stateless, request-response, no minimum message size. **HTTPS**: encrypted. **WebSocket**: full-duplex real-time. **GraphQL**: query-based API (request only needed data). **REST**: architectural style using HTTP methods.

### HTML, CSS, JS
HTML = structure (DOM tree). CSS = styling. Inherited properties: `color`, `font-family`. Not inherited: `margin`, `border`, `height`. JavaScript = dynamic behavior. DOM: `document.getElementById().innerHTML` changes content. AJAX: async server requests, partial page updates.

### State Management
Redux, Vuex, Context API manage application state across components.

### Security
SQL Injection (use prepared statements), XSS (inject scripts → use output encoding), Session hijacking (steal cookies → use HttpOnly/Secure flags).


## Quick Reference — Table of Specifications (Blueprint)

| LO | Topic | Items | Cognitive Levels |
|----|-------|-------|-----------------|
| 1 | Web protocols, design & development | 4 | 2 Rem, 1 Und, 1 App |
| 2 | Modern tools & techniques | 3 | 1 Und, 1 App, 1 Ana |
| 3 | HTML, CSS, JS, AJAX, Server-side | 3 | 1 App, 1 Ana, 1 Eva |
| 4 | Dynamic pages & DB connectivity | 3 | 1 App, 1 Ana, 1 Eva |
| **Total** | | **10** | |
