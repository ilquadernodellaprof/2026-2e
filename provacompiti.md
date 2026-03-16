---
title: Ultimi compiti assegnati
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
  margin-bottom: 0.35rem;
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

/* Colori per materia */
.materia-italiano  { border-left-color: #7a3b55; }
.materia-italiano .compito-materia { color: #7a3b55; }

.materia-storia    { border-left-color: #c8651a; }
.materia-storia .compito-materia { color: #c8651a; }

.materia-geografia { border-left-color: #6aab2e; }
.materia-geografia .compito-materia { color: #6aab2e; }
</style>

<ul class="compiti-lista">
{% for compito in site.data.compiti %}
  {% assign slug = compito.materia | downcase %}
  <li class="compito-card materia-{{ slug }}">
    <div class="compito-materia">{{ compito.materia }}</div>
    <p class="compito-testo">{{ compito.testo }}</p>
    <div class="compito-scadenza">Scadenza: {{ compito.scadenza }}</div>
    {% if compito.link %}
      <a class="compito-link" href="{{ compito.link }}" target="_blank">Apri il materiale →</a>
    {% endif %}
  </li>
{% endfor %}
</ul>

<a href="javascript:history.back()" class="btn-torna">← Torna indietro</a>
