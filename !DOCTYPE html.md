  
  
<!DOCTYPE html>  
  
<html lang="ko">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">  
<meta name="apple-mobile-web-app-capable" content="yes">  
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">  
<meta name="apple-mobile-web-app-title" content="덤프">  
<meta name="theme-color" content="#0a0a0a">  
<link rel="manifest" href="manifest.json">  
<title>브레인 덤프</title>  
<link href="https://fonts.googleapis.com/css2?family=Gowun+Batang:wght@400;700&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">  
<style>  
* { margin:0; padding:0; box-sizing:border-box; -webkit-tap-highlight-color:transparent; }  
  
:root {  
–bg: #0a0a0a;  
–s1: #141414;  
–s2: #1e1e1e;  
–s3: #282828;  
–border: #2a2a2a;  
–text: #ede9e1;  
–dim: #555;  
–dim2: #777;  
–todo: #f0a04b;  
–idea: #7ecfd4;  
–emotion: #e07898;  
–memo: #98c488;  
–safe-top: env(safe-area-inset-top, 44px);  
–safe-bottom: env(safe-area-inset-bottom, 34px);  
}  
  
html, body {  
height: 100%;  
background: var(–bg);  
color: var(–text);  
font-family: ‘Noto Sans KR’, sans-serif;  
overflow: hidden;  
}  
  
/* ── APP SHELL ── */  
.app {  
display: flex;  
flex-direction: column;  
height: 100dvh;  
height: 100vh;  
}  
  
/* ── STATUS BAR SPACER ── */  
.status-bar {  
height: var(–safe-top);  
background: var(–bg);  
flex-shrink: 0;  
}  
  
/* ── HEADER ── */  
.header {  
display: flex;  
align-items: center;  
justify-content: space-between;  
padding: 12px 20px 10px;  
flex-shrink: 0;  
}  
  
.header-title {  
font-family: ‘Gowun Batang’, serif;  
font-size: 22px;  
font-weight: 700;  
letter-spacing: -0.3px;  
}  
  
.header-sub {  
font-size: 11px;  
color: var(–dim2);  
font-weight: 300;  
}  
  
.header-right {  
display: flex;  
align-items: center;  
gap: 8px;  
}  
  
.icon-btn {  
width: 36px;  
height: 36px;  
background: var(–s2);  
border: 1px solid var(–border);  
border-radius: 10px;  
display: flex;  
align-items: center;  
justify-content: center;  
font-size: 15px;  
cursor: pointer;  
color: var(–text);  
transition: background 0.15s;  
}  
  
.icon-btn:active { background: var(–s3); }  
  
/* ── CONTENT AREA ── */  
.content {  
flex: 1;  
overflow: hidden;  
position: relative;  
}  
  
/* ── VIEWS ── */  
.view {  
position: absolute;  
inset: 0;  
overflow-y: auto;  
-webkit-overflow-scrolling: touch;  
overscroll-behavior: contain;  
padding: 0 16px 20px;  
display: none;  
}  
  
.view.active { display: block; }  
  
/* ── BOTTOM NAV ── */  
.bottom-nav {  
display: flex;  
background: var(–s1);  
border-top: 1px solid var(–border);  
padding-bottom: var(–safe-bottom);  
flex-shrink: 0;  
}  
  
.nav-item {  
flex: 1;  
display: flex;  
flex-direction: column;  
align-items: center;  
padding: 10px 0 8px;  
cursor: pointer;  
transition: all 0.15s;  
border: none;  
background: none;  
position: relative;  
}  
  
.nav-icon { font-size: 20px; line-height: 1; margin-bottom: 3px; }  
.nav-label { font-size: 9px; color: var(–dim); font-weight: 500; letter-spacing: 0.3px; font-family: ‘Noto Sans KR’, sans-serif; }  
.nav-item.active .nav-label { color: var(–text); }  
  
.nav-badge {  
position: absolute;  
top: 6px;  
right: calc(50% - 14px);  
background: var(–todo);  
color: #000;  
font-size: 9px;  
font-weight: 700;  
min-width: 16px;  
height: 16px;  
border-radius: 8px;  
display: flex;  
align-items: center;  
justify-content: center;  
padding: 0 4px;  
display: none;  
}  
  
.nav-badge.show { display: flex; }  
  
/* ─────────────────────────────────────  
DUMP VIEW (홈)  
───────────────────────────────────── */  
.dump-hero {  
padding: 20px 0 16px;  
text-align: center;  
}  
  
.dump-hero-icon {  
font-size: 32px;  
margin-bottom: 8px;  
animation: pulse 3s ease-in-out infinite;  
}  
  
