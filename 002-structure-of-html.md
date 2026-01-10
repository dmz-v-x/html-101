### 1. Structure of HTML

Every HTML page follows this basic skeleton:

```
<!DOCTYPE html>
<html>
<head>
  <!-- Metadata goes here -->
</head>
<body>
  <!-- Visible content goes here -->
</body>
</html>
```

Let's go through each term mentioned over here.

---

### 2. Tag vs Elements

#### What is a Tag in HTML?

A Tag is just the syntax, the thing inside angle brackets <>

Examples:

```
<p>
</p>

<img>
<br>
```

Types of tags

1. Opening tag:

```
<p>
<div>
<a>
```

2. Closing tag:

```
</p>
</div>
</a>
```

3. Self-Closing tag

```
<img>
<br>
<input>
```

⚠️ Important Point: A tag alone does not represent content, think of it just a marker or a label.

---

#### What is an Element in HTML?

An element is the complete unit that our browser actually understands and work with.

An element includes:
- the opening tag 
- the content (if any)
- the closing tag (if any)
- attributes (if any)

Void Elements: Elements that does not have closing tag.

Example:

```
<img>
<br>
<input>
<meta>
<link>
```

We'll see each one of them in later blogs.

Examples

`<p>Hello World</p>`
This is called a paragraph element.

`<a href="https://example.com">Click me</a>`
This is anchor element with attributes.

`<img src="cat.png" alt="Cat">`
This is called a void element.

---

#### DOM Representation (How browser sees it)

HTML:
`<p>Hello</p>`

DOM:
Paragraph Element
 └── Text Node ("Hello")

---

#### Some Incorrect Statements

- ❌ `<p>` is an element

Technically wrong.

Correct:

`<p>Hello</p>` is the element

- ❌ Self-closing tag means it closes itself

Wrong in HTML.

Correct:

Void elements never had closing tags to begin with

- ❌ HTML elements are just tags

No.

Elements = tags + content + attributes + structure

---

### 3. Purpose and importance of <!DOCTYPE html>

This is the first line of every modern HTML document. It tells the browser that this document uses HTML5 standards. 

- Always include it in your HTML document.
- It's not an HTML tag
- It's just a declaration

---

### 4. The `<html>` root element and the lang attribute

This is the root element of the web page. Everything inside our page must be wrapped inside <html>.

```
<html>
  ...
</html>
```

It is recommended to pass lang attribute in the html element as:
`<html lang="en">`

This attribute tells browser, what language the page is written in.
`<html lang="en">` means the page content is in English.

This also helps visually impaired users to understand the audio clearly and understand the content of the page.

This also helps google to rank our website better and serve our page to the right audience.

---

### 5. The `<head>` section and its role as metadata

The `<head>` tag is the most important or atleast the most confusing in terms of when just getting started with HTML atleast in my opinion.

The `<head>` contains metadata information about the page that is not visible content.

So What actually goes inside of `<head>`?
Common Metadata Elements:

1. `<title>`: Displays the text in the browser tab `<title>My Website</title>`

2. `<meta charset>`: Defines character encoding. 
`<meta charset="UTF-8">`

Question: Now the question arises, what actually is a character encoding?

Answer: So our computers don't understand letters. They understand numbers (binary) [0, 1] only. So Encoding tells browser, when you see this number, display this character.

Without encoding the browser might now know what a particular binary sequence represent in symbol, and it might display strange symbols.

`UTF-8` is the most universal encoding standard. It supports: 
- English letters (A - Z)
- Numbers (0 - 9)
- Symbols (! @ # $ % ...)
- Emojis 😊
- Characters of all the other languages

So when we write `<meta charset="UTF-8">` we are telling the browser that this page contains language or symbol. Display it properly.

Where it is placed?
It is placed inside `<head>`:

```
<head>
  <meta charset="UTF-8">
  <title>My Page</title>
</head>
```

Question: My next thought was okay i get that character encoding is a system that maps numbers -> letters/symbol as computers only understand numbers. And encoding tells browser that display this character when you see this number? But we don't write numbers in html we write text content so how does this all resolve?

Answer: So when we write `<p>Hello</p>`. It only sees numbers as:
01010100 00111010 10111101 00001110

So HTML itself doesn't encode, the encoding happens before the browser ever sees the file, by the time browser reads the file it's already in binary.

- So who does the encoding?
Encoding is done by our text editor (VSCode)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4ho7canfw2x4p3bgg70t.png)

