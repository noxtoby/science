---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  You can also find my articles on <u><a href="{{site.author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

Publications according to UCL's Research Publications Service:

<iframe style="margin: 0; border: 0; font-family: 'Arial Narrow', Arial, sans-serif;" src="http://research-reports.ucl.ac.uk/RPSDATA.SVC/pubs/noxto55" width="100%" height="800" scrolling="yes"></iframe>

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