@keyframes pulse {  
0%,100% { opacity: 0.7; transform: scale(1); }  
50% { opacity: 1; transform: scale(1.05); }  
}  
  
.dump-hero-text {  
font-size: 13px;  
color: var(–dim2);  
font-weight: 300;  
line-height: 1.7;  
}  
  
.input-card {  
background: var(–s1);  
border: 1px solid var(–border);  
border-radius: 16px;  
overflow: hidden;  
margin-bottom: 12px;  
}  
  
.input-area {  
width: 100%;  
background: transparent;  
border: none;  
color: var(–text);  
font-family: ‘Noto Sans KR’, sans-serif;  
font-size: 15px;  
font-weight: 300;  
line-height: 1.8;  
padding: 18px 18px 12px;  
resize: none;  
min-height: 140px;  
letter-spacing: 0.2px;  
}  
  
.input-area::placeholder { color: var(–dim); }  
.input-area:focus { outline: none; }  
  
.input-footer {  
display: flex;  
align-items: center;  
justify-content: space-between;  
padding: 10px 14px 14px;  
border-top: 1px solid var(–border);  
}  
  
.char-count {  
font-size: 11px;  
color: var(–dim);  
}  
  
.send-btn {  
background: var(–todo);  
color: #000;  
border: none;  
padding: 10px 20px;  
border-radius: 10px;  
font-family: ‘Noto Sans KR’, sans-serif;  
font-size: 13px;  
font-weight: 700;  
cursor: pointer;  
display: flex;  
align-items: center;  
gap: 6px;  
transition: all 0.2s;  
letter-spacing: 0.2px;  
}  
  
.send-btn:active { transform: scale(0.97); opacity: 0.85; }  
.send-btn:disabled { opacity: 0.35; }  
  
/* Recent items on home */  
.section-label {  
font-size: 10px;  
text-transform: uppercase;  
letter-spacing: 2px;  
color: var(–dim);  
font-weight: 500;  
margin: 20px 0 10px;  
}  
  
/* ─────────────────────────────────────  
CARDS  
───────────────────────────────────── */  
.card {  
background: var(–s1);  
border: 1px solid var(–border);  
border-radius: 14px;  
padding: 14px 16px;  
margin-bottom: 10px;  
animation: cardIn 0.3s ease;  
}  
  
@keyframes cardIn {  
from { opacity:0; transform:translateY(12px); }  
to { opacity:1; transform:translateY(0); }  
}  
  
.card-top {  
display: flex;  
align-items: center;  
gap: 8px;  
margin-bottom: 8px;  
}  
  
.tag {  
font-size: 10px;  
font-weight: 700;  
letter-spacing: 1px;  
text-transform: uppercase;  
padding: 3px 8px;  
border-radius: 6px;  
}  
  
.tag-todo { background: rgba(240,160,75,0.15); color: var(–todo); }  
.tag-idea { background: rgba(126,207,212,0.15); color: var(–idea); }  
.tag-emotion { background: rgba(224,120,152,0.15); color: var(–emotion); }  
.tag-memo { background: rgba(152,196,136,0.15); color: var(–memo); }  
  
.card-time {  
font-size: 11px;  
color: var(–dim);  
margin-left: auto;  
}  
  
.card-original {  
font-size: 12px;  
color: var(–dim2);  
font-style: italic;  
line-height: 1.6;  
padding-bottom: 8px;  
margin-bottom: 8px;  
border-bottom: 1px solid var(–border);  
}  
  
.card-content {  
font-size: 14px;  
line-height: 1.75;  
font-weight: 300;  
color: var(–text);  
}  
  
.card-actions {  
display: flex;  
gap: 6px;  
margin-top: 12px;  
flex-wrap: wrap;  
}  
  
.pill-btn {  
font-size: 11px;  
padding: 6px 12px;  
border-radius: 8px;  
border: 1px solid var(–border);  
background: var(–s2);  
color: var(–dim2);  
cursor: pointer;  
font-family: ‘Noto Sans KR’, sans-serif;  
font-weight: 500;  
transition: all 0.15s;  
-webkit-tap-highlight-color: transparent;  
}  
  
.pill-btn:active { background: var(–s3); }  
  
.pill-btn.cal-btn {  
border-color: rgba(240,160,75,0.3);  
color: var(–todo);  
}  
  
.pill-btn.del-btn {  
border-color: rgba(255,80,80,0.2);  
color: #ff6060;  
}  
  
.pill-btn.done-btn {  
border-color: rgba(240,160,75,0.5);  
color: var(–todo);  
text-decoration: line-through;  
}  
  
.expire-info {  
font-size: 11px;  
color: var(–emotion);  
margin-top: 8px;  
opacity: 0.8;  
}  
  
