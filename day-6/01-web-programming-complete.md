# Day 6 — Internet / Web Programming (112 Items)

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

## Quick Reference — Table of Specifications (Blueprint)

| LO | Topic | Items | Cognitive Levels |
|----|-------|-------|-----------------|
| 1 | Web protocols, design & development | 4 | 2 Rem, 1 Und, 1 App |
| 2 | Modern tools & techniques | 3 | 1 Und, 1 App, 1 Ana |
| 3 | HTML, CSS, JS, AJAX, Server-side | 3 | 1 App, 1 Ana, 1 Eva |
| 4 | Dynamic pages & DB connectivity | 3 | 1 App, 1 Ana, 1 Eva |
| **Total** | | **10** | |


## Practice Questions (from Question Bank)

### Q352. HTTP method for partial update?

- A) PUT
- B) UPDATE
- C) POST
- D) PATCH
  **Answer: D**

### Q353. CSS Box Model from inside out?

- A) Margin,Border,Padding,Content
- B) Border,Padding,Content,Margin
- C) Content,Padding,Border,Margin
- D) Padding,Content,Margin,Border
  **Answer: A**

### Q354. In a resource-constrained environment, javaScript block-scoped non-reassignable?

- A) let
- B) const
- C) var
- D) static
  **Answer: B**

### Q355. event.preventDefault() purpose?

- A) Stop propagation
- B) Remove listener
- C) Cancel AJAX
- D) Prevent default browser
  **Answer: D**

### Q356. How is Http 404 best characterized?

- A) Forbidden
- B) Unauthorized
- C) Not Found
- D) Bad Request
  **Answer: C**

### Q357. Consider a system where hTTPS vs HTTP?

- A) HTTPS avoids TCP
- B) HTTPS uses port 80
- C) HTTPS encrypts with TLS/SSL
- D) HTTPS is slower
  **Answer: C**

### Q358. Prepared statement prevents?

- A) CSRF
- B) SQL Injection
- C) XSS
- D) DDoS
  **Answer: B**

### Q359. Best CSS for 2D grid layouts?

- A) Float
- B) Inline-block
- C) Grid
- D) Flexbox
  **Answer: C**

### Q360. When designing for high performance, xSS is prevented by?

- A) Sanitising/escaping
- B) Parameterised queries
- C) HTTPS
- D) CSRF tokens
  **Answer: A**

### Q361. async/await in JavaScript?

- A) Blocks main thread
- B) Cleaner Promise syntax
- C) Converts sync to async
- D) Replaces callbacks with loops
  **Answer: C**

### Q362. HTML5 tag for navigation?

- A) <aside>
- B) <section>
- C) <nav>
- D) <header>
  **Answer: C**

### Q363. In a resource-constrained environment, cSS media query enables?

- A) Load different JS files
- B) Embed video
- C) Different styles by device
- D) Query server-side DB
  **Answer: C**

### Q364. What is the primary function of is?

- A) Deleting resources
- B) Submitting forms
- C) Retrieving resources
- D) Updating resources
  **Answer: C**

### Q365. In which scenario would is be employed?

- A) Deleting resources
- B) Submitting data to be processed
- C) Partial updates
- D) Retrieving data
  **Answer: B**

### Q366. In a resource-constrained environment, which statement about Http 200 is correct?

- A) OK
- B) Not Found
- C) Server Error
- D) Redirect
  **Answer: A**

### Q367. Which statement about Http 500 is correct?

- A) OK
- B) Not Found
- C) Redirect
- D) Server Error
  **Answer: D**

### Q368. How is Http 401 best characterized?

- A) Unauthorized
- B) Not Found
- C) Bad Request
- D) Forbidden
  **Answer: A**

### Q369. Consider a system where what does DNS do?

- A) Assigns IP addresses
- B) Encrypts traffic
- C) Translates domain names
- D) Routes packets
  **Answer: C**

### Q370. Which description of DOM is accurate?

- A) Dynamic Object Method
- B) Document Object Model — tree
- C) Data Object Manager
- D) Domain Operations Module
  **Answer: B**

### Q371. document.getElementById() returns?

- A) Array of all elements
- B) CSS styles
- C) First matching element by ID
- D) Event listeners
  **Answer: C**

### Q372. In a resource-constrained environment, querySelector() uses what syntax?

