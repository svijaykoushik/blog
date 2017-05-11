---
title:  "Welcome to my Blog"
date:   2017-05-11 16:16:01 -0600
---

  {% for post in site.posts %}
      - [{{ post.title }}]({{ post.url }}) 
      {{ post.excerpt }}
  {% endfor %}
