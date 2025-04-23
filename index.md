---
layout: default
title: Hack All The Things
---

# 👋 Welcome 

Welcome to my corner of the internet. I write about **Offensive Agentic AI**. 
Beyond that, I explore AI, Cyber Security, Philosophy, and ideas that matter.

## ✍️ Latest Posts

<ul>
{% for post in site.posts %}
  <li>
    <strong>{{ post.date | date: "%Y-%m-%d" }}</strong> — 
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>

---

## 👤 Contact Me

I perform research and work professionally in Cyber Security.

You can reach me on [LinkedIn](https://www.linkedin.com/in/frostsec), or via [email](mailto:contact@frost.fyi).

---

**NB.** I use LLMs with CoT prompting to help present my research.  I provide the core ideas and structure in a stream-of-thought draft, then shape the final version through proofreading and fine-tuning.

