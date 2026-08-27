[Uploading index.html…]()
<!DOCTYPE html>
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

# NIGHT CAST — キャバクラ求人サイト

キャバクラ・クラブ・ラウンジ・スナック・ガールズバーの求人検索サイトです。
検索、業種／人気エリアのアイコン検索、現在地からの距離順検索、店舗詳細（写真・SNSリンク）、店舗情報を編集できる管理（アドミン）画面を備えています。

## ファイル構成

```
.
├── index.html   ページの構造（検索ページ／店舗詳細／アドミン）
├── styles.css   デザイン（配色・タイポグラフィ・レイアウト）
├── script.js    検索・詳細表示・アドミン機能のロジック
└── README.md    このファイル
```

## 使い方（ローカル確認）

`index.html` をブラウザで直接開くだけで動作します。サーバーは不要です。

## GitHub Pages で公開する場合

1. このリポジトリを GitHub にアップロード（push）する
2. リポジトリの **Settings → Pages** を開く
3. **Branch** を `main`（または該当ブランチ）、フォルダを `/ (root)` に設定して **Save**
4. 数分後、`https://ユーザー名.github.io/リポジトリ名/` で公開されます

## 主な機能

- **検索**：キーワード／エリア／業種で絞り込み、時給・新着・店名で並び替え
- **業種アイコン検索**：キャバクラ／クラブ／ラウンジ／スナック／ガールズバーをタップで絞り込み
- **人気エリアアイコン検索**：銀座・六本木・渋谷・新宿・西麻布・池袋・新橋をタップで絞り込み
- **現在地から探す**：ブラウザの位置情報を使って現在地から近い順に表示（店舗の緯度経度が未設定の場合はエリア名から自動推定）
- **店舗詳細ページ**：メイン写真1枚、Instagram／TikTokアイコンリンク、詳細文、応募ボタン
- **アドミン画面**：右上「店舗管理」から、店舗の追加・編集・削除（写真URL、SNSリンク、詳細文、タグ、緯度経度など全項目を編集可能）

## アドミンのログイン

デモ用パスコード：`nightcast2026`

`script.js` 内の `ADMIN_PASS` を書き換えることで変更できます。あくまで簡易的なフロントエンド側のロックであり、本番運用でセキュリティが必要な場合は、サーバー側の認証（例：パスワード保護されたAPI、Basic認証、GitHubに公開しない管理画面など）に置き換えることを推奨します。

## データの保存について（重要）

店舗データの保存先は実行環境によって自動的に切り替わります。

- **Claude Artifacts 上で開いた場合**：Claude の共有ストレージ（`window.storage`）を使用します。誰が編集しても、閲覧者全員に同じ内容が反映されます。
- **GitHub Pages などスタンドアロンで公開した場合**：ブラウザの `localStorage` を使用します。この場合、**編集内容はその端末・ブラウザだけに保存され、他の訪問者には共有されません**。全員に同じ店舗データを見せたい場合は、店舗データをサーバー（データベースやHeadless CMS、Firebase、Supabaseなど）に置き換える改修が必要です。

## カスタマイズのヒント

- 店舗の初期データは `script.js` の `DEFAULT_STORES` 配列にあります
- 配色・フォントは `styles.css` 冒頭の `:root { --bg: ...; --gold: ...; }` などの変数から調整できます
- 人気エリアの一覧は `script.js` の `POPULAR_AREAS` 配列で変更できます

/* ---------------- storage layer ----------------
   Uses Claude Artifacts' window.storage (shared) when running inside
   Claude, and falls back to the browser's localStorage when hosted
   standalone (e.g. GitHub Pages). See README.md for details/limits. */
const siteStorage = {
  async get(key){
    if(typeof window.storage !== 'undefined'){
      try{ return await window.storage.get(key, true); }catch(e){ /* fall through */ }
    }
    const v = localStorage.getItem(key);
    return v !== null ? {key, value:v, shared:false} : null;
  },
  async set(key, value){
    if(typeof window.storage !== 'undefined'){
      try{ return await window.storage.set(key, value, true); }catch(e){ /* fall through */ }
    }
    localStorage.setItem(key, value);
    return {key, value, shared:false};
  }
};

/* ---------------- data layer ---------------- */
const STORAGE_KEY = 'nightcast:stores';
const ADMIN_PASS = 'nightcast2026';