.cal-date-label {  
font-size: 11px;  
color: var(–todo);  
margin-top: 6px;  
display: flex;  
align-items: center;  
gap: 4px;  
}  
  
/* ─────────────────────────────────────  
EMPTY STATE  
───────────────────────────────────── */  
.empty-state {  
text-align: center;  
padding: 60px 30px;  
color: var(–dim);  
}  
  
.empty-icon { font-size: 40px; margin-bottom: 12px; opacity: 0.5; }  
.empty-msg { font-size: 13px; font-weight: 300; line-height: 1.8; }  
  
/* ─────────────────────────────────────  
CALENDAR VIEW  
───────────────────────────────────── */  
.cal-month-nav {  
display: flex;  
align-items: center;  
justify-content: space-between;  
padding: 18px 4px 14px;  
}  
  
.cal-month-title {  
font-family: ‘Gowun Batang’, serif;  
font-size: 18px;  
font-weight: 700;  
}  
  
.cal-arrow {  
width: 34px;  
height: 34px;  
background: var(–s2);  
border: 1px solid var(–border);  
border-radius: 10px;  
color: var(–text);  
font-size: 16px;  
cursor: pointer;  
display: flex;  
align-items: center;  
justify-content: center;  
}  
  
.cal-arrow:active { background: var(–s3); }  
  
.cal-grid {  
background: var(–s1);  
border: 1px solid var(–border);  
border-radius: 16px;  
padding: 16px;  
margin-bottom: 20px;  
}  
  
.cal-weekdays {  
display: grid;  
grid-template-columns: repeat(7,1fr);  
margin-bottom: 8px;  
}  
  
.cal-wd {  
text-align: center;  
font-size: 11px;  
color: var(–dim);  
font-weight: 500;  
padding: 4px 0;  
}  
  
.cal-days {  
display: grid;  
grid-template-columns: repeat(7,1fr);  
gap: 2px;  
}  
  
.cal-cell {  
aspect-ratio: 1;  
display: flex;  
flex-direction: column;  
align-items: center;  
justify-content: center;  
border-radius: 8px;  
font-size: 13px;  
position: relative;  
color: var(–text);  
}  
  
.cal-cell.other { color: var(–dim); opacity: 0.4; }  
.cal-cell.today {  
background: var(–todo);  
color: #000;  
font-weight: 700;  
border-radius: 10px;  
}  
  
.cal-cell.has-task::after {  
content: ‘’;  
width: 4px;  
height: 4px;  
background: var(–todo);  
border-radius: 50%;  
position: absolute;  
bottom: 3px;  
}  
  
