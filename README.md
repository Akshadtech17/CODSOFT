<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CODSOFT Data Science Internship</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=DM+Sans:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050810;
    --surface: #0c1120;
    --surface2: #111827;
    --border: rgba(99,179,237,0.15);
    --accent: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --accent4: #f472b6;
    --accent5: #fb923c;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: rgba(56,189,248,0.25);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
    line-height: 1.7;
  }

  /* ── CANVAS STARS ── */
  #starfield {
    position: fixed; inset: 0; z-index: 0; pointer-events: none;
  }

  /* ── SCAN LINE OVERLAY ── */
  body::after {
    content: '';
    position: fixed; inset: 0; z-index: 1; pointer-events: none;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
  }

  .wrapper { position: relative; z-index: 2; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    text-align: center;
    padding: 4rem 2rem;
    position: relative;
    overflow: hidden;
  }

  .hero-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    animation: drift 8s ease-in-out infinite alternate;
    pointer-events: none;
  }
  .orb1 { width: 500px; height: 500px; background: rgba(56,189,248,0.12); top: -100px; left: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: rgba(129,140,248,0.10); bottom: -80px; right: -80px; animation-delay: -3s; }
  .orb3 { width: 300px; height: 300px; background: rgba(52,211,153,0.08); top: 30%; right: 10%; animation-delay: -5s; }

  @keyframes drift {
    from { transform: translate(0,0) scale(1); }
    to   { transform: translate(40px, 30px) scale(1.1); }
  }

  .badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: rgba(56,189,248,0.08);
    border: 1px solid rgba(56,189,248,0.3);
    border-radius: 999px;
    padding: 0.4rem 1.2rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 2rem;
    animation: fadeDown 0.8s ease both;
  }
  .badge-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent3); animation: pulse 2s ease infinite; }

  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.8); }
  }

  .hero-title {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(3rem, 8vw, 7rem);
    line-height: 1;
    letter-spacing: -0.03em;
    animation: fadeDown 0.8s 0.1s ease both;
  }

  .hero-title .line1 {
    display: block;
    background: linear-gradient(135deg, #fff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .hero-title .line2 {
    display: block;
    color: var(--muted);
    font-weight: 400;
    font-size: 0.45em;
    letter-spacing: 0.02em;
    margin-top: 0.5rem;
    -webkit-text-fill-color: var(--muted);
  }

  .hero-sub {
    margin-top: 1.5rem;
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 560px;
    animation: fadeDown 0.8s 0.2s ease both;
  }

  .stats-row {
    display: flex; gap: 2.5rem; flex-wrap: wrap;
    justify-content: center;
    margin-top: 3rem;
    animation: fadeDown 0.8s 0.3s ease both;
  }

  .stat {
    text-align: center;
  }
  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 2.2rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .stat-label { font-size: 0.78rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-top: 0.2rem; }

  .scroll-hint {
    position: absolute; bottom: 2rem;
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
    color: var(--muted); font-size: 0.75rem; letter-spacing: 0.1em;
    text-transform: uppercase; font-family: 'Space Mono', monospace;
    animation: fadeIn 1s 1s ease both;
  }
  .scroll-line { width: 1px; height: 40px; background: linear-gradient(to bottom, var(--accent), transparent); animation: scrollDown 2s ease-in-out infinite; }
  @keyframes scrollDown { 0%,100%{ transform: scaleY(1); opacity:1; } 50%{ transform: scaleY(0.3); opacity:0.3; } }

  /* ── SECTION ── */
  .section { padding: 5rem 2rem; max-width: 1200px; margin: 0 auto; }
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
    text-transform: uppercase;
    letter-spacing: 0.2em;
    margin-bottom: 0.8rem;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: clamp(1.8rem, 4vw, 3rem);
    line-height: 1.15;
    margin-bottom: 1rem;
  }
  .section-desc {
    color: var(--muted);
    max-width: 600px;
    margin-bottom: 3rem;
  }

  /* ── TECH STACK ── */
  .tech-marquee-wrap { overflow: hidden; padding: 2rem 0; }
  .tech-track {
    display: flex; gap: 1.5rem;
    animation: marquee 20s linear infinite;
    width: max-content;
  }
  .tech-track:hover { animation-play-state: paused; }
  @keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }

  .tech-pill {
    display: inline-flex; align-items: center; gap: 0.6rem;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 999px;
    padding: 0.5rem 1.2rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.78rem;
    color: var(--text);
    white-space: nowrap;
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  .tech-pill:hover { border-color: var(--accent); box-shadow: 0 0 16px var(--glow); }
  .tech-pill .icon { font-size: 1rem; }

  /* ── TASK CARDS ── */
  .tasks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
  }

  .task-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2rem;
    position: relative;
    overflow: hidden;
    transition: transform 0.4s cubic-bezier(.175,.885,.32,1.275), box-shadow 0.4s;
    cursor: default;
  }
  .task-card::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(circle at 30% 0%, var(--card-glow, rgba(56,189,248,0.07)), transparent 60%);
    pointer-events: none;
  }
  .task-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.4), 0 0 0 1px var(--card-accent, var(--accent));
  }

  .task-card.t1 { --card-glow: rgba(56,189,248,0.1); --card-accent: rgba(56,189,248,0.4); }
  .task-card.t2 { --card-glow: rgba(244,114,182,0.1); --card-accent: rgba(244,114,182,0.4); }
  .task-card.t3 { --card-glow: rgba(52,211,153,0.1); --card-accent: rgba(52,211,153,0.4); }
  .task-card.t4 { --card-glow: rgba(251,146,60,0.1); --card-accent: rgba(251,146,60,0.4); }
  .task-card.t5 { --card-glow: rgba(129,140,248,0.1); --card-accent: rgba(129,140,248,0.4); }

  .task-number {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--card-num, var(--accent));
    margin-bottom: 1rem;
    display: flex; align-items: center; gap: 0.5rem;
  }
  .task-card.t1 { --card-num: var(--accent); }
  .task-card.t2 { --card-num: var(--accent4); }
  .task-card.t3 { --card-num: var(--accent3); }
  .task-card.t4 { --card-num: var(--accent5); }
  .task-card.t5 { --card-num: var(--accent2); }

  .task-icon {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    display: block;
    filter: drop-shadow(0 0 12px var(--card-glow));
  }

  .task-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1.2rem;
    margin-bottom: 0.7rem;
    line-height: 1.3;
  }

  .task-desc {
    color: var(--muted);
    font-size: 0.88rem;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  .task-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
  .tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.68rem;
    padding: 0.25rem 0.7rem;
    border-radius: 999px;
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .task-bar {
    position: absolute; top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--card-accent, var(--accent)), transparent);
  }

  /* ── PIPELINE SECTION ── */
  .pipeline {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 24px;
    padding: 3rem;
    position: relative;
    overflow: hidden;
  }
  .pipeline::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; bottom: 0;
    background: radial-gradient(ellipse at 20% 50%, rgba(56,189,248,0.06), transparent 50%),
                radial-gradient(ellipse at 80% 50%, rgba(129,140,248,0.06), transparent 50%);
    pointer-events: none;
  }

  .pipeline-steps {
    display: flex; align-items: flex-start; flex-wrap: wrap; gap: 0;
    position: relative; z-index: 1;
  }

  .pipe-step {
    flex: 1; min-width: 140px;
    text-align: center;
    padding: 1rem;
    position: relative;
  }
  .pipe-step::after {
    content: '→';
    position: absolute; right: -0.6rem; top: 50%;
    transform: translateY(-60%);
    color: var(--muted);
    font-size: 1.2rem;
  }
  .pipe-step:last-child::after { display: none; }

  .pipe-icon {
    width: 52px; height: 52px;
    border-radius: 14px;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.1);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.4rem;
    margin: 0 auto 0.8rem;
    transition: background 0.3s, border-color 0.3s, transform 0.3s;
  }
  .pipe-step:hover .pipe-icon {
    background: rgba(56,189,248,0.1);
    border-color: rgba(56,189,248,0.4);
    transform: scale(1.1);
  }
  .pipe-step-title {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 0.82rem;
    margin-bottom: 0.3rem;
  }
  .pipe-step-sub { font-size: 0.72rem; color: var(--muted); }

  /* ── SKILLS TABLE ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }
  .skill-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.2rem;
    transition: border-color 0.3s, transform 0.3s;
  }
  .skill-item:hover { border-color: rgba(56,189,248,0.4); transform: scale(1.02); }
  .skill-item-head {
    display: flex; align-items: center; gap: 0.6rem;
    margin-bottom: 0.8rem;
  }
  .skill-dot { width: 8px; height: 8px; border-radius: 50%; }
  .skill-name {
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 0.9rem;
  }
  .skill-bar-bg {
    height: 4px; border-radius: 999px;
    background: rgba(255,255,255,0.06);
    overflow: hidden;
  }
  .skill-bar-fill {
    height: 100%; border-radius: 999px;
    background: linear-gradient(90deg, var(--bar-from), var(--bar-to));
    animation: fillBar 1.5s ease both;
    animation-delay: var(--delay, 0s);
    transform-origin: left;
  }
  @keyframes fillBar {
    from { transform: scaleX(0); }
    to { transform: scaleX(1); }
  }
  .skill-pct { font-family: 'Space Mono', monospace; font-size: 0.7rem; color: var(--muted); margin-top: 0.4rem; text-align: right; }

  /* ── SETUP BLOCK ── */
  .setup-block {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    margin-bottom: 1.5rem;
  }
  .setup-header {
    display: flex; align-items: center; justify-content: space-between;
    padding: 0.8rem 1.2rem;
    background: rgba(255,255,255,0.03);
    border-bottom: 1px solid var(--border);
  }
  .setup-title { font-family: 'Space Mono', monospace; font-size: 0.75rem; color: var(--accent); }
  .copy-btn {
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    color: var(--muted); background: none; border: 1px solid var(--border);
    padding: 0.25rem 0.7rem; border-radius: 6px; cursor: pointer;
    transition: color 0.2s, border-color 0.2s;
  }
  .copy-btn:hover { color: var(--accent); border-color: rgba(56,189,248,0.4); }
  .setup-code {
    padding: 1.2rem 1.5rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    line-height: 1.7;
    color: #94a3b8;
    overflow-x: auto;
  }
  .setup-code .cmd { color: var(--accent3); }
  .setup-code .comment { color: #475569; font-style: italic; }
  .setup-code .str { color: var(--accent4); }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 3rem 2rem;
    text-align: center;
    position: relative;
  }
  .footer-glow {
    position: absolute; bottom: 0; left: 50%; transform: translateX(-50%);
    width: 300px; height: 200px;
    background: radial-gradient(circle, rgba(56,189,248,0.08), transparent 70%);
    pointer-events: none;
  }
  .footer-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.8rem;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 0.5rem;
  }
  .footer-text { color: var(--muted); font-size: 0.85rem; }
  .footer-links { display: flex; gap: 2rem; justify-content: center; margin-top: 1.5rem; flex-wrap: wrap; }
  .footer-link {
    font-family: 'Space Mono', monospace; font-size: 0.72rem;
    color: var(--muted); text-decoration: none; text-transform: uppercase; letter-spacing: 0.1em;
    transition: color 0.2s;
  }
  .footer-link:hover { color: var(--accent); }

  /* ── DIVIDER ── */
  .divider {
    border: none;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 0 2rem;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── FLOATING PARTICLES ── */
  .particle {
    position: fixed;
    width: 2px; height: 2px;
    border-radius: 50%;
    background: var(--accent);
    pointer-events: none;
    opacity: 0;
    animation: floatUp var(--dur, 6s) var(--delay2, 0s) ease-in infinite;
    z-index: 1;
  }
  @keyframes floatUp {
    0% { opacity: 0; transform: translateY(0) scale(0); }
    10% { opacity: 0.6; transform: translateY(-10px) scale(1); }
    90% { opacity: 0.3; }
    100% { opacity: 0; transform: translateY(-120px) scale(0.5); }
  }

  /* ── HIGHLIGHT COLORS ── */
  .hl-blue { color: var(--accent); }
  .hl-purple { color: var(--accent2); }
  .hl-green { color: var(--accent3); }
  .hl-pink { color: var(--accent4); }
  .hl-orange { color: var(--accent5); }
</style>
</head>
<body>

<canvas id="starfield"></canvas>

<div class="wrapper">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-orb orb1"></div>
    <div class="hero-orb orb2"></div>
    <div class="hero-orb orb3"></div>

    <div class="badge">
      <span class="badge-dot"></span>
      Data Science Internship Program
    </div>

    <h1 class="hero-title">
      <span class="line1">CODSOFT</span>
      <span class="line2">Turning Raw Data into Real Intelligence</span>
    </h1>

    <p class="hero-sub">
      Five production-grade machine learning projects spanning classification, regression, fraud detection, and time-series forecasting — built from scratch in Python.
    </p>

    <div class="stats-row">
      <div class="stat">
        <div class="stat-number" data-count="5">5</div>
        <div class="stat-label">ML Projects</div>
      </div>
      <div class="stat">
        <div class="stat-number" data-count="10">10+</div>
        <div class="stat-label">Algorithms</div>
      </div>
      <div class="stat">
        <div class="stat-number" data-count="6">6</div>
        <div class="stat-label">Libraries</div>
      </div>
      <div class="stat">
        <div class="stat-number" data-count="100">100%</div>
        <div class="stat-label">Python</div>
      </div>
    </div>

    <div class="scroll-hint">
      <span>Scroll to explore</span>
      <div class="scroll-line"></div>
    </div>
  </section>

  <hr class="divider">

  <!-- TECH STACK MARQUEE -->
  <div style="padding: 3rem 0 1rem;">
    <div style="text-align:center; margin-bottom: 1.5rem;">
      <span class="section-label" style="display:inline-block;">Tech Stack</span>
    </div>
    <div class="tech-marquee-wrap">
      <div class="tech-track" id="techTrack"></div>
    </div>
  </div>

  <hr class="divider">

  <!-- TASKS -->
  <section class="section">
    <div class="section-label reveal">Projects</div>
    <h2 class="section-title reveal">Five Mission-Critical <br><span class="hl-blue">ML Challenges</span></h2>
    <p class="section-desc reveal">Each project is a self-contained end-to-end pipeline — from raw messy data to a deployed, evaluated model.</p>

    <div class="tasks-grid">

      <div class="task-card t1 reveal">
        <div class="task-bar"></div>
        <div class="task-number">Task 01</div>
        <span class="task-icon">🚢</span>
        <div class="task-title">Titanic Survival Prediction</div>
        <div class="task-desc">Binary classification on the legendary Titanic dataset. Engineer features from passenger data — age, class, gender, cabin — and predict survival outcomes using ensemble learning.</div>
        <div class="task-tags">
          <span class="tag">Classification</span>
          <span class="tag">Random Forest</span>
          <span class="tag">Feature Engineering</span>
          <span class="tag">EDA</span>
        </div>
      </div>

      <div class="task-card t2 reveal">
        <div class="task-bar"></div>
        <div class="task-number">Task 02</div>
        <span class="task-icon">🎬</span>
        <div class="task-title">Movie Rating Prediction</div>
        <div class="task-desc">Regression pipeline to estimate critic and audience scores from genre, director, cast, and release metadata. Explores NLP-based encoding for categorical high-cardinality features.</div>
        <div class="task-tags">
          <span class="tag">Regression</span>
          <span class="tag">NLP Features</span>
          <span class="tag">XGBoost</span>
          <span class="tag">Target Encoding</span>
        </div>
      </div>

      <div class="task-card t3 reveal">
        <div class="task-bar"></div>
        <div class="task-number">Task 03</div>
        <span class="task-icon">🌸</span>
        <div class="task-title">Iris Flower Classification</div>
        <div class="task-desc">Multi-class classification on the iconic Iris dataset. Visualize decision boundaries, compare SVM, KNN, and Logistic Regression, and achieve near-perfect accuracy on sepal/petal measurements.</div>
        <div class="task-tags">
          <span class="tag">Multi-class</span>
          <span class="tag">SVM</span>
          <span class="tag">Visualization</span>
          <span class="tag">KNN</span>
        </div>
      </div>

      <div class="task-card t4 reveal">
        <div class="task-bar"></div>
        <div class="task-number">Task 04</div>
        <span class="task-icon">📈</span>
        <div class="task-title">Sales Prediction</div>
        <div class="task-desc">Forecast product demand using advertising spend data across TV, radio, and digital. Build regression models to help marketing teams allocate budget and maximize ROI.</div>
        <div class="task-tags">
          <span class="tag">Forecasting</span>
          <span class="tag">Linear Regression</span>
          <span class="tag">RMSE</span>
          <span class="tag">Feature Importance</span>
        </div>
      </div>

      <div class="task-card t5 reveal">
        <div class="task-bar"></div>
        <div class="task-number">Task 05</div>
        <span class="task-icon">🛡️</span>
        <div class="task-title">Credit Card Fraud Detection</div>
        <div class="task-desc">High-stakes anomaly detection on severely imbalanced transaction data. Apply SMOTE, train Random Forest and Logistic Regression, and evaluate with precision-recall curves to protect real users.</div>
        <div class="task-tags">
          <span class="tag">Fraud Detection</span>
          <span class="tag">SMOTE</span>
          <span class="tag">Imbalanced Data</span>
          <span class="tag">F1-Score</span>
        </div>
      </div>

    </div>
  </section>

  <hr class="divider">

  <!-- ML PIPELINE -->
  <section class="section">
    <div class="section-label reveal">Methodology</div>
    <h2 class="section-title reveal">The <span class="hl-purple">ML Pipeline</span> <br>Used Across All Tasks</h2>
    <p class="section-desc reveal">Every project follows a consistent, production-grade workflow from raw data to evaluated model.</p>

    <div class="pipeline reveal">
      <div class="pipeline-steps">
        <div class="pipe-step">
          <div class="pipe-icon">📥</div>
          <div class="pipe-step-title">Data Ingestion</div>
          <div class="pipe-step-sub">Load & inspect raw datasets</div>
        </div>
        <div class="pipe-step">
          <div class="pipe-icon">🔍</div>
          <div class="pipe-step-title">EDA</div>
          <div class="pipe-step-sub">Distributions, correlations, outliers</div>
        </div>
        <div class="pipe-step">
          <div class="pipe-icon">🧹</div>
          <div class="pipe-step-title">Preprocessing</div>
          <div class="pipe-step-sub">Null handling, scaling, encoding</div>
        </div>
        <div class="pipe-step">
          <div class="pipe-icon">⚙️</div>
          <div class="pipe-step-title">Feature Eng.</div>
          <div class="pipe-step-sub">Selection, extraction, creation</div>
        </div>
        <div class="pipe-step">
          <div class="pipe-icon">🤖</div>
          <div class="pipe-step-title">Modeling</div>
          <div class="pipe-step-sub">Train multiple algorithms</div>
        </div>
        <div class="pipe-step">
          <div class="pipe-icon">📊</div>
          <div class="pipe-step-title">Evaluation</div>
          <div class="pipe-step-sub">Metrics, CV, confusion matrix</div>
        </div>
      </div>
    </div>
  </section>

  <hr class="divider">

  <!-- SKILLS -->
  <section class="section">
    <div class="section-label reveal">Competencies Developed</div>
    <h2 class="section-title reveal">Skills <span class="hl-green">Sharpened</span></h2>
    <div class="skills-grid reveal">
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent)"></div><div class="skill-name">Data Wrangling</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:92%;--bar-from:var(--accent);--bar-to:var(--accent2);--delay:0.1s"></div></div>
        <div class="skill-pct">92%</div>
      </div>
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent4)"></div><div class="skill-name">Feature Engineering</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:88%;--bar-from:var(--accent4);--bar-to:var(--accent5);--delay:0.2s"></div></div>
        <div class="skill-pct">88%</div>
      </div>
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent3)"></div><div class="skill-name">Model Training</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:90%;--bar-from:var(--accent3);--bar-to:var(--accent);--delay:0.3s"></div></div>
        <div class="skill-pct">90%</div>
      </div>
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent5)"></div><div class="skill-name">Model Evaluation</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:85%;--bar-from:var(--accent5);--bar-to:var(--accent4);--delay:0.4s"></div></div>
        <div class="skill-pct">85%</div>
      </div>
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent2)"></div><div class="skill-name">Data Visualization</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:80%;--bar-from:var(--accent2);--bar-to:var(--accent);--delay:0.5s"></div></div>
        <div class="skill-pct">80%</div>
      </div>
      <div class="skill-item">
        <div class="skill-item-head"><div class="skill-dot" style="background:var(--accent)"></div><div class="skill-name">Imbalanced Learning</div></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:78%;--bar-from:var(--accent);--bar-to:var(--accent3);--delay:0.6s"></div></div>
        <div class="skill-pct">78%</div>
      </div>
    </div>
  </section>

  <hr class="divider">

  <!-- SETUP -->
  <section class="section">
    <div class="section-label reveal">Getting Started</div>
    <h2 class="section-title reveal">Up & Running in <span class="hl-orange">3 Steps</span></h2>

    <div class="setup-block reveal">
      <div class="setup-header">
        <span class="setup-title">1 · Clone the Repository</span>
        <button class="copy-btn" onclick="copyCode(this,'clone')">Copy</button>
      </div>
      <div class="setup-code" id="clone">
        <span class="comment"># Clone the repo to your local machine</span><br>
        <span class="cmd">git clone</span> https://github.com/yourusername/codsoft-ds-internship.git<br>
        <span class="cmd">cd</span> codsoft-ds-internship
      </div>
    </div>

    <div class="setup-block reveal">
      <div class="setup-header">
        <span class="setup-title">2 · Install Dependencies</span>
        <button class="copy-btn" onclick="copyCode(this,'deps')">Copy</button>
      </div>
      <div class="setup-code" id="deps">
        <span class="comment"># Create and activate virtual environment</span><br>
        <span class="cmd">python -m venv</span> .venv<br>
        <span class="cmd">source</span> .venv/bin/activate &nbsp;&nbsp;<span class="comment"># Windows: .venv\Scripts\activate</span><br><br>
        <span class="comment"># Install all required packages</span><br>
        <span class="cmd">pip install</span> -r requirements.txt
      </div>
    </div>

    <div class="setup-block reveal">
      <div class="setup-header">
        <span class="setup-title">3 · Run Any Task Notebook</span>
        <button class="copy-btn" onclick="copyCode(this,'run')">Copy</button>
      </div>
      <div class="setup-code" id="run">
        <span class="comment"># Launch Jupyter and open the task of your choice</span><br>
        <span class="cmd">jupyter notebook</span><br><br>
        <span class="comment"># Or run a specific task directly</span><br>
        <span class="cmd">jupyter nbconvert --to notebook --execute</span> <span class="str">"Task1_Titanic/titanic.ipynb"</span>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-glow"></div>
    <div class="footer-logo">CODSOFT</div>
    <p class="footer-text">Data Science Internship · Built with Python, curiosity, and a lot of ☕</p>
    <div class="footer-links">
      <a href="#" class="footer-link">LinkedIn</a>
      <a href="#" class="footer-link">GitHub</a>
      <a href="#" class="footer-link">Twitter / X</a>
      <a href="#" class="footer-link">Portfolio</a>
      <a href="#" class="footer-link">CODSOFT</a>
    </div>
    <p style="color:var(--muted);font-size:0.72rem;margin-top:2rem;font-family:'Space Mono',monospace;">
      © 2024 · Made with scikit-learn, pandas, matplotlib, seaborn, XGBoost, imbalanced-learn
    </p>
  </footer>

