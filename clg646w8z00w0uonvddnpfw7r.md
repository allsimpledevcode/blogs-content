---
title: "Be careful when you using an input "number" field in your web app"
datePublished: Wed May 12 2021 19:04:39 GMT+0000 (Coordinated Universal Time)
cuid: clg646w8z00w0uonvddnpfw7r
slug: be-careful-when-you-using-an-input-number-field-in-your-web-app
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845794639/208d9334-20e6-4693-a71a-c69542a10fad.png

---

  Recently I faced one *interesting issue* when I working on my web application. I thoughts it will help others.

#Introduction
  <Input/> is one of the HTML tags and has some types are text, number, password..etc., So, a user able to give a value through to the input. Each input type field has some generic behavior. Input number type field rejects non-numerical entries. 

##Technical use case:
  If a user is able to create a custom number field in your product and add the field inside a product form(Add contact form). Inside the Contact form, the number field value will have an auto-generated large number of digits.


##Problem
   If an input field has without limit the min and max length of the number. if the user is able to more than 20 digits number value, the javascript engine only accepts as specified in `IEEE 754` remainings will automatically change 0.

Example:
![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845794639/208d9334-20e6-4693-a71a-c69542a10fad.png)
   
This is an issue.

###Solution 1
  By default, limit the number field max length and before save the field validation also. 
```
<input type="number" min="-9007199254740991" max="9007199254740991"/>
``` 

###Solution 2
  Whenever we save the user number field value before the two conditions need to check.
```
function saveNumber(value) {
   if( Number.MIN_SAFE_INTEGER <= value && Number.MAX_SAFE_INTEGER >= value)
     //do save stuff
   }else {
     // Throw error
   }
}
```    

Done and thanks for reading this post...
