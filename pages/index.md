---
layout: default_wrapper
---

{% for post in site.posts %}
  <h3 class="ttl"><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>
  <h4 class="info">Post by {{ post.author }} at {{ post.date | date: "%Y-%m-%d" }}</h4>
  {% if post.excerpt %}
    <p>{{ post.excerpt }}</p>
  {% else %}
    <p>{{ post.content | strip_html | truncate: 250 }}</p>
  {% endif %}
  <div class="read-more"><a href="{{ site.baseurl }}{{ post.url }}">繼續閱讀</a></div>
{% endfor %}