---
layout:     post
title:      "Harmonizing Colours"
subtitle:   "I found an easy way to create a good colour palate"
description: "I’ll be sharing here an easy method I found on the internet to create a palate of harmonious colours with the HSV colour model. I’ll also explain the terms Hue, saturation and value based on my understanding as a beginner."
author:     "Vijay Koushik"
date:       2019-03-03 09:00:00
keywords:   "design, colour palate, colour scheme, web design, colour terminology"
header-img: "img/2019_03_03/post_header.jpeg"
og_type: 	"article"
comments:   true
pageId:     "2019-03-03-harmonizing-colours"
tags:       ["beginner", "web design", "colour palate creation"]
creditCover: true
creditText: "Image by Steve Johnson from Pexels"
---
<p>Hello world!</p>
<p>I’ll be sharing here an easy method I found on the internet to create a palate of harmonious colours with the HSV colour model. I’ll also explain the terms Hue, saturation and value based on my understanding as a beginner.</p>
<p>Choosing a good palate of colours was always a herculean task for me as I’m new to web designing. The colours would either look unpleasant or straight up hurt my eyes. Thus, I used online colour picking tools like <a href="https://color.adobe.com/">Adobe Kuler</a> and <a href="http://paletton.com/">Paletton</a> to create my colour scheme. I decided to stick with choosing from the traditional methods of creating the colour schemes and I refrained from creating a custom palate. But soon my curiosity kicked in and I started reading articles on web designing and app designing to find out how others created harmonious custom colour palates.</p>
<h2>Using the HSV/HSB colour model</h2>
<p>Most articles I read suggested to use the HSV colour model to create custom colour palates because It allows to choose colours as we perceive in real life. But each article defined these terms in a unique way which was confusing to me and took a bit of time to grab the idea. Among those articles <a href="https://tutsplus.com/authors/tyler-seitz">Tyler Seitz's</a> article <a href="https://gamedevelopment.tutsplus.com/articles/picking-a-color-palette-for-your-games-artwork--gamedev-1174">Picking a Color Palette for Your Game's Artwork</a> on tuts-plus stood out because of its easily understandable algorithmic approach in creating custom colour palates using the HSV model.</p>
<p>According to their article, an appealing colour palate can be created by equalizing two of the components in the HSV model. What is HSV model anyway?<br/>
According to Wikipedia,
<blockquote>
HSV colour model was created to more closely align with the way human vision perceives colour-making attributes.
</blockquote>
It has three components viz
</p>
<h3>1. Hue</h3>
<p>
 According to Wikipedia, A hue is
 <blockquote>
 the degree to which a stimulus can be described as similar to or different from stimuli that are described as red, green, blue, and yellow
 </blockquote>
 In other words, hue is how we identify colours in terms of red, blue, green and yellow. For example, we identify Rose, Hibiscus, Apple and tulip as red even though they don’t exactly have the same colour.  And we identify the turquoise gem as greenish-blue colour not green or blue because it appears as a mix of both. This hilarious meme from <a href="https://imgur.com/gallery/DxkYG3s">imgur</a> gives a clear picture ;) of how we perceive hues. 
 <img src="{{site.baseurl}}/img/2019_03_03/hue_perception.jpg" alt="Perception of hues"  width="500" height="500"/>
 <span class="caption text-muted">How people perceive hues</span><br/>
 In HSV model, colours of each hue are arranged in a radial fasion and represented as degrees from 0° to 360°. Where Red has a hue value of 0 ° and going counter clockwise at 120° we have green and further at 240° we have blue. Going further we reach Red at 0°.
 <img src="{{site.baseurl}}/img/2019_03_03/color_wheel.png" alt="Colour wheel showing hues radially in a circular fashion" width="500" height="500"/>
 <span class="caption text-muted">Colour wheel showing hues radially in a circular fashion</span><br/>
</p>
<h3>2. Saturation</h3>
<p>
Saturation is the intensity of the colour with respect to the brightness of the light source. Saturation determines how vivid or how pale a colour appears in a light source. To put this in perspective, imagine how old clothes look faded when compared to new clothes in our wardrobe. The faded colour has less saturation whereas the vivid colours have high saturation. This image of faded jeans is the best representation for different saturations.
<img src="{{site.baseurl}}/img/2019_03_03/faded_denim.jpeg" alt="Image to represent different saturation of denim blue with constant brightness" width="600" height="800"/>
 <span class="caption text-muted">Image to represent different saturation of denim blue with constant brightness</span><br/>
 Sometimes low saturated colours are called muted colours. In HSV model Saturation takes a value between 0% to 100%. Where 0% saturation makes the colour white and 100% saturation has maximum intensity.