.cal-cell.today.has-task::after { background: #000; }  
  
.cal-tasks-section {  
display: flex;  
flex-direction: column;  
gap: 8px;  
}  
  
.cal-task-item {  
background: var(–s1);  
border: 1px solid var(–border);  
border-left: 3px solid var(–todo);  
border-radius: 10px;  
padding: 12px 14px;  
display: flex;  
gap: 10px;  
align-items: flex-start;  
}  
  
.cal-task-date {  
font-size: 12px;  
color: var(–todo);  
font-weight: 700;  
min-width: 32px;  
line-height: 1.7;  
}  
  
.cal-task-text {  
font-size: 13px;  
font-weight: 300;  
line-height: 1.7;  
flex: 1;  
}  
  
/* ─────────────────────────────────────  
FILTER CHIPS (for list views)  
───────────────────────────────────── */  
.filter-row {  
display: flex;  
gap: 6px;  
overflow-x: auto;  
padding: 14px 0 10px;  
scrollbar-width: none;  
}  
  
.filter-row::-webkit-scrollbar { display: none; }  
  
.chip {  
flex-shrink: 0;  
font-size: 12px;  
padding: 6px 14px;  
border-radius: 20px;  
border: 1px solid var(–border);  
background: var(–s2);  
color: var(–dim2);  
cursor: pointer;  
font-family: ‘Noto Sans KR’, sans-serif;  
font-weight: 400;  
transition: all 0.15s;  
white-space: nowrap;  
}  
  
.chip.active {  
background: var(–todo);  
color: #000;  
border-color: var(–todo);  
font-weight: 700;  
}  
  
/* ─────────────────────────────────────  
MODAL  
───────────────────────────────────── */  
.modal-bg {  
display: none;  
position: fixed;  
inset: 0;  
background: rgba(0,0,0,0.75);  
z-index: 200;  
align-items: flex-end;  
justify-content: center;  
}  
  
.modal-bg.open { display: flex; animation: bgIn 0.2s ease; }  
@keyframes bgIn { from { opacity:0; } to { opacity:1; } }  
  
.modal-sheet {  
background: var(–s1);  
border-radius: 20px 20px 0 0;  
padding: 0 20px calc(var(–safe-bottom) + 20px);  
width: 100%;  
animation: sheetUp 0.3s cubic-bezier(0.34,1.56,0.64,1);  
}  
  
@keyframes sheetUp {  
from { transform: translateY(100%); }  
to { transform: translateY(0); }  
}  
  
.modal-handle {  
width: 36px;  
height: 4px;  
background: var(–border);  
border-radius: 2px;  
margin: 12px auto 20px;  
}  
  
.modal-title {  
font-family: ‘Gowun Batang’, serif;  
font-size: 18px;  
margin-bottom: 6px;  
}  
  
.modal-task-preview {  
font-size: 13px;  
color: var(–dim2);  
font-weight: 300;  
line-height: 1.6;  
margin-bottom: 18px;  
padding: 10px 14px;  
background: var(–s2);  
border-radius: 10px;  
}  
  
.date-input {  
background: var(–s2);  
border: 1px solid var(–border);  
color: var(–text);  
padding: 14px 16px;  
border-radius: 12px;  
font-family: ‘Noto Sans KR’, sans-serif;  
font-size: 15px;  
width: 100%;  
margin-bottom: 14px;  
-webkit-appearance: none;  
}  
  
.date-input:focus { outline: none; border-color: var(–todo); }  
  
.modal-btns {  
display: flex;  
gap: 10px;  
}  
  
.modal-cancel {  
flex: 1;  
padding: 14px;  
border-radius: 12px;  
border: 1px solid var(–border);  
background: var(–s2);  
color: var(–dim2);  
font-family: ‘Noto Sans KR’, sans-serif;  
font-size: 14px;  
cursor: pointer;  
font-weight: 500;  
}  
  
.modal-confirm {  
flex: 2;  
padding: 14px;  
border-radius: 12px;  
border: none;  
background: var(–todo);  
color: #000;  
font-family: ‘Noto Sans KR’, sans-serif;  
font-size: 14px;  
font-weight: 700;  
cursor: pointer;  
}  
  
.modal-confirm:active { opacity: 0.85; }  
  
/* ─────────────────────────────────────  
LOADING OVERLAY  
───────────────────────────────────── */  
.loading-overlay {  
display: none;  
position: fixed;  
inset: 0;  
background: rgba(10,10,10,0.85);  
z-index: 300;  
align-items: center;  
justify-content: center;  
flex-direction: column;  
gap: 16px;  
}  
  
.loading-overlay.show { display: flex; }  
  
.spinner {  
width: 36px;  
height: 36px;  
border: 3px solid var(–border);  
border-top-color: var(–todo);  
border-radius: 50%;  
animation: spin 0.8s linear infinite;  
}  
  
@keyframes spin { to { transform: rotate(360deg); } }  
  
.loading-text {  
font-size: 14px;  
color: var(–dim2);  
font-weight: 300;  
letter-spacing: 0.5px;  
}  
  
/* ─────────────────────────────────────  
TOAST  
───────────────────────────────────── */  
.toast {  
position: fixed;  
bottom: calc(var(–safe-bottom) + 80px);  
left: 50%;  
transform: translateX(-50%);  
background: var(–s3);  
color: var(–text);  
padding: 10px 20px;  
border-radius: 20px;  
font-size: 13px;  
font-weight: 400;  
white-space: nowrap;  
z-index: 400;  
display: none;  
border: 1px solid var(–border);  
box-shadow: 0 4px 20px rgba(0,0,0,0.5);  
}  
  
/* ─────────────────────────────────────  
INSTALL BANNER  
───────────────────────────────────── */  
.install-banner {  
margin: 0 0 12px;  
background: linear-gradient(135deg, rgba(240,160,75,0.12), rgba(240,160,75,0.05));  
border: 1px solid rgba(240,160,75,0.25);  
border-radius: 14px;  
padding: 14px 16px;  
display: flex;  
gap: 10px;  
align-items: flex-start;  
}  
  
.install-banner-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }  
  
.install-banner-text {  
flex: 1;  
font-size: 12px;  
color: var(–dim2);  
line-height: 1.7;  
font-weight: 300;  
}  
  
.install-banner-text strong {  
color: var(–todo);  
font-weight: 600;  
display: block;  
margin-bottom: 2px;  
font-size: 13px;  
}  
  
.install-banner-close {  
font-size: 16px;  
color: var(–dim);  
cursor: pointer;  
padding: 2px;  
flex-shrink: 0;  
}  
</style>  
  
</head>  
<body>  
  
