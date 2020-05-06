---
layout: home
---

# What is this
I read somewhere that keeping a blog was good idea, so I uh, decided to follow through.

This is more just a stream of consciousness, some things that I found interesting or want to refer to later.


<h2>{{ site.data.samplelist.docs_list_title }}</h2>
<ul>
   {% for item in site.data.samplelist.docs %}
      <li><a href="{{ item.url }}">{{ item.title }}</a></li>
   {% endfor %}
</ul>
