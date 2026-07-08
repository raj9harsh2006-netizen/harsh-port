# harsh-port <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Harsh Raj — Supply Chain &amp; Data Analytics</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0B1220;
    --panel:#101A2C;
    --panel-2:#16223A;
    --ink:#E8E3D8;
    --ink-dim:#8B95A6;
    --copper:#C97B3D;
    --teal:#5FA3A3;
    --line:#22304A;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--ink);
    font-family:'Inter',sans-serif;
    line-height:1.6;
    overflow-x:hidden;
  }
  ::selection{background:var(--copper); color:var(--bg);}

  h1,h2,h3{ font-family:'Fraunces',serif; font-weight:600; letter-spacing:-0.01em;}
  .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size:0.72rem;
    letter-spacing:0.18em;
    text-transform:uppercase;
    color:var(--copper);
    display:flex; align-items:center; gap:10px;
  }
  .eyebrow::before{ content:''; width:24px; height:1px; background:var(--copper);}

  a{color:inherit; text-decoration:none;}

  .wrap{ max-width:1080px; margin:0 auto; padding:0 32px;}

  /* NAV */
  nav{
    position:fixed; top:0; left:0; right:0; z-index:50;
    background:rgba(11,18,32,0.85); backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line);
  }
  nav .wrap{ display:flex; align-items:center; justify-content:space-between; height:64px;}
  .logo{ font-family:'Fraunces',serif; font-weight:600; font-size:1.05rem;}
  .logo span{ color:var(--copper);}
  .navlinks{ display:flex; gap:28px; font-size:0.85rem; color:var(--ink-dim);}
  .navlinks a:hover{ color:var(--ink);}

  /* HERO */
  header.hero{
    position:relative;
    min-height:100vh;
    display:flex; align-items:center;
    padding-top:64px;
    overflow:hidden;
  }
  #routeCanvas{
    position:absolute; inset:0; width:100%; height:100%;
    opacity:0.55;
  }
  .hero-inner{ position:relative; z-index:2; width:100%;}
  .hero-grid{
    display:grid; grid-template-columns: 1.4fr 1fr; gap:40px; align-items:end;
  }
  .hero h1{
    font-size:clamp(2.6rem, 6vw, 4.6rem);
    line-height:1.04;
    margin-top:18px;
  }
  .hero h1 em{ font-style:italic; color:var(--copper);}
  .hero p.lede{
    margin-top:22px;
    font-size:1.05rem;
    color:var(--ink-dim);
    max-width:46ch;
  }
  .hero-stats{
    display:flex; flex-direction:column; gap:18px;
    border-left:1px solid var(--line);
    padding-left:24px;
  }
  .stat-num{ font-family:'Fraunces',serif; font-size:2.1rem; color:var(--teal);}
  .stat-label{ font-size:0.78rem; color:var(--ink-dim); font-family:'JetBrains Mono',monospace;}
  .hero-cta{ margin-top:34px; display:flex; gap:14px; flex-wrap:wrap;}
  .btn{
    font-family:'JetBrains Mono',monospace; font-size:0.8rem;
    padding:13px 22px; border-radius:2px;
    border:1px solid var(--line);
    transition:all .2s ease;
    letter-spacing:0.03em;
  }
  .btn.primary{ background:var(--copper); color:var(--bg); border-color:var(--copper); font-weight:500;}
  .btn.primary:hover{ background:#d98c4f;}
  .btn.ghost:hover{ border-color:var(--copper); color:var(--copper);}

  /* SECTIONS */
  section{ padding:110px 0; border-bottom:1px solid var(--line); position:relative;}
  .section-head{ display:flex; justify-content:space-between; align-items:flex-end; margin-bottom:56px; flex-wrap:wrap; gap:16px;}
  .section-head h2{ font-size:clamp(1.8rem,3.4vw,2.5rem); margin-top:10px;}

  /* SUMMARY */
  .summary-text{ font-size:1.15rem; color:var(--ink-dim); max-width:72ch;}
  .summary-text strong{ color:var(--ink); font-weight:500;}

  /* SKILLS - route diagram style */
  .skills-rail{
    display:grid; grid-template-columns:repeat(4,1fr); gap:1px;
    background:var(--line); border:1px solid var(--line);
  }
  .skill-node{ background:var(--panel); padding:26px 20px; min-height:120px; display:flex; flex-direction:column; justify-content:space-between;}
  .skill-node .tag{ font-family:'JetBrains Mono',monospace; font-size:0.68rem; color:var(--ink-dim); letter-spacing:0.05em;}
  .skill-node .name{ font-family:'Fraunces',serif; font-size:1.05rem; margin-top:10px;}
  .skill-node:hover{ background:var(--panel-2);}

  /* PROJECTS */
  .project{
    display:grid; grid-template-columns: 90px 1fr; gap:28px;
    padding:32px 0; border-top:1px solid var(--line);
  }
  .project:first-of-type{ border-top:none;}
  .project .pnum{ font-family:'JetBrains Mono',monospace; color:var(--ink-dim); font-size:0.85rem; padding-top:6px;}
  .project h3{ font-size:1.5rem;}
  .project .tools{ font-family:'JetBrains Mono',monospace; font-size:0.72rem; color:var(--teal); margin:8px 0 16px; letter-spacing:0.04em;}
  .project ul{ list-style:none; display:flex; flex-direction:column; gap:10px;}
  .project li{ position:relative; padding-left:20px; color:var(--ink-dim); font-size:0.95rem;}
  .project li::before{ content:'—'; position:absolute; left:0; color:var(--copper);}

  /* EXPERIENCE - timeline */
  .timeline{ position:relative; padding-left:28px;}
  .timeline::before{ content:''; position:absolute; left:5px; top:6px; bottom:6px; width:1px; background:var(--line);}
  .tl-item{ position:relative; padding-bottom:46px;}
  .tl-item:last-child{ padding-bottom:0;}
  .tl-item::before{ content:''; position:absolute; left:-28px; top:6px; width:9px; height:9px; border-radius:50%; background:var(--bg); border:2px solid var(--copper);}
  .tl-head{ display:flex; justify-content:space-between; flex-wrap:wrap; gap:8px; align-items:baseline;}
  .tl-role{ font-family:'Fraunces',serif; font-size:1.25rem;}
  .tl-date{ font-family:'JetBrains Mono',monospace; font-size:0.75rem; color:var(--ink-dim);}
  .tl-org{ color:var(--copper); font-size:0.9rem; margin-top:4px; font-style:italic;}
  .tl-item ul{ margin-top:14px; list-style:none; display:flex; flex-direction:column; gap:8px;}
  .tl-item li{ position:relative; padding-left:18px; color:var(--ink-dim); font-size:0.92rem;}
  .tl-item li::before{ content:'·'; position:absolute; left:0; color:var(--teal); font-size:1.4rem; line-height:0.7;}

  /* CERTS + EDU grid */
  .twocol{ display:grid; grid-template-columns:1fr 1fr; gap:48px;}
  .mini-head{ font-family:'JetBrains Mono',monospace; font-size:0.75rem; letter-spacing:0.1em; color:var(--ink-dim); text-transform:uppercase; margin-bottom:18px;}
  .cert-list, .edu-list{ list-style:none; display:flex; flex-direction:column; gap:16px;}
  .cert-list li{ font-size:0.92rem; color:var(--ink-dim); padding-bottom:16px; border-bottom:1px solid var(--line);}
  .cert-list li strong{ color:var(--ink); font-weight:500; display:block; margin-bottom:3px;}
  .edu-item{ padding-bottom:16px; border-bottom:1px solid var(--line);}
  .edu-item .deg{ font-family:'Fraunces',serif; font-size:1.05rem;}
  .edu-item .sch{ font-size:0.85rem; color:var(--ink-dim); margin-top:3px;}
  .edu-item .yr{ font-family:'JetBrains Mono',monospace; font-size:0.72rem; color:var(--teal); margin-top:5px;}

  /* COMPETENCIES chips */
  .chips{ display:flex; flex-wrap:wrap; gap:10px; margin-top:18px;}
  .chip{ font-family:'JetBrains Mono',monospace; font-size:0.78rem; padding:9px 16px; border:1px solid var(--line); border-radius:20px; color:var(--ink-dim);}

  /* FOOTER / CONTACT */
  footer{ padding:90px 0 50px; text-align:center;}
  footer h2{ font-size:clamp(2rem,4vw,3rem); margin-bottom:24px;}
  .contact-row{ display:flex; justify-content:center; gap:30px; flex-wrap:wrap; margin-top:30px; font-family:'JetBrains Mono',monospace; font-size:0.85rem; color:var(--ink-dim);}
  .contact-row a:hover{ color:var(--copper);}
  .foot-note{ margin-top:60px; font-size:0.75rem; color:var(--ink-dim); font-family:'JetBrains Mono',monospace;}

  @media (max-width:760px){
    .hero-grid{ grid-template-columns:1fr;}
    .hero-stats{ border-left:none; border-top:1px solid var(--line); padding-left:0; padding-top:20px; flex-direction:row; flex-wrap:wrap;}
    .skills-rail{ grid-template-columns:repeat(2,1fr);}
    .twocol{ grid-template-columns:1fr;}
    .project{ grid-template-columns:1fr;}
    .navlinks{ display:none;}
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation:none !important; transition:none !important;}
  }

  :focus-visible{ outline:2px solid var(--copper); outline-offset:3px;}
