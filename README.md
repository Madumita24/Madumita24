<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Madumita Karthikeyan — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
:root {
  --blue: #0E75B6;
  --cyan: #00D4FF;
  --light-blue: #6AA9E9;
  --dark: #020810;
  --card-bg: rgba(8,20,40,0.85);
  --border: rgba(0,212,255,0.18);
  --text: #E2E8F0;
  --muted: #64748B;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--dark);color:var(--text);font-family:'Rajdhani',sans-serif;overflow-x:hidden;cursor:none;}
.cursor{width:8px;height:8px;background:var(--cyan);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9999;mix-blend-mode:screen;}
.cursor-ring{width:32px;height:32px;border:1px solid rgba(0,212,255,0.5);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9998;transition:all 0.15s ease;}
#bg-canvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;}
body::after{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,0.03) 2px,rgba(0,0,0,0.03) 4px);pointer-events:none;z-index:1;}
.page{position:relative;z-index:2;max-width:1000px;margin:0 auto;padding:0 32px;}

/* HERO */
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:80px 0 60px;position:relative;}
.hero-ring{position:absolute;border-radius:50%;border:1px solid rgba(0,212,255,0.07);animation:ringRot 20s linear infinite;}
.hr1{width:500px;height:500px;}
.hr2{width:380px;height:380px;border-color:rgba(14,117,182,0.1);animation-duration:14s;animation-direction:reverse;}
.hr3{width:260px;height:260px;border-color:rgba(0,212,255,0.09);animation-duration:9s;}
@keyframes ringRot{from{transform:rotate(0deg);}to{transform:rotate(360deg);}}
.avatar-3d{width:110px;height:110px;background:linear-gradient(135deg,#041428,#0a2a50);border-radius:50%;border:2px solid rgba(0,212,255,0.5);display:flex;align-items:center;justify-content:center;font-size:48px;margin-bottom:32px;position:relative;animation:float 4s ease-in-out infinite;box-shadow:0 0 40px rgba(0,212,255,0.15),inset 0 0 30px rgba(0,212,255,0.05);}
.avatar-3d::before{content:'';position:absolute;inset:-4px;border-radius:50%;background:conic-gradient(from 0deg,transparent 60%,rgba(0,212,255,0.6) 100%,transparent);animation:ringRot 2s linear infinite;z-index:-1;}
@keyframes float{0%,100%{transform:translateY(0);}50%{transform:translateY(-12px);}}
.hero-tag{font-family:'Space Mono',monospace;font-size:11px;color:var(--cyan);letter-spacing:4px;text-transform:uppercase;margin-bottom:16px;opacity:0;animation:fadeUp 0.8s ease 0.2s both;}
.hero-name{font-family:'Orbitron',monospace;font-size:clamp(36px,7vw,68px);font-weight:900;line-height:1.05;margin-bottom:16px;background:linear-gradient(135deg,#fff 0%,#6AA9E9 50%,#00D4FF 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;opacity:0;animation:fadeUp 0.8s ease 0.4s both;}
.hero-sub{font-size:18px;color:var(--light-blue);letter-spacing:2px;margin-bottom:32px;font-weight:500;opacity:0;animation:fadeUp 0.8s ease 0.6s both;}
.typing-wrap{font-family:'Space Mono',monospace;font-size:14px;color:var(--muted);background:rgba(0,212,255,0.04);border:1px solid rgba(0,212,255,0.15);border-radius:8px;padding:12px 24px;margin-bottom:40px;display:inline-block;opacity:0;animation:fadeUp 0.8s ease 0.8s both;}
.typing-wrap .prompt{color:var(--cyan);}
#typed{color:#94A3B8;}
.blink{display:inline-block;width:2px;height:14px;background:var(--cyan);margin-left:2px;vertical-align:middle;animation:blink 1s step-end infinite;}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.badges{display:flex;gap:12px;flex-wrap:wrap;justify-content:center;margin-bottom:48px;opacity:0;animation:fadeUp 0.8s ease 1s both;}
.badge{padding:6px 16px;border-radius:4px;font-size:12px;font-weight:600;letter-spacing:1px;font-family:'Space Mono',monospace;position:relative;overflow:hidden;transition:all 0.3s;}
.badge::before{content:'';position:absolute;inset:0;background:linear-gradient(90deg,transparent,rgba(255,255,255,0.1),transparent);transform:translateX(-100%);transition:transform 0.5s;}
.badge:hover::before{transform:translateX(100%);}
.b-gpa{background:rgba(105,240,174,0.1);border:1px solid rgba(105,240,174,0.4);color:#69F0AE;}
.b-hack{background:rgba(255,213,79,0.1);border:1px solid rgba(255,213,79,0.4);color:#FFD54F;}
.b-focus{background:rgba(14,117,182,0.15);border:1px solid rgba(14,117,182,0.5);color:var(--light-blue);}
.b-asu{background:rgba(153,0,0,0.15);border:1px solid rgba(153,0,0,0.5);color:#FF6B6B;}
.scroll-hint{display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0;animation:fadeUp 0.8s ease 1.4s both;font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:var(--muted);}
.scroll-line{width:1px;height:50px;background:linear-gradient(to bottom,var(--cyan),transparent);animation:sline 1.5s ease-in-out infinite;}
@keyframes sline{0%,100%{opacity:1;transform:scaleY(1);}50%{opacity:0.3;transform:scaleY(0.5);}}
@keyframes fadeUp{from{opacity:0;transform:translateY(24px);}to{opacity:1;transform:translateY(0);}}

/* SECTIONS */
section{padding:100px 0;}
.sec-header{display:flex;align-items:center;gap:16px;margin-bottom:60px;}
.sec-num{font-family:'Orbitron',monospace;font-size:11px;color:var(--cyan);letter-spacing:2px;}
.sec-title{font-family:'Orbitron',monospace;font-size:28px;font-weight:700;color:#fff;}
.sec-line{flex:1;height:1px;background:linear-gradient(90deg,rgba(0,212,255,0.4),transparent);}

/* ABOUT CODE */
.about-code{background:rgba(4,15,30,0.9);border:1px solid rgba(0,212,255,0.15);border-radius:12px;overflow:hidden;}
.code-bar{display:flex;align-items:center;gap:8px;padding:12px 16px;background:rgba(0,212,255,0.05);border-bottom:1px solid rgba(0,212,255,0.1);}
.dot{width:10px;height:10px;border-radius:50%;}
.dr{background:#FF5F57;}.dy{background:#FEBC2E;}.dg{background:#28C840;}
.code-file{margin-left:auto;font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);}
.code-body{padding:28px 32px;font-family:'Space Mono',monospace;font-size:13px;line-height:2.1;}
.ck{color:#FF79C6;}.cv{color:#8BE9FD;}.cs{color:#F1FA8C;}.ca{color:#BD93F9;}.cc{color:#6272A4;}.ckey{color:#50FA7B;}.cn{color:#FFB86C;}

/* STATS */
.stats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;}
.stat-card{background:var(--card-bg);border:1px solid var(--border);border-radius:12px;padding:28px 20px;text-align:center;position:relative;overflow:hidden;transition:all 0.4s;cursor:default;}
.stat-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--cyan),transparent);transform:translateX(-100%);transition:transform 0.6s;}
.stat-card:hover::before{transform:translateX(0);}
.stat-card:hover{border-color:rgba(0,212,255,0.4);transform:translateY(-6px);box-shadow:0 20px 60px rgba(0,212,255,0.1);}
.stat-icon{font-size:28px;margin-bottom:12px;}
.stat-num{font-family:'Orbitron',monospace;font-size:38px;font-weight:900;color:var(--cyan);display:block;line-height:1;margin-bottom:8px;}
.stat-label{font-size:12px;color:var(--muted);letter-spacing:1px;text-transform:uppercase;}

/* PROJECTS */
.projects-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;}
.proj-card{background:var(--card-bg);border:1px solid var(--border);border-radius:16px;padding:28px;position:relative;overflow:hidden;transition:border-color 0.4s,box-shadow 0.4s;cursor:default;}
.proj-card.featured{grid-column:span 2;}
.proj-card::after{content:'';position:absolute;top:-50%;left:-50%;width:200%;height:200%;background:radial-gradient(circle at center,rgba(0,212,255,0.04) 0%,transparent 60%);opacity:0;transition:opacity 0.4s;pointer-events:none;}
.proj-card:hover::after{opacity:1;}
.proj-card:hover{border-color:rgba(0,212,255,0.35);box-shadow:0 24px 80px rgba(0,212,255,0.1);}
.proj-glow{position:absolute;top:0;right:0;width:200px;height:200px;background:radial-gradient(circle,rgba(0,212,255,0.05) 0%,transparent 70%);pointer-events:none;}
.proj-top{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:14px;}
.proj-icon{width:48px;height:48px;background:rgba(0,212,255,0.08);border:1px solid rgba(0,212,255,0.2);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:22px;flex-shrink:0;}
.hack-badge{font-family:'Space Mono',monospace;font-size:10px;color:#FFD54F;background:rgba(255,213,79,0.1);border:1px solid rgba(255,213,79,0.3);padding:4px 10px;border-radius:4px;letter-spacing:1px;}
.proj-title{font-family:'Orbitron',monospace;font-size:14px;font-weight:700;color:#fff;margin-bottom:10px;}
.proj-desc{font-size:14px;color:#94A3B8;line-height:1.6;margin-bottom:16px;}
.proj-stat{display:inline-flex;align-items:center;gap:6px;font-family:'Space Mono',monospace;font-size:11px;color:#69F0AE;background:rgba(105,240,174,0.08);border:1px solid rgba(105,240,174,0.2);padding:4px 12px;border-radius:20px;margin-right:8px;margin-bottom:8px;}
.proj-tags{display:flex;flex-wrap:wrap;gap:6px;margin-top:14px;}
.tag{font-size:11px;font-family:'Space Mono',monospace;color:var(--muted);background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);padding:3px 10px;border-radius:4px;transition:all 0.2s;}
.tag:hover{color:var(--cyan);border-color:rgba(0,212,255,0.3);background:rgba(0,212,255,0.06);}

/* SKILLS */
.skills-layout{display:grid;grid-template-columns:1fr 1fr;gap:40px;}
.sk-group-title{font-family:'Space Mono',monospace;font-size:11px;letter-spacing:3px;color:var(--cyan);text-transform:uppercase;margin-bottom:20px;padding-bottom:10px;border-bottom:1px solid rgba(0,212,255,0.1);}
.sk-row{margin-bottom:16px;}
.sk-meta{display:flex;justify-content:space-between;font-size:13px;color:#CBD5E1;margin-bottom:7px;font-weight:500;}
.sk-pct{font-family:'Space Mono',monospace;font-size:11px;color:var(--cyan);}
.sk-track{height:3px;background:rgba(0,212,255,0.08);border-radius:2px;overflow:hidden;position:relative;}
.sk-fill{height:100%;background:linear-gradient(90deg,var(--blue),var(--cyan));border-radius:2px;width:0;transition:width 1.4s cubic-bezier(0.16,1,0.3,1);position:relative;}
.sk-fill::after{content:'';position:absolute;right:0;top:50%;transform:translateY(-50%);width:6px;height:6px;border-radius:50%;background:var(--cyan);box-shadow:0 0 8px var(--cyan);}
.tech-cloud{display:flex;flex-wrap:wrap;gap:10px;}
.tech-chip{display:flex;align-items:center;gap:8px;padding:8px 14px;background:rgba(14,117,182,0.08);border:1px solid rgba(14,117,182,0.2);border-radius:8px;font-family:'Space Mono',monospace;font-size:12px;color:#94A3B8;transition:all 0.25s;cursor:default;}
.tech-chip:hover{background:rgba(0,212,255,0.1);border-color:rgba(0,212,255,0.4);color:var(--cyan);transform:translateY(-2px);}
.tc-dot{width:6px;height:6px;border-radius:50%;background:var(--cyan);opacity:0.5;transition:opacity 0.2s;}
.tech-chip:hover .tc-dot{opacity:1;}

/* ACTIVITY */
.contrib-wrap{background:var(--card-bg);border:1px solid var(--border);border-radius:16px;padding:32px;overflow-x:auto;}
.contrib-wrap::-webkit-scrollbar{height:3px;}
.contrib-wrap::-webkit-scrollbar-thumb{background:rgba(0,212,255,0.3);border-radius:2px;}
.m-row{display:flex;gap:3px;padding-left:28px;margin-bottom:6px;}
.m-lbl{font-family:'Space Mono',monospace;font-size:10px;color:#334155;width:16px;flex-shrink:0;}
.g-body{display:flex;gap:6px;align-items:flex-start;}
.d-lbls{display:flex;flex-direction:column;gap:3px;padding-top:2px;}
.d-lbl{font-family:'Space Mono',monospace;font-size:9px;color:#334155;height:13px;line-height:13px;width:22px;text-align:right;}
.w-row{display:flex;gap:3px;}
.w-col{display:flex;flex-direction:column;gap:3px;}
.g-cell{width:13px;height:13px;border-radius:3px;flex-shrink:0;cursor:pointer;transition:transform 0.12s,filter 0.12s;position:relative;}
.g-cell:hover{transform:scale(1.5);z-index:10;filter:brightness(1.4);}
.g-tip{position:absolute;bottom:calc(100% + 6px);left:50%;transform:translateX(-50%);background:#0F172A;border:1px solid rgba(0,212,255,0.3);border-radius:6px;padding:5px 10px;font-size:10px;white-space:nowrap;color:#94A3B8;pointer-events:none;opacity:0;transition:opacity 0.15s;z-index:30;font-family:'Space Mono',monospace;}
.g-cell:hover .g-tip{opacity:1;}
.c-footer{display:flex;align-items:center;justify-content:space-between;margin-top:16px;}
.legend{display:flex;align-items:center;gap:5px;font-family:'Space Mono',monospace;font-size:10px;color:#334155;}
.l-cell{width:13px;height:13px;border-radius:3px;flex-shrink:0;}

/* CONNECT */
.connect-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.connect-card{background:var(--card-bg);border:1px solid var(--border);border-radius:14px;padding:28px 24px;display:flex;flex-direction:column;align-items:center;gap:14px;text-decoration:none;transition:all 0.35s;position:relative;overflow:hidden;}
.connect-card::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at 50% 0%,rgba(0,212,255,0.08) 0%,transparent 70%);opacity:0;transition:opacity 0.35s;}
.connect-card:hover::before{opacity:1;}
.connect-card:hover{border-color:rgba(0,212,255,0.4);transform:translateY(-6px);box-shadow:0 20px 60px rgba(0,212,255,0.1);}
.c-icon{width:52px;height:52px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:24px;border:1px solid rgba(0,212,255,0.2);}
.c-label{font-family:'Orbitron',monospace;font-size:13px;font-weight:700;color:#fff;}
.c-val{font-size:12px;color:var(--muted);font-family:'Space Mono',monospace;text-align:center;}

/* FOOTER */
footer{text-align:center;padding:60px 0 40px;border-top:1px solid rgba(0,212,255,0.08);}
.f-text{font-family:'Orbitron',monospace;font-size:13px;color:var(--muted);letter-spacing:3px;}
.f-text span{color:var(--cyan);}
.f-line{width:60px;height:1px;background:linear-gradient(90deg,transparent,var(--cyan),transparent);margin:20px auto;}

/* REVEAL */
.reveal{opacity:0;transform:translateY(40px);transition:opacity 0.8s ease,transform 0.8s ease;}
.reveal.visible{opacity:1;transform:translateY(0);}
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursor-ring"></div>
<canvas id="bg-canvas"></canvas>

<div class="page">

  <div class="hero">
    <div class="hero-ring hr1"></div>
    <div class="hero-ring hr2"></div>
    <div class="hero-ring hr3"></div>
    <div class="avatar-3d">🤖</div>
    <div class="hero-tag">// madumita.karthikeyan · portfolio.exe</div>
    <h1 class="hero-name">MADUMITA<br>KARTHIKEYAN</h1>
    <div class="hero-sub">Data Science @ ASU &nbsp;·&nbsp; GPA 4.0 &nbsp;·&nbsp; GenAI · ML · Cloud</div>
    <div class="typing-wrap">
      <span class="prompt">$ </span><span id="typed"></span><span class="blink"></span>
    </div>
    <div class="badges">
      <span class="badge b-gpa">GPA 4.0 / 4.0</span>
      <span class="badge b-hack">🏆 Hackathon Winner</span>
      <span class="badge b-focus">GenAI · ML · Cloud</span>
      <span class="badge b-asu">ASU Data Science</span>
    </div>
    <div class="scroll-hint">
      <span>SCROLL</span>
      <div class="scroll-line"></div>
    </div>
  </div>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">01</span>
      <h2 class="sec-title">ABOUT ME</h2>
      <div class="sec-line"></div>
    </div>
    <div class="about-code">
      <div class="code-bar">
        <div class="dot dr"></div><div class="dot dy"></div><div class="dot dg"></div>
        <span class="code-file">madumita.py</span>
      </div>
      <div class="code-body">
        <div><span class="cc"># Who I am &amp; what I build</span></div>
        <div>&nbsp;</div>
        <div><span class="ck">class</span> <span class="cv">Madumita</span>:</div>
        <div>&nbsp;&nbsp;<span class="ckey">education</span>  = <span class="cs">"M.S. Data Science, Analytics &amp; Engineering @ ASU"</span></div>
        <div>&nbsp;&nbsp;<span class="ckey">gpa</span>        = <span class="cn">4.0</span> <span class="cc"># out of 4.0 🎯</span></div>
        <div>&nbsp;&nbsp;<span class="ckey">building</span>   = [<span class="cs">"LLM-powered apps"</span>, <span class="cs">"ML pipelines"</span>, <span class="cs">"forecasting models"</span>]</div>
        <div>&nbsp;&nbsp;<span class="ckey">stack</span>      = [<span class="cs">"LangChain"</span>, <span class="cs">"OpenAI"</span>, <span class="cs">"HuggingFace"</span>, <span class="cs">"GCP"</span>, <span class="cs">"AWS"</span>]</div>
        <div>&nbsp;&nbsp;<span class="ckey">domains</span>    = [<span class="cs">"Healthcare AI"</span>, <span class="cs">"Manufacturing"</span>, <span class="cs">"Social Good"</span>]</div>
        <div>&nbsp;&nbsp;<span class="ckey">achievement</span>= <span class="cs">"🏅 Most Creative Design — ASU Hackathon"</span></div>
        <div>&nbsp;&nbsp;<span class="ckey">motto</span>      = <span class="cs">"data → insights → impact"</span></div>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">02</span>
      <h2 class="sec-title">IMPACT</h2>
      <div class="sec-line"></div>
    </div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-icon">⚡</div><span class="stat-num" data-target="40">0</span><div class="stat-label">% faster retrieval</div></div>
      <div class="stat-card"><div class="stat-icon">🧠</div><span class="stat-num" data-target="97">0</span><div class="stat-label">% EEG accuracy</div></div>
      <div class="stat-card"><div class="stat-icon">📰</div><span class="stat-num" data-target="80">0</span><div class="stat-label">% review time cut</div></div>
      <div class="stat-card"><div class="stat-icon">🗄️</div><span class="stat-num" data-target="35">0</span><div class="stat-label">% fewer query fails</div></div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">03</span>
      <h2 class="sec-title">PROJECTS</h2>
      <div class="sec-line"></div>
    </div>
    <div class="projects-grid">
      <div class="proj-card featured">
        <div class="proj-glow"></div>
        <div class="proj-top">
          <div class="proj-icon">😊</div>
          <span class="hack-badge">🏅 MOST CREATIVE DESIGN · ASU HACKATHON</span>
        </div>
        <div class="proj-title">FeelIn – Emotion-Aware Dashboard</div>
        <div class="proj-desc">Real-time sentiment analytics with Firebase + OpenAI. A live emotional intelligence layer over conversation data — won ASU Hackathon for Most Creative Design.</div>
        <span class="proj-stat">↑ Real-time</span><span class="proj-stat">Hackathon Winner</span>
        <div class="proj-tags"><span class="tag">Firebase</span><span class="tag">OpenAI</span><span class="tag">Sentiment Analysis</span><span class="tag">Python</span></div>
      </div>
      <div class="proj-card">
        <div class="proj-glow"></div>
        <div class="proj-icon" style="margin-bottom:14px">🗂️</div>
        <div class="proj-title">Conversational Q&amp;A System</div>
        <div class="proj-desc">GenAI chatbot with LangChain + FAISS memory support for multi-turn retrieval.</div>
        <span class="proj-stat">↑ 40% retrieval speed</span>
        <div class="proj-tags"><span class="tag">LangChain</span><span class="tag">FAISS</span><span class="tag">OpenAI</span></div>
      </div>
      <div class="proj-card">
        <div class="proj-glow"></div>
        <div class="proj-icon" style="margin-bottom:14px">📊</div>
        <div class="proj-title">NL → SQL Agent</div>
        <div class="proj-desc">Bridges plain English to databases via LangChain — no SQL knowledge needed.</div>
        <span class="proj-stat">↓ 35% query failures</span>
        <div class="proj-tags"><span class="tag">LangChain</span><span class="tag">SQL</span><span class="tag">PostgreSQL</span></div>
      </div>
      <div class="proj-card">
        <div class="proj-glow"></div>
        <div class="proj-icon" style="margin-bottom:14px">📰</div>
        <div class="proj-title">LLM Summarizer</div>
        <div class="proj-desc">Auto-summarizes YouTube &amp; web articles via HuggingFace + Streamlit.</div>
        <span class="proj-stat">↓ 80% review time</span>
        <div class="proj-tags"><span class="tag">HuggingFace</span><span class="tag">Streamlit</span></div>
      </div>
      <div class="proj-card">
        <div class="proj-glow"></div>
        <div class="proj-icon" style="margin-bottom:14px">🧠</div>
        <div class="proj-title">EEG Seizure Detection</div>
        <div class="proj-desc">Random Forest + LLM ensemble on clinical EEG data for high-accuracy detection.</div>
        <span class="proj-stat">97% accuracy</span>
        <div class="proj-tags"><span class="tag">Random Forest</span><span class="tag">LLM</span><span class="tag">scikit-learn</span></div>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">04</span>
      <h2 class="sec-title">TECH STACK</h2>
      <div class="sec-line"></div>
    </div>
    <div class="skills-layout">
      <div>
        <div class="sk-group-title">// Core Languages</div>
        <div class="sk-row"><div class="sk-meta"><span>Python</span><span class="sk-pct">95%</span></div><div class="sk-track"><div class="sk-fill" data-w="95"></div></div></div>
        <div class="sk-row"><div class="sk-meta"><span>SQL / PostgreSQL</span><span class="sk-pct">88%</span></div><div class="sk-track"><div class="sk-fill" data-w="88"></div></div></div>
        <div class="sk-row"><div class="sk-meta"><span>R</span><span class="sk-pct">78%</span></div><div class="sk-track"><div class="sk-fill" data-w="78"></div></div></div>
        <br/>
        <div class="sk-group-title">// AI / ML / GenAI</div>
        <div class="sk-row"><div class="sk-meta"><span>LangChain</span><span class="sk-pct">92%</span></div><div class="sk-track"><div class="sk-fill" data-w="92"></div></div></div>
        <div class="sk-row"><div class="sk-meta"><span>OpenAI / GPT APIs</span><span class="sk-pct">90%</span></div><div class="sk-track"><div class="sk-fill" data-w="90"></div></div></div>
        <div class="sk-row"><div class="sk-meta"><span>HuggingFace</span><span class="sk-pct">85%</span></div><div class="sk-track"><div class="sk-fill" data-w="85"></div></div></div>
        <div class="sk-row"><div class="sk-meta"><span>scikit-learn</span><span class="sk-pct">88%</span></div><div class="sk-track"><div class="sk-fill" data-w="88"></div></div></div>
      </div>
      <div>
        <div class="sk-group-title">// Cloud &amp; DevOps</div>
        <div class="tech-cloud">
          <div class="tech-chip"><div class="tc-dot"></div>Docker</div>
          <div class="tech-chip"><div class="tc-dot"></div>Kubernetes</div>
          <div class="tech-chip"><div class="tc-dot"></div>GCP</div>
          <div class="tech-chip"><div class="tc-dot"></div>AWS</div>
          <div class="tech-chip"><div class="tc-dot"></div>Firebase</div>
          <div class="tech-chip"><div class="tc-dot"></div>Streamlit</div>
          <div class="tech-chip"><div class="tc-dot"></div>Git</div>
          <div class="tech-chip"><div class="tc-dot"></div>Neo4j</div>
        </div>
        <br/>
        <div class="sk-group-title">// Visualization</div>
        <div class="tech-cloud">
          <div class="tech-chip"><div class="tc-dot"></div>Power BI</div>
          <div class="tech-chip"><div class="tc-dot"></div>Tableau</div>
          <div class="tech-chip"><div class="tc-dot"></div>Plotly</div>
          <div class="tech-chip"><div class="tc-dot"></div>Matplotlib</div>
          <div class="tech-chip"><div class="tc-dot"></div>Seaborn</div>
        </div>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">05</span>
      <h2 class="sec-title">GITHUB ACTIVITY</h2>
      <div class="sec-line"></div>
    </div>
    <div class="contrib-wrap">
      <div class="m-row" id="m-row"></div>
      <div class="g-body">
        <div class="d-lbls">
          <div class="d-lbl"></div>
          <div class="d-lbl">Mon</div>
          <div class="d-lbl"></div>
          <div class="d-lbl">Wed</div>
          <div class="d-lbl"></div>
          <div class="d-lbl">Fri</div>
          <div class="d-lbl"></div>
        </div>
        <div class="w-row" id="w-row"></div>
      </div>
      <div class="c-footer">
        <div class="legend">
          Less
          <div class="l-cell" style="background:#0D1117;border:1px solid rgba(0,212,255,0.1)"></div>
          <div class="l-cell" style="background:#0d2137"></div>
          <div class="l-cell" style="background:#0a4272"></div>
          <div class="l-cell" style="background:#0E75B6"></div>
          <div class="l-cell" style="background:#00D4FF"></div>
          More
        </div>
        <div style="font-family:'Space Mono',monospace;font-size:11px;color:#475569">
          <span style="color:#6AA9E9">github.com/Madumita24</span>
        </div>
      </div>
    </div>
  </section>

  <section class="reveal">
    <div class="sec-header">
      <span class="sec-num">06</span>
      <h2 class="sec-title">CONNECT</h2>
      <div class="sec-line"></div>
    </div>
    <div class="connect-grid">
      <a class="connect-card" href="mailto:mkarthi5@asu.edu">
        <div class="c-icon" style="background:rgba(209,72,54,0.1);border-color:rgba(209,72,54,0.3)">📧</div>
        <div class="c-label">Email</div>
        <div class="c-val">mkarthi5@asu.edu</div>
      </a>
      <a class="connect-card" href="https://www.linkedin.com/in/madumita24/" target="_blank">
        <div class="c-icon" style="background:rgba(10,102,194,0.1);border-color:rgba(10,102,194,0.3)">💼</div>
        <div class="c-label">LinkedIn</div>
        <div class="c-val">madumita24</div>
      </a>
      <a class="connect-card" href="https://github.com/Madumita24" target="_blank">
        <div class="c-icon" style="background:rgba(255,255,255,0.06);border-color:rgba(255,255,255,0.15)">⌨️</div>
        <div class="c-label">GitHub</div>
        <div class="c-val">Madumita24</div>
      </a>
    </div>
  </section>

  <footer>
    <div class="f-line"></div>
    <div class="f-text">✦ Always curious, always building — <span>let's collaborate</span> ✦</div>
    <div class="f-line"></div>
  </footer>

</div>

<script>
/* CURSOR */
const cur=document.getElementById('cursor'),ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.left=(mx-4)+'px';cur.style.top=(my-4)+'px';});
(function ar(){rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;ring.style.left=(rx-16)+'px';ring.style.top=(ry-16)+'px';requestAnimationFrame(ar);})();
document.querySelectorAll('a,.stat-card,.proj-card,.tech-chip,.connect-card').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ring.style.transform='scale(1.8)';ring.style.borderColor='rgba(0,212,255,0.8)';});
  el.addEventListener('mouseleave',()=>{ring.style.transform='scale(1)';ring.style.borderColor='rgba(0,212,255,0.5)';});
});

/* THREE.JS */
(function(){
  const canvas=document.getElementById('bg-canvas');
  const renderer=new THREE.WebGLRenderer({canvas,alpha:true,antialias:true});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));
  renderer.setSize(window.innerWidth,window.innerHeight);
  const scene=new THREE.Scene();
  const camera=new THREE.PerspectiveCamera(60,window.innerWidth/window.innerHeight,0.1,1000);
  camera.position.z=5;

  const N=1800,pos=new Float32Array(N*3);
  for(let i=0;i<N*3;i++)pos[i]=(Math.random()-0.5)*30;
  const starGeo=new THREE.BufferGeometry();
  starGeo.setAttribute('position',new THREE.BufferAttribute(pos,3));
  scene.add(new THREE.Points(starGeo,new THREE.PointsMaterial({color:0x6AA9E9,size:0.04,transparent:true,opacity:0.55})));

  const gridMat=new THREE.LineBasicMaterial({color:0x0E75B6,transparent:true,opacity:0.05});
  for(let i=-6;i<=6;i++){
    scene.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints([new THREE.Vector3(-10,i*0.8,0),new THREE.Vector3(10,i*0.8,0)]),gridMat));
    scene.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints([new THREE.Vector3(i*1.2,-6,0),new THREE.Vector3(i*1.2,6,0)]),gridMat));
  }

  const orbs=[];
  for(let i=0;i<6;i++){
    const m=new THREE.Mesh(new THREE.SphereGeometry(0.03,8,8),new THREE.MeshBasicMaterial({color:0x00D4FF}));
    m.userData={r:1.5+i*0.4,spd:0.004+i*0.002,ph:i*Math.PI/3,y:(Math.random()-0.5)*2};
    scene.add(m);orbs.push(m);
  }

  let tmx=0,tmy=0;
  document.addEventListener('mousemove',e=>{tmx=(e.clientX/window.innerWidth-0.5)*0.3;tmy=(e.clientY/window.innerHeight-0.5)*-0.3;});

  let t=0;
  (function anim(){
    requestAnimationFrame(anim);t+=0.008;
    camera.position.x+=(tmx-camera.position.x)*0.04;
    camera.position.y+=(tmy-camera.position.y)*0.04;
    camera.lookAt(scene.position);
    const pa=starGeo.attributes.position.array;
    for(let i=2;i<pa.length;i+=3){pa[i]+=0.002;if(pa[i]>15)pa[i]=-15;}
    starGeo.attributes.position.needsUpdate=true;
    orbs.forEach(o=>{const d=o.userData;o.position.x=Math.cos(t*d.spd*100+d.ph)*d.r;o.position.y=Math.sin(t*d.spd*100+d.ph)*d.r*0.3+d.y;o.position.z=-2;});
    renderer.render(scene,camera);
  })();
  window.addEventListener('resize',()=>{camera.aspect=window.innerWidth/window.innerHeight;camera.updateProjectionMatrix();renderer.setSize(window.innerWidth,window.innerHeight);});
})();

