---
title: "Front end practice: CSS and SCSS"
seoTitle: "Front end practice: CSS and SCSS"
seoDescription: "Looking to enhance your front-end development skills? Explore the world of CSS and SCSS in this hands-on frontend practice project."
datePublished: Thu Jul 27 2023 04:00:09 GMT+0000 (Coordinated Universal Time)
cuid: clkkmmbpu000209l9asxl1ifh
slug: front-end-practice-css-and-scss
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690398384289/03462ba4-d1e8-4d8f-924d-d72fcba0c3ed.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690398428877/21593b15-eee7-4c86-827a-9494605a6ecc.png
tags: css, sass, frontend-development

---

Let's go through some CSS best practices with examples:

# In CSS

1. **Use External Stylesheets:**
    
    Instead of inline styles or internal styles, prefer using external stylesheets. Create a separate CSS file and link it to your HTML documents. This promotes code reusability and maintainability.
    
    **Example:** styles.css
    
    ```css
     /* styles.css */
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      color: #333;
    }
    ```
    
    index.html
    
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
      <!-- Your content here -->
    </body>
    </html>
    ```
    
2. **Follow a CSS Methodology:** Use a CSS methodology like BEM (Block, Element, Modifier) to organize your CSS classes and make them more manageable.
    
    **Example:**
    
    ```xml
    <div class="header">
      <h1 class="header__title">Welcome to our website</h1>
    </div>
    ```
    
    ```css
    /* styles.css */
    .header {
      background-color: #007bff;
      padding: 20px;
    }
    
    .header__title {
      color: #fff;
      font-size: 24px;
    }
    ```
    
3. **Avoid Using IDs for Styling:** IDs have higher specificity than classes, which can lead to issues with overriding styles. Reserve IDs for JavaScript interactions, and use classes for styling.
    
    **HTML:**
    
    ```xml
    <div class="header" id="main-header">
      <h1 class="header-title">Welcome to our Website</h1>
    </div>
    ```
    
    **CSS (Avoiding IDs for Styling):**
    
    ```css
    /* styles.css */
    .header {
      /* Common styles for all headers */
      font-size: 24px;
      color: #333;
      text-align: center;
      padding: 20px;
      background-color: #f0f0f0;
    }
    
    /* Specific styles for the main header */
    #main-header {
      /* Avoid styling directly using the ID */
      border-bottom: 2px solid #007bff;
    }
    ```
    
4. **Keep Selectors Specificity Low:** Use simple selectors and avoid deep nesting of classes. This makes your styles more maintainable and reduces the risk of unintended style overrides.
    
    **HTML:**
    
    ```xml
    <div class="container">
      <h2 class="section-title">Section Title</h2>
      <p class="section-text">This is some text in the section.</p>
    </div>
    ```
    
    **CSS (Keeping Selectors Specificity Low):**
    
    ```css
    /* styles.css */
    .container {
      /* Specificity kept low for container class */
      background-color: #f0f0f0;
      padding: 20px;
    }
    
    .container .section-title {
      /* Specificity kept low for section title */
      font-size: 24px;
      color: #007bff;
    }
    
    .container .section-text {
      /* Specificity kept low for section text */
      font-size: 16px;
      color: #333;
    }
    ```
    
    In this example, we keep the selectors' specificity low by using class selectors. We avoid using IDs or element selectors, which would increase the specificity and make it harder to override the styles. By utilizing class selectors for styling, we maintain a more modular and flexible approach, allowing easier style changes and better separation of concerns.
    
5. **Limit the Use of !important:** Avoid using `!important` to override styles. Instead, refactor your CSS to have better specificity or use more specific selectors.
    
    **HTML:**
    
    ```xml
    <button class="btn btn-primary">Click Me</button>
    ```
    
    **CSS (Avoiding !important):**
    
    ```css
    /* styles.css */
    .btn {
      padding: 10px 20px;
      border: none;
      cursor: pointer;
      font-size: 16px;
    }
    
    .btn-primary {
      background-color: #007bff;
      color: #fff;
    }
    
    /* Avoid using !important, and instead, use proper class specificity */
    ```
    
    In this example, we avoid using `!important`. We rely on class selectors for styling, which helps maintain the proper specificity. By using the appropriate class selectors, we ensure that the `.btn-primary` styles will take precedence over the base `.btn` styles. It's crucial to use proper class naming and specificity instead of resorting to `!important` to maintain a clean and maintainable codebase.
    
6. **Use Flexbox or Grid for Layouts:** Embrace CSS Flexbox or Grid for creating responsive and flexible page layouts, as they provide powerful layout capabilities.
    
    **Example:**
    
    ```css
    /* styles.css */
    .container {
      display: flex;
      justify-content: space-between;
    }
    
    .sidebar {
      flex-basis: 30%;
    }
    
    .main-content {
      flex-basis: 70%;
    }
    ```
    
    ```xml
    <div class="container">
      <div class="sidebar">
        <!-- Sidebar content -->
      </div>
      <div class="main-content">
        <!-- Main content -->
      </div>
    </div>
    ```
    
7. **Use CSS Variables (Custom Properties):** Leverage CSS variables to store and reuse values throughout your stylesheet. They promote consistency and make it easier to update global styles.
    
    **Example:**
    
    ```css
    /* styles.css */
    :root {
      --primary-color: #007bff;
    }
    
    .button {
      background-color: var(--primary-color);
    }
    ```
    
8. **Optimize and Minify CSS:** Minimize your CSS file by removing unnecessary whitespace and comments. You can use various tools and plugins to automate this process during build or deployment.
    

By following these CSS best practices, you can write cleaner, maintainable, and performant stylesheets, making your front-end development process more efficient and effective.

# In SCSS

1. **Use Nested Selectors Wisely**: SCSS allows you to nest selectors, but nesting too deeply can result in overly specific CSS output and increase the risk of CSS specificity conflicts. Avoid nesting beyond three levels whenever possible.
    
    ```css
    
    .header {
      .nav {
        ul {
          li {
            a {
              color: blue;
            }
          }
        }
      }
    }
    
    // Better practice: Limit nesting
    .header {
      .nav {
        li {
          a {
            color: blue;
          }
        }
      }
    }
    ```
    
2. **Use Variables**: Take advantage of variables to store reusable values like colors, font sizes, or spacing. This makes it easier to maintain and modify your styles consistently.
    
    ```scss
    
    $primary-color: #007bff;
    $font-size-base: 16px;
    
    // Usage
    .header {
      background-color: $primary-color;
      font-size: $font-size-base;
    }
    ```
    
3. **Avoid ID Selectors**: Prefer using class selectors over ID selectors. ID selectors have higher specificity, making them harder to override and lead to inflexible CSS.
    
    ```scss
    // Bad practice: Using ID selector
    #main-container {
      // styles...
    }
    
    // Better practice: Using class selector
    .main-container {
      // styles...
    }
    ```
    
4. **Modularize with Partials**: Split your SCSS code into smaller partial files. This helps organize your styles and makes them more manageable.
    
    ```scss
    styles/
    |-- _variables.scss
    |-- _header.scss
    |-- _footer.scss
    |-- main.scss
    ```
    
5. **Use @extend Sparingly**: While @extend can be useful for reusing styles, be cautious as it can lead to bloated CSS. Only use it when you need to share a significant amount of styles between selectors.
    
    ```scss
    // Bad practice: Overuse of @extend
    .button {
      border: 1px solid #ccc;
      padding: 10px;
    }
    
    .submit-button {
      @extend .button;
      background-color: #007bff;
    }
    
    .cancel-button {
      @extend .button;
      background-color: #dc3545;
    }
    
    // Better practice: Use classes instead of @extend
    .button {
      border: 1px solid #ccc;
      padding: 10px;
    }
    
    .submit-button {
      @extend .button;
      background-color: #007bff;
    }
    
    .cancel-button {
      @extend .button;
      background-color: #dc3545;
    }
    ```
    
6. **Use Mixins for Reusable Styles**: Mixins allow you to define reusable blocks of styles that can be included in multiple selectors.
    
    ```scss
    // Mixin
    @mixin button-styles {
      border: 1px solid #ccc;
      padding: 10px;
    }
    
    // Usage
    .button {
      @include button-styles;
    }
    
    .submit-button {
      @include button-styles;
      background-color: #007bff;
    }
    
    .cancel-button {
      @include button-styles;
      background-color: #dc3545;
    }
    ```
    
7. **Use % Placeholder Selectors for Extending**: When you need to extend styles but don't want to create additional CSS classes, use placeholder selectors with `%` to prevent generating extra CSS.
    
    ```scss
    // Placeholder selector
    %button-styles {
      border: 1px solid #ccc;
      padding: 10px;
    }
    
    // Usage
    .button {
      @extend %button-styles;
    }
    
    .submit-button {
      @extend %button-styles;
      background-color: #007bff;
    }
    
    .cancel-button {
      @extend %button-styles;
      background-color: #dc3545;
    }
    ```
    
8. **Use Parent Selector** `&`: The `&` symbol allows you to reference the parent selector, enabling you to create more specific styles.
    
    ```scss
    // Nested selector
    .button {
      &:hover {
        background-color: #ddd;
      }
    }
    
    // Output
    .button:hover {
      background-color: #ddd;
    }
    ```
    

These best practices should help you write cleaner, more maintainable SCSS code. Remember that the key to good SCSS is organization, reusability, and avoiding overly specific CSS output.

### Featured articles

1. [Dark light theme switch using CSS variable](https://lakshmananarumugam.com/the-simple-tricks-to-change-your-website-theme-based-on-day-and-night)
    
2. [API tutorial for beginner](https://lakshmananarumugam.com/api-tutorial-for-beginners-in-react-learn-api-in-10-minutes)