</style>
</head>
<body>

<nav>
  <div class="wrap">
    <div class="logo">HARSH<span>·</span>RAJ</div>
    <div class="navlinks">
      <a href="#work">Projects</a>
      <a href="#experience">Experience</a>
      <a href="#credentials">Credentials</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<header class="hero">
  <canvas id="routeCanvas"></canvas>
  <div class="wrap hero-inner">
    <div class="hero-grid">
      <div>
        <p class="eyebrow">Supply Chain · Data Analytics · BBA Finance, 2026</p>
        <h1>Tracing the path <em>from raw data</em><br>to operational decisions.</h1>
        <p class="lede">I build dashboards that turn inventory, vendor, and logistics data into decisions — Power BI, Tableau, and Excel, applied to real supply chain problems.</p>
        <div class="hero-cta">
          <a class="btn primary" href="#work">View projects</a>
          <a class="btn ghost" href="mailto:raj9harsh2006@gmail.com">Get in touch</a>
        </div>
      </div>
      <div class="hero-stats">
        <div>
          <div class="stat-num">03</div>
          <div class="stat-label">END-TO-END DASHBOARDS SHIPPED</div>
        </div>
        <div>
          <div class="stat-num">06</div>
          <div class="stat-label">INDUSTRY CERTIFICATIONS</div>
        </div>
        <div>
          <div class="stat-num">700+</div>
          <div class="stat-label">RECORDS ANALYSED ACROSS PROJECTS</div>
        </div>
      </div>
    </div>
  </div>
