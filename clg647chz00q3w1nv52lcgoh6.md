---
title: "The simple tricks to change your website theme based on day and night"
datePublished: Tue May 11 2021 18:53:42 GMT+0000 (Coordinated Universal Time)
cuid: clg647chz00q3w1nv52lcgoh6
slug: the-simple-tricks-to-change-your-website-theme-based-on-day-and-night
tags: css, css-tricks

---

Hi everyone, every website have a theme options. so, a website user able to choose their preferred theme like dark, light..etc., This is existing followed approach in everyone website.

how is it (we show the website theme based on the user day and night). I just tried. if you like it use in your website. give some different experience to your website user.

Let's jump into the implementation part:

For now, I take a simple coming soon html template for with dark and light theme.

{% codepen https://codepen.io/explore-free-projects/pen/zYZvewO %}

The above page theme change based on body attribute data-theme: "dark-theme" / "light-theme".

by default show `light-theme`.

Now, coming to main point how we change website theme based on day and night.

```css
function setThemePreference() {
  var d = new Date();
  /*
  * The getHours() method returns the hour (from 0 to 23) of the specified date and time.
  * Day = 0 - 11
  * Night = 12 - 23
  */
  var currentHour = d.getHours();
  
  /*
  * The dark theme load early morning and night
  * The light theme load morning and evening
  */

  if(currentHour >= 19 || currentHour <= 6) {
    document.body.setAttribute("data-theme", "dark_theme") 
  }else {
    document.body.setAttribute("data-theme", "light_theme") 
  }
}

window.onload = setThemePreference;
```

That's all.

The workable version of the [codepen URL](https://codepen.io/explore-free-projects/pen/zYZvewO)