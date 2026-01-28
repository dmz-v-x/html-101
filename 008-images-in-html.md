## Images in HTML (`<img>` tag)

### 1. What is the `<img>` tag?

The `<img>` tag is used to **display images on a webpage**.

Important thing to remember:

- `<img>` is a **void element**  
- It does **not** have a closing tag

```html
<img>
```

The image itself is not inside the tag — it is **referenced using attributes**.

---

### 2. Basic Syntax of an Image

```html
<img src="images/logo.png" alt="Website logo">
```

Breakdown:

- `<img>` → image element  
- `src` → path to the image file  
- `alt` → alternative text  

Both `src` and `alt` are **extremely important**.

---

### 3. The `src` Attribute

`src` tells the browser **where the image file is located**.

#### Example: Relative path

```html
<img src="images/profile.jpg" alt="My profile photo">
```

Folder structure:

```
project/
├── index.html
└── images/
    └── profile.jpg
```

Browser logic:

```
Start at index.html → go into images → load profile.jpg
```

---

#### Example: Absolute URL

```html
<img src="https://example.com/images/logo.png" alt="Company logo">
```

Use absolute URLs when:
- Loading images from a CDN
- Linking external images

---

### 4️. The `alt` Attribute 

`alt` = **alternative text**

It is used when:
- Image fails to load
- Screen readers read the page
- Search engines index content

```html
<img src="cat.jpg" alt="Orange cat sitting on a sofa">
```

#### Why `alt` matters

- Accessibility for visually impaired users  
- Improves SEO  
- Required for valid, good HTML  

❌ Bad alt:
```html
<img src="cat.jpg" alt="">
```

✅ Good alt:
```html
<img src="cat.jpg" alt="Orange cat sitting on a sofa">
```

💡 Think of `alt` as:  
**“How would I describe this image to someone over the phone?”**

---

### 5. Image Size: `width` & `height`

You can control image size using attributes:

```html
<img src="photo.jpg" alt="Beach view" width="300" height="200">
```

- Values are in **pixels**
- Helps browser reserve space before image loads

⚠️ Best practice:
- Use CSS for styling
- Use HTML width/height to avoid layout shift

---

### 6. Relative vs Absolute Image Paths (Quick Recap)

#### Relative path

```html
<img src="images/logo.png" alt="Logo">
```

- Portable
- Works locally
- Recommended for most projects

---

#### Absolute path

```html
<img src="https://cdn.example.com/logo.png" alt="Logo">
```

- Works everywhere
- Depends on external source

---

### 7. Common Beginner Mistakes

❌ Forgetting the `alt` attribute  
❌ Wrong file path (`Images` vs `images`)  
❌ Using spaces in file names (`my photo.jpg`)  
❌ Relying only on HTML for styling images  

Correct naming:

```
profile-photo.jpg ✅
My Photo.jpg ❌
```

---

### 8. Accessibility & Best Practices

- Always include `alt`
- Keep image file sizes optimized
- Don’t put important text inside images
- Use descriptive file names

Good example:

```html
<img src="team-member-john.jpg" alt="John smiling, frontend developer">
```

---

