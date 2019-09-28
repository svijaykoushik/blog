---
layout: post
title:      "Learning TypeScript: Hello world with DOM manipulation"
subtitle:   "They never mention it in the tutorials"
description: "It's about how to do DOM manipulation in TypeScript and how they are not available in the language tutorials"
header-img: "img/2019_09_27/ts-dom-manipulation-header.jpg"
author:     "Vijay Koushik"
keywords:   "Typescript, DOM manipulation, DOM types, Beginners, Tutorial"
header-img: "img/2019_09_27/ts-dom-manipulation-header.jpg"
og_type: 	"article"
comments:   true
pageId:     2019-09-27-typescript-dom-manipulation
tags:       ["beginner", "typescript", "domTypes", "domManipulation"]
---



> Every TypeScript example and tutorial I have found thus far is about language features, Static typing, Visual Studio, etc. I cannot find anything to tell me how I should be using it with reference to JavaScript and the DOM.
>
>My understanding it you can use TypeScript for the DOM. But, I never see anyone using it for that.

Said  [johnny](https://stackoverflow.com/users/28045/johnny) in a [question](https://stackoverflow.com/questions/43210642/is-typescripts-purpose-to-be-used-for-manipulating-the-dom-like-javascript-is) on stackoverflow.com. A while back I had the same question. Can We Use Typescript to manipulate the DOM?

Hello world!
I’ve been learning Typescript for a week now. I got into typescript when I wanted to learn the new Angular. Since it is based on Typescript, I decided to learn Typescript. During learning, I found it odd that none of the learning aids I used included examples of using the language with HTML. Every example I saw in those learning aids and some other tutorials I then looked up involved only node.js. More googling landed me on StackOverflow where johnny, as I mentioned before, had the same question. using this as an opportunity to make a post after almost a year, I’ve made this post, the missing piece of the puzzle, in hopes that it would land first instead of johnny’s question on StackOverflow.

## Configuration

Using the DOM or Dom manipulation in typescript is simple. All I needed to do was to use the types defined specifically for DOM access that is available in Typescript. The rest was the same as in JavaScript. But... these "DOM types" are not available out of the box with Typescript. I needed to explicitly configure the typescript compiler to include the “dom” library in the `compilerOptions` section in the configuration file<sup>\[[2](#References)\]</sup> to access the DOM types in my project. 
*"Why didn’t they include by default?. Maybe the creators didn't intend to use it primarily for front end development"* I thought to myself.

Some other configuration changes I made were: I enabled `strict` mode for strict type checking and I changed the `target` from "common JS" to "es5", so the compiler can output JS for browsers and not for node.js. I also added the "es2015" library so that I could use functionalities like arrays and Math functions for my example.

```javascript
/**
* tsconfig.json
* Configuration file in the project folder for the Typescript compiler
*/
{
    "compilerOptions": {
        "lib": [
            "es2015",
            "dom"
        ],
        "strict": true,
        "target": "es2015"
    }
}
```

## Hello world

In this article, I’m going to write a hello world program to demonstrate the use of DOM in typescript. Because it’s my first post on typescript. I’ll be covering the basics of using the DOM types and a problem a beginner like me would face while doing this the first time.
I’m not covering DOM events here. I’ll be covering them in another article coming soon.

I’ll begin with the basics where I change the inner text value of an existing element. I started by creating an HTML file with a simple html5 boilerplate with a `<h1>` element with id greeter saying “hello” inside the body.

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Hello world</title>
</head>
<body>
    <h1 id="greeter">Hello</h1>
</body>
</html>
```

Then, I opened a new typescript file and added the following code

``` typescript

let greeter:HTMLHeadingElement = document.getElementById("greeter");

greeter.innerText = "Hello world!";

 ```

![Typescript type declaration]({{ site.baseurl }}/img/2019_09_27/ts-type-declaration.jpg)

In the code, I created a variable greeter and I assigned the type `HTMLHeadingElement` to it. The `HTMLHeadingElement` type which is defined in the “dom” library we added to the configuration, tells the compiler that the greeter variable expects an Html heading element and nothing else. And, I assigned the greeter to the value returned by the function `getElementById` which returns the element with the ID provided. Then I assigned the string “hello world” to the `innerText` property of the greeter element.

When I compiled the code with the command

``` cmd
:> tsc script.js
```

![Typescript type declaration]({{ site.baseurl }}/img/2019_09_27/ts-compile-command.jpg)

It threw the following error

> Type 'HTMLElement | null' is not assignable to type 'HTMLHeadingElement'.
>
> Type 'null' is not assignable to type 'HTMLHeadingElement'.

Bummer! My first attempt failed. On the bright side, Typescript is doing its job and the configurations I set up works. The error means that, I tried to assign greeter which is of type `HTMLHeadingElement` with an object of type `HTMLElement` that the method `getElementById` returned. `HTMLElement | null` in the error message means that the method’s return value can be either of type `HTMLElement` or `null`. The special operator `|` is called the union operator. I won’t be explaining "union types" in this article. You can learn about them [here](https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types).

`HTMLElement` type is just a common interface for all the html elements<sup>\[[1](#References)\]</sup> but the compiler expects a `HTMLHeadingElement`. I thought of changing the greeter variable’s type to `HTMLElement` but I didn’t. Because, it’s not right. If I had changed it to `HTMLElement`, it means greeter could accept any HTML element from the DOM. I wanted it to accept only a heading element. So, I used *type assertion* feature of typescript (Learn about type assertion [here](https://www.typescriptlang.org/docs/handbook/basic-types.html#type-assertions)) to tell the compiler that the element returned from the getElementById is indeed a heading element and it doesn’t have to worry about it. Here's the fixed code:

``` typescript
let greeter:HTMLHeadingElement = document.getElementById("greeter") as HTMLHeadingElement;

greeter.innerText = "Hello world!";
```

![Typescript type declaration]({{ site.baseurl }}/img/2019_09_27/ts-type-assertion.jpg)

Now, the compilation was a success. I included the script.js file generated by the compiler in the Html document and opened it on a browser. It looked like this:

![Typescript type declaration]({{ site.baseurl }}/img/2019_09_27/ts-screenshot-no-style.png)

### Decoration time

Now that I've made sure that everything works as intended, It was time to decorate the page. I wanted a font style that is not formal looking. After browsing through google fonts, I chose *Rock Salt*. I imported it in my stylesheet along with *Dancing Script* as a secondary font using CSS imports.  I then proceeded by adding a few more elements to the Html document. I centered all the text using CSS flexbox, added a nice background from [UI gradients](https://uigradients.com/#CanYouFeelTheLoveTonight), and adjusted positions of some elements to arrange them properly. The page now looked beautiful.

![Typescript type declaration]({{ site.baseurl }}/img/2019_09_27/ts-screenshot-bg-and-font.png)

Next, to place the cherry on top, I wanted to add a pretty background animation of orbs rising to the top like bubbles to the page. To make the orbs I decided to use `<div>` elements. Since I wanted several of these orbs with different sizes, I split the task into two so the work could be simplified. One, I created a common style for all the orbs and created a custom animation for the orbs in CSS. And two, I created the orbs dynamically with the help of typescript by creating a set number of `<div>` elements, assigning them the style created beforehand and randomizing their sizes, positions, and animation-delay to make them look more natural.

```javascript
.
.
.
function createBubbles() {

 for (let i = 0; i < bubbleCount; i++) {

 let div: HTMLDivElement = document.createElement("div") as HTMLDivElement;

 let divSize = getSize();

 div.style.left = getLeftPosition() + "px";

 div.style.width = divSize + "px";

 div.style.height = divSize + "px";

 div.style.animationDelay = i * randomFloat(0, 30) + "s";

 div.style.filter = "blur(" + randomFloat(2, 5) + "px)";

 div.classList.add("bubble");

 bubbleBuffer.push(div);

 }

 console.log("Bubbles created");

}
.
.
.
```

Finally, I added the orbs to the dom like this and thereby kickstarting the animation

```javascript
.
.
.
function releaseBubbles() {

 createBubbles();

 for (let i = 0; i < bubbleCount; i++) {

 containerDiv.appendChild(bubbleBuffer[i]);

 }

 console.log("Bubbles released");

}
.
.
.
```

Here’s the final output

<iframe width="560" height="315" src="https://www.youtube.com/embed/tX8P-W_jNjI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

And the [link](https://github.com/svijaykoushik/learning-typescript/tree/master/helloworld) to the repo containing the complete code

## Conclusion

During writing this article and the example, I realized the involvement of advanced concepts like type assertion and union types. I now understand why the authors of those tutorials didn't include them. If included, it would have confused beginners outright. I think it’s best to learn typescript well before starting to use DOM in your projects.

In my example, I skipped the null checking when I fixed the type mismatch error as it seemed unnecessary for the example but you should check for nulls when necessary to avoid breaking your app at runtime. I also skipped the part where I added animations using the animate.css plugin for the text as it felt trivial explaining it.

Finally, I need to thank [Ivan Petrov](https://dev.to/tinmanjk) for suggesting me to read a book when learning a new tech in a comment on my [previous post](https://dev.to/svijaykoushik/stop-tracking-and-start-ignoring-ook) on <https://dev.to>. Thanks, Ivan 👍🏽. The exercises in the book helped me.

Thanks for your time. :)

## References

1. Interface HTMLElement - <http://definitelytyped.org/docs/flipsnap--flipsnap/interfaces/htmlelement.html>
2. Missing basic DOM types in TypeScript project - <https://stackoverflow.com/a/42604094>

## Further Reading

1. Stop tracking and start ignoring: A tip to delete files from a repository and stop tracking them while keeping them locally - <https://svijaykoushik.github.io/blog/2019/02/17/start-ignoring/>
2. TypeScript Tutorial - <https://www.tutorialspoint.com/typescript/.>
3. Programming Typescript by Boris Cherny - ISBN 9781492037651
4. Advanced types in Typescript - <https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types>
5. Type Assertion in Typescript - <https://www.typescriptlang.org/docs/handbook/basic-types.html#type-assertions>
6. Learn TypeScript in 50 Minutes - <https://youtu.be/WBPrJSw7yQA>
