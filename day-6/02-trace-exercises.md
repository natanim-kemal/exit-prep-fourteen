# Day 6 — Web Programming Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: HTML Trace/Predict

### Problem 1 — Form Output Prediction
```html
<form action="/login" method="POST">
  <input type="text" name="user" value="admin">
  <input type="submit">
</form>
```
What happens when the user clicks Submit?

**Solution:**
- Browser sends POST request to `/login`
- Form data: `user=admin`
- POST places data in request body (not URL)

---

### Problem 2 — Default Method
```html
<form action="/search">
  <input type="text" name="q">
  <input type="submit">
</form>
```
What HTTP method is used by default?

**Solution:** GET is the default method. Request: `GET /search?q=...`

---

### Problem 3 — Input Type Identification
Which HTML form element would you use for:
a) A user's biography (multiple lines)
b) A country selection from a list
c) A password field

**Solution:**
- a) `<textarea>`
- b) `<select>` with `<option>` elements
- c) `<input type="password">`

---

## Set 2: CSS Trace

### Problem 4 — Specificity Calculation
```css
p { color: blue; }
.text { color: green; }
#main p { color: red; }
```
If `<p id="main" class="text">Hello</p>`, what color is "Hello"?

**Solution:** red — `#main p` (ID + element = 1-0-1 specificity) beats `.text` (0-1-0) and `p` (0-0-1)

---

### Problem 5 — Box Model Calculation
```css
div {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```
What is the total visible width of the element?

**Solution:** 200 + 20×2 + 5×2 = **250px** (content + padding + border; margin adds space outside)

---

### Problem 6 — Display property
```css
span { display: block; width: 100px; }
```
What changes?

**Solution:** `<span>` normally inline (width ignored). With `display: block`, it takes full line and width applies.

---

## Set 3: JavaScript Trace (High Exam Priority)

### Problem 7 — substring Trace
```javascript
var a = "javascript";
var result = a.substring(0, 4);
console.log(result);
```

**Solution:** `"java"` — substring(0,4) extracts chars at indices 0,1,2,3 (exclusive end)

---

### Problem 8 — Multiple substring
```javascript
var a = "exit exam";
console.log(a.substring(0, 4));
console.log(a.substring(5, 9));
console.log(a.length);
```

**Solution:**
- `a.substring(0,4)` → "exit" (indices 0-3)
- `a.substring(5,9)` → "exam" (indices 5-8)
- `a.length` → 9 (including the space at index 4)

---

### Problem 9 — String Literal Trap (Exam Favorite!)
```javascript
var a = "preparation";
var result = "a.substring(2, 7)";
document.write(result);
```

**Solution:** `"a.substring(2, 7)"` — the entire thing is a STRING LITERAL (in quotes). The function is NEVER called. Output is the literal text itself, NOT the substring result.

---

### Problem 10 — Set Iteration Trace
```javascript
const set = new Set();
set.add(5);
set.add("js");
set.add(true);
for (let item of set) {
  console.log(item + 1);
}
```

**Trace:**
- 5 + 1 = 6 (number addition)
- "js" + 1 = "js1" (string concatenation)
- true + 1 = 2 (boolean coerced to 1, then addition)

**Output:**
```
6
js1
2
```

---

### Problem 11 — JSON Operations
```javascript
const obj = { name: "Alice", age: 25 };
const jsonStr = JSON.stringify(obj);
console.log(jsonStr);
const parsed = JSON.parse(jsonStr);
console.log(parsed.name);
```

**Solution:**
- `JSON.stringify(obj)` → `'{"name":"Alice","age":25}'`
- `JSON.parse(jsonStr)` → restores object
- `parsed.name` → "Alice"

---

