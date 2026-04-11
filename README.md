<!DOCTYPE html>
<html>
<head>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    background: #0D1117;
    color: #E6EDF3;
    font-family: 'JetBrains Mono', 'Fira Code', monospace;
    padding: 0;
  }

  /* HEADER */
  .header {
    background: linear-gradient(135deg, #0D1117 0%, #0A1628 50%, #0D2137 100%);
    border-bottom: 1px solid #00D4FF33;
    padding: 40px 32px 32px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute;
    top: -60px; left: 50%;
    transform: translateX(-50%);
    width: 400px; height: 200px;
    background: radial-gradient(ellipse, #00D4FF18 0%, transparent 70%);
    pointer-events: none;
  }
  .header-name {
    font-size: 42px;
    font-weight: 700;
    color: #fff;
    letter-spacing: -1px;
    line-height: 1;
  }
  .header-name span { color: #00D4FF; }
  .header-sub {
    font-size: 13px;
    color: #8B949E;
    margin-top: 8px;
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  .header-badges {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-top: 20px;
    flex-wrap: wrap;
  }
  .badge {
    background: #161B22;
    border: 1px solid #30363D;
    border-radius: 20px;
    padding: 5px 14px;
    font-size: 11px;
    color: #8B949E;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  .badge.cyan { border-color: #00D4FF44; color: #00D4FF; background: #00D4FF0D; }
  .badge.green { border-color: #2EA04344; color: #3FB950; background: #2EA04310; }
  .badge.orange { border-color: #F7881444; color: #F78814; background: #F7881410; }

  /* MAIN LAYOUT */
  .main {
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 0;
    min-height: 600px;
  }

  /* SIDEBAR */
  .sidebar {
    background: #0D1117;
    border-right: 1px solid #21262D;
    padding: 24px 20px;
  }
  .sidebar-section { margin-bottom: 28px; }
  .sidebar-label {
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: #00D4FF;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .sidebar-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #00D4FF22;
  }
  .info-row {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 5px 0;
    font-size: 12px;
    color: #8B949E;
    border-bottom: 1px solid #21262D;
  }
  .info-row:last-child { border-bottom: none; }
  .info-icon { color: #00D4FF; width: 14px; text-align: center; font-size: 11px; }
  .info-val { color: #E6EDF3; }

  /* SKILL BARS */
  .skill-item { margin-bottom: 10px; }
  .skill-header {
    display: flex;
    justify-content: space-between;
    font-size: 11px;
    color: #8B949E;
    margin-bottom: 4px;
  }
  .skill-pct { color: #00D4FF; font-weight: 700; }
  .skill-bar-bg {
    height: 3px;
    background: #21262D;
    border-radius: 2px;
    overflow: hidden;
  }
  .skill-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, #00D4FF, #0080FF);
    border-radius: 2px;
    transition: width 1s ease;
  }
  .skill-bar-fill.php { background: linear-gradient(90deg, #777BB4, #9999CC); }
  .skill-bar-fill.mysql { background: linear-gradient(90deg, #4479A1, #5599BB); }
  .skill-bar-fill.docker { background: linear-gradient(90deg, #2496ED, #44AAFF); }
  .skill-bar-fill.python { background: linear-gradient(90deg, #3776AB, #55AACC); }

  /* SOCIAL */
  .social-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6px;
  }
  .social-btn {
    background: #161B22;
    border: 1px solid #30363D;
    border-radius: 6px;
    padding: 7px 10px;
    font-size: 10px;
    color: #8B949E;
    text-align: center;
    cursor: pointer;
    transition: all 0.15s;
  }
  .social-btn:hover { border-color: #00D4FF55; color: #00D4FF; background: #00D4FF0A; }

  /* CONTENT */
  .content { background: #0D1117; padding: 24px; }

  /* ABOUT BLOCK */
  .code-block {
    background: #161B22;
    border: 1px solid #21262D;
    border-left: 3px solid #00D4FF;
    border-radius: 0 8px 8px 0;
    padding: 16px 18px;
    font-size: 12px;
    line-height: 1.9;
    margin-bottom: 24px;
  }
  .code-key { color: #79C0FF; }
  .code-str { color: #A5D6FF; }
  .code-arr { color: #FF7B72; }
  .code-val { color: #E6EDF3; }
  .code-comment { color: #8B949E; font-style: italic; }
  .code-muted { color: #8B949E; }

  /* STATS CARDS */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 24px;
  }
  .stat-card {
    background: #161B22;
    border: 1px solid #21262D;
    border-radius: 8px;
    padding: 14px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .stat-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: #00D4FF;
  }
  .stat-card.orange::after { background: #F78814; }
  .stat-card.green::after { background: #3FB950; }
  .stat-num {
    font-size: 26px;
    font-weight: 700;
    color: #E6EDF3;
    line-height: 1;
  }
  .stat-label {
    font-size: 10px;
    color: #8B949E;
    margin-top: 4px;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  /* PROJECTS */
  .section-title {
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: #00D4FF;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #21262D;
  }
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 24px;
  }
  .project-card {
    background: #161B22;
    border: 1px solid #21262D;
    border-radius: 8px;
    padding: 14px;
    transition: border-color 0.15s;
  }
  .project-card:hover { border-color: #00D4FF44; }
  .project-name {
    font-size: 13px;
    color: #79C0FF;
    font-weight: 600;
    margin-bottom: 4px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .project-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: #00D4FF;
    flex-shrink: 0;
  }
  .project-dot.php { background: #777BB4; }
  .project-dot.python { background: #3776AB; }
  .project-desc {
    font-size: 11px;
    color: #8B949E;
    line-height: 1.5;
  }
  .project-tag {
    display: inline-block;
    background: #21262D;
    border-radius: 4px;
    padding: 2px 7px;
    font-size: 10px;
    color: #8B949E;
    margin-top: 6px;
  }

  /* CONTRIBUTION */
  .contrib-section { margin-bottom: 0; }
  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 2px;
  }
  .contrib-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    background: #161B22;
  }
  .c1 { background: #003B1E; }
  .c2 { background: #00622F; }
  .c3 { background: #00A84F; }
  .c4 { background: #00D4FF; }

  /* FOOTER */
  .footer {
    background: #0D1117;
    border-top: 1px solid #21262D;
    padding: 16px 32px;
    text-align: center;
    font-size: 11px;
    color: #8B949E;
  }
  .footer span { color: #00D4FF; }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header">
  <div class="header-name">Cristian <span>Trujillo</span></div>
  <div class="header-sub">Backend Developer &nbsp;·&nbsp; ADSO @ SENA &nbsp;·&nbsp; Pitalito, Colombia</div>
  <div class="header-badges">
    <div class="badge cyan">⚡ NestJS</div>
    <div class="badge cyan">🐳 Docker</div>
    <div class="badge green">✓ Open to work</div>
    <div class="badge orange">17 y/o</div>
    <div class="badge">🇨🇴 Colombia</div>
  </div>
</div>

<!-- MAIN -->
<div class="main">

  <!-- SIDEBAR -->
  <div class="sidebar">

    <div class="sidebar-section">
      <div class="sidebar-label">Info</div>
      <div class="info-row"><span class="info-icon">◎</span><span class="info-val">Cristian Danilo Trujillo</span></div>
      <div class="info-row"><span class="info-icon">◉</span><span>Pitalito, Huila · 🇨🇴</span></div>
      <div class="info-row"><span class="info-icon">◈</span><span>ADSO Student @ SENA</span></div>
      <div class="info-row"><span class="info-icon">→</span><span>Backend Developer</span></div>
      <div class="info-row"><span class="info-icon">✦</span><span>17 years old</span></div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-label">Skills</div>
      <div class="skill-item">
        <div class="skill-header"><span>NestJS</span><span class="skill-pct">75%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:75%"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header"><span>PHP</span><span class="skill-pct">80%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill php" style="width:80%"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header"><span>MySQL</span><span class="skill-pct">70%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill mysql" style="width:70%"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header"><span>Docker</span><span class="skill-pct">60%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill docker" style="width:60%"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header"><span>HTML/CSS</span><span class="skill-pct">85%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill" style="width:85%"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header"><span>Python</span><span class="skill-pct">40%</span></div>
        <div class="skill-bar-bg"><div class="skill-bar-fill python" style="width:40%"></div></div>
      </div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-label">Connect</div>
      <div class="social-grid">
        <div class="social-btn">LinkedIn</div>
        <div class="social-btn">Instagram</div>
        <div class="social-btn">Facebook</div>
        <div class="social-btn">Gmail</div>
      </div>
    </div>

  </div>

  <!-- CONTENT -->
  <div class="content">

    <!-- ABOUT -->
    <div class="section-title">◈ About</div>
    <div class="code-block">
      <span class="code-key">const</span> <span class="code-val">cristian</span> <span class="code-muted">= {</span><br>
      &nbsp;&nbsp;<span class="code-key">name</span><span class="code-muted">:</span> <span class="code-str">"Cristian Danilo Trujillo"</span><span class="code-muted">,</span><br>
      &nbsp;&nbsp;<span class="code-key">role</span><span class="code-muted">:</span> <span class="code-str">"Backend Developer"</span><span class="code-muted">,</span><br>
      &nbsp;&nbsp;<span class="code-key">stack</span><span class="code-muted">:</span> <span class="code-arr">["NestJS", "PHP", "MySQL", "Docker"]</span><span class="code-muted">,</span><br>
      &nbsp;&nbsp;<span class="code-key">goal</span><span class="code-muted">:</span> <span class="code-str">"Land my first dev job"</span><span class="code-muted">,</span><br>
      &nbsp;&nbsp;<span class="code-comment">// "The code is creativity shaped by syntax."</span><br>
      <span class="code-muted">}</span>
    </div>

    <!-- STATS -->
    <div class="section-title">◈ Stats</div>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num">12</div>
        <div class="stat-label">Repositories</div>
      </div>
      <div class="stat-card orange">
        <div class="stat-num">3</div>
        <div class="stat-label">Stars earned</div>
      </div>
      <div class="stat-card green">
        <div class="stat-num">3</div>
        <div class="stat-label">Followers</div>
      </div>
    </div>

    <!-- PROJECTS -->
    <div class="section-title">◈ Projects</div>
    <div class="projects-grid">
      <div class="project-card">
        <div class="project-name"><div class="project-dot"></div>StorePrim</div>
        <div class="project-desc">Personal web store project — frontend</div>
        <span class="project-tag">HTML</span>
      </div>
      <div class="project-card">
        <div class="project-name"><div class="project-dot"></div>PrimeStore</div>
        <div class="project-desc">Improved version of StorePrim — v2</div>
        <span class="project-tag">HTML</span>
      </div>
      <div class="project-card">
        <div class="project-name"><div class="project-dot php"></div>ADSO5853</div>
        <div class="project-desc">Programming class work @ SENA</div>
        <span class="project-tag">PHP</span>
      </div>
      <div class="project-card">
        <div class="project-name"><div class="project-dot python"></div>mi_primer_repo</div>
        <div class="project-desc">First repo — Git class @ SENA</div>
        <span class="project-tag">Python</span>
      </div>
    </div>

    <!-- CONTRIBUTIONS -->
    <div class="section-title">◈ Activity</div>
    <div class="contrib-section">
      <div class="contrib-grid" id="grid"></div>
    </div>

  </div>
</div>

<!-- FOOTER -->
<div class="footer">
  <span>"The code is not just logic — it's creativity shaped by syntax."</span>
  &nbsp;·&nbsp; Designed by Cristian Trujillo &nbsp;·&nbsp; Pitalito, Colombia 🇨🇴
</div>

<script>
const grid = document.getElementById('grid');
const pattern = [0,0,1,0,0,1,2,0,1,0,2,1,0,0,3,1,2,0,0,1,0,2,3,1,0,2,0,1,0,0,2,1,3,0,1,2,0,0,1,0,2,1,0,3,1,0,2,0,1,0,2,1,3,1,0,2,1,0,0,1,2,0,3,1,0,2,1,0,0,1,2,3,0,1,0,2,0,1,0,2,1,0,1,2,3,1,0,0,1,2,0,1,3,1,2,0,0,1,0,2,1,3,0,1,2,0,0,1,0,2,3,1,0,0,2,1,0,3,1,2,0,1,0,0,2,1,0,1,2,3,0,1,2,0,1,0,2,1,0,0,1,2,3,1,0,2,0,1,3,1,2,0,0,1,2,1,0,0,3,1,2,0,1,0,2,1,0,0,3,1,2,0,0,1,2,3,0,1,2,0,1,0,0,2,1,3,1,0,2,0,1,2,0,1,0,2,3,1,0,2,0,0,1,2,3,1,0,0,1,0,2,1,0,3,1,2,0,1,0,2,3,1,0,0,1,2,0,1,0,2,1,0,3,1,2,0,1,0,0,2,1,3,0,1,2,0,1,0,2,1,0,0,1,2,3,1,2,0,1,0,2,1,0,0,3,1,2,0,1,2,0,3];
const classes = ['','c1','c2','c3','c4'];
for(let i=0;i<52*7;i++){
  const cell=document.createElement('div');
  cell.className='contrib-cell '+(classes[pattern[i%pattern.length]]||'');
  grid.appendChild(cell);
}
</script>
</body>
</html>
