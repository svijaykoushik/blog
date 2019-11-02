---
layout: post
title:      "My thoughts on TypeScript"
subtitle:   "A review of typescript after learning it for a week"
date:       2019-10-14 
description: "I list out my thoughts on typescript after learning it for a week"
header-img: "img/2019_10_14/cover.jpg"
author:     "Vijay Koushik"
keywords:   "Typescript, Javascript, Thoughts, review"
og_type: 	"article"
comments:   true
pageId:     2019-10-14-my-thoughts-on-typescript
tags:       ["typescript", "javascript", "thoughts", "beginners"]
creditCover: true
creditText: "Image by Pixabay from Pexels"
---

When I was a child, I used to play construction with my Dad’s music cassette collection. Sometimes, I would mix up the cases and the cassettes inside for fun. When my Dad wanted to listen to the music he liked, he would be disturbed when a completely different song play. And he would be frustrated when he couldn’t find the real one.  

I feel the same frustration whenever I try to access a property in a JavaScript object that is supposed to be available and It doesn’t exist.

JavaScript gives me "God" like powers where I can create objects in one form and change it into something different at my whim. Like turning a fox into a horse or turning blood to wine. But this power gave me problems just like how I gave my dad problems.

If I had the magic lamp, I would ask Genie Smith to find me a way to designate types to data & objects when I write code and not when I execute it. And he would've said "Dude you can use TypeScript. It has what you need".

If you don't know what TypeScript is, it is an open source programming language designed to provide type-safety to JS projects with its strict type system.

After learning typescript for a week, here are my thoughts on TypeScript.

## 1. A Super set of JavaScript

Typescript uses the same syntax as JavaScript with nifty additional features. And I love it.

Typescript is just like JS but has a strict syntactic structure with stringent datatype rules. I would say it as a meta-data to JavaScript as it gives additional information about types and object structures. It kind of reminds me of C++.

## 2. Type safety

The type system in TypeScript, the set of rules on how to assign data types or types for short to variables, objects and other elements of my code is very stringent. This ensures that I do not assign a Person object to an Animal object or add a string with a number. This is called type safety in computer programming. Though JavaScript has type safety, it's more lenient in my opinion.

## 3. A bouncer

I feel that typescript is like a bouncer in a bar who push away people when they do not follow the party etiquettes. It's because TS pushes me back whenever there is an inadvertent type-related error until I fix it. It might seem tedious, It's helpful nonetheless. The TS compiler helped me prevent spending a lot of time to debug the error which is the case in JS.

## 4. Code Hinting

My favourite part of typescript is its ability to present hints while I code. When combined with powerful code editors like VS Code or Atom, the contextual code suggestions helped me reduce errors and increased my typing speed. TS can do this because it's a statically typed language. It means information about types are available to the compiler before the compilation starts. This availability of information helps the editors compile my code on the go and provide contextual suggestions.

## 5. Red squiggly lines

 Available separately the linter when enabled in the editor, can detect errors of syntactic, type and even contextual nature. It presents the errors by underlining the error part with red squiggly lines as I type. This makes error correction easier and faster

## 6. Planning Ahead

New nifty features in typescript like the call signatures, object structure definition and interfaces allow me to plan ahead on how I'll be applying my design to the code. For example, the call signatures are similar to function declaration in C allow me to sketch out the number of parameters needed and the return type. And the Object structure definition allows me to design a skeleton for an object before I define it.

## 7. Versatility

What makes typescript versatile is its wide variety of configuration options. I can enable and disable different options to cater to my project's needs.

One of the settings I used a lot is the target option. It flipped between commonJS module system and the es5 module system while learning.

## 8. Just too many options

TS has just too many configuration options for a beginner. The ignorance of the purpose of some of these options led me to trouble. I did not know I had to include a separate library to use the DOM functions. I was like "What do you mean getElementById is not defined?"

## 9. Type definition

What makes typescript great is, it allows programmers to define new types for their need. Making use of this feature the definitely.org community has created high-quality type definitions for popular JS frameworks like JQuery, node.js and Angular which allows the use of these frameworks in Typescript.

But, could not find enough information on how to use a JS plugin or framework if it is not supported by the definitely typed community.

## 10. Partial to node.js

Typescript has so many features that I found useful. But in terms of documentation, it is partial to node.js. I found lots of learning aids about TS for node.js. But I couldn't find equivalent amounts of learning aids for front end programming. 

## Conclusion

As a beginner, all these strict rules felt time-consuming since it took less time to write the same in JS. Over time, I realized the usefulness of TS and started using its features as I learnt them. I've decided to use typescript in my next side project instead of JavaScript.

## References

- "Programming TypeScript, Making your Javascript applications to scale" by Borris Cherney. ISBN - 9781492037651
- "Type system", [Wikipedia](https://en.wikipedia.org/wiki/Type_system)
- "Data type", [Wikipedia](https://en.wikipedia.org/wiki/Data_type)
