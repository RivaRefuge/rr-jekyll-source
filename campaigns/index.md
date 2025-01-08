---
layout: page
title: Campaigns
menuEntry: campaigns
---

![Arms links](/images/fp-hero.jpg)

Riva Refuge is a small, secular non-profit organization that helps children, youth, young women, disabled, and elderly. Presently, we have three projects that need assistance:

{% capture campaigns_content %}
{% include campaigns.md %}
{% endcapture %}
{{ campaigns_content | markdownify }}

{% capture mission_content %}
{% include mission.html %}
{% endcapture %}
{{ mission_content | markdownify }}


