---
layout: default
title: The Lounge Archive
permalink: /reviews/
---

# The Lounge Archive
Explore my professional tasting notes.

<div class="search-container">
  <input type="text" id="search-input" placeholder="Search by brand, wrapper, flavor (e.g., 'Chocolate'), or location..." style="width: 100%; padding: 12px; font-size: 1.1rem; border: 1px solid #ccc; border-radius: 4px;">
  <ul id="results-container" style="list-style: none; padding: 20px 0;"></ul>
</div>

<script src="https://unpkg.com/simple-jekyll-search@latest/dest/simple-jekyll-search.min.js"></script>

<script>
  SimpleJekyllSearch({
    searchInput: document.getElementById('search-input'),
    resultsContainer: document.getElementById('results-container'),
    json: '{{ "/search.json" | relative_url }}',
    searchResultTemplate: '<li style="margin-bottom: 25px;"><a href="{url}" style="font-size: 1.4rem; font-weight: bold; color: #d35400; text-decoration: none;">{brand} {title}</a><br><small style="color: #666;">{strength} | {wrapper} | {place}</small><br><em style="font-size: 0.9rem;">Notes: {tags}</em></li>',
    noResultsText: 'No sticks found. Try searching for a different flavor or brand.',
    limit: 10,
    fuzzy: true
  });
</script>