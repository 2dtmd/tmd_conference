---
layout: page
title: Invited Speakers
permalink: /invited_speakers/
---

{% comment %} Step 1: Extract surnames and construct a sortable array {% endcomment %}
{% assign sorted_invitedSpeakers = "" | split: "" %}

{% for pair in site.data.2D_Conference %}
  {% assign name_parts = pair["Name"] | strip | split: " " %}
  {% assign surname = name_parts | last %}
  {% comment %} Combine surname and original index to preserve data association {% endcomment %}
  {% assign sort_key = surname | append: "___" | append: forloop.index0 %}
  {% assign sorted_invitedSpeakers = sorted_invitedSpeakers | push: sort_key %}
{% endfor %}

{% comment %} Step 2: Sort by the keys (surnames) {% endcomment %}
{% assign sorted_keys = sorted_invitedSpeakers | sort %}

<div class="entries-grid">
{% for key in sorted_keys %}
  {% comment %} Step 3: Retrieve original data item using the index {% endcomment %}
  {% assign index = key | split: "___" | last | plus: 0 %}
  {% assign pair = site.data.2D_Conference[index] %}

  <article class="portrait">
    <img src="{{ '/assets/Invited Speakers/Accepted/' | relative_url }}{{ pair['Name'] | strip }}.jpg" class="portrait">
    <b>{{ pair["Name"] | strip }}</b>
    <em>{{ pair["Institute"] | strip }}</em>
  </article>
{% endfor %}
</div>
