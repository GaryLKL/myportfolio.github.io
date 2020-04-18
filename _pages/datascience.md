---
layout: archive
permalink: /data-science/
title: "Data Science"
author_profile: true
excerpt: " "
header: 
  overlay_image: "/images/programming.jpg"
  overlay_filter: 0.5

---


{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}