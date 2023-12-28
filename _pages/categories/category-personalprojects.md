---
title: "Personal Projects"
layout: archive
permalink: /personalprojects/
sidebar:
    nav: "docs"
---

## Materials Related to My Own Indie Game Projects

{% assign posts = site.categories.PersonalProjects | sort: 'order' | reverse %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}