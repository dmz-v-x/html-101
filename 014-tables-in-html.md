## Tables in HTML

### 1. What is a table actually for?

A table is for **tabular data** — information that fits naturally into rows and columns.

**Examples:**
- Student marks: `Name | Subject | Score`  
- Pricing table: `Plan | Price | Features`  
- Schedule: `Day | Time | Activity`

**Important rule:**  
A table is **not** for layout. Don’t use `<table>` to place header/main/footer on a page. Use semantic HTML + CSS.

Bad old example (do not use):

```html
<!-- ❌ bad, old practice -->
<table>
  <tr><td>Header</td></tr>
  <tr><td>Main content here</td></tr>
  <tr><td>Footer</td></tr>
</table>
```

---

### 2. Basic table building blocks: `<table>`, `<tr>`, `<td>`, `<th>`

Start tiny — build up.

### 2.1 Minimal table

```html
<table>
  <tr>
    <td>Himanshu</td>
    <td>95</td>
  </tr>
</table>
```

- `<table>` wraps the whole table  
- `<tr>` = table row  
- `<td>` = table data (cell)

This example is **one row** and **two columns**.

---

### 3. Adding headers with `<th>`

Headers explain what each column means.

```html
<table>
  <tr>
    <th>Name</th>
    <th>Score</th>
  </tr>
  <tr>
    <td>Himanshu</td>
    <td>95</td>
  </tr>
  <tr>
    <td>Alex</td>
    <td>88</td>
  </tr>
</table>
```

- `<th>` cells are headers (browsers show them bold/centered by default).
- Use `<th>` instead of styling `<td>` as bold — semantics matter.

---

### 4. Concept: rows and columns

Think in table terms: rows run left→right, columns run top→bottom.

Markdown view:

| Name  | Subject | Score |
| ----- | ------- | ----- |
| Alice | Math    | 95    |
| Bob   | English | 88    |

HTML:

```html
<table>
  <tr>
    <th>Name</th>
    <th>Subject</th>
    <th>Score</th>
  </tr>
  <tr>
    <td>Alice</td>
    <td>Math</td>
    <td>95</td>
  </tr>
  <tr>
    <td>Bob</td>
    <td>English</td>
    <td>88</td>
  </tr>
</table>
```

---

### 5. `<thead>`, `<tbody>`, `<tfoot>` — grouping table parts

These tags don't change data — they **organize** it. They help CSS, accessibility, printing, and large tables.

### 5.1 `<thead>` — header rows

Use for the header row(s):

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Subject</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>...</tbody>
</table>
```

### 5.2 `<tbody>` — table body

Wrap main data rows:

```html
<tbody>
  <tr>...</tr>
  <tr>...</tr>
</tbody>
```

Browsers add `<tbody>` automatically if missing — but write it yourself for clarity.

### 5.3 `<tfoot>` — footer (totals/summary)

Used for totals or summary rows:

```html
<tfoot>
  <tr>
    <th>Total</th>
    <td>185</td>
  </tr>
</tfoot>
```

Fun fact: browsers can render `<tfoot>` before `<tbody>` on print so footers repeat on printed pages.

---

### 6. `colspan` & `rowspan` — merging cells

Sometimes a single cell must cover multiple columns or rows.

### 6.1 `colspan` — horizontally merge (span across columns)

Example: a title spanning 3 columns:

```html
<table>
  <thead>
    <tr>
      <th colspan="3">Student Marks</th>
    </tr>
    <tr>
      <th>Name</th>
      <th>Subject</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>Math</td>
      <td>95</td>
    </tr>
  </tbody>
</table>
```

`colspan="3"` → that cell covers 3 columns.

### 6.2 `rowspan` — vertically merge (span across rows)

Example: same name for multiple subjects:

```html
<table>
  <tr>
    <td rowspan="2">Alice</td>
    <td>Math</td>
    <td>95</td>
  </tr>
  <tr>
    <td>Science</td>
    <td>90</td>
  </tr>
</table>
```

`rowspan="2"` makes the first cell extend down into the next row.

---

### 7. Table captions — `<caption>`

A caption describes the whole table. It is read by screen readers and helps users understand the table.

```html
<table>
  <caption>Student Scores for Term 1</caption>
  <thead>...</thead>
  <tbody>...</tbody>
</table>
```

Rules:
- `<caption>` must be the **first child** inside `<table>`.  
- Only one caption per table.

Why use it? Screen readers announce the caption before the table. Good for clarity and SEO.

---

### 8. Use `<th>` for headers and `scope` attributes

To help screen readers, mark header scope:

```html
<table>
  <caption>Student Scores</caption>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Subject</th>
      <th scope="col">Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Alice</th>
      <td>Math</td>
      <td>95</td>
    </tr>
    <tr>
      <th scope="row">Bob</th>
      <td>Science</td>
      <td>90</td>
    </tr>
  </tbody>
