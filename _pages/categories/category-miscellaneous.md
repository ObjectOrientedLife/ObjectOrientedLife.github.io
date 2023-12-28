---
title: "Miscellaneous"
layout: single
permalink: /miscellaneous/
sidebar:
    nav: "docs"
---

## Miscellaneous Topics

{% assign posts = site.categories.Miscellaneous %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}