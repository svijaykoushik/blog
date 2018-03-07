---
layout:   		post
title:    		"Translucency with Transparency"
subtitle: 		"An experiment to implement Acrylic material of the Fluent Design System in HTML"
description:	"An experiment to implement Acrylic material of the Fluent Design System in HTML"
date:			2018-03-07 21:03:00
author: 		"Vijay Koushik"
keywords:   	"Fluent design, Acrylic material, HTML, CSS"
header-img: 	"img/post-header-acrylic.jpg"
og_type: 		"article"
comments:       true
pageId:         "2018-03-07-translucency-with-transparency"
tags:			["Fluent design", "Acrylic material", "HTML", "CSS", "learning-experience"]
---
<p>
Hey guys! So Windows 10 has been around for 2 years now with its attractive (it really is) colourful user interface, fancy start menu and live tiles. Yet the most captivating feature is the “blurry glass effect” that is used in store apps especially the mail, Groove Music, and the Store itself.
</p>
<p>I’ve seen beautiful use of transparent elements in several websites<sup><a href="#fn">[1]</a></sup>, but what sets out this “blurry glass effect” is that you know what is in the background but you can’t see it clearly! The effect hides the details of what is behind and makes you inquisitive to see what is behind.</p>
<p>The “blurry glass effect” as I describe is called Acrylic Material<sup><a href="#fn">[2]</a></sup> which is part of the “Fluent Design System”. It’s the name Microsoft gave to its “design guidelines” to build software for all windows 10 devices<sup><a href="#fn">[3]</a></sup>.</p>
<p>Now that you know what an Acrylic Material is, I’ll tell you about the experiment I did. As I said before, the acrylic material is so captivating that I thought to myself “Why shouldn’t I apply this in HTML?” and with that question I started researching on the internet for existing implementations and  to break the question into simpler ones to get a better understanding. I found two good existing implementations (Lucky me!) of this effect – a pen on <a href="https://codemyui.com/fluent-design-stacking-card-ui/">CodemyUi.com</a>  and a thread on <a href="https://stackoverflow.com/questions/44522299/css-only-acrylic-material-from-fluent-design-system">Stack Overflow</a>.</p>
<p>These implementations involved a parent container element with a picture as a background element, let’s called it “mommy” layer and 3 child container elements.
</p>
<ol start="1">
<li>A container element “blurry” with the blurred version of the mommy layer’s background using CSS filter property - blur<sup><a href="#fn">[4]</a></sup>.</li>
<li>Another container element “noisy” with noise texture as a background.</li>
<li>And finally, a third container element “showy” with the content text or image to be displayed and a colour overlay.</li>
</ol>
<p>In the final step the second key property, the first being “Blur filter” in this effect “Transparency” which in contrast is named “Opacity”<sup><a href="#fn">[5]</a></sup>  in CSS. This is the finishing touch to this effect. I achieved translucency via both colour transparency, where one can add transparency to the colour using the alpha value of that colour with the rgba() function and the opacity property of CSS. I found that opacity of 0.3 or 30% is sufficient for this effect. These steps are pretty close to Microsoft’s own recipe of creating the acrylic material.</p>
<a href="#">
    <img src="{{ site.baseurl }}/img/post-ms-acrylicrecipe-diagram.png" alt="Micrososft's acrylic recipe" width="800" height="534">
</a>
<span class="caption text-muted">Micrososft's acrylic recipe</span>
<p>Well, except for the exclusion blend. It can be added to the Blurry container with the CSS property “background-blend-mode"<sup><a href="#fn">[6]</a></sup>. This is the recipe for HTML implementation</p>
<a href="#">
    <img src="{{ site.baseurl }}/img/post-html-acrylicrecipe-diagram.jpg" alt="Html recipe for acrylic" width="800" height="600">
</a>
<span class="caption text-muted">Html recipe for acrylic</span>
<p>The resulting effect is very close to the original and it’s awesome! Take a look</p>
<script async src="//jsfiddle.net/svijaykoushik/ybLuvzh3/embed/result/"></script>
<p>It’s not over yet. I know that CSS background property not only supports pictures but also gradients and pure colours. Can this effect be applied to gradients and colours? A question popped in my head. So, I started experimenting this with different backgrounds with different colours and different gradients. And the result of this experiment is... (Drum roll) YES! This effect works on images, gradients and colours as background. Change the background from image to a gradient. Or just use a pure colour omitting the former. </p>
<p>Here's a sample with the Indian flag's tri-color gradient as a background with the acrylic effect</p>
<script async src="//jsfiddle.net/svijaykoushik/qoyj058m/embed/result/"></script>
<p>I had so much fun learning about this effect. I learnt about CSS filters , pseudo elements<sup><a href="#fn">[7]</a></sup> and efficient use of z-indexing to stack up multiple layers to create a single cool effect. Watch the effect in action in this fiddle. Click/tap on the <i class="fa fa-bars"></i> to togle the navigation pane.</p>
<script async src="//jsfiddle.net/svijaykoushik/8cdbe21b/embed/result/"></script>
<p>It's awesome na? Did you like it? Don’t forget to share what you think about this post in the comments.<br/>
Header Photo by Tim Gouw from <a href="https://www.pexels.com/photo/man-in-white-shirt-using-macbook-pro-52608/">Pexels</a></p>
<hr/>
<p id ="fn">
<sup>[1]</sup> Use of Transparency in Website Design, Examples - https://designmodo.com/transparency-website-design/
<sup>[2]</sup> Acrylic material - https://docs.microsoft.com/en-us/windows/uwp/design/style/acrylic
<sup>[3]</sup> Fluent design system - https://en.wikipedia.org/wiki/Fluent_Design_System
<sup>[4]</sup> CSS blur filter - https://developer.mozilla.org/en-US/docs/Web/CSS/filter
<sup>[5]</sup> CSS Opacity property - https://developer.mozilla.org/en-US/docs/Web/CSS/opacity
<sup>[6]</sup> Background-blend-mode property - https://developer.mozilla.org/en-US/docs/Web/CSS/background-blend-mode
<sup>[7]</sup> CSS pseudo elements - https://developer.mozilla.org/en/docs/Web/CSS/Pseudo-elements
</p>