- A) XPath
- B) JavaScript expressions
- C) CSS selector syntax
- D) HTML tag names only
  **Answer: C**

### Q373. Flexbox is best for?

- A) One-dimensional layouts
- B) 2D grid layouts
- C) Animation
- D) Print stylesheets
  **Answer: A**

### Q374. Which of the following best describes 'display: none' in CSS?

- A) Makes element invisible but
- B) Collapses element
- C) Hides element and removes from
- D) Makes element transparent
  **Answer: C**

### Q375. Which description of 'visibility: hidden' vs 'display: none' is accurate?

- A) Both remove from flow
- B) 'display: none' keeps space
- C) 'visibility: hidden' hides
- D) No difference
  **Answer: C**

### Q376. Which description of purpose of the <form> tag is accurate?

- A) Style elements
- B) Create navigation menus
- C) Group input elements to
- D) Display images
  **Answer: C**

### Q377. Identify the correct statement about event bubbling in JavaScript.

- A) Event cancels itself
- B) Event fires multiple times
- C) Event fires on all elements
- D) Event propagates from target up
  **Answer: D**

### Q378. In a resource-constrained environment, what does JSON.stringify() do?

- A) Validates JSON
- B) Converts JavaScript object to
- C) Parses JSON string to object
- D) Formats JSON for display
  **Answer: B**

### Q379. What does JSON.parse() do?

- A) Converts JS object to JSON
- B) Parses JSON string into JavaScript object
- C) Validates JSON format
- D) Stringifies arrays only
  **Answer: B**

### Q380. Which of the following best describes AJAX?

- A) Technique to update page
- B) A server-side language
- C) A JavaScript framework
- D) A CSS preprocessor
  **Answer: A**

### Q381. Consider a system where cSS specificity order from lowest to highest?

- A) Element, Class, ID
- B) ID, Element, Class
- C) ID, Class, Element
- D) Class, Element, ID
  **Answer: A**

### Q382. What does 'position: absolute' do in CSS?

- A) Positions relative to document flow
- B) Sticks at scroll position
- C) Removes from flow
- D) Fixes to viewport
  **Answer: C**

### Q383. What does 'position: fixed' do in CSS?

- A) Sticks to viewport regardless of scrolling
- B) Positions relative to parent
- C) Positions relative to nearest ancestor
- D) Positions relative to document flow
  **Answer: A**

### Q384. In a resource-constrained environment, hTTP is described as which type of protocol?

- A) Persistent state
- B) Connection-oriented
- C) Stateless request-response
- D) Encrypted by default
  **Answer: C**

### Q385. Identify the correct statement about sessions in web development.

- A) HTML segments
- B) JavaScript closures
- C) CSS transitions
- D) Server-side mechanism to
  **Answer: D**

### Q386. Which of the following best describes cookies?

- A) Small data stored
- B) Server-side data storage
- C) JavaScript variables
- D) HTML form data
  **Answer: A**

### Q387. Consider a system where in which scenario would primarily be employed?

- A) Server-side scripting
- B) Styling web pages
- C) Client-side scripting
- D) Database management
  **Answer: C**

### Q388. Node.js enables JavaScript to run:?

- A) Only in browsers
- B) On the server side
- C) In mobile apps
- D) On embedded systems
  **Answer: B**

### Q389. Which description of npm is accurate?

- A) Node Package Manager — manages
- B) Network Protocol Manager
- C) Node Performance Monitor
- D) New Programming Model
  **Answer: A**

### Q390. Consider a system where identify the correct statement about responsive web design.

- A) Websites with animations
- B) Design adapting to different screen sizes
- C) Server-side rendering
- D) Fast loading websites
  **Answer: B**

### Q391. Which CSS property controls text size?

- A) text-height
- B) font-size
- C) font-style
- D) font-weight
  **Answer: B**

### Q392. Which of the following best describes purpose of alt text on images?

- A) Caption displayed below image
- B) Image file name
- C) Accessibility description for
- D) Image tooltip on hover
  **Answer: C**

### Q393. When designing for high performance, what does 'semantic HTML' mean?

- A) HTML with no CSS
- B) Minified HTML
- C) Using tags that describe
- D) HTML with JavaScript
  **Answer: C**

### Q394. Which HTML tag creates a hyperlink?

- A) <a>
- B) <href>
- C) <url>
- D) <link>
  **Answer: A**

### Q395. Which of the following best describes difference between block and inline elements?

