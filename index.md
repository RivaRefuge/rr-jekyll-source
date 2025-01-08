---
layout: default
title: Riva Refuge
menuEntry: home
---


<div id="wrap">
	{% comment %}<!-- Begin page content --> {% endcomment %}
	<section id="main_content" class="inner">
		<img src="/images/fp-hero.jpg" alt="Arms links">

		Riva Refuge is a small, secular non-profit organization that helps
		children, youth, young women, disabled, and elderly. Presently, we have
		three projects that need assistance:

{% capture campaigns_content %}
{% include campaigns.md %}
{% endcapture %}
{{ campaigns_content | markdownify }}


{% capture mission_content %}
{% include mission.html %}
{% endcapture %}
{{ mission_content | markdownify }}

{% include donate.html %}

	</section>

