---
layout: page
title: Daily Comic
permalink: /dailycomic/
---
<h1>Today's Comic</h1>

{% for post in site.posts limit:1 %}
<!-- NOTE: always post a daily comic after adding posts to site -->

  {{ post.content }}

{% endfor %}

_I'm taking 5 minutes every evening to draw a one-panel comic from my day, based on one of Lynda Barry's journaling methods_
