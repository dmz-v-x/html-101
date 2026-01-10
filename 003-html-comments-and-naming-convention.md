### 1. What are HTML Comments.

First of all what are comments? 

Comments are simple text annotations within code that explain the purpose, logic, and history of the code making it easier for developers to understand, maintain, and collaborate on the software.

Comments are visible to developers, ignored during rendering, and do not appear on the webpage. But that doesn't mean commented HTML is not sent to the browser, browser still receives comments, the browser simply ignore them visually. So be mindful of what you add in your comments, never put confidential data in comments.

---

### 2. Syntax of HTML Comments

Syntax of HTML Comments:
`<!-- This is a comment -->`

Everything between <!-- and --> is ignored by the browser.

---

### 3. Basic Examples

```
<!-- Page Header -->
<header>
  <h1>My Website</h1>
</header>

<p>Hello World</p>
<!-- This paragraph explains the welcome message -->
```

---

### 4. Important Rule & Limitation

- ❌ We CANNOT nest comments

This is invalid:

```
<!-- Outer comment
   <!-- Inner comment -->
```

HTML will break.

- ❌ Comments are NOT secure

Comments are visible in: Developer Tools
So never put: Password, API Keys, Confidential Logic inside comments.

`<!-- Admin password: 123456 -->` ❌ NEVER

- ❌ Do NOT comment out large blocks permanently
Use comments for explanation, not disabling features.


---

### 5. HTML Comments vs CSS Comments vs JavaScript Comments

| Language   | Comment Syntax                  |
| ---------- | ------------------------------- |
| HTML       | `<!-- comment -->`              |
| CSS        | `/* comment */`                 |
| JavaScript | `// comment` or `/* comment */` |

---

### 6. HTML File Naming Convention

- Use Lowercase Only

index.html ✅
HomePage.html ❌

- No spaces in file names

about-us.html ✅
my portfolio.html ❌

- hyphens vs underscore 

hyphens - ✅ (recommended)
underscores _ ⚠️ (less preferred)

---

### 7. Standard Homepage Name

The standard homepage name of HTML file is: index.html

---

### 8. Common File Naming Conventions

| File Type  | Example             |
| ---------- | ------------------- |
| Main page  | index.html          |
| CSS        | style.css, main.css |
| JavaScript | script.js, app.js   |
| Images     | hero.jpg, logo.png  |

---