<div class="app">  
  <!-- Status bar spacer for iOS -->  
  <div class="status-bar"></div>  
  
  <!-- Header -->  
  
  <div class="header">  
    <div>  
      <div class="header-title">브레인 덤프 ✦</div>  
    </div>  
    <div class="header-right">  
      <div class="icon-btn" onclick="clearAll()" title="전체 삭제">🗑</div>  
    </div>  
  </div>  
  
  <!-- Content -->  
  
  <div class="content">  
  
```  
<!-- ① 홈(덤프) 뷰 -->  
<div class="view active" id="view-home">  
  <div id="installBanner" class="install-banner" style="display:none">  
    <div class="install-banner-icon">📲</div>  
    <div class="install-banner-text">  
      <strong>홈 화면에 추가하기</strong>  
      Safari 하단 공유버튼(□↑) → '홈 화면에 추가' 탭하면 앱처럼 사용할 수 있어요  
    </div>  
    <div class="install-banner-close" onclick="dismissBanner()">✕</div>  
  </div>  
  
  <div class="dump-hero">  
    <div class="dump-hero-icon">🧠</div>  
    <div class="dump-hero-text">머릿속에 있는 거 다 쏟아내세요<br>AI가 정리해줄게요</div>  
  </div>  
  
  <div class="input-card">  
    <textarea  
      class="input-area"  
      id="dumpInput"  
      placeholder="할일, 아이디어, 욕, 아무 말이나 다 괜찮아요.  
```  
  
예) 내일 보고서 제출해야 함  
앱에 다크모드 넣으면 어떨까  
아 오늘 너무 피곤해 죽겠다  
점심 뭐 먹지”  
oninput=“updateCharCount()”  
></textarea>  
<div class="input-footer">  
<span class="char-count" id="charCount">0자</span>  
<button class="send-btn" id="sendBtn" onclick="processDump()">  
<span>✦</span> AI 분류  
</button>  
</div>  
</div>  
  
```  
  <!-- Recent -->  
  <div class="section-label">최근 항목</div>  
  <div id="recentList"></div>  
</div>  
  
<!-- ② 전체 목록 뷰 -->  
<div class="view" id="view-list">  
  <div class="filter-row" id="filterRow">  
    <div class="chip active" onclick="setFilter('all', this)">전체</div>  
    <div class="chip" onclick="setFilter('todo', this)">✓ 할일</div>  
    <div class="chip" onclick="setFilter('idea', this)">💡 아이디어</div>  
    <div class="chip" onclick="setFilter('emotion', this)">🔥 감정</div>  
    <div class="chip" onclick="setFilter('memo', this)">📝 메모</div>  
  </div>  
  <div id="listCards"></div>  
</div>  
  
<!-- ③ 캘린더 뷰 -->  
<div class="view" id="view-calendar">  
  <div class="cal-month-nav">  
    <button class="cal-arrow" onclick="changeMonth(-1)">‹</button>  
    <div class="cal-month-title" id="calTitle"></div>  
    <button class="cal-arrow" onclick="changeMonth(1)">›</button>  
  </div>  
  <div class="cal-grid">  
    <div class="cal-weekdays">  
      <div class="cal-wd">일</div><div class="cal-wd">월</div><div class="cal-wd">화</div>  
      <div class="cal-wd">수</div><div class="cal-wd">목</div><div class="cal-wd">금</div><div class="cal-wd">토</div>  
    </div>  
    <div class="cal-days" id="calDays"></div>  
  </div>  
  <div class="section-label">등록된 할일</div>  
  <div class="cal-tasks-section" id="calTaskList"></div>  
</div>  
```  
  
  </div>  
  
  <!-- Bottom Nav -->  
  
  <nav class="bottom-nav">  
    <button class="nav-item active" onclick="switchTab('home', this)" id="nav-home">  
      <div class="nav-icon">✦</div>  
      <div class="nav-label">덤프</div>  
    </button>  
    <button class="nav-item" onclick="switchTab('list', this)" id="nav-list">  
      <div class="nav-icon">☰</div>  
      <div class="nav-label">전체</div>  
      <div class="nav-badge" id="totalBadge"></div>  
    </button>  
    <button class="nav-item" onclick="switchTab('calendar', this)" id="nav-calendar">  
      <div class="nav-icon">📅</div>  
      <div class="nav-label">캘린더</div>  
      <div class="nav-badge" id="calBadge"></div>  
    </button>  
  </nav>  
</div>  
  
<!-- Date Modal -->  
  
