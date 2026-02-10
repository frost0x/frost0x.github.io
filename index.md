---
layout: default
title: Mountain of Frost
---

# 🦿 ↗️  🗻

I am Frost and this is my mountain retreat. Here you can read things that matter to me. AI, Cyber Security, Philosophy, and more. For the innovators of tomorrow.

## ✍️ Articles by date of writing
{% assign sorted_posts = site.posts | sort: "date" | reverse %}
{% for post in sorted_posts %}
* [{{ post.title }}]({{ post.url }}) - Written: {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
---

## 👤 Contact Me

You can reach me on [LinkedIn](https://www.linkedin.com/in/frostsec) or via [contact@frost.fyi](mailto:contact@frost.fyi)
Find me on Twitter/X [@frostxlol](x.com/frostxlol)
---
