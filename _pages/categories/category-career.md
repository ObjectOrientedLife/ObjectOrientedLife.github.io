---
title: "Career"
layout: archive
permalink: /career/
sidebar:
    nav: "docs"
---

## About My Career As a Software Engineer

{% assign posts = site.categories.Career %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}