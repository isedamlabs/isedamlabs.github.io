---
title: Teaching
collection: teaching
layout: archive
permalink: /teaching/
---



{% assign teachings_by_year = site.data.teaching %}

{% for year in teachings_by_year %}
  <h2>{{ year[0] }}</h2>
  <div class="teaching-grid">
    {% for teaching in year[1] %}
      <div class="teaching-tile">
        <div class="teaching-content">
          <h3>{{ teaching.title }}</h3>
          <p><strong>Instructor:</strong> {{ teaching.instructor }}</p>
          <p><strong>Location:</strong> {{ teaching.location }}</p>
          <p><strong>Description:</strong> {{ teaching.description }}</p>
          <a href="{{ teaching.link }}">More Info</a>
        </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}
