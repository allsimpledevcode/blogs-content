---
title: "Build dynamic wallpaper on chrome"
datePublished: Tue Jun 15 2021 18:07:04 GMT+0000 (Coordinated Universal Time)
cuid: clg645kbp00vpuonveqwt2too
slug: build-dynamic-wallpaper-on-chrome
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845735347/0722d490-af36-4733-b5e7-2e583c37c2f3.jpeg

---

##Introduction
  Most of the web user uses the chrome web browser for searching things on the internet. so, here I share the dynamic wallpaper using chrome browser. but, the same concept we able to do in other browsers also, like firefox, safari...etc.,

###Dynamic theme on chrome browser
  In chrome browser, the new tab screen will be the home screen. whenever we open it. it will show first. so, in this article, I will share `how to replace the new tab screen and add our own features`.

###How to replace the chrome new tab screen?
Answer: **Chrome extension**

###Let's start the development.
1.build a screen using front-end lightweight library.
I personally choose the Vue app for example. if you things any other light-weighted app. you will use it.

```json
# In your system not installed vue-cli. the below command to use and install it.
$ yarn global add @vue/cli
$ vue create hello-world #I chose vue 3
```

2.create a `manifest.json` and add the below lines. Then, put the file into the public folder inside the Vue app.

```json
{
  "name": "<App name>",
  "description": "<App description>",
  "version": "1.0",
  "manifest_version": 3,
  "permissions": ["tabs"],
  "chrome_url_overrides": {    
    "newtab": "index.html"  ##Mention the file name. which is need to show in the new tab.
  },
  "background": {
    "service_worker": "background.js"
  },
  "action": {
    "default_icon": {
      "16": "/images/cool16.png",
      "32": "/images/cool32.png",
      "48": "/images/cool48.png",
      "128": "/images/cool128.png"
    }
  },
  "icons": {
    "16": "/images/cool16.png",
    "32": "/images/cool32.png",
    "48": "/images/cool48.png",
    "128": "/images/cool128.png"
  }
}
```

3.Replace the below code in `App.vue` file.
```javascript
<template>
  <div class="date-time-wrapper">
    <h1 class="time">{{time}}</h1>
    <h3 class="greet">{{greeting}}</h3>
  </div>
</template>

<script>
export default {
  name: 'App',
  setup() {
    const dateObject = new Date();
    const hour = dateObject.getHours();
    let greet = "Good";
    
    if(hour <= 11) {
      greet += " morning";
    }else if(hour <= 18) {
      greet += " afternoon";
    }else {
      greet += " evening";
    }
    return {
      greeting: greet,
      time: `${hour +":"+dateObject.getMinutes()}`
    }
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .date-time-wrapper {
    text-align: center;
    margin: auto;
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
  }
  .time {
    font-size: 8rem;
    font-weight: 600;
    margin-bottom: 4px;
  }
  .greet {
    font-size: 3.5rem;
    font-weight: 400;
  }
  body {
    font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;
    // This background will bring new dynamic wallper everytime its provided by unsplash
    background-image: url(https://source.unsplash.com/random);
    background-size: cover;
    background-color: auto;
  }
</style>
```
4.Once done all steps. Go to the app home directory and run the below command.
```
$ yarn serve
```
visit the serving URL like `http://localhost:8080`. we able to see the below screen.
![App screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845733535/2dab5fa7-8139-4232-b38a-e47a6d2587f5.png)

That's it *we build the dynamic wallpaper screen using the Vue app*.

**Next chapter** I will share how to test in chrome browser in local and publish the chrome extension and list it in the marketplace app.
______

Thanks for reading this post.🍻