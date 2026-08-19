---
layout: home
title: 2D Transition Metal Dichalcogenides 2027
sub_title: June 27 - July 1, 2027 | Churchill College, Cambridge, UK
image: /assets/top_banner.jpg
---

Following successful 2D TMDs conferences in Cambridge (2023), Hong Kong (2024), Cambridge (2025) and Singapore (2026), the conference will return to Cambridge in 2027.

2D TMDs 2027 will bring together leading researchers from academia and industry to present and discuss recent advances in atomically thin TMDs. The programme will span fundamental materials synthesis and physics through to device fabrication, integration and emerging applications in electronics, photonics, spintronics, catalysis, and energy conversion and storage.

**Abstracts from students and postdoctoral researchers are very welcome.**


## Topics

Topics will include but are not limited to:

<div style="display: flex; justify-content: center; width: 100%; margin: 1.5rem 0;">
  <ul style="display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 0.75rem 2.5rem; max-width: 900px; width: 100%; padding-left: 1.25rem; margin: 0; list-style-type: disc;">
    {% for topic in site.data.topics %}
      <li style="margin: 0; line-height: 1.4;">{{ topic['name'] }}</li>
    {% endfor %}
  </ul>
</div>

## Plenary Speakers

{% comment %} Step 1: Extract surnames and construct a sortable array {% endcomment %}
{% assign sorted_plenaries = "" | split: "" %}

{% for pair in site.data.plenaries %}
  {% assign name_parts = pair["Name"] | strip | split: " " %}
  {% assign surname = name_parts | last %}
  {% comment %} Combine surname and original index to preserve data association {% endcomment %}
  {% assign sort_key = surname | append: "___" | append: forloop.index0 %}
  {% assign sorted_plenaries = sorted_plenaries | push: sort_key %}
{% endfor %}

{% comment %} Step 2: Sort by the keys (surnames) {% endcomment %}
{% assign sorted_keys = sorted_plenaries | sort %}

<div class="entries-grid">
{% for key in sorted_keys %}
  {% comment %} Step 3: Retrieve original data item using the index {% endcomment %}
  {% assign index = key | split: "___" | last | plus: 0 %}
  {% assign pair = site.data.plenaries[index] %}

  <article class="portrait">
    <img src="{{ '/assets/Plenary Speakers/' | relative_url }}{{ pair['Name'] | strip }}.jpg" class="portrait">
    <b>{{ pair["Name"] | strip }}</b>
    <em>{{ pair["Institute"] | strip }}</em>
  </article>
{% endfor %}
</div>


## Organizers





<div class="speaker-box">
{% for pair in site.data.organizers %}

	<article class="portrait">
		<img src="{{ '/assets/organizers/' | relative_url }}{{ pair['Name'] }}.jpg" class="portrait">
        <b>{{ pair["Name"] }}</b>
        <em>{{ pair["Institute"] }}</em>
	</article>
{% endfor %}
</div>



## Co-organizers

<div class="speaker-box">
{% for pair in site.data.co-organizers %}

	<article class="portrait">
		<img src="{{ '/assets/co-organizers/' | relative_url }}{{ pair['Name'] }}.jpg" class="portrait">
        <b>{{ pair["Name"] }}</b>
        <em>{{ pair["Institute"] }}</em>
	</article>
{% endfor %}
</div>


## Sponsors

To be Confirmed.

{% comment %}

{% assign sponsors = "HenryRoyceInstitute.png;Aixtron.svg;molyon.png;weboftalents.png;RoyceCambridgelogo.jpg;APLEnergyElectronicslogo.jpg;Linkzilllogo.jpg;HeidelbergInstruments.png;Qlibri.png;nature materials.png;qamss.png" | split: ";"  %}


<div class="tmd-sponsors">
	{% for logoName in sponsors %}
	<article class="tmd-sponsors">
		<img src="{{ '/assets/sponsors/' | relative_url }}{{logoName}}" class="logo">
	</article>
	{% endfor %}
</div>

{% endcomment %}
