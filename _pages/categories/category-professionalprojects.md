---
title: "Professional Projects"
layout: archive
permalink: /professionalprojects/
sidebar:
    nav: "docs"
---

## About Projects I Have Engaged in as a Professional Software Engineer

{% assign posts = site.categories.ProfessionalProjects | sort: 'order' | reverse %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}