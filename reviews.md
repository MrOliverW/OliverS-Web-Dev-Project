---
layout: default
title: The Lounge Archive
permalink: /reviews/
---

# The Lounge Archive

<div class="filter-bar" style="background: #f4f1ea; padding: 20px; border-radius: 8px; margin-bottom: 30px; display: flex; flex-wrap: wrap; gap: 15px;">
  
  <div style="flex: 1; min-width: 250px;">
    <label style="display:block; font-weight:bold; margin-bottom:5px;">Search Notes</label>
    <input type="text" id="textSearch" placeholder="Try 'Chocolate', 'Alki', or 'Cedar'..." style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px;">
  </div>

  <div>
    <label style="display:block; font-weight:bold; margin-bottom:5px;">Brand</label>
    <select id="brandFilter" style="padding: 10px; border-radius: 4px; border: 1px solid #ccc;">
      <option value="all">All Brands</option>
      {% assign brands = site.reviews | map: 'brand' | uniq %}
      {% for brand in brands %}<option value="{{ brand }}">{{ brand }}</option>{% endfor %}
    </select>
  </div>

  <div>
    <label style="display:block; font-weight:bold; margin-bottom:5px;">Strength</label>
    <select id="strengthFilter" style="padding: 10px; border-radius: 4px; border: 1px solid #ccc;">
      <option value="all">All Strengths</option>
      {% assign strengths = site.reviews | map: 'strength' | uniq %}
      {% for strength in strengths %}<option value="{{ strength }}">{{ strength }}</option>{% endfor %}
    </select>
  </div>
</div>

<div id="reviews-list">
  {% for review in site.reviews %}
  <div class="review-card" 
       data-brand="{{ review.brand }}" 
       data-strength="{{ review.strength }}" 
       data-content="{{ review.brand }} {{ review.title }} {{ review.tags | join: ' ' }} {{ review.wrapper }} {{ review.place_smoked }}"
       style="border-bottom: 1px solid #eee; padding: 20px 0; display: block;">
    
    <a href="{{ review.url | relative_url }}" style="font-size: 1.5rem; font-weight: bold; color: #d35400; text-decoration: none;">
      {{ review.brand }} {{ review.title }}
    </a>
    <div style="margin: 8px 0; color: #666;">
      <strong>{{ review.strength }}</strong> | {{ review.wrapper }} | <em>{{ review.place_smoked }}</em>
    </div>
    <p style="font-size: 0.95rem; color: #444;">{{ review.content | strip_html | truncatewords: 25 }}</p>
  </div>
  {% endfor %}
</div>

<script>
const textInput = document.getElementById('textSearch');
const brandSelect = document.getElementById('brandFilter');
const strengthSelect = document.getElementById('strengthFilter');
const cards = document.querySelectorAll('.review-card');

function filterReviews() {
  const textQuery = textInput.value.toLowerCase();
  const brandQuery = brandSelect.value;
  const strengthQuery = strengthSelect.value;

  cards.forEach(card => {
    const content = card.getAttribute('data-content').toLowerCase();
    const brand = card.getAttribute('data-brand');
    const strength = card.getAttribute('data-strength');

    const matchesText = content.includes(textQuery);
    const matchesBrand = (brandQuery === 'all' || brand === brandQuery);
    const matchesStrength = (strengthQuery === 'all' || strength === strengthQuery);

    if (matchesText && matchesBrand && matchesStrength) {
      card.style.display = 'block';
    } else {
      card.style.display = 'none';
    }
  });
}

// Listen for any changes
textInput.addEventListener('input', filterReviews);
brandSelect.addEventListener('change', filterReviews);
strengthSelect.addEventListener('change', filterReviews);
</script>