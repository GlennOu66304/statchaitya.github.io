---
layout: archive
permalink: /machine-learning/
title: "Data Science blog"
author_profile: true
header:
  image: "images/wallpap_1_crop.jpg"
---

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive_subtitle"><em>{{ tag }}</em></h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
