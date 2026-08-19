---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults


layout: home
title: 2D Transition Metal Dichalcogenides 2027
sub_title: June 27 - July 1, 2027 | Churchill College, Cambridge, UK
image: /assets/top_banner.jpg
introduction: |
  <p>Following successful 2D TMDs conferences in Cambridge (2023), Hong Kong (2024), Cambridge (2025) and Singapore (2026), the conference will return to Cambridge in 2027.</p>
  
  <p>2D TMDs 2027 will bring together leading researchers from academia and industry to present and discuss recent advances in atomically thin TMDs. The programme will span fundamental materials synthesis and physics through to device fabrication, integration and emerging applications in electronics, photonics, spintronics, catalysis, and energy conversion and storage.</p>
  
  <p><b>Abstracts from students and postdoctoral researchers are very welcome.</b></p>
---

## Topics

Topics will include but are not limited to:

{% comment %} Calculate the halfway point automatically {% endcomment %}
{% assign total_topics = site.data.topics | size %}
{% assign half_point = total_topics | divided_by: 2.0 | ceil %}

<div class="topics-grid">
  <div>
    <ul>
      {% for topic in site.data.topics limit: half_point %}
        <li>{{ topic['name'] }}</li>
      {% endfor %}
    </ul>
  </div>
  <div>
    <ul>
      {% for topic in site.data.topics offset: half_point %}
        <li>{{ topic['name'] }}</li>
      {% endfor %}
    </ul>
  </div>
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
