---
title: Projects
sitemap: false
categories:
    - meta
---

An automatically updating list of the items I'm currently (claiming to be) working on. It will live here as a shaming reminder for future-me to actually complete them.

{% capture today_date %}{{ site.time | date: '%s' }}{% endcapture %}
{% capture today_year %}{{ site.time | date: '%Y' }}{% endcapture %}

<!-- Projects published on the site -->
### Here

{% assign yearly_site_project_count = 0 %}

{% if site.fiction.size > 0 %}
  {% for story in site.fiction %}
  {% assign story_year = story.date | date: '%Y' %}
  {% if story_year == today_year %}
	{% assign yearly_site_project_count = yearly_site_project_count | plus: 1 %}
  {% endif %}
  - ~~_[{{ story.title }}]({{ story.link }})_, a {{ story.genre }} {{ story.type }}~~, completed in {{ story.date | date: '%B %Y' }}.
  {% endfor %}
{% else %}
  - N/A
{% endif %}

<!-- Projects not published on the site -->
### Elsewhere

{% assign sorted_projects = site.data.projects | sort: 'completed' %}
{% assign yearly_project_count = 0 %}

{% if sorted_projects.size > 0 %}
  {% for project in sorted_projects %}
  {% if project.completed contains today_year %}
    {% assign yearly_project_count = yearly_project_count | plus: 1 %}
  {% endif %}
  {% capture completion_date %}{{ project.completed | date: '%s' }}{% endcapture %}
  {% if completion_date == "" %}{% assign completion_date = today_date %}{% endif %}
  - {% if completion_date < today_date %}~~{% endif %}_{% if project.link %}[{{ project.title }}]({{ project.link }}){% else %}{{ project.title }}{% endif %}_, a {{ project.type }}{% if completion_date < today_date %}~~, completed in {{ project.completed | date: '%B %Y' }}{% endif %}.
  {% endfor %}
{% endif %}

<!-- Shame counter -->
I have completed {{ yearly_site_project_count }} writing exercise{% if yearly_site_project_count != 1 %}s{% endif %} and {{ yearly_project_count }} longer-form project{% if yearly_project_count != 1 %}s{% endif %} so far in {{ today_year }}.
