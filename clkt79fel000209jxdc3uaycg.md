---
title: "Front end practice: Top 15  HTML code
best practices for development"
seoTitle: "Front end practice: HTML"
seoDescription: "Nowadays developers write code in HTML. but, some people do not write properly. so, that is the motivation for me to write this article."
datePublished: Wed Aug 02 2023 04:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clkt79fel000209jxdc3uaycg
slug: front-end-practice-top-15-html-code-best-practices-for-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690924953422/f5edee42-91fc-42df-90a8-d586f21fd95e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690917301344/d5746933-425f-4d37-b11e-a33eccdd3080.png
tags: css, html5, beginners

---

Nowadays developers write code in HTML. but, some people do not write properly. so, that is the motivation for me to write this article.

Let's go through some front-end best practices for HTML with examples:

1. **Use Semantically Meaningful HTML:**
    
    Use HTML tags that convey the meaning of the content they represent. This improves accessibility and allows search engines to understand the structure of your page better.
    
    Example:
    
    ```xml
    <header>
      <h1>Welcome to My Blog</h1>
    </header>
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </nav>
    <main>
      <article>
        <h2>Blog Post Title</h2>
        <p>Here is the content of the blog post...</p>
      </article>
    </main>
    <footer>
      <p>&copy; 2023 My Blog. All rights reserved.</p>
    </footer>
    ```
    
    Explanation:
    
    * We use `<header>` to represent the introductory content of the page, which includes the main heading `<h1>`.
        
    * The navigation menu is placed inside the `<nav>` element with a list of links `<ul>` and list items `<li>`.
        
    * The main content of the page is inside the `<main>` element. Each blog post is wrapped in an `<article>` element, and we use `<h2>` for the blog post title.
        
2. **Valid HTML:**
    
    Always ensure that your HTML code adheres to the W3C standards and validate it regularly.
    
    Example:
    
    ```xml
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>My Website</title>
    </head>
    <body>
      <!-- Your content goes here -->
    </body>
    </html>
    ```
    
    Explanation:
    
    * The `<!DOCTYPE html>` declaration specifies the document type and version of HTML used.
        
    * The `<html>` element is the root element of the HTML document and the `lang` attribute indicates the language of the content.
        
    * The `<head>` section contains meta information like character encoding and viewport settings.
        
    * The `<body>` element contains the visible content of the page.
        
3. **Accessibility:**
    
    Make your HTML accessible to all users, including those with disabilities. Use appropriate ARIA attributes and provide alternative text for images.
    
    Example:
    
    ```xml
    <img src="profile.jpg" alt="John Doe" aria-label="Profile Picture">
    <button aria-expanded="false">Toggle Menu</button>
    ```
    
    Explanation:
    
    * The `alt` attribute in the `<img>` tag provides alternative text for screen readers if the image cannot be displayed.
        
    * The `aria-label` attribute in the `<img>` and `<button>` tags give additional context to screen readers about the purpose of the image and button, respectively.
        
4. **Responsive Design:**
    
    Create a responsive layout that adapts to different screen sizes using media queries and CSS Grid/Flexbox.
    
    Example:
    
    ```xml
    <main>
      <section class="container">
        <div class="item">Content 1</div>
        <div class="item">Content 2</div>
        <div class="item">Content 3</div>
      </section>
    </main>
    ```
    
    ```css
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
    }
    
    .item {
      background-color: #f2f2f2;
      padding: 10px;
    }
    ```
    
    Explanation:
    
    * We use the CSS Grid layout with the `.container` class to create a responsive grid.
        
    * The `grid-template-columns` property with `auto-fit` and `minmax()` ensures that the items adapt to the available width and maintain a minimum size of 300px.
        
5. **Avoid Inline Styles:**
    
    Separate your CSS from your HTML to keep your code clean and maintainable.
    
    Example:
    
    ```xml
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>My Website</title>
      <link rel="stylesheet" href="styles.css">
    </head>
    <body>
      <header>
        <h1>My Website</h1>
      </header>
      <!-- Your content goes here -->
    </body>
    </html>
    ```
    
    Explanation:
    
    * We use an external stylesheet by linking the `styles.css` file in the `<head>` section of the HTML document.
        
    * The actual CSS styles are written in the `styles.css` file, keeping the HTML clean and uncluttered.
        
6. **Optimize for SEO:**
    
    Improve your website's search engine optimization by using appropriate HTML tags for headings, meta tags, and structured data.
    
    Example:
    
    ```xml
    <head>
      <title>My Blog Post</title>
      <meta name="description" content="This is a blog post about something interesting.">
    </head>
    <body>
      <header>
        <h1>My Blog Post Title</h1>
        <p>Published on <time datetime="2023-08-02">August 2, 2023</time> by <span>John Doe</span></p>
      </header>
      <!-- Your content goes here -->
    </body>
    ```
    
    Explanation:
    
    * The `<title>` element sets the title of the web page, which is important for SEO.
        
    * The `<meta>` tag with the `description` attribute provides a concise summary of the content, which search engines may use for display purposes.
        
    * The `<time>` element with the `datetime` attribute represents the publication date of the blog post, which can be useful for search engines to understand the content's recency.
        