<div class="modal-bg" id="dateModal">  
  <div class="modal-sheet">  
    <div class="modal-handle"></div>  
    <div class="modal-title">📅 캘린더에 추가</div>  
    <div class="modal-task-preview" id="modalPreview"></div>  
    <input type="date" class="date-input" id="modalDate">  
    <div class="modal-btns">  
      <button class="modal-cancel" onclick="closeModal()">취소</button>  
      <button class="modal-confirm" onclick="confirmCal()">추가하기</button>  
    </div>  
  </div>  
</div>  
  
<!-- Loading -->  
  
<div class="loading-overlay" id="loadingOverlay">  
  <div class="spinner"></div>  
  <div class="loading-text">AI가 분류 중이에요...</div>  
</div>  
  
<!-- Toast -->  
  
<div class="toast" id="toast"></div>  
  
<script>  
const STORAGE_KEY = 'bd_v2';  
let items = [];  
let calYear, calMonth;  
let pendingId = null;  
let activeFilter = 'all';  
  
// ── Storage ──────────────────────────────────────────  
function save() {  
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(items)); } catch(e) {}  
}  
  
function load() {  
  try {  
    const d = localStorage.getItem(STORAGE_KEY);  
    if (d) items = JSON.parse(d);  
  } catch(e) { items = []; }  
  pruneExpired();  
}  
  
function pruneExpired() {  
  const n = Date.now();  
  const prev = items.length;  
  items = items.filter(i => !(i.category === 'emotion' && i.expiresAt && n > i.expiresAt));  
  if (items.length !== prev) save();  
}  
  
// ── AI ───────────────────────────────────────────────  
async function processDump() {  
  const text = document.getElementById('dumpInput').value.trim();  
  if (!text) { showToast('내용을 입력해주세요'); return; }  
  
  document.getElementById('loadingOverlay').classList.add('show');  
  document.getElementById('sendBtn').disabled = true;  
  
  try {  
    const res = await fetch('https://api.anthropic.com/v1/messages', {  
      method: 'POST',  
      headers: { 'Content-Type': 'application/json' },  
      body: JSON.stringify({  
        model: 'claude-sonnet-4-20250514',  
        max_tokens: 1000,  
        system: `브레인 덤프 분류 AI입니다. 입력된 텍스트를 항목별로 분류하세요.  
  
카테고리:  
- todo: 할일, 과제, 해야 할 것  
- idea: 아이디어, 제안, 발전시킬 생각  
- emotion: 감정, 욕, 푸념, 감탄, 불만  
- memo: 정보, 사실, 메모  
  
반드시 JSON만 응답. 다른 텍스트 없이:  
{"items":[{"category":"todo|idea|emotion|memo","original":"원문","refined":"정돈된 표현"}]}  
  
refined 작성 가이드:  
- todo: 명확한 행동 문장 (~하기)  
- idea: 구체적이고 발전된 아이디어 문장  
- emotion: 원문 그대로 또는 살짝 정제  
- memo: 간결하게 정리된 메모`,  
        messages: [{ role: 'user', content: text }]  
      })  
    });  
  
    const data = await res.json();  
    const raw = data.content.map(i => i.text || '').join('');  
    const clean = raw.replace(/```json|```/g, '').trim();  
    const parsed = JSON.parse(clean);  
  
    const now = Date.now();  
    const newItems = parsed.items.map(item => ({  
      id: `${now}_${Math.random().toString(36).slice(2)}`,  
      category: item.category,  
      original: item.original,  
      refined: item.refined,  
      createdAt: now,  
      expiresAt: item.category === 'emotion' ? now + 7 * 86400000 : null,  
      calDate: null,  
      done: false  
    }));  
  
    items = [...newItems, ...items];  
    save();  
    document.getElementById('dumpInput').value = '';  
    document.getElementById('charCount').textContent = '0자';  
    renderAll();  
    showToast(`${newItems.length}개 분류 완료 ✦`);  
    switchTab('list', document.getElementById('nav-list'));  
  
  } catch(e) {  
    showToast('오류가 발생했어요. 다시 시도해주세요.');  
    console.error(e);  
  } finally {  
    document.getElementById('loadingOverlay').classList.remove('show');  
    document.getElementById('sendBtn').disabled = false;  
  }  
}  
  
// ── Render ───────────────────────────────────────────  
function renderAll() {  
  updateBadges();  
  renderRecent();  
  renderList();  
  renderCalendar();  
}  
  
function updateBadges() {  
  const total = items.length;  
  const calCount = items.filter(i => i.calDate).length;  
  const tb = document.getElementById('totalBadge');  
  const cb = document.getElementById('calBadge');  
  if (total > 0) { tb.textContent = total; tb.classList.add('show'); }  
  else tb.classList.remove('show');  
  if (calCount > 0) { cb.textContent = calCount; cb.classList.add('show'); }  
  else cb.classList.remove('show');  
}  
  
