---
layout: default
title: Riva Refuge
menuEntry: home
---

<div id="wrap">
	<!-- Begin page content -->
	<section id="main_content" class="inner">
		<img src="/images/fp-hero.jpg" alt="Arms links">

		Riva Refuge is a small, secular non-profit organization that helps
		children, youth, young women, disabled, and elderly. Presently, we have
		four projects that need assistance:
		{% comment %}{% markdown campaigns.md %}{% endcomment %}
		{% include campaigns.md %}
		{% comment %}{% capture my-include %}{% include campaigns.md %}{% endcapture %}
		{{ my-include | markdownify }}{% endcomment %}

		Our mission is to elevate the well-being of disadvantaged people, empowering them to succeed. We work in several countries in Africa and sometimes in Central America, the Caribbean and the United States. We are a volunteer only organization with no paid staff.

		{% include donate.html %}

	</section>

	<section>
		{%include twitter-timeline.html %}
	</section>
