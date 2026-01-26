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

{% if site.enable_project_categories and page.display_categories %}

  {% for category in page.display_categories %}
    <a id="{{ category }}"></a>
    <h2 class="category">{{ category | capitalize }}</h2>

    {% assign categorized_projects = site.projects | where: "category", category %}
    {% assign sorted_projects = categorized_projects | sort: "importance" %}

    <div class="row row-cols-1">
      {% for project in sorted_projects %}
        <div class="col mb-5">
          <article class="project-full">

            <h3>{{ project.title }}</h3>

            {% if project.img %}
              <img
                src="{{ project.img | relative_url }}"
                alt="{{ project.title }}"
                class="img-fluid mb-3 d-block mx-auto"
                style="max-width: 350px;">
            {% endif %}

            {% if project.description %}
              <p class="text-muted">{{ project.description }}</p>
            {% endif %}

            <div class="project-content">
              {{ project.content }}
            </div>

          </article>
          <hr>
        </div>
      {% endfor %}
    </div>

  {% endfor %}

{% else %}

  {% assign sorted_projects = site.projects | sort: "importance" %}

  <div class="row row-cols-1">
    {% for project in sorted_projects %}
      <div class="col mb-5">
        <article class="project-full">

          <h3>{{ project.title }}</h3>

          {% if project.img %}
            <img
              src="{{ project.img | relative_url }}"
              alt="{{ project.title }}"
              class="img-fluid mb-3 d-block mx-auto"
              style="max-width: 350px;">
          {% endif %}

          {% if project.description %}
            <p class="text-muted">{{ project.description }}</p>
          {% endif %}

          <div class="project-content">
            {{ project.content }}
          </div>

        </article>
        <hr>
      </div>
    {% endfor %}
  </div>

{% endif %}

</div>