const DEFAULT_STORES = [
  {
    id:'s1', name:'CLUB LUNA', area:'銀座', genre:'キャバクラ',
    catch:'王道の高級感。初日から指名がつく研修体制。',
    wage:'時給6,000円〜', tags:['未経験歓迎','送迎あり','日払いOK'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'https://www.tiktok.com/',
    phone:'03-1234-5678', email:'recruit@example.com',
    description:'銀座で15年続く老舗高級クラブです。落ち着いた内装と上質なお客様が多く、未経験の方でもマナー研修からしっかりサポートします。週1日・3時間からの勤務OK。ヘアメイク仕上げのアドバイスも先輩キャストが行っています。'
  },
  {
    id:'s2', name:'Rouge et Or', area:'六本木', genre:'ラウンジ',
    catch:'カジュアルな雰囲気で本指名が取りやすい。',
    wage:'時給5,500円〜', tags:['自由出勤','ノルマなし'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'',
    phone:'03-2345-6789', email:'staff@example.com',
    description:'六本木交差点近くのラウンジ。アットホームな雰囲気で年齢層も幅広く活躍中。ノルマが一切ないので落ち着いて接客に集中できます。私服勤務OK。'
  },
  {
    id:'s3', name:'STELLA NOIR', area:'渋谷', genre:'キャバクラ',
    catch:'20代中心。SNS発信も応援するお店です。',
    wage:'時給5,000円〜／バック率50%', tags:['未経験歓迎','寮完備','写メ日記自由'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'https://www.tiktok.com/',
    phone:'03-3456-7890', email:'stella@example.com',
    description:'渋谷駅徒歩5分。20代スタッフが中心の明るいお店です。SNS発信を積極的にサポートしており、集客のノウハウも共有しています。寮完備で地方からの入店も歓迎。'
  },
  {
    id:'s4', name:'AMOUR', area:'新宿・歌舞伎町', genre:'キャバクラ',
    catch:'歌舞伎町最大級のフロア。稼げる環境が自慢。',
    wage:'時給7,000円〜', tags:['体験入店OK','日払いOK','送迎あり'],
    photo:'', instagram:'', tiktok:'',
    phone:'03-4567-8901', email:'amour@example.com',
    description:'歌舞伎町でも屈指の広さを誇るフロアで、日々多くのお客様で賑わっています。体験入店の日から報酬をお支払い。まずは雰囲気だけでも見学にお越しください。'
  },
  {
    id:'s5', name:'Bijou Terrace', area:'西麻布', genre:'ラウンジ',
    catch:'隠れ家的な少人数制。落ち着いて働きたい方へ。',
    wage:'時給6,500円〜', tags:['少人数制','30代活躍中'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'',
    phone:'03-5678-9012', email:'bijou@example.com',
    description:'西麻布の隠れ家的ラウンジ。会員制で常連のお客様が中心のため、落ち着いた接客が得意な方に向いています。30代・40代のキャストも多数活躍中です。'
  },
  {
    id:'s6', name:'PRISM GIRLS BAR', area:'池袋', genre:'ガールズバー',
    catch:'カジュアル出勤OKのガールズバー。',
    wage:'時給3,500円〜', tags:['未経験歓迎','週1日OK','ノルマなし'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'https://www.tiktok.com/',
    phone:'03-6789-0123', email:'prism@example.com',
    description:'池袋駅東口すぐのガールズバーです。カウンター越しの接客が中心なので初めての方でも安心。友達と一緒の応募・勤務も歓迎しています。'
  },
  {
    id:'s7', name:'VELVET NOX', area:'六本木', genre:'クラブ',
    catch:'DJブースを備えたハイエナジーなクラブ空間。',
    wage:'時給5,800円〜', tags:['未経験歓迎','日払いOK'],
    photo:'', instagram:'https://www.instagram.com/', tiktok:'https://www.tiktok.com/',
    phone:'03-7890-1234', email:'velvetnox@example.com',
    description:'六本木の中心にある会員制クラブ。生バンドやDJイベントも定期開催しており、華やかな雰囲気で働けます。接客だけでなくイベント運営に興味がある方も歓迎。'
  },
  {
    id:'s8', name:'スナック 桜', area:'新橋', genre:'スナック',
    catch:'常連さん中心のアットホームなスナック。',
    wage:'時給3,000円〜', tags:['主婦活躍中','週1日OK','ノルマなし'],
    photo:'', instagram:'', tiktok:'',
    phone:'03-8901-2345', email:'sakura-snack@example.com',
    description:'新橋の路地裏にある、常連さんとの距離が近いアットホームなスナックです。カラオケ好きなお客様が多く、接客が初めての方でも先輩ママがしっかりサポートします。'
  }
];

let STORES = [];
let currentDetailId = null;
let adminUnlocked = false;
let adminSelectedId = null;

async function loadStores(){
  try{
    const res = await siteStorage.get(STORAGE_KEY);
    if(res && res.value){
      STORES = JSON.parse(res.value);
      return;
    }
  }catch(e){ /* not found yet */ }
  STORES = DEFAULT_STORES;
  try{ await siteStorage.set(STORAGE_KEY, JSON.stringify(STORES)); }catch(e){}
}

async function saveStores(){
  try{
    const r = await siteStorage.set(STORAGE_KEY, JSON.stringify(STORES));
    return !!r;
  }catch(e){ return false; }
}

/* ---------------- utils ---------------- */
function esc(s){
  return (s||'').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
}
function showToast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(showToast._h);
  showToast._h = setTimeout(()=> t.classList.remove('show'), 2200);
}
function photoBlock(store, opts){
  opts = opts || {};
  const cls = opts.big ? 'detail-photo' : 'photo';
  if(store.photo){
    return `<div class="${cls}"><img src="${esc(store.photo)}" alt="${esc(store.name)}">${opts.badge ? `<span class="badge">${esc(store.genre)}</span>` : ''}</div>`;
  }
  const initial = (store.name||'?').trim().charAt(0);
  return `<div class="${cls}">${esc(initial)}${opts.badge ? `<span class="badge">${esc(store.genre)}</span>` : ''}</div>`;
}
function igIcon(){
  return `<svg viewBox="0 0 24 24" stroke-width="1.7"><rect x="3" y="3" width="18" height="18" rx="6"/><circle cx="12" cy="12" r="4.2"/><circle cx="17.2" cy="6.8" r="1.1" fill="currentColor" stroke="none"/></svg>`;
}
function ttIcon(){
  return `<svg viewBox="0 0 24 24" stroke-width="1.7"><path d="M14 3v10.8a3.6 3.6 0 1 1-3-3.55"/><path d="M14 3c.5 2.6 2.3 4.3 5 4.6"/></svg>`;
}

/* ---------------- quick filter icons ---------------- */
const GENRE_ICONS = {
  'キャバクラ': `<svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M4 4h16l-7 8v6h3M11 12v6H8"/></svg>`,
  'クラブ': `<svg viewBox="0 0 24 24" stroke-width="1.6"><circle cx="12" cy="12" r="8.2"/><circle cx="12" cy="12" r="1.6" fill="currentColor" stroke="none"/><path d="M12 3.8v2.2M12 18v2.2M3.8 12h2.2M18 12h2.2"/></svg>`,
  'ラウンジ': `<svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M4 12v3.5a1.5 1.5 0 0 0 1.5 1.5h13a1.5 1.5 0 0 0 1.5-1.5V12"/><path d="M4 12V9.5A2.5 2.5 0 0 1 6.5 7h11A2.5 2.5 0 0 1 20 9.5V12"/><path d="M4 17v2M20 17v2M2 12h20"/></svg>`,
  'スナック': `<svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M7 4h10l-1.4 9.5a3 3 0 0 1-3 2.5h-1.2a3 3 0 0 1-3-2.5L7 4Z"/><path d="M9 19.5h6M12 16v3.5"/></svg>`,
  'ガールズバー': `<svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M6 3h12l-1 4H7L6 3Z"/><path d="M8.5 7 6 20h12l-2.5-13"/><path d="M9.3 11.5h5.4"/></svg>`
};
function pinIcon(){
  return `<svg viewBox="0 0 24 24" stroke-width="1.6"><path d="M12 21s7-6.2 7-11.3A7 7 0 0 0 5 9.7C5 14.8 12 21 12 21Z"/><circle cx="12" cy="9.6" r="2.4"/></svg>`;
}

const POPULAR_AREAS = ['銀座','六本木','渋谷','新宿・歌舞伎町','西麻布','池袋','新橋'];
const GENRE_LIST = ['キャバクラ','クラブ','ラウンジ','スナック','ガールズバー'];

function renderQuickFilters(){
  const gWrap = document.getElementById('genre-icons');
  gWrap.innerHTML = GENRE_LIST.map(g => `
    <button type="button" class="quick-chip" data-genre="${esc(g)}" onclick="toggleGenreFilter('${esc(g)}')">
      <span class="circle">${GENRE_ICONS[g]}</span>
      <span class="label">${esc(g)}</span>
    </button>
  `).join('');

  const aWrap = document.getElementById('area-icons');
  aWrap.innerHTML = POPULAR_AREAS.map(a => `
    <button type="button" class="quick-chip" data-area="${esc(a)}" onclick="toggleAreaFilter('${esc(a)}')">
      <span class="circle">${pinIcon()}</span>
      <span class="label">${esc(a)}</span>
    </button>
  `).join('');
}

function toggleGenreFilter(g){
  const sel = document.getElementById('f-genre');
  sel.value = (sel.value === g) ? '' : g;
  applyFilters();
}
function toggleAreaFilter(a){
  const sel = document.getElementById('f-area');
  sel.value = (sel.value === a) ? '' : a;
  applyFilters();
}
function syncQuickChips(){
  const genreVal = document.getElementById('f-genre').value;
  const areaVal = document.getElementById('f-area').value;
  document.querySelectorAll('#genre-icons .quick-chip').forEach(el=>{
    el.classList.toggle('active', el.dataset.genre === genreVal && genreVal !== '');
  });
  document.querySelectorAll('#area-icons .quick-chip').forEach(el=>{
    el.classList.toggle('active', el.dataset.area === areaVal && areaVal !== '');
  });
}

/* ---------------- nearby / geolocation ---------------- */
const AREA_COORDS = {
  '銀座':{lat:35.6717,lng:139.7650},
  '六本木':{lat:35.6627,lng:139.7307},
  '渋谷':{lat:35.6595,lng:139.7005},
  '新宿・歌舞伎町':{lat:35.6938,lng:139.7034},
  '新宿':{lat:35.6905,lng:139.7005},
  '西麻布':{lat:35.6564,lng:139.7239},
  '池袋':{lat:35.7295,lng:139.7109},
  '新橋':{lat:35.6665,lng:139.7583},
  '恵比寿':{lat:35.6467,lng:139.7100},
  '赤坂':{lat:35.6737,lng:139.7368},
  '上野':{lat:35.7141,lng:139.7774},
  '五反田':{lat:35.6262,lng:139.7238}
};
const DEFAULT_COORDS = {lat:35.6812,lng:139.7671}; // 東京駅を仮の中心地とする
let userLocation = null;

function coordsForStore(s){
  if(typeof s.lat === 'number' && typeof s.lng === 'number' && !isNaN(s.lat) && !isNaN(s.lng)){
    return {lat:s.lat, lng:s.lng};
  }
  if(s.area && AREA_COORDS[s.area]) return AREA_COORDS[s.area];
  const key = s.area ? Object.keys(AREA_COORDS).find(k => s.area.includes(k) || k.includes(s.area)) : null;
  if(key) return AREA_COORDS[key];
  return DEFAULT_COORDS;
}
function haversineKm(lat1,lng1,lat2,lng2){
  const R = 6371;
  const dLat = (lat2-lat1) * Math.PI/180;
  const dLng = (lng2-lng1) * Math.PI/180;
  const a = Math.sin(dLat/2)**2 + Math.cos(lat1*Math.PI/180)*Math.cos(lat2*Math.PI/180)*Math.sin(dLng/2)**2;
  return R * 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
}
function distanceForStore(s){
  if(!userLocation) return null;
  const c = coordsForStore(s);
  return haversineKm(userLocation.lat, userLocation.lng, c.lat, c.lng);
}
function useMyLocation(){
  const btn = document.getElementById('loc-btn');
  if(!navigator.geolocation){ showToast('お使いのブラウザは位置情報に対応していません'); return; }
  btn.textContent = '📍 取得中...';
  navigator.geolocation.getCurrentPosition(
    pos => {
      userLocation = {lat:pos.coords.latitude, lng:pos.coords.longitude};
      btn.textContent = '📍 現在地から検索中';
      btn.classList.add('active');
      document.getElementById('distance-option').disabled = false;
      document.getElementById('f-sort').value = 'distance';
      applyFilters();
      showToast('現在地から近い順に表示しています');
    },
    () => {
      btn.textContent = '📍 現在地から探す';
      showToast('現在地を取得できませんでした。位置情報の利用を許可してください。');
    },
    {timeout:10000}
  );
}

/* ---------------- navigation ---------------- */
function go(view){
  document.querySelectorAll('main').forEach(m => m.classList.remove('active'));
  document.getElementById('view-'+view).classList.add('active');
  window.scrollTo({top:0, behavior:'smooth'});
  if(view === 'admin') renderAdmin();
}

/* ---------------- home / search ---------------- */
function populateFilterOptions(){
  const areas = [...new Set(STORES.map(s=>s.area))].sort();
  const genres = [...new Set(STORES.map(s=>s.genre))].sort();
  const areaSel = document.getElementById('f-area');
  const genreSel = document.getElementById('f-genre');
  areaSel.innerHTML = '<option value="">すべて</option>' + areas.map(a=>`<option value="${esc(a)}">${esc(a)}</option>`).join('');
  genreSel.innerHTML = '<option value="">すべて</option>' + genres.map(g=>`<option value="${esc(g)}">${esc(g)}</option>`).join('');
}

function wageNumber(store){
  const m = (store.wage||'').match(/[\d,]+/);
  return m ? parseInt(m[0].replace(/,/g,''),10) : 0;
}

function applyFilters(){
  const kw = document.getElementById('f-keyword').value.trim().toLowerCase();
  const area = document.getElementById('f-area').value;
  const genre = document.getElementById('f-genre').value;
  const sort = document.getElementById('f-sort').value;

  let list = STORES.filter(s=>{
    if(area && s.area !== area) return false;
    if(genre && s.genre !== genre) return false;
    if(kw){
      const hay = [s.name, s.area, s.genre, s.catch, (s.tags||[]).join(' ')].join(' ').toLowerCase();
      if(!hay.includes(kw)) return false;
    }
    return true;
  });

  if(sort === 'wage-desc') list = list.slice().sort((a,b)=> wageNumber(b)-wageNumber(a));
  else if(sort === 'name') list = list.slice().sort((a,b)=> a.name.localeCompare(b.name,'ja'));
  else if(sort === 'distance' && userLocation) list = list.slice().sort((a,b)=> distanceForStore(a) - distanceForStore(b));

  syncQuickChips();
  renderGrid(list, sort === 'distance' && !!userLocation);
}

function renderGrid(list, showDistance){
  const grid = document.getElementById('store-grid');
  document.getElementById('result-count').textContent = list.length;
  if(list.length === 0){
    grid.innerHTML = `<div class="empty"><span class="serif">該当する店舗が見つかりませんでした</span>キーワードやエリアを変えて、もう一度検索してみてください。</div>`;
    return;
  }
  grid.innerHTML = list.map(s => `
    <div class="card" onclick="openDetail('${s.id}')">
      ${photoBlock(s,{badge:true})}
      <div class="body">
        <div class="name">${esc(s.name)}</div>
        <div class="loc">${esc(s.area)} ・ ${esc(s.genre)}</div>
        <div class="catch">${esc(s.catch)}</div>
        <div class="tags">${(s.tags||[]).slice(0,3).map(t=>`<span class="tag">${esc(t)}</span>`).join('')}</div>
        <div class="foot"><span class="wage">${esc(s.wage)}</span></div>
        ${showDistance ? `<div class="dist-badge">📍現在地から約${distanceForStore(s).toFixed(1)}km</div>` : ''}
      </div>
    </div>
  `).join('');
}

/* ---------------- detail ---------------- */
function openDetail(id){
  currentDetailId = id;
  const s = STORES.find(x=>x.id===id);
  if(!s) return;
  const el = document.getElementById('detail-content');
  const hasIg = !!s.instagram, hasTt = !!s.tiktok;
  el.innerHTML = `
    <a class="back" onclick="go('home')">← 検索結果に戻る</a>
    ${photoBlock(s,{big:true})}
    <div class="detail-head">
      <div>
        <span class="eyebrow">${esc(s.genre)} ・ ${esc(s.area)}</span>
        <h1>${esc(s.name)}</h1>
        <div class="loc">${esc(s.catch)}</div>
      </div>
      <div class="sns-row">
        <a class="sns-btn ${hasIg?'':'disabled'}" href="${hasIg? esc(s.instagram) : '#'}" target="_blank" rel="noopener" title="Instagram">${igIcon()}</a>
        <a class="sns-btn ${hasTt?'':'disabled'}" href="${hasTt? esc(s.tiktok) : '#'}" target="_blank" rel="noopener" title="TikTok">${ttIcon()}</a>
      </div>
    </div>

    <div class="detail-stats">
      <div class="stat-chip"><div class="k">時給目安</div><div class="v">${esc(s.wage)}</div></div>
      <div class="stat-chip"><div class="k">エリア</div><div class="v">${esc(s.area)}</div></div>
      <div class="stat-chip"><div class="k">業態</div><div class="v">${esc(s.genre)}</div></div>
    </div>
    <div class="detail-tags">${(s.tags||[]).map(t=>`<span class="tag">${esc(t)}</span>`).join('')}</div>

    <div class="section-title">お店について</div>
    <div class="desc">${esc(s.description || 'この店舗の詳細情報は準備中です。')}</div>

    <div class="apply-bar">
      <a class="btn-apply" href="${s.email? 'mailto:'+esc(s.email) : '#'}">この店舗に応募する</a>
      <span class="info">${s.phone? '電話でのお問い合わせ：'+esc(s.phone) : 'お問い合わせ先は準備中です'}</span>
    </div>
  `;
  go('detail');
}

/* ---------------- admin ---------------- */
function emptyStoreDraft(){
  return { id:'', name:'', area:'', genre:'キャバクラ', catch:'', wage:'', tags:[], photo:'', instagram:'', tiktok:'', phone:'', email:'', description:'' };
}

function renderAdmin(){
  const el = document.getElementById('admin-content');
  if(!adminUnlocked){
    el.innerHTML = `
      <div class="admin-gate">
        <span class="serif">アドミンログイン</span>
        <div style="color:var(--text-muted); font-size:12.5px; line-height:1.8;">店舗情報の編集にはパスコードが必要です</div>
        <input type="password" id="admin-pass-input" placeholder="パスコードを入力">
        <button class="btn-search" style="width:100%;" onclick="tryAdminLogin()">ログイン</button>
        <div class="hint">デモ用パスコード：nightcast2026</div>
      </div>`;
    return;
  }
  const selected = STORES.find(s=>s.id===adminSelectedId) || null;
  el.innerHTML = `
    <div class="admin-header">
      <h1>店舗管理</h1>
      <a class="btn-ghost" onclick="go('home')">サイトを見る</a>
    </div>
    <div class="admin-panel">
      <div>
        <div class="admin-list" id="admin-list"></div>
        <button class="admin-add" onclick="selectAdminStore(null,true)">＋ 新しい店舗を追加</button>
      </div>
      <div id="admin-form-wrap"></div>
    </div>
  `;
  renderAdminList();
  renderAdminForm(selected);
}

function tryAdminLogin(){
  const v = document.getElementById('admin-pass-input').value;
  if(v === ADMIN_PASS){
    adminUnlocked = true;
    renderAdmin();
  }else{
    showToast('パスコードが違います');
  }
}

function renderAdminList(){
  const list = document.getElementById('admin-list');
  if(STORES.length===0){ list.innerHTML = `<div style="padding:20px; color:var(--text-faint); font-size:13px;">店舗がまだ登録されていません</div>`; return; }
  list.innerHTML = STORES.map(s=>`
    <div class="admin-row ${s.id===adminSelectedId?'active':''}" onclick="selectAdminStore('${s.id}')">
      <div>
        <div class="rn">${esc(s.name)}</div>
        <div class="ra">${esc(s.area)} ・ ${esc(s.genre)}</div>
      </div>
      <span class="del" onclick="event.stopPropagation(); deleteStore('${s.id}')">削除</span>
    </div>
  `).join('');
}

function selectAdminStore(id, isNew){
  adminSelectedId = isNew ? null : id;
  renderAdminList();
  renderAdminForm(isNew ? emptyStoreDraft() : STORES.find(s=>s.id===id));
}

function renderAdminForm(store){
  const wrap = document.getElementById('admin-form-wrap');
  if(!store){
    wrap.innerHTML = `<div class="admin-form" style="text-align:center; color:var(--text-faint); padding:60px 20px;">左のリストから店舗を選ぶか、<br>「＋ 新しい店舗を追加」を押してください</div>`;
    return;
  }
  const isNew = !store.id;
  wrap.innerHTML = `
    <div class="admin-form">
      <h3>${isNew ? '新規店舗を追加' : '店舗情報を編集：'+esc(store.name)}</h3>
      <div class="form-grid">
        <div><label>店舗名</label><input id="af-name" value="${esc(store.name)}"></div>
        <div><label>業態</label>
          <select id="af-genre">
            ${['キャバクラ','クラブ','ラウンジ','スナック','ガールズバー'].map(g=>`<option ${store.genre===g?'selected':''}>${g}</option>`).join('')}
          </select>
        </div>
        <div><label>エリア</label><input id="af-area" value="${esc(store.area)}" placeholder="例：銀座"></div>
        <div><label>時給表記</label><input id="af-wage" value="${esc(store.wage)}" placeholder="例：時給6,000円〜"></div>
        <div class="full"><label>キャッチコピー</label><input id="af-catch" value="${esc(store.catch)}" placeholder="一覧に表示される一言"></div>
        <div class="full"><label>タグ（カンマ区切り）</label><input id="af-tags" value="${esc((store.tags||[]).join(', '))}" placeholder="未経験歓迎, 日払いOK, 送迎あり"></div>
        <div class="full"><label>店舗写真URL</label><input id="af-photo" value="${esc(store.photo)}" placeholder="https://...（未入力の場合はイニシャル表示）">
          <div class="field-hint">詳細ページに1枚だけ表示されるメイン写真です</div>
        </div>
        <div><label>Instagram URL</label><input id="af-ig" value="${esc(store.instagram)}" placeholder="https://www.instagram.com/..."></div>
        <div><label>TikTok URL</label><input id="af-tt" value="${esc(store.tiktok)}" placeholder="https://www.tiktok.com/..."></div>
        <div><label>電話番号</label><input id="af-phone" value="${esc(store.phone)}"></div>
        <div><label>応募先メール</label><input id="af-email" value="${esc(store.email)}"></div>
        <div><label>緯度（任意）</label><input id="af-lat" value="${store.lat!=null?esc(String(store.lat)):''}" placeholder="例：35.6717">
          <div class="field-hint">未入力ならエリア名から自動推定</div>
        </div>
        <div><label>経度（任意）</label><input id="af-lng" value="${store.lng!=null?esc(String(store.lng)):''}" placeholder="例：139.7650"></div>
        <div class="full"><label>店舗詳細文</label><textarea id="af-desc" placeholder="お店の雰囲気、待遇、こんな人におすすめ...等">${esc(store.description)}</textarea></div>
      </div>
      <div class="form-actions">
        <button class="btn-save" onclick="saveAdminForm('${isNew?'':store.id}')">保存する</button>
        <span class="save-flag" id="save-flag">保存しました</span>
      </div>
    </div>
  `;
}

async function saveAdminForm(existingId){
  const draft = {
    id: existingId || ('s' + Date.now()),
    name: document.getElementById('af-name').value.trim() || '無題の店舗',
    genre: document.getElementById('af-genre').value,
    area: document.getElementById('af-area').value.trim(),
    wage: document.getElementById('af-wage').value.trim(),
    catch: document.getElementById('af-catch').value.trim(),
    tags: document.getElementById('af-tags').value.split(',').map(t=>t.trim()).filter(Boolean),
    photo: document.getElementById('af-photo').value.trim(),
    instagram: document.getElementById('af-ig').value.trim(),
    tiktok: document.getElementById('af-tt').value.trim(),
    phone: document.getElementById('af-phone').value.trim(),
    email: document.getElementById('af-email').value.trim(),
    description: document.getElementById('af-desc').value.trim(),
    lat: (()=>{ const v=document.getElementById('af-lat').value.trim(); return v===''? null : parseFloat(v); })(),
    lng: (()=>{ const v=document.getElementById('af-lng').value.trim(); return v===''? null : parseFloat(v); })(),
  };
  const idx = STORES.findIndex(s=>s.id===draft.id);
  if(idx >= 0) STORES[idx] = draft; else STORES.push(draft);

  const ok = await saveStores();
  adminSelectedId = draft.id;
  populateFilterOptions();
  applyFilters();
  renderAdminList();
  const flag = document.getElementById('save-flag');
  flag.textContent = ok ? '保存しました' : '保存に失敗しました（再試行してください）';
  flag.classList.add('show');
  setTimeout(()=>flag.classList.remove('show'), 2200);
  showToast(ok ? `「${draft.name}」を保存しました` : '保存に失敗しました');
}

async function deleteStore(id){
  const s = STORES.find(x=>x.id===id);
  if(!s) return;
  if(!confirm(`「${s.name}」を削除しますか？`)) return;
  STORES = STORES.filter(x=>x.id!==id);
  if(adminSelectedId === id) adminSelectedId = null;
  await saveStores();
  populateFilterOptions();
  applyFilters();
  renderAdmin();
  showToast('店舗を削除しました');
}

/* ---------------- boot ---------------- */
(async function init(){
  document.getElementById('store-grid').innerHTML = `<div class="empty"><span class="serif">読み込み中...</span></div>`;
  await loadStores();
  populateFilterOptions();
  renderQuickFilters();
  applyFilters();
  document.getElementById('f-keyword').addEventListener('keydown', e=>{ if(e.key==='Enter') applyFilters(); });
})();

  :root{
    --bg:#0c0a12;
    --bg-elevated:#150f1c;
    --card:#1c1424;
    --card-line:rgba(243,237,226,0.10);
    --gold:#cba15c;
    --gold-soft:#e8caa0;
    --rose:#d9506f;
    --rose-soft:#f0879b;
    --text:#f3ede2;
    --text-muted:#a99cb3;
    --text-faint:#75697f;
    --shadow-gold: 0 0 18px rgba(203,161,92,0.35);
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:
      radial-gradient(1200px 600px at 15% -10%, rgba(217,80,111,0.14), transparent 60%),
      radial-gradient(1000px 500px at 90% 0%, rgba(203,161,92,0.10), transparent 55%),
      var(--bg);
    color:var(--text);
    font-family:'Zen Kaku Gothic New', sans-serif;
    min-height:100vh;
    -webkit-font-smoothing:antialiased;
  }
  .serif{ font-family:'Shippori Mincho', serif; }
  .eyebrow{
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    letter-spacing:0.22em;
    color:var(--gold-soft);
    font-size:13px;
    text-transform:uppercase;
  }
  a{ color:inherit; text-decoration:none; }
  button{ font-family:inherit; cursor:pointer; }
  input,select,textarea{ font-family:inherit; }

  /* ---------- topbar ---------- */
  .topbar{
    display:flex; align-items:center; justify-content:space-between;
    padding:22px clamp(18px,4vw,56px);
    border-bottom:1px solid var(--card-line);
    position:sticky; top:0; z-index:40;
    background:rgba(12,10,18,0.86);
    backdrop-filter:blur(10px);
  }
  .brand{ display:flex; flex-direction:column; gap:2px; cursor:pointer; }
  .brand .mark{
    font-family:'Shippori Mincho', serif;
    font-weight:800;
    font-size:22px;
    letter-spacing:0.08em;
    color:var(--gold-soft);
    text-shadow: 0 0 8px rgba(203,161,92,0.55), 0 0 22px rgba(203,161,92,0.25);
    animation: flicker 6s infinite ease-in-out;
  }
  @keyframes flicker{
    0%,19%,21%,23%,80%,100%{ opacity:1; }
    20%,22%{ opacity:0.72; }
  }
  .brand .sub{ font-size:10px; letter-spacing:0.32em; color:var(--text-faint); }
  .nav-actions{ display:flex; align-items:center; gap:10px; }
  .btn-ghost{
    background:transparent; border:1px solid var(--card-line); color:var(--text-muted);
    padding:9px 16px; border-radius:999px; font-size:13px; letter-spacing:0.03em;
    transition:.2s;
  }
  .btn-ghost:hover{ border-color:var(--gold); color:var(--gold-soft); }

  main{ display:none; }
  main.active{ display:block; }

  /* ---------- hero / search ---------- */
  .hero{
    padding:56px clamp(18px,4vw,56px) 20px;
    text-align:center;
  }
  .hero h1{
    font-family:'Shippori Mincho', serif;
    font-weight:800;
    font-size:clamp(28px,4.4vw,46px);
    line-height:1.35;
    margin:14px 0 8px;
  }
  .hero h1 .accent{ color:var(--rose-soft); }
  .hero p.lead{ color:var(--text-muted); font-size:14.5px; max-width:520px; margin:0 auto; line-height:1.9;}

  .search-panel{
    max-width:920px; margin:34px auto 0;
    background:linear-gradient(180deg, var(--bg-elevated), var(--card));
    border:1px solid var(--card-line);
    border-radius:18px;
    padding:20px clamp(14px,3vw,28px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.45), inset 0 1px 0 rgba(255,255,255,0.03);
    position:relative;
  }
  .search-panel::before{
    content:"";
    position:absolute; inset:-1px;
    border-radius:18px;
    padding:1px;
    background:linear-gradient(120deg, rgba(203,161,92,0.5), transparent 30%, transparent 70%, rgba(217,80,111,0.4));
    -webkit-mask:linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
    -webkit-mask-composite:xor; mask-composite:exclude;
    pointer-events:none;
  }
  .search-grid{
    display:grid;
    grid-template-columns: 1.6fr 1fr 1fr auto;
    gap:12px;
  }
  @media (max-width:760px){ .search-grid{ grid-template-columns: 1fr 1fr; } }

  .field label{
    display:block; font-size:11px; letter-spacing:0.14em; color:var(--text-faint);
    margin-bottom:6px; text-transform:uppercase;
  }
  .field input, .field select{
    width:100%; background:rgba(0,0,0,0.28); border:1px solid var(--card-line);
    color:var(--text); padding:11px 12px; border-radius:9px; font-size:14px; outline:none;
    transition:.15s;
  }
  .field input:focus, .field select:focus{ border-color:var(--gold); box-shadow:0 0 0 3px rgba(203,161,92,0.14); }
  .field select{ appearance:none; background-image:linear-gradient(45deg, transparent 50%, var(--gold-soft) 50%), linear-gradient(135deg, var(--gold-soft) 50%, transparent 50%); background-position: calc(100% - 18px) center, calc(100% - 13px) center; background-size:5px 5px, 5px 5px; background-repeat:no-repeat; }

  .btn-search{
    background:linear-gradient(120deg, var(--rose), #b83a58);
    border:none; color:#fff; padding:0 26px; border-radius:9px; font-weight:700; font-size:14px;
    letter-spacing:0.04em; box-shadow:0 8px 22px rgba(217,80,111,0.35);
    transition:.2s; white-space:nowrap;
  }
  .btn-search:hover{ transform:translateY(-1px); box-shadow:0 10px 26px rgba(217,80,111,0.48); }

  /* ---------- quick icon filters ---------- */
  .quick-filters{
    max-width:1180px; margin:36px auto 0; padding:0 clamp(18px,4vw,56px);
    display:flex; flex-direction:column; gap:24px;
  }
  .quick-block .quick-label{
    font-size:11.5px; letter-spacing:0.14em; color:var(--text-faint); text-transform:uppercase;
    margin-bottom:12px; display:flex; align-items:center; gap:8px;
  }
  .quick-block .quick-label::after{ content:""; flex:1; height:1px; background:var(--card-line); }
  .quick-icons{ display:flex; gap:16px; flex-wrap:wrap; }
  .quick-chip{
    display:flex; flex-direction:column; align-items:center; gap:8px; width:76px;
    cursor:pointer; background:none; border:none; padding:0; color:inherit;
  }
  .quick-chip .circle{
    width:58px; height:58px; border-radius:50%; background:var(--card); border:1px solid var(--card-line);
    display:flex; align-items:center; justify-content:center; transition:.2s;
  }
  .quick-chip .circle svg{ width:23px; height:23px; stroke:var(--text-muted); fill:none; }
  .quick-chip .label{ font-size:11.5px; color:var(--text-muted); text-align:center; line-height:1.3; transition:.2s; }
  .quick-chip:hover .circle{ border-color:var(--gold); transform:translateY(-2px); }
  .quick-chip.active .circle{
    background:linear-gradient(135deg, rgba(203,161,92,0.28), rgba(217,80,111,0.16));
    border-color:var(--gold); box-shadow:var(--shadow-gold);
  }
  .quick-chip.active .circle svg{ stroke:var(--gold-soft); }
  .quick-chip.active .label{ color:var(--gold-soft); }

  .result-meta{
    max-width:1180px; margin:38px auto 14px; padding:0 clamp(18px,4vw,56px);
    display:flex; align-items:baseline; justify-content:space-between; gap:12px; flex-wrap:wrap;
  }
  .result-meta h2{ font-family:'Shippori Mincho',serif; font-size:19px; font-weight:700; margin:0; }
  .result-meta .count{ color:var(--gold-soft); }
  .sort-inline{ display:flex; align-items:center; gap:10px; font-size:12.5px; color:var(--text-muted); flex-wrap:wrap; }
  .sort-inline select{ background:transparent; border:1px solid var(--card-line); color:var(--text); border-radius:7px; padding:6px 10px; font-size:12.5px; }
  .loc-btn{
    background:transparent; border:1px solid var(--card-line); color:var(--text-muted);
    padding:7px 14px; border-radius:999px; font-size:12.5px; display:inline-flex; align-items:center; gap:6px;
    transition:.2s;
  }
  .loc-btn:hover{ border-color:var(--gold); color:var(--gold-soft); }
  .loc-btn.active{ border-color:var(--rose); color:var(--rose-soft); background:rgba(217,80,111,0.08); }
  .dist-badge{ font-size:11px; color:var(--text-faint); margin-top:2px; }

  /* ---------- grid / cards ---------- */
  .grid{
    max-width:1180px; margin:0 auto; padding:0 clamp(18px,4vw,56px) 70px;
    display:grid; grid-template-columns:repeat(auto-fill, minmax(268px,1fr)); gap:20px;
  }
  .card{
    background:var(--card); border:1px solid var(--card-line); border-radius:16px; overflow:hidden;
    cursor:pointer; transition:.22s; display:flex; flex-direction:column;
  }
  .card:hover{ transform:translateY(-4px); border-color:rgba(203,161,92,0.45); box-shadow:0 16px 34px rgba(0,0,0,0.4); }
  .card .photo{
    height:150px; position:relative; display:flex; align-items:center; justify-content:center;
    font-family:'Shippori Mincho',serif; font-size:40px; font-weight:800; color:rgba(243,237,226,0.28);
    overflow:hidden;
  }
  .card .photo img{ width:100%; height:100%; object-fit:cover; }
  .card .photo .badge{
    position:absolute; top:10px; left:10px; background:rgba(12,10,18,0.72); border:1px solid rgba(203,161,92,0.4);
    color:var(--gold-soft); font-size:10.5px; padding:4px 9px; border-radius:999px; letter-spacing:0.04em;
  }
  .card .body{ padding:16px 16px 18px; display:flex; flex-direction:column; gap:8px; flex:1; }
  .card .name{ font-family:'Shippori Mincho',serif; font-weight:700; font-size:17px; }
  .card .loc{ font-size:12px; color:var(--text-muted); letter-spacing:0.02em; }
  .card .catch{ font-size:12.5px; color:var(--text-muted); line-height:1.7; flex:1; }
  .card .foot{ display:flex; align-items:center; justify-content:space-between; margin-top:4px; }
  .wage{ color:var(--rose-soft); font-weight:700; font-size:13.5px; }
  .tags{ display:flex; flex-wrap:wrap; gap:6px; }
  .tag{ font-size:10.5px; color:var(--gold-soft); border:1px solid rgba(203,161,92,0.35); padding:3px 8px; border-radius:999px; }
  .empty{ grid-column:1/-1; text-align:center; padding:70px 20px; color:var(--text-faint); }
  .empty .serif{ font-size:18px; color:var(--text-muted); display:block; margin-bottom:8px; }

  /* ---------- detail ---------- */
  .detail-wrap{ max-width:820px; margin:0 auto; padding:26px clamp(18px,4vw,56px) 80px; }
  .back{ display:inline-flex; align-items:center; gap:6px; color:var(--text-muted); font-size:13px; margin-bottom:18px; }
  .back:hover{ color:var(--gold-soft); }
  .detail-photo{
    width:100%; aspect-ratio:16/9; border-radius:18px; overflow:hidden; position:relative;
    background:var(--card); border:1px solid var(--card-line);
    display:flex; align-items:center; justify-content:center;
    font-family:'Shippori Mincho',serif; font-size:56px; color:rgba(243,237,226,0.22); font-weight:800;
  }
  .detail-photo img{ width:100%; height:100%; object-fit:cover; }
  .detail-head{ margin-top:22px; display:flex; align-items:flex-start; justify-content:space-between; gap:16px; flex-wrap:wrap; }
  .detail-head .eyebrow{ display:block; margin-bottom:6px; }
  .detail-head h1{ font-family:'Shippori Mincho',serif; font-size:clamp(24px,3.4vw,32px); margin:0 0 6px; font-weight:800; }
  .detail-head .loc{ color:var(--text-muted); font-size:13.5px; }
  .sns-row{ display:flex; gap:10px; }
  .sns-btn{
    width:42px; height:42px; border-radius:50%; border:1px solid var(--card-line);
    display:flex; align-items:center; justify-content:center; background:var(--card);
    transition:.2s;
  }
  .sns-btn svg{ width:19px; height:19px; stroke:var(--text-muted); fill:none; }
  .sns-btn:hover{ border-color:var(--gold); box-shadow:var(--shadow-gold); }
  .sns-btn:hover svg{ stroke:var(--gold-soft); }
  .sns-btn.disabled{ opacity:0.3; pointer-events:none; }

  .detail-stats{ display:flex; gap:10px; flex-wrap:wrap; margin:22px 0 6px; }
  .stat-chip{ background:var(--card); border:1px solid var(--card-line); border-radius:11px; padding:10px 16px; }
  .stat-chip .k{ font-size:10.5px; color:var(--text-faint); letter-spacing:0.08em; }
  .stat-chip .v{ font-size:15px; color:var(--gold-soft); font-weight:700; margin-top:2px; }

  .detail-tags{ display:flex; flex-wrap:wrap; gap:8px; margin:18px 0; }
  .section-title{ font-family:'Shippori Mincho',serif; font-size:16px; font-weight:700; margin:30px 0 10px; padding-bottom:8px; border-bottom:1px solid var(--card-line); }
  .desc{ color:var(--text-muted); line-height:2; font-size:14.5px; white-space:pre-wrap; }

  .apply-bar{
    margin-top:34px; display:flex; gap:12px; flex-wrap:wrap; align-items:center;
    padding:20px; border-radius:14px; background:linear-gradient(120deg, rgba(217,80,111,0.14), rgba(203,161,92,0.08));
    border:1px solid var(--card-line);
  }
  .btn-apply{
    background:linear-gradient(120deg, var(--rose), #b83a58); color:#fff; border:none; padding:13px 26px;
    border-radius:999px; font-weight:700; font-size:14px; box-shadow:0 8px 22px rgba(217,80,111,0.35);
  }
  .apply-bar .info{ font-size:12.5px; color:var(--text-muted); }

  /* ---------- admin ---------- */
  .admin-wrap{ max-width:960px; margin:0 auto; padding:34px clamp(18px,4vw,56px) 90px; }
  .admin-gate{ max-width:360px; margin:80px auto; text-align:center; }
  .admin-gate .serif{ font-size:20px; margin-bottom:14px; display:block; }
  .admin-gate input{ width:100%; background:var(--card); border:1px solid var(--card-line); color:var(--text); padding:12px 14px; border-radius:9px; margin:14px 0; text-align:center; letter-spacing:0.1em; }
  .admin-gate .hint{ font-size:11.5px; color:var(--text-faint); margin-top:8px; }
  .admin-header{ display:flex; align-items:center; justify-content:space-between; margin-bottom:22px; flex-wrap:wrap; gap:10px; }
  .admin-header h1{ font-family:'Shippori Mincho',serif; font-size:24px; margin:0; }
  .admin-panel{ display:grid; grid-template-columns: 1fr 1.3fr; gap:22px; align-items:start; }
  @media (max-width:860px){ .admin-panel{ grid-template-columns:1fr; } }
  .admin-list{ background:var(--card); border:1px solid var(--card-line); border-radius:14px; padding:10px; max-height:640px; overflow:auto; }
  .admin-row{ display:flex; align-items:center; justify-content:space-between; padding:12px 10px; border-radius:9px; cursor:pointer; gap:8px; }
  .admin-row:hover{ background:rgba(255,255,255,0.03); }
  .admin-row.active{ background:rgba(203,161,92,0.12); border:1px solid rgba(203,161,92,0.3); }
  .admin-row .rn{ font-size:13.5px; font-weight:700; }
  .admin-row .ra{ font-size:11px; color:var(--text-faint); }
  .admin-row .del{ color:var(--text-faint); font-size:12px; padding:5px 8px; border-radius:6px; }
  .admin-row .del:hover{ color:var(--rose-soft); background:rgba(217,80,111,0.1); }
  .admin-add{ width:100%; margin-top:10px; background:transparent; border:1px dashed var(--card-line); color:var(--gold-soft); padding:11px; border-radius:9px; font-size:13px; }
  .admin-add:hover{ border-color:var(--gold); }

  .admin-form{ background:var(--card); border:1px solid var(--card-line); border-radius:14px; padding:22px; }
  .admin-form h3{ font-family:'Shippori Mincho',serif; margin:0 0 16px; font-size:16px; }
  .form-grid{ display:grid; grid-template-columns:1fr 1fr; gap:12px; }
  .form-grid .full{ grid-column:1/-1; }
  .form-grid label{ display:block; font-size:11px; color:var(--text-faint); letter-spacing:0.06em; margin-bottom:5px; }
  .form-grid input, .form-grid select, .form-grid textarea{
    width:100%; background:rgba(0,0,0,0.25); border:1px solid var(--card-line); color:var(--text);
    padding:10px 11px; border-radius:8px; font-size:13.5px; outline:none;
  }
  .form-grid textarea{ resize:vertical; min-height:100px; line-height:1.7; }
  .form-grid input:focus, .form-grid select:focus, .form-grid textarea:focus{ border-color:var(--gold); }
  .form-actions{ display:flex; gap:10px; margin-top:18px; align-items:center; }
  .btn-save{ background:linear-gradient(120deg, var(--gold), #a8814a); border:none; color:#1a1420; font-weight:800; padding:11px 22px; border-radius:9px; font-size:13.5px; }
  .save-flag{ font-size:12px; color:var(--gold-soft); opacity:0; transition:.3s; }
  .save-flag.show{ opacity:1; }
  .field-hint{ font-size:10.5px; color:var(--text-faint); margin-top:4px; }

  .toast{
    position:fixed; bottom:24px; left:50%; transform:translateX(-50%) translateY(20px);
    background:var(--card); border:1px solid rgba(203,161,92,0.4); color:var(--text);
    padding:12px 22px; border-radius:999px; font-size:13px; box-shadow:0 10px 30px rgba(0,0,0,0.4);
    opacity:0; pointer-events:none; transition:.25s; z-index:100;
  }
  .toast.show{ opacity:1; transform:translateX(-50%) translateY(0); }

  footer{ text-align:center; padding:30px; color:var(--text-faint); font-size:11.5px; border-top:1px solid var(--card-line); }
