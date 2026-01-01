---
layout: default
title: Home
---

# Welcome to Torchbearer Lab

## All Posts (Automatic List)
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">
    </li>
  {% endfor %}
</ul>
