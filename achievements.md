---
layout: default
title: Achievements
permalink: /achievements/
---

# achievements

movie-club badges you can earn by using **suckling**. anything about watching movies uses returned rb9 rentals as the record, so `/return` is how those badges count.

macguffin sets have achievement titles too. collect every card in a set and the matching badge unlocks.

you can unlock as many as you want, then pin up to **3** as visible discord badge roles with `/achievementdisplay`.

<div class="catalog-toolbar" aria-label="achievement catalog tools">
  <label class="catalog-search">
    <span>search achievements</span>
    <input id="achievement-search" type="search" placeholder="try director, rental, macguffin..." autocomplete="off">
  </label>
  <div class="catalog-count" id="achievement-count">loading achievements...</div>
</div>

<div class="category-pills" id="achievement-categories" aria-label="achievement categories"></div>

<div class="achievement-catalog" id="achievement-catalog"></div>

<script src="https://cdn.jsdelivr.net/npm/twemoji@14.0.2/dist/twemoji.min.js" crossorigin="anonymous"></script>
<script>
(() => {
  const catalog = document.getElementById("achievement-catalog");
  const count = document.getElementById("achievement-count");
  const search = document.getElementById("achievement-search");
  const categories = document.getElementById("achievement-categories");
  const categoryOrder = ["rentals", "rb9 library", "reviews", "macguffins", "games", "discovery", "letterboxd"];
  let achievements = [];
  let activeCategory = "all";

  const normalize = (value) => (value || "").toString().toLowerCase();
  const escapeHtml = (value) => (value || "").toString().replace(/[&<>"']/g, (char) => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#39;"
  })[char]);
  const labelFor = (category) => category === "all" ? "all" : category;

  function grouped(items) {
    const byCategory = new Map();
    for (const item of items) {
      const category = item.category || "other";
      if (!byCategory.has(category)) byCategory.set(category, []);
      byCategory.get(category).push(item);
    }
    return byCategory;
  }

  function renderCategories() {
    const available = Array.from(new Set(achievements.map((item) => item.category))).filter(Boolean);
    const ordered = categoryOrder.filter((category) => available.includes(category));
    for (const category of available.sort()) {
      if (!ordered.includes(category)) ordered.push(category);
    }
    categories.innerHTML = ["all", ...ordered].map((category) => (
      `<button type="button" class="category-pill" data-category="${escapeHtml(category)}" aria-pressed="${category === activeCategory}">
        ${escapeHtml(labelFor(category))}
      </button>`
    )).join("");
  }

  function achievementCard(item) {
    return `
      <article class="achievement-card">
        <div class="achievement-card__icon" aria-hidden="true">${escapeHtml(item.emoji || "\u{1F3C6}")}</div>
        <div>
          <h3>${escapeHtml(item.title_name || item.name)}</h3>
          <p>${escapeHtml(item.hint || item.description)}</p>
        </div>
      </article>
    `;
  }

  function render() {
    const query = normalize(search.value);
    const filtered = achievements.filter((item) => {
      const inCategory = activeCategory === "all" || item.category === activeCategory;
      const haystack = normalize(`${item.display_name} ${item.title_name} ${item.name} ${item.hint} ${item.description} ${item.category}`);
      return inCategory && (!query || haystack.includes(query));
    });
    const byCategory = grouped(filtered);
    const ordered = categoryOrder.filter((category) => byCategory.has(category));
    for (const category of Array.from(byCategory.keys()).sort()) {
      if (!ordered.includes(category)) ordered.push(category);
    }

    count.textContent = `${filtered.length} of ${achievements.length} achievements`;
    if (!filtered.length) {
      catalog.innerHTML = `<p class="empty-state">no achievements match that search.</p>`;
      return;
    }

    catalog.innerHTML = ordered.map((category) => {
      const items = byCategory.get(category) || [];
      return `
        <section class="achievement-section" id="${category.replace(/\s+/g, "-")}">
          <div class="section-heading">
            <h2>${escapeHtml(category)}</h2>
            <span>${items.length}</span>
          </div>
          <div class="achievement-grid">
            ${items.map(achievementCard).join("")}
          </div>
        </section>
      `;
    }).join("");
    if (window.twemoji) {
      window.twemoji.parse(catalog, {
        folder: "svg",
        ext: ".svg",
      });
    }
  }

  categories.addEventListener("click", (event) => {
    const button = event.target.closest("[data-category]");
    if (!button) return;
    activeCategory = button.dataset.category;
    renderCategories();
    render();
  });
  search.addEventListener("input", render);

  fetch("{{ '/assets/data/achievements.json' | relative_url }}")
    .then((response) => response.json())
    .then((data) => {
      achievements = data.achievements || [];
      renderCategories();
      render();
    })
    .catch(() => {
      count.textContent = "couldn't load achievements";
      catalog.innerHTML = `<p class="empty-state">the achievement catalog did not load. try refreshing in a moment.</p>`;
    });
})();
</script>