7. **Avoid Deprecated HTML Features:**
    
    Stay updated with the latest HTML standards and avoid using deprecated elements or attributes.
    
    Example:
    
    ```xml
    <main>
      <section>
        <h2>My Deprecated Example</h2>
        <font size="4" color="blue">This text is deprecated.</font>
      </section>
    </main>
    ```
    
    Explanation:
    
    * The `<font>` element with the `size` and `color` attributes have been deprecated and should not be used. Instead, use CSS to style your text.
        
8. **Test on Multiple Browsers:**
    
    Check your HTML on different browsers (e.g., Chrome, Firefox, Safari, Edge) to ensure cross-browser compatibility.
    
    Explanation:
    
    * As an example, open your web page in different browsers and check for any rendering issues or inconsistencies in the appearance or functionality.
        
9. **Use Web Fonts Wisely:**
    
    Limit the number of custom web fonts to minimize page loading times.
    
    Example:
    
    ```xml
    <head>
      <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap">
    </head>
    <body>
      <p style="font-family: 'Roboto', sans-serif;">This is some text using the Roboto font.</p>
    </body>
    ```
    
    Explanation:
    
    * In this example, we use the Google Fonts API to load the Roboto font. However, avoid loading too many custom fonts as it can slow down the page load.
        
10. **HTML Comments:**
    
    Use comments in your HTML code to explain complex sections or provide context for other developers.
    
    Example:
    
    ```xml
    <!-- This is a comment explaining the purpose of the following section -->
    <section>
      <h2>Section Title</h2>
      <p>Content goes here...</p>
    </section>
    ```
    
    Explanation:
    
    * Comments help to document your code, making it easier for other developers (or even your future self) to understand the code's purpose and functionality.
        
11. **Avoid Excessive Nesting:**
    
    Keep your HTML structure as flat as possible and avoid excessive nesting to improve code readability and performance.
    
    Example:
    
    ```xml
    <div class="container">
      <div class="header">
        <h1>My Website</h1>
      </div>
      <div class="content">
        <!-- Content goes here -->
      </div>
      <div class="footer">
        <p>&copy; 2023 My Website. All rights reserved.</p>
      </div>
    </div>
    ```
    
    Explanation:
    
    * In this example, we avoid the unnecessary nesting of multiple `<div>` Elements and use classes to style different sections of the page.
        
12. **Proper Form Structure:**
    
    Create well-structured and accessible forms, with proper labels and associated form controls.
    
    Example:
    
    ```xml
    <form>
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required>
    
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
    
      <button type="submit">Submit</button>
    </form>
    ```
    
    Explanation:
    
    * We use the `<label>` element with the `for` attribute to associate the label with its corresponding form control using the `id` of the input element.
        
    * The `required` attribute in the input elements ensures that the fields must be filled out before the form can be submitted.
        
13. **Data Tables with Semantic Markup:**
    
    Use semantic markup to create data tables, providing headers and structure for screen readers.
    
    Example:
    
    ```xml
    <table>
      <caption>Monthly Expenses</caption>
      <thead>
        <tr>
          <th scope="col">Category</th>
          <th scope="col">Amount</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Rent</td>
          <td>$1000</td>
        </tr>
        <tr>
          <td>Utilities</td>
          <td>$150</td>
        </tr>
      </tbody>
    </table>
    ```
    
    Explanation:
    
    * We use the `<caption>` element to provide a summary of the table's content.
        
    * The `<thead>` element contains table headers and the `<tbody>` element contains table data.
        
14. **Use Inline SVG for Scalability:**
    
    Use inline SVG for logos, icons, or graphics to ensure they scale properly and look crisp on different devices.
    
    (If you live VueJS then how to implement SVG icon set to [read this article](https://lakshmananarumugam.com/design-system-icons-for-vue-3))
    
    Example:
    
    ```xml
    <svg width="100" height="100" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="50" cy="50" r="40" fill="blue" />
    </svg>
    ```
    
    Explanation:
    
    * In this example, we create a simple blue circle using inline SVG.
        
    * The `width`, `height`, and `viewBox` attributes ensure that the SVG scales appropriately while maintaining its aspect ratio.
        
15. **Prefetching and Preloading Resources:**
    
    Improve performance by prefetching and preloading resources that will be used on other pages.
    
    Example:
    
    ```xml
    <head>
      <link rel="prefetch" href="about.html">
      <link rel="preload" href="styles.css" as="style">
      <link rel="preload" href="image.jpg" as="image">
    </head>
    ```
    
    Explanation:
    
    * The `prefetch` attribute hints to the browser to fetch the specified resource in the background, which can improve the loading speed of subsequent pages.
        
    * The `preload` attribute tells the browser to load the specified resource early in the page load process, reducing latency when the resource is required.
        
    
    **Thanks for reading :)**
    
    ## Popular articles
    
    1. [Front-end best practices series blog](https://lakshmananarumugam.com/series/front-end-practice)
        
    2. [Top 14 Common Code bug and Fixes in React with Examples](https://lakshmananarumugam.com/top-14-common-code-bug-and-fix-in-react-with-examples-2023)