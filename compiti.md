---
title: Ultimi compiti assegnati
layout: page
---

<style>
.compiti-lista {
  list-style: none;
  padding: 0;
  margin: 1.5rem 0;
}
.compito-card {
  border-left: 5px solid #ccc;
  border-radius: 6px;
  background: #fff;
  padding: 1rem 1.2rem;
  margin-bottom: 1.1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
.compito-materia {
  font-size: 0.78rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin-bottom: 0.5rem;
}
.compito-separatore {
  height: 1px;
  border: none;
  margin: 0.5rem 10% 0.75rem;
  background: linear-gradient(to right, transparent, currentColor, transparent);
  opacity: 0.35;
}
.compito-testo {
  font-size: 1rem;
  margin: 0.3rem 0 0.5rem;
  line-height: 1.55;
}
.compito-scadenza {
  font-size: 0.82rem;
  color: #555;
}
.compito-link {
  display: inline-block;
  margin-top: 0.6rem;
  font-size: 0.85rem;
  padding: 5px 13px;
  border-radius: 5px;
  text-decoration: none;
  background: #f0f0f0;
  color: #2d2d2d;
}
.compito-link:hover {
  background: #e0e0e0;
}
.compito-links {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 0.6rem;
}

/* Colori per materia */
.materia-italiano  { border-left-color: #FF00FF; color: #FF00FF; }
.materia-italiano .compito-separatore { background: linear-gradient(to right, transparent, #FF00FF, transparent); }
.materia-italiano .compito-testo,
.materia-italiano .compito-scadenza { color: #2d2d2d; }

.materia-storia    { border-left-color: #c8651a; color: #c8651a; }
.materia-storia .compito-separatore { background: linear-gradient(to right, transparent, #c8651a, transparent); }
.materia-storia .compito-testo,
.materia-storia .compito-scadenza { color: #2d2d2d; }

.materia-geografia { border-left-color: #6aab2e; color: #6aab2e; }
.materia-geografia .compito-separatore { background: linear-gradient(to right, transparent, #6aab2e, transparent); }
.materia-geografia .compito-testo,
.materia-geografia .compito-scadenza { color: #2d2d2d; }
</style>

<ul class="compiti-lista">
{% for compito in site.data.compiti %}
  {% assign slug = compito.materia | downcase %}
  <li class="compito-card materia-{{ slug }}">
    <div class="compito-materia">{{ compito.materia }}</div>
    <hr class="compito-separatore">
    <p class="compito-testo">{{ compito.testo }}</p>
    <div class="compito-scadenza">Questi compiti sono per {{ compito.scadenza }}</div>
    {% if compito.link %}
      <div class="compito-links">
        {% for l in compito.link %}
          <a class="compito-link" href="{{ l.url }}" target="_blank">{{ l.testo }} →</a>
        {% endfor %}
      </div>
    {% endif %}
  </li>
{% endfor %}
</ul>

<a href="javascript:history.back()" class="btn-torna">← Torna indietro</a>
