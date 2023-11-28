---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Home
---
<h1>Today's Comic</h1>

{% for post in site.posts limit:1 %}

  {{ post.title }}
  {{ post.content }}

{% endfor %}
