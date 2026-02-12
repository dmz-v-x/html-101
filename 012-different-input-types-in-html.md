## Different Input Types in HTML

### 1. First: How `<input>` Works in General

The `<input>` tag is a single self-closing element that changes behavior based on its `type` attribute:

```html
<input type="text">
<input type="email">
<input type="checkbox">
```

Same tag, different type → different UI & behavior.

### Shared important attributes (these work on many — not all — input types)

- `id` — connect `<label>` and for CSS/JS  
- `name` — used when submitting form data (key in the key=value pair)  
- `value` — the current value (default or set by user / set by code)  
- `placeholder` — hint text inside the field  
- `required` — cannot submit form if empty/invalid  
- `disabled` — input is “off” and not sent in form  
- `readonly` — visible but cannot be edited  
- `autocomplete` — control browser autofill  
- `min`, `max`, `step` — for number/date/time/range  
- `tabindex` — control keyboard tab order (advanced)  
- `title` — tooltip (use sparingly)

> Note: Not every attribute applies to every input type; the browser ignores irrelevant ones.

---

### 2. Text-like Inputs

### 2.1 `type="text"` — basic single-line text

The simplest, most common one.

```html
<label for="username">Username</label>
<input id="username" name="username" type="text">
```

Single-line text. No built-in validation unless you add attributes like `required`, `pattern`, `minlength` / `maxlength`.

**Useful attributes:**

```html
<input
  type="text"
  name="username"
  id="username"
  placeholder="Himanshu"
  minlength="3"
  maxlength="20"
  required
>
```

- `minlength` / `maxlength` — browser checks length  
- `required` — cannot submit empty  
- `placeholder` — hint (NOT a label)

---

### 3. `type="password"` — hidden characters

```html
<label for="password">Password</label>
<input id="password" name="password" type="password" required>
```

- Shows bullets/dots instead of characters
- Still just a text field internally
- Value is not encrypted in the browser; transport security requires HTTPS

Use for passwords, PINs.

---

### 4. `type="email"` — email-specific validation

```html
<label for="email">Email</label>
<input id="email" name="email" type="email" required>
```

- Browser checks if the text looks like an email (`@` and something after)
- Mobile devices show an email-friendly keyboard
- `multiple` allowed for comma-separated addresses:

```html
<input type="email" name="emails" multiple>
```

---

### 5. `type="number"` — numeric spinner

```html
<label for="age">Age</label>
<input id="age" name="age" type="number" min="0" max="120" step="1">
```

- Shows a number input and often spinner arrows
- `min`, `max`, `step` control allowed values
- Users may still type non-numeric characters in some browsers — validation will catch it
- In JS, `input.value` is a string — convert via `Number(value)` or `parseInt`

---

### 6. Date & Time Inputs (native pickers)

Modern browsers provide native pickers.

### `type="date"` — date picker

```html
<label for="dob">Date of Birth</label>
<input id="dob" name="dob" type="date">
```

- Value format: `YYYY-MM-DD`
- Add `min` / `max` to restrict

### `type="time"` — time picker

```html
<label for="meeting-time">Meeting time</label>
<input id="meeting-time" name="meeting_time" type="time">
```

- Value like `14:30`
- `step` accepts seconds (e.g. `step="900"` for 15-minute steps)

### `type="datetime-local"` — date + time without timezone

```html
<input type="datetime-local" name="appointment">
```

- Value: `YYYY-MM-DDTHH:MM` (browser dependent)
- Useful for local appointment scheduling

---

### 7. Choice Inputs: Radio & Checkbox

These are SUPER important and easy to misuse if you don’t understand the difference.

### 7.1 `type="radio"` — choose ONE from a group

```html
<fieldset>
  <legend>Gender</legend>

  <label>
    <input type="radio" name="gender" value="male">
    Male
  </label>

  <label>
    <input type="radio" name="gender" value="female">
    Female
  </label>

  <label>
    <input type="radio" name="gender" value="other">
    Other
  </label>
</fieldset>
```

Key rules:

- Radios are grouped by the **same `name`**
- Only one in the group can be checked
- Each should have a `value`
- Use `<fieldset>` + `<legend>` for accessibility

### 7.2 `type="checkbox"` — choose zero, one, or many

```html
<label>
  <input type="checkbox" name="subscribe" value="yes">
  Subscribe to newsletter
</label>
```

- Each checkbox is independent
- For groups with the same name, multiple checked values will be submitted as repeated keys (e.g. `skills=html&skills=css`)

Example group:

```html
<fieldset>
  <legend>Skills</legend>
  <label><input type="checkbox" name="skills" value="html"> HTML</label>
  <label><input type="checkbox" name="skills" value="css"> CSS</label>
  <label><input type="checkbox" name="skills" value="js"> JavaScript</label>
</fieldset>
```

---

### 8. `type="file"` — file upload (added — important)

```html
<label for="avatar">Upload avatar</label>
<input id="avatar" name="avatar" type="file" accept="image/*">
```

- Allows user to pick files from their device
- `accept` restricts file types (e.g., `image/*`, `.pdf`)
- `multiple` attribute allows multiple files:
  ```html
  <input type="file" name="photos" multiple accept="image/*">
  ```
- Files are submitted as `multipart/form-data` (the form needs `enctype="multipart/form-data"` to send files properly)
- In JS, access selected files: `input.files` (FileList)

**Security note:** validate and sanitize files on server side; browsers only limit types on the client.

---

### 9. Hidden & Button Inputs: `hidden`, `submit`, `reset`, `button`

### `type="hidden"` — invisible field

```html
<input type="hidden" name="csrf_token" value="abc123">
```