function renderRecent() {  
  const el = document.getElementById('recentList');  
  const recent = items.slice(0, 3);  
  if (!recent.length) {  
    el.innerHTML = '<div class="empty-state"><div class="empty-icon">✦</div><div class="empty-msg">아직 항목이 없어요<br>위에 뭐든 적어보세요</div></div>';  
    return;  
  }  
  el.innerHTML = recent.map(i => cardHTML(i, true)).join('');  
}  
  
function renderList() {  
  const el = document.getElementById('listCards');  
  const filtered = activeFilter === 'all' ? items : items.filter(i => i.category === activeFilter);  
  if (!filtered.length) {  
    const msgs = { all:'아직 항목이 없어요', todo:'할일이 없어요', idea:'아이디어가 없어요', emotion:'감정 기록이 없어요', memo:'메모가 없어요' };  
    el.innerHTML = `<div class="empty-state"><div class="empty-icon">✦</div><div class="empty-msg">${msgs[activeFilter]||''}</div></div>`;  
    return;  
  }  
  el.innerHTML = filtered.map(i => cardHTML(i, activeFilter === 'all')).join('');  
}  
  
const LABELS = { todo:'할일', idea:'아이디어', emotion:'감정', memo:'메모' };  
const TAG_CLS = { todo:'tag-todo', idea:'tag-idea', emotion:'tag-emotion', memo:'tag-memo' };  
  
function cardHTML(item, showTag) {  
  const d = new Date(item.createdAt);  
  const time = `${d.getMonth()+1}/${d.getDate()} ${d.getHours()}:${String(d.getMinutes()).padStart(2,'0')}`;  
  
  let actions = '';  
  if (item.category === 'todo') {  
    if (item.calDate) {  
      actions += `<span class="pill-btn done-btn">📅 ${item.calDate}</span>`;  
    } else {  
      actions += `<button class="pill-btn cal-btn" onclick="openModal('${item.id}')">📅 캘린더 추가</button>`;  
    }  
  }  
  actions += `<button class="pill-btn del-btn" onclick="deleteItem('${item.id}')">삭제</button>`;  
  
  let extra = '';  
  if (item.category === 'emotion' && item.expiresAt) {  
    const days = Math.max(1, Math.ceil((item.expiresAt - Date.now()) / 86400000));  
    extra = `<div class="expire-info">⏱ ${days}일 후 자동 삭제</div>`;  
  }  
  
  return `  
    <div class="card" id="c_${item.id}">  
      <div class="card-top">  
        ${showTag ? `<span class="tag ${TAG_CLS[item.category]}">${LABELS[item.category]}</span>` : ''}  
        <span class="card-time">${time}</span>  
      </div>  
      <div class="card-original">${esc(item.original)}</div>  
      <div class="card-content">${esc(item.refined)}</div>  
      <div class="card-actions">${actions}</div>  
      ${extra}  
    </div>`;  
}  
  
function esc(s) {  
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');  
}  
  
function deleteItem(id) {  
  items = items.filter(i => i.id !== id);  
  save(); renderAll();  
  showToast('삭제했어요');  
}  
  
function clearAll() {  
  if (!items.length) { showToast('항목이 없어요'); return; }  
  if (confirm(`${items.length}개 항목을 모두 삭제할까요?`)) {  
    items = []; save(); renderAll();  
    showToast('전체 삭제했어요');  
  }  
}  
  
// ── Calendar ─────────────────────────────────────────  
function initCal() {  
  const now = new Date();  
  calYear = now.getFullYear(); calMonth = now.getMonth();  
}  
  
function changeMonth(d) {  
  calMonth += d;  
  if (calMonth > 11) { calMonth = 0; calYear++; }  
  if (calMonth < 0) { calMonth = 11; calYear--; }  
  renderCalendar();  
}  
  
