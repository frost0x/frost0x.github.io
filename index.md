---
layout: default
title: Hack All The Things
---

# 👋 Welcome 

Welcome to my corner of the internet. I write about **Offensive Agentic AI**. 
Beyond that, I explore AI, Cyber Security, Philosophy, and ideas that matter.

## ✍️ Posts by most recent edit
{% assign sorted_posts = site.posts | sort: "date" | reverse %}
{% for post in sorted_posts limit: 5 %}
* [{{ post.title }}]({{ post.url }}) - Last edited: {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
---

## 👤 Contact Me

I perform research and work professionally in Cyber Security.

You can reach me on [LinkedIn](https://www.linkedin.com/in/frostsec), or via [contact@frost.fyi](mailto:contact@frost.fyi)

---
