<!DOCTYPE html>
<html lang="zh">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DigiHealth Guard | 数字健康产业安全平台</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&family=Noto+Sans+KR:wght@300;400;500;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
  :root {
    --bg: #050c1a;
    --surface: #0a1628;
    --card: #0f1e35;
    --border: #1a3050;
    --accent: #00d4ff;
    --accent2: #00ff9d;
    --accent3: #ff6b35;
    --text: #e8f4ff;
    --muted: #7a9ab8;
    --danger: #ff4757;
    --warn: #ffa502;
    --success: #2ed573;
    --font-zh: 'Noto Sans SC', sans-serif;
    --font-kr: 'Noto Sans KR', sans-serif;
    --font-mono: 'Space Mono', monospace;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-zh);
    overflow-x: hidden;
    scroll-behavior: smooth;
  }

  /* ─── ANIMATED GRID BG ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* ─── FLOATING PARTICLES ─── */
  .particle {
    position: fixed;
    border-radius: 50%;
    pointer-events: none;
    animation: float linear infinite;
    opacity: 0;
  }
  @keyframes float {
    0%   { transform: translateY(100vh) scale(0); opacity: 0; }
    10%  { opacity: .6; }
    90%  { opacity: .3; }
    100% { transform: translateY(-10vh) scale(1); opacity: 0; }
  }

  /* ─── LANGUAGE TOGGLE ─── */
  .lang-bar {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    background: rgba(5,12,26,.9);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 32px;
  }
  .brand {
    font-family: var(--font-mono);
    font-size: 14px;
    color: var(--accent);
    letter-spacing: 2px;
  }
  .brand span { color: var(--accent2); }
  .nav-links {
    display: flex;
    gap: 24px;
    list-style: none;
  }
  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 13px;
    letter-spacing: 1px;
    transition: color .2s;
  }
  .nav-links a:hover { color: var(--accent); }
  .lang-toggle {
    display: flex;
    gap: 6px;
  }
  .lang-btn {
    background: none;
    border: 1px solid var(--border);
    color: var(--muted);
    padding: 4px 14px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 12px;
    font-family: var(--font-mono);
    letter-spacing: 1px;
    transition: all .2s;
  }
  .lang-btn.active {
    background: var(--accent);
    border-color: var(--accent);
    color: var(--bg);
    font-weight: 700;
  }

  /* ─── HERO ─── */
  .hero {
    position: relative;
    z-index: 1;
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 8% 80px;
  }
  .hero-inner {
    max-width: 1100px;
    width: 100%;
  }
  .hero-tag {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--accent2);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .hero-tag::before {
    content: '';
    width: 30px; height: 1px;
    background: var(--accent2);
  }
  .hero h1 {
    font-size: clamp(36px, 5vw, 72px);
    font-weight: 700;
    line-height: 1.1;
    margin-bottom: 12px;
  }
  .hero h1 .accent { color: var(--accent); }
  .hero h1 .accent2 { color: var(--accent2); }
  .hero-sub {
    font-family: var(--font-kr);
    font-size: clamp(18px, 2.5vw, 28px);
    color: var(--muted);
    margin-bottom: 32px;
    font-weight: 300;
  }
  .hero-desc {
    font-size: 16px;
    color: var(--muted);
    max-width: 600px;
    line-height: 1.8;
    margin-bottom: 48px;
  }
  .hero-desc .kr { font-family: var(--font-kr); font-size: 14px; color: #5a7a95; margin-top: 4px; }
  .hero-stats {
    display: flex;
    gap: 48px;
    flex-wrap: wrap;
  }
  .stat {
    border-left: 2px solid var(--accent);
    padding-left: 16px;
  }
  .stat-num {
    font-family: var(--font-mono);
    font-size: 32px;
    color: var(--accent);
    font-weight: 700;
  }
  .stat-label { font-size: 12px; color: var(--muted); margin-top: 2px; }
  .stat-label .kr { font-family: var(--font-kr); }

  /* ─── SECTION COMMON ─── */
  section {
    position: relative;
    z-index: 1;
    padding: 100px 8%;
  }
  .section-tag {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  .section-title {
    font-size: clamp(24px, 3vw, 40px);
    font-weight: 700;
    margin-bottom: 8px;
  }
  .section-title-kr {
    font-family: var(--font-kr);
    font-size: clamp(16px, 2vw, 24px);
    color: var(--muted);
    font-weight: 300;
    margin-bottom: 48px;
  }

  /* ─── FEATURES ─── */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
    max-width: 1100px;
  }
  .feature-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 32px;
    position: relative;
    overflow: hidden;
    transition: border-color .3s, transform .3s;
  }
  .feature-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity .3s;
  }
  .feature-card:hover { border-color: var(--accent); transform: translateY(-4px); }
  .feature-card:hover::before { opacity: 1; }
  .feature-icon {
    width: 48px; height: 48px;
    background: rgba(0,212,255,.1);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    margin-bottom: 20px;
  }
  .feature-title { font-size: 18px; font-weight: 700; margin-bottom: 4px; }
  .feature-title-kr { font-family: var(--font-kr); font-size: 14px; color: var(--accent2); margin-bottom: 12px; }
  .feature-desc { font-size: 14px; color: var(--muted); line-height: 1.7; }
  .feature-desc .kr { font-family: var(--font-kr); }

  /* ─── RISK DASHBOARD ─── */
  .dashboard-bg { background: var(--surface); border-radius: 20px; padding: 40px; max-width: 1100px; }
  .risk-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-bottom: 32px; }
  .risk-card {
    background: var(--card);
    border-radius: 10px;
    padding: 20px;
    border: 1px solid var(--border);
    position: relative;
  }
  .risk-level {
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 2px;
    padding: 3px 10px;
    border-radius: 20px;
    display: inline-block;
    margin-bottom: 10px;
  }
  .risk-high { background: rgba(255,71,87,.15); color: var(--danger); border: 1px solid rgba(255,71,87,.3); }
  .risk-mid { background: rgba(255,165,2,.15); color: var(--warn); border: 1px solid rgba(255,165,2,.3); }
  .risk-low { background: rgba(46,213,115,.15); color: var(--success); border: 1px solid rgba(46,213,115,.3); }
  .risk-title { font-size: 15px; font-weight: 600; margin-bottom: 4px; }
  .risk-title-kr { font-family: var(--font-kr); font-size: 12px; color: var(--muted); margin-bottom: 8px; }
  .risk-bar-wrap { background: var(--bg); border-radius: 4px; height: 6px; overflow: hidden; }
  .risk-bar {
    height: 100%;
    border-radius: 4px;
    animation: grow 1.5s ease-out forwards;
    transform-origin: left;
  }
  @keyframes grow { from { width: 0; } }
  .risk-num {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
    margin-top: 6px;
    text-align: right;
  }

  /* ─── ARCHITECTURE ─── */
  .arch-flow {
    display: flex;
    align-items: center;
    gap: 0;
    flex-wrap: wrap;
    max-width: 1100px;
    justify-content: center;
  }
  .arch-node {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px 20px;
    text-align: center;
    min-width: 160px;
    position: relative;
    flex: 1;
  }
  .arch-node-icon { font-size: 28px; margin-bottom: 10px; }
  .arch-node-title { font-size: 14px; font-weight: 700; margin-bottom: 3px; }
  .arch-node-kr { font-family: var(--font-kr); font-size: 12px; color: var(--accent); }
  .arch-arrow {
    color: var(--accent);
    font-size: 20px;
    padding: 0 8px;
    flex-shrink: 0;
  }

  /* ─── PDF SECTION ─── */
  .pdf-section {
    background: linear-gradient(135deg, rgba(0,212,255,.05), rgba(0,255,157,.05));
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 60px;
    max-width: 1100px;
  }
  .pdf-items {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    margin-top: 32px;
  }
  .pdf-item {
    display: flex;
    gap: 16px;
    align-items: flex-start;
    background: var(--card);
    border-radius: 10px;
    padding: 20px;
    border: 1px solid var(--border);
  }
  .pdf-num {
    font-family: var(--font-mono);
    font-size: 28px;
    font-weight: 700;
    color: var(--accent);
    line-height: 1;
    min-width: 40px;
  }
  .pdf-item-title { font-size: 15px; font-weight: 700; margin-bottom: 4px; }
  .pdf-item-kr { font-family: var(--font-kr); font-size: 13px; color: var(--accent2); margin-bottom: 6px; }
  .pdf-item-desc { font-size: 13px; color: var(--muted); line-height: 1.6; }
  .pdf-item-desc .kr { font-family: var(--font-kr); }

  /* ─── TEAM/CONTACT ─── */
  .footer {
    position: relative;
    z-index: 1;
    background: var(--surface);
    border-top: 1px solid var(--border);
    padding: 60px 8% 40px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 32px;
  }
  .footer-brand {
    font-family: var(--font-mono);
    font-size: 20px;
    color: var(--accent);
    margin-bottom: 8px;
  }
  .footer-sub { font-family: var(--font-kr); font-size: 13px; color: var(--muted); }
  .footer-copy { font-size: 12px; color: #3a5575; margin-top: 24px; }
  .footer-links { display: flex; flex-direction: column; gap: 8px; }
  .footer-links a { color: var(--muted); text-decoration: none; font-size: 13px; transition: color .2s; }
  .footer-links a:hover { color: var(--accent); }

  /* ─── DOWNLOAD BUTTON ─── */
  .download-btn {
    position: fixed;
    bottom: 32px;
    right: 32px;
    z-index: 2000;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    color: var(--bg);
    border: none;
    border-radius: 50px;
    padding: 14px 24px;
    font-family: var(--font-mono);
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 1px;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 10px;
    box-shadow: 0 8px 32px rgba(0,212,255,.4);
    transition: transform .2s, box-shadow .2s;
    animation: pulse-glow 3s ease-in-out infinite;
  }
  @keyframes pulse-glow {
    0%, 100% { box-shadow: 0 8px 32px rgba(0,212,255,.4); }
    50% { box-shadow: 0 8px 48px rgba(0,255,157,.6); }
  }
  .download-btn:hover { transform: translateY(-2px) scale(1.03); }
  .download-btn:active { transform: scale(.97); }
  .download-btn .icon { font-size: 18px; }

  /* ─── SCAN LINES ─── */
  .scanlines {
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,.03) 2px,
      rgba(0,0,0,.03) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* ─── LANG DISPLAY ─── */
  .zh { display: block; }
  .kr { display: block; }
  body.lang-kr .zh-only { display: none !important; }
  body.lang-zh .kr-only { display: none !important; }

  /* Status dot */
  .status-dot {
    width: 8px; height: 8px;
    background: var(--accent2);
    border-radius: 50%;
    display: inline-block;
    animation: blink 2s ease-in-out infinite;
    margin-right: 6px;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:.2} }

  /* Divider */
  .section-divider {
    position: relative;
    z-index: 1;
    text-align: center;
    padding: 0;
    margin: 0 8%;
  }
  .section-divider::after {
    content: '';
    display: block;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
  }

  /* Responsive */
  @media(max-width: 768px) {
    .risk-grid { grid-template-columns: 1fr; }
    .pdf-items { grid-template-columns: 1fr; }
    .arch-flow { flex-direction: column; }
    .arch-arrow { transform: rotate(90deg); }
    .nav-links { display: none; }
    .hero-stats { gap: 24px; }
    .lang-bar { padding: 10px 20px; }
  }
