## Other Form Input Types

### 1. Where do these elements fit?

All these controls normally live **inside a `<form>`**, and they behave like `<input>` when submitting:

- They usually have a `name` (the key sent to the server).  
- They have a value (typed or chosen) that gets submitted.  
- They can (and should) be associated with `<label>` for accessibility.

Example:

```html
<form action="/submit" method="post">
  <label for="message">Message</label>
  <textarea id="message" name="message"></textarea>

  <label for="country">Country</label>
  <select id="country" name="country">
    <!-- options here -->
  </select>
</form>
```

---

### 2. `<textarea>` — multi-line text box

### What it is  
`<textarea>` is the multi-line version of `<input type="text">`. Use it when users will type longer content: messages, comments, bios, addresses.

### Basic syntax

```html
<label for="message">Your message</label>
<textarea id="message" name="message"></textarea>
```

Note: `<textarea>` **has an opening and closing tag**. The text between them is the default value:

```html
<textarea>Default text here</textarea>
```

### Common attributes

- `name` — key for submission  
- `rows` — visible number of lines (height)  
- `cols` — width in characters (old-school; CSS is preferred)  
- `placeholder` — hint text (not a label)  
- `required` — must fill before submit  
- `maxlength` — max characters allowed  
- `readonly` / `disabled` — like `<input>`  

Example:

```html
<textarea
  id="message"
  name="message"
  rows="5"
  placeholder="Type your message here..."
  required
></textarea>
```

### Resizing behavior

Browsers usually let users resize textareas (corner handle). Useful for usability, but you can control it with CSS:

```css
textarea {
  resize: vertical; /* allow vertical only */
  /* or */
  resize: none;     /* disable */
}
```

Options: `both` (default), `vertical`, `horizontal`, `none`.

### Accessibility tips for `<textarea>`

- Always pair with `<label>`:
  ```html
  <label for="feedback">Feedback</label>
  <textarea id="feedback" name="feedback"></textarea>
  ```
- `placeholder` is **not** a replacement for a label.
- If you hide a label visually, provide an accessible alternative (see visually-hidden pattern in previous posts).

---

### 3. `<select>` + `<option>` + `<optgroup>` — dropdowns and list boxes

These three elements work together to make select lists.

### Basic `select` structure

```html
<label for="country">Country</label>
<select id="country" name="country">
  <option value="">-- Select your country --</option>
  <option value="in">India</option>
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
</select>
```

- The text inside `<option>` is what users see.  
- The `value` attribute is what the server receives. If the user picks "United States", the server gets `country=us`.

### Default selected option

Use `selected` to mark the default:

```html
<option value="in" selected>India</option>
```

### Placeholder-like first option

To force users to pick a real value, a common pattern is a disabled, selected placeholder:

```html
<select id="role" name="role" required>
  <option value="" disabled selected>-- Select your role --</option>
  <option value="student">Student</option>
  <option value="dev">Developer</option>
  <option value="other">Other</option>
</select>
```

- `disabled` prevents re-selecting the placeholder  
- `required` ensures a non-empty choice

### Multiple selection (`multiple`)

Allow users to select many options:

```html
<label for="skills">Skills</label>
<select id="skills" name="skills" multiple size="4">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
  <option value="react">React</option>
</select>
```

- `multiple` → users can choose multiple items (Ctrl/Shift + click on desktop)  
- `size="4"` shows 4 rows by default (looks like list box)  
- Submission: `skills=html&skills=js` (multiple repeated keys)

### `<optgroup>` — grouping related options

When lists get long, group related items:

```html
<label for="city">City</label>
<select id="city" name="city">
  <optgroup label="India">
    <option value="delhi">Delhi</option>
    <option value="mumbai">Mumbai</option>
  </optgroup>
  <optgroup label="USA">
    <option value="nyc">New York</option>
    <option value="sf">San Francisco</option>
  </optgroup>
</select>
```

- `<optgroup label="...">` shows a category label; options inside are selectable.  
- `<optgroup>` itself is **not** selectable.

---

### 4. `<datalist>` — input suggestions (autocomplete-style)

`<datalist>` is a lightweight suggestion list for a normal `<input>`.

### How it works

```html
<label for="browser">Favorite browser</label>
<input id="browser" name="browser" list="browsers">

<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Edge">
  <option value="Safari">
  <option value="Brave">
</datalist>
```

- The input uses `list="browsers"` which points to `<datalist id="browsers">`.  
- As the user types, the browser shows suggestions. The user **can still type something not in the list** (unlike `<select>`).

### When to use `<datalist>`

