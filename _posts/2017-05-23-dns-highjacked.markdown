---
layout:   		post
title:    		"Never forget to change your default router password"
subtitle: 		"Insecure routers open the back door to DNS hijacking"
description:	"Leaving factory access credentials of routers unchanged can open the back door to DNS hijacking"
date:			2017-05-23 20:39:00
author: 		"Vijay Koushik"
header-img: "img/post_dns_hijack_header.jpg"
---
<p>Two years ago on a fine morning I opened my computer to check my email. I started searching for job opportunities on Google and opened each result that Google brought up. Now, a strange thing happened! Whenever I tried to interact with a website that I opened from the results page an ad-popup opened. I thought I disabled the ad blocker plug-in, but it was enabled. I started to wonder what was going on. I then visited every webpage I used to visit and the same thing happened. Every time I clicked on an element an ad-popup opened. This frustrated me so I closed my browser and started a complete virus scan on my pc and then stared browsing on my phone. But alas! The same thing happened. This time every time I try to scroll a page on my phone it started to redirect to an advertisement. I felt something was not right and so I started to inspect on all my devices on my network the result was the same. By this time I could guess that something was wrong with my modem. Amidst this problem Google and Facebook were working fine. No irritating popups (thank god!). I fiddled around with my network configuration on my PC. I opened command prompt and typed in the command <em>ipconfig</em> and I noticed something unusual in the results displayed on the screen.</p>

<blockquote>
Ethernet adapter Ethernet:<br/><br/>

   Connection-specific DNS Suffix  . :<br/> 
   IPv4 Address. . . . . . . . . . . : 192.168.1.5<br/> 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0<br/> 
   Default Gateway . . . . . . . . . : 213.109.79.255
</blockquote>

<p>The default gateway address was not the modem's IP. I made a quick search on google on the unusual IP and I found that it was a "rouge dns" server's address and I was a victim of <em>DNS Hijacking</em>. After further research on dns high jacking trying very hard to ignore the ad-popup I came to know that this was done by a malware called <em>DNS changer</em>. That moment, I regretted the times I clicked the ignore button every time when my computer warned me about installing software from unknown publishers.</p>

<h2 class="section-heading">DNS Hijacked</h2>

<a href="#">
    <img src="{{ site.baseurl }}/img/post-dns-hijack-illustration.png" alt="Illustration of DNS hijacking">
</a>
<span class="caption text-muted">An Illustration of how ads were embeded into websites</span>

<p>On further reading about DNS changer malware, I learnt its working procedure. The malware exploited vulnerability in my modem. It used the default access credentials to get into my modem settings and changed the dns address to a rouge dns. I never changed the generic <em>username:admin and password:admin</em> credentials that came with the box because it was easy for me to remember. Another warning I ignored. Now that the malware changed the dns settings all my traffic to the internet were sent to a rouge dns instead of my ISP's DNS. The rouge dns was monitoring all the websites I visited, my email accounts and my passwords.</p>
<p>Wikipedia says <blockquote>DNS hijacking or DNS redirection is the practice of subverting the resolution of Domain Name System (DNS) queries. This can be achieved by malware that overrides a computer's TCP/IP configuration to point at a rogue DNS server under the control of an attacker, or through modifying the behaviour of a trusted DNS server so that it does not comply with internet standards.</blockquote> In my case the rouge server read all my queries and attached a <em>script</em> to the response that opens an advertisement pop whenever I interacted with any website I wanted to visit. Pretty cruel right? This way the hacker could earn money for the ads I was forced to visit. I had spent almost half a day trying to understand the problem and now I was desperate to find a solution to my problem.</p>

<h2 class="section-heading">Opendns to the rescue</h2>
<p>After surfing the internet for about half an hour I was suggested to do 2 things:
<ol>
<li>To change my modem's access credentials from the factory provided one.</li>
<li>To change my dns setting in my modem from automatic to a secure static dns, either <a href="https://developers.google.com/speed/public-dns/">Google Public DNS</a> or <a href="https://www.opendns.com/">Opendns</a>.</li>
</ol>
While the former is higly recomended, the latter is optional.<br/>
Google Public DNS provided the benefit of faster access to web pages and security from various attacks (more on this <a href="https://developers.google.com/speed/public-dns/docs/intro">here</a>).But, Opendns along with seemingly faster internet access and security also provided web filtering options (more on this <a href="https://www.opendns.com/home-internet-security/">here</a>) which made me choose Opendns for my network.
</p>

<p>I then changed the password for my modem which started all of my problems (I suggest you to include numbers and symbols in your password for added security). Now, everything is working fine and I'll never forget about his incident. If you think you are still using your modem/router's default username and password then change it immediately.</p>
<p>A random quote</p>
<blockquote>
You must not lose faith in humanity. Humanity is an ocean; if a few drops of the ocean are dirty, the ocean does not become dirty.-<cite>Mahatma Gandhi</cite>
</blockquote>
<p>Photographs by <a href="https://sentrant.com/">Sentrant.com</a> and header photo by <a href="https://commons.wikimedia.org/">Wikimedia Commons</a>.</p>