</header>

<section id="summary">
  <div class="wrap">
    <p class="eyebrow">Profile</p>
    <h2 style="margin-top:14px; max-width:18ch;">Built for the messy middle of the supply chain.</h2>
    <p class="summary-text" style="margin-top:28px;">
      I'm a <strong>Supply Chain &amp; Data Analytics</strong> professional finishing a BBA in Finance at Uttaranchal University, with hands-on experience in <strong>inventory analysis, vendor reconciliation, and procurement reporting</strong>. I've built three end-to-end dashboards in Power BI and Tableau tracking demand forecasting, logistics KPIs, and supplier performance, and I'm fluent in Excel — VLOOKUP, HLOOKUP, INDEX-MATCH, Pivot Tables — for day-to-day supply chain data operations. Certified in SCM, Digital Marketing, and Data Analytics through Deloitte, TCS, and Google, I'm looking to drive operational efficiency at a growth-oriented supply chain organisation.
    </p>
  </div>
</section>

<section id="skills">
  <div class="wrap">
    <div class="section-head">
      <div>
        <p class="eyebrow">Toolkit</p>
        <h2>Technical skills</h2>
      </div>
    </div>
    <div class="skills-rail">
      <div class="skill-node"><span class="tag">BI / VIZ</span><span class="name">Power BI</span></div>
      <div class="skill-node"><span class="tag">BI / VIZ</span><span class="name">Tableau</span></div>
      <div class="skill-node"><span class="tag">SPREADSHEET</span><span class="name">Excel (Advanced)</span></div>
      <div class="skill-node"><span class="tag">SPREADSHEET</span><span class="name">VLOOKUP · HLOOKUP · INDEX-MATCH</span></div>
      <div class="skill-node"><span class="tag">ANALYSIS</span><span class="name">Pivot Tables</span></div>
      <div class="skill-node"><span class="tag">ANALYSIS</span><span class="name">Data Visualization</span></div>
      <div class="skill-node"><span class="tag">ANALYSIS</span><span class="name">Dashboard Development</span></div>
      <div class="skill-node"><span class="tag">REPORTING</span><span class="name">Business Analytics</span></div>
      <div class="skill-node"><span class="tag">REPORTING</span><span class="name">Data Analysis &amp; Reporting</span></div>
      <div class="skill-node"><span class="tag">OPERATIONS</span><span class="name">Tally</span></div>
      <div class="skill-node"><span class="tag">OPERATIONS</span><span class="name">MS Office Suite</span></div>
    </div>
  </div>
</section>

