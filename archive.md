---
layout: page
title: archive
---

<section id="archive">
  {%for post in site.posts %}
    {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
    {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
    {% if year != nyear %}
      {% if forloop.index != 1 %}</ul>{% endif %}
      <h3>{{ post.date | date: '%Y' }}</h3><ul>
    {% endif %}
    <li><time>{{ post.date | date:"%d %b" }}</time> <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</section>