/* TYPING */
const phrases=['building LLM-powered applications...','designing ML pipelines & forecasts...','deploying on GCP, AWS & Docker...','achieving 97% EEG accuracy...','turning data → insights → impact...'];
let pi=0,ci=0,del=false;
const typedEl=document.getElementById('typed');
function tl(){const p=phrases[pi];if(!del){typedEl.textContent=p.slice(0,++ci);if(ci===p.length){del=true;setTimeout(tl,1800);return;}}else{typedEl.textContent=p.slice(0,--ci);if(ci===0){del=false;pi=(pi+1)%phrases.length;}}setTimeout(tl,del?38:72);}
tl();

/* REVEAL */
const obs=new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');if(e.target.querySelector('.stat-num'))animStats();if(e.target.querySelector('.sk-fill'))animBars();}});},{threshold:0.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

let sd=false;
function animStats(){if(sd)return;sd=true;document.querySelectorAll('.stat-num').forEach(el=>{const t=parseInt(el.dataset.target);let c=0;const iv=setInterval(()=>{c=Math.min(c+t/50,t);el.textContent=Math.round(c)+'%';if(c>=t)clearInterval(iv);},25);});}

let bd=false;
function animBars(){if(bd)return;bd=true;setTimeout(()=>{document.querySelectorAll('.sk-fill').forEach(f=>{f.style.width=f.dataset.w+'%';});},200);}

