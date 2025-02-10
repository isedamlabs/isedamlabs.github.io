---

collection: publication
layout: archive
permalink: /publications/
---


<h2>Our Recent Publications</h2>

{% assign publications_by_year = site.data.publication %}

{% for year in publications_by_year %}
  <h2>{{ year[0] }}</h2>
  <div class="publications-grid">
    {% for publication in year[1] %}
      <div class="publication-tile">
        <div class="publication-image">
          {% if publication.image %}
            <img src="{{ publication.image }}" alt="{{ publication.title }}">
          {% endif %}
        </div>
        <div class="publication-content">
          <h3>{{ publication.title }}</h3>
          <p><strong>Author(s):</strong> {{ publication.author }}</p>
          {% if publication.journal %}
            <p><strong>Journal:</strong> {{ publication.journal }}</p>
          {% endif %}
          {% if publication.conference %}
            <p><strong>Conference:</strong> {{ publication.conference }}</p>
          {% endif %}
          <a href="{{ publication.link }}" class="publication-link">Read more</a>
        </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}


<h2>Thesis and Dissertation</h2>

{% assign thesis_dissertation = site.data.publication.thesis_dissertation %}

<div class="publications-grid">
  {% for thesis in thesis_dissertation %}
    <div class="publication-tile">
      <div class="publication-image">
        {% if thesis.image %}
          <img src="{{ thesis.image }}" alt="{{ thesis.title }}">
        {% endif %}
      </div>
      <div class="publication-content">
        <h3>{{ thesis.title }}</h3>
        <p><strong>Author(s):</strong> {{ thesis.author }}</p>
        <p><strong>Institution:</strong> {{ thesis.institution }}</p>
        <p><strong>Year:</strong> {{ thesis.year }}</p>
        <a href="{{ thesis.link }}" class="publication-link">Read more</a>
      </div>
    </div>
  {% endfor %}
</div>
