<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@1,300;1,400&display=swap" rel="stylesheet">
<style>
:root{
  --ferrari-red:#E60000;
  --solid-black:#050505;
  --off-white:#F5F5F5;
  --light-blue:#130fd0;
  --light-green:#00ff00;
  --card-bg:#111;
  --card-bg2:#151515;
  --border:#333;
  --mono:'Courier New',Courier,monospace;
  --f1-font:'Segoe UI',Roboto,Helvetica,Arial,sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box}
body{
  background:linear-gradient(135deg,#050505 0%,#1a1a1a 100%);
  color:var(--off-white);font-family:var(--f1-font);
  min-height:100vh;overflow-x:hidden;
  background-attachment:fixed;
}
/* grid bg like portfolio */
body::before{
  content:'';position:fixed;inset:0;
  background-image:linear-gradient(rgba(230,0,0,0.04) 1px,transparent 1px),linear-gradient(90deg,rgba(230,0,0,0.04) 1px,transparent 1px);
  background-size:50px 50px;pointer-events:none;z-index:0;
}

/* NAV — exact portfolio match */
nav{
  display:flex;justify-content:space-between;align-items:center;
  padding:15px 8%;
  background:rgba(0,0,0,0.95);
  backdrop-filter:blur(15px);
  position:sticky;top:0;z-index:1000;
  border-bottom:2px solid var(--ferrari-red);
}
.logo{font-weight:900;font-size:1.4rem;letter-spacing:3px;color:var(--off-white)}
.logo span{color:var(--ferrari-red)}
.nav-socials{display:flex;gap:0;align-items:center}
.nav-social{
  padding:0 12px;font-size:1.1rem;
  text-decoration:none;color:#fff;
  transition:transform 0.3s,filter 0.3s,color 0.3s;
  display:flex;align-items:center;gap:7px;
  font-family:var(--mono);font-size:11px;letter-spacing:1px;
}
.nav-social:hover{
  transform:scale(1.2) translateY(-3px);
  filter:drop-shadow(0 0 8px var(--ferrari-red));
  color:var(--off-white)!important;
}
.nav-social.gmail:hover{filter:drop-shadow(0 0 8px #EA4335);color:#EA4335!important}
.nav-social.linkedin:hover{filter:drop-shadow(0 0 8px #0A66C2);color:#0A66C2!important}
.nav-social.leetcode:hover{filter:drop-shadow(0 0 8px #FFA116);color:#FFA116!important}
.nav-social.instagram:hover{filter:drop-shadow(0 0 8px #E1306C);color:#E1306C!important}
.nav-icon{width:18px;height:18px;flex-shrink:0}

/* scroll progress bar like portfolio */
#progress-bar{
  position:fixed;top:0;left:0;height:3px;width:0%;
  background:linear-gradient(90deg,var(--ferrari-red),#ff1e43);
  z-index:10001;transition:width 0.1s ease;
}

/* HERO */
.hero{
  min-height:90vh;display:flex;flex-direction:column;
  justify-content:center;padding:0 10%;
  position:relative;z-index:1;
}
.typewriter-tag{
  color:var(--ferrari-red);font-weight:bold;
  letter-spacing:3px;font-size:0.9rem;
  font-family:var(--mono);margin-bottom:20px;
  opacity:0;animation:fadeInUp 0.8s 0.2s cubic-bezier(0.2,0.8,0.2,1) forwards;
}
.name-container{position:relative;display:inline-block;margin:20px 0}
.racing-accent{
  position:absolute;top:0;left:0;width:0%;height:100%;
  background:var(--ferrari-red);z-index:1;
  transition:width 0.4s cubic-bezier(0.23,1,0.32,1);
  transform:skewX(-15deg);
}
.name-container:hover .racing-accent{width:108%}
.name-container:hover .highlight-name{color:#fff}
.highlight-name{
  font-size:clamp(2.5rem,7vw,5.5rem);
  color:var(--ferrari-red);text-transform:uppercase;
  font-weight:900;position:relative;z-index:5;
  padding:10px 15px;
  transition:color 0.3s ease;display:inline-block;
  opacity:0;animation:fadeInUp 0.9s 0.4s cubic-bezier(0.2,0.8,0.2,1) forwards;
}
/* Italic serif overlay on name — the F1 float */
.name-serif-float{
  font-family:'Cormorant Garamond',serif;
  font-style:italic;font-weight:300;
  font-size:clamp(1rem,2vw,1.4rem);
  color:rgba(230,0,0,0.5);letter-spacing:0.1em;
  position:absolute;bottom:-1.2rem;right:15px;z-index:6;
  opacity:0;animation:fadeInUp 0.8s 0.9s ease forwards;
}
.hero-desc{
  max-width:700px;line-height:1.8;font-size:1.05rem;opacity:0.9;
  opacity:0;animation:fadeInUp 0.8s 0.7s cubic-bezier(0.2,0.8,0.2,1) forwards;
  margin-top:1rem;
}
.hero-chips{
  display:flex;flex-wrap:wrap;gap:10px;margin-top:2rem;
  opacity:0;animation:fadeInUp 0.8s 1s ease forwards;
}
.hero-chip{
  font-family:var(--mono);font-size:11px;letter-spacing:2px;
  border:1px solid #333;padding:6px 16px;color:var(--off-white);
  text-transform:uppercase;transition:all 0.3s;cursor:default;
}
.hero-chip:hover{border-color:var(--ferrari-red);color:var(--ferrari-red);box-shadow:0 0 15px rgba(230,0,0,0.3)}

/* SECTION HEADERS — exact match */
.section-wrap{padding:80px 10%;position:relative;z-index:1}
.section-wrap.dark-section{background:rgba(0,0,0,0.4)}
h2{
  font-size:2rem;font-weight:900;letter-spacing:3px;
  text-transform:uppercase;color:var(--off-white);
  border-left:6px solid var(--ferrari-red);padding-left:20px;
  margin-bottom:8px;
}
.sub-header{
  font-family:var(--mono);font-size:0.75rem;
  letter-spacing:3px;color:var(--ferrari-red);
  text-transform:uppercase;display:block;margin-bottom:40px;
  padding-left:26px;
}

/* CARDS — exact portfolio style */
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:20px}
.card{
  background:var(--card-bg);
  border:1px solid var(--border);
  border-left:6px solid var(--ferrari-red);
  padding:1.5rem;
  transition:transform 0.4s cubic-bezier(0.175,0.885,0.32,1.275),box-shadow 0.5s ease,border-left-width 0.3s ease;
  position:relative;overflow:hidden;
}
.card::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(90deg,transparent,rgba(230,0,0,0.06),transparent);
  opacity:0;transition:opacity 0.3s;
}
.card:hover{
  transform:translateY(-8px) scale(1.01);
  box-shadow:0 25px 50px rgba(230,0,0,0.2);
  border-left-width:10px;
}
.card:hover::after{opacity:1}
.card h3,.card h4{font-size:1rem;font-weight:900;letter-spacing:2px;text-transform:uppercase;margin-bottom:10px}
.card h4{color:var(--ferrari-red)}
.card p{font-size:0.9rem;opacity:0.8;line-height:1.7}
.card .card-tag{
  font-family:var(--mono);font-size:9px;letter-spacing:2px;
  color:var(--ferrari-red);text-transform:uppercase;margin-bottom:8px;display:block;
}

/* SKILL LOGOS */
.skill-logo-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(100px,1fr));gap:12px;margin-top:16px}
.skill-logo{
  display:flex;flex-direction:column;align-items:center;gap:8px;
  background:var(--card-bg2);border:1px solid var(--border);
  border-left:3px solid var(--ferrari-red);
  padding:14px 8px;
  transition:all 0.3s;cursor:default;
}
.skill-logo:hover{
  border-color:var(--ferrari-red);transform:translateY(-4px);
  box-shadow:0 0 20px rgba(230,0,0,0.3);
}
.skill-logo svg,.skill-logo img{width:28px;height:28px}
.skill-logo span{font-family:var(--mono);font-size:9px;letter-spacing:1px;text-transform:uppercase;color:#888;text-align:center}
.skill-logo:hover span{color:var(--off-white)}

/* CAT LABEL */
.cat-row{font-family:var(--mono);font-size:10px;letter-spacing:3px;color:var(--ferrari-red);text-transform:uppercase;margin:24px 0 12px;border-left:3px solid var(--ferrari-red);padding-left:10px}

/* TELEMETRY — exact portfolio */
.telemetry-dashboard{display:grid;grid-template-columns:280px 1fr;gap:30px;margin-top:0}
.telemetry-sidebar{display:flex;flex-direction:column;gap:12px}
.stat-box{
  background:#0a0a0a;border:1px solid var(--border);
  font-family:var(--mono);padding:14px 18px;
  border-left:3px solid var(--ferrari-red);
}
.stat-box .label{font-size:9px;letter-spacing:3px;color:var(--ferrari-red);display:block;margin-bottom:6px}
.stat-box .value{font-size:13px;font-weight:bold;color:var(--off-white);letter-spacing:2px}
.stat-box .value.green-glow{
  color:var(--light-green);
  text-shadow:0 0 5px #00ff00;
  animation:pulse-green 3s infinite;
}
@keyframes pulse-green{
  0%,100%{text-shadow:0 0 5px #00ff00}
  50%{text-shadow:0 0 15px #00ff00,0 0 25px #00ff00}
}
.counter-row{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:4px}
.counter-box{background:#1a1a1a;border:1px solid #222;padding:12px 8px;text-align:center}
.counter-num{font-family:var(--mono);font-size:1.5rem;font-weight:900;color:var(--ferrari-red);display:block}
.counter-lbl{font-family:var(--mono);font-size:8px;letter-spacing:1px;color:#666;text-transform:uppercase}

/* VOLUNTEERING */
.vol-card{display:grid;grid-template-columns:4px 1fr;overflow:hidden;border:1px solid var(--border);margin-bottom:16px}
.vol-stripe{background:var(--ferrari-red)}
.vol-body{background:var(--card-bg);padding:1.5rem}

/* CERT GRID */
.cert-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:16px}

/* REVEAL */
.reveal{opacity:0;transform:translateY(30px);transition:opacity 0.7s ease,transform 0.7s ease}
.reveal.active{opacity:1;transform:none}

/* FOOTER */
footer{
  padding:40px 10%;background:#000;text-align:center;
  font-size:0.8rem;color:#555;border-top:1px solid #222;
  font-family:var(--mono);letter-spacing:1px;
}
footer a{color:#555;text-decoration:none;transition:color 0.3s}
footer a:hover{color:var(--ferrari-red)}

@keyframes fadeInUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}

/* responsive */
@media(max-width:720px){
  .telemetry-dashboard{grid-template-columns:1fr}
  .nav-socials .nav-social span{display:none}
  .hero{padding:0 5%}
  .section-wrap{padding:60px 5%}
}
</style>
</head>
<body>

<div id="progress-bar"></div>

<!-- NAV — exact portfolio structure -->
<nav>
  <div class="logo">AAYUSHMAN<span>.</span></div>
  <div class="nav-socials">
    <a href="mailto:aayushman.pratap.singh23@gmail.com" class="nav-social gmail">
      <svg class="nav-icon" viewBox="0 0 24 24" fill="none">
        <path d="M4 6h16v12H4z" stroke="#EA4335" stroke-width="1.5" stroke-linejoin="round"/>
        <path d="M4 6l8 7 8-7" stroke="#EA4335" stroke-width="1.5" stroke-linejoin="round"/>
      </svg>
      <span>GMAIL</span>
    </a>
    <a href="https://www.linkedin.com/in/aayushman-singh-63a975228/" target="_blank" class="nav-social linkedin">
      <svg class="nav-icon" viewBox="0 0 24 24" fill="none">
        <rect x="3" y="3" width="18" height="18" rx="3" stroke="#0A66C2" stroke-width="1.5"/>
        <path d="M8 10v7M8 7v.5M12 17v-4c0-1.5 2-3 4-1v5M16 13v4" stroke="#0A66C2" stroke-width="1.5" stroke-linecap="round"/>
      </svg>
      <span>LINKEDIN</span>
    </a>
    <a href="https://github.com/dismantled1" target="_blank" class="nav-social">
      <svg class="nav-icon" viewBox="0 0 24 24" fill="currentColor">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M12 2C6.48 2 2 6.58 2 12.2c0 4.5 2.87 8.32 6.84 9.68.5.1.68-.22.68-.49v-1.7C6.73 20.3 6.14 18 6.14 18c-.46-1.16-1.11-1.47-1.11-1.47-.91-.63.07-.62.07-.62 1 .07 1.53 1.05 1.53 1.05.89 1.56 2.34 1.1 2.91.84.09-.65.35-1.1.63-1.35-2.22-.25-4.56-1.13-4.56-5.02 0-1.11.39-2.01 1.03-2.72-.1-.26-.45-1.29.1-2.68 0 0 .84-.27 2.75 1.04A9.4 9.4 0 0 1 12 8.87c.85 0 1.7.12 2.5.34 1.9-1.31 2.74-1.04 2.74-1.04.55 1.39.2 2.42.1 2.68.64.71 1.03 1.61 1.03 2.72 0 3.9-2.34 4.76-4.57 5.01.36.31.68.93.68 1.87v2.77c0 .27.18.6.69.5A10.21 10.21 0 0 0 22 12.2C22 6.58 17.52 2 12 2z"/>
      </svg>
      <span>GITHUB</span>
    </a>
    <a href="https://leetcode.com/u/aayushmanpratapsingh/" target="_blank" class="nav-social leetcode">
      <svg class="nav-icon" viewBox="0 0 24 24" fill="none">
        <path d="M13.5 3L7 12.5h6L11 21l8-11h-6l.5-7z" stroke="#FFA116" stroke-width="1.5" stroke-linejoin="round"/>
      </svg>
      <span>LEETCODE</span>
    </a>
    <a href="https://www.instagram.com/aayushmanpsingh/" target="_blank" class="nav-social instagram">
      <svg class="nav-icon" viewBox="0 0 24 24" fill="none">
        <rect x="3" y="3" width="18" height="18" rx="5" stroke="#E1306C" stroke-width="1.5"/>
        <circle cx="12" cy="12" r="4" stroke="#E1306C" stroke-width="1.5"/>
        <circle cx="17" cy="7" r="1" fill="#E1306C"/>
      </svg>
      <span>INSTAGRAM</span>
    </a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="typewriter-tag">// ACADEMIC SPEC: THIRD YEAR UNDERGRADUATE · CSE · SRM IST 2027</div>
  <div class="name-container">
    <div class="racing-accent"></div>
    <h1 class="highlight-name">Aayushman Pratap Singh</h1>
    <div class="name-serif-float">— engineered for speed</div>
  </div>
  <p class="hero-desc">
    Computer Science Engineer specializing in high-performance systems.
    From <b>Python-based Data Analysis</b> to <b>SAP S/4HANA ERP Fundamentals</b>,
    I build digital engines that are <b>engineered for reliability and speed</b>.
  </p>
  <div class="hero-chips">
    <div class="hero-chip">Data Science</div>
    <div class="hero-chip">Full Stack Dev</div>
    <div class="hero-chip">ERP · SAP S/4HANA</div>
    <div class="hero-chip">DSA · OOP</div>
    <div class="hero-chip">Ghaziabad, India</div>
  </div>
</section>

<!-- STATS / TELEMETRY -->
<div class="section-wrap dark-section reveal">
  <h2>PIT-STOP TELEMETRY</h2>
  <span class="sub-header">LIVE STATUS FEED</span>
  <div class="telemetry-dashboard">
    <div class="telemetry-sidebar">
      <div class="stat-box">
        <span class="label">ENGINE STATUS</span>
        <span class="value green-glow">OPTIMAL</span>
      </div>
      <div class="stat-box">
        <span class="label">LOCATION</span>
        <span class="value">GHAZIABAD, INDIA</span>
      </div>
      <div class="stat-box">
        <span class="label">UNIVERSITY</span>
        <span class="value">SRM IST · 2027</span>
      </div>
      <div class="stat-box">
        <span class="label">LATENCY</span>
        <span class="value">12MS</span>
      </div>
      <div class="counter-row">
        <div class="counter-box">
          <span class="counter-num" data-target="2">0</span>
          <span class="counter-lbl">Yrs. Coding</span>
        </div>
        <div class="counter-box">
          <span class="counter-num" data-target="10">0</span>
          <span class="counter-lbl">Tech Stack</span>
        </div>
        <div class="counter-box">
          <span class="counter-num" data-target="2">0</span>
          <span class="counter-lbl">Certs</span>
        </div>
      </div>
    </div>
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;align-content:start">
      <div class="card">
        <span class="card-tag">Education</span>
        <h3>B.Tech CSE</h3>
        <p>SRM Institute of Science &amp; Technology<br>Aug 2023 – May 2027<br>Ghaziabad, UP</p>
      </div>
      <div class="card">
        <span class="card-tag">Languages</span>
        <h3>English · Hindi</h3>
        <p>Professional Working Proficiency in English. Native Hindi speaker.</p>
      </div>
      <div class="card">
        <span class="card-tag">Contact Signal</span>
        <h3>Open to Work</h3>
        <p style="word-break:break-all">as7310@srmist.edu.in<br>aayushman.pratap.singh23@gmail.com</p>
      </div>
      <div class="card">
        <span class="card-tag">Race Number</span>
        <h3 style="font-size:3rem;color:var(--ferrari-red)">01</h3>
        <p>Always first out of the pit lane.</p>
      </div>
    </div>
  </div>
</div>

<!-- TECHNICAL SPECS -->
<div class="section-wrap reveal">
  <h2>TECHNICAL SPECS</h2>
  <span class="sub-header">POWER UNIT COMPONENTS</span>

  <div class="cat-row">// Languages</div>
  <div class="skill-logo-grid">
    <div class="skill-logo">
      <svg viewBox="0 0 24 24"><path d="M11.9 2C9.2 2 7 3.3 7 5v2h5v1H5C3.3 8 2 9.7 2 12s1.3 4 3 4h1v-2c0-1.7 2.2-3 5-3h4c2.2 0 4-1 4-3V5c0-1.7-2.1-3-5-3h-3.1zM9 4.5c.6 0 1 .4 1 1s-.4 1-1 1-1-.4-1-1 .4-1 1-1z" fill="#3776AB"/><path d="M12.1 22c2.7 0 4.9-1.3 4.9-3v-2h-5v-1h7c1.7 0 3-1.7 3-4s-1.3-4-3-4h-1v2c0 1.7-2.2 3-5 3H9c-2.2 0-4 1-4 3v3c0 1.7 2.1 3 5 3h2.1zM15 19.5c-.6 0-1-.4-1-1s.4-1 1-1 1 .4 1 1-.4 1-1 1z" fill="#FFD343"/></svg>
      <span>Python</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24"><path d="M8.5 17.5s-.9.5.6.7c1.9.2 2.8.2 4.9-.2 0 0 .5.3 1.2.6-4.4 1.9-10-.1-6.7-1.1zm-.7-2.8s-1 .7.5 1c1.8.2 3.2.3 5.7-.3 0 0 .4.4.9.6-5 1.5-10.6.1-7.1-1.3z" fill="#EA2D2E"/><path d="M13.2 10.5c1 1.2-.3 2.2-.3 2.2s2.5-1.3 1.4-2.9c-1.1-1.5-1.9-2.3 2.5-4.9 0 0-6.8 1.7-3.6 5.6z" fill="#EA2D2E"/><path d="M17.5 19.4s.7.6-.7.7c-2.7.2-11.2.3-13.6 0-.9-.1-.9-.8-.9-.8S4 20.5 9.5 20.3c5.8-.2 7.7-.9 8-1zM8.8 13.4s-4 .9-1.4 1.3c1.1.2 3.3.1 5.3-.1 1.7-.2 3.3-.5 3.3-.5s-.6.3-1 .5c-4.1 1.1-12 .6-9.7-.5 1.9-.9 3.5-.7 3.5-.7zm7.2 4s3-1.6 1.6-2.8c-1.1-1-2.2-1-2.2-1s.5-.1 1-.2c3.3.9 5.8 3.6-1 4.5l.6-.5z" fill="#EA2D2E"/><path d="M14 1.7S16 4 12 5.7c-3.2 1.5-1.2 2.3 0 3.2-2.8-.8-4.9-1.9-3.5-3.7C10.4 3.2 14.7 2.5 14 1.7z" fill="#EA2D2E"/></svg>
      <span>Java</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><ellipse cx="12" cy="6" rx="8" ry="3" stroke="#336791" stroke-width="1.5"/><path d="M4 6v6c0 1.7 3.6 3 8 3s8-1.3 8-3V6" stroke="#336791" stroke-width="1.5"/><path d="M4 12v6c0 1.7 3.6 3 8 3s8-1.3 8-3v-6" stroke="#336791" stroke-width="1.5"/></svg>
      <span>SQL</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="9" stroke="#A8B9CC" stroke-width="1.5"/><path d="M15 9a5 5 0 1 0 0 6" stroke="#A8B9CC" stroke-width="1.5" stroke-linecap="round"/></svg>
      <span>C</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><circle cx="10" cy="12" r="7" stroke="#00599C" stroke-width="1.5"/><path d="M13 9a5 5 0 1 0 0 6" stroke="#00599C" stroke-width="1.5" stroke-linecap="round"/><path d="M17 10v4M15 12h4M20 10v4M18 12h4" stroke="#00599C" stroke-width="1.5" stroke-linecap="round"/></svg>
      <span>C++</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24"><path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z" fill="#E34F26"/><path d="M12 20.5l5.3-1.5 1.2-14H12v15.5z" fill="#EF652A"/><path d="M12 8H8.5l.2 2.5H12V13H9l.3 3 2.7.7V19l-4.7-1.3-.3-4.7H4.5l.5 7L12 23V20.5z" fill="#fff"/><path d="M12 8h3.5l-.3 2.5H12V13h3l-.3 3-2.7.7V19l4.7-1.3.4-4.7h1.4l-.5 7L12 23V8z" fill="#ebebeb"/></svg>
      <span>HTML</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24"><path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z" fill="#264DE4"/><path d="M12 20.5l5.3-1.5 1.2-14H12v15.5z" fill="#2965F1"/><path d="M12 8H8.5l.2 2.5H12V13H9l.3 3 2.7.7V19l-4.7-1.3-.3-4.7H4.5l.5 7L12 23V8z" fill="#fff"/><path d="M12 8h3.5l-.3 2.5H12V13h3l-.3 3-2.7.7V19l4.7-1.3.4-4.7h1.4l-.5 7L12 23V8z" fill="#ebebeb"/></svg>
      <span>CSS</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24"><rect width="20" height="20" x="2" y="2" rx="2" fill="#F7DF1E"/><path d="M14.5 16.5c.4.7 1 1.2 2 1.2 1 0 1.5-.5 1.5-1.1 0-.8-.6-1-1.5-1.5l-.5-.2c-1.5-.6-2.5-1.4-2.5-3 0-1.5 1.1-2.7 3-2.7 1.3 0 2.2.5 2.8 1.5l-1.5 1c-.4-.6-.7-.8-1.3-.8s-1 .4-1 .9c0 .6.4.9 1.3 1.3l.5.2c1.7.7 2.7 1.5 2.7 3.2 0 1.8-1.4 2.8-3.3 2.8-1.8 0-3-1-3.6-2.2l1.7-.9zM7 10.1v5.4c0 1.5.7 2.2 1.7 2.2 1.1 0 1.8-.7 1.8-2.2v-5.4h2v5.4c0 2.7-1.5 4-3.8 4-2 0-3.7-1-3.7-3.9v-5.5H7z" fill="#333"/></svg>
      <span>JavaScript</span>
    </div>
  </div>

  <div class="cat-row">// Frameworks & Libraries</div>
  <div class="skill-logo-grid">
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><rect x="3" y="3" width="18" height="18" rx="3" fill="#092E20"/><path d="M12 6v12M8 7v9c0 2 1 3 3 3M15 7v5" stroke="#44B78B" stroke-width="1.5" stroke-linecap="round"/></svg>
      <span>Django</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><rect x="4" y="3" width="4" height="8" rx="2" fill="#150458"/><rect x="10" y="7" width="4" height="10" rx="2" fill="#E70488"/><rect x="16" y="3" width="4" height="8" rx="2" fill="#150458"/><rect x="4" y="13" width="4" height="8" rx="2" fill="#150458"/><rect x="16" y="13" width="4" height="8" rx="2" fill="#150458"/></svg>
      <span>Pandas</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><path d="M12 3L2 8l10 5 10-5-10-5zM2 14l10 5 10-5M2 11l10 5 10-5" stroke="#4DABCF" stroke-width="1.5" stroke-linejoin="round"/></svg>
      <span>NumPy</span>
    </div>
  </div>

  <div class="cat-row">// Tools & IDEs</div>
  <div class="skill-logo-grid">
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="currentColor"><path fill-rule="evenodd" clip-rule="evenodd" d="M12 2C6.48 2 2 6.58 2 12.2c0 4.5 2.87 8.32 6.84 9.68.5.1.68-.22.68-.49v-1.7C6.73 20.3 6.14 18 6.14 18c-.46-1.16-1.11-1.47-1.11-1.47-.91-.63.07-.62.07-.62 1 .07 1.53 1.05 1.53 1.05.89 1.56 2.34 1.1 2.91.84.09-.65.35-1.1.63-1.35-2.22-.25-4.56-1.13-4.56-5.02 0-1.11.39-2.01 1.03-2.72-.1-.26-.45-1.29.1-2.68 0 0 .84-.27 2.75 1.04A9.4 9.4 0 0 1 12 8.87c.85 0 1.7.12 2.5.34 1.9-1.31 2.74-1.04 2.74-1.04.55 1.39.2 2.42.1 2.68.64.71 1.03 1.61 1.03 2.72 0 3.9-2.34 4.76-4.57 5.01.36.31.68.93.68 1.87v2.77c0 .27.18.6.69.5A10.21 10.21 0 0 0 22 12.2C22 6.58 17.52 2 12 2z"/></svg>
      <span>GitHub</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><path d="M17 2L2 9l5 3 10-7v14L7 12l-5 3 15 7 5-2.5V4.5L17 2z" fill="#007ACC"/></svg>
      <span>VS Code</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="9" stroke="#2C2255" stroke-width="1.5"/><ellipse cx="11" cy="12" rx="6" ry="9" stroke="#F7941E" stroke-width="1.5" transform="rotate(-20 11 12)"/></svg>
      <span>Eclipse IDE</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><rect x="3" y="3" width="18" height="18" rx="2" fill="#217346"/><path d="M8 8l4 8M12 8l-4 8M14 8h4M14 12h4M14 16h4" stroke="#fff" stroke-width="1.5" stroke-linecap="round"/></svg>
      <span>Excel</span>
    </div>
    <div class="skill-logo">
      <svg viewBox="0 0 24 24" fill="none"><rect x="2" y="6" width="20" height="12" rx="3" fill="#009DDE"/><text x="12" y="15.5" font-family="sans-serif" font-size="6.5" font-weight="700" fill="white" text-anchor="middle">SAP</text></svg>
      <span>SAP S/4HANA</span>
    </div>
  </div>
</div>

<!-- RACE LOG / EXPERIENCE -->
<div class="section-wrap dark-section reveal">
  <h2>THE RACE LOG</h2>
  <span class="sub-header">CAREER TRACK RECORD</span>
  <div class="grid">
    <div class="card">
      <span class="card-tag">Sept 2024 – Jan 2026</span>
      <h3>Content Team Co-Lead</h3>
      <p><strong>Computer Society of India</strong></p>
      <ul style="margin-top:12px;padding-left:18px;font-size:0.85rem;opacity:0.8;line-height:2">
        <li>Led technical documentation for Hackstasy '25</li>
        <li>Synchronized sponsors and participants like a pit-crew chief</li>
        <li>Resolved real-time logistical crises under race-day pressure</li>
      </ul>
    </div>
    <div class="card">
      <span class="card-tag">Jan – Sept 2024</span>
      <h3>Core Member</h3>
      <p><strong>Computer Society of India</strong></p>
      <ul style="margin-top:12px;padding-left:18px;font-size:0.85rem;opacity:0.8;line-height:2">
        <li>Anchored coding events and technical flow planning</li>
        <li>Developed content for hackathon scaling operations</li>
      </ul>
    </div>
  </div>
</div>

<!-- CERTIFICATIONS -->
<div class="section-wrap reveal">
  <h2>HOMOLOGATION</h2>
  <span class="sub-header">CERTIFIED TECHNICAL COMPLIANCE</span>
  <div class="cert-grid">
    <div class="card">
      <span class="card-tag">Oct 2024 · Slayor.org · ID: 4264583661AS</span>
      <h3>CS101: Intro to Computer Science I</h3>
      <p>Java Certificate — foundational CS theory and programming fundamentals.</p>
    </div>
    <div class="card">
      <span class="card-tag">Jan 2026 · SAP University Alliances</span>
      <h3>ERP using GBI 3.30 on SAP S/4HANA</h3>
      <p>Hands-on enterprise resource planning — production, procurement & finance modules.</p>
    </div>
  </div>
</div>

<!-- PROJECT -->
<div class="section-wrap dark-section reveal">
  <h2>ON-TRACK BUILDS</h2>
  <span class="sub-header">PROJECT TELEMETRY</span>
  <div class="grid">
    <div class="card" style="border-left:6px solid var(--light-blue)">
      <span class="card-tag" style="color:var(--light-blue)">Feb 2026 · HTML · CSS · JavaScript</span>
      <h3>Fully Functional Portfolio</h3>
      <p>F1 racing-inspired portfolio with parallax scrolling, glassmorphism UI, smoke cursor particles, custom telemetry dashboard, and EmailJS contact integration. Fully responsive.</p>
      <a href="https://github.com/dismantled1" target="_blank" style="display:inline-block;margin-top:14px;font-family:var(--mono);font-size:10px;letter-spacing:2px;color:var(--light-blue);border:1px solid var(--light-blue);padding:5px 14px;text-decoration:none;transition:all 0.3s" onmouseover="this.style.background='var(--light-blue)';this.style.color='#fff'" onmouseout="this.style.background='transparent';this.style.color='var(--light-blue)'">VIEW REPO →</a>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <p>
    <a href="mailto:aayushman.pratap.singh23@gmail.com">aayushman.pratap.singh23@gmail.com</a>
    &nbsp;//&nbsp;
    <a href="mailto:as7310@srmist.edu.in">as7310@srmist.edu.in</a>
    &nbsp;//&nbsp;
    <a href="tel:+919968347111">+91-9968347111</a>
  </p>
  <p style="margin-top:12px;font-size:0.7rem;opacity:0.4">AAYUSHMAN PRATAP SINGH · CSE · SRM IST · 2027 · dismantled1</p>
</footer>

<script>
// scroll progress bar
window.addEventListener('scroll',()=>{
  const s=document.body.scrollTop||document.documentElement.scrollTop;
  const h=document.documentElement.scrollHeight-document.documentElement.clientHeight;
  document.getElementById('progress-bar').style.width=(s/h*100)+'%';
});

// scroll reveal
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('active')});
},{threshold:0.12,rootMargin:'0px 0px -60px 0px'});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

// counter animation
function animateCounter(el){
  const target=+el.dataset.target,dur=1800,start=performance.now();
  function update(now){
    const p=Math.min((now-start)/dur,1),ease=1-Math.pow(1-p,3);
    el.textContent=Math.floor(ease*target);
    if(p<1)requestAnimationFrame(update);else el.textContent=target;
  }
  requestAnimationFrame(update);
}
const cObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting){animateCounter(e.target);cObs.unobserve(e.target)}});
},{threshold:0.5});
document.querySelectorAll('.counter-num').forEach(el=>cObs.observe(el));

// telemetry pulse
const vals=document.querySelectorAll('.stat-box .value');
setInterval(()=>{vals.forEach(v=>{v.style.opacity='0.7';setTimeout(()=>v.style.opacity='1',100)})},3000);

// card tilt
document.querySelectorAll('.card').forEach(card=>{
  card.addEventListener('mousemove',e=>{
    const r=card.getBoundingClientRect(),x=e.clientX-r.left,y=e.clientY-r.top;
    const rx=(y-r.height/2)/30,ry=(r.width/2-x)/30;
    card.style.transform=`translateY(-8px) scale(1.01) perspective(1000px) rotateX(${rx}deg) rotateY(${ry}deg)`;
  });
  card.addEventListener('mouseleave',()=>{card.style.transform=''});
});

// stagger skill logos
document.querySelectorAll('.skill-logo-grid').forEach(grid=>{
  const logos=grid.querySelectorAll('.skill-logo');
  logos.forEach((l,i)=>{l.style.opacity='0';l.style.transform='translateY(16px)';l.style.transitionDelay=i*0.04+'s'});
  const o=new IntersectionObserver(entries=>{
    entries.forEach(e=>{if(e.isIntersecting){logos.forEach(l=>{l.style.opacity='1';l.style.transform='none'});o.unobserve(e.target)}});
  },{threshold:0.2});
  o.observe(grid);
});
</script>
</body>
</html>
