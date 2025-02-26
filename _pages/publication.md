---
collection: publication
layout: archive
permalink: /publications/
---

<section class="publications">
  <header>
    <h2>Our Recent Publications</h2>
  </header>
  
  {% assign publications_by_year = site.data.publication %}
  {% for year in publications_by_year %}
    <article class="publication-year">
      <header>
        <h3>{{ year[0] }}</h3>
      </header>
      <div class="publications-list">
        {% for publication in year[1] %}
          <article class="publication-tile">
            {% if publication.image %}
              <figure class="publication-image">
                <img src="{{ publication.image }}" alt="{{ publication.title }}">
              </figure>
            {% endif %}
            <div class="publication-content">
              <h4>{{ publication.title }}</h4>
              <p><strong>Author(s):</strong> {{ publication.author }}</p>
              {% if publication.journal %}
                <p><strong>Journal:</strong> {{ publication.journal }}</p>
              {% endif %}
              {% if publication.conference %}
                <p><strong>Conference:</strong> {{ publication.conference }}</p>
              {% endif %}
              <p>
                <a href="{{ publication.link }}" class="publication-link">Read more</a>
              </p>
            </div>
          </article>
        {% endfor %}
      </div>
    </article>
  {% endfor %}
</section>

<section class="thesis-dissertation">
  <header>
    <h2>Thesis and Dissertation</h2>
  </header>
  <div class="publications-list">
    {% assign thesis_dissertation = site.data.dissertation %}
    {% for thesis in thesis_dissertation %}
      <article class="publication-tile">
        {% if thesis.image %}
          <figure class="publication-image">
            <img src="{{ thesis.image }}" alt="{{ thesis.title }}">
          </figure>
        {% endif %}
        <div class="publication-content">
          <h4>{{ thesis.title }}</h4>
          <p><strong>Author(s):</strong> {{ thesis.author }}</p>
          <p><strong>Institution:</strong> {{ thesis.institution }}</p>
          <p><strong>Year:</strong> {{ thesis.year }}</p>
          <p>
            <a href="{{ thesis.link }}" class="publication-link">Read more</a>
          </p>
        </div>
      </article>
    {% endfor %}
  </div>
</section>
