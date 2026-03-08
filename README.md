<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Karim Ayman Elmliegy</title>
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #090d13;
    --surface: #0e1520;
    --surface2: #131d2e;
    --border: #1a2a42;
    --accent: #00c2ff;
    --accent2: #0a66c2;
    --accent3: #00ffc8;
    --text: #cdd9e8;
    --text-dim: #5c7a9a;
    --glow: 0 0 20px rgba(0,194,255,0.15);
    --glow-strong: 0 0 40px rgba(0,194,255,0.3);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Fira Code', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,194,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,194,255,0.03) 1px, transparent 1px);
    background-size: 50px 50px;
    pointer-events: none;
    z-index: 0;
  }

  /* Radial glow top center */
  body::after {
    content: '';
    position: fixed;
    top: -200px;
    left: 50%;
    transform: translateX(-50%);
    width: 800px;
    height: 600px;
    background: radial-gradient(ellipse, rgba(0,194,255,0.07) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .page {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding-bottom: 48px;
    animation: fadeDown 0.8s ease both;
  }

  .hero-gif {
    width: 160px;
    border-radius: 50%;
    border: 2px solid var(--accent);
    box-shadow: var(--glow-strong);
    margin-bottom: 28px;
    animation: pulse-border 3s ease-in-out infinite;
  }

  @keyframes pulse-border {
    0%, 100% { box-shadow: 0 0 20px rgba(0,194,255,0.3); }
    50%       { box-shadow: 0 0 50px rgba(0,194,255,0.6); }
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 800;
    letter-spacing: -0.02em;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 10px;
  }

  .hero-sub {
    font-size: 0.85rem;
    color: var(--text-dim);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 28px;
  }

  .hero-sub span {
    color: var(--accent);
  }

  /* Typing cursor */
  .cursor {
    display: inline-block;
    width: 2px;
    height: 1em;
    background: var(--accent);
    margin-left: 2px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* Social badges */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin-bottom: 8px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 8px 16px;
    border-radius: 6px;
    font-size: 0.78rem;
    font-weight: 600;
    text-decoration: none;
    border: 1px solid transparent;
    transition: all 0.25s ease;
    letter-spacing: 0.04em;
  }

  .badge:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.4);
  }

  .badge-linkedin  { background: #0a66c2; color: #fff; }
  .badge-github    { background: #161b22; color: #fff; border-color: #30363d; }
  .badge-email     { background: #c0392b; color: #fff; }
  .badge-telegram  { background: #1e3145; color: #fff; border-color: #2980b9; }

  /* ── DIVIDER ── */
  hr.fancy {
    border: none;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), var(--accent2), var(--border), transparent);
    margin: 40px 0;
    opacity: 0.6;
  }

  /* ── SECTION TITLE ── */
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── ABOUT LIST ── */
  .about-list {
    list-style: none;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  @media (max-width: 600px) {
    .about-list { grid-template-columns: 1fr; }
  }

  .about-list li {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 16px;
    font-size: 0.82rem;
    color: var(--text);
    display: flex;
    align-items: flex-start;
    gap: 10px;
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  .about-list li:hover {
    border-color: var(--accent2);
    box-shadow: var(--glow);
  }

  .about-list li .icon { font-size: 1rem; flex-shrink: 0; margin-top: 1px; }
  .about-list li strong { color: var(--accent); }

  /* ── TOOLS ── */
  .tools-group { margin-bottom: 24px; }

  .tools-label {
    font-size: 0.72rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 10px;
  }

  .pill-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .pill {
    padding: 5px 12px;
    border-radius: 4px;
    font-size: 0.74rem;
    font-weight: 500;
    border: 1px solid var(--border);
    background: var(--surface2);
    color: var(--text);
    transition: all 0.2s ease;
    cursor: default;
  }

  .pill:hover {
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: 0 0 12px rgba(0,194,255,0.15);
    transform: translateY(-2px);
  }

  /* ── CODE BLOCK ── */
  .code-block {
    background: #07101a;
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    margin-top: 24px;
    box-shadow: 0 4px 30px rgba(0,0,0,0.4);
  }

  .code-bar {
    background: #0b1521;
    border-bottom: 1px solid var(--border);
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }

  .code-lang {
    margin-left: auto;
    font-size: 0.7rem;
    color: var(--text-dim);
    letter-spacing: 0.1em;
  }

  .code-body {
    padding: 20px 24px;
    font-size: 0.8rem;
    line-height: 1.8;
    overflow-x: auto;
  }

  .c-dim    { color: #4a6a8a; }
  .c-kw     { color: #cc99ff; }
  .c-class  { color: #79d4f1; }
  .c-key    { color: #5ecbef; }
  .c-str    { color: #a8d8a8; }
  .c-punc   { color: #6a8a9a; }

  /* ── PROJECTS ── */
  .projects { display: grid; gap: 16px; }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 22px 24px;
    transition: border-color 0.25s, box-shadow 0.25s, transform 0.2s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent2), var(--accent3));
    opacity: 0;
    transition: opacity 0.3s;
  }

  .project-card:hover {
    border-color: var(--accent2);
    box-shadow: var(--glow);
    transform: translateY(-4px);
  }

  .project-card:hover::before { opacity: 1; }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 6px;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 12px;
  }

  .tag {
    font-size: 0.68rem;
    padding: 3px 9px;
    background: rgba(0,194,255,0.08);
    border: 1px solid rgba(0,194,255,0.2);
    border-radius: 4px;
    color: var(--accent);
    letter-spacing: 0.05em;
  }

  .project-desc {
    font-size: 0.8rem;
    color: var(--text-dim);
    line-height: 1.7;
    margin-bottom: 14px;
  }

  .feature-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
  }

  @media (max-width: 500px) {
    .feature-grid { grid-template-columns: 1fr; }
  }

  .feature {
    font-size: 0.75rem;
    color: var(--text);
    display: flex;
    gap: 8px;
    align-items: flex-start;
    line-height: 1.5;
  }

  .project-list { list-style: none; }
  .project-list li {
    font-size: 0.8rem;
    color: var(--text);
    padding: 5px 0;
    padding-left: 16px;
    position: relative;
  }
  .project-list li::before {
    content: '▸';
    position: absolute;
    left: 0;
    color: var(--accent);
  }

  /* ── COMPETENCIES ── */
  .competencies { display: grid; gap: 14px; }

  .comp-row { }

  .comp-header {
    display: flex;
    justify-content: space-between;
    font-size: 0.78rem;
    margin-bottom: 7px;
    color: var(--text);
  }

  .comp-pct { color: var(--accent); font-weight: 600; }

  .bar-track {
    height: 4px;
    background: var(--surface2);
    border-radius: 99px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    border-radius: 99px;
    background: linear-gradient(90deg, var(--accent2), var(--accent3));
    transform: scaleX(0);
    transform-origin: left;
    animation: growBar 1.2s cubic-bezier(.22,.61,.36,1) both;
  }

  @keyframes growBar { to { transform: scaleX(1); } }

  /* ── CERTS ── */
  .certs { display: grid; gap: 10px; }

  .cert-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 13px 18px;
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 0.82rem;
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  .cert-item:hover {
    border-color: var(--accent);
    box-shadow: var(--glow);
  }

  .cert-icon { font-size: 1.2rem; }
  .cert-name { color: #fff; font-weight: 600; }
  .cert-org  { color: var(--text-dim); font-size: 0.72rem; margin-top: 2px; }

  /* ── LEARNING ICONS ── */
  .learn-row {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    align-items: center;
    justify-content: center;
  }

  .learn-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    font-size: 0.68rem;
    color: var(--text-dim);
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  .learn-item img {
    width: 44px;
    height: 44px;
    filter: grayscale(40%);
    transition: filter 0.2s, transform 0.2s;
  }

  .learn-item:hover img {
    filter: grayscale(0%);
    transform: translateY(-4px);
  }

  /* ── CODE CYCLE ── */
  .cycle {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
    flex-wrap: wrap;
    padding: 24px 0 8px;
  }

  .cycle-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    font-size: 0.72rem;
    color: var(--text-dim);
    letter-spacing: 0.06em;
  }

  .cycle-item img { width: 64px; }

  .cycle-arrow {
    font-size: 1.5rem;
    color: var(--border);
    padding-bottom: 20px;
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding-top: 20px;
    font-size: 0.75rem;
    color: var(--text-dim);
    letter-spacing: 0.06em;
  }

  .footer a { color: var(--accent); text-decoration: none; }
  .footer a:hover { text-decoration: underline; }

  /* ── ANIMATIONS ── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(24px);
    animation: fadeUp 0.7s ease both;
  }

  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }

  .d1 { animation-delay: 0.1s; }
  .d2 { animation-delay: 0.2s; }
  .d3 { animation-delay: 0.3s; }
  .d4 { animation-delay: 0.4s; }
  .d5 { animation-delay: 0.5s; }
  .d6 { animation-delay: 0.6s; }
  .d7 { animation-delay: 0.7s; }
</style>
</head>
<body>
<div class="page">

  <!-- HERO -->
  <div class="hero">
    <img class="hero-gif"
      src="https://github.com/SP-XD/SP-XD/blob/main/images/dev-working_rounded.gif?raw=true"
      alt="Working"
    />
    <h1>Karim Ayman Elmliegy<span class="cursor"></span></h1>
    <p class="hero-sub">Full Stack .NET Developer &nbsp;·&nbsp; Embedded Systems Engineer &nbsp;·&nbsp; <span>Cairo, Egypt 🇪🇬</span></p>
    <div class="badges">
      <a href="https://www.linkedin.com/in/karim-ayman-a3050516a/" class="badge badge-linkedin">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="white"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a href="https://github.com/KarimElmliegy" class="badge badge-github">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="white"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>
        GitHub
      </a>
      <a href="mailto:karim.ayman.kemo@gmail.com" class="badge badge-email">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Email
      </a>
      <a href="https://t.me/spxd007" class="badge badge-telegram">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="white"><path d="M22 2L11 13M22 2L15 22l-4-9-9-4 20-7z"/></svg>
        Telegram
      </a>
    </div>
  </div>

  <hr class="fancy"/>

  <!-- ABOUT -->
  <section class="reveal d1">
    <div class="section-title">👋 About Me</div>
    <ul class="about-list">
      <li><span class="icon">🎓</span><div><strong>Education:</strong> Electronics &amp; Communication Eng. — Mansoura University (2024)</div></li>
      <li><span class="icon">💼</span><div><strong>Currently:</strong> Backend Developer at Route &amp; ITI Student</div></li>
      <li><span class="icon">🚀</span><div><strong>Graduation Project:</strong> FOTA (Firmware Over-The-Air) — Grade: <strong>A+</strong></div></li>
      <li><span class="icon">🌱</span><div><strong>Learning:</strong> Frappe, Microservices, Docker, Azure, React, Angular</div></li>
      <li><span class="icon">🐧</span><div>I like exploring <strong>GNU/Linux</strong></div></li>
      <li><span class="icon">⚡</span><div><strong>Fun fact:</strong> Banging your head against a wall for one hour burns 150 calories</div></li>
    </ul>
  </section>

  <hr class="fancy"/>

  <!-- TOOLS -->
  <section class="reveal d2">
    <div class="section-title">🚀 Tools I Use</div>

    <div class="tools-group">
      <div class="tools-label">Backend &amp; Full Stack</div>
      <div class="pill-row">
        <span class="pill">.NET</span><span class="pill">C#</span><span class="pill">EF Core</span>
        <span class="pill">SQL Server</span><span class="pill">PostgreSQL</span>
        <span class="pill">Firebase</span><span class="pill">SQLite</span>
      </div>
    </div>

    <div class="tools-group">
      <div class="tools-label">Frontend</div>
      <div class="pill-row">
        <span class="pill">HTML5</span><span class="pill">CSS3</span><span class="pill">JavaScript</span>
        <span class="pill">jQuery</span><span class="pill">Bootstrap</span><span class="pill">Tailwind CSS</span>
      </div>
    </div>

    <div class="tools-group">
      <div class="tools-label">Embedded Systems</div>
      <div class="pill-row">
        <span class="pill">C</span><span class="pill">C++</span><span class="pill">Embedded C</span>
        <span class="pill">STM32</span><span class="pill">ESP32</span><span class="pill">Arduino</span>
        <span class="pill">ARM Cortex</span><span class="pill">AVR</span>
      </div>
    </div>

    <div class="tools-group">
      <div class="tools-label">Dev Tools &amp; Platforms</div>
      <div class="pill-row">
        <span class="pill">Git</span><span class="pill">GitHub</span><span class="pill">VS Code</span>
        <span class="pill">Visual Studio</span><span class="pill">Keil uVision</span>
        <span class="pill">Proteus</span><span class="pill">Linux</span>
        <span class="pill">Figma</span><span class="pill">Bash</span>
      </div>
    </div>

    <div class="code-block">
      <div class="code-bar">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="code-lang">skills.js</span>
      </div>
      <div class="code-body">
<span class="c-dim">// All tools organized</span><br><br>
<span class="c-kw">class</span> <span class="c-class">Skills</span> <span class="c-kw">extends</span> <span class="c-class">KarimAyman</span> <span class="c-punc">{</span><br><br>
&nbsp;&nbsp;<span class="c-key">stack</span> <span class="c-punc">= {</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Backend</span>  <span class="c-punc">: [</span> <span class="c-str">"C#"</span><span class="c-punc">,</span> <span class="c-str">".NET"</span><span class="c-punc">,</span> <span class="c-str">"EF Core"</span><span class="c-punc">,</span> <span class="c-str">"SQL Server"</span><span class="c-punc">,</span> <span class="c-str">"PostgreSQL"</span><span class="c-punc">,</span> <span class="c-str">"Firebase"</span><span class="c-punc">,</span> <span class="c-str">"SQLite"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Frontend</span> <span class="c-punc">: [</span> <span class="c-str">"HTML"</span><span class="c-punc">,</span> <span class="c-str">"CSS"</span><span class="c-punc">,</span> <span class="c-str">"JavaScript"</span><span class="c-punc">,</span> <span class="c-str">"jQuery"</span><span class="c-punc">,</span> <span class="c-str">"Bootstrap"</span><span class="c-punc">,</span> <span class="c-str">"Tailwind"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Embedded</span> <span class="c-punc">: [</span> <span class="c-str">"C"</span><span class="c-punc">,</span> <span class="c-str">"C++"</span><span class="c-punc">,</span> <span class="c-str">"Embedded C"</span><span class="c-punc">,</span> <span class="c-str">"STM32"</span><span class="c-punc">,</span> <span class="c-str">"ESP32"</span><span class="c-punc">,</span> <span class="c-str">"Arduino"</span><span class="c-punc">,</span> <span class="c-str">"ARM"</span><span class="c-punc">,</span> <span class="c-str">"AVR"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Protocols</span><span class="c-punc">: [</span> <span class="c-str">"UART"</span><span class="c-punc">,</span> <span class="c-str">"SPI"</span><span class="c-punc">,</span> <span class="c-str">"I2C"</span><span class="c-punc">,</span> <span class="c-str">"Wi-Fi"</span><span class="c-punc">,</span> <span class="c-str">"RTOS"</span><span class="c-punc">,</span> <span class="c-str">"OTA/FOTA"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">DevTools</span> <span class="c-punc">: [</span> <span class="c-str">"Git"</span><span class="c-punc">,</span> <span class="c-str">"VS Code"</span><span class="c-punc">,</span> <span class="c-str">"Visual Studio"</span><span class="c-punc">,</span> <span class="c-str">"Keil"</span><span class="c-punc">,</span> <span class="c-str">"Proteus"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Platforms</span><span class="c-punc">: [</span> <span class="c-str">"GNU/Linux"</span><span class="c-punc">,</span> <span class="c-str">"Windows"</span><span class="c-punc">,</span> <span class="c-str">"Red Hat"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">Design</span>   <span class="c-punc">: [</span> <span class="c-str">"Figma"</span><span class="c-punc">,</span> <span class="c-str">"Photoshop"</span><span class="c-punc">,</span> <span class="c-str">"Gimp"</span> <span class="c-punc">],</span><br>
&nbsp;&nbsp;<span class="c-punc">};</span><br><br>
<span class="c-punc">}</span>
      </div>
    </div>
  </section>

  <hr class="fancy"/>

  <!-- PROJECTS -->
  <section class="reveal d3">
    <div class="section-title">🚀 Featured Projects</div>
    <div class="projects">

      <div class="project-card">
        <div class="project-title">🤖 TalentFlow AI — ITI Graduation Project</div>
        <div class="project-stack">
          <span class="tag">C#</span><span class="tag">.NET</span><span class="tag">SQL</span>
          <span class="tag">EF Core</span><span class="tag">AI/ML</span>
        </div>
        <p class="project-desc">An AI-powered Workforce Intelligence Platform that revolutionizes employee-project matching in large enterprises.</p>
        <div class="feature-grid">
          <div class="feature"><span>🎯</span><span><strong style="color:#cdd9e8">Smart Resource Matching</strong> — ranks candidates by skills, experience &amp; availability</span></div>
          <div class="feature"><span>🔄</span><span><strong style="color:#cdd9e8">Dynamic Reallocation</strong> — detects idle employees and suggests transitions</span></div>
          <div class="feature"><span>📊</span><span><strong style="color:#cdd9e8">Skill Gap Analysis</strong> — personalized training recommendations</span></div>
          <div class="feature"><span>🛤️</span><span><strong style="color:#cdd9e8">Career Path Intelligence</strong> — AI-driven growth suggestions</span></div>
        </div>
      </div>

      <div class="project-card">
        <div class="project-title">🏫 ITI Examination System</div>
        <div class="project-stack">
          <span class="tag">C#</span><span class="tag">.NET</span><span class="tag">SQL</span><span class="tag">EF Core</span>
        </div>
        <p class="project-desc">A centralized examination management platform serving ITI branches across Egypt.</p>
        <ul class="project-list">
          <li>Role-Based Access Control — Students, Instructors, Branch Managers, Admins</li>
          <li>Multi-branch architecture with secure data handling</li>
          <li>Comprehensive exam management workflow</li>
        </ul>
      </div>

      <div class="project-card">
        <div class="project-title">📡 FOTA (Firmware Over-The-Air) &nbsp;<span style="background:#1a2a1a;color:#28c840;padding:3px 8px;border-radius:4px;font-size:0.72rem;">⭐ Grade: A+</span></div>
        <div class="project-stack">
          <span class="tag">C</span><span class="tag">Embedded C</span><span class="tag">ESP32</span><span class="tag">STM32F103</span>
        </div>
        <p class="project-desc">Remote firmware update system for microcontrollers with a custom secure bootloader.</p>
        <ul class="project-list">
          <li>Wireless firmware updates via ESP32</li>
          <li>Custom secure bootloader implementation</li>
          <li>STM32 integration with full OTA capabilities</li>
        </ul>
      </div>

      <div class="project-card">
        <div class="project-title">🔧 Embedded Systems Portfolio</div>
        <div class="project-stack"><span class="tag">C</span><span class="tag">ARM</span><span class="tag">AVR</span><span class="tag">STM32</span></div>
        <ul class="project-list">
          <li><strong style="color:#cdd9e8">Traffic Light Control System</strong> — Real-time traffic management simulation</li>
          <li><strong style="color:#cdd9e8">ARM Calculator</strong> — Calculator application on STM32 (Cortex-M3)</li>
        </ul>
      </div>

    </div>
  </section>

  <hr class="fancy"/>

  <!-- COMPETENCIES -->
  <section class="reveal d4">
    <div class="section-title">💡 Core Competencies</div>
    <div class="competencies">
      <div class="comp-row">
        <div class="comp-header"><span>Backend Development</span><span class="comp-pct">95%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:95%;animation-delay:0.1s"></div></div>
      </div>
      <div class="comp-row">
        <div class="comp-header"><span>Embedded Systems</span><span class="comp-pct">90%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:90%;animation-delay:0.2s"></div></div>
      </div>
      <div class="comp-row">
        <div class="comp-header"><span>Frontend Development</span><span class="comp-pct">80%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:80%;animation-delay:0.3s"></div></div>
      </div>
      <div class="comp-row">
        <div class="comp-header"><span>Database Design</span><span class="comp-pct">80%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:80%;animation-delay:0.4s"></div></div>
      </div>
      <div class="comp-row">
        <div class="comp-header"><span>AI Integration</span><span class="comp-pct">75%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:75%;animation-delay:0.5s"></div></div>
      </div>
      <div class="comp-row">
        <div class="comp-header"><span>System Architecture</span><span class="comp-pct">75%</span></div>
        <div class="bar-track"><div class="bar-fill" style="width:75%;animation-delay:0.6s"></div></div>
      </div>
    </div>
  </section>

  <hr class="fancy"/>

  <!-- CERTS -->
  <section class="reveal d5">
    <div class="section-title">🏆 Certifications</div>
    <div class="certs">
      <div class="cert-item">
        <span class="cert-icon">📜</span>
        <div><div class="cert-name">Embedded Systems Developer Nanodegree</div><div class="cert-org">Udacity</div></div>
      </div>
      <div class="cert-item">
        <span class="cert-icon">💻</span>
        <div><div class="cert-name">Problem Solving Certificate</div><div class="cert-org">HackerRank</div></div>
      </div>
      <div class="cert-item">
        <span class="cert-icon">🎓</span>
        <div><div class="cert-name">9-month Professional Development Program <span style="color:#febc2e;font-size:0.7rem">(In Progress)</span></div><div class="cert-org">ITI</div></div>
      </div>
    </div>
  </section>

  <hr class="fancy"/>

  <!-- LEARNING -->
  <section class="reveal d6">
    <div class="section-title">📚 Currently Learning</div>
    <div class="learn-row">
      <div class="learn-item">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original.svg" alt="Docker"/>
        Docker
      </div>
      <div class="learn-item">
        <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="Kubernetes"/>
        Kubernetes
      </div>
      <div class="learn-item">
        <img src="https://www.vectorlogo.zone/logos/microsoft_azure/microsoft_azure-icon.svg" alt="Azure"/>
        Azure
      </div>
      <div class="learn-item">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg" alt="React"/>
        React
      </div>
      <div class="learn-item">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/angularjs/angularjs-original.svg" alt="Angular"/>
        Angular
      </div>
    </div>
  </section>

  <hr class="fancy"/>

  <!-- CODE CYCLE -->
  <section class="reveal d7" style="text-align:center;">
    <div class="section-title" style="justify-content:center;">The Developer Code Cycle</div>
    <div class="cycle">
      <div class="cycle-item">
        <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Face%20with%20Spiral%20Eyes.png" alt="Broken"/>
        Broken
      </div>
      <div class="cycle-arrow">→</div>
      <div class="cycle-item">
        <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Relieved%20Face.png" alt="Fixed"/>
        Fixed
      </div>
      <div class="cycle-arrow">→</div>
      <div class="cycle-item">
        <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Astonished%20Face.png" alt="How"/>
        How?!
      </div>
    </div>
  </section>

  <hr class="fancy"/>

  <!-- FOOTER -->
  <div class="footer reveal">
    <p>⭐️ From <a href="https://github.com/KarimElmliegy">KarimElmliegy</a> — Let's build something amazing together!</p>
  </div>

</div>
</body>
</html>
