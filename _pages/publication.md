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
              {% if publication.url %}
                <p>
                  <a href="{{ publication.url }}" class="publication-link" target="_blank">Read the Article</a>
                </p>
              {% else %}
                {% assign associated_articles = site.articles | where: "publication_title", publication.title %}
                {% if associated_articles.size > 0 %}
                  <div class="associated-articles">
                    <h5>Associated Articles</h5>
                    <ul>
                      {% for article in associated_articles %}
                        <li><a href="{{ article.url }}">{{ article.title }}</a></li>
                      {% endfor %}
                    </ul>
                  </div>
                {% else %}
                  <p>
                    <a href="{{ publication.link }}" class="publication-link">Read more</a>
                  </p>
                {% endif %}
              {% endif %}
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
