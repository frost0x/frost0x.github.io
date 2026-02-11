---
layout: default
title: frosthub
---

# 🦿 ↗️  🗻

I am Frost and this is my corner of the internet. Here you can read things that matter to me. AI, Cyber Security, Philosophy, and more. For the innovators of tomorrow.

## ✍️ articles by date of writing
{% assign sorted_posts = site.posts | sort: "date" | reverse %}
{% for post in sorted_posts %}
* [{{ post.title }}]({{ post.url }}) - Written: {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
---

## 👤 contact me

You can reach me on [LinkedIn](https://www.linkedin.com/in/frostsec) or via [contact@frost.fyi](mailto:contact@frost.fyi)
Find me on Twitter/X [@frostxlol](https://x.com/frostxlol)

---