</div>

<script>
// ── STARFIELD ──
(function() {
  const canvas = document.getElementById('starfield');
  const ctx = canvas.getContext('2d');
  let stars = [], W, H;

  function resize() {
    W = canvas.width = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }

  function initStars() {
    stars = [];
    for (let i = 0; i < 220; i++) {
      stars.push({
        x: Math.random() * W,
        y: Math.random() * H,
        r: Math.random() * 1.2 + 0.2,
        o: Math.random() * 0.6 + 0.1,
        speed: Math.random() * 0.15 + 0.03,
        twinkle: Math.random() * Math.PI * 2
      });
    }
  }

  function draw() {
    ctx.clearRect(0, 0, W, H);
    const t = Date.now() / 1000;
    stars.forEach(s => {
      s.twinkle += 0.01;
      const alpha = s.o * (0.7 + 0.3 * Math.sin(s.twinkle));
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(200, 220, 255, ${alpha})`;
      ctx.fill();
      s.y -= s.speed;
      if (s.y < 0) { s.y = H; s.x = Math.random() * W; }
    });
    requestAnimationFrame(draw);
  }

  resize(); initStars(); draw();
  window.addEventListener('resize', () => { resize(); initStars(); });
})();

// ── TECH PILLS ──
const techs = [
  { icon: '🐍', name: 'Python 3.11' },
  { icon: '🔢', name: 'NumPy' },
  { icon: '🐼', name: 'Pandas' },
  { icon: '📊', name: 'Matplotlib' },
  { icon: '🌊', name: 'Seaborn' },
  { icon: '🤖', name: 'scikit-learn' },
  { icon: '⚡', name: 'XGBoost' },
  { icon: '⚖️', name: 'imbalanced-learn' },
  { icon: '📓', name: 'Jupyter' },
  { icon: '🔬', name: 'SciPy' },
  { icon: '🌲', name: 'Random Forest' },
  { icon: '📉', name: 'Logistic Reg.' },
  { icon: '🎯', name: 'SVM' },
  { icon: '🔍', name: 'KNN' },
];

const track = document.getElementById('techTrack');
const doubled = [...techs, ...techs];
doubled.forEach(t => {
  const pill = document.createElement('div');
  pill.className = 'tech-pill';
  pill.innerHTML = `<span class="icon">${t.icon}</span>${t.name}`;
  track.appendChild(pill);
});

// ── SCROLL REVEAL ──
const observer = new IntersectionObserver((entries) => {
  entries.forEach((e, i) => {
    if (e.isIntersecting) {
      e.target.style.transitionDelay = (i * 0.06) + 's';
      e.target.classList.add('visible');
    }
  });
}, { threshold: 0.12 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

// ── COPY BUTTONS ──
function copyCode(btn, id) {
  const el = document.getElementById(id);
  const text = el.innerText.replace(/^\s*#.*\n/gm, '').trim();
  navigator.clipboard.writeText(text).then(() => {
    btn.textContent = 'Copied!';
    btn.style.color = 'var(--accent3)';
    setTimeout(() => { btn.textContent = 'Copy'; btn.style.color = ''; }, 2000);
  });
}

// ── FLOATING PARTICLES ──
function spawnParticle() {
  const p = document.createElement('div');
  p.className = 'particle';
  const colors = ['var(--accent)', 'var(--accent2)', 'var(--accent3)', 'var(--accent4)'];
  p.style.cssText = `
    left: ${Math.random() * 100}vw;
    bottom: ${Math.random() * 30}vh;
    --dur: ${4 + Math.random() * 6}s;
    --delay2: ${Math.random() * 4}s;
    background: ${colors[Math.floor(Math.random() * colors.length)]};
    width: ${1 + Math.random() * 2}px;
    height: ${1 + Math.random() * 2}px;
  `;
  document.body.appendChild(p);
  setTimeout(() => p.remove(), 10000);
}
setInterval(spawnParticle, 600);
</script>

</body>
</html>
