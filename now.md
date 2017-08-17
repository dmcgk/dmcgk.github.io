---
title: Projects
permalink: /now/
sitemap: false
---

An automatically updating list of the items I'm currently (claiming to be) working on. It will live here as a shaming reminder for future-me to actually complete them.

{% capture today_date %}{{'now' | date: '%s'}}{% endcapture %}
{% assign sorted_projects = site.data.projects | sort: 'completed' %}

{% for project in sorted_projects %}
{% capture completion_date %}{{ project.completed | date: '%s' }}{% endcapture %}
{% if completion_date == "" %}{% assign completion_date = today_date %}{% endif %}
- {% if completion_date < today_date %}~~{% endif %}_{% if project.link %}[{{ project.title }}]({{ project.link }}){% else %}{{ project.title }}{% endif %}_, a {{ project.type }}{% if completion_date < today_date %}~~, completed in {{ project.completed | date: '%B %Y' }}{% endif %}.
{% endfor %}
