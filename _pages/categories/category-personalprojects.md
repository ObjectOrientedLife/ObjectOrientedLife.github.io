---
title: "Personal Projects"
layout: single
excerpt: "Materials Related to My Own Indie Game Projects"
header:
  overlay_image: /assets/images/BackgroundPersonalProjects.png
permalink: /personalprojects/
sidebar:
    nav: "docs"
---

{% assign posts = site.categories.PersonalProjects | sort: 'order' | reverse %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}