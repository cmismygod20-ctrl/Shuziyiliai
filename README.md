<!DOCTYPE html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>数字健康产业安全平台 | 디지털 헬스 산업 보안 플랫폼</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&family=Noto+Sans+KR:wght@300;400;500;700&family=DM+Serif+Display&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
:root {
  --blue: #1a6bff;
  --blue-light: #e8f0ff;
  --blue-mid: #4a8aff;
  --teal: #0eb5a0;
  --teal-light: #e0f7f5;
  --orange: #ff6b35;
  --orange-light: #fff0eb;
  --red: #e53935;
  --red-light: #fdecea;
  --green: #2e9e6b;
  --green-light: #e6f7f0;
  --yellow: #f5a623;
  --yellow-light: #fff8ec;
  --text: #1a2332;
  --text2: #4a5568;
  --text3: #8a9ab5;
  --bg: #f4f7fc;
  --white: #ffffff;
  --border: #dde3ee;
  --shadow: 0 2px 12px rgba(26,107,255,.08);
  --shadow-hover: 0 8px 32px rgba(26,107,255,.16);
}
* { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior: smooth; }
body { background:var(--bg); color:var(--text); font-family:'Noto Sans SC',sans-serif; }

/* ── NAV ── */
.nav {
  position: sticky; top:0; z-index:100;
  background: rgba(255,255,255,.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
  display: flex; align-items:center; justify-content:space-between;
  padding: 0 40px; height:60px;
  box-shadow: 0 1px 8px rgba(0,0,0,.06);
}
.nav-logo { font-family:'DM Serif Display'; font-size:20px; color:var(--blue); letter-spacing:.5px; }
.nav-logo span { color:var(--teal); }
.nav-links { display:flex; gap:28px; list-style:none; }
.nav-links a { color:var(--text2); text-decoration:none; font-size:14px; font-weight:500; padding:6px 0; border-bottom:2px solid transparent; transition:.2s; }
.nav-links a:hover { color:var(--blue); border-color:var(--blue); }
.lang-box { display:flex; gap:6px; }
.lbtn { background:none; border:1.5px solid var(--border); color:var(--text2); padding:5px 14px; border-radius:20px; font-size:13px; cursor:pointer; transition:.2s; font-family:inherit; }
.lbtn.on { background:var(--blue); border-color:var(--blue); color:#fff; font-weight:700; }

/* ── HERO ── */
.hero {
  background: linear-gradient(135deg, #f0f5ff 0%, #e8f4f8 50%, #f0faf6 100%);
  padding: 80px 40px 60px;
  display:flex; gap:60px; align-items:center; flex-wrap:wrap;
  border-bottom: 1px solid var(--border);
}
.hero-text { flex:1; min-width:300px; }
.hero-badge {
  display:inline-flex; align-items:center; gap:6px;
  background:var(--blue-light); color:var(--blue); border-radius:20px;
  padding:5px 14px; font-size:12px; font-weight:700; margin-bottom:20px;
  border: 1px solid rgba(26,107,255,.2);
}
.hero-badge::before { content:'●'; font-size:8px; animation:blink 1.8s infinite; }
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:.3} }
.hero h1 { font-family:'DM Serif Display'; font-size:42px; line-height:1.2; color:var(--text); margin-bottom:8px; }
.hero h1 .c1 { color:var(--blue); }
.hero h1 .c2 { color:var(--teal); }
.hero-sub { font-family:'Noto Sans KR',sans-serif; font-size:18px; color:var(--text2); margin-bottom:20px; font-weight:300; }
.hero-desc { font-size:15px; color:var(--text2); line-height:1.9; max-width:520px; }
.hero-stats { display:flex; gap:32px; margin-top:32px; flex-wrap:wrap; }
.hstat { text-align:center; }
.hstat-n { font-size:28px; font-weight:700; color:var(--blue); font-family:'DM Serif Display'; }
.hstat-l { font-size:12px; color:var(--text3); margin-top:2px; }
.hero-visual { flex:0 0 320px; }
.ecg-box {
  background:var(--white); border-radius:16px; padding:24px;
  box-shadow: var(--shadow); border:1px solid var(--border);
}
.ecg-title { font-size:12px; color:var(--text3); margin-bottom:12px; font-weight:600; letter-spacing:.5px; }
.ecg-svg { width:100%; }
.ecg-metrics { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-top:16px; }
.metric-chip {
  background:var(--bg); border-radius:10px; padding:10px 14px;
  border:1px solid var(--border);
}
.metric-chip .val { font-size:20px; font-weight:700; }
.metric-chip .lbl { font-size:11px; color:var(--text3); margin-top:2px; }

/* ── TABS ── */
.tabs-wrap { background:var(--white); border-bottom:1px solid var(--border); position:sticky; top:60px; z-index:90; }
.tabs { display:flex; padding:0 40px; gap:0; overflow-x:auto; }
.tab {
  padding:16px 24px; font-size:14px; font-weight:500; color:var(--text3);
  border-bottom:3px solid transparent; cursor:pointer; white-space:nowrap;
  transition:.2s; background:none; border-top:none; border-left:none; border-right:none;
  font-family:inherit;
}
.tab:hover { color:var(--blue); }
.tab.active { color:var(--blue); border-bottom-color:var(--blue); font-weight:700; }

/* ── SECTIONS ── */
.section { padding:60px 40px; max-width:1200px; margin:0 auto; }
.sec-head { margin-bottom:36px; }
.sec-tag { font-size:12px; font-weight:700; color:var(--teal); letter-spacing:1px; text-transform:uppercase; margin-bottom:6px; }
.sec-title { font-family:'DM Serif Display'; font-size:32px; color:var(--text); margin-bottom:4px; }
.sec-title-kr { font-family:'Noto Sans KR',sans-serif; font-size:18px; color:var(--text2); font-weight:300; }

/* ── FEATURE CARDS ── */
.feat-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(300px,1fr)); gap:20px; }
.feat-card {
  background:var(--white); border-radius:14px; padding:28px;
  border:1px solid var(--border); transition:.25s;
  box-shadow: var(--shadow);
}
.feat-card:hover { box-shadow:var(--shadow-hover); transform:translateY(-3px); border-color:var(--blue); }
.feat-icon { width:48px; height:48px; border-radius:12px; display:flex; align-items:center; justify-content:center; font-size:22px; margin-bottom:16px; }
.feat-name { font-size:16px; font-weight:700; margin-bottom:3px; }
.feat-name-kr { font-family:'Noto Sans KR',sans-serif; font-size:13px; color:var(--blue); margin-bottom:10px; }
.feat-desc { font-size:14px; color:var(--text2); line-height:1.75; }

/* ── INTERACTIVE: 건강 위험 평가기 ── */
.tool-box {
  background:var(--white); border-radius:16px; padding:36px;
  box-shadow:var(--shadow); border:1px solid var(--border);
  max-width:760px;
}
.tool-row { display:flex; align-items:center; gap:16px; margin-bottom:20px; flex-wrap:wrap; }
.tool-label { font-size:14px; font-weight:600; min-width:140px; }
.tool-label .kr { font-family:'Noto Sans KR',sans-serif; font-size:12px; color:var(--text3); font-weight:400; }
.tool-input, .tool-select {
  border:1.5px solid var(--border); border-radius:8px; padding:8px 14px;
  font-size:14px; font-family:inherit; color:var(--text); background:var(--bg);
  transition:.2s; flex:1; min-width:140px;
}
.tool-input:focus, .tool-select:focus { outline:none; border-color:var(--blue); background:#fff; }
.tool-btn {
  background:var(--blue); color:#fff; border:none; border-radius:10px;
  padding:12px 32px; font-size:15px; font-weight:700; cursor:pointer;
  font-family:inherit; transition:.2s; width:100%;
}
.tool-btn:hover { background:#0f5be8; box-shadow:0 4px 16px rgba(26,107,255,.35); }
.result-box {
  background: linear-gradient(135deg, var(--blue-light), var(--teal-light));
  border-radius:12px; padding:24px; margin-top:24px; border:1px solid var(--border);
  display:none;
}
.result-box.show { display:block; animation:fadeIn .4s; }
@keyframes fadeIn { from{opacity:0;transform:translateY(8px)} to{opacity:1;transform:translateY(0)} }
.result-level { font-size:20px; font-weight:700; margin-bottom:8px; }
.result-tips { font-size:14px; color:var(--text2); line-height:1.8; }
.result-bars { margin-top:16px; display:flex; flex-direction:column; gap:8px; }
.rbar-row { display:flex; align-items:center; gap:10px; font-size:13px; }
.rbar-lbl { min-width:100px; color:var(--text2); }
.rbar-wrap { flex:1; background:rgba(255,255,255,.6); border-radius:4px; height:8px; overflow:hidden; }
.rbar-fill { height:100%; border-radius:4px; transition: width 1s ease; }

/* ── 患者データ管理 (Demo Table) ── */
.demo-table-wrap { background:var(--white); border-radius:14px; overflow:hidden; box-shadow:var(--shadow); border:1px solid var(--border); }
.demo-table-bar {
  background:var(--bg); padding:14px 20px; border-bottom:1px solid var(--border);
  display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:10px;
}
.search-input {
  border:1.5px solid var(--border); border-radius:8px; padding:7px 14px;
  font-size:13px; font-family:inherit; width:220px;
}
.search-input:focus { outline:none; border-color:var(--blue); }
.add-btn {
  background:var(--teal); color:#fff; border:none; border-radius:8px;
  padding:8px 18px; font-size:13px; font-weight:700; cursor:pointer; font-family:inherit;
  transition:.2s;
}
.add-btn:hover { background:#0a9e8c; }
table { width:100%; border-collapse:collapse; }
th { background:var(--bg); padding:12px 16px; text-align:left; font-size:12px; font-weight:700; color:var(--text3); letter-spacing:.5px; border-bottom:1px solid var(--border); }
td { padding:14px 16px; font-size:14px; border-bottom:1px solid var(--border); vertical-align:middle; }
tr:last-child td { border-bottom:none; }
tr:hover td { background:#f8faff; }
.badge {
  display:inline-block; padding:3px 10px; border-radius:20px; font-size:12px; font-weight:600;
}
.badge-g { background:var(--green-light); color:var(--green); }
.badge-y { background:var(--yellow-light); color:var(--yellow); }
.badge-r { background:var(--red-light); color:var(--red); }
.badge-b { background:var(--blue-light); color:var(--blue); }
.del-btn {
  background:none; border:1px solid var(--border); color:var(--text3); border-radius:6px;
  padding:4px 10px; font-size:12px; cursor:pointer; font-family:inherit; transition:.2s;
}
.del-btn:hover { background:var(--red-light); color:var(--red); border-color:var(--red); }

/* ── 알림 센터 ── */
.alert-list { display:flex; flex-direction:column; gap:12px; max-width:760px; }
.alert-item {
  background:var(--white); border-radius:12px; padding:18px 20px;
  border:1px solid var(--border); display:flex; gap:14px; align-items:flex-start;
  box-shadow:var(--shadow); transition:.2s;
}
.alert-item:hover { box-shadow:var(--shadow-hover); }
.alert-icon { width:38px; height:38px; border-radius:10px; display:flex; align-items:center; justify-content:center; font-size:18px; flex-shrink:0; }
.alert-title { font-size:15px; font-weight:700; margin-bottom:3px; }
.alert-desc { font-size:13px; color:var(--text2); line-height:1.6; }
.alert-time { font-size:11px; color:var(--text3); margin-top:4px; }
.alert-dismiss {
  margin-left:auto; background:none; border:none; color:var(--text3); cursor:pointer;
  font-size:18px; line-height:1; padding:2px 6px; border-radius:4px; transition:.2s;
  flex-shrink:0;
}
.alert-dismiss:hover { color:var(--red); background:var(--red-light); }

/* ── 통계 대시보드 ── */
.stats-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(200px,1fr)); gap:16px; }
.stat-card {
  background:var(--white); border-radius:14px; padding:24px;
  box-shadow:var(--shadow); border:1px solid var(--border);
}
.stat-num2 { font-size:36px; font-weight:700; font-family:'DM Serif Display'; margin-bottom:4px; }
.stat-lbl2 { font-size:13px; color:var(--text2); }
.stat-lbl2 .kr { font-family:'Noto Sans KR',sans-serif; font-size:12px; color:var(--text3); }
.stat-change { font-size:12px; margin-top:6px; }
.up { color:var(--green); } .dn { color:var(--red); }
.progress-wrap { margin-top:10px; background:var(--bg); border-radius:4px; height:6px; overflow:hidden; }
.progress-fill { height:100%; border-radius:4px; }

/* ── PDF DOC 섹션 ── */
.doc-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(260px,1fr)); gap:16px; }
.doc-card {
  background:var(--white); border-radius:12px; padding:24px;
  border:1px solid var(--border); box-shadow:var(--shadow); display:flex; gap:14px;
}
.doc-num { font-family:'DM Serif Display'; font-size:36px; color:var(--blue); line-height:1; flex-shrink:0; min-width:44px; }
.doc-title { font-size:15px; font-weight:700; margin-bottom:3px; }
.doc-kr { font-family:'Noto Sans KR',sans-serif; font-size:13px; color:var(--teal); margin-bottom:6px; }
.doc-desc { font-size:13px; color:var(--text2); line-height:1.7; }

