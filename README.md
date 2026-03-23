


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Tushar Kaushik — Data Engineer & ML Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --cyan: #00f5d4;
    --cyan-dim: #00c9aa;
    --green: #a8ff78;
    --amber: #f9c846;
    --bg: #070b10;
    --bg2: #0d1520;
    --bg3: #111d2b;
    --border: rgba(0,245,212,0.15);
    --border-bright: rgba(0,245,212,0.4);
    --text: #e2eaf4;
    --text-dim: #7a91a8;
    --mono: 'Space Mono', monospace;
    --sans: 'Syne', sans-serif;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:var(--sans);
    overflow-x:hidden;
    cursor:none;
  }

  /* custom cursor */
  #cursor{
    position:fixed;width:10px;height:10px;
    background:var(--cyan);border-radius:50%;
    pointer-events:none;z-index:9999;
    transform:translate(-50%,-50%);
    transition:transform 0.08s,width 0.2s,height 0.2s,background 0.2s;
    mix-blend-mode:screen;
  }
  #cursor-ring{
    position:fixed;width:36px;height:36px;
    border:1px solid var(--cyan);border-radius:50%;
    pointer-events:none;z-index:9998;
    transform:translate(-50%,-50%);
    transition:transform 0.18s ease,width 0.25s,height 0.25s,opacity 0.2s;
    opacity:0.5;
  }
  body:hover #cursor{opacity:1;}

  /* scanline overlay */
  body::before{
    content:'';
    position:fixed;inset:0;
    background:repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.05) 2px,
      rgba(0,0,0,0.05) 4px
    );
    pointer-events:none;z-index:1000;
    animation:scanMove 8s linear infinite;
  }
  @keyframes scanMove{from{background-position:0 0;}to{background-position:0 100px;}}

  /* canvas */
  #bg-canvas{position:fixed;inset:0;z-index:0;pointer-events:none;}

  /* nav */
  nav{
    position:fixed;top:0;left:0;right:0;z-index:500;
    padding:1.2rem 4rem;
    display:flex;justify-content:space-between;align-items:center;
    background:rgba(7,11,16,0.85);
    backdrop-filter:blur(14px);
    border-bottom:1px solid var(--border);
  }
  .nav-logo{
    font-family:var(--mono);font-size:0.8rem;
    color:var(--cyan);letter-spacing:0.2em;
    text-transform:uppercase;
  }
  .nav-links{display:flex;gap:2.5rem;}
  .nav-links a{
    font-family:var(--mono);font-size:0.72rem;
    color:var(--text-dim);text-decoration:none;
    letter-spacing:0.15em;text-transform:uppercase;
    transition:color 0.2s;
    position:relative;
  }
  .nav-links a::after{
    content:'';position:absolute;bottom:-4px;left:0;width:0;height:1px;
    background:var(--cyan);transition:width 0.3s;
  }
  .nav-links a:hover{color:var(--cyan);}
  .nav-links a:hover::after{width:100%;}

  /* sections */
  section{position:relative;z-index:10;}

  /* hero */
  #hero{
    min-height:100vh;
    display:flex;flex-direction:column;justify-content:center;
    padding:8rem 4rem 4rem;
    max-width:1100px;margin:0 auto;
  }
  .hero-tag{
    font-family:var(--mono);font-size:0.72rem;
    color:var(--cyan);letter-spacing:0.3em;text-transform:uppercase;
    margin-bottom:1.5rem;
    opacity:0;animation:fadeUp 0.6s 0.3s forwards;
  }
  .hero-name{
    font-size:clamp(3rem,7vw,6.5rem);
    font-weight:800;line-height:1;
    letter-spacing:-0.02em;
    color:var(--text);
    margin-bottom:1.2rem;
    opacity:0;animation:fadeUp 0.7s 0.5s forwards;
  }
  .hero-name span{
    color:transparent;
    -webkit-text-stroke:1px var(--cyan);
    display:inline-block;
  }
  .hero-typewriter{
    font-family:var(--mono);font-size:clamp(0.9rem,2vw,1.15rem);
    color:var(--text-dim);
    min-height:1.8em;
    margin-bottom:2.5rem;
    opacity:0;animation:fadeUp 0.6s 0.7s forwards;
  }
  .hero-typewriter .cursor-blink{
    display:inline-block;width:2px;height:1em;
    background:var(--cyan);vertical-align:middle;
    animation:blink 0.9s step-end infinite;
  }
  @keyframes blink{0%,100%{opacity:1;}50%{opacity:0;}}
  .hero-cta{
    display:flex;gap:1rem;flex-wrap:wrap;
    opacity:0;animation:fadeUp 0.6s 0.9s forwards;
  }
  .btn{
    display:inline-flex;align-items:center;gap:0.5rem;
    padding:0.75rem 1.8rem;
    font-family:var(--mono);font-size:0.75rem;
    letter-spacing:0.15em;text-transform:uppercase;
    border-radius:2px;
    text-decoration:none;cursor:none;
    transition:all 0.25s;
  }
  .btn-primary{
    background:var(--cyan);color:#070b10;
    border:1px solid var(--cyan);font-weight:700;
  }
  .btn-primary:hover{background:transparent;color:var(--cyan);}
  .btn-ghost{
    background:transparent;color:var(--text-dim);
    border:1px solid var(--border-bright);
  }
  .btn-ghost:hover{border-color:var(--cyan);color:var(--cyan);}
  .hero-scroll{
    position:absolute;bottom:3rem;left:4rem;
    display:flex;align-items:center;gap:1rem;
    font-family:var(--mono);font-size:0.65rem;
    color:var(--text-dim);letter-spacing:0.2em;
    opacity:0;animation:fadeUp 0.6s 1.2s forwards;
  }
  .hero-scroll-line{
    width:60px;height:1px;background:var(--border-bright);
    position:relative;overflow:hidden;
  }
  .hero-scroll-line::after{
    content:'';position:absolute;left:-100%;top:0;height:100%;width:100%;
    background:var(--cyan);animation:scrollSlide 2s 1.5s linear infinite;
  }
  @keyframes scrollSlide{from{left:-100%;}to{left:100%;}}

  @keyframes fadeUp{
    from{opacity:0;transform:translateY(24px);}
    to{opacity:1;transform:translateY(0);}
  }

  /* section headings */
  .section-header{
    margin-bottom:4rem;
    display:flex;align-items:center;gap:1.5rem;
  }
  .section-num{
    font-family:var(--mono);font-size:0.7rem;
    color:var(--cyan);letter-spacing:0.3em;
  }
  .section-title{
    font-size:clamp(1.6rem,3vw,2.2rem);
    font-weight:800;letter-spacing:-0.01em;
  }
  .section-line{
    flex:1;height:1px;
    background:linear-gradient(to right,var(--border-bright),transparent);
  }

  /* about */
  #about{padding:8rem 4rem;max-width:1100px;margin:0 auto;}
  .about-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:5rem;
    align-items:start;
  }
  .about-text p{
    font-size:1rem;line-height:1.85;color:var(--text-dim);margin-bottom:1.2rem;
  }
  .about-text p strong{color:var(--text);font-weight:600;}
  .about-text a{color:var(--cyan);text-decoration:none;}
  .about-text a:hover{text-decoration:underline;}
  .stats-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:1.5rem;
  }
  .stat-card{
    border:1px solid var(--border);
    padding:1.5rem;border-radius:4px;
    background:var(--bg2);
    position:relative;overflow:hidden;
    transition:border-color 0.3s,transform 0.3s;
  }
  .stat-card::before{
    content:'';position:absolute;inset:0;
    background:linear-gradient(135deg,rgba(0,245,212,0.05) 0%,transparent 60%);
    opacity:0;transition:opacity 0.3s;
  }
  .stat-card:hover{border-color:var(--border-bright);transform:translateY(-3px);}
  .stat-card:hover::before{opacity:1;}
  .stat-num{
    font-family:var(--mono);font-size:2rem;font-weight:700;
    color:var(--cyan);display:block;margin-bottom:0.3rem;
  }
  .stat-label{font-size:0.78rem;color:var(--text-dim);letter-spacing:0.08em;}

  /* skills */
  #skills{padding:8rem 4rem;background:var(--bg2);}
  .skills-inner{max-width:1100px;margin:0 auto;}
  .skill-categories{display:flex;flex-direction:column;gap:3rem;}
  .skill-cat-label{
    font-family:var(--mono);font-size:0.68rem;
    color:var(--cyan);letter-spacing:0.25em;text-transform:uppercase;
    margin-bottom:1rem;
  }
  .skill-chips{display:flex;flex-wrap:wrap;gap:0.6rem;}
  .chip{
    font-family:var(--mono);font-size:0.72rem;
    padding:0.45rem 0.9rem;border-radius:2px;
    border:1px solid var(--border);background:var(--bg3);
    color:var(--text-dim);letter-spacing:0.05em;
    transition:all 0.25s;cursor:none;
    position:relative;overflow:hidden;
  }
  .chip::before{
    content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;
    background:linear-gradient(90deg,transparent,rgba(0,245,212,0.1),transparent);
    transition:left 0.4s;
  }
  .chip:hover{border-color:var(--cyan);color:var(--cyan);}
  .chip:hover::before{left:100%;}
  .chip.highlight{border-color:rgba(0,245,212,0.4);color:var(--cyan);}

  /* projects */
  #projects{padding:8rem 4rem;max-width:1100px;margin:0 auto;}
  .projects-filter{
    display:flex;gap:0.8rem;margin-bottom:3rem;flex-wrap:wrap;
  }
  .filter-btn{
    font-family:var(--mono);font-size:0.68rem;
    padding:0.4rem 1rem;border-radius:2px;
    border:1px solid var(--border);background:transparent;
    color:var(--text-dim);letter-spacing:0.1em;
    text-transform:uppercase;cursor:none;transition:all 0.2s;
  }
  .filter-btn.active,.filter-btn:hover{
    border-color:var(--cyan);color:var(--cyan);
    background:rgba(0,245,212,0.06);
  }
  .projects-grid{
    display:grid;grid-template-columns:repeat(auto-fill,minmax(340px,1fr));
    gap:1.5rem;
  }
  .project-card{
    border:1px solid var(--border);border-radius:4px;
    background:var(--bg2);padding:2rem;
    position:relative;overflow:hidden;
    transition:border-color 0.3s,transform 0.3s;
    cursor:none;
  }
  .project-card::after{
    content:'';position:absolute;bottom:0;left:0;right:0;height:2px;
    background:linear-gradient(to right,var(--cyan),var(--green));
    transform:scaleX(0);transform-origin:left;
    transition:transform 0.4s ease;
  }
  .project-card:hover{border-color:var(--border-bright);transform:translateY(-4px);}
  .project-card:hover::after{transform:scaleX(1);}
  .project-cat{
    font-family:var(--mono);font-size:0.62rem;
    letter-spacing:0.25em;text-transform:uppercase;
    margin-bottom:0.8rem;color:var(--cyan);
  }
  .project-title{
    font-size:1.05rem;font-weight:700;
    margin-bottom:0.8rem;line-height:1.4;
    color:var(--text);
  }
  .project-desc{
    font-size:0.82rem;line-height:1.7;
    color:var(--text-dim);margin-bottom:1.2rem;
  }
  .project-highlight{
    font-family:var(--mono);font-size:0.72rem;
    color:var(--green);margin-bottom:1.2rem;
    padding:0.5rem 0.8rem;
    border-left:2px solid var(--green);
    background:rgba(168,255,120,0.05);
  }
  .project-tags{display:flex;flex-wrap:wrap;gap:0.4rem;margin-bottom:1.5rem;}
  .project-tag{
    font-family:var(--mono);font-size:0.6rem;
    padding:0.25rem 0.5rem;
    border:1px solid var(--border);
    border-radius:2px;color:var(--text-dim);
    letter-spacing:0.05em;
  }
  .project-link{
    font-family:var(--mono);font-size:0.7rem;
    color:var(--cyan);text-decoration:none;
    letter-spacing:0.1em;display:inline-flex;align-items:center;gap:0.4rem;
    transition:gap 0.2s;
  }
  .project-link:hover{gap:0.7rem;}

  /* contact */
  #contact{
    padding:8rem 4rem;background:var(--bg2);
    text-align:center;
  }
  .contact-inner{max-width:600px;margin:0 auto;}
  .contact-inner p{
    font-size:1rem;line-height:1.8;color:var(--text-dim);margin-bottom:3rem;
  }
  .contact-links{
    display:flex;justify-content:center;gap:1.5rem;flex-wrap:wrap;
  }

  /* footer */
  footer{
    padding:2rem 4rem;
    border-top:1px solid var(--border);
    display:flex;justify-content:space-between;align-items:center;
    position:relative;z-index:10;
  }
  footer p{
    font-family:var(--mono);font-size:0.65rem;
    color:var(--text-dim);letter-spacing:0.1em;
  }

  /* reveal animation */
  .reveal{
    opacity:0;transform:translateY(30px);
    transition:opacity 0.7s ease,transform 0.7s ease;
  }
  .reveal.visible{opacity:1;transform:translateY(0);}

  /* glitch text */
  .glitch{
    position:relative;
  }
  .glitch::before,.glitch::after{
    content:attr(data-text);
    position:absolute;left:0;top:0;width:100%;
  }
  .glitch::before{
    color:var(--cyan);
    clip-path:polygon(0 20%,100% 20%,100% 30%,0 30%);
    animation:glitch1 4s 2s infinite;
  }
  .glitch::after{
    color:var(--amber);
    clip-path:polygon(0 60%,100% 60%,100% 70%,0 70%);
    animation:glitch2 4s 2s infinite;
  }
  @keyframes glitch1{
    0%,90%,100%{transform:translate(0);}
    92%{transform:translate(-3px,1px);}
    94%{transform:translate(3px,-1px);}
    96%{transform:translate(-2px,2px);}
    98%{transform:translate(2px,-2px);}
  }
  @keyframes glitch2{
    0%,90%,100%{transform:translate(0);}
    93%{transform:translate(3px,1px);}
    95%{transform:translate(-3px,-1px);}
    97%{transform:translate(2px,2px);}
    99%{transform:translate(-2px,-2px);}
  }

  /* terminal block */
  .terminal{
    background:#060a0f;
    border:1px solid var(--border);
    border-radius:4px;
    padding:1.5rem;
    font-family:var(--mono);font-size:0.78rem;
    line-height:1.8;
    position:relative;overflow:hidden;
    margin-top:2rem;
  }
  .terminal-bar{
    position:absolute;top:0;left:0;right:0;
    height:2rem;background:var(--bg3);
    border-bottom:1px solid var(--border);
    display:flex;align-items:center;gap:0.4rem;padding:0 0.8rem;
  }
  .terminal-dot{
    width:9px;height:9px;border-radius:50%;
  }
  .terminal-body{padding-top:2.5rem;}
  .t-cmd{color:var(--cyan);}
  .t-out{color:var(--text-dim);}
  .t-hi{color:var(--green);}
  .t-amber{color:var(--amber);}

  @media(max-width:768px){
    nav{padding:1rem 1.5rem;}
    .nav-links{display:none;}
    #hero{padding:7rem 1.5rem 3rem;}
    #about,#skills,#projects,#contact{padding:5rem 1.5rem;}
    .about-grid{grid-template-columns:1fr;}
    footer{flex-direction:column;gap:0.5rem;text-align:center;padding:1.5rem;}
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>
<canvas id="bg-canvas"></canvas>

<nav>
  <div class="nav-logo">TK_015</div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </div>
</nav>

<section id="hero">
  <div class="hero-tag">// Data Engineer · ML Engineer · USC '25</div>
  <h1 class="hero-name glitch" data-text="Tushar">
    Tushar<br/><span>Kaushik.</span>
  </h1>
  <div class="hero-typewriter">
    <span id="type-text"></span><span class="cursor-blink"></span>
  </div>
  <div class="hero-cta">
    <a href="https://www.linkedin.com/in/tushar-kaushik-493a8115a/" target="_blank" class="btn btn-primary">↗ LinkedIn</a>
    <a href="mailto:kaushiktk015@gmail.com" class="btn btn-ghost">✉ Get in Touch</a>
    <a href="#projects" class="btn btn-ghost">↓ View Work</a>
  </div>
  <div class="hero-scroll">
    <div class="hero-scroll-line"></div>
    SCROLL TO EXPLORE
  </div>
</section>

<section id="about">
  <div class="section-header reveal">
    <span class="section-num">01 /</span>
    <h2 class="section-title">About</h2>
    <div class="section-line"></div>
  </div>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>I'm a passionate engineer with a strong foundation in <strong>Data Engineering, Data Science, Machine Learning, and NLP</strong>, driven to turn raw data into actionable insights and reliable systems.</p>
      <p>Currently completing my <strong>MS in Applied Data Science at USC</strong>, I specialize in building end-to-end data pipelines, deploying ML models at scale, and designing cloud-native solutions that create measurable business impact.</p>
      <p>Based in <strong>Los Angeles, CA</strong> — open to full-time roles in Data Engineering, ML Engineering, and Analytics Engineering.</p>
      <p>📧 <a href="mailto:kaushiktk015@gmail.com">kaushiktk015@gmail.com</a></p>

      <div class="terminal">
        <div class="terminal-bar">
          <div class="terminal-dot" style="background:#ff5f56;"></div>
          <div class="terminal-dot" style="background:#ffbd2e;"></div>
          <div class="terminal-dot" style="background:#27c93f;"></div>
        </div>
        <div class="terminal-body">
          <div><span class="t-cmd">$</span> <span class="t-out">cat profile.json</span></div>
          <div class="t-out">{</div>
          <div class="t-out">&nbsp;&nbsp;<span class="t-hi">"education"</span>: <span class="t-amber">"MS Applied Data Science, USC"</span>,</div>
          <div class="t-out">&nbsp;&nbsp;<span class="t-hi">"focus"</span>: <span class="t-amber">"Data Eng · ML · NLP · Cloud"</span>,</div>
          <div class="t-out">&nbsp;&nbsp;<span class="t-hi">"cloud"</span>: <span class="t-amber">["Azure", "GCP", "AWS"]</span>,</div>
          <div class="t-out">&nbsp;&nbsp;<span class="t-hi">"status"</span>: <span style="color:var(--green);">"Open to opportunities ✓"</span></div>
          <div class="t-out">}</div>
          <div style="margin-top:0.5rem;"><span class="t-cmd">$ █</span></div>
        </div>
      </div>
    </div>

    <div class="stats-grid reveal">
      <div class="stat-card">
        <span class="stat-num" data-count="100">0</span>
        <span class="stat-label">GB+ Data processed in pipelines</span>
      </div>
      <div class="stat-card">
        <span class="stat-num" data-count="22">0</span>
        <span class="stat-label">% lower hallucination rate (Claude vs GPT-4o)</span>
      </div>
      <div class="stat-card">
        <span class="stat-num" data-count="89">0</span>
        <span class="stat-label">F1 Score — ECG Anomaly Detection</span>
      </div>
      <div class="stat-card">
        <span class="stat-num" data-count="18">0</span>
        <span class="stat-label">% RMSE reduction via AutoML on Vertex AI</span>
      </div>
    </div>
  </div>
</section>

<section id="skills">
  <div class="skills-inner">
    <div class="section-header reveal">
      <span class="section-num">02 /</span>
      <h2 class="section-title">Tech Stack</h2>
      <div class="section-line"></div>
    </div>
    <div class="skill-categories reveal">
      <div>
        <div class="skill-cat-label">// Cloud & Data Engineering</div>
        <div class="skill-chips">
          <span class="chip highlight">Azure Data Factory</span>
          <span class="chip highlight">Databricks</span>
          <span class="chip highlight">Delta Lake</span>
          <span class="chip highlight">PySpark</span>
          <span class="chip highlight">GCP Vertex AI</span>
          <span class="chip">Kubeflow</span>
          <span class="chip">BigQuery</span>
          <span class="chip">Cloud Run</span>
          <span class="chip">AWS</span>
          <span class="chip">Terraform</span>
          <span class="chip">Unity Catalog</span>
          <span class="chip">Airflow</span>
        </div>
      </div>
      <div>
        <div class="skill-cat-label">// Machine Learning & AI</div>
        <div class="skill-chips">
          <span class="chip highlight">PyTorch</span>
          <span class="chip highlight">TensorFlow</span>
          <span class="chip highlight">scikit-learn</span>
          <span class="chip highlight">XGBoost</span>
          <span class="chip">LlamaIndex</span>
          <span class="chip">CrewAI</span>
          <span class="chip">AutoGen</span>
          <span class="chip">MLflow</span>
          <span class="chip">SHAP</span>
          <span class="chip">Transformers</span>
          <span class="chip">Hugging Face</span>
          <span class="chip">DeepEval</span>
        </div>
      </div>
      <div>
        <div class="skill-cat-label">// Programming & DevOps</div>
        <div class="skill-chips">
          <span class="chip highlight">Python</span>
          <span class="chip highlight">SQL</span>
          <span class="chip">FastAPI</span>
          <span class="chip">Flask</span>
          <span class="chip">Docker</span>
          <span class="chip">Git</span>
          <span class="chip">Linux</span>
          <span class="chip">Cloud Build</span>
          <span class="chip">CI/CD</span>
        </div>
      </div>
      <div>
        <div class="skill-cat-label">// Analytics & BI</div>
        <div class="skill-chips">
          <span class="chip highlight">Power BI</span>
          <span class="chip highlight">Tableau</span>
          <span class="chip">pandas</span>
          <span class="chip">NumPy</span>
          <span class="chip">Matplotlib</span>
          <span class="chip">Seaborn</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="projects">
  <div class="section-header reveal">
    <span class="section-num">03 /</span>
    <h2 class="section-title">Featured Projects</h2>
    <div class="section-line"></div>
  </div>
  <div class="projects-filter reveal">
    <button class="filter-btn active" data-filter="all">All</button>
    <button class="filter-btn" data-filter="ml">ML / AI</button>
    <button class="filter-btn" data-filter="de">Data Engineering</button>
    <button class="filter-btn" data-filter="analytics">Analytics</button>
  </div>
  <div class="projects-grid" id="projects-grid">

    <div class="project-card reveal" data-category="ml">
      <div class="project-cat">// ML · Deep Learning</div>
      <div class="project-title">ECG Anomaly Detection — LSTM Autoencoder</div>
      <div class="project-desc">Trained a 2-layer LSTM Autoencoder in PyTorch on ECG5000 to detect abnormal cardiac rhythms via reconstruction error. Ran 6 MLflow experiments across latent dimensions.</div>
      <div class="project-highlight">↑ 0.89 F1 · 0.93 ROC-AUC · 14% lower false positive rate</div>
      <div class="project-tags">
        <span class="project-tag">PyTorch</span><span class="project-tag">MLflow</span>
        <span class="project-tag">SHAP</span><span class="project-tag">FastAPI</span>
        <span class="project-tag">GCP Cloud Run</span>
      </div>
      <a href="https://github.com/tkaushik015/ECG-Anomaly-Detection" target="_blank" class="project-link">View on GitHub →</a>
    </div>

    <div class="project-card reveal" data-category="ml">
      <div class="project-cat">// RAG · Multi-Agent · LLM</div>
      <div class="project-title">GenFinance: Multi-Agent RAG for Financial Analysis</div>
      <div class="project-desc">Built a multi-agent RAG pipeline using LlamaIndex, CrewAI, and AutoGen over SEC filings. Benchmarked GPT-4o vs Claude Sonnet on 50 chart interpretation tasks.</div>
      <div class="project-highlight">↑ Cut analysis time from ~3h to under 25 min per report</div>
      <div class="project-tags">
        <span class="project-tag">LlamaIndex</span><span class="project-tag">CrewAI</span>
        <span class="project-tag">AutoGen</span><span class="project-tag">DeepEval</span>
        <span class="project-tag">Claude Sonnet</span>
      </div>
      <a href="https://github.com/tkaushik015/GenFinance-Multi-Agent-RAG-System-for-Financial-Document-Analysis" target="_blank" class="project-link">View on GitHub →</a>
    </div>

    <div class="project-card reveal" data-category="ml">
      <div class="project-cat">// MLOps · GCP · Kubeflow</div>
      <div class="project-title">BabyWeight Predictor — End-to-End MLOps on Vertex AI</div>
      <div class="project-desc">Compared BQML and AutoML on GCP Vertex AI Pipelines. Deployed winning model with blue/green strategy and automated retraining via Cloud Build CI/CD.</div>
      <div class="project-highlight">↑ 18% RMSE reduction · Deployment cycle cut to under 35 min</div>
      <div class="project-tags">
        <span class="project-tag">Vertex AI</span><span class="project-tag">Kubeflow</span>
        <span class="project-tag">BigQuery ML</span><span class="project-tag">Terraform</span>
        <span class="project-tag">Docker</span>
      </div>
      <a href="https://github.com/tkaushik015/CloudML-Engine-End-to-End-MLOps-Pipeline-on-GCP-Vertex-AI-Kubeflow-" target="_blank" class="project-link">View on GitHub →</a>
    </div>

    <div class="project-card reveal" data-category="de">
      <div class="project-cat">// Azure · ETL · Delta Lake</div>
      <div class="project-title">NYC Taxi Data Engineering Pipeline</div>
      <div class="project-desc">Built a production ETL pipeline for 100GB+ taxi data using ADF, Databricks, and Delta Lake. Implemented Bronze → Silver → Gold medallion architecture for BI-ready datasets.</div>
      <div class="project-highlight">↑ 100GB+ data processed with medallion architecture</div>
      <div class="project-tags">
        <span class="project-tag">Azure Data Factory</span><span class="project-tag">Databricks</span>
        <span class="project-tag">Delta Lake</span><span class="project-tag">PySpark</span>
      </div>
      <a href="https://github.com/tkaushik015/NYC-TAXi-DataEngineering-Project" target="_blank" class="project-link">View on GitHub →</a>
    </div>

    <div class="project-card reveal" data-category="de">
      <div class="project-cat">// Azure · Enterprise · Governance</div>
      <div class="project-title">Azure End-to-End Enterprise Data Pipeline</div>
      <div class="project-desc">Designed an enterprise-scale pipeline with ADF, Databricks, Delta Lake, Unity Catalog, and Power BI for incremental ingestion, governance, and scalable analytics.</div>
      <div class="project-highlight">↑ Enterprise-grade governance with Unity Catalog</div>
      <div class="project-tags">
        <span class="project-tag">ADF</span><span class="project-tag">Unity Catalog</span>
        <span class="project-tag">Power BI</span><span class="project-tag">Delta Lake</span>
      </div>
      <a href="https://github.com/tkaushik015/Enterprise-Data-Governance-and-Analytics-Framework/blob/main/README.md" target="_blank" class="project-link">View on GitHub →</a>
    </div>

    <div class="project-card reveal" data-category="analytics">
      <div class="project-cat">// Tableau · Analytics · BI</div>
      <div class="project-title">Adidas Sales Performance Analytics</div>
      <div class="project-desc">Designed interactive Tableau dashboards to uncover KPIs, sales trends, regional insights, and business intelligence for data-driven decision making.</div>
      <div class="project-highlight">↑ KPI dashboards for executive decision making</div>
      <div class="project-tags">
        <span class="project-tag">Tableau</span><span class="project-tag">BI</span>
        <span class="project-tag">KPI Analysis</span><span class="project-tag">Data Viz</span>
      </div>
      <a href="https://github.com/tkaushik015/Adidas-Sales-Performance-Analytics-Insights-Driven-Decision-Making-with-Tableau" target="_blank" class="project-link">View on GitHub →</a>
    </div>

  </div>
</section>

<section id="contact">
  <div class="contact-inner">
    <div class="section-header reveal" style="justify-content:center;text-align:center;">
      <span class="section-num">04 /</span>
      <h2 class="section-title">Let's Connect</h2>
    </div>
    <p class="reveal">Currently seeking full-time roles in Data Engineering, ML Engineering, and Analytics Engineering. I'm always open to interesting projects, collaborations, and conversations.</p>
    <div class="contact-links reveal">
      <a href="mailto:kaushiktk015@gmail.com" class="btn btn-primary">✉ Send Email</a>
      <a href="https://www.linkedin.com/in/tushar-kaushik-493a8115a/" target="_blank" class="btn btn-ghost">↗ LinkedIn</a>
      <a href="https://github.com/tkaushik015" target="_blank" class="btn btn-ghost">↗ GitHub</a>
    </div>
  </div>
</section>

<footer>
  <p>© 2025 Tushar Kaushik</p>
  <p>Built with ♥ in Los Angeles, CA</p>
  <p style="color:var(--cyan);">OPEN TO WORK</p>
</footer>

<script>
/* custom cursor */
const cursor=document.getElementById('cursor');
const ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  cursor.style.left=mx+'px';cursor.style.top=my+'px';
});
function animRing(){
  rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;
  ring.style.left=rx+'px';ring.style.top=ry+'px';
  requestAnimationFrame(animRing);
}
animRing();
document.querySelectorAll('a,button,.chip,.project-card,.stat-card,.filter-btn').forEach(el=>{
  el.addEventListener('mouseenter',()=>{
    cursor.style.width='18px';cursor.style.height='18px';
    ring.style.width='50px';ring.style.height='50px';
    ring.style.opacity='0.3';
  });
  el.addEventListener('mouseleave',()=>{
    cursor.style.width='10px';cursor.style.height='10px';
    ring.style.width='36px';ring.style.height='36px';
    ring.style.opacity='0.5';
  });
});