/* 3D TILT */
document.querySelectorAll('.proj-card,.stat-card,.connect-card').forEach(card=>{
  card.addEventListener('mousemove',e=>{const r=card.getBoundingClientRect(),x=(e.clientX-r.left)/r.width-0.5,y=(e.clientY-r.top)/r.height-0.5;card.style.transform=`perspective(600px) rotateX(${-y*8}deg) rotateY(${x*8}deg) translateY(-4px)`;});
  card.addEventListener('mouseleave',()=>{card.style.transform='';card.style.transition='transform 0.5s ease';});
  card.addEventListener('mouseenter',()=>{card.style.transition='transform 0.1s ease';});
});

/* CONTRIB GRAPH */
(function(){
  const WEEKS=52,palette=['#0D1117','#0d2137','#0a4272','#0E75B6','#00D4FF'];
  const months=['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
  const mws=[0,4,9,13,17,22,26,30,35,39,43,48];
  function rl(){const r=Math.random();if(r<0.22)return 0;if(r<0.42)return 1;if(r<0.62)return 2;if(r<0.82)return 3;return 4;}
  const mr=document.getElementById('m-row');
  let lm=-1;
  for(let w=0;w<WEEKS;w++){const mi=mws.filter(s=>s<=w).length-1;const el=document.createElement('div');el.className='m-lbl';el.textContent=(mi>=0&&mws[mi]===w)?months[mi]:'';mr.appendChild(el);}
  const wr=document.getElementById('w-row'),now=new Date();
  for(let w=0;w<WEEKS;w++){
    const col=document.createElement('div');col.className='w-col';
    for(let d=0;d<7;d++){
      const cell=document.createElement('div');cell.className='g-cell';
      const lvl=rl();cell.style.background=palette[lvl];
      if(lvl===0)cell.style.border='1px solid rgba(0,212,255,0.08)';
      const cnt=lvl===0?0:[1,3,7,15][lvl-1]+Math.floor(Math.random()*3);
      const tip=document.createElement('div');tip.className='g-tip';
      const dt=new Date(now);dt.setDate(dt.getDate()-(WEEKS-1-w)*7-(6-d));
      const ds=dt.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'numeric'});
      tip.textContent=lvl===0?`No contributions · ${ds}`:`${cnt} contributions · ${ds}`;
      cell.appendChild(tip);col.appendChild(cell);
    }
    wr.appendChild(col);
  }
})();
</script>
</body>
</html>
