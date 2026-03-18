---
title: Dispense di storia
layout: page
---

<div class="dispensa-controlli">
  <button class="font-btn" id="btn-recenti" onclick="ordinaPer('recenti')">Più recenti</button>
  <button class="font-btn" id="btn-alfa" onclick="ordinaPer('alfabetico')">A–Z</button>
</div>

<ul class="dispensa-lista" id="dispensa-lista">
{% assign appunti = site.data.storia | reverse %}
{% for appunto in appunti %}
  <li class="dispensa-card colore-classe" data-titolo="{{ appunto.titolo | downcase }}" data-indice="{{ forloop.index }}">
    <div class="dispensa-titolo">{{ appunto.titolo }}</div>
    <p class="dispensa-descrizione">{{ appunto.descrizione }}</p>
{% if appunto.link %}
  {% for link in appunto.link %}
    <a class="dispensa-link" href="{{ link.url }}" aria-label="Apri la pagina: {{ link.testo }}">{{ link.testo }} →</a>
  {% endfor %}
{% endif %}
  </li>
{% endfor %}
</ul>

<a href="javascript:history.back()" class="btn-torna">← Torna indietro</a>

<style>
.dispensa-controlli {
  display: flex;
  gap: 10px;
  margin: 1rem 0 1.5rem;
}
.dispensa-lista {
  list-style: none;
  padding: 0;
  margin: 0;
}
.dispensa-card {
  border-left: 5px solid;
  border-radius: 6px;
  background: #fff;
  padding: 1rem 1.2rem;
  margin-bottom: 1.1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
.dispensa-titolo {
  font-weight: bold;
  font-size: 1rem;
  margin-bottom: 0.4rem;
}
.dispensa-descrizione {
  font-size: 0.95rem;
  margin: 0.3rem 0 0.6rem;
  line-height: 1.5;
}
.dispensa-link {
  display: inline-block;
  padding: 6px 14px;
  border-radius: 5px;
  background: #f0f0f0;
  color: #2d2d2d;
  text-decoration: none;
  font-size: 0.9rem;
}
.dispensa-link:hover {
  background: #e0e0e0;
}
</style>

<script>
function ordinaPer(criterio) {
  const lista = document.getElementById('dispensa-lista');
  const cards = Array.from(lista.querySelectorAll('.dispensa-card'));
  if (criterio === 'alfabetico') {
    cards.sort((a, b) => a.dataset.titolo.localeCompare(b.dataset.titolo, 'it'));
  } else {
    cards.sort((a, b) => parseInt(a.dataset.indice) - parseInt(b.dataset.indice));
  }
  cards.forEach(c => lista.appendChild(c));
}
</script>
