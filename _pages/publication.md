---
collection: publication
layout: archive
permalink: /publications/
---

<section class="publications">
  <header>
    <h2>Our Recent Publications</h2>
  </header>
  
  <!-- Publication Timeline Graph -->
  <div style="margin: 2rem 0 3rem 0; padding: 1.5rem; background: #2d2d2d; border-radius: 8px;">
    <h3 style="margin-top: 0; margin-bottom: 1.5rem; font-size: 1.1rem; color: #e0e0e0;">Publications by Year</h3>
    <div style="display: flex; flex-direction: column; align-items: center;">
      {% assign publications_by_year = site.data.publication %}
      {% assign max_count = 0 %}
      {% for year in publications_by_year %}
        {% assign count = year[1] | size %}
        {% if count > max_count %}
          {% assign max_count = count %}
        {% endif %}
      {% endfor %}
      {% assign max_height = 200 %}
      {% assign years_array = '' | split: '' %}
      {% for year in publications_by_year %}
        {% assign year_num = year[0] | plus: 0 %}
        {% assign years_array = years_array | push: year_num %}
      {% endfor %}
      {% assign sorted_years = years_array | sort %}
      <!-- Chart bars container -->
      <div style="display: flex; align-items: flex-end; gap: 0.5rem; justify-content: center; flex-wrap: nowrap; width: 100%; margin-bottom: 0.5rem; min-height: 220px; padding-bottom: 2rem;">
        {% for year_num in sorted_years %}
          {% assign year_str = year_num | append: '' %}
          {% for year in publications_by_year %}
            {% if year[0] == year_str %}
              {% assign count = year[1] | size %}
              {% assign bar_height = count | times: max_height | divided_by: max_count %}
              {% if bar_height < 20 and count > 0 %}
                {% assign bar_height = 20 %}
              {% endif %}
              <div style="flex: 1; min-width: 50px; max-width: 80px; text-align: center; display: flex; flex-direction: column; align-items: center; justify-content: flex-end;">
                <div style="background: linear-gradient(to top, #4a90e2 0%, #357abd 100%); height: {{ bar_height }}px; width: 80%; min-width: 30px; border-radius: 4px 4px 0 0; position: relative; transition: opacity 0.3s; {% if count == 0 %}opacity: 0.3;{% endif %}" title="{{ count }} publication{% if count != 1 %}s{% endif %} in {{ year[0] }}">
                  {% if count > 0 %}
                  <span style="position: absolute; top: -1.5rem; left: 50%; transform: translateX(-50%); font-size: 0.85rem; font-weight: 600; color: #e0e0e0; white-space: nowrap;">{{ count }}</span>
                  {% endif %}
                </div>
              </div>
            {% endif %}
          {% endfor %}
        {% endfor %}
      </div>
      <!-- X-axis labels (years) -->
      <div style="display: flex; gap: 0.5rem; justify-content: center; flex-wrap: nowrap; width: 100%; border-top: 1px solid #444; padding-top: 0.5rem;">
        {% for year_num in sorted_years %}
          {% assign year_str = year_num | append: '' %}
          <div style="flex: 1; min-width: 50px; max-width: 80px; text-align: center;">
            <div style="font-size: 0.9rem; color: #b0b0b0; font-weight: 500;">{{ year_str }}</div>
          </div>
        {% endfor %}
      </div>
    </div>
  </div>
  
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
                  <a href="{{ publication.url }}" class="publication-link" target="_blank" rel="noopener noreferrer">Read the Article</a>
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