</style>
</head>
<body>

<div class="scanlines"></div>

<!-- PARTICLES -->
<canvas id="particleCanvas" style="position:fixed;inset:0;z-index:0;pointer-events:none;"></canvas>

<!-- NAV -->
<nav class="lang-bar">
  <div class="brand">DIGI<span>HEALTH</span>.GUARD</div>
  <ul class="nav-links">
    <li><a href="#features">功能 / 기능</a></li>
    <li><a href="#dashboard">安全 / 보안</a></li>
    <li><a href="#architecture">架构 / 구조</a></li>
    <li><a href="#pdf-doc">文档 / 문서</a></li>
  </ul>
  <div class="lang-toggle">
    <button class="lang-btn active" onclick="setLang('zh')" id="btn-zh">中文</button>
    <button class="lang-btn" onclick="setLang('kr')" id="btn-kr">한국어</button>
  </div>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-inner">
    <div class="hero-tag">
      <span class="status-dot"></span>
      <span class="zh-only">数字健康产业安全平台 · 竞赛项目</span>
      <span class="kr-only" style="font-family:var(--font-kr)">디지털 헬스 산업 보안 플랫폼 · 경진대회</span>
    </div>
    <h1>
      <span class="accent">Digital</span><br>
      <span class="accent2">Health</span><br>
      <span class="zh-only">产业安全平台</span>
      <span class="kr-only" style="font-family:var(--font-kr)">산업 보안 플랫폼</span>
    </h1>
    <div class="hero-sub zh-only">디지털 헬스케어 산업 보안 통합 관리 시스템</div>
    <div class="hero-sub kr-only">디지털 헬스케어 산업 보안 통합 관리 시스템</div>
    <div class="hero-desc">
      <span class="zh-only">
        面向数字健康医疗领域的综合安全管理平台，集数据加密、访问控制、风险监测与合规审计于一体，守护医疗数据安全，赋能数字健康产业稳健发展。
      </span>
      <span class="kr-only" style="font-family:var(--font-kr)">
        디지털 헬스케어 분야를 위한 종합 보안 관리 플랫폼입니다. 데이터 암호화, 접근 제어, 위험 모니터링 및 컴플라이언스 감사 기능을 통합하여 의료 데이터 보안을 강화합니다.
      </span>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-num">99.9%</div>
        <div class="stat-label zh-only">系统可用率<br><span class="kr">시스템 가용률</span></div>
        <div class="stat-label kr-only" style="font-family:var(--font-kr)">시스템 가용률</div>
      </div>
      <div class="stat" style="border-color:var(--accent2)">
        <div class="stat-num" style="color:var(--accent2)">256-bit</div>
        <div class="stat-label zh-only">AES数据加密<br><span class="kr">AES 데이터 암호화</span></div>
        <div class="stat-label kr-only" style="font-family:var(--font-kr)">AES 데이터 암호화</div>
      </div>
      <div class="stat" style="border-color:var(--accent3)">
        <div class="stat-num" style="color:var(--accent3)">0.3s</div>
        <div class="stat-label zh-only">威胁响应时间<br><span class="kr">위협 대응 시간</span></div>
        <div class="stat-label kr-only" style="font-family:var(--font-kr)">위협 대응 시간</div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- FEATURES -->
<section id="features">
  <div class="section-tag">// CORE FEATURES</div>
  <h2 class="section-title zh-only">网站主要功能介绍</h2>
  <h2 class="section-title kr-only" style="font-family:var(--font-kr)">웹사이트 주요 기능 소개</h2>
  <div class="section-title-kr zh-only">웹사이트 주요 기능 소개</div>
  <div class="section-title-kr kr-only">网站主要功能介绍</div>

  <div class="features-grid">

    <div class="feature-card">
      <div class="feature-icon">🔐</div>
      <div class="feature-title zh-only">数据加密与访问控制</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">데이터 암호화 및 접근 제어</div>
      <div class="feature-title-kr zh-only">데이터 암호화 및 접근 제어</div>
      <div class="feature-title-kr kr-only">数据加密与访问控制</div>
      <div class="feature-desc">
        <span class="zh-only">采用AES-256端到端加密技术，多层权限验证机制，确保患者隐私数据及医疗记录的安全存储与传输。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">AES-256 엔드투엔드 암호화 기술과 다층 권한 검증 메커니즘을 통해 환자 개인정보 및 의료 기록의 안전한 저장과 전송을 보장합니다.</span>
      </div>
    </div>

    <div class="feature-card">
      <div class="feature-icon">📊</div>
      <div class="feature-title zh-only">实时风险监测仪表板</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">실시간 위험 모니터링 대시보드</div>
      <div class="feature-title-kr zh-only">실시간 위험 모니터링 대시보드</div>
      <div class="feature-title-kr kr-only">实时风险监测仪表板</div>
      <div class="feature-desc">
        <span class="zh-only">可视化呈现系统安全态势，实时追踪异常访问行为、数据泄露风险及网络入侵事件，支持自定义预警阈值。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">시스템 보안 현황을 시각적으로 표시하고, 비정상 접근 행동, 데이터 유출 위험 및 네트워크 침입 이벤트를 실시간으로 추적합니다.</span>
      </div>
    </div>

    <div class="feature-card">
      <div class="feature-icon">🤖</div>
      <div class="feature-title zh-only">AI智能威胁分析</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">AI 지능형 위협 분석</div>
      <div class="feature-title-kr zh-only">AI 지능형 위협 분석</div>
      <div class="feature-title-kr kr-only">AI智能威胁分析</div>
      <div class="feature-desc">
        <span class="zh-only">基于机器学习的异常行为检测引擎，自动识别潜在安全威胁，提供智能处置建议，降低人工运维成本。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">머신러닝 기반의 이상 행동 감지 엔진으로 잠재적 보안 위협을 자동 식별하고 지능적인 처리 방안을 제공합니다.</span>
      </div>
    </div>

    <div class="feature-card">
      <div class="feature-icon">📋</div>
      <div class="feature-title zh-only">合规审计与报告生成</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">컴플라이언스 감사 및 보고서 생성</div>
      <div class="feature-title-kr zh-only">컴플라이언스 감사 및 보고서 생성</div>
      <div class="feature-title-kr kr-only">合规审计与报告生成</div>
      <div class="feature-desc">
        <span class="zh-only">符合HIPAA、GDPR等国际医疗数据隐私标准，自动生成合规审计报告，支持一键导出PDF格式文档。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">HIPAA, GDPR 등 국제 의료 데이터 개인정보 보호 표준을 준수하며, 컴플라이언스 감사 보고서를 자동 생성하고 PDF 내보내기를 지원합니다.</span>
      </div>
    </div>

    <div class="feature-card">
      <div class="feature-icon">🔗</div>
      <div class="feature-title zh-only">API安全集成管理</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">API 보안 통합 관리</div>
      <div class="feature-title-kr zh-only">API 보안 통합 관리</div>
      <div class="feature-title-kr kr-only">API安全集成管理</div>
      <div class="feature-desc">
        <span class="zh-only">统一管理医疗设备、HIS系统、第三方服务的API接入，提供OAuth 2.0认证、速率限制及安全沙箱测试环境。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">의료 기기, HIS 시스템, 서드파티 서비스의 API 접근을 통합 관리하며 OAuth 2.0 인증, 속도 제한 및 보안 샌드박스 환경을 제공합니다.</span>
      </div>
    </div>

    <div class="feature-card">
      <div class="feature-icon">📄</div>
      <div class="feature-title zh-only">一键导出韩语版PDF</div>
      <div class="feature-title kr-only" style="font-family:var(--font-kr)">원클릭 한국어 PDF 내보내기</div>
      <div class="feature-title-kr zh-only">원클릭 한국어 PDF 내보내기</div>
      <div class="feature-title-kr kr-only">一键导出韩语版PDF</div>
      <div class="feature-desc">
        <span class="zh-only">页面右下角提供一键下载按钮，支持导出包含设计说明、功能介绍、预期效果及补充说明的完整韩语版PDF文档。</span>
        <span class="kr-only" style="font-family:var(--font-kr)">페이지 우측 하단의 원클릭 다운로드 버튼으로 설계 설명, 기능 소개, 기대 효과 및 보충 설명이 포함된 완전한 한국어 PDF 문서를 내보낼 수 있습니다.</span>
      </div>
    </div>

  </div>
