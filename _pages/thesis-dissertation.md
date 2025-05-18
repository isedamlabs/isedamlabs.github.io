---
collection: thesis-dissertation
layout: archive
permalink: /thesis-dissertation/
---

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
          {% if thesis.url %}
            <p>
              <a href="{{ thesis.url }}" class="publication-link">Read the Article</a>
            </p>
          {% else %}
            <p>
              <a href="{{ thesis.link }}" class="publication-link">Read more</a>
            </p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>
