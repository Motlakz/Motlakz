<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Motlalepula Sello — Software Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=DM+Mono:wght@400;500&family=Bricolage+Grotesque:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg: #06080f;
  --surface: #0d1117;
  --card: #0f1520;
  --border: #1a2235;
  --border-hi: #243050;
  --lime: #c8f542;
  --cyan: #3de8c8;
  --orange: #ff8c42;
  --rose: #ff5e87;
  --blue: #4d9eff;
  --text: #dce4f0;
  --muted: #58667a;
  --faint: #1c2535;
}

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  font-family: 'DM Mono', monospace;
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 100;
  opacity: 0.6;
}

.glow-tl {
  position: fixed;
  top: -200px; left: -200px;
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(200,245,66,0.06) 0%, transparent 70%);
  pointer-events: none;
}
.glow-br {
  position: fixed;
  bottom: -200px; right: -200px;
  width: 600px; height: 600px;
  background: radial-gradient(circle, rgba(61,232,200,0.05) 0%, transparent 70%);
  pointer-events: none;
}

.page {
  position: relative;
  z-index: 1;
  max-width: 900px;
  margin: 0 auto;
  padding: 64px 28px 96px;
}

/* HEADER */
.header {
  margin-bottom: 64px;
  animation: rise 0.7s cubic-bezier(.16,1,.3,1) both;
}

.header-top {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 28px;
}

.eyebrow {
  font-family: 'DM Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 0.28em;
  color: var(--lime);
  text-transform: uppercase;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.eyebrow::before {
  content: '';
  display: inline-block;
  width: 20px; height: 1px;
  background: var(--lime);
}

h1 {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: clamp(2.4rem, 6vw, 4rem);
  font-weight: 800;
  line-height: 1.0;
  letter-spacing: -0.03em;
  color: var(--text);
}

h1 .accent {
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-weight: 400;
  background: linear-gradient(110deg, var(--lime) 0%, var(--cyan) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-size: 0.78rem;
  color: var(--muted);
  margin-top: 10px;
  letter-spacing: 0.04em;
}
.subtitle span { color: var(--text); }

.header-right {
  display: flex;
  flex-direction: column;
  gap: 8px;
  align-items: flex-end;
  padding-top: 8px;
}

.location-tag {
  font-size: 0.68rem;
  color: var(--muted);
  letter-spacing: 0.08em;
}

.contact-link {
  font-size: 0.68rem;
  color: var(--cyan);
  text-decoration: none;
  letter-spacing: 0.05em;
  transition: opacity 0.15s;
}
.contact-link:hover { opacity: 0.7; }

/* STATS */
.stats-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0;
  border: 1px solid var(--border);
  border-radius: 12px;
  overflow: hidden;
  animation: rise 0.7s 0.1s cubic-bezier(.16,1,.3,1) both;
}

.stat {
  flex: 1;
  min-width: 120px;
  padding: 18px 20px;
  border-right: 1px solid var(--border);
  background: var(--card);
  transition: background 0.2s;
}
.stat:last-child { border-right: none; }
.stat:hover { background: var(--faint); }

.stat-num {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 1.7rem;
  font-weight: 800;
  line-height: 1;
  margin-bottom: 4px;
}
.stat-num.lime   { color: var(--lime); }
.stat-num.cyan   { color: var(--cyan); }
.stat-num.orange { color: var(--orange); }
.stat-num.rose   { color: var(--rose); }

.stat-label {
  font-size: 0.62rem;
  color: var(--muted);
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

/* SECTION */
.section { margin-bottom: 48px; }

.section-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 20px;
}

.section-title {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--muted);
}

.section-line {
  flex: 1;
  height: 1px;
  background: var(--border);
}

/* PROJECTS */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.project-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 18px 16px;
  text-decoration: none;
  color: inherit;
  display: flex;
  flex-direction: column;
  gap: 8px;
  transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
  position: relative;
  overflow: hidden;
  animation: rise 0.6s cubic-bezier(.16,1,.3,1) both;
}
.project-card:nth-child(1) { animation-delay: 0.15s; }
.project-card:nth-child(2) { animation-delay: 0.2s; }
.project-card:nth-child(3) { animation-delay: 0.25s; }

