---
layout: default
title: Mark — Greek / Spanish Reader
---

# Mark — Greek / Spanish Reader

{% assign chapters = site.pages | where_exp: "p", "p.path contains 'mark-'" | sort: "path" %}
{% for chapter in chapters %}
- [{{ chapter.title }}]({{ chapter.url | relative_url }})
{% endfor %}
