---
layout: default
title: Hack All The Things
---

# hack ALL the things 

I write about things that matter to me. AI, Cyber Security, Philosophy, and more. For the readers of tomorrow.

## ✍️ Posts by most recent edit
{% assign sorted_posts = site.posts | sort: "date" | reverse %}
{% for post in sorted_posts %}
* [{{ post.title }}]({{ post.url }}) - Last edited: {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
---

## 👤 Contact Me

I do Cyber Security and AI stuff.

You can reach me on [LinkedIn](https://www.linkedin.com/in/frostsec), or via [contact@frost.fyi](mailto:contact@frost.fyi)

---