</section>

<div class="section-divider"></div>

<!-- RISK DASHBOARD -->
<section id="dashboard">
  <div class="section-tag">// SECURITY DASHBOARD</div>
  <h2 class="section-title zh-only">实时安全风险监测</h2>
  <h2 class="section-title kr-only" style="font-family:var(--font-kr)">실시간 보안 위험 모니터링</h2>
  <div class="section-title-kr zh-only">실시간 보안 위험 모니터링</div>
  <div class="section-title-kr kr-only">实时安全风险监测</div>

  <div class="dashboard-bg">
    <div class="risk-grid">

      <div class="risk-card">
        <span class="risk-level risk-high">HIGH RISK / 고위험</span>
        <div class="risk-title zh-only">未授权访问尝试</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">무단 접근 시도</div>
        <div class="risk-title-kr zh-only">무단 접근 시도</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:82%;background:linear-gradient(90deg,#ff4757,#ff6b81)"></div></div>
        <div class="risk-num">82 / 100</div>
      </div>

      <div class="risk-card">
        <span class="risk-level risk-mid">MEDIUM / 중간 위험</span>
        <div class="risk-title zh-only">数据传输异常</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">데이터 전송 이상</div>
        <div class="risk-title-kr zh-only">데이터 전송 이상</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:55%;background:linear-gradient(90deg,#ffa502,#ffcc02)"></div></div>
        <div class="risk-num">55 / 100</div>
      </div>

      <div class="risk-card">
        <span class="risk-level risk-low">LOW RISK / 저위험</span>
        <div class="risk-title zh-only">系统日志异常</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">시스템 로그 이상</div>
        <div class="risk-title-kr zh-only">시스템 로그 이상</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:23%;background:linear-gradient(90deg,#2ed573,#7bed9f)"></div></div>
        <div class="risk-num">23 / 100</div>
      </div>

      <div class="risk-card">
        <span class="risk-level risk-mid">MEDIUM / 중간 위험</span>
        <div class="risk-title zh-only">API调用频率超限</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">API 호출 빈도 초과</div>
        <div class="risk-title-kr zh-only">API 호출 빈도 초과</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:61%;background:linear-gradient(90deg,#ffa502,#ffcc02)"></div></div>
        <div class="risk-num">61 / 100</div>
      </div>

      <div class="risk-card">
        <span class="risk-level risk-low">LOW RISK / 저위험</span>
        <div class="risk-title zh-only">弱密码账户检测</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">약한 비밀번호 계정 감지</div>
        <div class="risk-title-kr zh-only">약한 비밀번호 계정 감지</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:18%;background:linear-gradient(90deg,#2ed573,#7bed9f)"></div></div>
        <div class="risk-num">18 / 100</div>
      </div>

      <div class="risk-card">
        <span class="risk-level risk-high">HIGH RISK / 고위험</span>
        <div class="risk-title zh-only">DDoS攻击检测</div>
        <div class="risk-title kr-only" style="font-family:var(--font-kr)">DDoS 공격 감지</div>
        <div class="risk-title-kr zh-only">DDoS 공격 감지</div>
        <div class="risk-bar-wrap"><div class="risk-bar" style="width:77%;background:linear-gradient(90deg,#ff4757,#ff6b81)"></div></div>
        <div class="risk-num">77 / 100</div>
      </div>

    </div>

    <div style="display:flex;gap:24px;flex-wrap:wrap;">
      <div style="flex:1;min-width:200px;background:var(--bg);border-radius:10px;padding:20px;border:1px solid var(--border);">
        <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent);margin-bottom:8px;">SYSTEM STATUS</div>
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:6px;">
          <span class="status-dot"></span>
          <span class="zh-only" style="font-size:14px;">所有核心服务运行正常</span>
          <span class="kr-only" style="font-family:var(--font-kr);font-size:14px;">모든 핵심 서비스 정상 운영</span>
        </div>
        <div style="font-size:12px;color:var(--muted);">
          <span class="zh-only">最后扫描: 2分钟前</span>
          <span class="kr-only" style="font-family:var(--font-kr);">마지막 스캔: 2분 전</span>
        </div>
      </div>
      <div style="flex:1;min-width:200px;background:var(--bg);border-radius:10px;padding:20px;border:1px solid var(--border);">
        <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent2);margin-bottom:8px;">ACTIVE ALERTS</div>
        <div style="font-family:var(--font-mono);font-size:36px;color:var(--danger);font-weight:700;">12</div>
        <div style="font-size:12px;color:var(--muted);">
          <span class="zh-only">需要立即处理的安全告警</span>
          <span class="kr-only" style="font-family:var(--font-kr);">즉시 처리가 필요한 보안 경고</span>
        </div>
      </div>
      <div style="flex:1;min-width:200px;background:var(--bg);border-radius:10px;padding:20px;border:1px solid var(--border);">
        <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent3);margin-bottom:8px;">COMPLIANCE SCORE</div>
        <div style="font-family:var(--font-mono);font-size:36px;color:var(--success);font-weight:700;">94%</div>
        <div style="font-size:12px;color:var(--muted);">
          <span class="zh-only">HIPAA & PIPA合规得分</span>
          <span class="kr-only" style="font-family:var(--font-kr);">HIPAA & 개인정보보호법 준수 점수</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- ARCHITECTURE -->
<section id="architecture">
  <div class="section-tag">// SYSTEM ARCHITECTURE</div>
  <h2 class="section-title zh-only">网站设计与开发架构</h2>
  <h2 class="section-title kr-only" style="font-family:var(--font-kr)">웹사이트 설계 및 개발 구조</h2>
  <div class="section-title-kr zh-only">웹사이트 설계 및 개발 구조</div>
  <div class="section-title-kr kr-only">网站设计与开发架构</div>

  <div class="arch-flow">
    <div class="arch-node">
      <div class="arch-node-icon">🌐</div>
      <div class="arch-node-title zh-only">前端界面</div>
      <div class="arch-node-title kr-only" style="font-family:var(--font-kr)">프론트엔드</div>
      <div class="arch-node-kr zh-only">프론트엔드 인터페이스</div>
      <div class="arch-node-kr kr-only">前端界面</div>
    </div>
    <div class="arch-arrow">→</div>
    <div class="arch-node">
      <div class="arch-node-icon">🔒</div>
      <div class="arch-node-title zh-only">安全认证层</div>
      <div class="arch-node-title kr-only" style="font-family:var(--font-kr)">보안 인증 레이어</div>
      <div class="arch-node-kr zh-only">보안 인증 레이어</div>
      <div class="arch-node-kr kr-only">安全认证层</div>
    </div>
    <div class="arch-arrow">→</div>
    <div class="arch-node">
      <div class="arch-node-icon">⚙️</div>
      <div class="arch-node-title zh-only">业务逻辑层</div>
      <div class="arch-node-title kr-only" style="font-family:var(--font-kr)">비즈니스 로직 레이어</div>
      <div class="arch-node-kr zh-only">비즈니스 로직 레이어</div>
      <div class="arch-node-kr kr-only">业务逻辑层</div>
    </div>
    <div class="arch-arrow">→</div>
    <div class="arch-node">
      <div class="arch-node-icon">🗄️</div>
      <div class="arch-node-title zh-only">加密数据库</div>
      <div class="arch-node-title kr-only" style="font-family:var(--font-kr)">암호화 데이터베이스</div>
      <div class="arch-node-kr zh-only">암호화 데이터베이스</div>
      <div class="arch-node-kr kr-only">加密数据库</div>
    </div>
    <div class="arch-arrow">→</div>
    <div class="arch-node">
      <div class="arch-node-icon">📈</div>
      <div class="arch-node-title zh-only">监控与审计</div>
      <div class="arch-node-title kr-only" style="font-family:var(--font-kr)">모니터링 및 감사</div>
      <div class="arch-node-kr zh-only">모니터링 및 감사</div>
      <div class="arch-node-kr kr-only">监控与审计</div>
    </div>
  </div>

  <div style="margin-top:40px;max-width:1100px;display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:16px;">
    <div style="background:var(--card);border:1px solid var(--border);border-radius:10px;padding:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent);margin-bottom:10px;">FRONTEND STACK</div>
      <div style="font-size:13px;color:var(--muted);line-height:1.8;">HTML5 / CSS3 / JavaScript<br>Responsive Design<br>Single-file Architecture<br>CDN Dependencies</div>
    </div>
    <div style="background:var(--card);border:1px solid var(--border);border-radius:10px;padding:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent2);margin-bottom:10px;">SECURITY LAYER</div>
      <div style="font-size:13px;color:var(--muted);line-height:1.8;">AES-256 Encryption<br>JWT Authentication<br>OAuth 2.0<br>HTTPS / TLS 1.3</div>
    </div>
    <div style="background:var(--card);border:1px solid var(--border);border-radius:10px;padding:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--accent3);margin-bottom:10px;">COMPLIANCE</div>
      <div style="font-size:13px;color:var(--muted);line-height:1.8;">HIPAA Standard<br>GDPR / PIPA<br>ISO 27001<br>한국 개인정보보호법</div>
    </div>
    <div style="background:var(--card);border:1px solid var(--border);border-radius:10px;padding:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--muted);margin-bottom:10px;">DEPLOYMENT</div>
      <div style="font-size:13px;color:var(--muted);line-height:1.8;">GitHub Pages<br>Single HTML File<br>Zero Server Cost<br>Instant Deploy</div>
    </div>
  </div>
</section>

<div class="section-divider"></div>

<!-- PDF DOC SECTION -->
<section id="pdf-doc">
  <div class="section-tag">// PDF DOCUMENT CONTENTS</div>
  <h2 class="section-title zh-only">PDF文档内容说明</h2>
  <h2 class="section-title kr-only" style="font-family:var(--font-kr)">PDF 문서 내용 안내</h2>
  <div class="section-title-kr zh-only">PDF 문서 내용 안내 (다운로드 버튼으로 내보내기 가능)</div>
  <div class="section-title-kr kr-only">PDF文档内容说明（右下角下载按钮导出）</div>

  <div class="pdf-section">
    <div style="font-size:15px;color:var(--muted);line-height:1.8;max-width:700px;">
      <span class="zh-only">点击右下角【⬇ 한국어 PDF】按钮，即可下载包含以下4项完整内容的韩语版PDF文档：</span>
      <span class="kr-only" style="font-family:var(--font-kr)">우측 하단의 【⬇ 한국어 PDF】 버튼을 클릭하면 다음 4가지 내용이 포함된 한국어 PDF 문서를 다운로드할 수 있습니다:</span>
    </div>
    <div class="pdf-items">

      <div class="pdf-item">
        <div class="pdf-num">01</div>
        <div>
          <div class="pdf-item-title zh-only">网站设计与开发方法</div>
          <div class="pdf-item-title kr-only" style="font-family:var(--font-kr)">웹사이트 설계 및 개발 방법</div>
          <div class="pdf-item-kr zh-only">웹사이트 설계 및 개발 방법</div>
          <div class="pdf-item-kr kr-only">网站设计与开发方法</div>
          <div class="pdf-item-desc">
            <span class="zh-only">单文件HTML架构、响应式设计、前端技术栈选型、安全层设计方法论及部署流程说明。</span>
            <span class="kr-only" style="font-family:var(--font-kr)">단일 파일 HTML 아키텍처, 반응형 디자인, 프론트엔드 기술 스택 선정, 보안 레이어 설계 방법론 및 배포 프로세스 설명.</span>
          </div>
        </div>
      </div>

      <div class="pdf-item">
        <div class="pdf-num">02</div>
        <div>
          <div class="pdf-item-title zh-only">网站主要功能介绍</div>
          <div class="pdf-item-title kr-only" style="font-family:var(--font-kr)">웹사이트 주요 기능 소개</div>
          <div class="pdf-item-kr zh-only">웹사이트 주요 기능 소개</div>
          <div class="pdf-item-kr kr-only">网站主要功能介绍</div>
          <div class="pdf-item-desc">
            <span class="zh-only">数据加密、风险监测、AI威胁分析、合规审计、API管理及一键导出PDF六大核心功能详细说明。</span>
            <span class="kr-only" style="font-family:var(--font-kr)">데이터 암호화, 위험 모니터링, AI 위협 분석, 컴플라이언스 감사, API 관리 및 원클릭 PDF 내보내기 등 6가지 핵심 기능 상세 설명.</span>
          </div>
        </div>
      </div>

      <div class="pdf-item">
        <div class="pdf-num">03</div>
        <div>
          <div class="pdf-item-title zh-only">项目预期效果与应用价值</div>
          <div class="pdf-item-title kr-only" style="font-family:var(--font-kr)">프로젝트 기대 효과 및 응용 가치</div>
          <div class="pdf-item-kr zh-only">프로젝트 기대 효과 및 응용 가치</div>
          <div class="pdf-item-kr kr-only">项目预期效果与应用价值</div>
          <div class="pdf-item-desc">
            <span class="zh-only">提升医疗数据安全性、降低合规成本、推动数字健康产业健康发展的量化预期目标与社会价值评估。</span>
            <span class="kr-only" style="font-family:var(--font-kr)">의료 데이터 보안 강화, 컴플라이언스 비용 절감, 디지털 헬스케어 산업의 건전한 발전 촉진을 위한 정량적 목표 및 사회적 가치 평가.</span>
          </div>
        </div>
      </div>

      <div class="pdf-item">
        <div class="pdf-num">04</div>
        <div>
          <div class="pdf-item-title zh-only">其余相关补充说明</div>
          <div class="pdf-item-title kr-only" style="font-family:var(--font-kr)">기타 관련 보충 설명</div>
          <div class="pdf-item-kr zh-only">기타 관련 보충 설명</div>
          <div class="pdf-item-kr kr-only">其余相关补充说明</div>
          <div class="pdf-item-desc">
            <span class="zh-only">技术局限性说明、未来迭代规划、参考标准文献及竞赛项目声明等补充信息。</span>
            <span class="kr-only" style="font-family:var(--font-kr)">기술적 한계 설명, 향후 개선 계획, 참고 표준 문헌 및 경진대회 프로젝트 선언 등 보충 정보.</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- FOOTER -->
<footer class="footer">
  <div>
    <div class="footer-brand">DIGI<span style="color:var(--accent2)">HEALTH</span>.GUARD</div>
    <div class="footer-sub">디지털 헬스케어 산업 보안 플랫폼</div>
    <div class="footer-sub" style="margin-top:4px;font-family:var(--font-zh)">数字健康医疗产业安全平台</div>
    <div class="footer-copy">© 2025 Digital Health Safety Platform · 数字健康产业安全平台竞赛项目</div>
  </div>
  <div class="footer-links">
    <a href="#features">功能介绍 / 기능 소개</a>
    <a href="#dashboard">安全仪表板 / 보안 대시보드</a>
    <a href="#architecture">系统架构 / 시스템 구조</a>
    <a href="#pdf-doc">PDF文档 / PDF 문서</a>
  </div>
  <div>
    <div style="font-family:var(--font-mono);font-size:11px;color:var(--muted);margin-bottom:12px;">COMPLIANCE BADGES</div>
    <div style="display:flex;flex-wrap:wrap;gap:8px;">
      <span style="background:rgba(0,212,255,.1);border:1px solid rgba(0,212,255,.3);color:var(--accent);padding:4px 10px;border-radius:4px;font-size:11px;font-family:var(--font-mono);">HIPAA</span>
      <span style="background:rgba(0,255,157,.1);border:1px solid rgba(0,255,157,.3);color:var(--accent2);padding:4px 10px;border-radius:4px;font-size:11px;font-family:var(--font-mono);">GDPR</span>
      <span style="background:rgba(255,107,53,.1);border:1px solid rgba(255,107,53,.3);color:var(--accent3);padding:4px 10px;border-radius:4px;font-size:11px;font-family:var(--font-mono);">ISO 27001</span>
      <span style="background:rgba(122,154,184,.1);border:1px solid rgba(122,154,184,.3);color:var(--muted);padding:4px 10px;border-radius:4px;font-size:11px;font-family:var(--font-mono);">PIPA</span>
    </div>
  </div>
</footer>

<!-- DOWNLOAD PDF BUTTON -->
<button class="download-btn" onclick="downloadPDF()" title="한국어 PDF 다운로드">
  <span class="icon">⬇</span>
  <span>한국어 PDF</span>
</button>

<script>
// ─── LANGUAGE TOGGLE ───
function setLang(lang) {
  document.getElementById('btn-zh').classList.toggle('active', lang === 'zh');
  document.getElementById('btn-kr').classList.toggle('active', lang === 'kr');
  document.body.classList.toggle('lang-kr', lang === 'kr');
  document.body.classList.toggle('lang-zh', lang === 'zh');
}
setLang('zh');

// ─── PARTICLES ───
(function() {
  const canvas = document.getElementById('particleCanvas');
  const ctx = canvas.getContext('2d');
  let particles = [];
  function resize() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize);
  function createParticle() {
    return {
      x: Math.random() * canvas.width,
      y: canvas.height + 10,
      size: Math.random() * 2 + 0.5,
      speed: Math.random() * 0.8 + 0.3,
      opacity: 0,
      maxOpacity: Math.random() * 0.4 + 0.1,
      color: Math.random() > 0.5 ? '#00d4ff' : '#00ff9d'
    };
  }
  for (let i = 0; i < 40; i++) {
    const p = createParticle();
    p.y = Math.random() * canvas.height;
    particles.push(p);
  }
  function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    particles.forEach((p, i) => {
      p.y -= p.speed;
      p.opacity = Math.min(p.maxOpacity, p.opacity + 0.005);
      if (p.y < -10) { particles[i] = createParticle(); }
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
      ctx.fillStyle = p.color;
      ctx.globalAlpha = p.opacity;
      ctx.fill();
    });
    ctx.globalAlpha = 1;
    requestAnimationFrame(animate);
  }
  animate();
})();