<section id="work">
  <div class="wrap">
    <div class="section-head">
      <div>
        <p class="eyebrow">Selected Work</p>
        <h2>Academic projects</h2>
      </div>
    </div>

    <div class="project">
      <div class="pnum">01</div>
      <div>
        <h3>HR Analytics Dashboard</h3>
        <div class="tools">POWER BI · DAX · WORKFORCE ANALYTICS</div>
        <ul>
          <li>Reduced HR reporting effort by 50% by developing a Power BI dashboard tracking attrition, workforce distribution, and performance KPIs across 200+ employee records.</li>
          <li>Surfaced 3 high-impact attrition risk segments via department-level drill-down analysis using slicers and dynamic filters.</li>
          <li>Generated 5 strategic HR recommendations by translating raw workforce data into actionable insights using DAX measures.</li>
        </ul>
      </div>
    </div>

    <div class="project">
      <div class="pnum">02</div>
      <div>
        <h3>Supply Chain Analysis Project</h3>
        <div class="tools">EXCEL · INDEX-MATCH · POWER BI</div>
        <ul>
          <li>Identified 4 critical supply chain bottlenecks through root-cause analysis of 500+ inventory and logistics records.</li>
          <li>Proposed a vendor consolidation strategy projected to cut process redundancies by an estimated 18%, by benchmarking supplier lead times and procurement cycles.</li>
          <li>Communicated findings to 3 stakeholder groups via a Power BI report visualising 3PL logistics costs, inventory turnover, and demand variance.</li>
        </ul>
      </div>
    </div>

    <div class="project">
      <div class="pnum">03</div>
      <div>
        <h3>Sales Performance Dashboard</h3>
        <div class="tools">TABLEAU · POWER BI · KPI REPORTING</div>
        <ul>
          <li>Delivered an end-to-end sales KPI report spanning 12 months of data, adopted across 2 simulated business units.</li>
          <li>Uncovered 3 high-growth revenue segments by visualising quarterly sales variance and regional demand patterns.</li>
          <li>Enabled 2 simulated procurement decisions by converting dashboard KPIs into sourcing and restocking recommendations.</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<section id="experience">
  <div class="wrap">
    <div class="section-head">
      <div>
        <p class="eyebrow">Track Record</p>
        <h2>Internships &amp; work experience</h2>
      </div>
    </div>

    <div class="timeline">
      <div class="tl-item">
        <div class="tl-head">
          <span class="tl-role">Data Operations &amp; Audit Assistant</span>
          <span class="tl-date">JUL — AUG 2025</span>
        </div>
        <div class="tl-org">Sanjeev Kumar and Associates — CA Firm</div>
        <ul>
          <li>Improved audit documentation accuracy by 30% by building structured Excel reconciliation templates with VLOOKUP to cross-match vendor payment records.</li>
          <li>Accelerated financial reporting by 20% by building Tableau dashboards visualising supplier invoice trends and logistics cost variances.</li>
          <li>Ensured 100% compliance across 3 audit cycles by reconciling procurement and vendor payment data using Tally and structured validation protocols.</li>
        </ul>
      </div>

      <div class="tl-item">
        <div class="tl-head">
          <span class="tl-role">Data Analytics Job Simulation</span>
          <span class="tl-date">JUN 2025</span>
        </div>
        <div class="tl-org">Deloitte — Virtual Internship</div>
        <ul>
          <li>Delivered 4 business insight recommendations by completing a real-world simulation focused on supply chain performance and demand trend analysis.</li>
          <li>Improved data accuracy by 25% by applying INDEX-MATCH and Pivot Table techniques to cleanse multi-source logistics datasets.</li>
        </ul>
      </div>

      <div class="tl-item">
        <div class="tl-head">
          <span class="tl-role">Marketing Manager — Financial Institution Field</span>
          <span class="tl-date">JUN — JUL 2024</span>
        </div>
        <div class="tl-org">Fintech Shine Pvt. Ltd.</div>
        <ul>
          <li>Grew campaign reach by 35% by designing and executing targeted marketing initiatives for fintech products.</li>
          <li>Reduced campaign reporting time by 40% by building Excel-based tracking dashboards with Pivot Tables.</li>
          <li>Delivered campaigns on time for 100% of deadlines by coordinating cross-functional vendor and partner teams.</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<section id="credentials">
  <div class="wrap">
    <div class="section-head">
      <div>
        <p class="eyebrow">Foundation</p>
        <h2>Credentials &amp; education</h2>
      </div>
    </div>
    <div class="twocol">
      <div>
        <p class="mini-head">Certifications</p>
        <ul class="cert-list">
          <li><strong>Supply Chain Management Certification</strong>NPTEL / Coursera</li>
          <li><strong>Power BI Certification</strong>Microsoft</li>
          <li><strong>Tableau Certification</strong>Salesforce / Tableau</li>
          <li><strong>Data Analytics Job Simulation</strong>Deloitte — June 2025</li>
          <li><strong>TCS iON Career Edge — Young Professional</strong>Tata Consultancy Services — March 2024</li>
          <li><strong>Fundamentals of Digital Marketing</strong>Google Digital Garage — May 2023</li>
        </ul>
      </div>
      <div>
        <p class="mini-head">Education</p>
        <div class="edu-list">
          <div class="edu-item">
            <div class="deg">Bachelor of Business Administration — Finance</div>
            <div class="sch">Uttaranchal University, Dehradun, India</div>
            <div class="yr">EXPECTED 2026</div>
          </div>
          <div class="edu-item">
            <div class="deg">Senior Secondary — Science (PCM)</div>
            <div class="sch">St. Xavier's Jr/Sr School, Muzaffarpur</div>
            <div class="yr">2021 — 2023</div>
          </div>
          <div class="edu-item">
            <div class="deg">Secondary — Science</div>
            <div class="sch">St. Xavier's Jr/Sr School, Muzaffarpur</div>
            <div class="yr">2020 — 2021</div>
          </div>
        </div>
        <p class="mini-head" style="margin-top:32px;">Key competencies</p>
        <div class="chips">
          <span class="chip">Supply Chain Analysis</span>
          <span class="chip">Demand Forecasting</span>
          <span class="chip">Vendor &amp; Procurement Data</span>
          <span class="chip">Inventory Management</span>
          <span class="chip">KPI &amp; Dashboard Reporting</span>
          <span class="chip">ERP Fundamentals</span>
        </div>
      </div>
    </div>
  </div>
