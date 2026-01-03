---
collection: People
permalink: /people/
layout: archive
---

<h2>Our Team</h2>
{%  assign members = site.data.members %}


  {% for faculty in members %}
   <h2> {{ faculty[0] }} </h2>
  <div class="team-container">
   {% for person in faculty[1] %}
      <div class="tile-card">
        <div class="card-image">
          <img src="{{ person.image }}" alt="{{ person.name }}">
        </div>
        <div class="card-content">
          <h2 class="card-title">{{ person.name }}</h2>
          <p class="card-role">{{ person.role }}</p>
          {% if faculty[0] == 'Faculty'%}
          <p class="card-role"> {{ person.description }}</p>
          {% else %}
           <p class="card-role"> Supervised By: <strong>{{ person.description }} </strong> </p>
          {% endif %}
          {% if person.link %}
          <a href="{{ person.link }}" class="card-link">Learn More</a>
          {% endif %}
        </div>
      </div>
    {% endfor %}
    </div>
  {% endfor %}


{% assign graduated = site.data.graduated %}

  <h1>Graduated Students</h1>
  {% for people in graduated %}
  <h2>{{ people[0] }}</h2>
  <div class="team-container">
    {% for person in people[1] %}
      <div class="tile-card">
        <div class="card-image">
          <img src="{{ person.image }}" alt="{{ person.name }}">
        </div>
        <div class="card-content">
          <h2 class="card-title">{{ person.name }}</h2>
          <p class="card-role">{{ person.role }}</p>
          <p class="card-role"> Supervised By: <strong>{{ person.supervisedBy }}</strong> </p>
          {% if person.link %}
            <a href="{{ person.link }}" class="card-link">Learn More</a>
          {% endif %}
        </div>
      </div>
     {% endfor %}
    </div>
{% endfor %}



