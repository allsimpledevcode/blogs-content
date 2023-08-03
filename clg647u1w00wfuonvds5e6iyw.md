---
title: "Design System - Icons for vue 3"
datePublished: Fri May 07 2021 10:31:02 GMT+0000 (Coordinated Universal Time)
cuid: clg647u1w00wfuonvds5e6iyw
slug: design-system-icons-for-vue-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845838569/2bc86465-9b7b-49d9-849e-c0aaf2ab345d.jpeg
tags: npm, svg, npm-publish

---

Now a days every web application using svg icons for their project. because, svg give a detailed view, resolution, speed...etc., each one use different approach to load the svg icon in their project. but, I personally like this **Convert all svg's into one sprite.svg** approach

Refer this [guide](https://v3.vuejs.org/cookbook/editable-svg-icons.html#base-example) to know why i approach this pattern.

> Initial project setup

First install the vue cli in your sysstem

```css
$ npm install -g @vue/cli
       -OR-
$ yarn global add @vue/cli
```

Create a vue project using vue cli

```css
$ vue create svg-icon-setup
#choose: Vue 3 Preview (if you own setup your own configuration)
$ cd svg-icon-setup
$ yarn serve
```

Now the vue app is ready. Then go to your browser and open this url: [http://localhost:8080/](http://localhost:8080/)

![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845833737/8ea6e622-2899-47a9-8b89-bc3cc213b59d.png align="left")

> Setup svg sprite icon.

The same code directory run the below command

```css
$ vue add svg-sprite
```

For more info about this \[svg-sprint\] (https://github.com/swisnl/vue-cli-plugin-svg-sprite) addon

Once the svg-sprite added into your project. the addon will create two files are:

* svg-icon-setup/src/components/SvgIcon.vue (Icon component)
    
* svg-icon-setup/vue.config.js (Build configuration)
    

Now, time to add our own svg icons inside `src/assets` the directory.

Replace the below code changes in the project

```css
<!-- src/App.vue -->

<template>
  <SvgIcon
    name="facebook"
  />
  <SvgIcon
    name="twitter"
  />
  <SvgIcon
    name="tumblr"
  />
</template>

<script>
import SvgIcon from '@/components/SvgIcon'

export default {
  name: 'App',
  components: {
    SvgIcon
  }
}
</script>
```

```css
/* vue.config.js */

module.exports = {
  pluginOptions: {
    svgSprite: {
      /*
       * The directory containing your SVG files.
       */
      dir: 'src/assets/icons',
      /*
       * The reqex that will be used for the Webpack rule.
       */
      test: /\.(svg)(\?.*)?$/,
      /*
       * @see https://github.com/kisenka/svg-sprite-loader#configuration
       */
      loaderOptions: {
        extract: true,
        spriteFilename: 'img/icons.svg' // or 'img/icons.svg' if filenameHashing == false
      },
      /*
       * @see https://github.com/kisenka/svg-sprite-loader#configuration
       */
      pluginOptions: {
        plainSprite: true
      }
    }
  },
  chainWebpack: config => {
    config.module
      .rule('svg-sprite')
      .use('svgo-loader')
      .loader('svgo-loader')
  }
}
```

After the above code replaced. `kill` and run the `serve once again`:

The page will be render below like the screenshot

![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845835779/3076c4cb-f564-4c2a-bb10-bfe064203ba3.png align="left")

That's all.

Reference for the [code repo](https://github.com/explore-free-projects/svg-icon-setup)

Cover image by [**balazsketyi unsplash**](https://unsplash.com/@balazsketyi)