---
title: Current projects
permalink: /now/
sitemap: false
---

An automatically updating list of the items I'm currently (claiming to be) working on. It will live here as a shaming reminder for future-me to actually complete them.

{% for project in site.data.projects  %}
- _[{{ project.title }}]({{ project.link }})_, a {{ project.type }}.
{% endfor %}
