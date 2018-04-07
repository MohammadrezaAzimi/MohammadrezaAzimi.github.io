---
layout: archive
permalink: /cv/
title: "Computer Vision Projects by Tags"
author_profile: true
header:
  image: "/images/datascience.png"
---

{% include base_path %}
{% include group-by-array collection=site.postscv field="tags" %}

{% for tag in group_names %}
   {% assign postscv = group_items[forloop.index0] %}
   <h2 id="{{ tag | slugify }}" class="archive_subtitle">{{ tag }} </h2>
   {% for post in postscv %}
      {% include archive-single.html %}
   {% endfor %}
{% endfor %}
