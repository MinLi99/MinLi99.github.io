---
layout: page
permalink: /learning/index.html
title: Learning
---

Notes from courses, papers and hands-on experiments. Newest first.

{% assign notes = site.learning | sort: "date" | reverse %}
{% if notes.size > 0 %}
<ul class="learning-list">
  {% for note in notes %}
  {% assign summary = note.description | default: note.content | strip_html | normalize_whitespace | truncate: 180 %}
  <li>
    <a class="learning-title" href="{{ note.url | relative_url }}">{{ note.title }}</a>
    <time class="learning-date" datetime="{{ note.date | date_to_xmlschema }}">{{ note.date | date: "%Y-%m-%d" }}</time>
    {% if summary != "" %}<p class="learning-summary">{{ summary }}</p>{% endif %}
  </li>
  {% endfor %}
</ul>
{% else %}
<p>No notes yet — drop a Markdown file into <code>_learning/</code> to add one.</p>
{% endif %}

