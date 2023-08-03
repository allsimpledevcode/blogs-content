---
title: "Architecture:Web app[front-end] from scratch 2021 - part 2"
datePublished: Wed May 26 2021 05:45:24 GMT+0000 (Coordinated Universal Time)
cuid: clg6468y300pvw1nvf73z6pqe
slug: architectureweb-appfront-end-from-scratch-2021-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845767032/c165f770-4801-414a-b743-eff5b18f3f1d.jpeg

---

1. Coding style guide
2. Theme customization
3. Es-lint and Prettier
4. Git pre-commit hook
5. Internationalization

##Code style guide
![image](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845753063/89916069-ec4b-46b5-a2b3-9fcda13ea537.gif)
* Every product use multiple language and tools like SCSS, ReactJS / VueJS/ EmberJS,  Handlebar, HTML5, Typescript, Javascript...etc.., Each one have some code standard.

* When we start building a web app front end maybe work with one front end developer in the product. but, later many more developers will come and join the team.

* In that time developer writes him/her own style of the code and writes a non-standard code. in this case, in a later stage, we have to face code maintainability, existing feature enhancement development delay, and spend more time to fix the bug. 

*Real-time problems:*
1. In a single file with 1000 lines of code
2. Same style code write on different pages (Instead of writing a common component)
3. Code in-consistency (One dev write outdated function and another dev write an advanced released function/methods)

*Solution:*
1. Use the framework recommended style guide and enforce it.
2. Refer other tech gurus following code style guide.
3. Use es-lint in git pre-commit hook(I will explain more about below here)

*Example:*
1. [Google](https://google.github.io/styleguide/)
2. [Airbnb](https://github.com/airbnb/javascript)
3. [Vue 3](https://v3.vuejs.org/style-guide/)

##Theme customization
![Theme customization](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845754679/892b89cf-76f6-4ecb-8681-30bf6327f13e.gif)

* In the last couple of years every SASS product provide a theme customization option. a user able to change their preferred theme like dark, light, green ...etc..,.

* You may have doubt `why I am talking about this in web app architecture. it looks like a small one.`  Yes,  but it's more important in long term.

*Real-time problem:* 
* We build a product without considering theme customization. the later stage we want to add it. it will be more complicated. because the style/CSS files grown. we have to add theme customization changes to all of the style files. (It will be more like re-work overall the product)

*Solution:*
* When we set up a product add the theme customization base also.
* Use variable for each color code and serve all the files accessible.

*Reference:*
1. [Styled component](https://css-tricks.com/theming-and-theme-switching-with-react-and-styled-components/) 
2. [CSS Custom properties](https://css-tricks.com/css-custom-properties-theming/)
3. [CSS-Modules](https://kswanie21.medium.com/css-modules-sass-in-create-react-app-37c3152de9)

##Eslint and prettier
![Eslint and prettier](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845757410/72927e31-0cc5-43bf-b6d6-7dcd4ddf2501.gif)
* It's a must-have to add it when you set up a web app. because this one will help to maintain your javascript code standard problems and code formatting. 
* Eslint helps to identify your JS code problem using as per the dev configuration. by default it will check eslint default eslint rules configuration. if we need, we able to customize our own rules using the .eslintrc.{js,yml,json} file.
* Prettier helps to keep your product code clean and format. The main benefit is a uniform codebase and easier to read and modify. refer the below example: 
*Before without prettier*
```
function HelloWorld({greeting = "hello", greeted = '"World"', silent = false, onMouseOver,}) {

  if(!greeting){return null};

     // TODO: Don't use random in render
  let num = Math.floor (Math.random() * 1E+7).toString().replace(/\.\d+/ig, "")

  return <div className='HelloWorld' title={`You are visitor number ${ num }`} onMouseOver={onMouseOver}>

    <strong>{ greeting.slice( 0, 1 ).toUpperCase() + greeting.slice(1).toLowerCase() }</strong>
    {greeting.endsWith(",") ? " " : <span style={{color: '\grey'}}>", "</span> }
    <em>
	{ greeted }
	</em>
    { (silent)
      ? "."
      : "!"}

    </div>;
}
```
*Before without prettier*
```
function HelloWorld({
  greeting = "hello",
  greeted = '"World"',
  silent = false,
  onMouseOver,
}) {
  if (!greeting) {
    return null;
  }

  // TODO: Don't use random in render
  let num = Math.floor(Math.random() * 1e7)
    .toString()
    .replace(/\.\d+/gi, "");

  return (
    <div
      className="HelloWorld"
      title={`You are visitor number ${num}`}
      onMouseOver={onMouseOver}
    >
      <strong>
        {greeting.slice(0, 1).toUpperCase() + greeting.slice(1).toLowerCase()}
      </strong>
      {greeting.endsWith(",") ? (
        " "
      ) : (
        <span style={{ color: "grey" }}>", "</span>
      )}
      <em>{greeted}</em>
      {silent ? "." : "!"}
    </div>
  );
}
```
*Reference*
1. ESlint(https://eslint.org/docs/user-guide/getting-started)
2. VS code(https://www.digitalocean.com/community/tutorials/linting-and-formatting-with-eslint-in-vs-code)

*Bonus:*
 * We able to check the es-lint problem when we are in working using VS code. so, if we added it VScode. we don't need to check using the command. 

`NOTE: Es-lint and prettier set up in VS code and the product is an added advantage. but, it must have in the product.`

##Git pre-commit hook
![Git pre-commit hook](https://media.giphy.com/media/8TweEdaxxfuElKkRxz/giphy.gif)
* The pre-commit hooks are basically checking custom scripts when a developer pushes changes to the branch. if the script did not returns any errors it allows to push of the code. if have some error it will throw it on the terminal.

*Real-time problem:*
* The developer able to push the code changes with es-lint errors and un-formatted code. because this all command-line oriented. Maybe a developer forgot to check these errors. 

*Solution*
* Add the pre-commit hooks script to the project.

*Reference*
1. [Huskey](https://www.npmjs.com/package/husky)
2. [Setup and pre-commit hook](https://www.freecodecamp.org/news/how-to-add-commit-hooks-to-git-with-husky-to-automate-code-tasks/)

##Internationalization
![Internationalization](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845765047/f32956eb-321a-41c3-84b4-77f30c75cd25.gif)
* Internalisation is about provide multiple language support like english, german, spanish..etc..,

*Real-time problem:*
 * Build an app without considering Internalisation support is more like re-work overall the product code template. because, when we plan to support Internalisation. The copy text will be completely different from the old one. Example:

Without translation support:
```
<p>Hello world</p>
```
With translation support:
```
<p>{{t "Hello world"}</p>
```
*Solution:*
* By default set up the internalization support with core language. 

*Reference*
[Base setup for all language](https://www.soluling.com/Help/Web/Index.htm)

Thanks for reading this post. 😊

Part 3 will be coming soon...