.project-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
}
.project-card.p1::before { background: linear-gradient(90deg, var(--lime), var(--cyan)); }
.project-card.p2::before { background: linear-gradient(90deg, var(--orange), var(--rose)); }
.project-card.p3::before { background: linear-gradient(90deg, var(--blue), var(--cyan)); }

.project-card:hover { transform: translateY(-4px); }
.project-card.p1:hover { border-color: rgba(200,245,66,0.35); box-shadow: 0 8px 32px rgba(200,245,66,0.12); }
.project-card.p2:hover { border-color: rgba(255,140,66,0.35); box-shadow: 0 8px 32px rgba(255,140,66,0.12); }
.project-card.p3:hover { border-color: rgba(77,158,255,0.35); box-shadow: 0 8px 32px rgba(77,158,255,0.12); }

.project-icon { font-size: 1.3rem; }

.project-name {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text);
}

.project-url {
  font-size: 0.62rem;
  color: var(--muted);
  letter-spacing: 0.03em;
  transition: color 0.15s;
}
.project-card:hover .project-url { color: var(--cyan); }

/* EXPERIENCE */
.exp-item {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 20px 22px;
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 4px 20px;
  align-items: start;
  transition: border-color 0.2s, background 0.2s;
  animation: rise 0.6s cubic-bezier(.16,1,.3,1) both;
  margin-bottom: 8px;
}
.exp-item:nth-child(1) { animation-delay: 0.10s; }
.exp-item:nth-child(2) { animation-delay: 0.18s; }
.exp-item:nth-child(3) { animation-delay: 0.26s; }
.exp-item:nth-child(4) { animation-delay: 0.34s; }
.exp-item:hover { background: var(--faint); border-color: var(--border-hi); }

.exp-role {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text);
  grid-column: 1;
}

.exp-company {
  font-size: 0.72rem;
  color: var(--cyan);
  grid-column: 1;
  margin-top: 2px;
}

.exp-date {
  font-size: 0.62rem;
  color: var(--muted);
  grid-column: 2;
  grid-row: 1 / 3;
  white-space: nowrap;
  text-align: right;
  padding-top: 3px;
  letter-spacing: 0.04em;
}

.exp-highlights {
  grid-column: 1 / -1;
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.highlight {
  font-size: 0.74rem;
  color: #8494b0;
  line-height: 1.6;
  display: flex;
  gap: 8px;
  align-items: flex-start;
}

.highlight::before {
  content: '▸';
  color: var(--lime);
  flex-shrink: 0;
  font-size: 0.65rem;
  margin-top: 2px;
}

.highlight strong { color: var(--text); font-weight: 500; }

/* SKILLS */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
}

.skill-group {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 16px 18px;
  animation: rise 0.6s cubic-bezier(.16,1,.3,1) both;
}
.skill-group:nth-child(1) { animation-delay: 0.10s; }
.skill-group:nth-child(2) { animation-delay: 0.15s; }
.skill-group:nth-child(3) { animation-delay: 0.20s; }
.skill-group:nth-child(4) { animation-delay: 0.25s; }

.skill-group-label {
  font-size: 0.58rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 10px;
}

.pills { display: flex; flex-wrap: wrap; gap: 6px; }

.pill {
  font-size: 0.66rem;
  padding: 4px 10px;
  border-radius: 20px;
  border: 1px solid;
  font-family: 'DM Mono', monospace;
  letter-spacing: 0.03em;
  transition: transform 0.15s;
}
.pill:hover { transform: scale(1.06); }

.pill-lime   { color: var(--lime);   border-color: rgba(200,245,66,0.3);  background: rgba(200,245,66,0.07); }
.pill-cyan   { color: var(--cyan);   border-color: rgba(61,232,200,0.3);  background: rgba(61,232,200,0.07); }
.pill-orange { color: var(--orange); border-color: rgba(255,140,66,0.3);  background: rgba(255,140,66,0.07); }
.pill-rose   { color: var(--rose);   border-color: rgba(255,94,135,0.3);  background: rgba(255,94,135,0.07); }

/* EDUCATION */
.edu-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 10px;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 18px 22px;
  animation: rise 0.6s 0.1s cubic-bezier(.16,1,.3,1) both;
}

