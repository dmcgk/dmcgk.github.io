---
title: Site Statistics
sitemap: false
categories:
    - meta
---

{% assign wordcount = 0%}
{% assign total_posts = site.posts | concat: site.fiction %}
{% for post in total_posts %}
	{% assign rawpost = post | strip_html %}
	{% assign post_wordcount = rawpost | number_of_words %}
	{% assign wordcount = wordcount | plus: post_wordcount %}
{% endfor %}

There are {{ total_posts.size }} posts on [{{ site.long_title }}](/), totalling {{ wordcount }} words. The site was last updated on {{ site.time | date: '%B %d, %Y' }}.