/* particle canvas */
const canvas=document.getElementById('bg-canvas');
const ctx=canvas.getContext('2d');
let W,H,particles=[];
function resize(){W=canvas.width=window.innerWidth;H=canvas.height=window.innerHeight;}
resize();window.addEventListener('resize',resize);
class Particle{
  constructor(){this.reset();}
  reset(){
    this.x=Math.random()*W;
    this.y=Math.random()*H;
    this.vx=(Math.random()-0.5)*0.3;
    this.vy=(Math.random()-0.5)*0.3;
    this.r=Math.random()*1.5+0.3;
    this.a=Math.random()*0.5+0.1;
    this.pulse=Math.random()*Math.PI*2;
  }
  update(){
    this.x+=this.vx;this.y+=this.vy;
    this.pulse+=0.02;
    if(this.x<0||this.x>W||this.y<0||this.y>H)this.reset();
  }
  draw(){
    const alpha=this.a*(0.6+0.4*Math.sin(this.pulse));
    ctx.beginPath();ctx.arc(this.x,this.y,this.r,0,Math.PI*2);
    ctx.fillStyle=`rgba(0,245,212,${alpha})`;ctx.fill();
  }
}
for(let i=0;i<120;i++)particles.push(new Particle());

function drawConnections(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      const dx=particles[i].x-particles[j].x;
      const dy=particles[i].y-particles[j].y;
      const d=Math.sqrt(dx*dx+dy*dy);
      if(d<90){
        const a=(1-d/90)*0.15;
        ctx.beginPath();
        ctx.moveTo(particles[i].x,particles[i].y);
        ctx.lineTo(particles[j].x,particles[j].y);
        ctx.strokeStyle=`rgba(0,245,212,${a})`;
        ctx.lineWidth=0.5;ctx.stroke();
      }
    }
  }
}

