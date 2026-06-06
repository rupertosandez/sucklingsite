---
layout: default
title: MacGuffins
permalink: /macguffins/
---

# macguffins

collectible movie objects that can drop when members `/return` rentals. every macguffin is unique, so once one is claimed, it is out of the pool.

some macguffins belong to sets. collect every item in a set to unlock that set's achievement title.

<div class="catalog-toolbar" aria-label="macguffin catalog tools">
  <label class="catalog-search">
    <span>search macguffins</span>
    <input id="macguffin-search" type="search" placeholder="try ring, paddy's, iconic..." autocomplete="off">
  </label>
  <div class="catalog-count" id="macguffin-count">loading macguffins...</div>
</div>

<div class="category-pills" id="macguffin-filters" aria-label="macguffin filters"></div>

<div class="macguffin-catalog" id="macguffin-catalog"></div>

<script src="https://cdn.jsdelivr.net/npm/twemoji@14.0.2/dist/twemoji.min.js" crossorigin="anonymous"></script>
<script>
(() => {
  const catalog = document.getElementById("macguffin-catalog");
  const count = document.getElementById("macguffin-count");
  const search = document.getElementById("macguffin-search");
  const filters = document.getElementById("macguffin-filters");
  const rarityOrder = ["iconic", "rare", "common"];
  let macguffins = [];
  let sets = [];
  let activeFilter = "all";

  const normalize = (value) => (value || "").toString().toLowerCase();
  const escapeHtml = (value) => (value || "").toString().replace(/[&<>"']/g, (char) => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#39;"
  })[char]);
  const filterLabel = (filter) => {
    if (filter === "all") return "all";
    if (filter === "no-set") return "no set";
    if (filter.startsWith("rarity:")) return filter.replace("rarity:", "");
    const itemSet = sets.find((set) => `set:${set.id}` === filter);
    return itemSet ? itemSet.label : filter;
  };

  function grouped(items) {
    const byRarity = new Map();
    for (const item of items) {
      const rarity = item.rarity || "other";
      if (!byRarity.has(rarity)) byRarity.set(rarity, []);
      byRarity.get(rarity).push(item);
    }
    return byRarity;
  }

  function renderFilters() {
    const setFilters = sets.map((set) => `set:${set.id}`);
    const allFilters = ["all", ...rarityOrder.map((rarity) => `rarity:${rarity}`), ...setFilters, "no-set"];
    filters.innerHTML = allFilters.map((filter) => (
      `<button type="button" class="category-pill" data-filter="${escapeHtml(filter)}" aria-pressed="${filter === activeFilter}">
        ${escapeHtml(filterLabel(filter))}
      </button>`
    )).join("");
  }

  function setPills(item) {
    if (!item.sets || !item.sets.length) {
      return `<span class="macguffin-set-pill macguffin-set-pill--empty">no set</span>`;
    }
    return item.sets.map((itemSet) => (
      `<span class="macguffin-set-pill">${escapeHtml(itemSet.emoji || "")} ${escapeHtml(itemSet.label)}</span>`
    )).join("");
  }

  function macguffinCard(item) {
    return `
      <article class="achievement-card macguffin-card">
        <div class="achievement-card__icon macguffin-card__icon" aria-hidden="true">${escapeHtml(item.emoji || "\u{1F4E6}")}</div>
        <div>
          <div class="macguffin-card__meta">
            <span class="macguffin-rarity macguffin-rarity--${escapeHtml(item.rarity)}">${escapeHtml(item.rarity)}</span>
          </div>
          <h3>${escapeHtml(item.name)}</h3>
          <p class="macguffin-source">${escapeHtml(item.source)}</p>
          <p>${escapeHtml(item.flavor)}</p>
          <div class="macguffin-card__sets">${setPills(item)}</div>
        </div>
      </article>
    `;
  }

  function matchesFilter(item) {
    if (activeFilter === "all") return true;
    if (activeFilter === "no-set") return !item.sets || !item.sets.length;
    if (activeFilter.startsWith("rarity:")) return item.rarity === activeFilter.replace("rarity:", "");
    if (activeFilter.startsWith("set:")) {
      const setId = activeFilter.replace("set:", "");
      return (item.sets || []).some((itemSet) => itemSet.id === setId);
    }
    return true;
  }

  function render() {
    const query = normalize(search.value);
    const filtered = macguffins.filter((item) => {
      const setText = (item.sets || []).map((itemSet) => `${itemSet.label} ${itemSet.achievement_name}`).join(" ");
      const haystack = normalize(`${item.name} ${item.rarity} ${item.source} ${item.flavor} ${setText}`);
      return matchesFilter(item) && (!query || haystack.includes(query));
    });
    const byRarity = grouped(filtered);
    const ordered = rarityOrder.filter((rarity) => byRarity.has(rarity));
    for (const rarity of Array.from(byRarity.keys()).sort()) {
      if (!ordered.includes(rarity)) ordered.push(rarity);
    }

    count.textContent = `${filtered.length} of ${macguffins.length} macguffins`;
    if (!filtered.length) {
      catalog.innerHTML = `<p class="empty-state">no macguffins match that search.</p>`;
      return;
    }

    catalog.innerHTML = ordered.map((rarity) => {
      const items = byRarity.get(rarity) || [];
      return `
        <section class="achievement-section" id="${escapeHtml(rarity)}">
          <div class="section-heading">
            <h2>${escapeHtml(rarity)}</h2>
            <span>${items.length}</span>
          </div>
          <div class="achievement-grid macguffin-grid">
            ${items.map(macguffinCard).join("")}
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

  filters.addEventListener("click", (event) => {
    const button = event.target.closest("[data-filter]");
    if (!button) return;
    activeFilter = button.dataset.filter;
    renderFilters();
    render();
  });
  search.addEventListener("input", render);

  fetch("{{ '/assets/data/macguffins.json' | relative_url }}")
    .then((response) => response.json())
    .then((data) => {
      macguffins = data.macguffins || [];
      sets = data.sets || [];
      renderFilters();
      render();
    })
    .catch(() => {
      count.textContent = "couldn't load macguffins";
      catalog.innerHTML = `<p class="empty-state">the macguffin catalog did not load. try refreshing in a moment.</p>`;
    });
})();
</script>
