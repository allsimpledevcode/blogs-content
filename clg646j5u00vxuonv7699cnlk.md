---
title: "Architecture: Web app[front-end] from scratch 2021"
datePublished: Wed May 19 2021 04:48:11 GMT+0000 (Coordinated Universal Time)
cuid: clg646j5u00vxuonv7699cnlk
slug: architecture-web-appfront-end-from-scratch-2021
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845777286/0d2f7efe-063d-4f12-937a-17aa69ceaa2b.jpeg

---

Currently, I work as a front-end engineer and I worked on some of the frameworks Ember, React, and Vue. during that time I learned a lot of things about the web application. some of the learnings I wish to share here.

#Intro
  At some stage, a front-end developer not only knows how to develop a feature. Should know what are the main components must-have in a web application.

 Here I am sharing as much of waht I know here.  If, you will feel I missed anything here please, feel free to add a comment below here the post. 

###Architecture components:
1. Choosing the right JS framework
2. File system
3. Typescript
4. Styling system
5. Design documentation

###1.Choosing the right JS framework
![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845774829/7d8e174c-9fab-46cd-abb2-794b11cf4a26.jpeg)
 The first is the best. we solve 60% of problems by choosing the right framework for your product. when you choose consider the below points:

1. Don't choose a framework based on popularity until suit for your tech.
2. Availability of Learning Resources
3. Core Features (Which your product required)
4. Active community and version release.

At least the above points when you decide on a framework for your product.

###2.File system
  As a product, the code files will grow year by year. so, later stage with a poor file system we have a code file finding and organizing, dynamic module loading issue. nowadays by default, all frameworks give a default file structure. but, we have to reconsider when files grow it will work for maintainability.

Some popular file system:

```
// Classic
|--components
|--services
|--utils
|--store
|--icons
|--routes
```

```
//Pods 
|--FeatureOne
   |--components
   |--services
   |--store
   index.js
|--FeatureTwo
   |--components
   |--services
   |--store
   index.js
```
###3.Typescript
   Why we have to consider [typescript](https://www.typescriptlang.org/) nowadays in the web app. even though has a modern javascript.
   
   because typescript builds some additional features on top of the javascript only. Reason is:

`1. one of the big benefits is to enable IDEs to provide a richer environment for spotting common errors as you type the code.`
`2. TypeScript makes code easier to read and understand`
`3. Make app development as quick and easy as possible,`


###4.Styling system
   I mean styling system is organizing your style codes like CSS, sass, or CSS-in-JS. It looks like a small one. but, this only later is harder to maintain. `As a product design may change every 3/6 months. so, we able to change the design without the code duplication`. 

Styling tools:
1. [Atomic CSS](https://acss.io/)(New one (Facebook using this))
2. [CSS-in-JS](https://styled-components.com/) (Popular one)
3. [SASS](https://sass-lang.com/)
4. [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)

###5.Design documentation
   The design style guides nothing but, it's used to find co-worked what are the component available in the product and how to use them. 

Why it's important:
1. When a web app grows people may not know what are the components available.
2. The Same component creates multiple times due to the different names. (Ex: UserLink vs Hyperlink(both do the same thing)).  

Design documentation tools:
[Storybook](https://storybook.js.org/)
[styleguidist](https://react-styleguidist.js.org/)

Thanks to all who read this post.

Part 2 - [Link](https://dev.to/lakshmananarumugam/architecture-web-app-front-end-from-scratch-2021-v2-fa)

