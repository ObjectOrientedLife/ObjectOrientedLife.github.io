---
title: "Professional Projects"
layout: single
excerpt: "About Projects I Have Engaged in as a Professional Software Engineer"
header:
  overlay_image: /assets/images/BackgroundProfessionalProjects.jpg
permalink: /professionalprojects/
sidebar:
    nav: "docs"
---

{% assign posts = site.categories.ProfessionalProjects | sort: 'order' | reverse %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}