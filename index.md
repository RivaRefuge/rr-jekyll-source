---
layout: default
title: Riva Refuge
menuEntry: home
---


<div id="wrap">
	{% comment %}<!-- Begin page content --> {% endcomment %}
	<section id="main_content" class="inner">
		<img src="/images/fp-hero.jpg" alt="Linked arms symbolizing unity and support among diverse individuals.">

		Riva Refuge is a small, secular non-profit organization that helps
		children, youth, young women, disabled, and elderly. Presently, we have
		three projects that need assistance:

{% capture campaigns_content %}
{% include campaigns.md %}
{% endcapture %}
{{ campaigns_content | markdownify }}


		Our mission is to elevate the well-being of disadvantaged people, empowering them to succeed. We work in several countries in Africa and sometimes in Central America, the Caribbean and the United States. We are a volunteer only organization with no paid staff.

{% include donate.html %}

	</section>

