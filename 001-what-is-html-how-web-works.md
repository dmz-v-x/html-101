## What is HTML & How Web Works

### 1. What HTML is and why it exists

Okay so first thing first what actually is HTML. So HTML stands for HyperText Markup Language (Nothing hyper about it). It is the standard language of web pages that defines the skeleton of a website. 

It tells the browser, what exact content exists for the website, what type of content it is. How it is organized. That's it.

---

### 2. What HTML can and cannot do in a website

It defines Headings, create paragraphs, display images, we can build forms, and few other stuff.

It doesn't add any style (CSS, we'll see that later) or behavior/interactivity (JavaScript, we'll see this later too😜)

---

### 3. Understanding HTML as the structure (skeleton) of the web

Also if you're wondering what HTML actually looks like this is what it looks like: 

```
<!DOCTYPE html>
<html>
<head>
  <title>My First Page</title>
</head>
<body>
  <h1>Hello World</h1>
  <p>This is my first webpage</p>
</body>
</html>

```
Don't worry if you don't get this right now we'll understand each and every word mentioned above in great detail in next blog.

Btw the above markup just tell show a big heading that says 'Hello World' and below it a paragraph that says 'This is my first webpage'

---



### 4. The roles of HTML, CSS, and JavaScript in a web application

| Technology | Role                  |
| ---------- | --------------------- |
| HTML       | Structure (bones)     |
| CSS        | Design (skin/clothes) |
| JavaScript | Functionality (brain) |

A website without CSS & JS still works, but looks plain.

---

### 5. What actually happens inside the browser when a page loads (DOM, CSS, JS)

So whenever you load a website, the browser first reads the HTML line by line. Converts it into a DOM (Document Object Model, don't worry about that now) just think of it as a tree structure that represents our HTML structure and tells at what position what things lies in our html page, how the page content will be displayed to the user.

Then browser downloads the linked CSS & JS apply respective styles and executes scripts to add interactivity. And then it displays the final page.

In simple terms, the browser flow looks like this:

HTML → DOM → CSS applied → JavaScript runs → Final page

---