- A) Both take full width
- B) No difference
- C) Inline takes full width
- D) Block takes full width and
  **Answer: D**

### Q396. When designing for high performance, which description of CSS specificity is accurate?

- A) Speed of CSS rendering
- B) Browser compatibility
- C) System determining which CSS
- D) Order of CSS file loading
  **Answer: C**

### Q397. Which HTTP method should be idempotent (same result multiple times)?

- A) PATCH
- B) POST only
- C) GET
- D) POST
  **Answer: C**

### Q398. Which of the following best describes RESTful API?

- A) API requiring authentication
- B) API using WebSockets
- C) API with XML only
- D) API following REST
  **Answer: D**

### Q399. When designing for high performance, what does PUT do in REST?

- A) Replaces resource entirely
- B) Deletes resource
- C) Partially updates resource
- D) Creates new resource
  **Answer: A**

### Q400. What does DELETE do in REST?

- A) Creates resource
- B) Updates resource
- C) Removes resource
- D) Retrieves resource
  **Answer: C**

### Q401. CSRF attack is prevented by:?

- A) Prepared statements
- B) CSRF tokens in forms
- C) Output escaping
- D) HTTPS
  **Answer: B**

### Q402. When designing for high performance, which description of web framework is accurate?

- A) HTML layout template
- B) Reusable code structure
- C) Browser plugin
- D) CSS preprocessor
  **Answer: B**

### Q403. What does the 'src' attribute in <script> tag do?

- A) Links external JavaScript file
- B) Imports CSS
- C) Styles the script
- D) Runs inline JavaScript
  **Answer: A**

### Q404. localStorage vs sessionStorage?

- A) No difference
- B) sessionStorage persists
- C) localStorage persists across
- D) Both clear on refresh
  **Answer: C**

### Q405. When designing for high performance, identify the correct statement about Promise in JavaScript.

- A) An event listener
- B) A callback function
- C) A guaranteed result
- D) Object representing
  **Answer: D**

### Q406. What does .then() do on a Promise?

- A) Handles rejection
- B) Cancels promise
- C) Creates new promise chain
- D) Handles resolution with callback
  **Answer: D**

### Q407. What does .catch() do on a Promise?

- A) Logs promise state
- B) Handles rejection/error
- C) Handles resolution
- D) Cancels promise
  **Answer: B**

### Q408. Consider a system where identify the correct statement about fetch() API used for.

- A) CSS animation
- B) Making HTTP requests
- C) File system access
- D) DOM manipulation
  **Answer: B**

### Q409. Identify the correct statement about callback function.

- A) Anonymous function only
- B) Recursive function
- C) Function returned from another
- D) Function passed as argument to
  **Answer: D**

### Q410. Identify the correct statement about event loop in JavaScript.

- A) Mechanism managing async
- B) CSS animation loop
- C) HTML rendering cycle
- D) Server request cycle
  **Answer: A**

### Q411. In a resource-constrained environment, which of the following best describes form validation?

- A) Encrypting form data
- B) Styling form elements
- C) Checking server response
- D) Verifying user input before
  **Answer: D**

### Q412. What does the 'action' attribute in <form> specify?

- A) Form styling
- B) Input type
- C) URL where form data is
- D) HTTP method
  **Answer: C**

### Q413. What does the 'method' attribute in <form> specify?

- A) HTTP method for form submission
- B) Encoding type
- C) URL for submission
- D) Validation rules
  **Answer: A**

### Q414. In a resource-constrained environment, which CSS selector targets all paragraph elements?

- A) #p
- B) p
- C) *p
- D) .p
  **Answer: B**

### Q415. Which CSS selector targets element with class 'box'?

- A) .box
- B) box
- C) #box
- D) *box
  **Answer: A**

### Q416. Which CSS selector targets element with id 'header'?

- A) #header
- B) header
- C) *header
- D) .header
  **Answer: A**

### Q417. When designing for high performance, which of the following best describes CSS inheritance?

- A) CSS files importing other CSS files
- B) Classes extending other classes
- C) Child elements inheriting certain CSS
- D) Stylesheets merging rules
  **Answer: C**

### Q418. Which description of purpose of the <head> HTML element is accurate?

- A) Contains metadata, links to
- B) Navigation container
- C) Displays page title visually
- D) Main page header section
  **Answer: D**

### Q419. What does <meta charset='UTF-8'> do?