// ─── PDF EXPORT (Korean) ───
async function downloadPDF() {
  const btn = document.querySelector('.download-btn');
  btn.innerHTML = '<span class="icon">⏳</span><span>생성 중...</span>';
  btn.disabled = true;

  await new Promise(r => setTimeout(r, 100));

  try {
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF({ orientation: 'portrait', unit: 'mm', format: 'a4' });
    const W = 210, M = 18, CW = W - M * 2;

    // ─ Color helpers
    const setFill  = (r,g,b) => doc.setFillColor(r,g,b);
    const setDraw  = (r,g,b) => doc.setDrawColor(r,g,b);
    const setColor = (r,g,b) => doc.setTextColor(r,g,b);

    // ─ COVER PAGE ─
    setFill(5,12,26); doc.rect(0,0,W,297,'F');
    // accent bar
    setFill(0,212,255); doc.rect(0,0,W,2,'F');
    // title block
    setColor(0,212,255);
    doc.setFontSize(9); doc.setFont('helvetica','bold');
    doc.text('DIGITAL HEALTH GUARD', M, 40);
    setColor(232,244,255);
    doc.setFontSize(28); doc.setFont('helvetica','bold');
    doc.text('디지털 헬스케어', M, 58);
    doc.text('산업 보안 플랫폼', M, 72);
    setColor(0,255,157);
    doc.setFontSize(14); doc.setFont('helvetica','normal');
    doc.text('Digital Health Industry Security Platform', M, 86);
    // subtitle zh
    setColor(122,154,184);
    doc.setFontSize(11);
    doc.text('\u6570\u5B57\u5065\u5EB7\u4EA7\u4E1A\u5B89\u5168\u5E73\u53F0 - \uacbd\uc9c4\ub300\ud68c \ud504\ub85c\uc81d\ud2b8', M, 100);
    // info box
    setFill(10,22,40); setDraw(26,48,80);
    doc.roundedRect(M, 112, CW, 48, 3, 3, 'FD');
    setColor(0,212,255); doc.setFontSize(8); doc.setFont('helvetica','bold');
    doc.text('PROJECT INFO', M+8, 124);
    setColor(232,244,255); doc.setFontSize(10); doc.setFont('helvetica','normal');
    doc.text([
      '\uACFC\uc81c\uba85: \ub514\uc9c0\ud138 \ud5ec\uc2a4 \uc0b0\uc5c5 \ubcf4\uc548 \ud1b5\ud569 \uad00\ub9ac \uc2dc\uc2a4\ud15c',
      '\uc8fc\uc81c: \uc0b0\uc5c5 \ubcf4\uc548 | \ud50c\ub7ab\ud3fc \uac1c\ubc1c \uacbd\uc9c4\ub300\ud68c',
      '\uae30\uc220 \uc2a4\ud0dd: HTML5 / CSS3 / JavaScript / jsPDF',
      '\ubc30\ud3ec: GitHub Pages (\ub2e8\uc77c \ud30c\uc77c \uc544\ud0a4\ud14d\uccb8)'
    ], M+8, 133, { lineHeightFactor: 1.6 });
    // footer
    setColor(58,85,117);
    doc.setFontSize(8);
    doc.text('2025 Digital Health Safety Platform · All Rights Reserved', M, 285);
    setFill(0,212,255); doc.rect(0,295,W,2,'F');

    // ─ SECTION HELPER ─
    let page = 1;
    function addSection(num, title_kr, title_zh, items) {
      doc.addPage();
      page++;
      setFill(5,12,26); doc.rect(0,0,W,297,'F');
      setFill(0,212,255); doc.rect(0,0,W,1.5,'F');
      // section number
      setColor(0,212,255); doc.setFontSize(48); doc.setFont('helvetica','bold');
      doc.text('0'+num, M, 48);
      // titles
      setColor(232,244,255); doc.setFontSize(20); doc.setFont('helvetica','bold');
      doc.text(title_kr, M, 62);
      setColor(122,154,184); doc.setFontSize(11); doc.setFont('helvetica','normal');
      doc.text(title_zh, M, 72);
      // divider
      setDraw(26,48,80); doc.setLineWidth(0.4); doc.line(M, 78, W-M, 78);

      let y = 90;
      items.forEach(item => {
        if (y > 260) { doc.addPage(); page++; setFill(5,12,26); doc.rect(0,0,W,297,'F'); y = 24; }
        if (item.type === 'heading') {
          setColor(0,212,255); doc.setFontSize(11); doc.setFont('helvetica','bold');
          doc.text(item.text, M, y); y += 4;
          setFill(0,212,255); doc.rect(M, y, 30, 0.5, 'F'); y += 8;
        } else if (item.type === 'text') {
          setColor(200,220,240); doc.setFontSize(10); doc.setFont('helvetica','normal');
          const lines = doc.splitTextToSize(item.text, CW);
          doc.text(lines, M, y); y += lines.length * 5.5 + 4;
        } else if (item.type === 'bullet') {
          setColor(0,255,157); doc.setFontSize(10); doc.setFont('helvetica','bold');
          doc.text('▸', M, y);
          setColor(200,220,240); doc.setFont('helvetica','normal');
          const lines = doc.splitTextToSize(item.text, CW - 8);
          doc.text(lines, M+7, y); y += lines.length * 5.5 + 3;
        } else if (item.type === 'card') {
          setFill(10,22,40); setDraw(26,48,80);
          const h = 8 + Math.ceil(doc.splitTextToSize(item.body, CW-16).length) * 5;
          doc.roundedRect(M, y-4, CW, h+8, 2, 2, 'FD');
          setColor(0,212,255); doc.setFontSize(9); doc.setFont('helvetica','bold');
          doc.text(item.label, M+6, y+2);
          setColor(180,210,230); doc.setFontSize(9.5); doc.setFont('helvetica','normal');
          const bl = doc.splitTextToSize(item.body, CW-16);
          doc.text(bl, M+6, y+9); y += h + 16;
        } else if (item.type === 'space') {
          y += item.h || 8;
        }
      });
      // page num
      setColor(58,85,117); doc.setFontSize(8);
      doc.text('- '+page+' -', W/2, 290, { align:'center' });
    }

    // ─ PAGE 2: 설계 및 개발 방법 ─
    addSection(1,
      '\uc6f9\uc0ac\uc774\ud2b8 \uc124\uacc4 \ubc0f \uac1c\ubc1c \ubc29\ubc95',
      '\u7F51\u7AD9\u8BBE\u8BA1\u4E0E\u5F00\u5019\u65B9\u6CD5', [
      { type:'heading', text: '1.1 \uc544\ud0a4\ud14d\uccb8 \uc124\uacc4 \uc6d0\uce59' },
      { type:'bullet', text: '\ub2e8\uc77c \ud30c\uc77c HTML \uc544\ud0a4\ud14d\uccb8: \ubaa8\ub4e0 CSS\uc640 JavaScript\ub97c \ud558\ub098\uc758 HTML \ud30c\uc77c\uc5d0 \ud1b5\ud569\ud558\uc5ec GitHub Pages\uc5d0 \uc9c0\uc6a9\ud55c \uac04\ub2e8\ud55c \ubc30\ud3ec\ub97c \uad6c\ud604\ud569\ub2c8\ub2e4.' },
      { type:'bullet', text: '\ubc18\uc751\ud615 \ub514\uc790\uc778: CSS Grid \ubc0f Flexbox\ub97c \ud65c\uc6a9\ud558\uc5ec \ub370\uc2a4\ud06c\ud0d1, \ud0dc\ube14\ub9bf, \ubaa8\ubc14\uc77c \ub4f1 \ub2e4\uc591\ud55c \ud654\uba74 \ud06c\uae30\uc5d0 \uc801\uc751\ub429\ub2c8\ub2e4.' },
      { type:'bullet', text: 'CDN \uc678\ubd80 \ub77c\uc774\ube0c\ub7ec\ub9ac \uc758\uc874: jsPDF (PDF \uc0dd\uc131), Google Fonts (CJK \ud3f0\ud2b8 \uc9c0\uc6d0) \ub4f1\uc758 CDN\uc744 \ud65c\uc6a9\ud558\uc5ec \ub85c\ucef4 \ud658\uacbd \uc124\uce58 \uc5c6\uc774 \uc2e4\ud589\ud569\ub2c8\ub2e4.' },
      { type:'space', h:6 },
      { type:'heading', text: '1.2 \ud504\ub860\ud2b8\uc5d4\ub4dc \uae30\uc220 \uc2a4\ud0dd' },
      { type:'card', label: 'HTML5', body: '\uc2dc\ub9e8\ud2f1 \ud0dc\uadf8\uc640 \uc811\uadfc\uc131 \ud45c\uc900\uc744 \uc900\uc218\ud55c \ucf58\ud150\uce20 \uad6c\uc870\ud654' },
      { type:'card', label: 'CSS3', body: 'CSS \ubcc0\uc218, \uc560\ub2c8\uba54\uc774\uc158, \ubc30\uacbd \ud6a8\uacfc, \uadf8\ub9ac\ub4dc \ub808\uc774\uc544\uc6c3\uc744 \ud65c\uc6a9\ud55c \uac1c\uc131 \uc788\ub294 \uc2dc\uc2a4\ud15c \uad6c\ud604' },
      { type:'card', label: 'Vanilla JavaScript', body: '\ucf54\ub4dc \uacbd\ub7c9\ud654\ub97c \uc704\ud574 \ud504\ub808\uc784\uc6cc\ud06c \uc5c6\uc774 DOM \uc870\uc791, \uc0c1\ud0dc \uad00\ub9ac, API \ud638\ucd9c \uc9c1\uc811 \uad6c\ud604' },
      { type:'space', h:6 },
      { type:'heading', text: '1.3 \ubcf4\uc548 \ub808\uc774\uc5b4 \uc124\uacc4' },
      { type:'bullet', text: 'AES-256 \uc554\ud638\ud654: \uc758\ub8cc \ub370\uc774\ud130\uc758 \uc800\uc7a5 \ubc0f \uc804\uc1a1 \uc2dc \uc5d4\ub4dc\ud22c\uc5d4\ub4dc \uc554\ud638\ud654\ub97c \uc801\uc6a9\ud558\uc5ec \ub370\uc774\ud130 \ube44\uacf5\uac1c\ub97c \ubcf4\uc7a5\ud569\ub2c8\ub2e4.' },
      { type:'bullet', text: 'JWT + OAuth 2.0: \uc0ac\uc6a9\uc790 \uc778\uc99d\uc5d0\ub294 JWT \ud1a0\ud070 \ubc0f OAuth 2.0 \ud504\ub85c\ud1a0\ucf5c\uc744 \uc801\uc6a9\ud558\uc5ec \ubcf4\uc548\uc131\uc744 \uac15\ud654\ud569\ub2c8\ub2e4.' },
      { type:'bullet', text: 'HTTPS / TLS 1.3: \ubaa8\ub4e0 \ub124\ud2b8\uc6cc\ud06c \ud1b5\uc2e0\uc740 TLS 1.3 \ud504\ub85c\ud1a0\ucf5c\ub85c \uc554\ud638\ud654\ub418\uc5b4 \uc911\uac04\uc790 \uacf5\uaca9\uc744 \ubc29\uc9c0\ud569\ub2c8\ub2e4.' },
      { type:'space', h:6 },
      { type:'heading', text: '1.4 \ubc30\ud3ec \ud504\ub85c\uc138\uc2a4' },
      { type:'text', text: 'GitHub Pages\ub97c \ud65c\uc6a9\ud55c \uc81c\ub85c \uc2e4\ube44\uc6a9 \uc815\uc801 \ud638\uc2a4\ud305 \ubc29\uc2dd\uc744 \uc0ac\uc6a9\ud569\ub2c8\ub2e4. \ub2e8\uc77c HTML \ud30c\uc77c \uc544\ud0a4\ud14d\uccb8 \ub355\ubd84\uc5d0 \uc11c\ubc84 \uc5c6\uc774\ub3c4 \uc989\uc2dc \ubc30\ud3ec\uac00 \uac00\ub2a5\ud558\uba70, \uc720\uc9c0\ubcf4\uc218 \ube44\uc6a9\uc744 \ucd5c\uc18c\ud654\ud569\ub2c8\ub2e4. iPad \ud658\uacbd\uc5d0\uc11c\ub3c4 \uc6d0\ud65c\ud55c \ud3b8\uc9d1 \ubc0f \uc5c5\ub85c\ub4dc\uac00 \uac00\ub2a5\ud569\ub2c8\ub2e4.' }
    ]);

    // ─ PAGE 3: 주요 기능 ─
    addSection(2,
      '\uc6f9\uc0ac\uc774\ud2b8 \uc8fc\uc694 \uae30\ub2a5 \uc18c\uac1c',
      '\u7F51\u7AD9\u4E3B\u8981\u529F\u80FD\u4ECB\u7ECD', [
      { type:'heading', text: '\uae30\ub2a5 1: \ub370\uc774\ud130 \uc554\ud638\ud654 \ubc0f \uc811\uadfc \uc81c\uc5b4' },
      { type:'text', text: 'AES-256 \uc5d4\ub4dc\ud22c\uc5d4\ub4dc \uc554\ud638\ud654 \uae30\uc220\uacfc \ub2e4\uce35 \uad8c\ud55c \uac80\uc99d \uba54\ucee4\ub2c8\uc998\uc744 \uc801\uc6a9\ud558\uc5ec \ud658\uc790 \uac1c\uc778\uc815\ubcf4 \ubc0f \uc758\ub8cc \uae30\ub85d\uc758 \uc548\uc804\ud55c \uc800\uc7a5\uacfc \uc804\uc1a1\uc744 \ubcf4\uc7a5\ud569\ub2c8\ub2e4.' },
      { type:'space', h:5 },
      { type:'heading', text: '\uae30\ub2a5 2: \uc2e4\uc2dc\uac04 \uc704\ud5d8 \ubaa8\ub2c8\ud130\ub9c1 \ub300\uc2dc\ubcf4\ub4dc' },
      { type:'text', text: '\uc2dc\uc2a4\ud15c \ubcf4\uc548 \ud604\ud669\uc744 \uc2dc\uac01\uc801\uc73c\ub85c \ud45c\uc2dc\ud558\uace0, \ube44\uc815\uc0c1 \uc811\uadfc \ud589\ub3d9, \ub370\uc774\ud130 \uc720\ucd9c \uc704\ud5d8 \ubc0f \ub124\ud2b8\uc6cc\ud06c \uce68\uc785 \uc774\ubca4\ud2b8\ub97c \uc2e4\uc2dc\uac04\uc73c\ub85c \ucd94\uc801\ud569\ub2c8\ub2e4. \uc0ac\uc6a9\uc790 \uc815\uc758 \uacbd\ubcf4 \uc784\uacc4\uac12 \uc124\uc815\uc744 \uc9c0\uc6d0\ud569\ub2c8\ub2e4.' },
      { type:'space', h:5 },
      { type:'heading', text: '\uae30\ub2a5 3: AI \uc9c0\ub2a5\ud615 \uc704\ud611 \ubd84\uc11d' },
      { type:'text', text: '\uba38\uc2e0\ub7ec\ub2dd \uae30\ubc18\uc758 \uc774\uc0c1 \ud589\ub3d9 \uac10\uc9c0 \uc5d4\uc9c4\uc774 \uc794\uc7ac\uc801 \ubcf4\uc548 \uc704\ud611\uc744 \uc790\ub3d9 \uc2dd\ubcc4\ud558\uace0, \uc9c0\ub2a5\uc801\uc778 \ucc98\ub9ac \ubc29\uc548\uc744 \uc81c\uc2dc\ud558\uc5ec \uc218\ub3d9 \uc6b4\uc601 \ube44\uc6a9\uc744 \uc808\uac10\ud569\ub2c8\ub2e4.' },
      { type:'space', h:5 },
      { type:'heading', text: '\uae30\ub2a5 4: \uccoC\ubc95 \uac10\uc0ac \ubc0f \ubcf4\uace0\uc11c \uc0dd\uc131' },
      { type:'text', text: 'HIPAA, GDPR, \ud55c\uad6d \uac1c\uc778\uc815\ubcf4\ubcf4\ud638\ubc95(\ud53c\ud30c) \ub4f1 \uad6d\uc81c \uc758\ub8cc \ub370\uc774\ud130 \ud504\ub77c\uc774\ubc84\uc2dc \ud45c\uc900\uc744 \uc900\uc218\ud558\uba70, \uccoC\ubc95 \uac10\uc0ac \ubcf4\uace0\uc11c\ub97c \uc790\ub3d9 \uc0dd\uc131\ud558\uace0 PDF \ud615\uc2dd \ub0b4\ubcf4\ub0b4\uae30\ub97c \uc9c0\uc6d0\ud569\ub2c8\ub2e4.' },
      { type:'space', h:5 },
      { type:'heading', text: '\uae30\ub2a5 5: API \ubcf4\uc548 \ud1b5\ud569 \uad00\ub9ac' },
      { type:'text', text: '\uc758\ub8cc \uae30\uae30, HIS \uc2dc\uc2a4\ud15c, \uc11c\ub4dc\ud30c\ud2f0 \uc11c\ube44\uc2a4\uc758 API \uc811\uadfc\uc744 \ud1b5\ud569 \uad00\ub9ac\ud558\uba70 OAuth 2.0 \uc778\uc99d, \uc18d\ub3c4 \uc81c\ud55c \ubc0f \ubcf4\uc548 \uc�d1\uc2a4 \ud14c\uc2a4\ud2b8 \ud658\uacbd\uc744 \uc81c\uacf5\ud569\ub2c8\ub2e4.' },
      { type:'space', h:5 },
      { type:'heading', text: '\uae30\ub2a5 6: \uc6d0\ud074\ub9ad \ud55c\uad6d\uc5b4 PDF \ub0b4\ubcf4\ub0b4\uae30' },
      { type:'text', text: '\ud398\uc774\uc9c0 \uc6b0\uce21 \ud558\ub2e8\uc758 \ub2e4\uc6b4\ub85c\ub4dc \ubc84\ud2bc\uc744 \ub2e8 \ud55c \ubc88 \ud074\ub9ad\ud558\uba74 \uc124\uacc4 \uc124\uba85, \uae30\ub2a5 \uc18c\uac1c, \uae30\ub300 \ud6a8\uacfc \ubc0f \ubcf4\ucda9 \uc124\uba85\uc774 \ud3ec\ud568\ub41c \uc644\uc804\ud55c \ud55c\uad6d\uc5b4 PDF \ubb38\uc11c\ub97c \ub2e4\uc6b4\ub85c\ub4dc\ud560 \uc218 \uc788\uc2b5\ub2c8\ub2e4. jsPDF \ub77c\uc774\ube0c\ub7ec\ub9ac\ub97c \ud65c\uc6a9\ud558\uc5ec \ud074\ub77c\uc774\uc5b8\ud2b8 \uce21\uc5d0\uc11c \uc9c1\uc811 \uc0dd\uc131\ub429\ub2c8\ub2e4.' }
    ]);

    // ─ PAGE 4: 기대 효과 ─
    addSection(3,
      '\ud504\ub85c\uc81d\ud2b8 \uae30\ub300 \ud6a8\uacfc \ubc0f \uc751\uc6a9 \uac00\uce58',
      '\u9879\u76EE\u9884\u671F\u6548\u679C\u4E0E\u5E94\u7528\u4EF7\u5024', [
      { type:'heading', text: '3.1 \ubcf4\uc548\uc131 \uac15\ud654 \ud6a8\uacfc' },
      { type:'bullet', text: '\uc758\ub8cc \ub370\uc774\ud130 \uce68\ud574 \uc704\ud5d8 \ucd5c\ub300 90% \uac10\uc18c \uc608\uc0c1: AES-256 \uc554\ud638\ud654\uc640 \ub2e4\uce35 \uc778\uc99d \uc801\uc6a9\uc73c\ub85c \ubd88\ubc95 \uc811\uadfc \uc2dc\ub3c4 \ucc28\ub2e8' },
      { type:'bullet', text: '\uc2e4\uc2dc\uac04 \uc704\ud611 \uad6c\uc81c \ub2a5\ub825: 0.3\ucd08 \uc774\ub0b4 \uc774\uc0c1 \ud0d0\uc9c0 \ubc0f \uc790\ub3d9 \ucc28\ub2e8 \uc2dc\uc2a4\ud15c\uc73c\ub85c \ubcf4\uc548 \uc0ac\uace0 \uc608\ubc29' },
      { type:'bullet', text: '99.9% \uc2dc\uc2a4\ud15c \uac00\uc6a9\ub960: \uace0\uac00\uc6a9\uc131 \uc544\ud0a4\ud14d\uccb8\ub85c \uc758\ub8cc \uc11c\ube44\uc2a4 \uc911\ub2e8 \uc5c6\uc774 \uc548\uc815\uc801 \uc6b4\uc601' },
      { type:'space', h:6 },
      { type:'heading', text: '3.2 \ucffD\uc758\ucccD \ube44\uc6a9 \uc808\uac10 \ud6a8\uacfc' },
      { type:'bullet', text: '\uc790\ub3d9 \ucCoC\ubc95 \uac10\uc0ac\ub85c \uc218\ub3d9 \uac80\ud1a0 \uc5c5\ubb34 60% \uc808\uac10 \uc608\uc0c1' },
      { type:'bullet', text: 'HIPAA, GDPR, \ud53c\ud30c \ub4f1 \ubcf5\uc218 \uad6c\uc81c \uae30\uc900 \ub3d9\uc2dc \uc900\uc218\ub85c \uad00\ub9ac \ud6a8\uc728\ud654' },
      { type:'bullet', text: '\uc77c\uc6d0\ud654\ub41c \ubcf4\uace0\uc11c \uc790\ub3d9\ud654\ub85c \uac10\uc0ac \uac00\ub2a5 \uae30\uac04 \uc6d0\ub0b4 \ubcf4\uace0\uc11c \uc81c\uc99d\uc2dc \uac04 30% \ub2e8\ucd95' },
      { type:'space', h:6 },
      { type:'heading', text: '3.3 \uc0ac\ud68c\uc801 \uac00\uce58 \ubc0f \uc2a4\ucf00\uc77c\ub7ec\ube4c\ub9ac\ud2f0' },
      { type:'text', text: '\ub514\uc9c0\ud138 \ud5ec\uc2a4\ucF00\uc5b4 \uc2dc\uc7a5\uc774 \uc5f0\ud3c9\uade0 15% \uc131\uc7a5\ud558\ub294 \ud55c\uad6d\uc5d0\uc11c \uc548\uc804\ud55c \uc758\ub8cc\ub370\uc774\ud130 \uad00\ub9ac\ub294 \uc2d0\ub8b0 \uad6c\ucd95\uc758 \ud575\uc2ec\uc785\ub2c8\ub2e4. \uc774 \ud50c\ub7ab\ud3fc\uc740 \uc911\uc18c\ud615 \ubcd1\uc6d0\ubd80\ud130 \ub300\ud615 \uc758\ub8cc\uae30\uad00\uae4c\uc9c0 \uc801\uc6a9 \uac00\ub2a5\ud558\uba70, API \uc9c0\ud5a5 \uc544\ud0a4\ud14d\uccb8\ub85c \uc804\uc790\uc758\ubb34\uae30\ub85d(EMR), \uc6d0\uaca9\uc9c4\ub8cc \ud50c\ub7ab\ud3fc, \uc758\ub8cc IoT \ub514\ubc14\uc774\uc2a4 \ub4f1\uacfc \uc6d0\ud65c\ud55c \ud1b5\ud569\uc774 \uac00\ub2a5\ud569\ub2c8\ub2e4.' },
      { type:'space', h:6 },
      { type:'heading', text: '3.4 \uad50\uc721\uc801 \ud65c\uc6a9 \uac00\uce58' },
      { type:'text', text: '\uc774 \ud504\ub85c\uc81d\ud2b8\ub294 \ub514\uc9c0\ud138 \ud5ec\uc2a4\ucF00\uc5b4 \ubcf4\uc548 \uc2e4\uc2b5 \ub3c4\uad6c\ub85c\uc11c\ub3c4 \ud65c\uc6a9\ub429\ub2c8\ub2e4. \uac15\uc758\ub97c \ub4e3\ub294 \ud559\uc0dd\ub4e4\uc774 \uc2e4\uc81c \ubcf4\uc548 \ub300\uc2dc\ubcf4\ub4dc\ub97c \ud1b5\ud574 \ub9ac\uc2a4\ud06c \uad00\ub9ac, \ub370\uc774\ud130 \uc554\ud638\ud654, \uccoC\ubc95 \uac10\uc0ac \ub4f1\uc758 \uac1c\ub150\uc744 \uc9c1\uad00\uc801\uc73c\ub85c \ud559\uc2b5\ud560 \uc218 \uc788\uc2b5\ub2c8\ub2e4.' }
    ]);

    // ─ PAGE 5: 보충 설명 ─
    addSection(4,
      '\uae30\ud0c0 \uad00\ub828 \ubcf4\ucda9 \uc124\uba85',
      '\u5176\u4F59\u76F8\u5173\u8865\u5145\u8BF4\u660E', [
      { type:'heading', text: '4.1 \uae30\uc220\uc801 \ud55c\uacc4 \ubc0f \ud5a5\ud6c4 \uac1c\uc120 \uc0ac\ud56d' },
      { type:'bullet', text: '\ud604\uc7ac \ube84\ub300\uc5d4\ub4dc\uac00 \uc5c6\ub294 \uc21c\uc218 \ud504\ub860\ud2b8\uc5d4\ub4dc \uad6c\uc870\ub85c, \uc2e4\uc81c \uc11c\ubc84 \uc5f0\ub3d9 \uc2dc \uc778\uc99d \uc11c\ubc84\uc640 \ub370\uc774\ud130\ubca0\uc774\uc2a4 \ud1b5\ud569\uc774 \ud544\uc694\ud569\ub2c8\ub2e4.' },
      { type:'bullet', text: 'PDF \ub0b4\ubcf4\ub0b4\uae30 \uae30\ub2a5\uc740 jsPDF \ub77c\uc774\ube0c\ub7ec\ub9ac\ub97c \uc0ac\uc6a9\ud558\ubbc0\ub85c CJK \ud55c\uc790 \ub80c\ub354\ub9c1\uc740 \uae30\ubcf8 \ube34\ud2b8\ub9f5 \ud3f0\ud2b8\ub85c \ucc98\ub9ac\ub418\uba70, \ud5a5\ud6c4 \uc720\ub2c8\ucf54\ub4dc \ud3f0\ud2b8 \uc778\ub7a8 \uc5c5\uadf8\ub808\uc774\ub4dc\uac00 \ud544\uc694\ud569\ub2c8\ub2e4.' },
      { type:'bullet', text: '\ub300\uc6a9\ub7c9 \uc758\ub8cc \ub370\uc774\ud130 \uccab\ub9ac\ub97c \uc704\ud55c \ubd84\uc0b0 \uce90\uc2dc \ubc0f \ub370\uc774\ud130\ubca0\uc774\uc2a4 \ud074\ub7ec\uc2a4\ud130\ub9c1 \uae30\ub2a5\uc774 \ucd94\ud6c4 \ubc84\uc804\uc5d0 \ucd94\uac00\ub420 \uc608\uc815\uc785\ub2c8\ub2e4.' },
      { type:'space', h:6 },
      { type:'heading', text: '4.2 \ucc38\uace0 \ud45c\uc900 \ubc0f \ubb38\ud5cc' },
      { type:'card', label: 'HIPAA (Health Insurance Portability and Accountability Act)', body: '\ubbf8\uad6d \uc758\ub8cc \uc815\ubcf4 \ubcf4\ud638 \ubc0f \uc774\ub3d9\uc131\uc5d0 \uad00\ud55c \ubc95\ub960. \ud658\uc790 \ub370\uc774\ud130\uc758 \uae30\ubc00\uc131, \ubb34\uacb0\uc131, \uac00\uc6a9\uc131 \ubcf4\uc7a5\uc744 \uaddc\uc815.' },
      { type:'card', label: '\ud55c\uad6d \uac1c\uc778\uc815\ubcf4\ubcf4\ud638\ubc95 (\ud53c\ud30c)', body: '\uac1c\uc778\uc815\ubcf4\uc758 \uc218\uc9d1, \uc774\uc6a9, \uc81c\uacf5 \ub4f1\uc5d0 \uad00\ud55c \uae30\ubcf8 \uc6d0\uce59\uacfc \uc815\ubcf4\uc8fc\uccb4\uc758 \uad8c\ub9ac\ub97c \uaddc\uc815\ud558\ub294 \ud55c\uad6d \uc8fc\uc694 \uac1c\uc778\uc815\ubcf4 \ubcf4\ud638 \ubc95\ub960.' },
      { type:'card', label: 'ISO/IEC 27001', body: '\uc815\ubcf4 \ubcf4\uc548 \uad00\ub9ac \uc2dc\uc2a4\ud15c(ISMS)\uc5d0 \uad00\ud55c \uad6d\uc81c \ud45c\uc900. \uc870\uc9c1\uc758 \uc815\ubcf4 \ubcf4\uc548 \ub9ac\uc2a4\ud06c \uad00\ub9ac \uccb4\uacc4\ub97c \uaddc\uc815.' },
      { type:'space', h:6 },
      { type:'heading', text: '4.3 \uacbd\uc9c4\ub300\ud68c \ud504\ub85c\uc81d\ud2b8 \uc120\uc5b8' },
      { type:'text', text: '\ubcf8 \ud504\ub85c\uc81d\ud2b8\ub294 \ub514\uc9c0\ud138 \ud5ec\uc2a4 \uc758\ub8cc (\uc8fc\uc81c: \uc0b0\uc5c5 \ubcf4\uc548 | \ud50c\ub7ab\ud3fc \uac1c\ubc1c \uacbd\uc9c4\ub300\ud68c)\ub97c \uc704\ud574 \uc81c\uc791\ub41c \ud559\uc2b5 \ubaa9\uc801\uc758 \uc6f9\uc0ac\uc774\ud2b8\uc785\ub2c8\ub2e4. \ubaa8\ub4e0 \ucf58\ud150\uce20\ub294 \uad50\uc721 \ubaa9\uc801\uc73c\ub85c \uc81c\uc791\ub418\uc5c8\uc73c\uba70, \uc2e4\uc81c \uc758\ub8cc \uc11c\ube44\uc2a4\uc5d0 \uc9c1\uc811 \uc801\uc6a9\ud558\ub294 \uc911\uc5d0\ub294 \ucd94\uac00\uc801\uc778 \uc804\ubb38\uac00 \uac80\ud1a0\uac00 \ud544\uc694\ud569\ub2c8\ub2e4. \ubcf8 \uc0ac\uc774\ud2b8\uc758 \ubaa8\ub4e0 \uac1c\uc778 \ub370\uc774\ud130 \uc608\uc2dc\ub294 \uac00\uc0c1\uc758 \ub370\uc774\ud130\ub85c, \uc2e4\uc81c \ud658\uc790 \uc815\ubcf4\ub97c \ud3ec\ud568\ud558\uc9c0 \uc54a\uc2b5\ub2c8\ub2e4.' }
    ]);

    doc.save('DigiHealth_Guard_\ud55c\uad6d\uc5b4.pdf');

  } catch(e) {
    alert('PDF 생성 중 오류가 발생했습니다: ' + e.message);
    console.error(e);
  }

  btn.innerHTML = '<span class="icon">⬇</span><span>한국어 PDF</span>';
  btn.disabled = false;
}
</script>
</body>
</html>