</section>

<footer id="contact">
  <div class="wrap">
    <p class="eyebrow" style="justify-content:center;">Let's talk</p>
    <h2>Open to supply chain &amp; analytics roles.</h2>
    <p class="summary-text" style="margin:0 auto; text-align:center;">Based in Muzaffarpur, Bihar — available for internships, full-time roles, and project collaboration.</p>
    <div class="contact-row">
      <a href="mailto:raj9harsh2006@gmail.com">raj9harsh2006@gmail.com</a>
      <a href="tel:+917992219005">+91 79922 19005</a>
      <a href="https://linkedin.com/in/harsh-sharma-a0b5622b5" target="_blank" rel="noopener">linkedin.com/in/harsh-sharma</a>
    </div>
    <p class="foot-note">HARSH RAJ — BUILT FROM DATA, FOR DATA · 2026</p>
  </div>
</footer>

<script>
  // Route/network animation in hero — nodes connected like a logistics route map
  const canvas = document.getElementById('routeCanvas');
  const ctx = canvas.getContext('2d');
  let w, h, nodes;
  const reduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  function resize(){
    w = canvas.width = canvas.offsetWidth;
    h = canvas.height = canvas.offsetHeight;
  }

  function initNodes(){
    nodes = [];
    const count = w < 700 ? 14 : 26;
    for(let i=0;i<count;i++){
      nodes.push({
        x: Math.random()*w,
        y: Math.random()*h,
        vx: (Math.random()-0.5)*0.18,
        vy: (Math.random()-0.5)*0.18,
        r: Math.random()*1.6+1
      });
    }
  }

  function draw(){
    ctx.clearRect(0,0,w,h);
    for(let i=0;i<nodes.length;i++){
      const n = nodes[i];
      if(!reduced){
        n.x += n.vx; n.y += n.vy;
        if(n.x<0||n.x>w) n.vx*=-1;
        if(n.y<0||n.y>h) n.vy*=-1;
      }
      for(let j=i+1;j<nodes.length;j++){
        const m = nodes[j];
        const dx = n.x-m.x, dy = n.y-m.y;
        const dist = Math.sqrt(dx*dx+dy*dy);
        if(dist < 180){
          ctx.strokeStyle = `rgba(201,123,61,${(1-dist/180)*0.22})`;
          ctx.lineWidth = 1;
          ctx.beginPath();
          ctx.moveTo(n.x,n.y);
          ctx.lineTo(m.x,m.y);
          ctx.stroke();
        }
      }
    }
    for(const n of nodes){
      ctx.fillStyle = 'rgba(95,163,163,0.55)';
      ctx.beginPath();
      ctx.arc(n.x,n.y,n.r,0,Math.PI*2);
      ctx.fill();
    }
    if(!reduced) requestAnimationFrame(draw);
  }

  window.addEventListener('resize', ()=>{ resize(); initNodes(); });
  resize(); initNodes(); draw();
</script>

</body>
</html>
