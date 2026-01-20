## Text Formatting, Quotes & Code Formatting

### 1. HTML Text Formatting Tags

- `<strong>`: This tag show importance semantically, and visually it makes the text bold. So `<strong>` should be used where want to show something important rather than using `<b>`.

Syntax: `<strong>Warning</strong>`

When to use:
Use when text is important, not just bold-looking.

- `<em>`: This tag should be used when we want to add stress or emphasis, screen readers changes tone when they come across that is wrapped around `<em>` tag. Visually it makes the text italics.

Syntax: I `<em>really</em>` sorry

When to use:
Use when we want to show emphasis, not just italics.

- `<b>`: This tag makes our text to appear bold. It has no semantic meaning.

Syntax: `<b>Hi There!</b>`

When to use:
Use when we want to make text appear bold but no importance.

- `<i>`: This tag makes our text to appear italics. It has no semantic meaning.

Syntax: `<i>Hi There!</i>`

When to use:
Use when we want to make text appear italics but no importance.

- Comparison: strong vs b / em vs i

| Tag    | Visual | Semantic meaning | Screen reader |
| ------ | ------ | ---------------- | ------------- |
| strong | Bold   | ✅ Yes           | Emphasized   |
| b      | Bold   | ❌ No            | Normal       |
| em     | Italic | ✅ Yes           | Emphasized   |
| i      | Italic | ❌ No            | Normal       |

- `<u>`: Underlines text visually.

Syntax: `<u>This is underlined</u>`

When to use: 
`<u>` should NOT be used to indicate importance.
It is mainly used for annotations, misspellings, or stylistic purposes.

- `<mark>`: This tag makes text highligted with yellow background

Syntax: `This is a <mark>highlighted</mark> word`

When to use:
Use to highlight relevant or matched text (e.g. search results).

- `<small>`: This tag makes text to appear small on the screen.

Syntax: `<small>Terms and conditions apply </small>`

When to use:
Often used for disclaimers or legal notes.

- `<del>`: This shows strikethrough in the text.

Syntax: `<del>$50</del> 30`

When to use: 
Represent removed/obsolete content, for price reductions, version changes, corrections

- `<sup>`: This raises text above line, sup means Superscript.

Syntax: `x<sup>2</sup>`

When to use:
Used when we want to perform math exponets.

- `<sub>`: This lowers the text below baseline, sub means Subscript.

Syntax: `H<sub>2</sub>O`

When to use:
Used in chemical formulas or Scientific expressions.

- `<abbr>`: Used for abbreviations with a full form.

Syntax:
`<abbr title="HyperText Markup Language">HTML</abbr>`

When to use:
Helps accessibility and shows meaning on hover.


---

### 2. Quotes in HTML

- `<blockquote>`: Used for long quotes or cited section that should stand apart from the main content. This displays the content on a separate block, indented by default and starts on a new line.

Syntax: 

```
<blockquote>
  This is a long quoted section from another source.
</blockquote>
```

We can use cite attribute to specify where the quote came from.

```
<blockquote>
  The future belongs to those who believe in the beauty of their dreams.
</blockquote>
<cite>— Eleanor Roosevelt</cite>
```

When to use:
When you want to quote something from another source.

- `<cite>`: Used to reference the source of a quote or creative work.

Syntax:
`<cite>— Eleanor Roosevelt</cite>`

When to use:
Use it to attribute quotes, books, articles, or authors.


- `q`: Used for short quotes inside a sentence, q for Inline Quote. When used browser automatically adds quotation marks.

Syntax:

```
<p>
  He said, <q>HTML is easy to learn</q> and smiled.
</p>
```

When to use: 
Use when quote is part of a line, it should not break text flow.

- Key Differences:

| Feature          | `<blockquote>` | `<q>`           |
| ---------------- | -------------- | --------------- |
| Display          | Block-level    | Inline          |
| Usage            | Long quotes    | Short quotes    |
| Line break       | Yes            | No              |
| Default styling  | Indented       | Quotation marks |
| Semantic meaning | Quoted section | Quoted phrase   |

---

### 3. Code Formatting Tags

- `<code>`: Used to represent short snippets of code inside a sentence. It keeps the code inline with surrounding text.

Syntax:

`<p>Use the <code>console.log()</code>function to debug.</p>`

When to use:
Use when we want to show short commands, file names, variables etc. 
When we want to show the code inline with the text.

- `<pre>`: Used to display multi-line code or content exactly as written.

Syntax:

```
<pre>
  function greet(){
    console.log("Hello World");
  }
</pre>
```

When to use:
Use when we want to show multi-line code, and wants to preserve spaces, preserve identation, preserve line break and display as is.

- Using `<pre>` & `<code>` together

For real code blocks we should nest them as:

```
<pre><code>
function add(a, b) {
  return a + b;
}
</code></pre>
``` 

`<pre>` preserve formatting, `<code>` gives semantic meaning.

---
