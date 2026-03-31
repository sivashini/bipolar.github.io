<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Bipolar Factory — Dedicated Technology Partner</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=Syne+Mono&family=DM+Sans:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0b;
    --surface: #111114;
    --border: #1e1e24;
    --electric: #00e5ff;
    --volt: #d4ff00;
    --ember: #ff4d1c;
    --text: #e8e8ec;
    --muted: #5a5a6e;
    --white: #ffffff;
    --font-display: 'Syne', sans-serif;
    --font-mono: 'Syne Mono', monospace;
    --font-body: 'DM Sans', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 10px; height: 10px;
    background: var(--electric);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--electric);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: left 0.12s ease, top 0.12s ease, width 0.2s, height 0.2s, border-color 0.2s;
    opacity: 0.6;
  }
  body:hover .cursor { opacity: 1; }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 3px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--electric); }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 20px 48px;
    background: rgba(10,10,11,0.8);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    transition: padding 0.3s;
  }
  nav.scrolled { padding: 14px 48px; }
  .logo {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1.2rem;
    letter-spacing: -0.02em;
    color: var(--white);
    text-decoration: none;
    display: flex; align-items: center; gap: 10px;
  }
  .logo-dot {
    width: 8px; height: 8px;
    background: var(--electric);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%,100% { box-shadow: 0 0 0 0 rgba(0,229,255,0.4); }
    50% { box-shadow: 0 0 0 8px rgba(0,229,255,0); }
  }
  .nav-links {
    display: flex; gap: 36px; list-style: none;
  }
  .nav-links a {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    transition: color 0.2s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -2px; left: 0; right: 0;
    height: 1px; background: var(--electric);
    transform: scaleX(0);
    transition: transform 0.2s;
    transform-origin: left;
  }
  .nav-links a:hover { color: var(--electric); }
  .nav-links a:hover::after { transform: scaleX(1); }
  .nav-cta {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--bg);
    background: var(--electric);
    padding: 10px 22px;
    border: none;
    text-decoration: none;
    transition: background 0.2s, transform 0.15s;
    font-weight: 700;
  }
  .nav-cta:hover { background: var(--volt); transform: translateY(-1px); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center;
    padding: 120px 48px 80px;
    position: relative;
    overflow: hidden;
  }

  /* Grid lines background */
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
  }

  .hero-noise {
    position: absolute; inset: 0;
    opacity: 0.04;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    background-size: 200px 200px;
    z-index: 0;
  }

  /* Glow orb */
  .hero-glow {
    position: absolute;
    top: -200px; right: -100px;
    width: 700px; height: 700px;
    background: radial-gradient(ellipse, rgba(0,229,255,0.07) 0%, transparent 70%);
    z-index: 0;
    animation: drift 8s ease-in-out infinite alternate;
  }
  @keyframes drift {
    0% { transform: translate(0, 0); }
    100% { transform: translate(-40px, 60px); }
  }

  .hero-content { position: relative; z-index: 1; max-width: 900px; }

  .hero-tag {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--electric);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 28px;
    display: flex; align-items: center; gap: 12px;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards;
  }
  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 32px; height: 1px;
    background: var(--electric);
  }

  h1 {
    font-family: var(--font-display);
    font-size: clamp(3.5rem, 9vw, 8rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.04em;
    color: var(--white);
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.15s forwards;
  }
  h1 em {
    font-style: normal;
    color: transparent;
    -webkit-text-stroke: 1.5px var(--electric);
  }
  h1 .accent { color: var(--electric); }

  .hero-sub {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.7;
    margin-bottom: 48px;
    font-weight: 300;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.3s forwards;
  }

  .hero-actions {
    display: flex; gap: 16px; align-items: center; flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.45s forwards;
  }
  .btn-primary {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--bg);
    background: var(--electric);
    padding: 14px 32px;
    text-decoration: none;
    font-weight: 700;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .btn-primary::after {
    content: '→';
    margin-left: 8px;
    display: inline-block;
    transition: transform 0.2s;
  }
  .btn-primary:hover { background: var(--volt); }
  .btn-primary:hover::after { transform: translateX(4px); }
  .btn-ghost {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    padding: 14px 0;
    border-bottom: 1px solid var(--border);
    transition: color 0.2s, border-color 0.2s;
  }
  .btn-ghost:hover { color: var(--text); border-color: var(--muted); }

  .hero-stats {
    position: absolute;
    bottom: 60px; right: 48px;
    display: flex; gap: 48px;
    z-index: 1;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.6s forwards;
  }
  .stat { text-align: right; }
  .stat-num {
    font-family: var(--font-display);
    font-size: 2.4rem;
    font-weight: 800;
    color: var(--white);
    line-height: 1;
  }
  .stat-num span { color: var(--electric); }
  .stat-label {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    color: var(--muted);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-top: 4px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* MARQUEE */
  .marquee-wrap {
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    background: var(--surface);
    padding: 14px 0;
    overflow: hidden;
  }
  .marquee-track {
    display: flex; gap: 0;
    animation: marquee 22s linear infinite;
    width: max-content;
  }
  .marquee-item {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--muted);
    padding: 0 40px;
    white-space: nowrap;
  }
  .marquee-item .dot { color: var(--electric); margin-right: 40px; }
  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* SECTIONS */
  section { padding: 120px 48px; }
  .section-tag {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--electric);
    margin-bottom: 20px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-tag::before {
    content: attr(data-n);
    color: var(--muted);
  }

  h2 {
    font-family: var(--font-display);
    font-size: clamp(2.2rem, 5vw, 4rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.03em;
    color: var(--white);
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
    margin-top: 64px;
  }
  .about-text p {
    color: var(--muted);
    font-size: 1.05rem;
    line-height: 1.75;
    margin-bottom: 20px;
    font-weight: 300;
  }
  .about-text p strong { color: var(--text); font-weight: 400; }
  .values-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
  }
  .value-item {
    background: var(--surface);
    padding: 28px 24px;
    transition: background 0.2s;
  }
  .value-item:hover { background: #16161a; }
  .value-icon {
    font-size: 1.4rem;
    margin-bottom: 12px;
    display: block;
  }
  .value-name {
    font-family: var(--font-display);
    font-size: 0.95rem;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 6px;
  }
  .value-desc {
    font-size: 0.8rem;
    color: var(--muted);
    line-height: 1.5;
  }

  /* PRODUCTS */
  .products-section { background: var(--surface); }
  .products-header {
    display: flex; justify-content: space-between; align-items: flex-end;
    margin-bottom: 64px; flex-wrap: wrap; gap: 24px;
  }
  .products-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
  }
  .product-card {
    background: var(--bg);
    padding: 40px 36px;
    position: relative;
    overflow: hidden;
    transition: background 0.25s;
    cursor: pointer;
  }
  .product-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--electric);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s ease;
  }
  .product-card:hover::before { transform: scaleX(1); }
  .product-card:hover { background: #0e0e12; }
  .product-num {
    font-family: var(--font-mono);
    font-size: 0.6rem;
    color: var(--electric);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 24px;
    opacity: 0.7;
  }
  .product-name {
    font-family: var(--font-display);
    font-size: 1.6rem;
    font-weight: 800;
    color: var(--white);
    letter-spacing: -0.02em;
    margin-bottom: 16px;
    line-height: 1.1;
  }
  .product-tag {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    background: rgba(0,229,255,0.1);
    color: var(--electric);
    padding: 4px 10px;
    margin-bottom: 20px;
  }
  .product-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.65;
    font-weight: 300;
  }
  .product-arrow {
    position: absolute; bottom: 32px; right: 32px;
    font-size: 1.2rem;
    color: var(--border);
    transition: color 0.2s, transform 0.2s;
  }
  .product-card:hover .product-arrow { color: var(--electric); transform: translate(3px,-3px); }

  /* SERVICES */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    margin-top: 64px;
  }
  .service-item {
    background: var(--bg);
    padding: 40px;
    display: flex; gap: 24px;
    transition: background 0.2s;
  }
  .service-item:hover { background: var(--surface); }
  .service-num {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    color: var(--electric);
    opacity: 0.5;
    padding-top: 3px;
  }
  .service-name {
    font-family: var(--font-display);
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 10px;
    letter-spacing: -0.01em;
  }
  .service-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.65;
    font-weight: 300;
  }

  /* CASE STUDIES */
  .cases-section { background: var(--surface); }
  .cases-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
    margin-top: 64px;
  }
  .case-card {
    border: 1px solid var(--border);
    padding: 36px;
    position: relative;
    transition: border-color 0.2s, transform 0.2s;
  }
  .case-card:hover { border-color: var(--electric); transform: translateY(-4px); }
  .case-industry {
    font-family: var(--font-mono);
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ember);
    margin-bottom: 16px;
  }
  .case-title {
    font-family: var(--font-display);
    font-size: 1.3rem;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 12px;
    letter-spacing: -0.01em;
    line-height: 1.2;
  }
  .case-client {
    font-size: 0.82rem;
    color: var(--muted);
    font-weight: 300;
    line-height: 1.6;
  }
  .case-quote {
    margin-top: 24px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    font-size: 0.82rem;
    color: var(--muted);
    font-style: italic;
    line-height: 1.65;
    font-weight: 300;
  }
  .case-author {
    margin-top: 12px;
    font-family: var(--font-mono);
    font-size: 0.65rem;
    color: var(--electric);
    letter-spacing: 0.1em;
  }

  /* INDUSTRIES */
  .industries-row {
    display: flex; flex-wrap: wrap; gap: 12px;
    margin-top: 48px;
  }
  .industry-pill {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    border: 1px solid var(--border);
    padding: 10px 20px;
    transition: all 0.2s;
  }
  .industry-pill:hover { border-color: var(--electric); color: var(--electric); }

  /* MANIFESTO */
  .manifesto {
    position: relative;
    overflow: hidden;
    text-align: center;
    background: linear-gradient(180deg, var(--bg) 0%, #06090f 100%);
  }
  .manifesto::before {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
  }
  .manifesto-content { position: relative; z-index: 1; max-width: 780px; margin: 0 auto; }
  .manifesto h2 {
    font-size: clamp(2.8rem, 7vw, 6rem);
    margin-bottom: 28px;
  }
  .manifesto p {
    font-size: 1.1rem;
    color: var(--muted);
    line-height: 1.8;
    font-weight: 300;
    margin-bottom: 48px;
  }
  .manifesto-glow {
    position: absolute;
    bottom: -100px; left: 50%;
    transform: translateX(-50%);
    width: 500px; height: 400px;
    background: radial-gradient(ellipse, rgba(0,229,255,0.08) 0%, transparent 70%);
  }

  /* FOOTER */
  footer {
    background: var(--surface);
    border-top: 1px solid var(--border);
    padding: 64px 48px 40px;
  }
  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 48px;
    margin-bottom: 48px;
  }
  .footer-brand .logo { margin-bottom: 16px; display: inline-flex; }
  .footer-brand p {
    font-size: 0.85rem;
    color: var(--muted);
    line-height: 1.7;
    max-width: 260px;
    font-weight: 300;
  }
  .footer-col h4 {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 20px;
  }
  .footer-col ul { list-style: none; }
  .footer-col li { margin-bottom: 10px; }
  .footer-col a {
    font-size: 0.88rem;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .footer-col a:hover { color: var(--electric); }
  .footer-address {
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.7;
    font-style: normal;
    font-weight: 300;
  }
  .footer-bottom {
    border-top: 1px solid var(--border);
    padding-top: 24px;
    display: flex; justify-content: space-between; align-items: center;
  }
  .footer-bottom p {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    color: var(--muted);
  }
  .footer-bottom span { color: var(--electric); }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(32px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }

  /* MOBILE */
  @media (max-width: 900px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    section { padding: 80px 24px; }
    .hero { padding: 100px 24px 120px; }
    .hero-stats { right: 24px; gap: 28px; }
    .about-grid, .products-grid, .cases-grid { grid-template-columns: 1fr; }
    .services-grid { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr 1fr; }
    h1 { font-size: 3rem; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="logo">
    <span class="logo-dot"></span>
    Bipolar Factory
  </a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#products">Products</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Let's Build</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-noise"></div>
  <div class="hero-glow"></div>
  <div class="hero-content">
    <div class="hero-tag" data-n="">Dedicated Technology Partner · Est. 2020 · Coimbatore</div>
    <h1>Build<br/><em>Bold.</em><br/>Ship <span class="accent">Real.</span></h1>
    <p class="hero-sub">We are a collective of dreamers, thinkers, and doers — harnessing technology to solve real problems for real people. Innovations of tomorrow, delivered today.</p>
    <div class="hero-actions">
      <a href="#products" class="btn-primary">Explore Products</a>
      <a href="#work" class="btn-ghost">See Case Studies</a>
    </div>
  </div>
  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">4<span>+</span></div>
      <div class="stat-label">Years Operating</div>
    </div>
    <div class="stat">
      <div class="stat-num">3</div>
      <div class="stat-label">SaaS Products</div>
    </div>
    <div class="stat">
      <div class="stat-num">6<span>+</span></div>
      <div class="stat-label">Industries Served</div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track" id="marquee">
    <span class="marquee-item">Video Intelligence <span class="dot">◆</span></span>
    <span class="marquee-item">Custom Application Dev <span class="dot">◆</span></span>
    <span class="marquee-item">Digital Transformation <span class="dot">◆</span></span>
    <span class="marquee-item">Decentralised Creator Economy <span class="dot">◆</span></span>
    <span class="marquee-item">Election Tech <span class="dot">◆</span></span>
    <span class="marquee-item">Indoor GPS & Tracking <span class="dot">◆</span></span>
    <span class="marquee-item">Make in India <span class="dot">◆</span></span>
    <span class="marquee-item">Technical Consulting <span class="dot">◆</span></span>
    <span class="marquee-item">Video Intelligence <span class="dot">◆</span></span>
    <span class="marquee-item">Custom Application Dev <span class="dot">◆</span></span>
    <span class="marquee-item">Digital Transformation <span class="dot">◆</span></span>
    <span class="marquee-item">Decentralised Creator Economy <span class="dot">◆</span></span>
    <span class="marquee-item">Election Tech <span class="dot">◆</span></span>
    <span class="marquee-item">Indoor GPS & Tracking <span class="dot">◆</span></span>
    <span class="marquee-item">Make in India <span class="dot">◆</span></span>
    <span class="marquee-item">Technical Consulting <span class="dot">◆</span></span>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-tag" data-n="01 —">Who We Are</div>
  <h2 class="reveal">Not just a vendor.<br/>Your technology partner.</h2>
  <div class="about-grid">
    <div class="about-text reveal reveal-delay-1">
      <p>Founded in 2020, Bipolar Factory is a <strong>dynamic technology company</strong> headquartered in Coimbatore, Tamil Nadu. We're not your typical IT firm — we're a mix of builders, researchers, and strategists united by one obsession: <strong>making technology work for people.</strong></p>
      <p>From automated election systems in Bihar to indoor GPS for textile factories in Coimbatore, we don't pick small problems. We dig deep into industries that are ripe for disruption and build solutions that <strong>actually move the needle.</strong></p>
      <p>Our mission: be the torchbearers of Make in India products on a global stage — combining fun with professionalism, underdog grit with technical excellence.</p>
    </div>
    <div class="values-grid reveal reveal-delay-2">
      <div class="value-item">
        <span class="value-icon">⚡</span>
        <div class="value-name">Innovation</div>
        <div class="value-desc">Pioneering solutions that redefine industries.</div>
      </div>
      <div class="value-item">
        <span class="value-icon">🎯</span>
        <div class="value-name">Quality</div>
        <div class="value-desc">Excellence in every product and service delivered.</div>
      </div>
      <div class="value-item">
        <span class="value-icon">📡</span>
        <div class="value-name">Continuous Learning</div>
        <div class="value-desc">Adapting and evolving in a dynamic landscape.</div>
      </div>
      <div class="value-item">
        <span class="value-icon">🤝</span>
        <div class="value-name">Client-First</div>
        <div class="value-desc">Putting customers at the heart of everything.</div>
      </div>
      <div class="value-item">
        <span class="value-icon">🔥</span>
        <div class="value-name">Passion</div>
        <div class="value-desc">Infusing real enthusiasm into everything we do.</div>
      </div>
      <div class="value-item">
        <span class="value-icon">🌱</span>
        <div class="value-name">Humility</div>
        <div class="value-desc">Embracing the learning journey with an open mind.</div>
      </div>
    </div>
  </div>
</section>

<!-- PRODUCTS -->
<section id="products" class="products-section">
  <div class="products-header">
    <div>
      <div class="section-tag" data-n="02 —">Our Products</div>
      <h2 class="reveal">Signature software.<br/>Built from scratch.</h2>
    </div>
    <a href="#contact" class="btn-ghost">View all →</a>
  </div>
  <div class="products-grid">
    <div class="product-card reveal">
      <div class="product-num">Product 01</div>
      <div class="product-name">OLY Store Sync</div>
      <div class="product-tag">SaaS · Video Security</div>
      <p class="product-desc">Unlock the full potential of your video security network. A revolutionary SaaS platform that connects, manages, and extracts intelligence from distributed camera infrastructure across your retail estate.</p>
      <div class="product-arrow">↗</div>
    </div>
    <div class="product-card reveal reveal-delay-1">
      <div class="product-num">Product 02</div>
      <div class="product-name">OLY Control Center</div>
      <div class="product-tag">Video Management · Enterprise</div>
      <p class="product-desc">A Video Management System unlike anything that has ever worked for you. Centralized intelligence, unified control, and real-time monitoring designed around how operators actually think and act.</p>
      <div class="product-arrow">↗</div>
    </div>
    <div class="product-card reveal reveal-delay-2">
      <div class="product-num">Product 03</div>
      <div class="product-name">Metawood</div>
      <div class="product-tag">Web3 · Streaming · Creator Economy</div>
      <p class="product-desc">A gamified streaming platform and a decentralised creator economy — all rolled into one. Where creators own their work, audiences own their experience, and the platform serves both.</p>
      <div class="product-arrow">↗</div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="section-tag" data-n="03 —">Technology Partnership</div>
  <h2 class="reveal">We go where<br/>the problem is.</h2>
  <div class="services-grid">
    <div class="service-item reveal">
      <div class="service-num">01</div>
      <div>
        <div class="service-name">Technical Consulting</div>
        <p class="service-desc">Our consultants dig into your systems, workflows, and bottlenecks — then hand you a strategy built for your exact challenges. No templates, no generic decks.</p>
      </div>
    </div>
    <div class="service-item reveal reveal-delay-1">
      <div class="service-num">02</div>
      <div>
        <div class="service-name">Digital Transformation</div>
        <p class="service-desc">Comprehensive transformation strategies that redefine how you operate and deliver value to customers. From legacy modernization to full-stack digital reinvention.</p>
      </div>
    </div>
    <div class="service-item reveal reveal-delay-2">
      <div class="service-num">03</div>
      <div>
        <div class="service-name">Research & Development</div>
        <p class="service-desc">Dedicated research into tech trends and emerging fields. We track what's coming so you're not reacting to the future — you're already there.</p>
      </div>
    </div>
    <div class="service-item reveal reveal-delay-3">
      <div class="service-num">04</div>
      <div>
        <div class="service-name">Custom Application Development</div>
        <p class="service-desc">Bring your vision to life with applications meticulously crafted for your exact business needs. We own the full lifecycle — from architecture to deployment.</p>
      </div>
    </div>
  </div>

  <div class="reveal" style="margin-top:64px;">
    <div class="section-tag" data-n="">Industries We Serve</div>
    <div class="industries-row">
      <div class="industry-pill">Retail</div>
      <div class="industry-pill">Manufacturing</div>
      <div class="industry-pill">Civil Aviation</div>
      <div class="industry-pill">Road Safety</div>
      <div class="industry-pill">Entertainment</div>
      <div class="industry-pill">Content Creation</div>
      <div class="industry-pill">Governance</div>
      <div class="industry-pill">Waste Management</div>
      <div class="industry-pill">Textile</div>
    </div>
  </div>
</section>

<!-- CASE STUDIES -->
<section id="work" class="cases-section">
  <div class="section-tag" data-n="04 —">Work & Impact</div>
  <h2 class="reveal">Problems we've<br/>actually solved.</h2>
  <div class="cases-grid">
    <div class="case-card reveal">
      <div class="case-industry">Governance · Bihar</div>
      <div class="case-title">Automated Vote Counting System</div>
      <p class="case-client">Bihar State Election Commission — delivering a transparent, accurate counting process for one of India's most critical democratic exercises.</p>
      <div class="case-quote">"Their solution ensured accuracy and efficiency in a critical democratic process — a testament to their understanding of complex systems."</div>
      <div class="case-author">Gajapathy Chakravarthy · iNET Secure Labs</div>
    </div>
    <div class="case-card reveal reveal-delay-1">
      <div class="case-industry">Waste Management · EPR</div>
      <div class="case-title">EPR Portal for Zigma</div>
      <p class="case-client">A digital backbone for Zigma's Extended Producer Responsibility services — modernizing waste management operations and amplifying environmental impact.</p>
      <div class="case-quote">"A cornerstone in modernizing our waste management services — their expertise has significantly elevated our operational efficiency and environmental impact."</div>
      <div class="case-author">Boopathy Dharmaraj · Zigma</div>
    </div>
    <div class="case-card reveal reveal-delay-2">
      <div class="case-industry">Textile · Coimbatore</div>
      <div class="case-title">Indoor GPS for Weaving Units</div>
      <p class="case-client">Precision indoor positioning system for WoTA — transforming worker productivity and operational accuracy across weaving factory floors in Coimbatore.</p>
      <div class="case-quote">"A game-changer for weaving units in Coimbatore — it has brought a new level of precision to our operations."</div>
      <div class="case-author">Elavarasu Arumugham · WoTA</div>
    </div>
  </div>
</section>

<!-- MANIFESTO -->
<section class="manifesto">
  <div class="manifesto-glow"></div>
  <div class="manifesto-content">
    <div class="section-tag reveal" data-n="05 —" style="justify-content:center;">The Mission</div>
    <h2 class="reveal">We build for<br/><em>people</em>, not portfolios.</h2>
    <p class="reveal reveal-delay-1">We exist to prove that the best technology can come from anywhere. From Coimbatore to the world — one bold, scrappy, meticulously crafted product at a time.</p>
    <a href="#contact" class="btn-primary reveal reveal-delay-2">Start a Conversation</a>
  </div>
</section>

<!-- FOOTER / CONTACT -->
<footer id="contact">
  <div class="footer-grid">
    <div class="footer-brand">
      <a href="#" class="logo">
        <span class="logo-dot"></span>
        Bipolar Factory
      </a>
      <p>A collective of dreamers, thinkers, and doers building technology that matters — from Coimbatore, for the world.</p>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <ul>
        <li><a href="#about">About Us</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Privacy Policy</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Products</h4>
      <ul>
        <li><a href="#products">OLY Store Sync</a></li>
        <li><a href="#products">OLY Control Center</a></li>
        <li><a href="#products">Metawood</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Connect</h4>
      <address class="footer-address">
        2/118, First Floor,<br/>
        Nehru Nagar, Koundampalayam Road,<br/>
        Edayarpalayam, Coimbatore,<br/>
        Tamil Nadu 641025
      </address>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2024 Bipolar Factory Private Limited. All Rights Reserved.</p>
    <p>Built with <span>◆</span> in Coimbatore</p>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
    ring.style.left = mx + 'px';
    ring.style.top = my + 'px';
  });
  document.querySelectorAll('a, button, .product-card, .case-card, .value-item').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '16px'; cursor.style.height = '16px';
      ring.style.width = '52px'; ring.style.height = '52px';
      ring.style.borderColor = 'var(--volt)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '10px'; cursor.style.height = '10px';
      ring.style.width = '36px'; ring.style.height = '36px';
      ring.style.borderColor = 'var(--electric)';
    });
  });

  // Sticky nav
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
