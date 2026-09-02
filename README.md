<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Crypto Edge — Trade with precision</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #0a0d12;
    --panel: #10141b;
    --panel-2: #151a23;
    --line: #232a36;
    --text: #eef1f5;
    --muted: #7c8697;
    --mint: #35e0a1;
    --mint-dim: #1c8f68;
    --red: #ff5c72;
    --gold: #e8b95f;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Manrope', sans-serif;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  .mono{font-family:'JetBrains Mono', monospace;}
  a{color:inherit; text-decoration:none;}
  .wrap{max-width:1180px; margin:0 auto; padding:0 32px;}

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important;}
  }

  /* ---------- Ticker strip ---------- */
  .ticker-bar{
    background:var(--panel);
    border-bottom:1px solid var(--line);
    overflow:hidden;
    white-space:nowrap;
    position:relative;
    height:38px;
    display:flex;
    align-items:center;
  }
  .ticker-track{
    display:inline-flex;
    animation: scroll-left 32s linear infinite;
  }
  @keyframes scroll-left{
    from{transform:translateX(0);}
    to{transform:translateX(-50%);}
  }
  .tick{
    display:inline-flex;
    align-items:center;
    gap:8px;
    padding:0 22px;
    font-size:12.5px;
    color:var(--muted);
    border-right:1px solid var(--line);
  }
  .tick b{color:var(--text); font-weight:600;}
  .tick .up{color:var(--mint);}
  .tick .down{color:var(--red);}

  /* ---------- Nav ---------- */
  nav{
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:22px 0;
    border-bottom:1px solid var(--line);
  }
  .logo{
    display:flex;
    align-items:center;
    gap:10px;
    font-weight:700;
    font-size:18px;
    letter-spacing:-0.01em;
  }
  .logo-mark{
    width:26px; height:26px;
    position:relative;
  }
  .logo-mark svg{width:100%; height:100%;}
  .nav-links{
    display:flex;
    gap:34px;
    font-size:14.5px;
    color:var(--muted);
  }
  .nav-links a{transition:color .2s;}
  .nav-links a:hover{color:var(--text);}
  .nav-cta{
    display:flex;
    gap:14px;
    align-items:center;
  }
  .btn{
    padding:10px 20px;
    border-radius:7px;
    font-size:14.5px;
    font-weight:600;
    cursor:pointer;
    border:1px solid transparent;
    transition:transform .15s ease, background .2s, border-color .2s;
    display:inline-block;
  }
  .btn:active{transform:scale(0.97);}
  .btn-ghost{color:var(--text); border-color:var(--line);}
  .btn-ghost:hover{border-color:#3a4453;}
  .btn-solid{background:var(--mint); color:#06130f;}
  .btn-solid:hover{background:#4aebb4;}
  .nav-toggle{display:none;}

  /* ---------- Hero ---------- */
  .hero{
    padding:88px 0 100px;
    display:grid;
    grid-template-columns:1.05fr 0.95fr;
    gap:64px;
    align-items:center;
  }
  .eyebrow-row{
    display:flex;
    align-items:center;
    gap:10px;
    margin-bottom:26px;
    font-size:13px;
    color:var(--muted);
  }
  .pulse-dot{
    width:7px;height:7px;border-radius:50%;
    background:var(--mint);
    box-shadow:0 0 0 0 rgba(53,224,161,.6);
    animation:pulse 2s infinite;
  }
  @keyframes pulse{
    0%{box-shadow:0 0 0 0 rgba(53,224,161,.55);}
    70%{box-shadow:0 0 0 8px rgba(53,224,161,0);}
    100%{box-shadow:0 0 0 0 rgba(53,224,161,0);}
  }
  h1{
    font-size:clamp(38px, 4.6vw, 60px);
    line-height:1.06;
    font-weight:800;
    letter-spacing:-0.025em;
    margin-bottom:22px;
  }
  h1 .accent{color:var(--mint);}
  .hero-sub{
    font-size:17px;
    color:var(--muted);
    max-width:480px;
    line-height:1.6;
    margin-bottom:34px;
  }
  .hero-actions{
    display:flex;
    gap:14px;
    margin-bottom:40px;
  }
  .btn-lg{padding:14px 26px; font-size:15.5px; border-radius:9px;}
  .hero-stats{
    display:flex;
    gap:36px;
    padding-top:28px;
    border-top:1px solid var(--line);
  }
  .hstat b{
    display:block;
    font-size:22px;
    font-weight:700;
    font-family:'JetBrains Mono', monospace;
    margin-bottom:4px;
  }
  .hstat span{font-size:12.5px; color:var(--muted);}

  /* ---------- Hero panel (chart card) ---------- */
  .chart-card{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:14px;
    padding:24px;
    position:relative;
  }
  .chart-head{
    display:flex;
    justify-content:space-between;
    align-items:flex-start;
    margin-bottom:18px;
  }
  .pair-name{font-size:15px; font-weight:700;}
  .pair-sub{font-size:12px; color:var(--muted); margin-top:3px;}
  .price-now{font-family:'JetBrains Mono',monospace; font-size:26px; font-weight:700; text-align:right;}
  .price-delta{font-size:12.5px; text-align:right; color:var(--mint); margin-top:3px; font-family:'JetBrains Mono',monospace;}
  .chart-svg-wrap{width:100%; height:190px;}
  .chart-legend{
    display:flex;
    gap:18px;
    margin-top:16px;
    padding-top:16px;
    border-top:1px solid var(--line);
    font-size:12px;
    color:var(--muted);
  }
  .chart-legend b{color:var(--text); font-family:'JetBrains Mono',monospace;}

  /* ---------- Section shell ---------- */
  section{padding:96px 0;}
  .section-head{
    max-width:560px;
    margin-bottom:56px;
  }
  .section-head h2{
    font-size:clamp(28px,3vw,36px);
    font-weight:800;
    letter-spacing:-0.02em;
    line-height:1.15;
    margin-bottom:14px;
  }
  .section-head p{color:var(--muted); font-size:15.5px; line-height:1.6;}

  /* ---------- Features ---------- */
  .feat-grid{
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    border:1px solid var(--line);
    border-radius:14px;
    overflow:hidden;
  }
  .feat{
    padding:34px 30px;
    border-right:1px solid var(--line);
    border-bottom:1px solid var(--line);
    background:var(--panel);
  }
  .feat:nth-child(3n){border-right:none;}
  .feat:nth-last-child(-n+3){border-bottom:none;}
  .feat-icon{width:34px; height:34px; margin-bottom:20px;}
  .feat h3{font-size:16.5px; font-weight:700; margin-bottom:10px;}
  .feat p{font-size:14px; color:var(--muted); line-height:1.6;}

  /* ---------- Markets table ---------- */
  .market-table{
    border:1px solid var(--line);
    border-radius:14px;
    overflow:hidden;
    background:var(--panel);
  }
  .mrow{
    display:grid;
    grid-template-columns:2.2fr 1.2fr 1.2fr 1.4fr 1fr;
    align-items:center;
    padding:16px 26px;
    border-bottom:1px solid var(--line);
    font-size:13.5px;
  }
  .mrow.head{
    color:var(--muted);
    font-size:12px;
    background:var(--panel-2);
  }
  .mrow:last-child{border-bottom:none;}
  .coin-cell{display:flex; align-items:center; gap:12px;}
  .coin-dot{width:30px; height:30px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:12px; font-weight:700; font-family:'JetBrains Mono',monospace;}
  .coin-name{font-weight:600;}
  .coin-sym{color:var(--muted); font-size:12px;}
  .mono-cell{font-family:'JetBrains Mono',monospace;}
  .chg-up{color:var(--mint);}
  .chg-down{color:var(--red);}
  .mini-spark{width:90px; height:28px;}

  /* ---------- Steps ---------- */
  .steps{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:1px;
    background:var(--line);
    border:1px solid var(--line);
    border-radius:14px;
    overflow:hidden;
  }
  .step{
    background:var(--panel);
    padding:34px 30px 38px;
    position:relative;
  }
  .step-index{
    font-family:'JetBrains Mono',monospace;
    color:var(--mint-dim);
    font-size:13px;
    margin-bottom:22px;
  }
  .step h3{font-size:16.5px; font-weight:700; margin-bottom:10px;}
  .step p{font-size:14px; color:var(--muted); line-height:1.6;}

  /* ---------- Security band ---------- */
  .security{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:16px;
    padding:56px;
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:48px;
    align-items:center;
  }
  .security h2{font-size:28px; font-weight:800; margin-bottom:16px; letter-spacing:-0.02em;}
  .security p{color:var(--muted); font-size:15px; line-height:1.65; margin-bottom:26px;}
  .sec-list{display:flex; flex-direction:column; gap:14px;}
  .sec-item{display:flex; gap:12px; align-items:flex-start; font-size:14px; color:var(--text);}
  .sec-item svg{flex-shrink:0; margin-top:2px;}
  .vault-visual{
    aspect-ratio:1/1;
    max-width:280px;
    justify-self:center;
    position:relative;
  }

  /* ---------- CTA ---------- */
  .cta-band{
    text-align:center;
    padding:100px 0;
  }
  .cta-band h2{
    font-size:clamp(30px,4vw,46px);
    font-weight:800;
    letter-spacing:-0.02em;
    margin-bottom:18px;
  }
  .cta-band p{color:var(--muted); font-size:16px; margin-bottom:36px;}
  .cta-actions{display:flex; gap:14px; justify-content:center;}

  /* ---------- Footer ---------- */
  footer{
    border-top:1px solid var(--line);
    padding:56px 0 40px;
  }
  .foot-top{
    display:grid;
    grid-template-columns:1.4fr 1fr 1fr 1fr;
    gap:40px;
    margin-bottom:48px;
  }
  .foot-brand p{color:var(--muted); font-size:13.5px; line-height:1.6; margin-top:14px; max-width:260px;}
  .foot-col h4{font-size:13px; color:var(--muted); margin-bottom:16px; font-weight:600;}
  .foot-col a{display:block; font-size:14px; margin-bottom:11px; color:var(--text); opacity:.85;}
  .foot-col a:hover{color:var(--mint);}
  .foot-bottom{
    display:flex;
    justify-content:space-between;
    padding-top:26px;
    border-top:1px solid var(--line);
    font-size:12.5px;
    color:var(--muted);
  }

  /* ---------- Register modal ---------- */
  .modal-overlay{
    position:fixed; inset:0;
    background:rgba(6,8,12,0.72);
    backdrop-filter:blur(3px);
    display:flex; align-items:center; justify-content:center;
    padding:20px;
    z-index:100;
    opacity:0; pointer-events:none;
    transition:opacity .2s ease;
  }
  .modal-overlay.open{opacity:1; pointer-events:auto;}
  .modal-card{
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:16px;
    padding:34px;
    width:100%;
    max-width:400px;
    position:relative;
    transform:translateY(10px);
    transition:transform .2s ease;
  }
  .modal-overlay.open .modal-card{transform:translateY(0);}
  .modal-close{
    position:absolute; top:18px; right:18px;
    background:none; border:none; color:var(--muted);
    cursor:pointer; padding:6px;
    transition:color .15s;
  }
  .modal-close:hover{color:var(--text);}
  .modal-head{
    display:flex; align-items:flex-start; gap:12px;
    margin-bottom:26px;
  }
  .modal-head h3{font-size:19px; font-weight:700; margin-bottom:4px;}
  .modal-head p{font-size:13.5px; color:var(--muted);}
  .field{margin-bottom:16px;}
  .field label{
    display:block; font-size:13px; color:var(--muted);
    margin-bottom:7px;
  }
  .field input{
    width:100%;
    background:var(--panel-2);
    border:1px solid var(--line);
    border-radius:8px;
    padding:11px 13px;
    font-size:14.5px;
    color:var(--text);
    font-family:'Manrope', sans-serif;
    transition:border-color .15s;
  }
  .field input:focus{outline:none; border-color:var(--mint);}
  .field input.invalid{border-color:var(--red);}
  .field-err{
    display:block;
    font-size:12px;
    color:var(--red);
    margin-top:6px;
    min-height:0;
  }
  .check-row{
    display:flex; align-items:flex-start; gap:10px;
    font-size:13px; color:var(--muted);
    margin-bottom:4px; cursor:pointer;
    line-height:1.5;
  }
  .check-row input{margin-top:3px; accent-color:var(--mint);}
  .check-row a{color:var(--text); text-decoration:underline;}
  .modal-foot{
    text-align:center; font-size:13px; color:var(--muted);
    margin-top:18px;
  }
  .modal-foot a{color:var(--mint); font-weight:600;}
  .success-view{display:none; text-align:center; padding:8px 0;}
  .success-view.show{display:block;}
  #formView.hide{display:none;}
  .success-icon{
    width:56px; height:56px; border-radius:50%;
    background:rgba(53,224,161,0.12);
    display:flex; align-items:center; justify-content:center;
    margin:0 auto 20px;
  }
  .success-view h3{font-size:19px; font-weight:700; margin-bottom:10px;}
  .success-view p{font-size:14px; color:var(--muted); line-height:1.6; margin-bottom:26px;}

  /* ---------- Responsive ---------- */
  @media (max-width: 880px){
    .wrap{padding:0 20px;}
    .nav-links{display:none;}
    .hero{grid-template-columns:1fr; padding:56px 0 64px; gap:44px;}
    .hero-sub{max-width:100%;}
    .feat-grid{grid-template-columns:1fr;}
    .feat{border-right:none !important;}
    .feat:last-child{border-bottom:none !important;}
    .steps{grid-template-columns:1fr;}
    .security{grid-template-columns:1fr; padding:32px;}
    .vault-visual{order:-1; max-width:180px;}
    .mrow{grid-template-columns:1.6fr 1fr 1fr; font-size:12.5px; padding:14px 16px;}
    .mrow span:nth-child(4), .mrow span:nth-child(5){display:none;}
    .foot-top{grid-template-columns:1fr 1fr; gap:32px;}
  }
</style>
</head>
<body>

  <div class="ticker-bar">
    <div class="ticker-track" id="tickerTrack"></div>
  </div>

  <div class="wrap">
    <nav>
      <div class="logo">
        <span class="logo-mark">
          <svg viewBox="0 0 26 26" fill="none">
            <path d="M13 1L24 7V19L13 25L2 19V7L13 1Z" stroke="#35e0a1" stroke-width="1.6"/>
            <path d="M13 8L18 11V17L13 20L8 17V11L13 8Z" fill="#35e0a1"/>
          </svg>
        </span>
        Crypto Edge
      </div>
      <div class="nav-links">
        <a href="#markets">Markets</a>
        <a href="#features">Platform</a>
        <a href="#steps">Get started</a>
        <a href="#security">Security</a>
      </div>
      <div class="nav-cta">
        <a class="btn btn-ghost" href="#">Log in</a>
        <a class="btn btn-solid" href="#">Create account</a>
      </div>
    </nav>

    <section class="hero">
      <div>
        <div class="eyebrow-row">
          <span class="pulse-dot"></span>
          <span>Live order book · 180 markets</span>
        </div>
        <h1>Read the market.<br>Act on the <span class="accent">edge</span>.</h1>
        <p class="hero-sub">Crypto Edge gives you institutional-grade execution, real-time depth, and a clean interface built for people who trade every day — not just when the market moves.</p>
        <div class="hero-actions">
          <a class="btn btn-solid btn-lg" href="#">Start trading</a>
          <a class="btn btn-ghost btn-lg" href="#">View live markets</a>
        </div>
        <div class="hero-stats">
          <div class="hstat">
            <b>$2.4B</b>
            <span>Daily volume</span>
          </div>
          <div class="hstat">
            <b>40ms</b>
            <span>Median fill time</span>
          </div>
          <div class="hstat">
            <b>0.02%</b>
            <span>Maker fee</span>
          </div>
        </div>
      </div>

      <div class="chart-card">
        <div class="chart-head">
          <div>
            <div class="pair-name">BTC / USDT</div>
            <div class="pair-sub">Perpetual · 24h</div>
          </div>
          <div>
            <div class="price-now" id="livePrice">68,214.30</div>
            <div class="price-delta" id="liveDelta">▲ 2.84%</div>
          </div>
        </div>
        <div class="chart-svg-wrap">
          <svg viewBox="0 0 460 190" width="100%" height="100%" preserveAspectRatio="none">
            <defs>
              <linearGradient id="chartFill" x1="0" y1="0" x2="0" y2="1">
                <stop offset="0%" stop-color="#35e0a1" stop-opacity="0.28"/>
                <stop offset="100%" stop-color="#35e0a1" stop-opacity="0"/>
              </linearGradient>
            </defs>
            <path d="M0,140 L0,120 L25,128 L50,100 L75,112 L100,90 L125,98 L150,70 L175,84 L200,60 L225,68 L250,44 L275,58 L300,36 L325,48 L350,26 L375,40 L400,18 L425,30 L460,10 L460,190 L0,190 Z" fill="url(#chartFill)"/>
            <path d="M0,120 L25,128 L50,100 L75,112 L100,90 L125,98 L150,70 L175,84 L200,60 L225,68 L250,44 L275,58 L300,36 L325,48 L350,26 L375,40 L400,18 L425,30 L460,10" fill="none" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" id="mainLine"/>
          </svg>
        </div>
        <div class="chart-legend">
          <span>24h high <b>68,940.10</b></span>
          <span>24h low <b>65,102.44</b></span>
          <span>Vol <b>18,204 BTC</b></span>
        </div>
      </div>
    </section>
  </div>

  <div class="wrap" id="features">
    <section>
      <div class="section-head">
        <h2>Built for how traders actually work</h2>
        <p>Every part of the platform is built around speed and clarity, from order placement to portfolio review.</p>
      </div>
      <div class="feat-grid">
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><rect x="4" y="18" width="5" height="12" fill="#35e0a1"/><rect x="14.5" y="10" width="5" height="20" fill="#35e0a1"/><rect x="25" y="4" width="5" height="26" fill="#35e0a1"/></svg>
          <h3>Advanced order types</h3>
          <p>Limit, stop-limit, trailing stop, and OCO orders, with a book depth view that updates on every tick.</p>
        </div>
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><circle cx="17" cy="17" r="13" stroke="#35e0a1" stroke-width="2"/><path d="M17 9V17L22 20" stroke="#35e0a1" stroke-width="2" stroke-linecap="round"/></svg>
          <h3>Sub-second execution</h3>
          <p>A matching engine colocated across three regions keeps fills fast even during high-volatility windows.</p>
        </div>
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><path d="M17 4L28 9V17C28 23 23 28 17 30C11 28 6 23 6 17V9L17 4Z" stroke="#35e0a1" stroke-width="2"/></svg>
          <h3>Segregated custody</h3>
          <p>Client funds sit in multi-signature cold storage, separate from operating accounts, audited quarterly.</p>
        </div>
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><path d="M5 26L13 14L19 20L29 6" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
          <h3>Portfolio analytics</h3>
          <p>Track realized and unrealized P&L, exposure by asset, and historical performance in one dashboard.</p>
        </div>
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><rect x="5" y="7" width="24" height="20" rx="2" stroke="#35e0a1" stroke-width="2"/><path d="M5 13H29" stroke="#35e0a1" stroke-width="2"/></svg>
          <h3>API & automation</h3>
          <p>REST and WebSocket access with the same rate limits as the web app, so your bots trade at full speed.</p>
        </div>
        <div class="feat">
          <svg class="feat-icon" viewBox="0 0 34 34" fill="none"><path d="M17 3V6M17 28V31M3 17H6M28 17H31M7 7L9 9M25 25L27 27M27 7L25 9M9 25L7 27" stroke="#35e0a1" stroke-width="2" stroke-linecap="round"/><circle cx="17" cy="17" r="7" stroke="#35e0a1" stroke-width="2"/></svg>
          <h3>24/7 desk support</h3>
          <p>A human trading desk is reachable around the clock, not just a chatbot pointing at help articles.</p>
        </div>
      </div>
    </section>
  </div>

  <div class="wrap" id="markets">
    <section style="padding-top:0;">
      <div class="section-head">
        <h2>Markets, priced right now</h2>
        <p>A sample of pairs available on Crypto Edge. Spreads shown are indicative, not a quote.</p>
      </div>
      <div class="market-table" id="marketTable">
        <div class="mrow head">
          <span>Asset</span>
          <span>Price</span>
          <span>24h change</span>
          <span>24h volume</span>
          <span>Chart</span>
        </div>
      </div>
    </section>
  </div>

  <div class="wrap" id="steps">
    <section>
      <div class="section-head">
        <h2>From sign-up to first trade in minutes</h2>
        <p>No lengthy onboarding calls. Verify, fund, and place your first order the same day.</p>
      </div>
      <div class="steps">
        <div class="step">
          <div class="step-index mono">01</div>
          <h3>Verify your identity</h3>
          <p>A short KYC check confirms who you are and unlocks full trading and withdrawal limits.</p>
        </div>
        <div class="step">
          <div class="step-index mono">02</div>
          <h3>Fund your account</h3>
          <p>Deposit via bank transfer, card, or an existing wallet — funds are available within minutes.</p>
        </div>
        <div class="step">
          <div class="step-index mono">03</div>
          <h3>Place your first order</h3>
          <p>Use the spot or perpetual order book, set your risk, and let the engine handle execution.</p>
        </div>
      </div>
    </section>
  </div>

  <div class="wrap" id="security">
    <section>
      <div class="security">
        <div>
          <h2>Security isn't a feature here, it's the foundation</h2>
          <p>Every design decision starts from the assumption that this platform holds real money. That shows up in how funds are stored, how access is granted, and how we report on it.</p>
          <div class="sec-list">
            <div class="sec-item">
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8L6 12L14 4" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
              95% of assets held in offline, multi-signature cold storage
            </div>
            <div class="sec-item">
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8L6 12L14 4" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
              Mandatory two-factor authentication on every account
            </div>
            <div class="sec-item">
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8L6 12L14 4" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
              Independent quarterly proof-of-reserves audits
            </div>
            <div class="sec-item">
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8L6 12L14 4" stroke="#35e0a1" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
              Withdrawal allow-listing and address verification
            </div>
          </div>
        </div>
        <div class="vault-visual">
          <svg viewBox="0 0 280 280" width="100%" height="100%" fill="none">
            <circle cx="140" cy="140" r="120" stroke="#232a36" stroke-width="1.5"/>
            <circle cx="140" cy="140" r="90" stroke="#232a36" stroke-width="1.5"/>
            <circle cx="140" cy="140" r="60" stroke="#35e0a1" stroke-width="1.5" opacity="0.5"/>
            <path d="M140 40L200 66V138C200 178 175 208 140 220C105 208 80 178 80 138V66L140 40Z" stroke="#35e0a1" stroke-width="2"/>
            <path d="M120 138L134 152L164 118" stroke="#35e0a1" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
      </div>
    </section>
  </div>

  <div class="wrap">
    <section class="cta-band">
      <h2>Your next trade is one click away</h2>
      <p>Open an account in under five minutes. No hidden fees, no minimum deposit.</p>
      <div class="cta-actions">
        <a class="btn btn-solid btn-lg" href="#">Create free account</a>
        <a class="btn btn-ghost btn-lg" href="#">Talk to the desk</a>
      </div>
    </section>
  </div>

  <footer>
    <div class="wrap">
      <div class="foot-top">
        <div class="foot-brand">
          <div class="logo">
            <span class="logo-mark">
              <svg viewBox="0 0 26 26" fill="none">
                <path d="M13 1L24 7V19L13 25L2 19V7L13 1Z" stroke="#35e0a1" stroke-width="1.6"/>
                <path d="M13 8L18 11V17L13 20L8 17V11L13 8Z" fill="#35e0a1"/>
              </svg>
            </span>
            Crypto Edge
          </div>
          <p>A trading platform for spot and perpetual crypto markets, built on fast execution and clear risk controls.</p>
        </div>
        <div class="foot-col">
          <h4>Product</h4>
          <a href="#markets">Markets</a>
          <a href="#features">Platform</a>
          <a href="#">Fee schedule</a>
          <a href="#">API docs</a>
        </div>
        <div class="foot-col">
          <h4>Company</h4>
          <a href="#">About</a>
          <a href="#">Careers</a>
          <a href="#">Press</a>
          <a href="#">Blog</a>
        </div>
        <div class="foot-col">
          <h4>Legal</h4>
          <a href="#">Terms of service</a>
          <a href="#">Privacy policy</a>
          <a href="#">Risk disclosure</a>
          <a href="#">Licensing</a>
        </div>
      </div>
      <div class="foot-bottom">
        <span>© 2026 Crypto Edge. All rights reserved.</span>
        <span>Trading digital assets carries risk. Not investment advice.</span>
      </div>
    </div>
  </footer>

  <!-- ---------- Register modal ---------- -->
  <div class="modal-overlay" id="modalOverlay">
    <div class="modal-card">
      <button class="modal-close" id="modalClose" aria-label="Close">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 2L14 14M14 2L2 14" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"/></svg>
      </button>

      <div id="formView">
        <div class="modal-head">
          <span class="logo-mark">
            <svg viewBox="0 0 26 26" fill="none">
              <path d="M13 1L24 7V19L13 25L2 19V7L13 1Z" stroke="#35e0a1" stroke-width="1.6"/>
              <path d="M13 8L18 11V17L13 20L8 17V11L13 8Z" fill="#35e0a1"/>
            </svg>
          </span>
          <div>
            <h3>Create your account</h3>
            <p>Start trading in a few minutes.</p>
          </div>
        </div>

        <form id="registerForm" novalidate>
          <div class="field">
            <label for="fullName">Full name</label>
            <input type="text" id="fullName" name="fullName" placeholder="Ahmed Khan" autocomplete="name" required>
            <span class="field-err" id="err-fullName"></span>
          </div>
          <div class="field">
            <label for="email">Email address</label>
            <input type="email" id="email" name="email" placeholder="you@example.com" autocomplete="email" required>
            <span class="field-err" id="err-email"></span>
          </div>
          <div class="field">
            <label for="password">Password</label>
            <input type="password" id="password" name="password" placeholder="At least 8 characters" autocomplete="new-password" required>
            <span class="field-err" id="err-password"></span>
          </div>
          <label class="check-row">
            <input type="checkbox" id="terms" name="terms" required>
            <span>I agree to the <a href="#">Terms of Service</a> and <a href="#">Risk Disclosure</a>.</span>
          </label>
          <span class="field-err" id="err-terms"></span>

          <button type="submit" class="btn btn-solid btn-lg" style="width:100%; margin-top:6px;">Create account</button>
          <p class="modal-foot">Already have an account? <a href="#" id="switchToLogin">Log in</a></p>
        </form>
      </div>

      <div id="successView" class="success-view">
        <div class="success-icon">
          <svg width="30" height="30" viewBox="0 0 30 30" fill="none"><path d="M6 16L12 22L24 8" stroke="#35e0a1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </div>
        <h3>You're in, <span id="successName">trader</span></h3>
        <p>We sent a confirmation link to <b id="successEmail" class="mono"></b>. Verify it to activate your account.</p>
        <button class="btn btn-ghost btn-lg" style="width:100%;" id="closeSuccess">Done</button>
      </div>
    </div>
  </div>

<script>
  // ---- Live data powered by CoinGecko's free public API (no key needed) ----
  const COIN_IDS = ['bitcoin','ethereum','solana','binancecoin','ripple','cardano','avalanche-2','dogecoin','polkadot','chainlink'];
  const COIN_META = {
    bitcoin:      {s:'BTC',  name:'Bitcoin',   color:'#f7931a'},
    ethereum:     {s:'ETH',  name:'Ethereum',  color:'#8c8fdb'},
    solana:       {s:'SOL',  name:'Solana',    color:'#35e0a1'},
    binancecoin:  {s:'BNB',  name:'BNB',       color:'#e8b95f'},
    ripple:       {s:'XRP',  name:'XRP',       color:'#7c8697'},
    cardano:      {s:'ADA',  name:'Cardano',   color:'#3aa6e0'},
    'avalanche-2':{s:'AVAX', name:'Avalanche', color:'#e0435a'},
    dogecoin:     {s:'DOGE', name:'Dogecoin',  color:'#e8b95f'},
    polkadot:     {s:'DOT',  name:'Polkadot',  color:'#e0435a'},
    chainlink:    {s:'LINK', name:'Chainlink', color:'#3a6ee0'}
  };
  const MARKET_IDS = ['bitcoin','ethereum','solana','binancecoin','ripple','cardano']; // shown in the table

  const track = document.getElementById('tickerTrack');
  const table = document.getElementById('marketTable');
  const priceEl = document.getElementById('livePrice');
  const deltaEl = document.getElementById('liveDelta');
  const statusEl = document.querySelector('.eyebrow-row span:last-child');

  function fmtPrice(n){
    const decimals = n >= 1 ? 2 : 4;
    return n.toLocaleString('en-US', {minimumFractionDigits:decimals, maximumFractionDigits:decimals});
  }
  function fmtVol(n){
    if(n >= 1e9) return '$' + (n/1e9).toFixed(2) + 'B';
    if(n >= 1e6) return '$' + (n/1e6).toFixed(1) + 'M';
    return '$' + n.toLocaleString('en-US');
  }
  function sparkSvg(up){
    const pathUp = "M2,22 L14,16 L26,18 L38,8 L50,12 L62,4 L74,10 L88,2";
    const pathDown = "M2,4 L14,10 L26,7 L38,16 L50,12 L62,20 L74,15 L88,24";
    const color = up ? '#35e0a1' : '#ff5c72';
    return `<svg class="mini-spark" viewBox="0 0 90 28"><path d="${up?pathUp:pathDown}" fill="none" stroke="${color}" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>`;
  }

  async function fetchLiveData(){
    const url = `https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&ids=${COIN_IDS.join(',')}&price_change_percentage=24h`;
    const res = await fetch(url);
    if(!res.ok) throw new Error('CoinGecko request failed: ' + res.status);
    return res.json();
  }

  function renderTicker(data){
    track.innerHTML = '';
    const rows = [...data, ...data]; // duplicate for seamless scroll
    rows.forEach(c=>{
      const up = c.price_change_percentage_24h >= 0;
      const el = document.createElement('div');
      el.className = 'tick mono';
      el.innerHTML = `<b>${c.symbol.toUpperCase()}/USD</b> $${fmtPrice(c.current_price)} <span class="${up?'up':'down'}">${up?'▲':'▼'} ${Math.abs(c.price_change_percentage_24h).toFixed(2)}%</span>`;
      track.appendChild(el);
    });
  }

  function renderMarketTable(data){
    table.innerHTML = `
      <div class="mrow head">
        <span>Asset</span>
        <span>Price</span>
        <span>24h change</span>
        <span>24h volume</span>
        <span>Chart</span>
      </div>`;
    data.filter(c => MARKET_IDS.includes(c.id)).forEach(c=>{
      const meta = COIN_META[c.id];
      const up = c.price_change_percentage_24h >= 0;
      const row = document.createElement('div');
      row.className = 'mrow';
      row.innerHTML = `
        <span class="coin-cell">
          <span class="coin-dot" style="background:${meta.color}22; color:${meta.color}; border:1px solid ${meta.color}55;">${meta.s.slice(0,2)}</span>
          <span><span class="coin-name">${meta.name}</span><br><span class="coin-sym">${meta.s}/USD</span></span>
        </span>
        <span class="mono-cell">$${fmtPrice(c.current_price)}</span>
        <span class="mono-cell ${up?'chg-up':'chg-down'}">${up?'▲':'▼'} ${Math.abs(c.price_change_percentage_24h).toFixed(2)}%</span>
        <span class="mono-cell">${fmtVol(c.total_volume)}</span>
        <span>${sparkSvg(up)}</span>
      `;
      table.appendChild(row);
    });
  }

  function renderHeroPrice(data){
    const btc = data.find(c => c.id === 'bitcoin');
    if(!btc) return;
    priceEl.textContent = fmtPrice(btc.current_price);
    const up = btc.price_change_percentage_24h >= 0;
    deltaEl.textContent = `${up?'▲':'▼'} ${Math.abs(btc.price_change_percentage_24h).toFixed(2)}%`;
    deltaEl.style.color = up ? '#35e0a1' : '#ff5c72';
  }

  async function refreshAll(){
    try{
      const data = await fetchLiveData();
      renderTicker(data);
      renderMarketTable(data);
      renderHeroPrice(data);
      if(statusEl) statusEl.textContent = 'Live market data · CoinGecko';
    }catch(err){
      console.error(err);
      if(statusEl) statusEl.textContent = 'Live data unavailable — retrying…';
    }
  }

  refreshAll();
  setInterval(refreshAll, 30000); // refresh every 30s (stays within CoinGecko's free rate limit)

  // ---- Register modal: open/close ----
  const overlay = document.getElementById('modalOverlay');
  const formView = document.getElementById('formView');
  const successView = document.getElementById('successView');
  const form = document.getElementById('registerForm');

  function openModal(){
    overlay.classList.add('open');
    formView.classList.remove('hide');
    successView.classList.remove('show');
    form.reset();
    clearErrors();
    document.body.style.overflow = 'hidden';
  }
  function closeModal(){
    overlay.classList.remove('open');
    document.body.style.overflow = '';
  }
  function clearErrors(){
    ['fullName','email','password','terms'].forEach(id=>{
      document.getElementById('err-'+id).textContent = '';
      const input = document.getElementById(id);
      if(input) input.classList.remove('invalid');
    });
  }

  // Open modal from any "register" trigger button
  document.querySelectorAll('a.btn-solid, a[href="#"]').forEach(btn=>{
    const label = btn.textContent.trim().toLowerCase();
    if(label.includes('create account') || label.includes('start trading') || label.includes('create free account')){
      btn.addEventListener('click', (e)=>{ e.preventDefault(); openModal(); });
    }
  });
  document.getElementById('modalClose').addEventListener('click', closeModal);
  document.getElementById('closeSuccess').addEventListener('click', closeModal);
  overlay.addEventListener('click', (e)=>{ if(e.target === overlay) closeModal(); });
  document.addEventListener('keydown', (e)=>{ if(e.key === 'Escape' && overlay.classList.contains('open')) closeModal(); });

  const switchLink = document.getElementById('switchToLogin');
  if(switchLink){
    switchLink.addEventListener('click', (e)=>{
      e.preventDefault();
      alert('Log in flow isn\'t wired up in this preview — connect this button to your auth backend.');
    });
  }

  // ---- Form validation ----
  form.addEventListener('submit', (e)=>{
    e.preventDefault();
    clearErrors();
    let valid = true;

    const fullName = document.getElementById('fullName').value.trim();
    const email = document.getElementById('email').value.trim();
    const password = document.getElementById('password').value;
    const terms = document.getElementById('terms').checked;

    if(fullName.length < 2){
      setError('fullName', 'Enter your full name.');
      valid = false;
    }
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if(!emailPattern.test(email)){
      setError('email', 'Enter a valid email address.');
      valid = false;
    }
    if(password.length < 8){
      setError('password', 'Password must be at least 8 characters.');
      valid = false;
    }
    if(!terms){
      setError('terms', 'You must accept the terms to continue.');
      valid = false;
    }

    if(!valid) return;

    // NOTE: This demo has no backend. In production, POST { fullName, email, password }
    // to your signup API or an auth provider (e.g. Supabase, Firebase Auth, your own server)
    // instead of showing this local success state.
    document.getElementById('successName').textContent = fullName.split(' ')[0];
    document.getElementById('successEmail').textContent = email;
    formView.classList.add('hide');
    successView.classList.add('show');
  });

  function setError(id, message){
    document.getElementById('err-'+id).textContent = message;
    const input = document.getElementById(id);
    if(input) input.classList.add('invalid');
  }
</script>
</body>
</html>