.edu-name {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 0.92rem;
  font-weight: 600;
  color: var(--text);
}
.edu-detail {
  font-size: 0.7rem;
  color: var(--muted);
  margin-top: 3px;
}
.edu-year {
  font-size: 0.62rem;
  color: var(--lime);
  letter-spacing: 0.1em;
  white-space: nowrap;
}

/* FOOTER */
.footer {
  margin-top: 60px;
  padding-top: 24px;
  border-top: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
  animation: rise 0.6s 0.3s cubic-bezier(.16,1,.3,1) both;
}

.footer-left {
  font-size: 0.65rem;
  color: var(--muted);
  letter-spacing: 0.08em;
}
.footer-left span { color: var(--lime); }

.footer-btn {
  font-family: 'Bricolage Grotesque', sans-serif;
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  color: var(--bg);
  background: var(--lime);
  border: none;
  border-radius: 6px;
  padding: 8px 18px;
  text-decoration: none;
  transition: opacity 0.15s, transform 0.15s;
  display: inline-flex;
  align-items: center;
  gap: 5px;
}
.footer-btn:hover { opacity: 0.85; transform: scale(1.03); }

@keyframes rise {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}

@media (max-width: 640px) {
  .projects-grid { grid-template-columns: 1fr; }
  .skills-grid   { grid-template-columns: 1fr; }
  .stats-row .stat { min-width: 90px; }
  .exp-item { grid-template-columns: 1fr; }
  .exp-date { grid-column: 1; grid-row: auto; text-align: left; }
  .header-right { align-items: flex-start; }
}
</style>
</head>
<body>
<div class="glow-tl"></div>
<div class="glow-br"></div>

