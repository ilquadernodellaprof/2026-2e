---
title: Laboratorio di lettura
layout: page
---

<div class="lettura-controlli">
  <button class="font-btn" id="btn-recenti" onclick="ordinaPer('recenti')">Più recenti</button>
  <button class="font-btn" id="btn-alfa" onclick="ordinaPer('alfabetico')">A–Z</button>
</div>

<ul class="lettura-lista" id="lettura-lista">
{% assign appunti = site.data.lettura | reverse %}
{% for appunto in appunti %}
  <li class="lettura-card colore-classe" data-titolo="{{ appunto.titolo | downcase }}" data-indice="{{ forloop.index }}">
    <div class="lettura-titolo">{{ appunto.titolo }}</div>
    <p class="lettura-descrizione">{{ appunto.descrizione }}</p>
{% if appunto.link %}
  <a class="lettura-link" href="{{ appunto.link }}" aria-label="Apri la pagina: {{ appunto.titolo }}">Apri la pagina →</a>
{% endif %}
  </li>
{% endfor %}
</ul>

<a href="javascript:history.back()" class="btn-torna">← Torna indietro</a>

<style>
.lettura-controlli {
  display: flex;
  gap: 10px;
  margin: 1rem 0 1.5rem;
}
.lettura-lista {
  list-style: none;
  padding: 0;
  margin: 0;
}
.lettura-card {
  border-left: 5px solid;
  border-radius: 6px;
  background: #fff;
  padding: 1rem 1.2rem;
  margin-bottom: 1.1rem;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
}
.lettura-titolo {
  font-weight: bold;
  font-size: 1rem;
  margin-bottom: 0.4rem;
}
.lettura-descrizione {
  font-size: 0.95rem;
  margin: 0.3rem 0 0.6rem;
  line-height: 1.5;
}
.lettura-link {
  display: inline-block;
  padding: 6px 14px;
  border-radius: 5px;
  background: #f0f0f0;
  color: #2d2d2d;
  text-decoration: none;
  font-size: 0.9rem;
}
.lettura-link:hover {
  background: #e0e0e0;
}
</style>

<script>
function ordinaPer(criterio) {
  const lista = document.getElementById('lettura-lista');
  const cards = Array.from(lista.querySelectorAll('.lettura-card'));
  if (criterio === 'alfabetico') {
    cards.sort((a, b) => a.dataset.titolo.localeCompare(b.dataset.titolo, 'it'));
  } else {
    cards.sort((a, b) => parseInt(a.dataset.indice) - parseInt(b.dataset.indice));
  }
  cards.forEach(c => lista.appendChild(c));
}
</script>
