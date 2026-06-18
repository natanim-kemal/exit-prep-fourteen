# Web Programming — Study Notes

## 1. Web Protocols

**HTTP** (Hypertext Transfer Protocol): stateless protocol for web communication. An HTTP message has no specified minimum size; the body can be empty.

**HTTPS**: HTTP over SSL/TLS for encrypted communication.

**WebSocket**: enables real-time, two-way (full-duplex) communication between client and server.

**GraphQL**: query-based API that allows clients to request only needed data.

**REST**: architectural style for designing networked applications using HTTP methods (GET, POST, PUT, DELETE).

## 2. HTML (Structure)

HTML provides the structure of a webpage. Key elements include headings (`h1`-`h6`), paragraphs (`p`), links (`a`), images (`img`), lists (`ul`, `ol`), tables (`table`), forms (`form`), and semantic elements (`header`, `footer`, `section`, `article`).

**DOM (Document Object Model)**: tree representation of the HTML document that can be manipulated with JavaScript.

## 3. CSS (Styling)

CSS styles and lays out webpage elements. Key concepts:
- **Selectors**: element, class (`.`), id (`#`), descendant, child, attribute
- **Box model**: content → padding → border → margin
- **Display**: block, inline, inline-block, flex, grid, none
- **Position**: static, relative, absolute, fixed, sticky
- **Inherited properties**: some CSS properties (like `color`, `font-family`) are inherited from parent to child elements; others (like `margin`, `border`, `height`) are not.

## 4. JavaScript (Interactivity)

JavaScript adds dynamic behavior to webpages. Key concepts:
- **Variables**: `var`, `let`, `const`
- **DOM manipulation**: `document.getElementById().innerHTML` changes element content dynamically
- **Events**: click, submit, load, mouseover, keypress
- **AJAX (Asynchronous JavaScript and XML)**: makes asynchronous requests to the server and updates the page dynamically without full reload (uses `XMLHttpRequest` or `fetch` API)

**Key difference with Java**: JavaScript is dynamically typed, interpreted, runs in browser; Java is statically typed, compiled, runs on JVM/server.

## 5. Server-Side Development

**PHP**: server-side scripting language for generating dynamic content and database connectivity.

**Database connectivity**: server-side code (PHP, Node.js, Python, Java Servlets/JSP) connects to databases to store/retrieve data.

## 6. State Management & Tools

**State management** in web applications: Redux (for React apps), Vuex, or Context API for managing application state across components.

**AJAX**: enables partial page updates without full reload. Example: fetch suggestions as user types in search box.

## 7. Web Security

- **SQL Injection**: attacker injects malicious SQL through input fields. Prevented by prepared statements/parameterized queries.
- **XSS (Cross-Site Scripting)**: injects JavaScript to steal user data. Prevented by output encoding and Content Security Policy.
- **Session hijacking**: attacker steals session cookies. Prevented by using secure, HttpOnly cookies.

## 8. Key Development Concepts

- **Responsive design**: layouts adapt to different screen sizes using CSS media queries and flexible grids.
- **Version control (Git)**: tracks changes to code, enables collaboration.
- **Package managers**: npm (Node.js), yarn — manage project dependencies.
- **Build tools**: webpack, gulp, vite.