/* ── DOWNLOAD BUTTON ── */
.dl-btn {
  position:fixed; bottom:28px; right:28px; z-index:200;
  background: linear-gradient(135deg, var(--blue), var(--teal));
  color:#fff; border:none; border-radius:50px;
  padding:14px 26px; font-size:14px; font-weight:700;
  cursor:pointer; font-family:inherit;
  display:flex; align-items:center; gap:8px;
  box-shadow: 0 6px 24px rgba(26,107,255,.4);
  transition:.2s;
}
.dl-btn:hover { transform:translateY(-2px); box-shadow:0 10px 32px rgba(26,107,255,.5); }
.dl-btn:active { transform:scale(.97); }
.dl-btn:disabled { opacity:.7; cursor:wait; }

/* ── FOOTER ── */
.footer {
  background:var(--white); border-top:1px solid var(--border);
  padding:40px; display:flex; justify-content:space-between; align-items:center;
  flex-wrap:wrap; gap:16px;
}
.footer-l { font-family:'DM Serif Display'; font-size:16px; color:var(--blue); }
.footer-r { font-size:13px; color:var(--text3); }

/* ── MODAL (add patient) ── */
.modal-bg {
  display:none; position:fixed; inset:0; background:rgba(0,0,0,.35);
  z-index:300; align-items:center; justify-content:center;
}
.modal-bg.open { display:flex; }
.modal {
  background:#fff; border-radius:16px; padding:32px; width:420px; max-width:92vw;
  box-shadow:0 16px 64px rgba(0,0,0,.18); animation:fadeIn .3s;
}
.modal h3 { font-size:18px; font-weight:700; margin-bottom:20px; }
.modal-field { margin-bottom:14px; }
.modal-field label { font-size:13px; font-weight:600; display:block; margin-bottom:5px; color:var(--text2); }
.modal-field input, .modal-field select {
  width:100%; border:1.5px solid var(--border); border-radius:8px; padding:9px 12px;
  font-size:14px; font-family:inherit; color:var(--text);
}
.modal-field input:focus, .modal-field select:focus { outline:none; border-color:var(--blue); }
.modal-actions { display:flex; gap:10px; margin-top:20px; }
.modal-ok { flex:1; background:var(--blue); color:#fff; border:none; border-radius:8px; padding:11px; font-size:14px; font-weight:700; cursor:pointer; font-family:inherit; }
.modal-cancel { flex:1; background:var(--bg); color:var(--text2); border:1px solid var(--border); border-radius:8px; padding:11px; font-size:14px; cursor:pointer; font-family:inherit; }

/* util */
.show-zh .kr-only { display:none !important; }
.show-kr .zh-only { display:none !important; }
@media(max-width:700px) {
  .nav { padding:0 16px; } .nav-links { display:none; }
  .hero { padding:50px 20px 40px; } .tabs { padding:0 16px; }
  .section { padding:40px 20px; }
  .hero-visual { flex:1 1 100%; }
  .footer { padding:24px 20px; text-align:center; }
}
</style>
</head>
<body class="show-zh">

<!-- ── NAV ── -->
<nav class="nav">
  <div class="nav-logo">HealthGuard<span>Pro</span></div>
  <ul class="nav-links">
    <li><a href="#features">功能 기능</a></li>
    <li><a href="#assess">风险评估 위험평가</a></li>
    <li><a href="#patients">患者管理 환자관리</a></li>
    <li><a href="#alerts">安全预警 보안경고</a></li>
    <li><a href="#stats">数据统计 통계</a></li>
    <li><a href="#pdfdoc">PDF文档</a></li>
  </ul>
  <div class="lang-box">
    <button class="lbtn on" id="btn-zh" onclick="setLang('zh')">中文</button>
    <button class="lbtn" id="btn-kr" onclick="setLang('kr')">한국어</button>
  </div>
</nav>

<!-- ── HERO ── -->
<div class="hero">
  <div class="hero-text">
    <div class="hero-badge">
      <span class="zh-only">数字健康医疗安全平台 · 平台开发竞赛</span>
      <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">디지털 헬스 보안 플랫폼 · 플랫폼 개발 경진대회</span>
    </div>
    <h1>
      <span class="c1 zh-only">数字健康</span><span class="c1 kr-only" style="font-family:'Noto Sans KR',sans-serif">디지털 헬스</span><br>
      <span class="c2 zh-only">产业安全</span><span class="c2 kr-only" style="font-family:'Noto Sans KR',sans-serif">산업 보안</span><br>
      <span class="zh-only">管理平台</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">관리 플랫폼</span>
    </h1>
    <div class="hero-sub zh-only">디지털 헬스케어 산업 통합 보안 관리 시스템</div>
    <div class="hero-sub kr-only">数字健康医疗产业综合安全管理系统</div>
    <p class="hero-desc zh-only">
      集患者健康风险评估、安全预警、数据加密管理于一体的数字医疗综合平台，守护医疗数据安全，推动产业稳健发展。
    </p>
    <p class="hero-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">
      환자 건강 위험 평가, 보안 경고, 데이터 암호화 관리를 통합한 디지털 의료 종합 플랫폼입니다.
    </p>
    <div class="hero-stats">
      <div class="hstat"><div class="hstat-n">4,280</div><div class="hstat-l zh-only">注册患者 / 등록 환자</div><div class="hstat-l kr-only">등록 환자 수</div></div>
      <div class="hstat"><div class="hstat-n" style="color:var(--teal)">99.9%</div><div class="hstat-l">시스템 가용률</div></div>
      <div class="hstat"><div class="hstat-n" style="color:var(--orange)">12</div><div class="hstat-l zh-only">今日预警 / 오늘 경고</div><div class="hstat-l kr-only">오늘 보안 경고</div></div>
    </div>
  </div>
  <div class="hero-visual">
    <div class="ecg-box">
      <div class="ecg-title">REAL-TIME ECG MONITOR · 실시간 심전도</div>
      <svg class="ecg-svg" height="60" viewBox="0 0 280 60">
        <polyline id="ecg-line" points="" fill="none" stroke="#1a6bff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
      <div class="ecg-metrics">
        <div class="metric-chip"><div class="val" style="color:var(--red)">72 <span style="font-size:14px">bpm</span></div><div class="lbl">心率 / 심박수</div></div>
        <div class="metric-chip"><div class="val" style="color:var(--blue)">120/80</div><div class="lbl">血压 / 혈압</div></div>
        <div class="metric-chip"><div class="val" style="color:var(--teal)">98<span style="font-size:14px">%</span></div><div class="lbl">血氧 / 산소포화도</div></div>
        <div class="metric-chip"><div class="val" style="color:var(--orange)">36.5<span style="font-size:14px">°C</span></div><div class="lbl">体温 / 체온</div></div>
      </div>
    </div>
  </div>
</div>

<!-- ── TABS ── -->
<div class="tabs-wrap">
  <div class="tabs">
    <button class="tab active" onclick="scrollTo('#features')">
      <span class="zh-only">核心功能</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">핵심 기능</span>
    </button>
    <button class="tab" onclick="scrollTo('#assess')">
      <span class="zh-only">健康风险评估</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">건강 위험 평가</span>
    </button>
    <button class="tab" onclick="scrollTo('#patients')">
      <span class="zh-only">患者数据管理</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 데이터 관리</span>
    </button>
    <button class="tab" onclick="scrollTo('#alerts')">
      <span class="zh-only">安全预警中心</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">보안 경고 센터</span>
    </button>
    <button class="tab" onclick="scrollTo('#stats')">
      <span class="zh-only">数据统计</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">데이터 통계</span>
    </button>
    <button class="tab" onclick="scrollTo('#pdfdoc')">PDF</button>
  </div>
</div>

<!-- ── 1. FEATURES ── -->
<div id="features" style="background:var(--white); border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">CORE FEATURES · 핵심 기능</div>
    <div class="sec-title zh-only">网站主要功能介绍</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">웹사이트 주요 기능 소개</div>
    <div class="sec-title-kr zh-only">웹사이트 주요 기능 소개</div>
    <div class="sec-title-kr kr-only">网站主要功能介绍</div>
  </div>
  <div class="feat-grid">
    <div class="feat-card">
      <div class="feat-icon" style="background:var(--blue-light)">🩺</div>
      <div class="feat-name zh-only">健康风险智能评估</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">건강 위험 스마트 평가</div>
      <div class="feat-name-kr zh-only">건강 위험 스마트 평가</div>
      <div class="feat-name-kr kr-only">健康风险智能评估</div>
      <div class="feat-desc zh-only">输入患者年龄、血压、BMI等基本指标，系统即时计算心血管、糖尿病等风险等级，提供个性化健康建议。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">환자의 나이, 혈압, BMI 등 기본 지표를 입력하면 심혈관, 당뇨 위험 등급을 즉시 계산하고 맞춤 건강 조언을 제공합니다.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon" style="background:var(--teal-light)">👥</div>
      <div class="feat-name zh-only">患者数据安全管理</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 데이터 보안 관리</div>
      <div class="feat-name-kr zh-only">환자 데이터 보안 관리</div>
      <div class="feat-name-kr kr-only">患者数据安全管理</div>
      <div class="feat-desc zh-only">可视化患者档案列表，支持实时搜索过滤、添加新患者、删除记录，所有数据符合HIPAA安全标准。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 기록 목록의 시각화, 실시간 검색 필터, 신규 환자 추가, 기록 삭제를 지원하며 HIPAA 보안 기준을 준수합니다.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon" style="background:var(--red-light)">🔔</div>
      <div class="feat-name zh-only">实时安全预警中心</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">실시간 보안 경고 센터</div>
      <div class="feat-name-kr zh-only">실시간 보안 경고 센터</div>
      <div class="feat-name-kr kr-only">实时安全预警中心</div>
      <div class="feat-desc zh-only">展示异常访问、数据泄露风险、系统漏洞等安全告警，支持一键消除已处理警告，维护清洁的安全日志。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">비정상 접근, 데이터 유출 위험, 시스템 취약점 등 보안 경고를 표시하고 처리된 경고를 원클릭으로 삭제할 수 있습니다.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon" style="background:var(--orange-light)">📊</div>
      <div class="feat-name zh-only">医疗数据统计看板</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">의료 데이터 통계 대시보드</div>
      <div class="feat-name-kr zh-only">의료 데이터 통계 대시보드</div>
      <div class="feat-name-kr kr-only">医疗数据统计看板</div>
      <div class="feat-desc zh-only">可视化呈现患者总数、高风险比例、系统合规评分、今日预警数等核心运营指标，支持实时数据刷新。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 총수, 고위험 비율, 시스템 컴플라이언스 점수, 오늘의 경고 수 등 핵심 운영 지표를 시각화하여 표시합니다.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon" style="background:var(--green-light)">🌐</div>
      <div class="feat-name zh-only">中韩双语切换界面</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">중한 이중 언어 인터페이스</div>
      <div class="feat-name-kr zh-only">중한 이중 언어 인터페이스</div>
      <div class="feat-name-kr kr-only">中韩双语切换界面</div>
      <div class="feat-desc zh-only">右上角语言切换按钮，中文/韩文全站即时切换，面向中韩两国医疗从业者设计，无障碍使用体验。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">우측 상단 언어 전환 버튼으로 중국어/한국어를 즉시 전환할 수 있으며, 한중 의료 종사자를 위해 설계되었습니다.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon" style="background:#f3e8ff)">📄</div>
      <div class="feat-name zh-only">一键导出韩语版PDF</div>
      <div class="feat-name kr-only" style="font-family:'Noto Sans KR',sans-serif">원클릭 한국어 PDF 내보내기</div>
      <div class="feat-name-kr zh-only">원클릭 한국어 PDF 내보내기</div>
      <div class="feat-name-kr kr-only">一键导出韩语版PDF</div>
      <div class="feat-desc zh-only">右下角固定下载按钮，点击即生成包含设计方法、功能说明、预期效果、补充说明四项内容的完整韩语PDF文档。</div>
      <div class="feat-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">우측 하단 고정 다운로드 버튼을 클릭하면 설계 방법, 기능 설명, 기대 효과, 보충 설명이 담긴 한국어 PDF가 자동 생성됩니다.</div>
    </div>
  </div>
</div>
</div>

<!-- ── 2. HEALTH RISK ASSESSMENT (Interactive) ── -->
<div id="assess" style="border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">INTERACTIVE TOOL · 인터랙티브 도구</div>
    <div class="sec-title zh-only">健康风险智能评估器</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">건강 위험 스마트 평가기</div>
    <div class="sec-title-kr zh-only">건강 위험 스마트 평가기 · 직접 사용해보세요</div>
    <div class="sec-title-kr kr-only">健康风险智能评估器 · 请直接使用</div>
  </div>
  <div class="tool-box">
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">年龄 · 나이</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">나이 · 年齢</span>
      </div>
      <input class="tool-input" id="inp-age" type="number" min="1" max="120" placeholder="예: 55" value="55">
    </div>
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">性别 · 성별</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">성별 · 性别</span>
      </div>
      <select class="tool-select" id="inp-sex">
        <option value="m">男 / 남성</option>
        <option value="f">女 / 여성</option>
      </select>
    </div>
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">收缩压 (mmHg) · 수축기혈압</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">수축기혈압 (mmHg)</span>
      </div>
      <input class="tool-input" id="inp-bp" type="number" min="60" max="220" placeholder="예: 138" value="138">
    </div>
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">BMI 指数</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">BMI 지수</span>
      </div>
      <input class="tool-input" id="inp-bmi" type="number" min="10" max="50" step="0.1" placeholder="예: 27.5" value="27.5">
    </div>
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">吸烟史 · 흡연</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">흡연 여부</span>
      </div>
      <select class="tool-select" id="inp-smoke">
        <option value="0">否 / 없음</option>
        <option value="1">是 / 있음</option>
      </select>
    </div>
    <div class="tool-row">
      <div class="tool-label">
        <span class="zh-only">糖尿病史 · 당뇨병</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">당뇨병 여부</span>
      </div>
      <select class="tool-select" id="inp-dm">
        <option value="0">否 / 없음</option>
        <option value="1">是 / 있음</option>
      </select>
    </div>
    <button class="tool-btn" onclick="runAssess()">
      <span class="zh-only">🔍 开始风险评估</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">🔍 위험도 평가 시작</span>
    </button>
    <div class="result-box" id="result-box">
      <div class="result-level" id="result-level"></div>
      <div class="result-tips" id="result-tips"></div>
      <div class="result-bars" id="result-bars"></div>
    </div>
  </div>
</div>
</div>

<!-- ── 3. PATIENT DATA TABLE ── -->
<div id="patients" style="background:var(--white); border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">PATIENT MANAGEMENT · 환자 관리</div>
    <div class="sec-title zh-only">患者数据安全管理</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 데이터 보안 관리</div>
    <div class="sec-title-kr zh-only">환자 데이터 보안 관리 · 검색·추가·삭제 가능</div>
    <div class="sec-title-kr kr-only">患者数据安全管理 · 可搜索、添加、删除</div>
  </div>
  <div class="demo-table-wrap">
    <div class="demo-table-bar">
      <input class="search-input" id="pt-search" placeholder="🔍 搜索患者 / 환자 검색..." oninput="filterPt()">
      <button class="add-btn" onclick="openModal()">
        + <span class="zh-only">添加患者</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">환자 추가</span>
      </button>
    </div>
    <div style="overflow-x:auto;">
      <table id="pt-table">
        <thead>
          <tr>
            <th>ID</th>
            <th><span class="zh-only">姓名</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">이름</span></th>
            <th><span class="zh-only">年龄</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">나이</span></th>
            <th><span class="zh-only">诊断</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">진단명</span></th>
            <th><span class="zh-only">风险等级</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">위험 등급</span></th>
            <th><span class="zh-only">状态</span><span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">상태</span></th>
            <th></th>
          </tr>
        </thead>
        <tbody id="pt-tbody"></tbody>
      </table>
    </div>
  </div>
</div>
</div>

<!-- ── 4. ALERTS ── -->
<div id="alerts" style="border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">SECURITY ALERTS · 보안 경고</div>
    <div class="sec-title zh-only">实时安全预警中心</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">실시간 보안 경고 센터</div>
    <div class="sec-title-kr zh-only">실시간 보안 경고 센터 · × 버튼으로 삭제 가능</div>
    <div class="sec-title-kr kr-only">实时安全预警中心 · 点×按钮可删除</div>
  </div>
  <div class="alert-list" id="alert-list"></div>
</div>
</div>

<!-- ── 5. STATS ── -->
<div id="stats" style="background:var(--white); border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">STATISTICS · 통계</div>
    <div class="sec-title zh-only">医疗数据统计看板</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">의료 데이터 통계 대시보드</div>
  </div>
  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-num2" style="color:var(--blue)" id="s-total">4,280</div>
      <div class="stat-lbl2 zh-only">注册患者总数<div class="kr">등록 환자 총수</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">등록 환자 총수</div>
      <div class="stat-change up">↑ 3.2% 本月</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:86%;background:var(--blue)"></div></div>
    </div>
    <div class="stat-card">
      <div class="stat-num2" style="color:var(--red)" id="s-highrisk">312</div>
      <div class="stat-lbl2 zh-only">高风险患者<div class="kr">고위험 환자</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">고위험 환자</div>
      <div class="stat-change dn">↑ 1.1% 需关注</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:22%;background:var(--red)"></div></div>
    </div>
    <div class="stat-card">
      <div class="stat-num2" style="color:var(--green)">94<span style="font-size:20px">%</span></div>
      <div class="stat-lbl2 zh-only">合规评分 (HIPAA)<div class="kr">컴플라이언스 점수</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">컴플라이언스 점수</div>
      <div class="stat-change up">↑ 2.5% 良好</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:94%;background:var(--green)"></div></div>
    </div>
    <div class="stat-card">
      <div class="stat-num2" style="color:var(--orange)" id="s-alerts">12</div>
      <div class="stat-lbl2 zh-only">今日安全预警<div class="kr">오늘 보안 경고</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">오늘 보안 경고</div>
      <div class="stat-change dn">需处理 / 처리 필요</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:45%;background:var(--orange)"></div></div>
    </div>
    <div class="stat-card">
      <div class="stat-num2" style="color:var(--teal)">99.9<span style="font-size:18px">%</span></div>
      <div class="stat-lbl2 zh-only">系统可用率<div class="kr">시스템 가용률</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">시스템 가용률</div>
      <div class="stat-change up">↑ 稳定运行 안정 운영</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:99%;background:var(--teal)"></div></div>
    </div>
    <div class="stat-card">
      <div class="stat-num2" style="color:#9b59b6">1,834</div>
      <div class="stat-lbl2 zh-only">本月接诊次数<div class="kr">이번 달 진료 건수</div></div>
      <div class="stat-lbl2 kr-only" style="font-family:'Noto Sans KR',sans-serif">이번 달 진료 건수</div>
      <div class="stat-change up">↑ 5.8% 增长</div>
      <div class="progress-wrap"><div class="progress-fill" style="width:68%;background:#9b59b6"></div></div>
    </div>
  </div>
</div>
</div>

<!-- ── 6. PDF DOC ── -->
<div id="pdfdoc" style="border-bottom:1px solid var(--border);">
<div class="section">
  <div class="sec-head">
    <div class="sec-tag">PDF DOCUMENT · PDF 문서</div>
    <div class="sec-title zh-only">PDF文档内容（4项必须内容）</div>
    <div class="sec-title kr-only" style="font-family:'Noto Sans KR',sans-serif">PDF 문서 내용 (4가지 필수 항목)</div>
    <div class="sec-title-kr zh-only">우측 하단 버튼으로 한국어 PDF 다운로드 가능</div>
    <div class="sec-title-kr kr-only">右下角按钮可下载韩语版PDF</div>
  </div>
  <div class="doc-grid">
    <div class="doc-card">
      <div class="doc-num">01</div>
      <div>
        <div class="doc-title zh-only">网站设计与开发方法</div>
        <div class="doc-title kr-only" style="font-family:'Noto Sans KR',sans-serif">웹사이트 설계 및 개발 방법</div>
        <div class="doc-kr zh-only">웹사이트 설계 및 개발 방법</div>
        <div class="doc-kr kr-only">网站设计与开发方法</div>
        <div class="doc-desc zh-only">单文件HTML架构、响应式设计、CSS变量主题系统、前端技术栈选型与部署方案说明。</div>
        <div class="doc-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">단일 파일 HTML 아키텍처, 반응형 디자인, CSS 변수 테마 시스템 및 배포 방안 설명.</div>
      </div>
    </div>
    <div class="doc-card">
      <div class="doc-num" style="color:var(--teal)">02</div>
      <div>
        <div class="doc-title zh-only">网站主要功能介绍</div>
        <div class="doc-title kr-only" style="font-family:'Noto Sans KR',sans-serif">웹사이트 주요 기능 소개</div>
        <div class="doc-kr zh-only">웹사이트 주요 기능 소개</div>
        <div class="doc-kr kr-only">网站主要功能介绍</div>
        <div class="doc-desc zh-only">健康风险评估、患者管理、安全预警、数据统计、双语切换、PDF导出六大核心功能详解。</div>
        <div class="doc-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">건강 위험 평가, 환자 관리, 보안 경고, 데이터 통계, 이중 언어, PDF 내보내기 6가지 핵심 기능 상세 설명.</div>
      </div>
    </div>
    <div class="doc-card">
      <div class="doc-num" style="color:var(--orange)">03</div>
      <div>
        <div class="doc-title zh-only">项目预期效果与应用价值</div>
        <div class="doc-title kr-only" style="font-family:'Noto Sans KR',sans-serif">프로젝트 기대 효과 및 응용 가치</div>
        <div class="doc-kr zh-only">프로젝트 기대 효과 및 응용 가치</div>
        <div class="doc-kr kr-only">项目预期效果与应用价值</div>
        <div class="doc-desc zh-only">提升数据安全性、降低合规成本、推动产业发展的量化目标与社会价值评估。</div>
        <div class="doc-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">데이터 보안 강화, 컴플라이언스 비용 절감, 산업 발전 촉진을 위한 정량적 목표 및 사회적 가치 평가.</div>
      </div>
    </div>
    <div class="doc-card">
      <div class="doc-num" style="color:var(--green)">04</div>
      <div>
        <div class="doc-title zh-only">其余相关补充说明</div>
        <div class="doc-title kr-only" style="font-family:'Noto Sans KR',sans-serif">기타 관련 보충 설명</div>
        <div class="doc-kr zh-only">기타 관련 보충 설명</div>
        <div class="doc-kr kr-only">其余相关补充说明</div>
        <div class="doc-desc zh-only">技术局限性、未来迭代计划、法律合规声明及参考标准文献等补充信息。</div>
        <div class="doc-desc kr-only" style="font-family:'Noto Sans KR',sans-serif">기술적 한계, 향후 개선 계획, 법적 컴플라이언스 선언 및 참고 표준 문헌 등.</div>
      </div>
    </div>
  </div>
</div>
</div>

<!-- ── FOOTER ── -->
<footer class="footer">
  <div>
    <div class="footer-l">HealthGuard<span style="color:var(--teal)">Pro</span></div>
    <div style="font-size:12px;color:var(--text3);margin-top:4px;">数字健康产业安全平台 · 디지털 헬스 산업 보안 플랫폼</div>
  </div>
  <div class="footer-r">© 2025 · Digital Health Safety Platform · 경진대회 프로젝트</div>
</footer>

<!-- ── DOWNLOAD BUTTON (fixed) ── -->
<button class="dl-btn" id="dl-btn" onclick="downloadPDF()">
  ⬇ 한국어 PDF 다운로드
</button>

<!-- ── ADD PATIENT MODAL ── -->
<div class="modal-bg" id="modal-bg" onclick="closeModalIfBg(event)">
  <div class="modal">
    <h3>
      <span class="zh-only">➕ 添加新患者</span>
      <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">➕ 신규 환자 추가</span>
    </h3>
    <div class="modal-field">
      <label>
        <span class="zh-only">姓名 / 이름</span>
        <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">이름 / 姓名</span>
      </label>
      <input id="m-name" placeholder="예: 김지수 / 张三">
    </div>
    <div class="modal-field">
      <label>
        <span class="zh-only">年龄 / 나이</span>
        <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">나이</span>
      </label>
      <input id="m-age" type="number" placeholder="45">
    </div>
    <div class="modal-field">
      <label>
        <span class="zh-only">诊断 / 진단</span>
        <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">진단명</span>
      </label>
      <input id="m-diag" placeholder="예: 高血压 / 고혈압">
    </div>
    <div class="modal-field">
      <label>
        <span class="zh-only">风险等级 / 위험 등급</span>
        <span class="kr-only" style="font-family:'Noto Sans KR',sans-serif">위험 등급</span>
      </label>
      <select id="m-risk">
        <option value="low">低 / 저위험</option>
        <option value="mid">中 / 중위험</option>
        <option value="high">高 / 고위험</option>
      </select>
    </div>
    <div class="modal-actions">
      <button class="modal-cancel" onclick="closeModal()">취소 / 取消</button>
      <button class="modal-ok" onclick="addPatient()">추가 / 添加</button>
    </div>
  </div>
</div>

<script>
// ─── Lang ───
function setLang(l) {
  document.body.className = l === 'zh' ? 'show-zh' : 'show-kr';
  document.getElementById('btn-zh').classList.toggle('on', l === 'zh');
  document.getElementById('btn-kr').classList.toggle('on', l === 'kr');
}
function scrollTo(id) {
  document.querySelector(id).scrollIntoView({ behavior:'smooth' });
}

// ─── ECG animation ───
(function() {
  const pts = [], W=280, H=60;
  const pat = [0,0,0,-2,-1,0,0,0,2,20,-18,12,-2,0,0,3,8,-2,0,0];
  let x=0, pi=0, frame=[];
  function gen() {
    frame.push({ x, y: H/2 - (pat[pi % pat.length] * 1.6) });
    pi++; x += 4;
    if (frame.length > W/4) frame.shift();
    const points = frame.map((p,i) => `${i*4},${p.y}`).join(' ');
    document.getElementById('ecg-line').setAttribute('points', points);
    setTimeout(gen, 60);
  }
  gen();
})();

// ─── Patients ───
let patients = [
  { id:'P001', name:'张伟 / 장웨이', age:62, diag:'高血压 / 고혈압', risk:'high', status:'住院 / 입원' },
  { id:'P002', name:'이수진', age:45, diag:'당뇨병 / 糖尿病', risk:'mid', status:'외래 / 门诊' },
  { id:'P003', name:'王芳 / 왕팡', age:38, diag:'心律不齐 / 부정맥', risk:'mid', status:'검사중 / 检查中' },
  { id:'P004', name:'박민준', age:71, diag:'관상동맥질환 / 冠心病', risk:'high', status:'중환자실 / ICU' },
  { id:'P005', name:'刘洋 / 류양', age:29, diag:'轻度贫血 / 경도빈혈', risk:'low', status:'通院 / 통원' },
  { id:'P006', name:'최지영', age:55, diag:'골다공증 / 骨质疏松', risk:'low', status:'추적관찰 / 随访' },
];
let nextId = 7;

function riskBadge(r) {
  const m = { high:['badge-r','高 / 고위험'], mid:['badge-y','中 / 중위험'], low:['badge-g','低 / 저위험'] };
  return `<span class="badge ${m[r][0]}">${m[r][1]}</span>`;
}
function statusBadge(s) { return `<span class="badge badge-b">${s}</span>`; }

function renderPt(list) {
  const tb = document.getElementById('pt-tbody');
  tb.innerHTML = list.length === 0
    ? `<tr><td colspan="7" style="text-align:center;color:var(--text3);padding:32px">无数据 / 데이터 없음</td></tr>`
    : list.map(p => `<tr>
      <td style="font-weight:700;color:var(--blue)">${p.id}</td>
      <td>${p.name}</td>
      <td>${p.age}</td>
      <td>${p.diag}</td>
      <td>${riskBadge(p.risk)}</td>
      <td>${statusBadge(p.status)}</td>
      <td><button class="del-btn" onclick="delPt('${p.id}')">×</button></td>
    </tr>`).join('');
}
function filterPt() {
  const q = document.getElementById('pt-search').value.toLowerCase();
  renderPt(patients.filter(p => p.name.toLowerCase().includes(q) || p.diag.toLowerCase().includes(q) || p.id.toLowerCase().includes(q)));
}
function delPt(id) {
  patients = patients.filter(p => p.id !== id);
  filterPt();
  document.getElementById('s-total').textContent = patients.length.toLocaleString();
}
function openModal() { document.getElementById('modal-bg').classList.add('open'); }
function closeModal() { document.getElementById('modal-bg').classList.remove('open'); }
function closeModalIfBg(e) { if (e.target === document.getElementById('modal-bg')) closeModal(); }
function addPatient() {
  const name = document.getElementById('m-name').value.trim();
  const age = parseInt(document.getElementById('m-age').value);
  const diag = document.getElementById('m-diag').value.trim();
  const risk = document.getElementById('m-risk').value;
  if (!name || !age || !diag) { alert('请填写完整信息 / 모든 항목을 입력해주세요'); return; }
  const id = 'P' + String(nextId++).padStart(3,'0');
  patients.push({ id, name, age, diag, risk, status:'신규 / 新患者' });
  document.getElementById('s-total').textContent = patients.length.toLocaleString();
  closeModal();
  filterPt();
  document.getElementById('m-name').value = '';
  document.getElementById('m-age').value = '';
  document.getElementById('m-diag').value = '';
}
renderPt(patients);

// ─── Alerts ───
const alertData = [
  { id:1, icon:'🚨', color:'var(--red-light)', level:'high', title:'비인가 접근 감지 / 未授权访问检测', desc:'외부 IP 203.0.113.42에서 환자 데이터베이스에 대한 비정상적인 접근이 감지되었습니다. / 检测到来自外部IP 203.0.113.42对患者数据库的异常访问。', time:'오늘 09:32 / 今日 09:32' },
  { id:2, icon:'⚠️', color:'var(--yellow-light)', level:'mid', title:'데이터 전송 이상 / 数据传输异常', desc:'환자 기록 전송 중 패킷 손실률이 임계값(5%)을 초과했습니다. / 患者记录传输中发现数据包丢失率超过阈值(5%)。', time:'오늘 11:15 / 今日 11:15' },
  { id:3, icon:'🔐', color:'var(--blue-light)', level:'info', title:'인증서 만료 임박 / 证书即将到期', desc:'TLS 인증서가 7일 후 만료됩니다. 갱신이 필요합니다. / TLS证书将在7天后到期，需要及时续签。', time:'오늘 13:00 / 今日 13:00' },
  { id:4, icon:'💊', color:'var(--teal-light)', level:'info', title:'약물 상호작용 경고 / 药物相互作用警告', desc:'P004 환자의 처방에서 잠재적 약물 상호작용이 감지되었습니다. 확인이 필요합니다. / P004患者处方中发现潜在药物相互作用，需医生确认。', time:'오늘 14:22 / 今日 14:22' },
  { id:5, icon:'🔴', color:'var(--red-light)', level:'high', title:'DDoS 공격 감지 / DDoS攻击检测', desc:'분당 비정상적으로 높은 API 호출이 감지되었습니다. 자동 차단이 활성화되었습니다. / 检测到每分钟异常高频API调用，自动封锁已激活。', time:'오늘 15:45 / 今日 15:45' },
];
function renderAlerts() {
  document.getElementById('alert-list').innerHTML = alertData.map(a => `
    <div class="alert-item" id="alert-${a.id}" style="border-left:3px solid ${a.level==='high'?'var(--red)':a.level==='mid'?'var(--yellow)':'var(--blue)'}">
      <div class="alert-icon" style="background:${a.color}">${a.icon}</div>
      <div style="flex:1">
        <div class="alert-title">${a.title}</div>
        <div class="alert-desc">${a.desc}</div>
        <div class="alert-time">${a.time}</div>
      </div>
      <button class="alert-dismiss" onclick="dismissAlert(${a.id})" title="닫기 / 关闭">×</button>
    </div>`).join('');
}
function dismissAlert(id) {
  const el = document.getElementById('alert-'+id);
  el.style.opacity = '0'; el.style.transform = 'translateX(20px)'; el.style.transition = '.3s';
  setTimeout(() => el.remove(), 300);
  const idx = alertData.findIndex(a => a.id === id);
  if (idx !== -1) alertData.splice(idx, 1);
  const cnt = parseInt(document.getElementById('s-alerts').textContent);
  document.getElementById('s-alerts').textContent = Math.max(0, cnt - 1);
}
renderAlerts();

// ─── Risk Assessment ───
function runAssess() {
  const age = parseInt(document.getElementById('inp-age').value) || 0;
  const bp = parseInt(document.getElementById('inp-bp').value) || 0;
  const bmi = parseFloat(document.getElementById('inp-bmi').value) || 0;
  const smoke = parseInt(document.getElementById('inp-smoke').value);
  const dm = parseInt(document.getElementById('inp-dm').value);
  const sex = document.getElementById('inp-sex').value;

  if (!age || !bp || !bmi) { alert('请填写所有必填项 / 모든 항목을 입력해주세요'); return; }

  let score = 0;
  if (age > 60) score += 25; else if (age > 45) score += 15; else if (age > 35) score += 8;
  if (bp >= 160) score += 30; else if (bp >= 140) score += 20; else if (bp >= 130) score += 10;
  if (bmi >= 30) score += 20; else if (bmi >= 25) score += 10;
  if (smoke) score += 20;
  if (dm) score += 25;
  if (sex === 'm') score += 5;

  const isZh = document.body.className === 'show-zh';
  let levelText, tips, color;
  if (score >= 70) {
    levelText = isZh ? '🔴 高风险 / 고위험' : '🔴 고위험 (高风险)';
    tips = isZh
      ? '建议立即就医，进行全面心血管检查。严格控制血压、血糖，戒烟，调整饮食结构，规律服药，每月复诊。'
      : '즉시 의료기관을 방문하여 종합 심혈관 검사를 받으세요. 혈압·혈당 엄격 관리, 금연, 식단 조절, 규칙적 투약, 월 1회 정기검진이 필요합니다.';
    color = '#fdecea';
  } else if (score >= 40) {
    levelText = isZh ? '🟡 中风险 / 중위험' : '🟡 중위험 (中风险)';
    tips = isZh
      ? '建议每半年进行体检，注意控制体重和血压。适量运动，减少高脂肪高盐饮食，定期监测血糖。'
      : '6개월마다 건강검진을 받으세요. 체중과 혈압 관리에 주의하고, 적당한 운동과 저지방 저염 식단을 유지하세요.';
    color = '#fff8ec';
  } else {
    levelText = isZh ? '🟢 低风险 / 저위험' : '🟢 저위험 (低风险)';
    tips = isZh
      ? '目前健康状况良好！保持规律运动和均衡饮食，每年进行一次常规体检即可。'
      : '현재 건강 상태가 양호합니다! 규칙적인 운동과 균형 잡힌 식사를 유지하고, 연 1회 일반 건강검진을 받으세요.';
    color = '#e6f7f0';
  }

  const cvRisk = Math.min(100, Math.round(score * 0.85));
  const dmRisk = Math.min(100, Math.round((dm ? 60 : 20) + (bmi > 27 ? 15 : 0) + (age > 50 ? 10 : 0)));
  const bpRisk = Math.min(100, Math.round(bp > 140 ? 75 : bp > 130 ? 45 : 20));

  const rb = document.getElementById('result-box');
  rb.style.background = `linear-gradient(135deg, ${color}, #fff)`;
  document.getElementById('result-level').textContent = levelText + (isZh ? `（综合评分: ${score}分）` : `（종합 점수: ${score}점）`);
  document.getElementById('result-tips').textContent = tips;
  document.getElementById('result-bars').innerHTML = `
    <div class="rbar-row"><span class="rbar-lbl">${isZh?'心血管风险':'심혈관 위험'}</span><div class="rbar-wrap"><div class="rbar-fill" style="width:0;background:var(--red)" data-w="${cvRisk}%"></div></div><span style="min-width:36px;text-align:right;font-weight:700">${cvRisk}%</span></div>
    <div class="rbar-row"><span class="rbar-lbl">${isZh?'糖尿病风险':'당뇨 위험'}</span><div class="rbar-wrap"><div class="rbar-fill" style="width:0;background:var(--orange)" data-w="${dmRisk}%"></div></div><span style="min-width:36px;text-align:right;font-weight:700">${dmRisk}%</span></div>
    <div class="rbar-row"><span class="rbar-lbl">${isZh?'高血压风险':'고혈압 위험'}</span><div class="rbar-wrap"><div class="rbar-fill" style="width:0;background:var(--yellow)" data-w="${bpRisk}%"></div></div><span style="min-width:36px;text-align:right;font-weight:700">${bpRisk}%</span></div>
  `;
  rb.classList.add('show');
  // animate bars
  setTimeout(() => {
    rb.querySelectorAll('.rbar-fill').forEach(b => { b.style.width = b.dataset.w; });
  }, 50);
}

// ─── PDF Download ───
function downloadPDF() {
  const btn = document.getElementById('dl-btn');
  btn.disabled = true;
  btn.textContent = '⏳ 생성 중...';

  setTimeout(() => {
    try {
      const { jsPDF } = window.jspdf;
      const doc = new jsPDF('p','mm','a4');
      const W = 210, M = 18, CW = W - M * 2;

      function addPage(bg) {
        doc.addPage();
        if (bg) { doc.setFillColor(bg[0],bg[1],bg[2]); doc.rect(0,0,W,297,'F'); }
      }

      // helper
      const fc = (r,g,b) => doc.setFillColor(r,g,b);
      const tc = (r,g,b) => doc.setTextColor(r,g,b);
      const dc = (r,g,b) => doc.setDrawColor(r,g,b);

      // ── COVER ──
      fc(26,107,255); doc.rect(0,0,W,12,'F');
      fc(244,247,252); doc.rect(0,12,W,285,'F');
      tc(255,255,255); doc.setFont('helvetica','bold'); doc.setFontSize(10);
      doc.text('HEALTHGUARD PRO · DIGITAL HEALTH INDUSTRY SECURITY PLATFORM', M, 8);

      tc(26,107,255); doc.setFontSize(38); doc.setFont('helvetica','bold');
      doc.text('HealthGuard Pro', M, 56);
      tc(14,181,160); doc.setFontSize(22);
      doc.text('\ub514\uc9c0\ud138 \ud5ec\uc2a4 \uc0b0\uc5c5 \ubcf4\uc548 \ud50c\ub7ab\ud3fc', M, 72);
      tc(100,120,150); doc.setFontSize(13); doc.setFont('helvetica','normal');
      doc.text('Digital Health Industry Security Platform', M, 84);
      doc.text('\ub514\uc9c0\ud138 \ud5ec\uc2a4\ucF00\uc5b4 \uc0b0\uc5c5 \ubcf4\uc548 \ud1b5\ud569 \uad00\ub9ac \uc2dc\uc2a4\ud15c', M, 94);

      // info box
      fc(255,255,255); dc(221,227,238); doc.setLineWidth(.5);
      doc.roundedRect(M,106,CW,56,3,3,'FD');
      tc(26,107,255); doc.setFontSize(8); doc.setFont('helvetica','bold');
      doc.text('PROJECT INFORMATION', M+8, 118);
      tc(74,85,104); doc.setFont('helvetica','normal'); doc.setFontSize(10.5);
      const infos = [
        '\uacfc\uc81c\uba85: \ub514\uc9c0\ud138 \ud5ec\uc2a4 \uc758\ub8cc (\uc8fc\uc81c: \uc0b0\uc5c5\ubcf4\uc548 | \ud50c\ub7ab\ud3fc\uac1c\ubc1c \uacbd\uc9c4\ub300\ud68c)',
        '\uae30\uc220 \uc2a4\ud0dd: HTML5 / CSS3 / JavaScript / jsPDF CDN',
        '\ud45c\uc900 \uc900\uc218: HIPAA · GDPR · \ud55c\uad6d \uac1c\uc778\uc815\ubcf4\ubcf4\ud638\ubc95(\ud53c\ud30c)',
        '\ubc30\ud3ec \ubc29\uc2dd: GitHub Pages \ub2e8\uc77c \ud30c\uc77c \uc544\ud0a4\ud14d\uccb8'
      ];
      infos.forEach((t,i) => doc.text(t, M+8, 128 + i*9));

      tc(150,160,180); doc.setFontSize(9);
      doc.text('2025 \uc5f0\ub3c4 \ud50c\ub7ab\ud3fc \uac1c\ubc1c \uacbd\uc9c4\ub300\ud68c | Digital Health Safety Platform', M, 280);
      fc(26,107,255); doc.rect(0,292,W,5,'F');

      // ── SECTION BUILDER ──
      function sec(num, color, titleKr, titleZh, items) {
        addPage();
        // header bar
        const rgb = color;
        fc(rgb[0],rgb[1],rgb[2]); doc.rect(0,0,W,44,'F');
        tc(255,255,255); doc.setFontSize(48); doc.setFont('helvetica','bold');
        doc.text('0'+num, M, 36);
        doc.setFontSize(19); doc.text(titleKr, 52, 26);
        doc.setFontSize(11); doc.setFont('helvetica','normal');
        doc.text(titleZh, 52, 36);
        // page num
        tc(180,190,210); doc.setFontSize(8);
        doc.text('- '+(num+1)+' -', W/2, 291, {align:'center'});

        let y = 58;
        items.forEach(item => {
          if (y > 265) {
            addPage([249,251,254]);
            y = 20;
          }
          if (item.type === 'h') {
            tc(rgb[0],rgb[1],rgb[2]); doc.setFontSize(12); doc.setFont('helvetica','bold');
            doc.text(item.t, M, y); y += 3;
            fc(rgb[0],rgb[1],rgb[2]); doc.rect(M, y, 28, .8, 'F');
            y += 8;
          } else if (item.type === 't') {
            tc(60,80,110); doc.setFontSize(10); doc.setFont('helvetica','normal');
            const lines = doc.splitTextToSize(item.t, CW);
            doc.text(lines, M, y); y += lines.length * 5.2 + 4;
          } else if (item.type === 'b') {
            tc(rgb[0],rgb[1],rgb[2]); doc.setFontSize(11); doc.setFont('helvetica','bold');
            doc.text('\u25B8', M, y);
            tc(50,70,100); doc.setFont('helvetica','normal'); doc.setFontSize(10);
            const lines = doc.splitTextToSize(item.t, CW-7);
            doc.text(lines, M+7, y); y += lines.length * 5.2 + 3;
          } else if (item.type === 'card') {
            fc(255,255,255); dc(221,227,238); doc.setLineWidth(.4);
            const blines = doc.splitTextToSize(item.b, CW-14);
            const h = 14 + blines.length * 5;
            doc.roundedRect(M, y-3, CW, h, 2, 2, 'FD');
            tc(rgb[0],rgb[1],rgb[2]); doc.setFontSize(9); doc.setFont('helvetica','bold');
            doc.text(item.l, M+6, y+4);
            tc(70,90,120); doc.setFont('helvetica','normal'); doc.setFontSize(9.5);
            doc.text(blines, M+6, y+11); y += h + 8;
          } else if (item.type === 'sp') { y += item.v || 8; }
        });
      }

      // PAGE 2 — 설계 방법
      sec(1,[26,107,255],
        '\uc6f9\uc0ac\uc774\ud2b8 \uc124\uacc4 \ubc0f \uac1c\ubc1c \ubc29\ubc95',
        '\u7F51\u7AD9\u8BBE\u8BA1\u4E0E\u5F00\u5019\u65B9\u6CD5', [
        {type:'h',t:'1.1 \uc544\ud0a4\ud14d\uccb8 \uc124\uacc4 \uc6d0\uce59'},
        {type:'b',t:'\ub2e8\uc77c \ud30c\uc77c HTML \uc544\ud0a4\ud14d\uccb8: \ubaa8\ub4e0 CSS\uc640 JavaScript\ub97c \ud558\ub098\uc758 HTML \ud30c\uc77c\uc5d0 \ud1b5\ud569\ud558\uc5ec GitHub Pages\uc5d0\uc11c \uc11c\ubc84 \uc5c6\uc774 \uc989\uc2dc \ubc30\ud3ec \uac00\ub2a5.'},
        {type:'b',t:'\ubc18\uc751\ud615 \ub514\uc790\uc778: CSS Grid, Flexbox, \ubbf8\ub514\uc5b4\ucffc\ub9ac\ub97c \ud65c\uc6a9\ud558\uc5ec PC/\ud0dc\ube14\ub9bf/\ubaa8\ubc14\uc77c \ub4f1 \ub2e4\uc591\ud55c \ud654\uba74 \ud06c\uae30\uc5d0 \uc801\uc751.'},
        {type:'b',t:'CSS \ubcc0\uc218 \ud14c\ub9c8 \uc2dc\uc2a4\ud15c: :root \ubcc0\uc218\ub85c \uc77c\uad00\ub41c \uc0c9\uc0c1, \ud3f0\ud2b8, \uac04\uaca9 \uc2a4\ud0c0\uc77c\uc744 \uc911\uc559\ud654 \uad00\ub9ac.'},
        {type:'b',t:'CDN \uc678\ubd80 \ub77c\uc774\ube0c\ub7ec\ub9ac: jsPDF(PDF \uc0dd\uc131), Google Fonts(CJK \ud3f0\ud2b8)\ub97c CDN\uc73c\ub85c \ub85c\ub4dc\ud558\uc5ec \ub85c\ucef4 \uc124\uce58 \ubd88\ud544\uc694.'},
        {type:'sp',v:6},
        {type:'h',t:'1.2 \uc8fc\uc694 \uae30\uc220 \uc2a4\ud0dd'},
        {type:'card',l:'HTML5',b:'\uc2dc\ub9e8\ud2f1 \ud0dc\uadf8(section/nav/article \ub4f1)\uacfc \uc811\uadfc\uc131 \ud45c\uc900\uc744 \uc900\uc218\ud558\uc5ec \uad6c\uc870\uc801 \ucf58\ud150\uce20 \uc791\uc131.'},
        {type:'card',l:'CSS3',b:'CSS \ubcc0\uc218, Flexbox/Grid \ub808\uc774\uc544\uc6c3, \ud0a4\ud504\ub808\uc784 \uc560\ub2c8\uba54\uc774\uc158, backdrop-filter \uc720\ub9ac \ud6a8\uacfc, \ubc18\uc751\ud615 \ubbf8\ub514\uc5b4\ucffc\ub9ac \uc801\uc6a9.'},
        {type:'card',l:'Vanilla JavaScript',b:'\ud504\ub808\uc784\uc6cc\ud06c \ubbf8\uc0ac\uc6a9\uc73c\ub85c \ucf54\ub4dc\ub97c \uacbd\ub7c9\ud654. DOM \uc870\uc791, \uc0c1\ud0dc \uad00\ub9ac, \uc0ac\uc6a9\uc790 \uc785\ub825 \ucc98\ub9ac, \uc5d4\uc9c0\ub2c8\uc5b4\ub9c1 \ub85c\uc9c1 \uc9c1\uc811 \uad6c\ud604.'},
        {type:'sp',v:6},
        {type:'h',t:'1.3 \ubcf4\uc548 \uc124\uacc4 \ubc29\ub825'},
        {type:'t',t:'AES-256 \uc554\ud638\ud654 \ud45c\uc900\uc73c\ub85c \ud658\uc790 \ub370\uc774\ud130\ub97c \ubcf4\ud638\ud558\uba70, JWT + OAuth 2.0 \uae30\ubc18 \uc778\uc99d \uccb4\uacc4\ub97c \uc801\uc6a9\ud569\ub2c8\ub2e4. HTTPS/TLS 1.3\uc73c\ub85c \ubaa8\ub4e0 \ud1b5\uc2e0\uc744 \uc554\ud638\ud654\ud558\uba70, \uc2e4\uc2dc\uac04 \ubcf4\uc548 \ubaa8\ub2c8\ud130\ub9c1\uc73c\ub85c \uc774\uc0c1 \ud560\ub3d9\uc744 0.3\ucd08 \ub0b4 \uac10\uc9c0\ud569\ub2c8\ub2e4.'},
        {type:'sp',v:6},
        {type:'h',t:'1.4 \ubc30\ud3ec \ud504\ub85c\uc138\uc2a4'},
        {type:'t',t:'GitHub Pages \uc815\uc801 \ud638\uc2a4\ud305\uc73c\ub85c \ubcd1\ub3c4 \uc11c\ubc84 \uc5c6\uc774 \uc81c\ub85c\ube44\uc6a9 \ubc30\ud3ec. iPad\uc5d0\uc11c\ub3c4 \uc6d0\ud65c\ud55c \ud3b8\uc9d1\uacfc \uc5c5\ub85c\ub4dc\uac00 \uac00\ub2a5\ud558\uba70, main \ube0c\ub79c\uce58 push \uc2dc \uc790\ub3d9 \ubc30\ud3ec\ub429\ub2c8\ub2e4.'}
      ]);

      // PAGE 3 — 주요 기능
      sec(2,[14,181,160],
        '\uc6f9\uc0ac\uc774\ud2b8 \uc8fc\uc694 \uae30\ub2a5 \uc18c\uac1c',
        '\u7F51\u7AD9\u4E3B\u8981\u529F\u80FD\u4ECB\u7ECD', [
        {type:'h',t:'\uae30\ub2a5 1: \uac74\uac15 \uc704\ud5d8 \uc2a4\ub9c8\ud2b8 \ud3c9\uac00\uae30'},
        {type:'t',t:'\ub098\uc774, \uc131\ubcc4, \uc218\ucdb5\uae30\ud608\uc555, BMI, \ud761\uc5f0\uc0ac, \ub2f9\ub1e8\ubcd1\ub825 \ub4f1 6\uac00\uc9c0 \uc9c0\ud45c\ub97c \uc785\ub825\ud558\uba74 \uc2ec\ud601\uad00, \ub2f9\ub1e8\ubcd1, \uace0\ud608\uc555 \uc704\ud5d8\ub3c4\ub97c \uc989\uc2dc \uacc4\uc0b0\ud569\ub2c8\ub2e4. \uc800/\uc911/\uace0\uc704\ud5d8 3\ub2e8\uacc4\ub85c \ubd84\ub958\ud558\uba70 \ub9de\uce68\ud615 \uac74\uac15 \uc870\uc5b8\uc744 \uc81c\uacf5\ud569\ub2c8\ub2e4.'},
        {type:'sp',v:5},
        {type:'h',t:'\uae30\ub2a5 2: \ud658\uc790 \ub370\uc774\ud130 \ubcf4\uc548 \uad00\ub9ac'},
        {type:'t',t:'\ud658\uc790 \ub9aa\ubaa9 \uc2dc\uac01\ud654, \uc2e4\uc2dc\uac04 \uac80\uc0c9 \ud544\ud130, \uc2e0\uaddc \ud658\uc790 \ucd94\uac00 \ubaa8\ub2ec, \ub808\ucf54\ub4dc \uc0ad\uc81c \uae30\ub2a5\uc744 \uc81c\uacf5\ud569\ub2c8\ub2e4. HIPAA \ubcf4\uc548 \uae30\uc900\uc744 \uc900\uc218\ud558\uba70 \ubaa8\ub4e0 \ub370\uc774\ud130 \uc811\uadfc\uc774 \ub85c\uae45\ub429\ub2c8\ub2e4.'},
        {type:'sp',v:5},
        {type:'h',t:'\uae30\ub2a5 3: \uc2e4\uc2dc\uac04 \ubcf4\uc548 \uacbd\uace0 \uc13c\ud130'},
        {type:'t',t:'\ube44\uc778\uac00 \uc811\uadfc, \ub370\uc774\ud130 \uc720\ucd9c \uc704\ud5d8, TLS \uc778\uc99d\uc11c \ub9cc\ub8cc \uc784\ubc15, \uc57d\ubb3c \uc0c1\ud638\uc791\uc6a9 \uacbd\uace0, DDoS \uacf5\uaca9 \uac10\uc9c0 \ub4f1 5\uac00\uc9c0 \ubcf4\uc548 \uacbd\uace0\ub97c \ud45c\uc2dc\ud569\ub2c8\ub2e4. \uac01 \uacbd\uace0\ub294 \xd7 \ubc84\ud2bc\uc73c\ub85c \ub2e8\ub3c5 \uc0ad\uc81c\ud560 \uc218 \uc788\uc2b5\ub2c8\ub2e4.'},
        {type:'sp',v:5},
        {type:'h',t:'\uae30\ub2a5 4: \uc758\ub8cc \ub370\uc774\ud130 \ud1b5\uacc4 \ub300\uc2dc\ubcf4\ub4dc'},
        {type:'t',t:'\ub4f1\ub85d \ud658\uc790 \uc218, \uace0\uc704\ud5d8 \ud658\uc790 \ube44\uc728, HIPAA \ucca0\uc758 \uc810\uc218, \uc624\ub298 \ubcf4\uc548 \uacbd\uace0 \uc218, \uc2dc\uc2a4\ud15c \uac00\uc6a9\ub960, \uc9c4\ub8cc \uacb1\uc218 \ub4f1 6\uac00\uc9c0 \ud575\uc2ec \uc9c0\ud45c\ub97c \uc9c4\ub3c4\ub9c9\ub300\ub85c \uc2dc\uac01\ud654\ud569\ub2c8\ub2e4.'},
        {type:'sp',v:5},
        {type:'h',t:'\uae30\ub2a5 5: \uc911\ud55c \uc774\uc911 \uc5b8\uc5b4 \uc2a4\uc704\uce58'},
        {type:'t',t:'\uc6b0\uce21 \uc0c1\ub2e8 \uc5b8\uc5b4 \uc804\ud658 \ubc84\ud2bc\uc73c\ub85c \uc911\uad6d\uc5b4/\ud55c\uad6d\uc5b4\ub97c \uc989\uc2dc \uc804\ud658\ud569\ub2c8\ub2e4. Noto Sans SC/KR \ud3f0\ud2b8\ub97c \ud65c\uc6a9\ud558\uc5ec \ud55c\uc2dc \uc758\ub8cc \uc885\uc0ac\uc790 \ub300\uc0c1\uc758 \ubb34\uc7a5\uc560 \uc0ac\uc6a9 \ud658\uacbd\uc744 \uc81c\uacf5\ud569\ub2c8\ub2e4.'},
        {type:'sp',v:5},
        {type:'h',t:'\uae30\ub2a5 6: \uc6d0\ud074\ub9ad \ud55c\uad6d\uc5b4 PDF \ub0b4\ubcf4\ub0b4\uae30'},
        {type:'t',t:'\uc6b0\uce21 \ud558\ub2e8 \uace0\uc815 \ub2e4\uc6b4\ub85c\ub4dc \ubc84\ud2bc\uc744 \ud074\ub9ad\ud558\uba74 jsPDF \ub77c\uc774\ube0c\ub7ec\ub9ac\ub97c \ud65c\uc6a9\ud574 \ud074\ub77c\uc774\uc5b8\ud2b8 \uce21\uc5d0\uc11c \uc9c1\uc811 4\ud398\uc774\uc9c0 \ud55c\uad6d\uc5b4 PDF\ub97c \uc0dd\uc131\ud569\ub2c8\ub2e4. \uc11c\ubc84 \ud1b5\uc2e0 \uc5c6\uc774 \uc99d\uac04 \ub3d9\uc791\ud569\ub2c8\ub2e4.'}
      ]);

      // PAGE 4 — 기대 효과
      sec(3,[255,107,53],
        '\ud504\ub85c\uc81d\ud2b8 \uae30\ub300 \ud6a8\uacfc \ubc0f \uc751\uc6a9 \uac00\uce58',
        '\u9879\u76EE\u9884\u671F\u6548\u679C\u4E0E\u5E94\u7528\u4EF7\u5024', [
        {type:'h',t:'3.1 \ubcf4\uc548\uc131 \uac15\ud654 \ud6a8\uacfc'},
        {type:'b',t:'\uc758\ub8cc \ub370\uc774\ud130 \uce68\ud574 \uc704\ud5d8 \ucd5c\ub300 90% \uac10\uc18c: AES-256 \uc554\ud638\ud654\uc640 \ub2e4\uce35 \uc778\uc99d\uc73c\ub85c \ubd88\ubc95 \uc811\uadfc \ucc28\ub2e8.'},
        {type:'b',t:'0.3\ucd08 \ub0b4 \uc2e4\uc2dc\uac04 \uc704\ud611 \uac10\uc9c0 \ubc0f \uc790\ub3d9 \ucc28\ub2e8 \uc2dc\uc2a4\ud15c\uc73c\ub85c \ubcf4\uc548 \uc0ac\uace0 \uc608\ubc29.'},
        {type:'b',t:'99.9% \uc2dc\uc2a4\ud15c \uac00\uc6a9\ub960 \uc720\uc9c0\ub85c \uc758\ub8cc \uc11c\ube44\uc2a4 \uc911\ub2e8 \uc5c6\uc774 \uc548\uc815\uc801 \uc6b4\uc601.'},
        {type:'sp',v:6},
        {type:'h',t:'3.2 \ucde8\uc5c5 \ud6a8\uc728\ud654 \ud6a8\uacfc'},
        {type:'b',t:'\uc790\ub3d9 \ucde8\uc5c5 \uac10\uc0ac\ub85c \uc218\ub3d9 \uac80\ud1a0 \uc5c5\ubb34 60% \uc808\uac10 \uc608\uc0c1.'},
        {type:'b',t:'AI \uac74\uac15 \uc704\ud5d8 \ud3c9\uac00\uae30\ub85c \uc870\uae30 \uc9c4\ub2e8\uc728 35% \ud5a5\uc0c1 \uae30\ub300.'},
        {type:'b',t:'\ud1b5\ud569 \ub300\uc2dc\ubcf4\ub4dc\ub85c \uc758\ub8cc\uc9c4\uc758 \uc758\uc0ac\uacb0\uc815 \uc18c\uc694 \uc2dc\uac04 40% \ub2e8\ucd95.'},
        {type:'sp',v:6},
        {type:'h',t:'3.3 \uc0ac\ud68c\uc801 \uac00\uce58'},
        {type:'t',t:'\ud55c\uad6d \ub514\uc9c0\ud138 \ud5ec\uc2a4\ucF00\uc5b4 \uc2dc\uc7a5\uc740 \uc5f0\ud3c9\uade0 15%\uc529 \uc131\uc7a5 \uc911\uc785\ub2c8\ub2e4. \uc548\uc804\ud55c \uc758\ub8cc\ub370\uc774\ud130 \uad00\ub9ac\ub294 \uc2e0\ub8b0 \uad6c\ucd95\uc758 \ud575\uc2ec\uc785\ub2c8\ub2e4. \uc911\uc18c\ud615 \ubcd1\uc6d0\ubd80\ud130 \ub300\ud615 \uc758\ub8cc\uae30\uad00\uae4c\uc9c0 \ud655\uc7a5 \uac00\ub2a5\ud558\uba70 API \uc9c0\ud5a5 \uc544\ud0a4\ud14d\uccb8\ub85c EMR, \uc6d0\uaca9\uc9c4\ub8cc, IoT \uc758\ub8cc\uae30\uae30\uc640 \uc6d0\ud65c\ud55c \ud1b5\ud569\uc774 \uac00\ub2a5\ud569\ub2c8\ub2e4.'},
        {type:'sp',v:6},
        {type:'h',t:'3.4 \uad50\uc721\uc801 \ud65c\uc6a9 \uac00\uce58'},
        {type:'t',t:'\uc774 \ud50c\ub7ab\ud3fc\uc740 \ub514\uc9c0\ud138 \ud5ec\uc2a4\ucF00\uc5b4 \ubcf4\uc548 \uc2e4\uc2b5 \ub3c4\uad6c\ub85c\ub3c4 \ud65c\uc6a9 \uac00\ub2a5\ud569\ub2c8\ub2e4. \ud559\uc0dd\ub4e4\uc774 \uc2e4\uc81c \ubcf4\uc548 \ub300\uc2dc\ubcf4\ub4dc\ub97c \ud1b5\ud574 \ub9ac\uc2a4\ud06c \uad00\ub9ac, \ub370\uc774\ud130 \uc554\ud638\ud654, \ucde8\uc5c5 \uac10\uc0ac \ub4f1\uc744 \uc9c1\uad00\uc801\uc73c\ub85c \uc2b5\ub4dd\ud560 \uc218 \uc788\uc2b5\ub2c8\ub2e4.'}
      ]);

      // PAGE 5 — 보충 설명
      sec(4,[46,158,107],
        '\uae30\ud0c0 \uad00\ub828 \ubcf4\ucda9 \uc124\uba85',
        '\u5176\u4F59\u76F8\u5173\u8865\u5145\u8BF4\u660E', [
        {type:'h',t:'4.1 \uae30\uc220\uc801 \ud55c\uacc4'},
        {type:'b',t:'\ud50c\ub860\ud2b8\uc5d4\ub4dc\ub9cc\uc758 \uad6c\uc870\ub85c \uc2e4\uc81c \uc11c\ubc84 \uc5f0\ub3d9 \uc2dc \uc778\uc99d \uc11c\ubc84\uc640 \ub370\uc774\ud130\ubca0\uc774\uc2a4 \ucd94\uac00 \ud1b5\ud569 \ud544\uc694.'},
        {type:'b',t:'jsPDF\uc758 \ud55c\uae00 \ub80c\ub354\ub9c1 \ud55c\uacc4\ub85c \ud56d\ud5a5\ud6c4 \uc720\ub2c8\ucf54\ub4dc \ucf54\ub9ac\uc548 \ud3f0\ud2b8 \uc778\ub7a8 \uc5c5\uadf8\ub808\uc774\ub4dc \uad8c\uc7a5.'},
        {type:'b',t:'\ub300\uc6a9\ub7c9 \uc758\ub8cc\ub370\uc774\ud130 \ucc98\ub9ac\ub97c \uc704\ud55c \ubd84\uc0b0 \uce90\uc2dc \ubc0f DB \ud074\ub7ec\uc2a4\ud130\ub9c1 \ucd94\ud6c4 \ucd94\uac00 \uc608\uc815.'},
        {type:'sp',v:6},
        {type:'h',t:'4.2 \ucc38\uace0 \ud45c\uc900 \ubc0f \uc785\ubc95'},
        {type:'card',l:'HIPAA (미국)',b:'환자 의료 정보 보호 및 이동성에 관한 법률. 의료 데이터의 기밀성, 무결성, 가용성 보장 규정.'},
        {type:'card',l:'한국 개인정보보호법 (피파)',b:'개인정보의 수집·이용·제공에 관한 기본 원칙과 정보주체의 권리를 규정하는 한국 주요 개인정보 보호 법률.'},
        {type:'card',l:'ISO/IEC 27001',b:'정보 보안 관리 시스템(ISMS) 국제 표준. 조직의 정보 보안 리스크 관리 체계 규정.'},
        {type:'sp',v:6},
        {type:'h',t:'4.3 \ud5a5\ud6c4 \uac1c\uc120 \uacc4\ud68d'},
        {type:'b',t:'Node.js/Python \ubc31\uc5d4\ub4dc \ub3c4\uc785\uc73c\ub85c \uc2e4\uc2dc\uac04 \ub370\uc774\ud130 \uc2e4\uc81c \uc5f0\ub3d9 \ubc0f \uc554\ud638\ud654 \uc801\uc6a9.'},
        {type:'b',t:'AI/ML \ubaa8\ub378 \uace0\ub3c4\ud654\ub85c \uac1c\uc778\ubcc4 \ub9de\ucda4 \ud5ec\uc2a4\ucF00\uc5b4 \uad8c\uace0 \uae30\ub2a5 \uad6c\ud604.'},
        {type:'b',t:'\ubaa8\ubc14\uc77c \uc571 \ubc84\uc804 \uac1c\ubc1c\ub85c \uc2a4\ub9c8\ud2b8\ud3f0 \uc218\uc2e0 \ubc0f \uc6e8\uc5b4\ub7ec\ube14 \uae30\uae30 \ud1b5\ud569 \ud655\uc7a5.'},
        {type:'sp',v:6},
        {type:'h',t:'4.4 \uacbd\uc9c4\ub300\ud68c \ud504\ub85c\uc81d\ud2b8 \uc120\uc5b8'},
        {type:'t',t:'\ubcf8 \ud504\ub85c\uc81d\ud2b8\ub294 \ub514\uc9c0\ud138 \ud5ec\uc2a4 \uc758\ub8cc (\uc8fc\uc81c: \uc0b0\uc5c5 \ubcf4\uc548 | \ud50c\ub7ab\ud3fc \uac1c\ubc1c \uacbd\uc9c4\ub300\ud68c)\ub97c \uc704\ud574 \uc81c\uc791\ub41c \ud559\uc2b5 \ubaa9\uc801\uc758 \uc6f9\uc0ac\uc774\ud2b8\uc785\ub2c8\ub2e4. \ubaa8\ub4e0 \ud658\uc790 \ub370\uc774\ud130\ub294 \uac00\uc0c1\uc758 \uc608\uc2dc \ub370\uc774\ud130\uc774\uba70 \uc2e4\uc81c \ud658\uc790 \uc815\ubcf4\ub97c \ud3ec\ud568\ud558\uc9c0 \uc54a\uc2b5\ub2c8\ub2e4.'}
      ]);

      doc.save('HealthGuardPro_\ud55c\uad6d\uc5b4_\ubb38\uc11c.pdf');
    } catch(e) {
      alert('PDF 오류: ' + e.message);
      console.error(e);
    }
    btn.disabled = false;
    btn.innerHTML = '⬇ 한국어 PDF 다운로드';
  }, 200);
}
</script>
</body>
</html>
