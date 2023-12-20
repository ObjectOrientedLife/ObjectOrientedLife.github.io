---
title: "Professional Projects"
layout: archive
permalink: /professionalprojects/
sidebar:
    nav: "docs"
---

## About Projects I Have Experienced as a Professional Software Engineer

{% assign posts = site.categories.ProfessionalProjects %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}