<div class="page">

  <!-- HEADER -->
  <div class="header">
    <div class="header-top">
      <div class="name-block">
        <div class="eyebrow">Software Engineer</div>
        <h1>Motlalepula <span class="accent">Sello</span></h1>
        <div class="subtitle">
          <span>Full Stack</span> · Ruby on Rails · React · Next.js
        </div>
      </div>
      <div class="header-right">
        <div class="location-tag">📍 Johannesburg, South Africa</div>
        <a href="mailto:motlalepulasello5@gmail.com" class="contact-link">✉ motlalepulasello5@gmail.com</a>
      </div>
    </div>

    <div class="stats-row">
      <div class="stat">
        <div class="stat-num lime">6+</div>
        <div class="stat-label">SaaS Products Shipped</div>
      </div>
      <div class="stat">
        <div class="stat-num cyan">300+</div>
        <div class="stat-label">Organic Sign-ups</div>
      </div>
      <div class="stat">
        <div class="stat-num orange">93%</div>
        <div class="stat-label">Customer Satisfaction</div>
      </div>
      <div class="stat">
        <div class="stat-num rose">4★</div>
        <div class="stat-label">Avg. Product Rating</div>
      </div>
      <div class="stat">
        <div class="stat-num lime" style="font-size:1.3rem">3+ yrs</div>
        <div class="stat-label">Industry Experience</div>
      </div>
    </div>
  </div>

  <!-- LIVE PROJECTS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">Live Projects</div>
      <div class="section-line"></div>
    </div>
    <div class="projects-grid">
      <a href="https://quollie.com" target="_blank" rel="noopener" class="project-card p1">
        <div class="project-icon">🤖</div>
        <div class="project-name">Quollie AI</div>
        <div class="project-url">quollie.com</div>
      </a>
      <a href="https://bellyclock.com" target="_blank" rel="noopener" class="project-card p2">
        <div class="project-icon">🤰</div>
        <div class="project-name">Belly Clock</div>
        <div class="project-url">bellyclock.com</div>
      </a>
      <a href="https://indielaunchers.com" target="_blank" rel="noopener" class="project-card p3">
        <div class="project-icon">🚀</div>
        <div class="project-name">Indie Launchers</div>
        <div class="project-url">indielaunchers.com</div>
      </a>
    </div>
  </div>

  <!-- EXPERIENCE -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">Experience</div>
      <div class="section-line"></div>
    </div>

    <div class="exp-item">
      <div class="exp-role">Founding Full Stack Engineer</div>
      <div class="exp-company">Sello Software Solutions</div>
      <div class="exp-date">Mar 2024 — Present</div>
      <div class="exp-highlights">
        <div class="highlight">Built and deployed <strong>6 SaaS products</strong> achieving 300+ organic sign-ups with a 4-star avg. rating.</div>
        <div class="highlight">Designed scalable <strong>REST APIs</strong> and full-stack apps with <strong>React, Next.js & PostgreSQL</strong>.</div>
        <div class="highlight">Reduced downtime by <strong>20%</strong> through cross-layer debugging across frontend, backend, and database.</div>
        <div class="highlight">Built <strong>marketing automation</strong> workflows — lead capture, email campaigns, and analytics dashboards.</div>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-role">Ruby on Rails Engineer</div>
      <div class="exp-company">Kodeco</div>
      <div class="exp-date">Mar 2023 — Sep 2023</div>
      <div class="exp-highlights">
        <div class="highlight">Implemented bug fixes across production using <strong>Linux, Docker, PgAdmin, SCSS & Rails MVC</strong>.</div>
        <div class="highlight">Developed enterprise features including <strong>custom learning paths and assignments</strong>.</div>
        <div class="highlight">Integrated new components improving end-user productivity by <strong>5%</strong>.</div>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-role">Customer Success Engineer</div>
      <div class="exp-company">Kodeco</div>
      <div class="exp-date">Sep 2022 — Mar 2023</div>
      <div class="exp-highlights">
        <div class="highlight">Achieved <strong>93% monthly customer satisfaction</strong> resolving technical inquiries end-to-end.</div>
        <div class="highlight">Executed front-end coding changes from design specs, improving <strong>functionality and aesthetics</strong>.</div>
        <div class="highlight">Led QA and project planning in <strong>Jira</strong>, ensuring quality standards and timely delivery.</div>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-role">Customer Experience Specialist</div>
      <div class="exp-company">Kodeco</div>
      <div class="exp-date">Mar 2022 — Sep 2022</div>
      <div class="exp-highlights">
        <div class="highlight">Resolved ~<strong>100 daily customer requests</strong> via email and chat, consistently earning 5-star ratings.</div>
        <div class="highlight">Documented member issues in <strong>HubSpot</strong> to surface patterns and inform product decisions.</div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">Skills</div>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-group">
        <div class="skill-group-label">Frontend</div>
        <div class="pills">
          <span class="pill pill-lime">JavaScript</span>
          <span class="pill pill-lime">TypeScript</span>
          <span class="pill pill-lime">React</span>
          <span class="pill pill-lime">Next.js</span>
          <span class="pill pill-lime">HTML5</span>
          <span class="pill pill-lime">CSS</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Backend & Data</div>
        <div class="pills">
          <span class="pill pill-cyan">Ruby on Rails</span>
          <span class="pill pill-cyan">Node.js</span>
          <span class="pill pill-cyan">REST APIs</span>
          <span class="pill pill-cyan">PostgreSQL</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Tooling & DevOps</div>
        <div class="pills">
          <span class="pill pill-orange">Docker</span>
          <span class="pill pill-orange">Linux</span>
          <span class="pill pill-orange">PgAdmin</span>
          <span class="pill pill-orange">Git</span>
          <span class="pill pill-orange">Jira</span>
          <span class="pill pill-orange">HubSpot</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Quality & Growth</div>
        <div class="pills">
          <span class="pill pill-rose">Test Automation</span>
          <span class="pill pill-rose">Unit Testing</span>
          <span class="pill pill-rose">Debugging</span>
          <span class="pill pill-rose">Email Campaigns</span>
          <span class="pill pill-rose">Analytics</span>
        </div>
      </div>
    </div>
  </div>

  <!-- EDUCATION -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">Education</div>
      <div class="section-line"></div>
    </div>
    <div class="edu-row">
      <div>
        <div class="edu-name">The Odin Project</div>
        <div class="edu-detail">Full Stack JavaScript · Web Development</div>
      </div>
      <div class="edu-year">2020 — 2025</div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-left">
      open to opportunities · <span>@Motlakz</span> · Johannesburg, ZA
    </div>
    <a class="footer-btn" href="mailto:motlalepulasello5@gmail.com">✉ Get in Touch</a>
  </div>

</div>
</body>
</html>