- Not visible but included in submission
- Can be changed by users (devtools) — never trust on server

### `type="submit"` — submit button

```html
<input type="submit" value="Send">
```

- Submits the form
- Preferred alternative: `<button type="submit">Send</button>` (more flexible for icons/markup)

**Note:** Pressing Enter in a text input typically triggers the first submit button.

### `type="reset"` — reset all fields

```html
<input type="reset" value="Reset form">
```

- Resets inputs to their initial values
- Often avoided in modern UX because users can lose typed data accidentally

### `type="button"` — plain button (useful for JS actions)

```html
<button type="button" onclick="doSomething()">Click</button>
```

---

### 10. Other Useful Input Types (quick list)

- `type="search"` — search-specific (semantic; mobile keyboard may differ)
- `type="tel"` — telephone number (no browser validation, but mobile keyboards help)
- `type="url"` — URL validation (expects `https?://...`)

---

### 11. Important Attributes & Patterns (added / expanded)

### `pattern` — regex validation

```html
<input type="text" name="code" pattern="[A-Za-z0-9]{6}" title="6 alphanumeric characters">
```

- Browser checks pattern when submitting
- `title` can show a helpful hint in the browser message

### `minlength` / `maxlength`

- `minlength="3"` and `maxlength="20"` control length limits

### `multiple`

- On `input[type="email"]` or `input[type="file"]`, allows multiple values/files

### `accept` (for file inputs)

- `accept="image/*,.pdf"` restricts selectable files

### `inputmode` — hint keyboard type on mobile

```html
<input type="text" inputmode="numeric" pattern="[0-9]*">
```

- `inputmode="numeric"` hints to show numeric keypad

### `list` + `<datalist>` — suggest values while typing (lightweight autocomplete)

```html
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
</datalist>
```

- Not a replacement for server-side validation, but nice UX

### `form` attribute — associate input with a form by id (advanced but useful)

```html
<form id="signup" action="/signup" method="post"></form>

<input form="signup" name="email" type="email">
```

- Lets inputs live outside `<form>` element visually but still belong to it

### `autofocus` — focus when page loads (use carefully)

```html
<input autofocus>
```

- Only one input should have autofocus per page

### `disabled` vs `readonly`

- `disabled` — omitted in submission, not focusable  
- `readonly` — included in submission, focusable but not editable

### `checked` (radios/checkboxes)

- Use `checked` attribute to set default checked state:

```html
<input type="checkbox" name="agree" checked>
```

---

### 12. Value, Default Value & How Data Is Sent

- The `value` attribute sets the initial value in the HTML.
- The **current value** (what user typed) is what the browser sends.
- For checkboxes/radios, the `value` attribute is sent when the control is checked.
- For multiple checkboxes with same `name`, the server receives repeated keys (`skills=html&skills=css`).
- If an input has **no `name`**, it is ignored during submission — always include `name` for fields you want sent.

---

### 13. Basic JavaScript Notes (added)

- Read value: `const val = document.querySelector('#email').value;` (returns string)
- For checkboxes: `input.checked` is a boolean
- For file inputs: `input.files` is a `FileList`
- Input events:
  - `input` fires on every change (as user types)
  - `change` fires when the value is committed (blur or selection)
- Prevent form submission in JS:

```js
form.addEventListener('submit', function (e) {
  e.preventDefault(); // stop default submit
  // validate and send via fetch/ajax
});
```

### Constraint Validation API (browser-side)

- `input.checkValidity()` returns `true/false`
- `form.reportValidity()` shows browser validation UI
- `input.setCustomValidity('Custom message')` sets a custom validation message

Browser validation is helpful but never replaces server-side validation.

---

### 14. Validation & Security (reminder)

- HTML validation (`required`, `pattern`, `type="email"`, etc.) is **useful UX**, but **not secure**.
- Always validate and sanitize on the **server**.
- For sensitive data, always use **HTTPS**.
- Never trust hidden inputs or values from the client.

---

### 15. Best Practices & Accessibility Tips (noob-friendly checklist)

- Always use `<label>` for inputs (or visually hidden labels)  
- Give inputs `name` attributes if you want them to be submitted  
- Use `required` for fields that must be filled in  
- Use appropriate `type` (email/tel/number/date) to help mobile users  
- Avoid relying on `placeholder` as the only label  
- Use `fieldset` + `legend` for grouped radios/checkboxes  
- Put helpful `title` or `aria-describedby` for extra context when needed  
- Use `accept` for file types and `multiple` only when relevant  
- Use `inputmode` to improve mobile keyboards for numeric input  
- Test forms on desktop and mobile — mobile keyboards and pickers differ

---

### 16. Example: Complete Form Using Many Concepts

```html
<form action="/register" method="post" enctype="multipart/form-data">
  <div>
    <label for="name">Full name</label>
    <input id="name" name="name" type="text" required minlength="3" maxlength="50" autocomplete="name">
  </div>

  <div>
    <label for="email">Email</label>
    <input id="email" name="email" type="email" required autocomplete="email">
  </div>

  <div>
    <label for="avatar">Avatar</label>
    <input id="avatar" name="avatar" type="file" accept="image/*">
  </div>

  <fieldset>
    <legend>Skills</legend>
    <label><input type="checkbox" name="skills" value="html"> HTML</label>
    <label><input type="checkbox" name="skills" value="css"> CSS</label>
    <label><input type="checkbox" name="skills" value="js"> JavaScript</label>
  </fieldset>

  <div>
    <label for="age">Age</label>
    <input id="age" name="age" type="number" min="0" max="120">
  </div>

  <button type="submit">Register</button>
</form>
```

---