- Suggest cities, tags, browsers, skills, etc.  
- Use when you want suggestions but also allow custom input.  
- Middle-ground between `<select>` (fixed) and `<input>` (free text).

### Formatting with extra info

You can include extra text inside `<option>` in some browsers:

```html
<datalist id="languages">
  <option value="JavaScript">Front-end and back-end</option>
  <option value="Python">Scripting and data</option>
</datalist>
```

- `value` is what goes into the input. The text content can provide extra clues (browser-dependent display).

---

### 5. Labels with these elements (always do this)

Always connect your controls to labels:

```html
<label for="bio">Bio</label>
<textarea id="bio" name="bio"></textarea>

<label for="country">Country</label>
<select id="country" name="country">...</select>

<label for="browser">Favorite browser</label>
<input id="browser" name="browser" list="browsers">
<datalist id="browsers">...</datalist>
```

Screen reader examples:

- “Bio, edit text”  
- “Country, combo box”  
- “Favorite browser, edit text with autocomplete”

Labels are critical for accessibility and usability.

---

### 6. Keyboard behavior (native interactions)

These elements come with built-in keyboard behavior:

- `Tab` to move forward, `Shift + Tab` to go back  
- On `<select>`:
  - `Space` or `Alt+Down` opens dropdown (OS dependent)  
  - Arrow keys move between options  
  - `Enter` or `Space` selects  
- `<textarea>`:
  - `Enter` adds a new line  
  - `Tab` usually moves out of the textarea (unless intercepted)  
- `<datalist>`:
  - Arrow keys to pick a suggestion  
  - `Enter` to apply suggestion

Native keyboard support means users can interact without a mouse — huge accessibility win.

---

### 7. Putting everything together — a realistic mini form

A complete small form using textarea, select, optgroup and datalist:

```html
<form action="/submit" method="post" class="profile-form">
  <div class="form-field">
    <label for="bio">Short Bio</label>
    <textarea
      id="bio"
      name="bio"
      rows="4"
      placeholder="Tell us a bit about yourself..."
      required
    ></textarea>
  </div>

  <div class="form-field">
    <label for="country">Country</label>
    <select id="country" name="country" required>
      <option value="" disabled selected>-- Select your country --</option>
      <optgroup label="Asia">
        <option value="in">India</option>
        <option value="jp">Japan</option>
      </optgroup>
      <optgroup label="Europe">
        <option value="de">Germany</option>
        <option value="fr">France</option>
      </optgroup>
    </select>
  </div>

  <div class="form-field">
    <label for="fav-lang">Favorite language</label>
    <input
      id="fav-lang"
      name="favorite_language"
      list="languages"
      placeholder="Start typing..."
    >
    <datalist id="languages">
      <option value="JavaScript">
      <option value="Python">
      <option value="Go">
      <option value="Rust">
    </datalist>
  </div>

  <button type="submit">Save Profile</button>
</form>
```

---

### 8. Extra important notes (submission & server behavior)

- **What gets submitted**:
  - For `<textarea>`: the inner text is the value sent for its `name`.  
  - For `<select>`: the `value` of the selected `<option>` is sent.  
  - For `<select multiple>`: each selected option is sent with the same `name` (repeated keys on server).  
  - For `<datalist>`: the input value (what the user typed or chose) is sent.

- **If a control has no `name`, it is ignored** when submitting. Always add `name` if you want the data on the server.

- **Default/placeholder options**: using a `value=""` placeholder plus `required` is a good pattern to force a meaningful choice.

- **Encoding for file uploads**: not directly relevant to textarea/select/datalist, but remember: if your form includes a file input, set `enctype="multipart/form-data"` on `<form>`.

- **Server parsing**:
  - For repeated keys (e.g., `skills=html&skills=js`), servers usually provide an array (check your backend framework docs).
  - For empty selects (`value=""`), server receives empty string — handle it server-side as "no selection".

---

###  Styling & UX tips (simple, practical)

- Remove default select/textarea styling cautiously — native controls give good UX.  
- Use CSS to control textarea width/height instead of `cols`. Example:

```css
textarea { width: 100%; max-width: 600px; }
select { min-width: 200px; }
```

- For long selects, consider searchable custom UI (JS) or `datalist` for suggestions.  
- For `select multiple`, consider checkboxes if many users struggle with multi-select UI on mobile.

---

### Accessibility checklist

- Label every control with `<label>` (or provide equivalent ARIA labels)  
- Use `<fieldset>` + `<legend>` for groups of radios/checkboxes  
- Use `optgroup` to group long option lists for clarity  
- Ensure `size` and `multiple` are usable on mobile — test!  
- Provide clear placeholder/help text with `aria-describedby` if necessary
