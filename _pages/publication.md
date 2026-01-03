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
      {% if max_count == 0 %}
        {% assign max_count = 1 %}
      {% endif %}
      {% assign max_height = 200 %}
      {% assign years_array = '' | split: '' %}
      {% for year in publications_by_year %}
        {% assign year_num = year[0] | plus: 0 %}
        {% assign years_array = years_array | push: year_num %}
      {% endfor %}
      {% assign sorted_years = years_array | sort %}
      <!-- Chart bars container -->
      <div style="display: flex; align-items: flex-end; gap: 0.5rem; justify-content: center; flex-wrap: nowrap; width: 100%; margin-bottom: 0.5rem; height: 250px; padding-bottom: 2rem;">
        {% for year_num in sorted_years %}
          {% assign year_str = year_num | append: '' %}
          {% assign count = 0 %}
          {% for year in publications_by_year %}
            {% if year[0] == year_str %}
              {% assign count = year[1] | size %}
            {% endif %}
          {% endfor %}
          {% if count > 0 %}
            {% if max_count > 0 %}
              {% assign bar_height_calc = count | times: max_height %}
              {% assign bar_height = bar_height_calc | divided_by: max_count %}
            {% else %}
              {% assign bar_height = max_height %}
            {% endif %}
            {% if bar_height < 20 %}
              {% assign bar_height = 20 %}
            {% endif %}
          {% else %}
            {% assign bar_height = 0 %}
          {% endif %}
          <div style="flex: 1; min-width: 50px; max-width: 80px; display: flex; flex-direction: column; align-items: center; justify-content: flex-end; height: 100%;">
            {% if count > 0 %}
            <div style="background: linear-gradient(to top, #4a90e2 0%, #357abd 100%); height: {{ bar_height }}px; width: 80%; min-width: 30px; min-height: 20px; border-radius: 4px 4px 0 0; position: relative; transition: opacity 0.3s; box-sizing: border-box;" title="{{ count }} publication{% if count != 1 %}s{% endif %} in {{ year_str }}">
              <span style="position: absolute; top: -1.5rem; left: 50%; transform: translateX(-50%); font-size: 0.85rem; font-weight: 600; color: #e0e0e0; white-space: nowrap; z-index: 1;">{{ count }}</span>
            </div>
            {% else %}
            <div style="background: transparent; height: 0px; width: 80%; min-width: 30px; border-radius: 4px 4px 0 0; position: relative; opacity: 0.3;" title="0 publications in {{ year_str }}">
            </div>
            {% endif %}
          </div>
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
  {% assign sorted_years_pubs = '' | split: '' %}
  {% for year in publications_by_year %}
    {% assign year_num = year[0] | plus: 0 %}
    {% assign sorted_years_pubs = sorted_years_pubs | push: year_num %}
  {% endfor %}
  {% assign sorted_years_pubs = sorted_years_pubs | sort | reverse %}
  
  {% for year_num in sorted_years_pubs %}
    {% assign year_str = year_num | append: '' %}
    {% for year in publications_by_year %}
      {% if year[0] == year_str %}
        <article class="publication-year">
          <header>
            <h3>{{ year[0] }}</h3>
          </header>
          <div class="publications-table-container">
            <table class="publications-table">
              <thead>
                <tr>
                  <th style="width: 120px;">Image</th>
                  <th>Citation (APA 7th Edition)</th>
                  <th style="width: 100px;">Link</th>
                </tr>
              </thead>
              <tbody>
                {% for publication in year[1] %}
                  <tr class="publication-row">
                    <td class="publication-image-cell">
                      {% if publication.image %}
                        <img src="{{ publication.image }}" alt="{{ publication.title }}" class="publication-thumbnail">
                      {% else %}
                        <img src="/assets/images/papers/research.jpg" alt="Research paper" class="publication-thumbnail">
                      {% endif %}
                    </td>
                    <td class="publication-citation-cell">
                      <div class="publication-citation">
                        <strong class="publication-title">{{ publication.title }}</strong>
                        <br>
                        <span class="publication-authors">{{ publication.author }}</span>
                        {% if publication.journal %}
                          <br><span class="publication-venue">{{ publication.journal }}</span>
                        {% endif %}
                        {% if publication.conference %}
                          <br><span class="publication-venue">{{ publication.conference }}</span>
                        {% endif %}
                        <br><span class="publication-year-label">({{ year[0] }})</span>
                      </div>
                    </td>
                    <td class="publication-link-cell">
                      {% if publication.url %}
                        <a href="{{ publication.url }}" class="publication-table-link" target="_blank" rel="noopener noreferrer" title="Read the article">📄</a>
                      {% else %}
                        {% assign associated_articles = site.articles | where: "publication_title", publication.title %}
                        {% if associated_articles.size > 0 %}
                          <a href="{{ associated_articles.first.url }}" class="publication-table-link" title="Read more">📄</a>
                        {% else %}
                          {% if publication.link %}
                            <a href="{{ publication.link }}" class="publication-table-link" title="Read more">📄</a>
                          {% else %}
                            <span class="publication-no-link">—</span>
                          {% endif %}
                        {% endif %}
                      {% endif %}
                    </td>
                  </tr>
                {% endfor %}
              </tbody>
            </table>
          </div>
        </article>
      {% endif %}
    {% endfor %}
  {% endfor %}
</section>


