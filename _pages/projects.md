---
layout: page
title: Projects
permalink: /projects/
description: Research projects and academic work
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">
  {% assign sorted_projects = site.projects | sort: "importance" %}
  {% if site.enable_project_categories and page.display_categories %}
    {% for category in page.display_categories %}
      {% assign categorized_projects = sorted_projects | where: "category", category %}
      {% if categorized_projects.size > 0 %}
        <a id="{{ category }}"></a>
        <h2 class="category">{{ category | capitalize }}</h2>
        <div class="row row-cols-1 row-cols-md-2">
          {% for project in categorized_projects %}
            {% include projects.liquid %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}
  {% else %}
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in sorted_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  {% endif %}
</div>
