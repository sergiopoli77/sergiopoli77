<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sergio Poli — LLM Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
  :root{
    --bg:#020812;
    --surface:#080f1e;
    --surface2:#0c1628;
    --border:#1a2d4a;
    --accent:#00d4ff;
    --accent2:#7b61ff;
    --accent3:#00ff9d;
    --text:#e8f4ff;
    --muted:#4a6a8a;
    --glow:rgba(0,212,255,0.15);
    --glow2:rgba(123,97,255,0.12);
  }
  html{scroll-behavior:smooth}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Syne',sans-serif;
    font-size:16px;
    line-height:1.7;
    overflow-x:hidden;
  }

  /* GRID BG */
  body::before{
    content:'';
    position:fixed;inset:0;
    background-image:
      linear-gradient(rgba(0,212,255,0.04) 1px,transparent 1px),
      linear-gradient(90deg,rgba(0,212,255,0.04) 1px,transparent 1px);
    background-size:40px 40px;
    pointer-events:none;z-index:0;
  }

  .wrapper{max-width:860px;margin:0 auto;padding:60px 24px 100px;position:relative;z-index:1}

  /* HERO */
  .hero{text-align:center;padding:80px 0 60px;position:relative}
  .hero-orb{
    position:absolute;top:-40px;left:50%;transform:translateX(-50%);
    width:400px;height:400px;
    background:radial-gradient(circle,rgba(0,212,255,0.12) 0%,rgba(123,97,255,0.08) 40%,transparent 70%);
    border-radius:50%;pointer-events:none;animation:pulse 4s ease-in-out infinite;
  }
  @keyframes pulse{0%,100%{transform:translateX(-50%) scale(1);opacity:1}50%{transform:translateX(-50%) scale(1.08);opacity:0.7}}

  .badge{
    display:inline-flex;align-items:center;gap:8px;
    border:1px solid var(--accent);
    color:var(--accent);font-family:'Space Mono',monospace;
    font-size:12px;padding:5px 14px;border-radius:2px;
    letter-spacing:0.1em;margin-bottom:28px;
    box-shadow:0 0 12px rgba(0,212,255,0.2);
    animation:fadeUp 0.6s ease both;
  }
  .badge-dot{width:6px;height:6px;border-radius:50%;background:var(--accent);animation:blink 1.5s step-end infinite}
  @keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

  .hero h1{
    font-size:clamp(40px,8vw,72px);
    font-weight:800;
    letter-spacing:-0.03em;
    line-height:1.05;
    animation:fadeUp 0.7s ease 0.1s both;
  }
  .hero h1 span{
    background:linear-gradient(135deg,var(--accent) 0%,var(--accent2) 60%,var(--accent3) 100%);
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  }
  .hero-sub{
    font-family:'Space Mono',monospace;
    color:var(--muted);font-size:14px;
    margin-top:16px;letter-spacing:0.05em;
    animation:fadeUp 0.7s ease 0.2s both;
  }
  .hero-desc{
    max-width:480px;margin:24px auto 0;
    color:#7a9ab8;font-size:15px;line-height:1.8;
    animation:fadeUp 0.7s ease 0.3s both;
  }

  @keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}

  /* STATS ROW */
  .stats{
    display:grid;grid-template-columns:repeat(3,1fr);gap:1px;
    border:1px solid var(--border);margin:48px 0;
    animation:fadeUp 0.7s ease 0.4s both;
  }
  .stat{
    padding:24px;text-align:center;background:var(--surface);
    position:relative;overflow:hidden;
  }
  .stat::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,var(--glow),transparent);opacity:0;transition:opacity 0.3s}
  .stat:hover::before{opacity:1}
  .stat-num{font-size:32px;font-weight:800;color:var(--accent);font-family:'Space Mono',monospace;display:block}
  .stat-label{font-size:11px;color:var(--muted);letter-spacing:0.1em;text-transform:uppercase;margin-top:4px}

  /* SECTION */
  .section{margin:64px 0}
  .section-header{
    display:flex;align-items:center;gap:12px;margin-bottom:32px;
  }
  .section-line{flex:1;height:1px;background:linear-gradient(to right,var(--border),transparent)}
  .section-label{
    font-family:'Space Mono',monospace;font-size:11px;
    color:var(--accent);letter-spacing:0.15em;text-transform:uppercase;
    white-space:nowrap;
  }

  /* SKILL PILLS */
  .skills-grid{display:flex;flex-wrap:wrap;gap:8px}
  .pill{
    padding:7px 14px;border:1px solid var(--border);
    font-family:'Space Mono',monospace;font-size:12px;
    color:var(--muted);border-radius:2px;
    transition:all 0.2s;cursor:default;
    position:relative;overflow:hidden;
  }
  .pill::before{content:'';position:absolute;inset:0;background:var(--glow);opacity:0;transition:opacity 0.2s}
  .pill:hover{border-color:var(--accent);color:var(--accent);transform:translateY(-2px);box-shadow:0 4px 16px rgba(0,212,255,0.15)}
  .pill:hover::before{opacity:1}
  .pill.hi{border-color:rgba(123,97,255,0.4);color:#9b85ff}
  .pill.hi:hover{border-color:var(--accent2);color:var(--accent2);box-shadow:0 4px 16px rgba(123,97,255,0.2)}
  .pill.hi::before{background:var(--glow2)}

  /* PROJECT CARDS */
  .projects{display:grid;gap:1px;border:1px solid var(--border)}
  .proj-card{
    background:var(--surface);padding:28px 32px;
    position:relative;overflow:hidden;
    transition:background 0.3s;
    cursor:default;
  }
  .proj-card::before{
    content:'';position:absolute;left:0;top:0;bottom:0;width:3px;
    background:linear-gradient(to bottom,var(--accent),var(--accent2));
    transform:scaleY(0);transform-origin:top;
    transition:transform 0.3s;
  }
  .proj-card:hover{background:var(--surface2)}
  .proj-card:hover::before{transform:scaleY(1)}
  .proj-card.featured::before{transform:scaleY(1)}
  .proj-card.featured{background:var(--surface2)}
  .proj-tag{
    font-family:'Space Mono',monospace;font-size:10px;
    letter-spacing:0.12em;text-transform:uppercase;
    margin-bottom:10px;display:inline-block;
  }
  .proj-tag.sig{color:var(--accent3)}
  .proj-tag.std{color:var(--muted)}
  .proj-title{font-size:18px;font-weight:700;margin-bottom:8px;letter-spacing:-0.01em}
  .proj-desc{color:#5a7a96;font-size:14px;line-height:1.7}
  .proj-features{
    display:flex;flex-wrap:wrap;gap:6px;margin-top:14px;
  }
  .feat-tag{
    font-family:'Space Mono',monospace;font-size:10px;
    padding:3px 8px;border-radius:1px;
    background:rgba(0,212,255,0.07);
    border:1px solid rgba(0,212,255,0.15);
    color:rgba(0,212,255,0.7);
  }

  /* CONNECT */
  .connect-row{display:flex;gap:12px;flex-wrap:wrap}
  .connect-btn{
    display:inline-flex;align-items:center;gap:8px;
    padding:10px 20px;border:1px solid var(--border);
    font-family:'Space Mono',monospace;font-size:12px;
    color:var(--muted);text-decoration:none;border-radius:2px;
    transition:all 0.25s;letter-spacing:0.05em;
    position:relative;overflow:hidden;
  }
  .connect-btn::before{content:'';position:absolute;inset:0;opacity:0;transition:opacity 0.25s}
  .connect-btn.discord::before{background:rgba(88,101,242,0.12)}
  .connect-btn.insta::before{background:rgba(228,64,95,0.10)}
  .connect-btn:hover{transform:translateY(-2px)}
  .connect-btn.discord:hover{border-color:#5865f2;color:#8b99ff;box-shadow:0 4px 16px rgba(88,101,242,0.2)}
  .connect-btn.discord:hover::before{opacity:1}
  .connect-btn.insta:hover{border-color:#e4405f;color:#f07;box-shadow:0 4px 16px rgba(228,64,95,0.2)}
  .connect-btn.insta:hover::before{opacity:1}
  .connect-icon{font-size:15px}

  /* QUOTE */
  .quote{
    border-left:2px solid var(--border);
    padding:20px 28px;margin:56px 0 0;
    color:var(--muted);font-size:14px;font-style:italic;
    position:relative;
  }
  .quote::before{
    content:'"';position:absolute;top:-10px;left:20px;
    font-size:60px;color:var(--border);font-style:normal;
    font-weight:800;line-height:1;
  }

  /* FOOTER */
  .footer{
    text-align:center;margin-top:80px;
    font-family:'Space Mono',monospace;font-size:11px;
    color:var(--muted);letter-spacing:0.1em;
  }
  .footer span{color:var(--accent)}

  /* 3D CARD TILT */
  .tilt-zone{
    transform-style:preserve-3d;perspective:1000px;
  }

  /* TERMINAL LINE */
  .terminal-line{
    font-family:'Space Mono',monospace;font-size:12px;
    color:var(--accent3);margin-bottom:4px;
    animation:typeIn 1.5s steps(40) both;
    white-space:nowrap;overflow:hidden;
  }
  @keyframes typeIn{from{width:0}to{width:100%}}

  /* SCROLL REVEAL */
  .reveal{opacity:0;transform:translateY(24px);transition:opacity 0.6s ease,transform 0.6s ease}
  .reveal.visible{opacity:1;transform:none}

  @media(max-width:600px){
    .stats{grid-template-columns:1fr}
    .proj-card{padding:20px}
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-orb"></div>
    <div class="badge"><span class="badge-dot"></span>AVAILABLE FOR PROJECTS</div>
    <h1>Sergio <span>Poli</span></h1>
    <p class="hero-sub">// LLM_DEVELOPER &nbsp;·&nbsp; AI_APPLICATIONS &nbsp;·&nbsp; FULLSTACK</p>
    <p class="hero-desc">Building intelligent systems with Large Language Models, RAG pipelines, and automation workflows that solve real-world problems.</p>
  </section>

  <!-- TERMINAL -->
  <div style="background:var(--surface);border:1px solid var(--border);padding:20px 24px;margin-bottom:64px" class="reveal">
    <div style="display:flex;gap:6px;margin-bottom:14px">
      <div style="width:10px;height:10px;border-radius:50%;background:#ff5f56"></div>
      <div style="width:10px;height:10px;border-radius:50%;background:#ffbd2e"></div>
      <div style="width:10px;height:10px;border-radius:50%;background:#27c93f"></div>
    </div>
    <div class="terminal-line">$ whoami</div>
    <div style="font-family:'Space Mono',monospace;font-size:13px;color:#4a6a8a;margin-top:2px">→ Sergio Poli / LLM Developer / Building AI that works</div>
    <div class="terminal-line" style="margin-top:14px;animation-delay:0.4s">$ skills --list</div>
    <div style="font-family:'Space Mono',monospace;font-size:13px;color:#4a6a8a;margin-top:2px">→ RAG · LangChain · OpenAI API · WhatsApp Gateway · React · Node · PostgreSQL</div>
    <div class="terminal-line" style="margin-top:14px;animation-delay:0.8s">$ status</div>
    <div style="font-family:'Space Mono',monospace;font-size:13px;color:var(--accent3);margin-top:2px">→ <span style="animation:blink 1.5s step-end infinite;display:inline-block">BUILDING</span>... AI-powered solutions for real-world problems</div>
  </div>

  <!-- STATS -->
  <div class="stats reveal">
    <div class="stat"><span class="stat-num">6+</span><div class="stat-label">Projects Shipped</div></div>
    <div class="stat"><span class="stat-num">3</span><div class="stat-label">AI Integrations</div></div>
    <div class="stat"><span class="stat-num">∞</span><div class="stat-label">Building Streak</div></div>
  </div>

  <!-- TECH STACK -->
  <section class="section reveal">
    <div class="section-header">
      <div class="section-line"></div>
      <div class="section-label">// tech_stack</div>
    </div>
    <div style="margin-bottom:16px;font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);letter-spacing:0.1em">AI / LLM</div>
    <div class="skills-grid" style="margin-bottom:20px">
      <div class="pill">OpenAI API</div>
      <div class="pill">LangChain</div>
      <div class="pill">RAG Systems</div>
      <div class="pill">Vector DBs</div>
      <div class="pill">LLM Integration</div>
    </div>
    <div style="margin-bottom:16px;margin-top:20px;font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);letter-spacing:0.1em">FULLSTACK</div>
    <div class="skills-grid" style="margin-bottom:20px">
      <div class="pill hi">React.js</div>
      <div class="pill hi">Node.js</div>
      <div class="pill hi">Express.js</div>
      <div class="pill hi">PostgreSQL</div>
      <div class="pill hi">Firebase</div>
      <div class="pill hi">MongoDB</div>
    </div>
    <div style="margin-bottom:16px;margin-top:20px;font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);letter-spacing:0.1em">INTEGRATIONS</div>
    <div class="skills-grid">
      <div class="pill">WhatsApp Gateway</div>
      <div class="pill">REST APIs</div>
      <div class="pill">Payment Gateway</div>
      <div class="pill">Automation Workflows</div>
    </div>
  </section>

  <!-- FLAGSHIP -->
  <section class="section reveal">
    <div class="section-header">
      <div class="section-line"></div>
      <div class="section-label">// flagship_project</div>
    </div>
    <div class="projects">
      <div class="proj-card featured">
        <div class="proj-tag sig">⚡ SIGNATURE PROJECT</div>
        <div class="proj-title">AI-Powered Citizen Complaint System</div>
        <div class="proj-desc">A digital assistant that lets citizens submit complaints via WhatsApp with AI-powered automated responses — helping public institutions manage community issues faster and smarter.</div>
        <div class="proj-features">
          <span class="feat-tag">LLM Integration</span>
          <span class="feat-tag">WhatsApp Gateway</span>
          <span class="feat-tag">LangChain</span>
          <span class="feat-tag">Express.js</span>
          <span class="feat-tag">Scalable Architecture</span>
        </div>
      </div>
    </div>
  </section>

  <!-- OTHER PROJECTS -->
  <section class="section reveal">
    <div class="section-header">
      <div class="section-line"></div>
      <div class="section-label">// other_projects</div>
    </div>
    <div class="projects">
      <div class="proj-card">
        <div class="proj-tag std">RAG · DOCUMENT AI</div>
        <div class="proj-title">AI Document Assistant</div>
        <div class="proj-desc">Upload documents, ask questions. RAG-based intelligent assistant that understands and answers queries from user-provided files.</div>
        <div class="proj-features">
          <span class="feat-tag">RAG</span>
          <span class="feat-tag">Document Processing</span>
          <span class="feat-tag">Q&amp;A Interface</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-tag std">HEALTH · CHATBOT</div>
        <div class="proj-title">TBC WhatsApp Chatbot</div>
        <div class="proj-desc">LLM-powered health information chatbot providing accessible tuberculosis guidance through WhatsApp for community health outreach.</div>
        <div class="proj-features">
          <span class="feat-tag">LLM</span>
          <span class="feat-tag">WhatsApp</span>
          <span class="feat-tag">Health Tech</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-tag std">BUSINESS · WEB</div>
        <div class="proj-title">POS System</div>
        <div class="proj-desc">Full web-based point-of-sale platform with transaction management, product tracking, inventory control, and sales reporting.</div>
        <div class="proj-features">
          <span class="feat-tag">Transactions</span>
          <span class="feat-tag">Inventory</span>
          <span class="feat-tag">Reporting</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-tag std">AGRITECH · MANAGEMENT</div>
        <div class="proj-title">Agriculture Management System</div>
        <div class="proj-desc">Digital platform for managing crop tracking, harvest monitoring, fertilizer records, and agricultural inventory for farm productivity.</div>
        <div class="proj-features">
          <span class="feat-tag">Crop Tracking</span>
          <span class="feat-tag">Harvest Monitor</span>
          <span class="feat-tag">Agri Inventory</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-tag std">HR · ATTENDANCE</div>
        <div class="proj-title">Employee Attendance System</div>
        <div class="proj-desc">Selfie-based attendance check-in system with an admin monitoring dashboard and real-time attendance records.</div>
        <div class="proj-features">
          <span class="feat-tag">Selfie Verification</span>
          <span class="feat-tag">Admin Dashboard</span>
          <span class="feat-tag">Real-time Records</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-tag std">TOURISM · WEB</div>
        <div class="proj-title">À L'Aise by the Lake</div>
        <div class="proj-desc">Restaurant and tourism experience platform with booking for sailing, cycling, pottery, painting, and prewedding events — plus full payment gateway integration.</div>
        <div class="proj-features">
          <span class="feat-tag">Booking System</span>
          <span class="feat-tag">Payment Gateway</span>
          <span class="feat-tag">Gallery</span>
        </div>
      </div>
    </div>
  </section>

  <!-- CONNECT -->
  <section class="section reveal">
    <div class="section-header">
      <div class="section-line"></div>
      <div class="section-label">// connect</div>
    </div>
    <div class="connect-row">
      <a href="https://discord.com/users/581871647066423297" class="connect-btn discord" target="_blank">
        <span class="connect-icon">🎮</span>Discord — sergiopoli
      </a>
      <a href="https://instagram.com/sergiooyp" class="connect-btn insta" target="_blank">
        <span class="connect-icon">📷</span>Instagram — @sergiooyp
      </a>
    </div>
  </section>

  <!-- QUOTE -->
  <div class="quote reveal">
    "Technology is best when it brings people together."
    <div style="margin-top:10px;font-style:normal;font-size:12px;font-family:'Space Mono',monospace;color:#2a4a66">— Matt Mullenweg</div>
  </div>

  <div class="footer reveal">
    <p>Built by <span>Sergio Poli</span> &nbsp;·&nbsp; LLM Developer &nbsp;·&nbsp; github.com/sergiopoli77</p>
  </div>

</div>

<script>
// Scroll reveal
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => { if(e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
}, { threshold: 0.1 });
revealEls.forEach(el => io.observe(el));

// 3D tilt on project cards
document.querySelectorAll('.proj-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const r = card.getBoundingClientRect();
    const x = e.clientX - r.left;
    const y = e.clientY - r.top;
    const cx = r.width / 2;
    const cy = r.height / 2;
    const rotX = ((y - cy) / cy) * -4;
    const rotY = ((x - cx) / cx) * 4;
    card.style.transform = `perspective(600px) rotateX(${rotX}deg) rotateY(${rotY}deg) translateZ(4px)`;
    card.style.transition = 'transform 0.05s ease';
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = '';
    card.style.transition = 'transform 0.4s ease, background 0.3s';
  });
});

// Pill tilt
document.querySelectorAll('.pill').forEach(pill => {
  pill.addEventListener('mouseenter', () => {
    pill.style.transform = 'translateY(-3px) rotateX(8deg)';
  });
  pill.addEventListener('mouseleave', () => {
    pill.style.transform = '';
  });
});

// Stat counter animation
function animateCount(el, target, suffix='') {
  let start = 0;
  const dur = 1200;
  const step = (t) => {
    const progress = Math.min(t / dur, 1);
    const ease = 1 - Math.pow(1 - progress, 3);
    const val = Math.round(ease * target);
    el.textContent = val + suffix;
    if (progress < 1) requestAnimationFrame(t2 => step(t2 - rAFStart));
  };
  let rAFStart;
  const observer = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting) {
      rAFStart = performance.now();
      requestAnimationFrame(() => step(0));
      observer.disconnect();
    }
  });
  observer.observe(el);
}

const statNums = document.querySelectorAll('.stat-num');
if (statNums[0]) animateCount(statNums[0], 6, '+');
if (statNums[1]) animateCount(statNums[1], 3, '');

// Mouse parallax on hero orb
document.addEventListener('mousemove', e => {
  const orb = document.querySelector('.hero-orb');
  if (!orb) return;
  const cx = window.innerWidth / 2;
  const cy = window.innerHeight / 2;
  const dx = (e.clientX - cx) / cx * 16;
  const dy = (e.clientY - cy) / cy * 10;
  orb.style.transform = `translateX(calc(-50% + ${dx}px)) translateY(${dy}px)`;
});
</script>
</body>
</html>
