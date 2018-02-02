---
title: Projects
sitemap: false
categories:
    - meta
---
{% capture current_date %}{{ site.time | date: '%s' }}{% endcapture %}
{% capture current_year %}{{ site.time | date: '%Y' }}{% endcapture %}
{% assign yearly_competition_count = 0 %}
{% assign filtered_fiction = site.fiction | where_exp:"project","project.path contains current_year" %}
{% assign completed_projects = site.data.projects | where_exp:"project","project.completed contains current_year" %}
{% assign outstanding_projects = site.data.projects | where_exp:"project","project.completed == nil" %}
{% assign filtered_projects = outstanding_projects | concat: completed_projects | sort: 'completed' %}

An automatically updating list of the items I'm working on in {{ current_year }}. It will live here as a shaming reminder for future-me to actually complete them.

<!-- Projects published on the site -->
{% if filtered_fiction.size > 0 %}
{% if filtered_projects.size > 0 %}
### Here
{% endif %}

  {% for story in filtered_fiction %}
  - ~~_[{{ story.title }}]({{ story.link }})_, a {{ story.genre }} {{ story.type }}~~, completed in {{ story.date | date: '%B' }}.
  {% if story.competition %}
  {% assign yearly_competition_count = yearly_competition_count | plus: 1 %}
  {% endif %}
  {% endfor %}
{% endif %}

<!-- Projects not published on the site -->
{% if filtered_projects.size > 0 %}
{% if filtered_fiction.size > 0 %}
### Elsewhere
{% endif %}

  {% for project in filtered_projects %}
  {% capture completion_date %}{{ project.completed | date: '%s' }}{% endcapture %}
  {% if completion_date == "" %}{% assign completion_date = current_date %}{% endif %}
  - {% if completion_date < current_date %}~~{% endif %}_{% if project.link %}[{{ project.title }}]({{ project.link }}){% else %}{{ project.title }}{% endif %}_, a {{ project.type }}{% if completion_date < current_date %}~~, completed in {{ project.completed | date: '%B' }}{% endif %}.
  {% endfor %}
{% endif %}

<!-- Shame counter -->
{% assign total_yearly_project_count = completed_projects.size | plus: yearly_competition_count %}
{% assign total_writing_exercise_count = filtered_fiction.size | minus: yearly_competition_count %}

I have completed {{ total_writing_exercise_count }} writing exercise{% if total_writing_exercise_count != 1 %}s{% endif %} and {{ total_yearly_project_count }} longer-form project{% if total_yearly_project_count != 1 %}s{% endif %} so far this year.
