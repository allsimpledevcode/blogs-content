---
title: "Build a chrome extension with modern code setup"
datePublished: Wed Jun 23 2021 12:38:54 GMT+0000 (Coordinated Universal Time)
cuid: clg645ai700pkw1nvfe61emb3
slug: build-a-chrome-extension-with-modern-code-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845722211/996d29ac-633b-480a-84da-a17f416b74a2.jpeg

---

In the previous article, I covered `How to set a chrome extension base code setup`. In this article, I am going to cover `how to use test it and publish to chrome extension marketplace app`.

Once you completed the all previous article step. you will have the below folder structure in your code directory.
```js
├── public
│   ├── images
│   ├── background.js (Require for a chrome extension)
│   ├── index.html (Extension home file)
│   └── manifest.json (Detect as a chrome extension)
├── src
│   ├── assets
│   ├── App.vue (Main UI screen)
│   └── main.js (Vue main JS file)
├── dist (Build folder)
├── node_modules
├── README.md
├── package.json
├── babel.config.js
└── .gitignore
```
Above the folder, you don't find any `dist` folder. please use the below command in your code main directory

```command
$ yarn build
```

Once you find the `dist` folder. dist folder will be the major part of the chrome extension. because we will test the app in the local port. but, we compress(.zip) and sent the dist inside code only. 

![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845720721/c764a636-90b5-4dde-b24f-e6ea2d5566e4.png)

Follow the above screen steps and target the `dist` to the target directory. Once you opened the chrome extension directory. 

you will find the chrome extension name called `Cool chrome theme`. Then, test all features which you did in the Vue app. once done the dev testing. it's time to publish the app.
  
Chrome already has some articles about how to publish the app. please check it out.

[Publish chrome extension](https://developer.chrome.com/docs/webstore/update/)

**FYI**

**Why I used VUE for the chrome extension?**
  Even though we able to develop a UI screen using plain HTML, JS, and CSS. when we build a complex screen I HTML and JS. it will take more time and complexity in development. 

Thanks for reading the post 😀. 

------------

[Code URL](https://github.com/lakshmanan-arumugam/cool-chrome-theme)
[Demo extension](https://chrome.google.com/webstore/detail/cool-chrome-theme/hnjfgakjgenceanlamddolhjgnmackfg)