function renderCalendar() {  
  const mn = ['1월','2월','3월','4월','5월','6월','7월','8월','9월','10월','11월','12월'];  
  document.getElementById('calTitle').textContent = `${calYear}년 ${mn[calMonth]}`;  
  
  const today = new Date();  
  const firstDay = new Date(calYear, calMonth, 1).getDay();  
  const daysInMonth = new Date(calYear, calMonth+1, 0).getDate();  
  const prevDays = new Date(calYear, calMonth, 0).getDate();  
  
  const todoWithDate = items.filter(i => i.category === 'todo' && i.calDate);  
  const taskDays = new Set(todoWithDate.map(i => {  
    const d = new Date(i.calDate);  
    if (d.getFullYear() === calYear && d.getMonth() === calMonth) return d.getDate();  
    return null;  
  }).filter(Boolean));  
  
  let html = '';  
  
  for (let i = firstDay-1; i >= 0; i--)  
    html += `<div class="cal-cell other">${prevDays-i}</div>`;  
  
  for (let d = 1; d <= daysInMonth; d++) {  
    const isToday = today.getFullYear()===calYear && today.getMonth()===calMonth && today.getDate()===d;  
    const hasTask = taskDays.has(d);  
    html += `<div class="cal-cell ${isToday?'today':''} ${hasTask?'has-task':''}">${d}</div>`;  
  }  
  
  const total = firstDay + daysInMonth;  
  for (let d = 1; d <= (total%7===0 ? 0 : 7-(total%7)); d++)  
    html += `<div class="cal-cell other">${d}</div>`;  
  
  document.getElementById('calDays').innerHTML = html;  
  
  const sorted = todoWithDate.sort((a,b) => new Date(a.calDate)-new Date(b.calDate));  
  const tl = document.getElementById('calTaskList');  
  if (!sorted.length) {  
    tl.innerHTML = '<div class="empty-state"><div class="empty-icon">📅</div><div class="empty-msg">캘린더에 추가된 할일이 없어요</div></div>';  
  } else {  
    tl.innerHTML = sorted.map(i => {  
      const d = new Date(i.calDate);  
      return `<div class="cal-task-item">  
        <div class="cal-task-date">${d.getMonth()+1}/${d.getDate()}</div>  
        <div class="cal-task-text">${esc(i.refined)}</div>  
      </div>`;  
    }).join('');  
  }  
}  
  
// ── Modal ─────────────────────────────────────────────  
function openModal(id) {  
  pendingId = id;  
  const item = items.find(i => i.id === id);  
  document.getElementById('modalPreview').textContent = item?.refined || '';  
  document.getElementById('modalDate').value = new Date().toISOString().slice(0,10);  
  document.getElementById('dateModal').classList.add('open');  
}  
  
function closeModal() {  
  document.getElementById('dateModal').classList.remove('open');  
  pendingId = null;  
}  
  
function confirmCal() {  
  const date = document.getElementById('modalDate').value;  
  if (!date) { showToast('날짜를 선택해주세요'); return; }  
  const item = items.find(i => i.id === pendingId);  
  if (item) {  
    item.calDate = date;  
    save(); renderAll();  
    const d = date.replace(/-/g,'');  
    const t = encodeURIComponent(item.refined);  
    window.open(`https://calendar.google.com/calendar/render?action=TEMPLATE&text=${t}&dates=${d}/${d}`, '_blank');  
    showToast('캘린더에 추가했어요 📅');  
  }  
  closeModal();  
}  
  
// ── Tabs ──────────────────────────────────────────────  
function switchTab(name, el) {  
  document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));  
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));  
  document.getElementById(`view-${name}`).classList.add('active');  
  el.classList.add('active');  
  if (name === 'calendar') renderCalendar();  
}  
  
// ── Filter ────────────────────────────────────────────  
function setFilter(f, el) {  
  activeFilter = f;  
  document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));  
  el.classList.add('active');  
  renderList();  
}  
  
// ── UI helpers ────────────────────────────────────────  
function updateCharCount() {  
  const len = document.getElementById('dumpInput').value.length;  
  document.getElementById('charCount').textContent = `${len}자`;  
}  
  
function showToast(msg) {  
  const t = document.getElementById('toast');  
  t.textContent = msg;  
  t.style.display = 'block';  
  clearTimeout(t._t);  
  t._t = setTimeout(() => t.style.display = 'none', 2200);  
}  
  
function dismissBanner() {  
  document.getElementById('installBanner').style.display = 'none';  
  localStorage.setItem('bd_banner_dismissed', '1');  
}  
  
// ── Install banner ────────────────────────────────────  
function checkInstallBanner() {  
  const isStandalone = window.navigator.standalone === true;  
  const dismissed = localStorage.getItem('bd_banner_dismissed');  
  const isSafari = /Safari/.test(navigator.userAgent) && !/Chrome/.test(navigator.userAgent);  
  if (!isStandalone && !dismissed && isSafari) {  
    document.getElementById('installBanner').style.display = 'flex';  
  }  
}  
  
// ── Init ──────────────────────────────────────────────  
initCal();  
load();  
renderAll();  
checkInstallBanner();  
  
// Auto-prune every minute  
setInterval(() => { pruneExpired(); renderAll(); }, 60000);  
  
// Close modal on backdrop tap  
document.getElementById('dateModal').addEventListener('click', function(e) {  
  if (e.target === this) closeModal();  
});  
</script>  
  
</body>  
</html>  