- A) Adds metadata description
- B) Imports fonts
- C) Declares character
- D) Sets page language
  **Answer: C**

### Q420. Which description of viewport meta tag used for is accurate?

- A) Defining page description
- B) Setting page background
- C) Controlling how page scales on
- D) Linking stylesheets
  **Answer: C**

### Q421. Identify the correct statement about Flexbox 'justify-content' for.

- A) Aligns items on cross axis
- B) Aligns items along main axis
- C) Controls flex wrap
- D) Sets flex direction
  **Answer: B**

### Q422. Which of the following best describes Flexbox 'align-items' for?

- A) Sets flex grow
- B) Aligns items along cross axis
- C) Controls spacing between items
- D) Aligns items along main axis
  **Answer: B**

### Q423. In a resource-constrained environment, which description of :hover pseudo-class is accurate?

- A) Applies to focused elements
- B) Selects odd elements
- C) Applies styles when mouse
- D) Selects first child
  **Answer: C**

### Q424. Which of the following best describes purpose of z-index in CSS?

- A) Controls element opacity
- B) Controls animation speed
- C) Controls stacking order of
- D) Sets zoom level
  **Answer: C**

### Q425. What does 'overflow: hidden' do?

- A) Adds scrollbar
- B) Collapses element
- C) Hides content that
- D) Makes overflow visible
  **Answer: C**

### Q426. Consider a system where what is the primary function of is?

- A) <li>
- B) <ol>
- C) <dl>
- D) <ul>
  **Answer: D**

### Q427. Which HTML element defines a table row?

- A) <th>
- B) <td>
- C) <table>
- D) <tr>
  **Answer: D**

### Q428. Which description of difference between <div> and <span> is accurate?

- A) <span> is block-level
- B) No difference
- C) <div> is block-level
- D) Both are inline
  **Answer: C**

### Q429. Which of the following best describes SQL injection and how is it prevented?

- A) Script injection in HTML
- B) JavaScript injection
- C) CSS injection
- D) Malicious SQL in input
  **Answer: D**

### Q430. Which of the following best describes CORS?

- A) Cross-Origin Resource Sharing —
- B) Cached Object Retrieval Service
- C) Content Ordering Resource System
- D) Certificate Origin Request Standard
  **Answer: A**

### Q431. What does PDO stand for in PHP?

- A) Public Data Object
- B) PHP Data Objects — database
- C) Parameterised Data Output
- D) Persistent Database Object
  **Answer: B**

### Q432. Which description of server-side rendering (SSR) is accurate?

- A) Database renders templates
- B) Client browser builds HTML
- C) Server generates full HTML before
- D) CDN caches rendered pages
  **Answer: C**

### Q433. Identify the correct statement about client-side rendering (CSR).

- A) Database generates HTML
- B) Browser builds HTML using
- C) Server generates HTML
- D) CDN generates HTML
  **Answer: B**

### Q434. What does HTTP status 301 mean?

- A) OK
- B) Not Found
- C) Moved Permanently
- D) Server Error
  **Answer: C**

### Q435. In a resource-constrained environment, what does HTTP status 403 mean?

- A) Forbidden — access denied
- B) Not Found
- C) Unauthorized
- D) Server Error
  **Answer: A**

### Q436. Which description of purpose of HTTPS is accurate?

- A) Encrypts data in transit
- B) Improves SEO only
- C) Faster page loading
- D) Compresses web pages
  **Answer: A**

### Q437. Which description of Content Delivery Network (CDN) is accurate?

- A) Distributed servers
- B) Database replication
- C) DNS alternative
- D) Load balancer
  **Answer: A**

### Q438. When designing for high performance, which description of n HTTP header is accurate?

- A) CSS at-rule
- B) JavaScript function
- C) HTML <header> element
- D) Metadata sent with HTTP
  **Answer: C**

### Q439. What does 'enctype' attribute in forms set?

- A) Encryption algorithm
- B) Character set
- C) How form data is encoded
- D) Form validation rules
  **Answer: C**

### Q440. What does the 'required' attribute on input do?

- A) Makes field mandatory
- B) Sets maximum length
- C) Pre-fills input value
- D) Disables the field
  **Answer: A**

### Q441. Which of the following best describes purpose of the <label> tag?

- A) Associates text description
- B) Creates input field
- C) Displays decorative text
- D) Groups form elements
  **Answer: A**