### Problem 12 — var vs let Scoping
```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```
vs
```javascript
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

**Solution:**
- With `var`: prints `3, 3, 3` (function-scoped, all closures share same `i`)
- With `let`: prints `0, 1, 2` (block-scoped, each iteration gets its own `i`)

---

### Problem 13 — Type Coercion
```javascript
console.log(1 + "2" + 3);
console.log(1 + 2 + "3");
```

**Solution:**
- `1 + "2" + 3` → `"123"` (1 + "2" = "12", then "12" + 3 = "123")
- `1 + 2 + "3"` → `"33"` (1 + 2 = 3, then 3 + "3" = "33")

---

### Problem 14 — == vs ===
```javascript
console.log(5 == "5");
console.log(5 === "5");
console.log(null == undefined);
console.log(null === undefined);
```

**Solution:**
- `5 == "5"` → true (type coercion)
- `5 === "5"` → false (strict, different types)
- `null == undefined` → true (special rule)
- `null === undefined` → false (different types)

---

## Set 4: HTTP & Protocol Trace

### Problem 15 — Port Matching
Match protocols to ports:
1. HTTP     a. 443
2. HTTPS    b. 22
3. SSH      c. 80
4. FTP      d. 21

**Solution:** 1-c, 2-a, 3-b, 4-d

---

### Problem 16 — Status Code Interpretation
Match the status code:
1. 200   a. Not Found
2. 404   b. Internal Server Error
3. 500   c. OK
4. 403   d. Forbidden

**Solution:** 1-c, 2-a, 3-b, 4-d

---

### Problem 17 — URI Decomposition
`https://www.example.com:8080/products?id=5#reviews`

Identify each component:
- Scheme: _______
- Host: _______
- Port: _______
- Path: _______
- Query: _______
- Fragment: _______

**Solution:**
- Scheme: https
- Host: www.example.com
- Port: 8080
- Path: /products
- Query: id=5
- Fragment: reviews

---

## Set 5: Security & Architecture Trace

### Problem 18 — OAuth Flow
Put the OAuth steps in order:
- [ ] Client receives token
- [ ] Resource Server validates token
- [ ] Authorization Server validates user identity
- [ ] User authenticates to Authorization Server
- [ ] Client accesses Resource Server

**Solution:**
1. User authenticates to Authorization Server
2. Authorization Server validates user identity
3. Client receives token
4. Client accesses Resource Server
5. Resource Server validates token

---

### Problem 19 — REST vs GraphQL
Which approach would be better for:
a) A simple blog where every page needs full article data
b) A dashboard where users need specific fields from multiple data sources

**Solution:**
- a) REST (fixed endpoints match the blog structure)
- b) GraphQL (flexible querying avoids over/under-fetching)

---

### Problem 20 — Cookie/Session Decision
Should you use cookies or sessions for:
a) Remembering a user's theme preference (dark/light)
b) Storing a user's credit card number during checkout
c) Tracking anonymous site visits

**Solution:**
- a) Cookie (preference persists, not sensitive)
- b) Session (sensitive data, server-side storage)
- c) Cookie (anonymous tracking, no login needed)

---

## Common Exam Traps — Web Programming

| Trap | Explanation |
|------|-------------|
| **substring trap** | `"a.substring(2,6)"` is a string literal, NOT a function call |
| **GET vs POST default** | HTML form default method is **GET**, not POST |
| **CSS class selector** | `.` for class, `#` for ID |
| **text-decoration** | `text-decoration: none` removes underline (not `text-style` or `text`) |
| **Opacidad ≠ Alpha** | CSS property is `opacity`, not `alpha` or `transparency` |
| **Cookie nature** | Cookies are **transient** (client-side, can be cleared) |
| **substring indices** | `substring(start, end)` — end is **exclusive** |
| **Type coercion** | `+` with string causes concatenation; `==` coerces, `===` doesn't |
| **var vs let** | `var` is function-scoped; `let`/`const` are block-scoped |
| **HTTP message parts** | Request = request line + headers (+ optional body) |
| **URI optional** | Query string is **optional**, scheme and path are required |
| **OAuth roles** | **Authorization Server** validates identity, not Resource Server |
