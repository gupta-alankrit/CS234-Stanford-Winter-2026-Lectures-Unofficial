---
layout: default
title: Modules
---

# Modules

Lecture materials are organized by topic.

{% for m in site.data.modules %}
<div class="module">
  <div class="module-title">{{ m.topic }}</div>

  {% assign lecture_num = 0 %}

  {% for it in m.items %}
    {% if it.kind == "Lecture" %}
      {% assign lecture_num = lecture_num | plus: 1 %}
      <div class="item-kind">Lecture</div>
      <div class="item-title">{{ lecture_num }}. {{ it.title }}</div>
      <div class="links">
        {% for l in it.links %}
          <a href="{{ l.url | relative_url }}">{{ l.label }}</a>
        {% endfor %}
      </div>
    {% else %}
      <div class="item-kind">{{ it.kind }}</div>
      <ul>
        {% for b in it.bullets %}
          <li><a href="{{ b.url }}">{{ b.label }}</a></li>
        {% endfor %}
      </ul>
    {% endif %}
  {% endfor %}
</div>
<hr />
{% endfor %}
