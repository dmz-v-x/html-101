### 1. HTML Heading: `<h1>` - `<h6>`

Headings define the hierarchy and structure of our content.
Visually h1 is the biggest heading followed by h2, h3 ... h6.

Now that doesn't mean they are just for big text, they describe the importance of sections.

```
<h1>Main Title</h1>
<h2>Sub Section</h2>
<h3>Sub Sub Section</h3>
```

---

### 2. Heading Levels Explained

| Tag | Meaning            | Importance       |
| --- | ------------------ | ---------------- |
| h1  | Main page title    | Highest Priority |
| h2  | Section heading    | Secondary        |
| h3  | Sub-section        | More detail      |
| h4  | Minor subsection   | Lower            |
| h5  | Very minor heading | Even lower       |
| h6  | Smallest heading   | Lowest           |

Analogy with a book:

Book Title (h1) > Chapter (h2) > Section (h3) > Subsection (h4)
        

```
<h1>Web Development Guide</h1>

<h2>HTML Basics</h2>
<h3>Headings</h3>
<h3>Paragraphs</h3>

<h2>CSS Basics</h2>
<h3>Selectors</h3>
<h4>Class Selectors</h4>


This creates a logical structure.
```

---

### 3. Mistakes to Avoid

- ❌ DO NOT use headings just for size:

```
<h1>Big Text</h1>
<h4>Smaller Text</h4>
```


Use CSS for visual styling, not heading levels.

- ✅ Correct Way to Control Sizes
`<h1 class="title">Welcome</h1>`

```
.title {
  font-size: 20px;
}
```


Headings define structure, CSS defines appearance.

---

### 4. Visual Representation

Visual Representation

```
h1 - Website Title
│
├── h2 - Section
│     ├── h3 - Subsection
│     └── h3 - Subsection
│
└── h2 - Another Section
      └── h3 - Subsection
```

---

### 5. Browser Default Sizes

Approximate Default Sizes:

| Heading | Size   |
| ------- | ------ |
| h1      | 2em    |
| h2      | 1.5em  |
| h3      | 1.17em |
| h4      | 1em    |
| h5      | 0.83em |
| h6      | 0.67em |

---

### 6. Paragraph in HTML: The `<p>` tag

The `<p>` tag is used to define a block of text — a paragraph.

`<p>This is a paragraph.</p>`

It represents a complete thought or idea, just like paragraphs in a book.

---

### 7. `<p>` is a Block-level Element

This means, it takes full horizontal width, always starts on a new line. Can Contain inline elements (but not other block elements)

Allowed inside `<p>`:

- `<strong>`
- `<em>`
- `<span>`
- `<code>`

Not Allowed inside `<p>`:

- `<div>`
- `<h1>`
- `<section>`
- `<p>`

This is invalid:

```
<p>
  <div>This is wrong</div>
</p>
```

---

### 8. Default Styling

Browsers add spacing automatically:

margin-top: 1em
margin-bottom: 1em

Though we can override it with CSS:

```
p {
  margin: 0;
  line-height: 1.6;
}
```

---

### 9. Line Breaks `<br>` & `<hr>`

- `<br>`: Line Break 
The `<br>` tag creates a single line break inside text.
It tells the browser move the rest of the content to the next line.

Syntax: `<br>`

Example: 

```
<p>
  Hello John,<br>
  Thank you for your message.<br>
  We will get back to you soon.
</p>
```

- `<hr>`: Horizontal Rule
The `<hr>` tag inserts a thematic break between sections. 
Visually, it usually appears as a horizontal line.

Syntax: `<hr>`

Example:

```
<h2>Introduction</h2>
<p>This is the intro section.</p>

<hr>

<h2>Conclusion</h2>
<p>This is the conclusion section.</p>
```

---

### 10. Example of combining them both

```
<p>
  Dear User,<br>
  Your subscription will expire soon.<br>
  Please renew to continue services.
</p>

<hr>

<p>
  Support Team<br>
  support@example.com
</p>

```

---