</p>
<h3>3. Value</h3>
<p>Value indicates how bright or how dark a colour is. When value component of a colour decreases it becomes darker and darker and eventually becomes black with the lowest brightness. On the other hand, increasing the value component makes the colour brighter. With the highest brightness, the colour is considered to be a pure colour when it’s fully saturated. In the real world, birghtness can be visualized as illuminated and shadow regions of objects in everyday life. The illuminated areas have high brightness and the part of objects in the shadows have low brightness.
<img src="{{site.baseurl}}/img/2019_03_03/shades_demo.jpg" alt="Image to represent green under different brightness" width="800" height="600"/>
 <span class="caption text-muted">Image to represent green under different brightness</span><br/>
</p>
<h2>Algorithm to create a harmonious colour palate</h2>
<p><strong><em>Note: From this point onwards, I'll be using the term brightness to represent the Value component of HSV model because it's more easy to understand.</em></strong></p>
<p>I find Tyler Seitz's algorithm easy and efficient in creating a custom colour palate. I’ll just re iterate their algorithm here.
<blockquote>To create a great colour palette, you need only follow this rule: 
<pre>
    <code>
IF hues do not equal each other<br/>

THEN set saturations to match each other<br/>

AND set brightnesses to match each other<br/>

ELSE IF saturations do not equal each other<br/>

THEN set hues to match each other<br/>

AND set brightnesses to match each other<br/>

ELSE IF brightnesses do not equal each other<br/>

THEN set hues to equal each other<br/>

AND set saturations to equal each other<br/>
   </code>
</pre>
</blockquote>
</p>
<h2>Shades, Tints and Tones</h2>
<p>We can extend this algorithm to create shades, tints and tones of a particular hue</p>
<pre>
<code>
// SHADES

SELECT a Colour

Keep the Hue constant

THEN Change the Brightness in equal intervals

AND Keep the Saturation unchanged.
</code>
</pre>
<p>To create different shades of the colour red, I started with Brightness at 100% and reduced it by 12 equally. This would create 8 shades of the colour.
<img src="{{site.baseurl}}/img/2019_03_03/shades_of_red.jpg" alt="Different shades of red"/>
<span class="caption text-muted">Different shades of red</span><br/>
</p>
<pre>
<code>
// TINTS

SELECT a Colour

Keep the Hue constant

THEN Change the Saturation in equal intervals

AND Keep the Brightness unchanged.
</code>
</pre>
<p>Similarly, to create different tints, I start with 100% saturation and bring the it down by 12 evenly to get 8 separate tints.
<img src="{{site.baseurl}}/img/2019_03_03/tints_of_red.jpg" alt="Different tints of red"/>
<span class="caption text-muted">Different tints of red</span><br/>
</p>
<pre>
<code>
// TONES

SELECT a Colour

Keep the Hue constant

THEN Change the Brightness in equal intervals

AND Change the Saturation with the same interval.
</code>
</pre>
<p>And to create multiple tones, I would again start with 100% brightness and 100% saturation and reduce them both in counts of 12 to obtain 8 different tones.
<img src="{{site.baseurl}}/img/2019_03_03/tones_of_red.jpg" alt="Different tones of red"/>
<span class="caption text-muted">Different tones of red</span><br/>
</p>

## Conclusion

I used this algorithm to create a palate and it's not bad for a first attempt. And This is how I implemented it.

<img src="{{site.baseurl}}/img/2019_03_03/my_result.png" alt="My result after after following the steps to create a color palate"/>
<span class="caption text-muted">My result after after following the steps to create a color palate</span><br/>

## References

1. Color Theory for Designers: How To Create Your Own Color Schemes - https://www.smashingmagazine.com/2010/02/color-theory-for-designer-part-3-creating-your-own-color-palettes/
2. Picking a Color Palette for Your Game's Artwork - https://gamedevelopment.tutsplus.com/articles/picking-a-color-palette-for-your-games-artwork--gamedev-1174
3. Color: HSB and tint-tone-shade - https://getpocket.com/a/read/1609347779
4. HSV color model - https://en.wikipedia.org/wiki/HSL_and_HSV