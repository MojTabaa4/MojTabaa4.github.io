---
layout: page
title: Projects
permalink: /projects/
description:
nav: true
nav_order: 4
#display_categories: [All, MACHINE LEARNING, WEB APPLICATION, OPERATING SYSTEMS, COMPUTER VISION]
display_categories: 
is_active: false
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{% if page.is_active -%}
    {%- if site.enable_project_categories and page.display_categories %}
      <!-- Display categorized projects -->
      {%- for category in page.display_categories %}
      <h2 class="category">{{ category }}</h2>
      {%- assign categorized_projects = site.projects | where: "category", category -%}
      {%- assign sorted_projects = categorized_projects | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal -%}
      <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
          {% include projects_horizontal.html %}
        {%- endfor %}
        </div>
      </div>
      {%- else -%}
      <div class="grid">
        {%- for project in sorted_projects -%}
          {% include projects.html %}
        {%- endfor %}
      </div>
      {%- endif -%}
      {% endfor %}
    
    {%- else -%}
    <!-- Display projects without categories -->
      {%- assign sorted_projects = site.projects | sort: "importance" -%}
      <!-- Generate cards for each project -->
      {% if page.horizontal -%}
      <div class="container">
        <div class="row row-cols-2">
        {%- for project in sorted_projects -%}
          {% include projects_horizontal.html %}
        {%- endfor %}
        </div>
      </div>
      {%- else -%}
      <div class="grid">
        {%- for project in sorted_projects -%}
          {% include projects.html %}
        {%- endfor %}
      </div>
      {%- endif -%}
    {%- endif -%}
{%- else -%}
This page is currently being developed, but if you're eager to access my projects, you can find them on my <a href="https://github.com/MojTabaa4">GitHub page</a>.
{%- endif -%}
</div>