function animCanvas(){
  ctx.clearRect(0,0,W,H);
  particles.forEach(p=>{p.update();p.draw();});
  drawConnections();
  requestAnimationFrame(animCanvas);
}
animCanvas();

/* typewriter */
const phrases=[
  'Building scalable data pipelines on Azure & GCP',
  'Deploying ML models with MLflow & Vertex AI',
  'Engineering RAG systems with LlamaIndex & CrewAI',
  'Turning raw data into actionable insights',
  'MS Applied Data Science @ USC',
];
let pi=0,ci=0,del=false;
const typeEl=document.getElementById('type-text');
function typeStep(){
  const phrase=phrases[pi];
  if(!del){
    typeEl.textContent=phrase.substring(0,ci);
    ci++;
    if(ci>phrase.length){del=true;setTimeout(typeStep,1800);return;}
  }else{
    typeEl.textContent=phrase.substring(0,ci);
    ci--;
    if(ci<0){del=false;pi=(pi+1)%phrases.length;ci=0;setTimeout(typeStep,400);return;}
  }
  setTimeout(typeStep,del?40:60);
}
setTimeout(typeStep,1200);

/* reveal on scroll */
const reveals=document.querySelectorAll('.reveal');
const observer=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      /* count-up for stat numbers */
      const numEl=e.target.querySelector('.stat-num[data-count]');
      if(numEl&&!numEl.dataset.counted){
        numEl.dataset.counted='1';
        const target=+numEl.dataset.count;
        let curr=0;
        const inc=target/60;
        const step=()=>{
          curr=Math.min(curr+inc,target);
          numEl.textContent=Math.round(curr)+(target>=89?'%':'+');
          if(curr<target)requestAnimationFrame(step);
        };
        step();
      }
    }
  });
},{threshold:0.15});
reveals.forEach(r=>observer.observe(r));

/* project filter */
document.querySelectorAll('.filter-btn').forEach(btn=>{
  btn.addEventListener('click',()=>{
    document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
    btn.classList.add('active');
    const filter=btn.dataset.filter;
    document.querySelectorAll('.project-card').forEach(card=>{
      if(filter==='all'||card.dataset.category===filter){
        card.style.display='block';
      }else{
        card.style.display='none';
      }
    });
  });
});

/* chip hover shimmer stagger */
document.querySelectorAll('.chip').forEach((chip,i)=>{
  chip.style.animationDelay=`${i*0.06}s`;
});
</script>
</body>
</html>
