<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=yes">
  <title>Minecraft Mod Platform | Next-Gen Modding</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #0B0E14;
      color: #EFF3F8;
      line-height: 1.5;
      overflow-x: hidden;
    }

    .glass-panel {
      background: rgba(18, 22, 32, 0.75);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(66, 80, 102, 0.3);
      border-radius: 28px;
    }

    .card {
      background: rgba(22, 28, 40, 0.9);
      backdrop-filter: blur(2px);
      border-radius: 24px;
      border: 1px solid rgba(255, 255, 255, 0.05);
      transition: transform 0.2s ease, box-shadow 0.2s;
      overflow: hidden;
    }

    .card:hover {
      transform: translateY(-4px);
      box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.5);
      border-color: rgba(99, 102, 241, 0.4);
    }

    button, .btn {
      cursor: pointer;
      transition: all 0.2s ease;
      font-weight: 500;
    }

    ::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #1E2432;
    }
    ::-webkit-scrollbar-thumb {
      background: #3B4254;
      border-radius: 10px;
    }

    .container {
      max-width: 1600px;
      margin: 0 auto;
      padding: 0 24px;
    }

    .header {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(11, 14, 20, 0.9);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid rgba(66, 80, 102, 0.4);
      padding: 12px 0;
    }

    .header-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
      flex-wrap: wrap;
    }

    .search-area {
      flex: 2;
      min-width: 200px;
      position: relative;
    }

    .search-wrapper {
      display: flex;
      align-items: center;
      background: #1A1F2C;
      border-radius: 48px;
      padding: 8px 16px;
      border: 1px solid #2D3442;
      transition: all 0.2s;
    }
    .search-wrapper:focus-within {
      border-color: #6C63FF;
      box-shadow: 0 0 0 2px rgba(108, 99, 255, 0.3);
    }
    .search-wrapper i {
      color: #8A94A8;
      margin-right: 12px;
    }
    .search-wrapper input {
      background: transparent;
      border: none;
      color: white;
      font-size: 1rem;
      width: 100%;
      outline: none;
    }
    .search-suggestions {
      position: absolute;
      top: 52px;
      left: 0;
      right: 0;
      background: #1E2436;
      border-radius: 20px;
      backdrop-filter: blur(20px);
      border: 1px solid #2D3442;
      z-index: 200;
      display: none;
    }
    .suggestion-item {
      padding: 10px 16px;
      cursor: pointer;
      transition: background 0.1s;
    }
    .suggestion-item:hover { background: #2A3246; }

    .nav-links {
      display: flex;
      gap: 28px;
      align-items: center;
    }
    .nav-links a {
      color: #D1D8E8;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.2s;
    }
    .nav-links a:hover, .nav-links a.active {
      color: #A78BFA;
    }
    .user-actions {
      display: flex;
      gap: 16px;
      align-items: center;
    }
    .icon-btn {
      background: #1A1F2C;
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 40px;
      color: #CBD5E6;
      font-size: 1.2rem;
      transition: 0.2s;
    }
    .icon-btn:hover { background: #2F374B; color: white; }

    .section-title {
      font-size: 1.8rem;
      font-weight: 700;
      margin: 2rem 0 1.2rem 0;
      letter-spacing: -0.3px;
    }

    .carousel {
      display: flex;
      gap: 20px;
      overflow-x: auto;
      scroll-snap-type: x mandatory;
      padding-bottom: 12px;
    }
    .carousel-card {
      min-width: 280px;
      scroll-snap-align: start;
    }

    .mod-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 24px;
    }
    .mod-list {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }
    .list-card {
      display: flex;
      flex-direction: row;
      align-items: center;
      gap: 20px;
    }

    .badge {
      background: #2D374B;
      border-radius: 40px;
      padding: 4px 12px;
      font-size: 0.7rem;
      font-weight: 600;
    }

    .platform-java { background: #E06C75; color:white; }
    .platform-bedrock { background: #61AFEF; color:white; }

    .filter-bar {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin: 24px 0;
      align-items: center;
    }
    select, .filter-btn {
      background: #1A1F2C;
      border: 1px solid #2D3442;
      border-radius: 40px;
      padding: 8px 18px;
      color: white;
      font-weight: 500;
    }

    .detail-hero {
      background: linear-gradient(135deg, #11161f, #07090e);
      border-radius: 32px;
      padding: 32px;
      margin-bottom: 32px;
    }

    .mobile-menu {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 80%;
      height: 100%;
      background: #0F131C;
      z-index: 1000;
      transform: translateX(-100%);
      transition: 0.3s;
      padding: 32px;
    }
    .mobile-menu.open { transform: translateX(0); }

    @media (max-width: 768px) {
      .nav-links { display: none; }
      .mobile-menu-toggle { display: block; }
      .container { padding: 0 16px; }
      .mod-grid { grid-template-columns: 1fr; }
    }
    .mobile-menu-toggle {
      display: none;
      background: none;
      border: none;
      font-size: 1.8rem;
      color: white;
    }
  </style>
</head>
<body>

<div class="mobile-menu" id="mobileMenu">
  <button id="closeMobileMenu" style="background:none; border:none; color:white; font-size:1.8rem; float:right;">&times;</button>
  <div style="margin-top:60px; display:flex; flex-direction:column; gap:24px;">
    <a href="#" data-nav="home">Home</a>
    <a href="#" data-nav="browse">Browse Mods</a>
    <a href="#" data-nav="admin">Admin Panel</a>
    <a href="#" data-nav="profile">Profile</a>
  </div>
</div>

<header class="header">
  <div class="container header-inner">
    <button class="mobile-menu-toggle" id="menuToggle"><i class="fas fa-bars"></i></button>
    <div class="search-area">
      <div class="search-wrapper">
        <i class="fas fa-search"></i>
        <input type="text" id="globalSearchInput" placeholder="Search mods, authors, versions...">
      </div>
      <div id="searchSuggestions" class="search-suggestions glass-panel"></div>
    </div>
    <div class="nav-links">
      <a href="#" data-nav="home" class="active-nav">Home</a>
      <a href="#" data-nav="browse">Browse</a>
      <a href="#" data-nav="admin">Admin</a>
    </div>
    <div class="user-actions">
      <button class="icon-btn" id="notifBtn"><i class="far fa-bell"></i></button>
      <button class="icon-btn" id="profileBtn"><i class="far fa-user-circle"></i></button>
      <button class="icon-btn" id="settingsBtn"><i class="fas fa-cog"></i></button>
    </div>
  </div>
</header>

<main id="appRoot" class="container"></main>

<script>
  // ---------- MOCK DATABASE ----------
  let mods = [];

  function generateMockMods() {
    const categories = ['Adventure', 'Technology', 'Magic', 'RPG', 'Survival', 'Mobs', 'Weapons', 'Optimization', 'Visuals', 'World Generation', 'Utility'];
    const platforms = ['Java', 'Bedrock', 'Both'];
    const modNames = ['Create', 'Biomes O\' Plenty', 'Tinkers Construct', 'Alex\'s Mobs', 'JEI', 'The Twilight Forest', 'Applied Energistics', 'Mekanism', 'Ice and Fire', 'Immersive Engineering', 'BetterEnd', 'RLCraft Tweaks', 'Supplementaries', 'Traveler's Backpack', 'Ars Nouveau'];
    const authors = ['Simibubi', 'Glitchfiend', 'mDiyo', 'Alexthe666', 'mezz', 'Benimatic', 'AlgorithmX2', 'aidancbrady', 'Raptorfarian', 'BluSunrize', 'paulevs', 'Shivaxi', 'MehVahdJukaar', 'Tiviacz1337', 'BaileyHoll2'];
    for (let i = 0; i < 34; i++) {
      const platform = platforms[Math.floor(Math.random() * platforms.length)];
      const category = categories[Math.floor(Math.random() * categories.length)];
      const downloads = Math.floor(Math.random() * 500000) + 5000;
      const rating = (Math.random() * 2 + 3.5).toFixed(1);
      const lastUpdated = new Date(Date.now() - Math.random() * 30 * 86400000).toISOString().split('T')[0];
      mods.push({
        id: i,
        name: modNames[i % modNames.length] + (i > 14 ? `+ ${Math.floor(i/3)}` : ''),
        description: `An incredible ${category.toLowerCase()} mod that transforms Minecraft experience with unique mechanics.`,
        author: authors[i % authors.length],
        logo: `https://picsum.photos/id/${80 + i}/200/200`,
        screenshots: [`https://picsum.photos/id/${i+10}/800/450`],
        platform: platform,
        supported_versions: platform === 'Java' ? ['1.20.4', '1.21'] : (platform === 'Bedrock' ? ['1.20.60', '1.21.20'] : ['Java 1.21.4', 'Bedrock 1.20.1']),
        downloads: downloads,
        rating: parseFloat(rating),
        tags: [category.toLowerCase()],
        category: category,
        last_updated: lastUpdated,
        changelog: `Improved stability and added new features for version ${platform === 'Java' ? '1.21' : '1.21.20'}.`
      });
    }
    // Add a few both platform examples
    mods.push({id:99, name:"Universal Craft", description:"Cross-platform mod for both editions", author:"CrossTeam", logo:"https://picsum.photos/id/200/200/200", screenshots:["https://picsum.photos/id/101/800/450"], platform:"Both", supported_versions:["Bedrock 1.20.1","Java 1.21.4"], downloads:124000, rating:4.9, tags:["utility","bridge"], category:"Utility", last_updated:"2025-02-01", changelog:"Full compatibility."});
  }
  generateMockMods();

  // ---------- REAL DOWNLOAD SIMULATION ----------
  function downloadModFile(mod) {
    // Choose file extension based on platform
    let extension = '.jar';
    let mimeType = 'application/java-archive';
    if (mod.platform === 'Bedrock') {
      extension = '.mcaddon';
      mimeType = 'application/octet-stream';
    } else if (mod.platform === 'Both') {
      extension = '.zip';
      mimeType = 'application/zip';
    }
    
    const fileName = `${mod.name.replace(/[^a-z0-9]/gi, '_')}_v${mod.supported_versions[0]}${extension}`;
    
    // Create fake mod content (metadata + placeholder)
    const content = `# ${mod.name} by ${mod.author}
Platform: ${mod.platform}
Supported versions: ${mod.supported_versions.join(', ')}
Category: ${mod.category}
Downloads: ${mod.downloads + 1}
Description: ${mod.description}
--- This is a simulated mod file for demonstration purposes ---
In a real environment, this would be the actual mod binary.
`;
    const blob = new Blob([content], { type: mimeType });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = fileName;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
    
    // increment download counter
    mod.downloads++;
    // update UI if needed
    refreshCurrentView();
  }

  // state
  let currentView = 'home';
  let currentModDetailId = null;
  let browseFilter = { platform: 'all', category: 'all', sort: 'trending', searchQuery: '' };
  let browseDisplayMode = 'grid';
  let browseInfiniteOffset = 0;
  let browseAllFiltered = [];
  let homeInfiniteOffset = 0;
  let favoriteMods = JSON.parse(localStorage.getItem('favorites') || '[]');
  let searchHistory = JSON.parse(localStorage.getItem('searchHistory') || '[]');

  function renderStars(rating) { let full = Math.floor(rating); let half = rating % 1 >= 0.5; let stars=''; for(let i=0;i<5;i++) { if(i<full) stars+='<i class="fas fa-star" style="color:#FFB83B;"></i>'; else if(i===full && half) stars+='<i class="fas fa-star-half-alt" style="color:#FFB83B;"></i>'; else stars+='<i class="far fa-star" style="color:#5F6A7A;"></i>'; } return stars; }

  function modCardHTML(mod, isList = false) {
    const platformClass = mod.platform === 'Java' ? 'platform-java' : (mod.platform === 'Bedrock' ? 'platform-bedrock' : 'badge');
    const versionDisplay = Array.isArray(mod.supported_versions) ? mod.supported_versions.slice(0,2).join(', ') : mod.supported_versions;
    const isFav = favoriteMods.includes(mod.id);
    return `
      <div class="card ${isList ? 'list-card' : ''}" data-mod-id="${mod.id}" style="${isList ? 'display:flex; flex-direction:row; padding:16px;' : 'padding:0 0 16px 0'}">
        <img src="${mod.logo}" alt="${mod.name}" style="width:${isList ? '80px' : '100%'}; height:${isList ? '80px' : '180px'}; object-fit:cover; ${isList ? 'border-radius:16px;' : ''}">
        <div style="flex:1; padding:${isList ? '0' : '16px'}">
          <div style="display:flex; justify-content:space-between; align-items:start;"><h3 style="font-size:1.2rem;">${mod.name}</h3><button class="fav-btn" data-id="${mod.id}" style="background:none; border:none; color:${isFav ? '#F97316' : '#7C879E'}"><i class="fas fa-heart"></i></button></div>
          <div style="font-size:0.8rem; color:#A0AEC0;">by ${mod.author}</div>
          <p style="margin:8px 0; font-size:0.85rem; display:-webkit-box; -webkit-line-clamp:2; -webkit-box-orient:vertical; overflow:hidden;">${mod.description}</p>
          <div style="display:flex; flex-wrap:wrap; gap:6px; margin:8px 0"><span class="badge ${platformClass}">${mod.platform}</span><span class="badge">${mod.category}</span><span class="badge">${versionDisplay}</span></div>
          <div style="display:flex; justify-content:space-between; align-items:center; margin-top:8px;"><div style="display:flex; gap:12px;"><span><i class="fas fa-download"></i> ${mod.downloads.toLocaleString()}</span><span>${renderStars(mod.rating)}</span><span><i class="far fa-calendar-alt"></i> ${mod.last_updated}</span></div><div><button class="quick-download" data-id="${mod.id}" style="background:#2A3246; border:none; border-radius:30px; padding:6px 12px; color:white;"><i class="fas fa-download"></i> Download</button><button class="details-btn" data-id="${mod.id}" style="margin-left:8px; background:#6C63FF; border:none; border-radius:30px; padding:6px 14px; color:white;">Details</button></div></div>
        </div>
      </div>
    `;
  }

  function renderModsToContainer(containerId, modsArray, isListMode = false) {
    const container = document.getElementById(containerId);
    if (!container) return;
    container.innerHTML = modsArray.map(m => modCardHTML(m, isListMode)).join('');
    attachCardEvents();
  }

  function attachCardEvents() {
    document.querySelectorAll('.quick-download').forEach(btn => {
      btn.removeEventListener('click', quickDownloadHandler);
      btn.addEventListener('click', quickDownloadHandler);
    });
    document.querySelectorAll('.details-btn').forEach(btn => {
      btn.removeEventListener('click', detailsHandler);
      btn.addEventListener('click', detailsHandler);
    });
    document.querySelectorAll('.fav-btn').forEach(btn => {
      btn.removeEventListener('click', favHandler);
      btn.addEventListener('click', favHandler);
    });
  }
  
  function quickDownloadHandler(e) { 
    e.stopPropagation(); 
    const id = parseInt(e.currentTarget.dataset.id); 
    const mod = mods.find(m => m.id === id); 
    if(mod){ 
      downloadModFile(mod);
      refreshCurrentView(); 
    } 
  }
  
  function detailsHandler(e) { 
    const id = parseInt(e.currentTarget.dataset.id); 
    showModDetail(id); 
  }
  
  function favHandler(e) { 
    const id = parseInt(e.currentTarget.dataset.id); 
    if(favoriteMods.includes(id)) favoriteMods = favoriteMods.filter(f => f !== id); 
    else favoriteMods.push(id); 
    localStorage.setItem('favorites', JSON.stringify(favoriteMods)); 
    refreshCurrentView(); 
  }

  function refreshCurrentView() { renderCurrentView(); }

  // Browse & infinite scroll logic
  function applyBrowseFilters() {
    let filtered = [...mods];
    if (browseFilter.platform !== 'all') filtered = filtered.filter(m => m.platform === browseFilter.platform || (browseFilter.platform === 'Both' && m.platform === 'Both'));
    if (browseFilter.category !== 'all') filtered = filtered.filter(m => m.category === browseFilter.category);
    if (browseFilter.searchQuery) {
      const q = browseFilter.searchQuery.toLowerCase();
      filtered = filtered.filter(m => m.name.toLowerCase().includes(q) || m.author.toLowerCase().includes(q) || m.description.toLowerCase().includes(q) || m.tags.some(t => t.toLowerCase().includes(q)));
    }
    if (browseFilter.sort === 'downloads') filtered.sort((a,b)=>b.downloads - a.downloads);
    else if (browseFilter.sort === 'rating') filtered.sort((a,b)=>b.rating - a.rating);
    else if (browseFilter.sort === 'newest') filtered.sort((a,b)=>new Date(b.last_updated) - new Date(a.last_updated));
    else filtered.sort((a,b)=>b.downloads - a.downloads);
    browseAllFiltered = filtered;
    browseInfiniteOffset = 0;
    renderBrowseInfinite();
  }
  function renderBrowseInfinite() {
    const container = document.getElementById('browseModsContainer');
    if (!container) return;
    const nextBatch = browseAllFiltered.slice(browseInfiniteOffset, browseInfiniteOffset + 12);
    if (browseInfiniteOffset === 0) container.innerHTML = '';
    container.innerHTML += nextBatch.map(m => modCardHTML(m, browseDisplayMode === 'list')).join('');
    attachCardEvents();
    browseInfiniteOffset += 12;
  }
  function handleBrowseScroll() {
    const browseSection = document.getElementById('browseView');
    if (!browseSection || currentView !== 'browse') return;
    const nearBottom = window.innerHeight + window.scrollY >= document.body.offsetHeight - 600;
    if (nearBottom && browseInfiniteOffset < browseAllFiltered.length) renderBrowseInfinite();
  }

  // Home infinite feed
  let homeFeedMods = [];
  function initHomeFeed() { homeFeedMods = [...mods].sort((a,b)=>new Date(b.last_updated) - new Date(a.last_updated)); homeInfiniteOffset = 0; renderHomeFeed(); }
  function renderHomeFeed() {
    const feedContainer = document.getElementById('infiniteFeedContainer');
    if(!feedContainer) return;
    const next = homeFeedMods.slice(homeInfiniteOffset, homeInfiniteOffset+8);
    feedContainer.innerHTML += next.map(m => modCardHTML(m, false)).join('');
    attachCardEvents();
    homeInfiniteOffset+=8;
  }
  function onHomeScroll() {
    if(currentView !== 'home') return;
    if((window.innerHeight + window.scrollY) >= document.body.offsetHeight - 500 && homeInfiniteOffset < homeFeedMods.length) renderHomeFeed();
  }

  function renderHomeView() {
    const trending = [...mods].sort((a,b)=>b.downloads - a.downloads).slice(0,8);
    const popular = [...mods].sort((a,b)=>b.rating - a.rating).slice(0,6);
    const recents = [...mods].sort((a,b)=>new Date(b.last_updated)-new Date(a.last_updated)).slice(0,6);
    const featured = [...mods].slice(0,4);
    return `
      <div>
        <div class="section-title"><i class="fas fa-star"></i> Featured Mods</div>
        <div class="carousel">${featured.map(m => `<div class="carousel-card card" style="padding:12px;">${modCardHTML(m, false)}</div>`).join('')}</div>
        <div class="section-title"><i class="fas fa-fire"></i> Trending Mods</div>
        <div class="carousel">${trending.map(m => `<div class="carousel-card card" style="padding:12px;">${modCardHTML(m, false)}</div>`).join('')}</div>
        <div class="section-title"><i class="fas fa-chart-line"></i> Popular Add-ons</div>
        <div class="mod-grid" id="popularGrid">${popular.map(m => modCardHTML(m, false)).join('')}</div>
        <div class="section-title"><i class="fas fa-sync-alt"></i> Recently Updated</div>
        <div class="mod-grid" id="recentGrid">${recents.map(m => modCardHTML(m, false)).join('')}</div>
        <div class="section-title"><i class="fas fa-thumbs-up"></i> Recommended for You</div>
        <div class="mod-grid" id="recommendedGrid">${featured.slice(2).map(m => modCardHTML(m, false)).join('')}</div>
        <div class="section-title"><i class="fas fa-infinity"></i> Infinite Feed · Latest Mods</div>
        <div id="infiniteFeedContainer" class="mod-grid"></div>
      </div>
    `;
  }

  function renderBrowseView() {
    const categories = ['all', ...new Set(mods.map(m=>m.category))];
    return `
      <div style="margin:24px 0;"><div class="filter-bar"><select id="platformFilter"><option value="all">All Platforms</option><option value="Java">Java</option><option value="Bedrock">Bedrock</option><option value="Both">Both</option></select>
      <select id="categoryFilter">${categories.map(c=>`<option value="${c}">${c.charAt(0).toUpperCase()+c.slice(1)}</option>`).join('')}</select>
      <select id="sortSelect"><option value="trending">Trending</option><option value="downloads">Most Downloaded</option><option value="rating">Highest Rated</option><option value="newest">Newest</option></select>
      <button id="gridViewBtn" class="filter-btn"><i class="fas fa-th"></i> Grid</button><button id="listViewBtn" class="filter-btn"><i class="fas fa-list"></i> List</button></div></div>
      <div id="browseModsContainer" class="${browseDisplayMode === 'grid' ? 'mod-grid' : 'mod-list'}"></div>
    `;
  }

  function showModDetail(id) {
    const mod = mods.find(m => m.id == id);
    if(!mod) return;
    currentModDetailId = id;
    currentView = 'detail';
    renderDetailView(mod);
  }
  
  function renderDetailView(mod) {
    const html = `<div><button id="backToBrowseBtn" style="margin:20px 0; background:#2D374B; border:none; padding:10px 20px; border-radius:40px;"><i class="fas fa-arrow-left"></i> Back</button>
    <div class="detail-hero"><img src="${mod.screenshots[0]}" style="width:100%; border-radius:24px; max-height:350px; object-fit:cover;"><div style="margin-top:20px;"><h1>${mod.name}</h1><p>by ${mod.author}</p><div>${renderStars(mod.rating)}</div><p>${mod.description}</p><div class="badge">${mod.platform}</div><div>Supported: ${mod.supported_versions.join(', ')}</div><div>Downloads: ${mod.downloads.toLocaleString()}</div><div>Changelog: ${mod.changelog}</div><button id="downloadNowBtn" class="filter-btn" style="margin-top:16px; background:#6C63FF;"><i class="fas fa-download"></i> Download ${mod.name}</button></div></div>
    <div class="glass-panel" style="padding:24px"><h3>Gallery</h3><div class="carousel">${mod.screenshots.map(s=>`<img src="${s}" style="width:260px; border-radius:16px;">`).join('')}</div></div>
    <div class="glass-panel" style="padding:24px; margin-top:20px;"><h3>Installation Guide</h3><p>1. Download the mod file. 2. Place in mods folder. 3. Enjoy!</p><h3>Comments & Ratings</h3><textarea placeholder="Write a comment..." rows="2" style="width:100%; background:#1A1F2C; border:none; border-radius:16px; padding:12px; color:white;"></textarea><button style="margin-top:10px;">Post Comment</button></div></div>`;
    document.getElementById('appRoot').innerHTML = html;
    document.getElementById('backToBrowseBtn')?.addEventListener('click',()=>{ currentView='browse'; renderCurrentView(); });
    document.getElementById('downloadNowBtn')?.addEventListener('click',()=>{ downloadModFile(mod); renderDetailView(mod); });
  }

  function renderAdminPanel() {
    return `<div style="display:flex; gap:24px; flex-wrap:wrap;"><div class="glass-panel" style="flex:2; padding:24px;"><h2>➕ Add New Mod</h2><input id="adminName" placeholder="Mod Name" style="width:100%;margin:8px 0; padding:12px; background:#1A1F2C; border:none; border-radius:20px;"><input id="adminAuthor" placeholder="Author"><textarea id="adminDesc" placeholder="Description"></textarea><input id="adminLogoUrl" placeholder="Logo URL"><input id="adminScreenshots" placeholder="Screenshot URLs (comma)"><select id="adminPlatform"><option>Java</option><option>Bedrock</option><option>Both</option></select><input id="adminVersions" placeholder="Supported versions (comma)"><select id="adminCategory">${[...new Set(mods.map(m=>m.category))].map(c=>`<option>${c}</option>`).join('')}</select><button id="submitAddMod" class="filter-btn">Create Mod</button><h3 style="margin-top:24px;">🗑️ Delete / Edit Mod</h3><div id="adminModList">${mods.slice(0,12).map(m=>`<div style="display:flex; justify-content:space-between;"><span>${m.name}</span><div><button class="editModBtn" data-id="${m.id}">Edit</button><button class="deleteModBtn" data-id="${m.id}">Delete</button></div></div>`).join('')}</div></div><div class="glass-panel" style="flex:1; padding:24px;"><h3>📂 Category Manager</h3><input id="newCategory" placeholder="New Category"><button id="addCategoryBtn">Add</button><ul id="categoryList">${[...new Set(mods.map(m=>m.category))].map(c=>`<li>${c} <button class="delCatBtn" data-cat="${c}">❌</button></li>`).join('')}</ul></div></div>`;
  }
  
  function initAdminEvents() {
    document.getElementById('submitAddMod')?.addEventListener('click',()=>{
      const name = document.getElementById('adminName').value, author = document.getElementById('adminAuthor').value, desc = document.getElementById('adminDesc').value, logo = document.getElementById('adminLogoUrl').value, screensRaw = document.getElementById('adminScreenshots').value, platform = document.getElementById('adminPlatform').value, versions = document.getElementById('adminVersions').value.split(','), category = document.getElementById('adminCategory').value;
      if(!name) return alert('Enter name');
      const newMod = { id: Date.now(), name, author, description: desc, logo: logo || 'https://picsum.photos/200/200', screenshots: screensRaw? screensRaw.split(','): ['https://picsum.photos/800/450'], platform, supported_versions: versions, downloads:0, rating:5, tags:[category.toLowerCase()], category, last_updated: new Date().toISOString().split('T')[0], changelog:"Initial release" };
      mods.push(newMod);
      alert('Mod added!');
      renderCurrentView();
    });
    document.querySelectorAll('.deleteModBtn').forEach(btn=>btn.addEventListener('click',(e)=>{const id=parseInt(btn.dataset.id); mods = mods.filter(m=>m.id!==id); renderCurrentView();}));
    document.querySelectorAll('.editModBtn').forEach(btn=>btn.addEventListener('click',(e)=>{alert('Edit feature: implement extended, for demo edit manually in console');}));
    document.getElementById('addCategoryBtn')?.addEventListener('click',()=>{const nc = document.getElementById('newCategory').value; if(nc && !mods.some(m=>m.category===nc)){ alert('Category concept added, use in new mods'); } renderCurrentView();});
  }
  
  function renderCurrentView() {
    if(currentView === 'home') { document.getElementById('appRoot').innerHTML = renderHomeView(); initHomeFeed(); attachCardEvents(); window.addEventListener('scroll', onHomeScroll); }
    else if(currentView === 'browse') { document.getElementById('appRoot').innerHTML = renderBrowseView(); applyBrowseFilters(); attachBrowseEvents(); window.addEventListener('scroll', handleBrowseScroll); }
    else if(currentView === 'detail') { showModDetail(currentModDetailId); }
    else if(currentView === 'admin') { document.getElementById('appRoot').innerHTML = renderAdminPanel(); initAdminEvents(); }
    if(currentView !== 'browse') window.removeEventListener('scroll', handleBrowseScroll);
    if(currentView !== 'home') window.removeEventListener('scroll', onHomeScroll);
  }
  
  function attachBrowseEvents() {
    document.getElementById('platformFilter')?.addEventListener('change',e=>{browseFilter.platform=e.target.value; applyBrowseFilters();});
    document.getElementById('categoryFilter')?.addEventListener('change',e=>{browseFilter.category=e.target.value; applyBrowseFilters();});
    document.getElementById('sortSelect')?.addEventListener('change',e=>{browseFilter.sort=e.target.value; applyBrowseFilters();});
    document.getElementById('gridViewBtn')?.addEventListener('click',()=>{browseDisplayMode='grid'; applyBrowseFilters();});
    document.getElementById('listViewBtn')?.addEventListener('click',()=>{browseDisplayMode='list'; applyBrowseFilters();});
  }

  const searchInput = document.getElementById('globalSearchInput');
  const suggestionsDiv = document.getElementById('searchSuggestions');
  searchInput?.addEventListener('input',()=>{
    const val = searchInput.value.toLowerCase();
    if(val.length<2) { suggestionsDiv.style.display='none'; return; }
    const matches = mods.filter(m=>m.name.toLowerCase().includes(val)||m.author.toLowerCase().includes(val)).slice(0,5);
    suggestionsDiv.innerHTML = matches.map(m=>`<div class="suggestion-item" data-sug="${m.name}">${m.name} by ${m.author}</div>`).join('');
    suggestionsDiv.style.display='block';
    document.querySelectorAll('.suggestion-item').forEach(el=>el.addEventListener('click',()=>{ searchInput.value=el.innerText.split(' by')[0]; browseFilter.searchQuery=searchInput.value; currentView='browse'; renderCurrentView(); suggestionsDiv.style.display='none'; }));
  });
  searchInput?.addEventListener('keypress',e=>{ if(e.key==='Enter'){ browseFilter.searchQuery=searchInput.value; currentView='browse'; renderCurrentView(); suggestionsDiv.style.display='none'; } });

  document.querySelectorAll('[data-nav]').forEach(link=>{ link.addEventListener('click',(e)=>{ e.preventDefault(); const view = link.dataset.nav; if(view==='home') currentView='home'; else if(view==='browse') currentView='browse'; else if(view==='admin') currentView='admin'; else if(view==='profile') alert('User profile (favorites:'+favoriteMods.length+') \nDownload history in console'); renderCurrentView(); }); });
  document.getElementById('menuToggle')?.addEventListener('click',()=>document.getElementById('mobileMenu').classList.add('open'));
  document.getElementById('closeMobileMenu')?.addEventListener('click',()=>document.getElementById('mobileMenu').classList.remove('open'));
  document.getElementById('notifBtn')?.addEventListener('click',()=>alert('🔔 New updates from followed creators!'));
  document.getElementById('profileBtn')?.addEventListener('click',()=>alert(`👤 Favorites: ${favoriteMods.length} mods\nFollowed creators: modding legends`));
  renderCurrentView();
</script>
</body>
</html>
