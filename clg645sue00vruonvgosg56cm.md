---
title: "Normal text box vs Magical text box"
datePublished: Mon May 31 2021 00:01:21 GMT+0000 (Coordinated Universal Time)
cuid: clg645sue00vruonvgosg56cm
slug: normal-text-box-vs-magical-text-box
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680845746171/aad3ddc9-a4d6-4026-9aba-c75de99e8c98.png
tags: reactjs, typescript

---

Last week I faced one problem in the HTML text area. it more about the user interaction with the text area component. In, this article I am going to cover the problem and solution.

##Magic text box We all know about HTML [input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) element and behaviour. but, In the input have one problem is inside the text box large text not able to read properly.

*Example:*

![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845743034/44cbad0a-cd82-4442-8518-3840d469467c.jpeg align="left")

In this case in our mind comes `This problem will solve replace Input element to Text area element. so, we able to read the text properly`.

Yes. but, inside the text area will come small text. so the text area will fill more space without having large content.

*Example:*

![Alt Text](https://cdn.hashnode.com/res/hashnode/image/upload/v1680845745112/d8735bbe-8482-46f5-9f87-6bf8189315b0.jpeg align="left")

####Solution conclusion Use text area with increase height based on the content. now, solved the problem in both cases.

let see the implementation part using **react** and **typescript**.

```javascript
import React, { useEffect } from "react";

interface MagicTextBoxProps {
  value?: string;
  onChange?: (value: string) => void;
  placeholder?: string;
  defaultValue?: string;
}

const ReactMagicTextBox = (props: MagicTextBoxProps) => {
  const textAreaRef = React.createRef<HTMLTextAreaElement>();
  const [value, setValue] = React.useState(props.value);
  
  /* Incase text area based on the content */
  const autoAlignment = () => {
    // Using ref to get the text area element
    const node = textAreaRef?.current;

    if (node) {
      node.style.height = "auto";
      node.style.height = node.scrollHeight + "px"; // Main part of the code
    }
  };

  /* On load check and incase the height based on the content */
  useEffect(() => {
    autoAlignment();
  });

  const inputDataChange = (
    event: React.ChangeEvent<HTMLTextAreaElement>
  ): void => {
    // On change every time check the text area content and height
    autoAlignment();
    const currentValue = event.target.value;

    setValue(currentValue);

    if (props.onChange) {
      props.onChange(currentValue);
    }
  };

  return (
    <textarea
      className="input-text"
      ref={textAreaRef}
      onChange={inputDataChange}
      rows={1}
      placeholder={props.placeholder}
      value={value}
    />
  );
};

export default ReactMagicTextBox;
```

That's all. This is how I solved the problem. In case you know any solution better than this. please, share the solution via a comment at the post bottom.

Refer to the below real-time example for more understanding. `Inside the textbox use large content and test it. And, see the difference.`  

%[https://codesandbox.io/s/react-magic-textbox-wulbc] 

Thanks for reading this post 🍻🍻🍻.

Please, [subscribe](https://lakshmananarumugam.com/#/portal/signup) to my blog website to get my latest blogs and project directly into your mail inbox.