---
layout: default
title: Home
---

# 👋 Welcome

Welcome to my personal blog, where I explore the world of tech, ideas, and thoughts that cross my mind.

## ✍️ Latest Posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}

---
Feel free to explore. I’m writing about technology, philosophy, and whatever else intrigues me.