### Q442. Identify the correct statement about URL encoding.

- A) Signing URLs with
- B) Shortening URLs
- C) Converting special
- D) Encrypting URLs
  **Answer: C**

### Q443. What does the <iframe> tag do?

- A) Embeds another HTML page
- B) Defines page border
- C) Creates an image frame
- D) Creates a table frame
  **Answer: A**

### Q444. Identify the correct statement about progressive enhancement.

- A) Loading CSS before JavaScript
- B) Incrementally adding pages
- C) Gradual page loading
- D) Building core experience first
  **Answer: D**

### Q445. Which of the following best describes single-page application (SPA)?

- A) Mobile-only website
- B) Website with only one HTML page
- C) Website with no JavaScript
- D) App loading once then dynamically
  **Answer: D**

### Q446. What does REST stand for?

- A) Reusable Event State Technology
- B) Resource Entry State Type
- C) Representational State Transfer
- D) Remote Execution Standard Transfer
  **Answer: C**

### Q447. When designing for high performance, which CSS property creates rounded corners?

- A) corner-radius
- B) round-corners
- C) border-radius
- D) border-round
  **Answer: C**

### Q448. Identify the correct statement about purpose of @media in CSS.

- A) Defines media types for print
- B) Embeds media files
- C) Applies styles conditionally
- D) Imports media libraries
  **Answer: C**

### Q449. Identify the correct statement about difference between margin and padding.

- A) Padding is outside
- B) Both are inside border
- C) No difference
- D) Margin is outside border
  **Answer: D**

### Q450. Consider a system where what does 'box-sizing: border-box' do?

- A) Removes box model
- B) Width/height include padding
- C) Adds margin to sizing
- D) Adds border outside element
  **Answer: B**

### Q451. Which of the following best describes cascading in CSS (Cascading Style Sheets)?

- A) Styles cascade from JavaScript
- B) Rules cascade: later/more specific
- C) CSS files cascade down the page
- D) CSS loads in waterfall
  **Answer: A**

### Q452. Which description of CSS pseudo-element is accurate?

- A) CSS variable
- B) Fake HTML element
- C) Selector targeting
- D) Browser-specific property
  **Answer: C**

### Q453. When designing for high performance, identify the correct statement about localStorage.

- A) IndexedDB shortcut
- B) Server-side session
- C) Temporary cookie
- D) Client-side key-value
  **Answer: D**

### Q454. Which description of web API is accurate?

- A) HTML element
- B) Browser plugin
- C) Interface allowing web
- D) CSS framework
  **Answer: C**

### Q455. Which of the following best describes purpose of the <script> tag in HTML?

- A) Creates interactive forms
- B) Embeds
- C) Imports external HTML
- D) Embeds CSS
  **Answer: B**

### Q456. Consider a system where what does 'defer' attribute on <script> do?

- A) Loads script asynchronously
- B) Script downloads in background
- C) Prevents script execution
- D) Blocks page rendering
  **Answer: B**

### Q457. Which of the following best describes event 'DOMContentLoaded'?

- A) Fires on every page interaction
- B) Fires when JavaScript loads
- C) Fires when initial HTML parsed and DOM ready
- D) Fires when all resources including images load
  **Answer: C**

### Q458. Which of the following best describes innerHTML?

- A) CSS property
- B) HTTP header
- C) Property getting/setting
- D) JavaScript import
  **Answer: C**

### Q459. Consider a system where which description of textContent is accurate?

- A) Font file format
- B) Property getting/setting
- C) HTTP content type
- D) CSS text property
  **Answer: B**

### Q460. Which of the following best describes difference between innerHTML and textContent?

- A) Both always parse HTML
- B) innerHTML parses HTML
- C) textContent parses HTML
- D) No difference
  **Answer: B**

### Q461. Which of the following best describes event.stopPropagation()?

- A) Pauses event queue
- B) Removes event listener
- C) Prevents event from bubbling
- D) Cancels default browser action
  **Answer: C**

### Q462. When designing for high performance, what does the 'type' attribute on input define?

- A) Validation regex
- B) Input CSS class
- C) Input label
- D) Kind of input control
  **Answer: D**

### Q463. Which description of HTTP/2's main advantage over HTTP/1.1 is accurate?

- A) Multiplexing — multiple
- B) Encryption by default
- C) Larger packet size
- D) Simpler headers