We can see in the image at the bottom right corner that the encoding will be done in utf-8 format and it will be done by the browser.

By the time browser reads our html file it is already in binary format.

Question: My next thought of question was if browser receives a binary data how come browser know what was the encoding format was as:
`<meta charset="UTF-8">` would've been converted to binary data as well.

Answer: There are few rules by which browser decide what the encoding format was:

1. HTTP headers: The server tells the browser what encoding those bytes should be interpreted as, using HTTP header:

Content-Type: text/html; charset=UTF-8

2. Byte Order Mark (BOM): Some files start with a special signature (only for UTF-8/16/32). If BOM is detected, browser knows encoding immediately.

3. Browser finds <meta charset="UTF-8">: Since most of the browser uses UTF-8 as encoding, browser tries to find the binary bytes of
`<meta charset="UTF-8">` it is also in binary but the raw bytes are predictable. If browser finds the raw bytes, then the browser be like okay i get it  the real encoding is UTF-8, so it uses that encoding format to decode the bytes.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/24rue2z90pmrd73aj5ca.png)


---

### 6. The `<meta viewport>` for content width

This tag controls how our website is displayed on different screen sizes.

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

- name="viewport": This meta tag appplies to the viewport (the visible area of the web page)

- content="width=device-width": Set the page width equal to the device's screen width

- initial-scale=1.0: This controls the zoom level when the page loads.
1.0 = 100% zoom
2.0 = 200% zoom

---

### 7. Description Meta Tag: This tag tells the metadata about the website

`<meta name="description" content="This is my personal website">`

- name="description": This tell the page description
- content="This is my personal website": What the page is about.

Google often uses this for understanding our content and serve our content to similary people.

---

### 8. Author Meta Tag: Defines the author of the page

`<meta name="author" content="Himanshu Bhatt">`

- name="author": Defines who created the page.
- content="Himanshu Bhatt": Tells the author of the page

Not really used by Google, but good for metadata completeness.


----

### 9. Complete Setup of Meta Tags.

```
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Personal portfolio of Himanshu Bhatt, full stack developer">
<meta name="author" content="Himanshu Bhatt">
```

---

### 10. Link Tag: The `<link>` tag is used inside <head> to connect external resources to our HTML.

`<link rel="stylesheet" href="style.css">`

<link> is used for
- CSS files
- Favicon
- Fonts
- Preloading resources
- Icons

Core Attributes
- rel (Relationship) - Required: Defines what the linked resources is
`<link rel="stylesheet" href="/css/main.css">`

link can be
- Relative
- Absolute 
- CDN link

---

### 11. The `<script>` tag - Loading JavaScript

The script tag is used to add javascript. Now this can be done in two ways we can either add javascript as a link to another file. Or we can add inline javascript meaning adding javascript in the html file itself.

1. Linking JavaScript file:
`<script src="script.js"></script>`

2. Adding Inline JavaScript
```
<script>
  alert("Hello");
</script>
```

Core Attributes of <script>

- src: Loads external JavaScript.
`<script src="app.js"></script>`

- type: Define script type.
Defines script type.

`<script type="text/javascript"></script>`
`<script type="module"></script>`

- defer: If we specify defer attribute in script tag it downloads script in background, run after HTML parsing completes. It is recommended, here script executes after dom is ready, order is preserved & is non-blocking, it is best for most scripts.

`<script src="main.js" defer></script>`

- async: Downloads script in background AND executes immediately when ready. This doesn't guarantees execution order, it loads fast and order is unpredictable.

`<script src="analytics.js" async></script>`

The best place to keep `<script>` tag:
We can place our script tag inside head since we are specifying the defer attribute, html loads and parses first and once the dom is ready it downloads the script and then executes it. So the website behaves as expected.

---

### 12. The `<body>` Tag (For Visible Content)

This holds everything the user sees. 

Example of content inside <body>
- Headings
- Paragraphs
- Images
- Hyperlinks
- Buttons
- Forms
- Buttons

---

### 13. Complete HTML Skeleton based on what all things we discussed above

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Portfolio Website">
    <meta name="author" content="Himanshu Bhatt">
    <title>HTML Structure</title>
    <link rel="stylesheet" href="styles.css">
    <script src="index.js" defer></script>
  </head>
  <body>
    <header>
      <h1>My Website</h1>
    </header>

    <main>
      <p>This is my website content.</p>
    </main>

    <footer>
      <p>&copy 2026 My Website</p>
    </footer>
  </body>
</html>
```

---