</table>
```

- `scope="col"` marks column headers.
- `scope="row"` marks row headers.

Screen readers can then announce both row & column headers for any cell.

### 8.1 When `scope` is not enough — `id` + `headers` (advanced)

For very complex tables with multi-layered headers and many merged cells, use `id` on header `<th>` and `headers` attribute on `<td>` to explicitly map which headers apply to the cell:

```html
<th id="h-name">Name</th>
<th id="h-math">Math</th>

<td headers="h-name h-math">95</td>
```

This is advanced and usually not needed for simple tables, but good to know.

---

### 9. Accessibility & keyboard reading (added — very important)

Tables must be accessible:

- Always provide meaningful header cells (`<th>`) and a `<caption>`.  
- Use `scope` or `headers` to help assistive tech map cells.  
- Avoid using tables for layout — screen readers expect tabular data.  
- For complex interactive tables, consider `role="table"`, `role="row"`, `role="columnheader"` etc. only if native semantics are insufficient (native elements are best when possible).  
- Keyboard users: ensure focusable controls inside tables are reachable (links, buttons, inputs).

**Screen reader behavior:**  
When a user navigates to a table, the screen reader typically announces table size (rows × columns) and then can move cell-by-cell. Proper headers & caption let the user understand context.

---

### 10. Responsive tables & UX on small screens (added)

Tables are wide. On small screens they can overflow. Options:

### Option A — Horizontal scroll (simple, safe)

Wrap table in a scroll container:

```html
<div class="table-wrap">
  <table>...</table>
</div>
```

CSS:

```css
.table-wrap {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}
table { width: 100%; border-collapse: collapse; }
```

This preserves the table layout and lets users scroll horizontally.

### Option B — Stack rows into cards (complex, needs JS/CSS)

Convert each row into stacked cards for mobile. This requires JS or CSS tricks (`display: block` on rows, `data-label` attributes) — only use if you need better mobile readability.

### Option C — Hide low-priority columns

Use CSS media queries to hide less-important columns on small screens:

```css
@media (max-width: 600px) {
  .col-optional { display: none; }
}
```

**Best practice:** prefer horizontal scroll for data tables — it's predictable and preserves relationships.

---

### 11. Styling tables with CSS basics (added)

Simple CSS improves readability:

```css
table {
  width: 100%;
  border-collapse: collapse;
  border: 1px solid #ddd;
  font-family: system-ui, Arial, sans-serif;
}

th, td {
  padding: 8px 12px;
  border: 1px solid #e5e7eb;
  text-align: left;
}

thead th {
  background: #f3f4f6;
  font-weight: 600;
}

tbody tr:nth-child(odd) {
  background: #ffffff;
}

tbody tr:nth-child(even) {
  background: #fbfbfb; /* zebra stripes */
}
```

### `table-layout` property

- `table-layout: auto` (default) — browser calculates column widths from content (can be slow for big tables).  
- `table-layout: fixed` — columns are sized based on table width and `width` on `th`/`td`. Faster and more predictable:

```css
table { table-layout: fixed; }
th:first-child, td:first-child { width: 30%; }
```

### Borders

- `border-collapse: collapse;` removes double borders and is commonly used.
- `border-spacing` gives space between cells when `border-collapse: separate` is used.

---

### 12. Complex table example (combine concepts)

```html
<table>
  <caption>Class Scores</caption>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Math</th>
      <th scope="col">Science</th>
      <th scope="col">Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Alice</th>
      <td>95</td>
      <td>90</td>
      <td>185</td>
    </tr>
    <tr>
      <th scope="row">Bob</th>
      <td>88</td>
      <td>92</td>
      <td>180</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Total</th>
      <td>183</td>
      <td>182</td>
      <td>365</td>
    </tr>
  </tfoot>
</table>
```

This uses `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `scope` on headers and a footer row.

---

### 13. Best practices checklist & common mistakes

### Best practices
- Only use tables for tabular data (not layout).  
- Always include meaningful `<th>` headers.  
- Use `<caption>` to describe the table.  
- Group rows with `<thead>`, `<tbody>`, `<tfoot>`.  
- Use `scope` on header cells for accessibility.  
- Add `role` or `headers` only when necessary — prefer native semantics.  
- Add horizontal scrolling wrapper for responsive behavior.  
- Use CSS for styling (zebra stripes, spacing).  
- Test keyboard and screen-reader navigation.  
- Keep tables small and focused — large tables may need search, filter, or pagination.

### Common mistakes
- Using tables for page layout.  
- Missing headers (`<th>`) — makes tables hard to understand.  
- Forgetting `caption` — deprives screen-reader users of context.  
- Not handling overflow on mobile.  
- Styling table with inline attributes rather than CSS (hard to maintain).  
- Overcomplicating `rowspan` / `colspan` without clear reason — hard to maintain.
