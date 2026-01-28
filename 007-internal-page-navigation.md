## Internal Page Navigation (Anchor / Hash Links)

### 1. What is Internal Page Navigation?

### Simple definition

**Internal page navigation** means:
👉 links that move you to **another section on the same page**.

Instead of navigating to another file like `about.html`, you jump to a specific part **inside the same HTML page**.

---

### Example behavior

- You click **“Contact”** in a navbar → the page scrolls down to the contact section  
- You click **“Back to top”** → the page jumps to the top  

These are often called:

- Anchor links  
- Hash links  
- In-page navigation  

All of them mean the same thing.

---

### 2. Core Idea: `id` + `href="#id"`

This is the **heart** of internal page navigation.

You always need **two things**:

1. A **target** → an element with an `id`
2. A **link** → an `<a>` tag whose `href` points to that `id` using `#`

---

#### Step 1: Give your section an `id`

```html
<section id="about">
  <h2>About Me</h2>
  <p>Some info about me...</p>
</section>
```

Explanation:

- `id="about"` gives this section a **unique name**
- `id` must be **unique** on the page  
  ❌ No two elements should have the same `id`

---

#### Step 2: Create a link to that `id`

```html
<a href="#about">Go to About section</a>
```

What `href="#about"` means:

👉 “Scroll to the element whose `id` is `about`”

When the user clicks the link:

- The browser scrolls to that section  
- The URL updates to something like:

```
index.html#about
```

---

#### Another simple example

```html
<h2 id="contact">Contact</h2>

<a href="#contact">Contact me</a>
```

Clicking the link scrolls directly to the **Contact** heading.

---

### 3. Making a Simple Internal Navigation Menu

Imagine a **single-page portfolio website**.

```html
<body>
  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>

  <section id="home">
    <h1>Home</h1>
  </section>

  <section id="about">
    <h1>About</h1>
  </section>

  <section id="projects">
    <h1>Projects</h1>
  </section>

  <section id="contact">
    <h1>Contact</h1>
  </section>
</body>
```

What’s happening here:

- Each section has a **unique `id`**
- Each navigation link uses `href="#that-id"`
- Clicking a nav link scrolls to the matching section

This is the **basic structure of a one-page website**.

---

### 4. “Back to Top” Links

A very common pattern on long pages is a **Back to top** link.

#### Step 1: Add the link at the bottom

```html
<a href="#top">Back to top</a>
```

---

#### Step 2: Add a target at the top of the page

```html
<body>
  <div id="top"></div>
  <!-- rest of the content -->
</body>
```

Now:

- Clicking **Back to top** scrolls to the top of the page
- Simple and effective

---

### 5. Accessibility Problem 

### The problem

For **keyboard and screen reader users**:

- They must press **Tab** many times
- Every time they open a page, they have to tab through the entire navigation
- Only then can they reach the main content

This can be frustrating.

---

### 6. Solution: “Skip to Main Content” Link

#### Step 1: Add this at the very top of your HTML

```html
<a href="#main-content" class="skip-link">
  Skip to main content
</a>
```

---

#### Step 2: Mark your main content

```html
<nav>
  <!-- navigation links -->
</nav>

<main id="main-content">
  <!-- main page content -->
</main>
```

---

#### How this helps

Now when a keyboard user:

1. Presses **Tab**
2. The “Skip to main content” link gets focus
3. Presses **Enter**
4. Instantly jumps to the main content

This is a **huge accessibility improvement** and considered best practice.

---

