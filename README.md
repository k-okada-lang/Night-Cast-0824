[Uploading index.html…]()
# Night-Cast-0824<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NIGHT CAST | 高級キャバクラ・ラウンジ求人</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@500;700;800&family=Zen+Kaku+Gothic+New:wght@400;500;700;900&family=Cormorant+Garamond:ital,wght@0,500;1,500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="styles.css">
</head>
</head>
<body>

<header class="topbar">
  <div class="brand" onclick="go('home')">
    <span class="mark">NIGHT CAST</span>
    <span class="sub">GINZA · ROPPONGI · SHINJUKU RECRUIT</span>
  </div>
  <div class="nav-actions">
    <a class="btn-ghost" onclick="go('admin')">店舗管理（アドミン）</a>
  </div>
</header>

<main id="view-home" class="active">
  <section class="hero">
    <span class="eyebrow">Cast Recruiting</span>
    <h1>あなたに合う一軒が、<br class="brk"><span class="accent">ここで見つかる。</span></h1>
    <p class="lead">エリア・業態・時給から、今日から働ける優良店を検索。写真とSNSで雰囲気を見てから応募できます。</p>

    <div class="search-panel">
      <div class="search-grid">
        <div class="field">
          <label>キーワード</label>
          <input id="f-keyword" type="text" placeholder="店舗名・エリア・特徴で検索">
        </div>
        <div class="field">
          <label>エリア</label>
          <select id="f-area"><option value="">すべて</option></select>
        </div>
        <div class="field">
          <label>業態</label>
          <select id="f-genre"><option value="">すべて</option></select>
        </div>
        <div class="field" style="align-self:end;">
          <button class="btn-search" onclick="applyFilters()">検索する</button>
        </div>
      </div>
    </div>

    <div class="quick-filters">
      <div class="quick-block">
        <div class="quick-label">業種から探す</div>
        <div class="quick-icons" id="genre-icons"></div>
      </div>
      <div class="quick-block">
        <div class="quick-label">人気エリアから探す</div>
        <div class="quick-icons" id="area-icons"></div>
      </div>
    </div>
  </section>

  <div class="result-meta">
    <h2>掲載店舗 <span class="count" id="result-count">0</span> 件</h2>
    <div class="sort-inline">
      <button class="loc-btn" id="loc-btn" onclick="useMyLocation()">📍 現在地から探す</button>
      並び替え：
      <select id="f-sort" onchange="applyFilters()">
        <option value="new">新着順</option>
        <option value="wage-desc">時給が高い順</option>
        <option value="name">店舗名順</option>
        <option value="distance" id="distance-option" disabled>現在地から近い順</option>
      </select>
    </div>
  </div>

  <div class="grid" id="store-grid"></div>
</main>

<main id="view-detail">
  <div class="detail-wrap" id="detail-content"></div>
</main>

<main id="view-admin">
  <div class="admin-wrap" id="admin-content"></div>
</main>

<footer>NIGHT CAST — 求人情報サイト（デモ） / 掲載内容はアドミン画面から編集できます</footer>
<div class="toast" id="toast"></div>

<script src="script.js"></script>
</body>
</html>
