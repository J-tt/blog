---
layout: home
---

# What is this
I read somewhere that keeping a blog was good idea, so I made one.

This is more just a stream of consciousness, some things that I found interesting or want to refer to later.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
