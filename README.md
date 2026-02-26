<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Joaquín Galbis — Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;700;900&family=Barlow:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --black: #0a0a0a;
      --white: #f5f5f5;
      --gray-dark: #1c1c1c;
      --gray-mid: #6b6b6b;
      --gray-light: #d4d4d4;
      --gray-bg: #f0f0f0;
      --red: #e01e2e;
      --red-dark: #b5172a;
      --font-display: 'Barlow Condensed', 'Impact', sans-serif;
      --font-body: 'Barlow', 'Helvetica Neue', Helvetica, sans-serif;
    }
    html { scroll-behavior: smooth; }
    body {
      background: var(--white);
      color: var(--black);
      font-family: var(--font-body);
      font-weight: 300;
      line-height: 1.6;
    }

    /* ─── NAV ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 48px; height: 64px;
      background: var(--white);
      border-bottom: 1px solid var(--gray-light);
      transition: box-shadow 0.3s;
    }
    nav.scrolled { box-shadow: 0 2px 20px rgba(0,0,0,0.08); }
    .nav-logo {
      font-family: var(--font-display); font-weight: 900; font-size: 1.4rem;
      letter-spacing: 0.06em; text-transform: uppercase;
      color: var(--black); text-decoration: none;
    }
    .nav-logo span { color: var(--red); }
    .nav-links { display: flex; gap: 40px; list-style: none; }
    .nav-links a {
      font-family: var(--font-display); font-weight: 700; font-size: 0.85rem;
      letter-spacing: 0.12em; text-transform: uppercase; text-decoration: none;
      color: var(--gray-mid); transition: color 0.2s; position: relative;
    }
    .nav-links a::after {
      content: ''; position: absolute; bottom: -3px; left: 0;
      width: 0; height: 2px; background: var(--red); transition: width 0.25s ease;
    }
    .nav-links a:hover { color: var(--black); }
    .nav-links a:hover::after { width: 100%; }

    /* ─── HERO ─── */
    #home {
      min-height: 100vh; display: grid; grid-template-columns: 1fr 1fr;
      padding-top: 64px;
    }
    .hero-text {
      display: flex; flex-direction: column; justify-content: center;
      padding: 80px 60px 80px 80px;
    }
    .hero-tag {
      font-family: var(--font-display); font-weight: 700; font-size: 0.75rem;
      letter-spacing: 0.2em; text-transform: uppercase; color: var(--red);
      margin-bottom: 20px;
    }
    .hero-name {
      font-family: var(--font-display); font-weight: 900;
      font-size: clamp(3.5rem, 6vw, 6rem); line-height: 0.92;
      text-transform: uppercase; letter-spacing: -0.01em;
      color: var(--black); margin-bottom: 24px;
    }
    .hero-name .line2 { color: var(--gray-mid); }
    .hero-slogan {
      font-family: var(--font-display); font-weight: 400; font-size: 1.15rem;
      letter-spacing: 0.08em; text-transform: uppercase; color: var(--gray-mid);
      border-left: 3px solid var(--red); padding-left: 16px; margin-bottom: 40px;
    }
    .hero-cta { display: flex; gap: 16px; flex-wrap: wrap; }
    .btn {
      font-family: var(--font-display); font-weight: 700; font-size: 0.8rem;
      letter-spacing: 0.14em; text-transform: uppercase; text-decoration: none;
      padding: 14px 32px; border: 2px solid var(--black);
      color: var(--black); background: transparent; cursor: pointer;
      transition: all 0.22s ease; display: inline-block;
    }
    .btn:hover { background: var(--black); color: var(--white); }
    .btn.btn-red { background: var(--red); border-color: var(--red); color: var(--white); }
    .btn.btn-red:hover { background: var(--red-dark); border-color: var(--red-dark); }
    .hero-visual {
      background: var(--black); position: relative; overflow: hidden;
      display: flex; align-items: center; justify-content: center;
    }
    .hero-grid-lines {
      position: absolute; inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 40px 40px;
    }
    .initials-block {
      font-family: var(--font-display); font-weight: 900;
      font-size: clamp(6rem, 14vw, 14rem); line-height: 1;
      color: transparent; -webkit-text-stroke: 1px rgba(255,255,255,0.12);
      letter-spacing: -0.05em; position: absolute;
      top: 50%; left: 50%; transform: translate(-50%, -50%); user-select: none;
    }
    .hero-visual-inner { position: relative; z-index: 3; text-align: center; padding: 40px; }
    .hero-role-badge {
      display: inline-block; background: var(--red); color: var(--white);
      font-family: var(--font-display); font-weight: 700; font-size: 0.75rem;
      letter-spacing: 0.18em; text-transform: uppercase; padding: 8px 20px;
    }
    .hero-accent-bar {
      position: absolute; bottom: 0; left: 0; width: 100%; height: 4px;
      background: var(--red);
    }

    /* ─── SECTIONS ─── */
    section { padding: 100px 80px; }
    .section-label {
      font-family: var(--font-display); font-weight: 700; font-size: 0.75rem;
      letter-spacing: 0.22em; text-transform: uppercase; color: var(--red);
      display: block; margin-bottom: 12px;
    }
    .section-title {
      font-family: var(--font-display); font-weight: 900;
      font-size: clamp(2.5rem, 4vw, 4rem); text-transform: uppercase;
      line-height: 1; margin-bottom: 60px; letter-spacing: -0.01em;
    }

    /* ─── ABOUT ─── */
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; }
    .about-text p {
      font-size: 1rem; color: var(--gray-mid); margin-bottom: 20px; line-height: 1.8;
    }
    .about-right-title {
      font-family: var(--font-display); font-weight: 700; font-size: 0.7rem;
      letter-spacing: 0.2em; text-transform: uppercase; color: var(--black);
      margin-bottom: 20px;
    }
    .skills-grid { display: flex; flex-wrap: wrap; gap: 10px; }
    .skill-tag {
      font-family: var(--font-display); font-weight: 700; font-size: 0.72rem;
      letter-spacing: 0.12em; text-transform: uppercase;
      padding: 8px 16px; border: 1.5px solid var(--black); color: var(--black);
      opacity: 0; transform: translateY(12px);
      transition: opacity 0.4s ease, transform 0.4s ease, background 0.2s, color 0.2s;
    }
    .skill-tag.visible { opacity: 1; transform: translateY(0); }
    .skill-tag:hover { background: var(--black); color: var(--white); }

    /* ─── WORK ─── */
    #work { background: var(--black); }
    #work .section-title { color: var(--white); }
    #work .section-label { color: var(--red); }
    .work-grid {
      display: grid; grid-template-columns: repeat(2, 1fr); gap: 2px;
    }
    .work-card {
      position: relative; aspect-ratio: 16/10; overflow: hidden;
      cursor: pointer; background: var(--gray-dark);
    }
    .work-card-bg {
      position: absolute; inset: 0;
      background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
      transition: transform 0.5s ease;
    }
    .work-card:hover .work-card-bg { transform: scale(1.04); }
    .work-card-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0.2) 60%, transparent 100%);
    }
    .work-card-content {
      position: absolute; inset: 0;
      padding: 32px; display: flex; flex-direction: column; justify-content: flex-end;
    }
    .work-card-num {
      font-family: var(--font-display); font-weight: 900; font-size: 0.7rem;
      letter-spacing: 0.2em; color: var(--red); margin-bottom: 8px;
    }
    .work-card-tag {
      font-family: var(--font-display); font-weight: 700; font-size: 0.65rem;
      letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.5);
      margin-bottom: 8px;
    }
    .work-card-title {
      font-family: var(--font-display); font-weight: 900; font-size: 1.6rem;
      text-transform: uppercase; color: var(--white); line-height: 1.05;
      margin-bottom: 10px;
    }
    .work-card-desc {
      font-size: 0.82rem; color: rgba(255,255,255,0.55); line-height: 1.5;
      max-width: 360px;
    }
    .work-card-arrow {
      position: absolute; top: 28px; right: 28px;
      font-size: 1.2rem; color: rgba(255,255,255,0.3);
      transition: color 0.2s, transform 0.2s;
    }
    .work-card:hover .work-card-arrow { color: var(--red); transform: translate(3px,-3px); }

    /* ─── PROJECT PANEL (full-width expand) ─── */
    .project-panel {
      display: none;
      background: var(--white);
      border-top: 4px solid var(--red);
    }
    .project-panel.active { display: block; }
    .panel-inner {
      max-width: 1100px; margin: 0 auto;
      padding: 60px 80px 80px;
    }
    .panel-close-bar {
      display: flex; justify-content: space-between; align-items: center;
      margin-bottom: 48px;
    }
    .panel-project-label {
      font-family: var(--font-display); font-weight: 700; font-size: 0.7rem;
      letter-spacing: 0.22em; text-transform: uppercase; color: var(--red);
    }
    .panel-close-btn {
      font-family: var(--font-display); font-weight: 700; font-size: 0.72rem;
      letter-spacing: 0.16em; text-transform: uppercase;
      background: none; border: 1.5px solid var(--gray-mid);
      color: var(--gray-mid); padding: 8px 20px; cursor: pointer;
      transition: all 0.2s;
    }
    .panel-close-btn:hover { border-color: var(--black); color: var(--black); }
    .panel-title {
      font-family: var(--font-display); font-weight: 900;
      font-size: clamp(2rem, 4vw, 3.5rem); text-transform: uppercase;
      line-height: 1; margin-bottom: 40px;
    }
    .panel-layout {
      display: grid; grid-template-columns: 1fr 1fr; gap: 60px;
      align-items: start;
    }
    .panel-embed {
      width: 100%; aspect-ratio: 16/10; background: #111;
      border: none; display: block;
    }
    .panel-summary h3 {
      font-family: var(--font-display); font-weight: 900; font-size: 0.7rem;
      letter-spacing: 0.2em; text-transform: uppercase; color: var(--red);
      margin-bottom: 16px; margin-top: 32px;
    }
    .panel-summary h3:first-child { margin-top: 0; }
    .panel-summary p {
      font-size: 0.95rem; color: var(--gray-mid); line-height: 1.8; margin-bottom: 12px;
    }
    .panel-pills {
      display: flex; flex-wrap: wrap; gap: 8px; margin-top: 28px;
    }
    .panel-pill {
      font-family: var(--font-display); font-weight: 700; font-size: 0.65rem;
      letter-spacing: 0.14em; text-transform: uppercase;
      padding: 5px 12px; border: 1.5px solid var(--black); color: var(--black);
    }
    .panel-view-btn {
      display: inline-block; margin-top: 32px;
    }

    /* ─── SERVICES ─── */
    .services-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; }
    .service-card {
      padding: 48px 40px; border: 1px solid var(--gray-light);
      transition: border-color 0.2s, background 0.2s;
    }
    .service-card:hover { border-color: var(--black); background: var(--black); }
    .service-card:hover .service-name,
    .service-card:hover .service-desc { color: var(--white); }
    .service-icon { font-size: 1.4rem; display: block; margin-bottom: 24px; }
    .service-name {
      font-family: var(--font-display); font-weight: 900; font-size: 1.3rem;
      text-transform: uppercase; letter-spacing: 0.02em; margin-bottom: 16px;
      transition: color 0.2s;
    }
    .service-desc { font-size: 0.88rem; color: var(--gray-mid); line-height: 1.7; transition: color 0.2s; }

    /* ─── CONTACT ─── */
    #contact { background: var(--black); }
    #contact .section-title { color: var(--white); }
    #contact .section-label { color: var(--red); }
    .contact-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; }
    .contact-intro { font-size: 1rem; color: rgba(255,255,255,0.55); line-height: 1.8; margin-bottom: 40px; }
    .contact-line {
      display: flex; gap: 20px; align-items: baseline;
      padding: 16px 0; border-bottom: 1px solid rgba(255,255,255,0.08);
    }
    .contact-line .label {
      font-family: var(--font-display); font-weight: 700; font-size: 0.7rem;
      letter-spacing: 0.2em; text-transform: uppercase; color: var(--red);
      min-width: 80px;
    }
    .contact-line span:last-child { font-size: 0.9rem; color: rgba(255,255,255,0.7); }
    .contact-line a { color: rgba(255,255,255,0.7); text-decoration: none; }
    .contact-line a:hover { color: var(--red); }
    .contact-form { display: flex; flex-direction: column; gap: 16px; }
    .contact-form input, .contact-form textarea {
      background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.12);
      padding: 14px 18px; font-family: var(--font-body); font-size: 0.9rem;
      color: var(--white); outline: none; transition: border-color 0.2s;
    }
    .contact-form input:focus, .contact-form textarea:focus { border-color: var(--red); }
    .contact-form textarea { min-height: 140px; resize: vertical; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }

    /* ─── FOOTER ─── */
    footer {
      background: var(--black); padding: 32px 80px;
      display: flex; justify-content: space-between; align-items: center;
      border-top: 1px solid rgba(255,255,255,0.06);
    }
    .footer-logo {
      font-family: var(--font-display); font-weight: 900; font-size: 1.6rem;
      color: var(--white); letter-spacing: 0.06em;
    }
    .footer-logo span { color: var(--red); }
    .footer-copy { font-size: 0.75rem; color: rgba(255,255,255,0.35); letter-spacing: 0.06em; }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .hero-tag  { animation: fadeUp 0.7s ease both; animation-delay: 0.1s; }
    .hero-name { animation: fadeUp 0.7s ease both; animation-delay: 0.25s; }
    .hero-slogan { animation: fadeUp 0.7s ease both; animation-delay: 0.4s; }
    .hero-cta  { animation: fadeUp 0.7s ease both; animation-delay: 0.55s; }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 900px) {
      nav { padding: 0 24px; }
      section { padding: 70px 24px; }
      #home { grid-template-columns: 1fr; }
      .hero-visual { min-height: 40vh; }
      .hero-text { padding: 60px 24px; }
      .about-grid, .contact-layout, .panel-layout { grid-template-columns: 1fr; gap: 40px; }
      .work-grid { grid-template-columns: 1fr; }
      .services-grid { grid-template-columns: 1fr; }
      .panel-inner { padding: 40px 24px 60px; }
      footer { flex-direction: column; gap: 12px; text-align: center; padding: 24px; }
    }
    @media (max-width: 600px) {
      .form-row { grid-template-columns: 1fr; }
      .nav-links { gap: 20px; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav id="navbar">
    <a href="#home" class="nav-logo">JG<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#work">My Work</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="home">
    <div class="hero-text">
      <span class="hero-tag">Portfolio</span>
      <h1 class="hero-name">Joaquín<br><span class="line2">Galbis</span></h1>
      <p class="hero-slogan">Smart ideas, meaningful impact</p>
      <div class="hero-cta">
        <a href="#work" class="btn btn-red">View My Work</a>
        <a href="#contact" class="btn">Get in Touch</a>
      </div>
    </div>
    <div class="hero-visual">
      <div class="hero-grid-lines"></div>
      <div class="initials-block">JG</div>
      <div class="hero-visual-inner">
        <div class="hero-role-badge">Digital Marketing</div>
      </div>
      <div class="hero-accent-bar"></div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <span class="section-label">Who I am</span>
    <h2 class="section-title">About Me</h2>
    <div class="about-grid">
      <div class="about-text">
        <p>I'm Joaquín Galbis, a digital marketer with a strong interest in strategic thinking, brand storytelling, and data-informed creative work. I approach every project with curiosity and a drive to connect ideas to real audiences.</p>
        <p>My work sits at the intersection of strategy, content, and digital channels — always with the goal of producing ideas that are both smart and meaningful.</p>
        <p>This portfolio brings together projects that reflect my approach to digital marketing and communication — from research and strategy to campaign execution.</p>
      </div>
      <div class="about-right">
        <p class="about-right-title">Skills &amp; Disciplines</p>
        <div class="skills-grid">
          <span class="skill-tag">Digital Strategy</span>
          <span class="skill-tag">Content Marketing</span>
          <span class="skill-tag">Social Media</span>
          <span class="skill-tag">Brand Strategy</span>
          <span class="skill-tag">Campaign Planning</span>
          <span class="skill-tag">Market Research</span>
          <span class="skill-tag">SEO</span>
          <span class="skill-tag">Analytics &amp; Insight</span>
        </div>
      </div>
    </div>
  </section>

  <!-- MY WORK -->
  <section id="work">
    <span class="section-label">Selected Projects</span>
    <h2 class="section-title">My Work</h2>

    <div class="work-grid">

      <!-- CARD 1: FUSTER LAB -->
      <div class="work-card" onclick="togglePanel('panel1', this)">
        <div class="work-card-bg"></div>
        <div class="work-card-overlay"></div>
        <div class="work-card-content">
          <div class="work-card-num">01</div>
          <div class="work-card-tag">Coming Soon · Fuster Lab</div>
          <div class="work-card-title">Fuster Lab</div>
          <div class="work-card-desc">Project details coming soon — click to preview the presentation.</div>
        </div>
        <span class="work-card-arrow">↗</span>
      </div>

      <!-- CARD 2: GREEN GATHERINGS I -->
      <div class="work-card" onclick="togglePanel('panel2', this)">
        <div class="work-card-bg"></div>
        <div class="work-card-overlay"></div>
        <div class="work-card-content">
          <div class="work-card-num">02</div>
          <div class="work-card-tag">Content Marketing · Sustainability</div>
          <div class="work-card-title">Green Gatherings I</div>
          <div class="work-card-desc">Inbound content marketing campaign: brand messaging, market research, buyer persona, blog article, and product landing page.</div>
        </div>
        <span class="work-card-arrow">↗</span>
      </div>

      <!-- CARD 3: GREEN GATHERINGS II -->
      <div class="work-card" onclick="togglePanel('panel3', this)">
        <div class="work-card-bg"></div>
        <div class="work-card-overlay"></div>
        <div class="work-card-content">
          <div class="work-card-num">03</div>
          <div class="work-card-tag">SEO &amp; Email Marketing · Sustainability</div>
          <div class="work-card-title">Green Gatherings II</div>
          <div class="work-card-desc">SEO optimisation, Google Analytics funnel tracking, and a 3-email Mailchimp campaign with measurable results.</div>
        </div>
        <span class="work-card-arrow">↗</span>
      </div>

      <!-- CARD 4: ONE HEALTH -->
      <div class="work-card" onclick="togglePanel('panel4', this)">
        <div class="work-card-bg"></div>
        <div class="work-card-overlay"></div>
        <div class="work-card-content">
          <div class="work-card-num">04</div>
          <div class="work-card-tag">Social Media Strategy · Healthcare</div>
          <div class="work-card-title">One Health</div>
          <div class="work-card-desc">Full social media marketing strategy for a digital health app across Instagram, Facebook, and Twitter.</div>
        </div>
        <span class="work-card-arrow">↗</span>
      </div>

    </div><!-- /.work-grid -->


    <!-- PANEL 1: FUSTER LAB -->
    <div class="project-panel" id="panel1">
      <div class="panel-inner">
        <div class="panel-close-bar">
          <span class="panel-project-label">01 — SEO &amp; Email Marketing</span>
          <button class="panel-close-btn" onclick="closePanel('panel1')">✕ Close</button>
        </div>
        <h2 class="panel-title">Fuster Lab</h2>
        <div class="panel-layout">
          <div>
            <iframe class="panel-embed"
              src="https://www.canva.com/design/DAG3CZwuY54/7Op8S_BwUvwIVf7awwPd1g/view?embed"
              allow="fullscreen" allowfullscreen
              title="Fuster Lab">
            </iframe>
            <a href="https://www.canva.com/design/DAG3CZwuY54/7Op8S_BwUvwIVf7awwPd1g/view" target="_blank" rel="noopener" class="btn btn-red panel-view-btn">Open Full Presentation ↗</a>
          </div>
          <div class="panel-summary">
            <h3>The Project</h3>
            <p>A project focused on SEO optimisation, data analytics, and email marketing execution using real tools — combining technical and strategic work to drive measurable results.</p>
            <h3>My Contribution</h3>
            <p><strong>SEO:</strong> I used SEMrush and Moz to research and select the primary keyword. I optimised both the landing page and blog article — updating headings, restructuring content, compressing images, and improving URL structure. Page performance improved significantly across both assets.</p>
            <p><strong>Analytics:</strong> I set up Google Analytics tracking, built a funnel event to monitor the full user journey, and tracked CTA click events to measure real conversion behaviour.</p>
            <p><strong>Email Campaign:</strong> I designed and sent a 3-email Mailchimp sequence structured as welcome → problem/solution → human story → CTA. The campaign exceeded open rate targets and drove traffic well above the pageview goals set at the start of the project.</p>
            <div class="panel-pills">
              <span class="panel-pill">SEO Optimisation</span>
              <span class="panel-pill">Keyword Research</span>
              <span class="panel-pill">Google Analytics</span>
              <span class="panel-pill">Funnel Analysis</span>
              <span class="panel-pill">Email Marketing</span>
              <span class="panel-pill">Mailchimp</span>
              <span class="panel-pill">KPI Reporting</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- PANEL 2: GREEN GATHERINGS I -->
    <div class="project-panel" id="panel2">
      <div class="panel-inner">
        <div class="panel-close-bar">
          <span class="panel-project-label">02 — Content Marketing · Sustainability</span>
          <button class="panel-close-btn" onclick="closePanel('panel2')">✕ Close</button>
        </div>
        <h2 class="panel-title">Green Gatherings I</h2>
        <div class="panel-layout">
          <div>
            <iframe class="panel-embed"
              src="https://www.canva.com/design/DAG2_AQLSIc/HlwJeu-jRPsVmjxN_THYrA/view?embed"
              allow="fullscreen" allowfullscreen
              title="Green Gatherings – Content Marketing Campaign">
            </iframe>
            <a href="https://www.canva.com/design/DAG2_AQLSIc/HlwJeu-jRPsVmjxN_THYrA/view" target="_blank" rel="noopener" class="btn btn-red panel-view-btn">Open Full Presentation ↗</a>
          </div>
          <div class="panel-summary">
            <h3>The Project</h3>
            <p>Designed a complete inbound content marketing campaign for <strong>Green Gatherings</strong>, a biodegradable picnic products brand, covering the full funnel from awareness to conversion.</p>
            <h3>My Contribution</h3>
            <p>I built the brand messaging framework: mission, purpose, UVP, values, tone of voice, colour palette, and logo. I then conducted market research and competitor analysis (LEEF, GreenBox, Oasis Green), identifying key gaps around affordability, community, and anti-greenwashing positioning.</p>
            <p>From the research I developed the buyer persona "Emma" — a 40-year-old environmentally conscious mother in Munich — and used her profile to guide all content decisions.</p>
            <p>I produced three campaign pieces: a long-form educational blog article for the attention stage, an email course for consideration, and a product landing page with strong CTAs and a launch offer for the decision stage.</p>
            <div class="panel-pills">
              <span class="panel-pill">Brand Messaging</span>
              <span class="panel-pill">Market Research</span>
              <span class="panel-pill">Competitor Analysis</span>
              <span class="panel-pill">Buyer Persona</span>
              <span class="panel-pill">Blog Article</span>
              <span class="panel-pill">Landing Page</span>
              <span class="panel-pill">Inbound Strategy</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- PANEL 3: GREEN GATHERINGS II -->
    <div class="project-panel" id="panel3">
      <div class="panel-inner">
        <div class="panel-close-bar">
          <span class="panel-project-label">03 — Social Media Strategy · Sustainability</span>
          <button class="panel-close-btn" onclick="closePanel('panel3')">✕ Close</button>
        </div>
        <h2 class="panel-title">Green Gatherings II</h2>
        <div class="panel-layout">
          <div>
            <iframe class="panel-embed"
              src="https://www.canva.com/design/DAG5VdtgM2k/JipYG4ji2WWefjEduIDzAQ/view?embed"
              allow="fullscreen" allowfullscreen
              title="Green Gatherings II">
            </iframe>
            <a href="https://www.canva.com/design/DAG5VdtgM2k/JipYG4ji2WWefjEduIDzAQ/view" target="_blank" rel="noopener" class="btn btn-red panel-view-btn">Open Full Presentation ↗</a>
          </div>
          <div class="panel-summary">
            <h3>The Project</h3>
            <p>Developed a full social media marketing strategy for <strong>Green Gatherings</strong>, covering goal setting, platform selection, audience research, content pillars, brand guidelines, post templates, and a growth strategy.</p>
            <h3>My Contribution</h3>
            <p>I defined the core business goals and translated each into measurable social media objectives with specific KPIs across platforms. I structured the content strategy around four pillars, with a tailored approach for each channel.</p>
            <p>I developed detailed brand guidelines covering voice, visual identity, and image direction, built a two-week content calendar with post formats and captions, and designed a community management answer flowchart for handling comments and DMs.</p>
            <p>I also proposed a growth strategy through an Instagram giveaway, benchmarked against real competitor examples to validate the mechanic and format.</p>
            <div class="panel-pills">
              <span class="panel-pill">Social Media Strategy</span>
              <span class="panel-pill">Content Planning</span>
              <span class="panel-pill">Brand Guidelines</span>
              <span class="panel-pill">Audience Research</span>
              <span class="panel-pill">Growth Strategy</span>
              <span class="panel-pill">KPI Framework</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- PANEL 4: ONE HEALTH -->
    <div class="project-panel" id="panel4">
      <div class="panel-inner">
        <div class="panel-close-bar">
          <span class="panel-project-label">04 — Social Media Strategy · Healthcare</span>
          <button class="panel-close-btn" onclick="closePanel('panel4')">✕ Close</button>
        </div>
        <h2 class="panel-title">One Health</h2>
        <div class="panel-layout">
          <div>
            <iframe class="panel-embed"
              src="https://www.canva.com/design/DAG-4W3aHJo/3R_r5RHICIlSULGf4CSKuQ/view?embed"
              allow="fullscreen" allowfullscreen
              title="One Health – Social Media Strategy">
            </iframe>
            <a href="https://www.canva.com/design/DAG-4W3aHJo/3R_r5RHICIlSULGf4CSKuQ/view" target="_blank" rel="noopener" class="btn btn-red panel-view-btn">Open Full Presentation ↗</a>
          </div>
          <div class="panel-summary">
            <h3>The Project</h3>
            <p>Developed a full social media marketing strategy for <strong>One Health</strong>, a digital health app targeting adults across different age groups in the US. The brief required building a coherent, multi-platform presence from the ground up.</p>
            <h3>My Contribution</h3>
            <p>I defined three business goals — brand awareness, health leadership, and customer acquisition — and translated each into measurable social media objectives with specific KPIs (reach, CTR, app sign-ups).</p>
            <p>I structured the content strategy around four pillars: Health Education, Human Stories, Wellness &amp; Healthy Living, and Engagement &amp; Brand Growth, with a tailored approach for Instagram, Facebook, and Twitter/X.</p>
            <p>I developed detailed brand guidelines, built a two-week content calendar, designed a community management answer flowchart, and proposed a growth strategy through an Instagram giveaway benchmarked against competitors Viome and VitaHealth.</p>
            <div class="panel-pills">
              <span class="panel-pill">Social Media Strategy</span>
              <span class="panel-pill">Content Planning</span>
              <span class="panel-pill">Brand Guidelines</span>
              <span class="panel-pill">Audience Research</span>
              <span class="panel-pill">Growth Strategy</span>
              <span class="panel-pill">KPI Framework</span>
            </div>
          </div>
        </div>
      </div>
    </div>

  </section><!-- /#work -->

  <!-- SERVICES -->
  <section id="services">
    <span class="section-label">What I offer</span>
    <h2 class="section-title">Services</h2>
    <div class="services-grid">
      <div class="service-card">
        <span class="service-icon">✦</span>
        <div class="service-name">Digital Strategy</div>
        <div class="service-desc">Building data-informed digital marketing strategies that align brand goals with audience behaviour across online channels.</div>
      </div>
      <div class="service-card">
        <span class="service-icon">◈</span>
        <div class="service-name">Content &amp; Social Media</div>
        <div class="service-desc">Planning and creating content strategies for social platforms that engage communities and grow brand presence.</div>
      </div>
      <div class="service-card">
        <span class="service-icon">◻</span>
        <div class="service-name">Research &amp; Insight</div>
        <div class="service-desc">Conducting consumer and market research to uncover meaningful insights that fuel strategic and creative decisions.</div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <span class="section-label">Let's talk</span>
    <h2 class="section-title">Contact</h2>
    <div class="contact-layout">
      <div>
        <p class="contact-intro">Whether you want to collaborate, ask about my work, or just say hello — I'd love to hear from you.</p>
        <div class="contact-line">
          <span class="label">Email</span>
          <span><a href="/cdn-cgi/l/email-protection#78121719090d11161f19141a110b1e0d0b0c1d0a381f15191114561b1715"><span class="__cf_email__" data-cfemail="cca6a3adbdb9a5a2abada0aea5bfaab9bfb8a9be8caba1ada5a0e2afa3a1">[email&#160;protected]</span></a></span>
        </div>
        <div class="contact-line">
          <span class="label">Location</span>
          <span>Berlin, Germany</span>
        </div>
      </div>
      <form class="contact-form" onsubmit="return false;">
        <div class="form-row">
          <input type="text" placeholder="Name" />
          <input type="email" placeholder="Email" />
        </div>
        <input type="text" placeholder="Subject" />
        <textarea placeholder="Your message"></textarea>
        <button type="submit" class="btn btn-red" style="align-self:flex-start;">Send Message</button>
      </form>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">JG<span>.</span></div>
    <p class="footer-copy">© 2025 Joaquín Galbis — Smart ideas, meaningful impact</p>
  </footer>

  <script data-cfasync="false" src="/cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js"></script><script>
    // Nav scroll shadow
    window.addEventListener('scroll', () => {
      document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 20);
    });

    // Skill tag fade-in on scroll
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.querySelectorAll('.skill-tag').forEach((tag, i) => {
            setTimeout(() => tag.classList.add('visible'), i * 60);
          });
        }
      });
    }, { threshold: 0.2 });
    document.querySelectorAll('.skills-grid').forEach(el => observer.observe(el));

    // Panel toggle
    function togglePanel(id, card) {
      const panel = document.getElementById(id);
      const isOpen = panel.classList.contains('active');

      // Close all panels first
      document.querySelectorAll('.project-panel').forEach(p => p.classList.remove('active'));
      document.querySelectorAll('.work-card').forEach(c => c.style.outline = '');

      if (!isOpen) {
        panel.classList.add('active');
        card.style.outline = '3px solid #e01e2e';
        // Smooth scroll to panel
        setTimeout(() => {
          panel.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }, 50);
      }
    }

    function closePanel(id) {
      const panel = document.getElementById(id);
      panel.classList.rem
