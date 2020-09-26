---
layout: default
---

{% assign weighted_categories = site.category_weights %}
{% assign categories = site.categories %}
{% assign page_category = page.category %}
{% assign page_title = page.title %}

{% for category in categories %}
  <div class="category-group">
    {% assign sorted_articles = category[1] | sort: 'weight' %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    {% if category_name == page_category %}
      {% for article in sorted_articles %}
        {% if article.title == page_title %}
          {% assign currIndex = forloop.index0 %}
          {% assign prevIndex = currIndex | minus: 1 %}
          {% assign nextIndex = currIndex | plus: 1 %}
          {% assign articleIndexLength = forloop.length | minus: 1 %}
          <div class="page-navigation">
            {% if currIndex == 0 %}
              <a class="next0" href="{{ site.url }}{{ site.baseurl }}{{ sorted_articles[nextIndex].url }}">{{ sorted_articles[nextIndex].title }} &raquo;</a>
            {% elsif currIndex < articleIndexLength and currIndex != 0 %}
              <a class="prev" href="{{ site.url }}{{ site.baseurl }}{{ sorted_articles[prevIndex].url }}">&laquo; {{ sorted_articles[prevIndex].title }}</a>
              <a class="next" href="{{ site.url }}{{ site.baseurl }}{{ sorted_articles[nextIndex].url }}">{{ sorted_articles[nextIndex].title }} &raquo;</a>
            {% elsif currIndex == articleIndexLength %}
              <a class="prev" href="{{ site.url }}{{ site.baseurl }}{{ sorted_articles[prevIndex].url }}">&laquo; {{ sorted_articles[prevIndex].title }}</a>
            {% endif %}
          </div>
        {% endif %}
      {% endfor %}
    {% endif %}
  </div>
{% endfor %}
