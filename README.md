<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>The Builder's Gazette — Kommi Nithin</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700;1,900&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=IM+Fell+DW+Pica:ital@0;1&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}

:root{
  --ink:#111008;
  --ink2:#2d2a1e;
  --ink3:#5c5740;
  --ink4:#8a8470;
  --paper:#f5f0e8;
  --paper2:#ede8dc;
  --paper3:#e6dfd0;
  --cream:#faf7f2;
  --rule:#2d2a1e;
  --accent:#c8922a;
  --accent2:#a3722a;
  --accent-light:#f7e9cc;
  --red:#8b2020;
  --red-light:#f5e0e0;
  --col-border:rgba(45,42,30,0.25);
}

body{
  font-family:'Libre Baskerville',Georgia,serif;
  background:var(--paper);
  color:var(--ink);
  overflow-x:hidden;
}

/* noise texture overlay */
body::after{
  content:'';
  position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events:none;z-index:999;opacity:0.4;
}

/* ─── TICKER ─── */
.ticker{
  background:var(--ink);color:var(--accent-light);
  padding:7px 0;overflow:hidden;white-space:nowrap;
  font-family:'IM Fell DW Pica',serif;font-size:12px;letter-spacing:0.06em;
  border-bottom:2px solid var(--accent);
}
.ticker-inner{display:inline-block;animation:scroll-left 28s linear infinite;}
@keyframes scroll-left{0%{transform:translateX(0);}100%{transform:translateX(-50%);}}
.ticker-sep{color:var(--accent);margin:0 20px;}

/* ─── MASTHEAD ─── */
.masthead{
  background:var(--cream);
  border-bottom:1px solid var(--rule);
  position:relative;
  overflow:hidden;
}
.masthead-meta{
  display:flex;justify-content:space-between;align-items:center;
  padding:8px 36px;
  border-bottom:1px solid var(--col-border);
  font-family:'IM Fell DW Pica',serif;
  font-size:11.5px;color:var(--ink3);letter-spacing:0.04em;
}
.meta-live{
  display:inline-flex;align-items:center;gap:6px;
  color:var(--red);font-weight:700;
}
.live-dot{
  width:7px;height:7px;border-radius:50%;
  background:var(--red);
  animation:blink-dot 1.6s ease-in-out infinite;
}
@keyframes blink-dot{0%,100%{opacity:1;transform:scale(1);}50%{opacity:0.3;transform:scale(0.7);}}

.masthead-title-wrap{
  text-align:center;
  padding:22px 36px 16px;
  position:relative;
}
.edition-flag{
  display:inline-block;
  background:var(--ink);color:var(--accent-light);
  font-family:'IM Fell DW Pica',serif;
  font-size:10px;letter-spacing:0.18em;text-transform:uppercase;
  padding:3px 14px;margin-bottom:14px;
}
.title-ornament{
  font-family:'Playfair Display',serif;
  font-size:11px;color:var(--ink3);letter-spacing:0.3em;text-transform:uppercase;
  margin-bottom:6px;
}
.gazette-title{
  font-family:'Playfair Display',serif;
  font-size:clamp(56px,10vw,104px);
  font-weight:900;line-height:0.92;
  letter-spacing:-0.03em;
  color:var(--ink);
  position:relative;
  display:inline-block;
}
.gazette-title::after{
  content:'';position:absolute;
  bottom:-8px;left:0;right:0;height:4px;
  background:var(--accent);
}
.gazette-sub{
  font-family:'IM Fell DW Pica',serif;
  font-style:italic;font-size:14px;
  color:var(--ink3);letter-spacing:0.1em;
  margin-top:18px;
}
.masthead-rule-set{
  display:flex;flex-direction:column;gap:3px;
  padding:0 36px 12px;
}
.rule-thick{height:4px;background:var(--ink);}
.rule-thin{height:1px;background:var(--rule);}
.rule-accent{height:2px;background:var(--accent);}

/* ─── BYLINE STRIP ─── */
.byline-strip{
  display:flex;justify-content:space-between;align-items:center;
  padding:7px 36px;
  background:var(--paper2);
  border-bottom:2px solid var(--ink);
  font-family:'IM Fell DW Pica',serif;
  font-size:11.5px;color:var(--ink3);
  flex-wrap:wrap;gap:4px;
}

/* ─── PAGE WRAPPER ─── */
.page{max-width:1040px;margin:0 auto;padding:0 28px 80px;}

/* ─── SECTIONS ─── */
.section{padding:32px 0;border-bottom:2px solid var(--ink);}
.section-last{padding:32px 0;}

/* ─── SECTION LABEL ─── */
.section-label{
  display:flex;align-items:center;gap:0;
  margin-bottom:20px;
}
.section-label-text{
  font-family:'IM Fell DW Pica',serif;
  font-size:10.5px;font-weight:700;
  letter-spacing:0.22em;text-transform:uppercase;
  color:var(--cream);
  background:var(--ink);
  padding:5px 14px;
  white-space:nowrap;
}
.section-label-line{flex:1;height:1px;background:var(--rule);}
.section-label-accent{
  background:var(--accent);
  font-family:'IM Fell DW Pica',serif;
  font-size:10.5px;letter-spacing:0.15em;text-transform:uppercase;
  color:var(--ink);padding:5px 10px;
}

/* ─── HERO STORY ─── */
.hero-grid{
  display:grid;
  grid-template-columns:1fr 340px;
  gap:0;
  border:1px solid var(--rule);
}
.hero-main{
  padding:28px 28px 28px 0;
  border-right:1px solid var(--col-border);
}
.hero-sidebar{padding:28px 0 28px 28px;}

.kicker{
  font-family:'IM Fell DW Pica',serif;
  font-size:11px;letter-spacing:0.18em;text-transform:uppercase;
  color:var(--accent2);
  margin-bottom:10px;
}
.headline-xl{
  font-family:'Playfair Display',serif;
  font-size:clamp(32px,4.5vw,52px);
  font-weight:900;line-height:1.04;
  letter-spacing:-0.02em;color:var(--ink);
  margin-bottom:14px;
}
.headline-xl em{font-style:italic;color:var(--accent2);}
.deck{
  font-family:'Libre Baskerville',serif;
  font-size:14px;font-weight:400;font-style:italic;
  color:var(--ink2);line-height:1.65;
  border-top:1px solid var(--col-border);
  border-bottom:1px solid var(--col-border);
  padding:10px 0;margin-bottom:16px;
}
.body{
  font-family:'Libre Baskerville',serif;
  font-size:13px;line-height:1.85;
  color:var(--ink2);
  column-count:2;column-gap:24px;
  column-rule:1px solid var(--col-border);
}
.body p+p{text-indent:1.4em;}
.drop::first-letter{
  font-family:'Playfair Display',serif;
  font-size:4.8em;font-weight:900;
  float:left;line-height:0.78;
  margin:5px 7px -4px 0;
  color:var(--ink);
}

/* ─── AVATAR ─── */
.avatar-block{
  display:flex;flex-direction:column;align-items:center;
  gap:12px;margin-bottom:20px;
}
.avatar-frame{
  border:3px solid var(--ink);
  outline:1px solid var(--ink);
  outline-offset:4px;
  width:110px;height:110px;border-radius:50%;overflow:hidden;
  position:relative;
}
.avatar-frame img{width:100%;height:100%;object-fit:cover;display:block;filter:grayscale(20%) contrast(1.05);}
.avatar-name{
  font-family:'Playfair Display',serif;
  font-size:18px;font-weight:900;
  color:var(--ink);text-align:center;letter-spacing:-0.01em;
}
.avatar-title{
  font-family:'IM Fell DW Pica',serif;
  font-style:italic;font-size:12px;color:var(--ink3);
  text-align:center;letter-spacing:0.06em;
}

/* ─── SIDEBAR FACTS ─── */
.fact-rule{height:1px;background:var(--rule);margin:14px 0;}
.fact-label{
  font-family:'IM Fell DW Pica',serif;
  font-size:10px;letter-spacing:0.2em;text-transform:uppercase;
  color:var(--ink3);margin-bottom:5px;
}
.fact-value{
  font-family:'Playfair Display',serif;
  font-size:15px;font-weight:700;color:var(--ink);
}
.fact-small{
  font-family:'Libre Baskerville',serif;
  font-size:12px;color:var(--ink2);line-height:1.6;
}

/* ─── PULL QUOTE ─── */
.pull-quote{
  border-top:3px solid var(--ink);
  border-bottom:1px solid var(--ink);
  padding:14px 0;margin:16px 0;
  font-family:'Playfair Display',serif;
  font-size:16px;font-style:italic;font-weight:700;
  line-height:1.38;color:var(--ink);
}
.pull-quote.gold{border-top-color:var(--accent);color:var(--accent2);}

/* ─── TYPEWRITER ─── */
.tw-block{
  background:var(--ink);color:var(--accent-light);
  padding:10px 14px;
  font-family:'Fira Code',monospace;font-size:12px;
  letter-spacing:0.04em;
  display:flex;align-items:center;gap:8px;
}
.tw-prompt{color:var(--accent);font-weight:500;}
#tw-text::after{content:'█';animation:cur 0.85s step-end infinite;font-size:9px;}
@keyframes cur{0%,100%{opacity:1;}50%{opacity:0;}}

/* ─── STATS ROW ─── */
.stats-row{
  display:grid;grid-template-columns:repeat(5,1fr);
  border:1px solid var(--rule);
  border-bottom:2px solid var(--rule);
  background:var(--cream);
}
.stat-cell{
  padding:20px 12px 16px;
  border-right:1px solid var(--col-border);
  text-align:center;
  position:relative;
  overflow:hidden;
}
.stat-cell:last-child{border-right:none;}
.stat-num{
  font-family:'Playfair Display',serif;
  font-size:0;font-weight:900;line-height:1;
  color:var(--ink);transition:font-size 0s;
}
.stat-num.counted{font-size:38px;}
.stat-num.gold{color:var(--accent2);}
.stat-lbl{
  font-family:'IM Fell DW Pica',serif;
  font-size:10px;letter-spacing:0.18em;text-transform:uppercase;
  color:var(--ink4);margin-top:5px;
}

/* ─── THREE-COL LAYOUT ─── */
.cols-3{
  display:grid;grid-template-columns:1fr 1fr 1fr;
  border:1px solid var(--rule);
  border-top:none;
}
.cols-2{
  display:grid;grid-template-columns:2fr 1fr;
  border:1px solid var(--rule);
  border-top:none;
}
.cols-2-eq{
  display:grid;grid-template-columns:1fr 1fr;
  border:1px solid var(--rule);
  border-top:none;
}
.col{
  padding:22px 22px 26px;
  border-right:1px solid var(--col-border);
}
.col:last-child{border-right:none;}
.col-label{
  font-family:'IM Fell DW Pica',serif;
  font-size:10px;letter-spacing:0.2em;text-transform:uppercase;
  color:var(--ink);
  border-bottom:2px solid var(--ink);
  padding-bottom:6px;margin-bottom:14px;
}
.col-label.gold{border-color:var(--accent);color:var(--accent2);}
.col-headline{
  font-family:'Playfair Display',serif;
  font-size:17px;font-weight:700;line-height:1.18;
  color:var(--ink);margin-bottom:9px;letter-spacing:-0.01em;
}
.col-headline.italic{font-style:italic;}
.col-body{
  font-family:'Libre Baskerville',serif;
  font-size:12.5px;line-height:1.8;
  color:var(--ink2);
}
.col-body strong{font-weight:700;color:var(--ink);}

/* ─── TECH TAGS ─── */
.tag-list{display:flex;flex-wrap:wrap;gap:6px;margin-top:10px;}
.tag{
  font-family:'Fira Code',monospace;font-size:10.5px;
  padding:3px 9px;
  border:1px solid var(--ink);
  color:var(--ink2);letter-spacing:0.03em;
  transition:background 0.2s,color 0.2s;cursor:default;
}
.tag:hover{background:var(--ink);color:var(--accent-light);}
.tag.gold{background:var(--ink);color:var(--accent-light);border-color:var(--ink);}

/* ─── PROJECTS ─── */
.proj-entry{
  padding:14px 0;
  border-bottom:1px solid var(--col-border);
  opacity:0;transform:translateX(-16px);
  transition:opacity 0.5s ease,transform 0.5s ease;
}
.proj-entry.visible{opacity:1;transform:translateX(0);}
.proj-entry:last-child{border-bottom:none;}
.proj-rank{
  font-family:'Playfair Display',serif;
  font-size:10px;color:var(--ink4);margin-bottom:2px;
  font-style:italic;
}
.proj-name{
  font-family:'Playfair Display',serif;
  font-size:15px;font-weight:700;color:var(--ink);
  margin-bottom:4px;letter-spacing:-0.01em;
}
.proj-name a{color:inherit;text-decoration:none;}
.proj-name a:hover{color:var(--accent2);text-decoration:underline;}
.proj-desc{
  font-family:'Libre Baskerville',serif;
  font-size:12px;color:var(--ink2);line-height:1.6;
}

/* ─── BUILDING ITEMS ─── */
.build-item{
  display:flex;align-items:flex-start;gap:12px;
  padding:12px 0;border-bottom:1px solid var(--col-border);
  opacity:0;transform:translateY(12px);
  transition:opacity 0.5s ease,transform 0.5s ease;
}
.build-item.visible{opacity:1;transform:translateY(0);}
.build-item:last-child{border-bottom:none;}
.build-num{
  font-family:'Playfair Display',serif;
  font-size:22px;font-weight:900;color:var(--accent);
  line-height:1;min-width:28px;flex-shrink:0;
  margin-top:-2px;
}
.build-body{font-family:'Libre Baskerville',serif;font-size:12.5px;color:var(--ink2);line-height:1.65;}
.build-body strong{font-weight:700;color:var(--ink);}

/* ─── SKILLS RADAR / BARS ─── */
.skill-bar-wrap{margin-bottom:12px;}
.skill-bar-label{
  display:flex;justify-content:space-between;
  font-family:'IM Fell DW Pica',serif;font-size:12px;
  color:var(--ink2);margin-bottom:4px;letter-spacing:0.04em;
}
.skill-bar-track{
  height:7px;background:var(--paper3);
  border:1px solid var(--col-border);
}
.skill-bar-fill{
  height:100%;background:var(--ink);width:0%;
  transition:width 1.2s cubic-bezier(0.22,1,0.36,1);
}
.skill-bar-fill.gold{background:var(--accent);}

/* ─── SOCIAL TABLE ─── */
.social-table{width:100%;border-collapse:collapse;margin-top:10px;}
.social-table td{
  padding:9px 0;border-bottom:1px solid var(--col-border);
  font-family:'Libre Baskerville',serif;font-size:12.5px;color:var(--ink2);
  vertical-align:middle;
}
.social-table tr:last-child td{border-bottom:none;}
.social-table td:first-child{
  font-family:'IM Fell DW Pica',serif;
  font-size:10.5px;letter-spacing:0.12em;text-transform:uppercase;
  color:var(--ink3);width:70px;font-weight:700;
}
.social-table a{color:var(--accent2);text-decoration:none;}
.social-table a:hover{text-decoration:underline;}

/* ─── ACCENT BAND ─── */
.accent-band{
  background:var(--ink);
  padding:18px 36px;
  display:flex;justify-content:space-between;align-items:center;
  flex-wrap:wrap;gap:10px;
  border-top:3px solid var(--accent);
  border-bottom:3px solid var(--accent);
  position:relative;overflow:hidden;
}
.accent-band::before{
  content:'"';
  font-family:'Playfair Display',serif;
  font-size:200px;font-weight:900;
  color:rgba(200,146,42,0.06);
  position:absolute;left:-20px;top:-50px;line-height:1;
  pointer-events:none;
}
.band-headline{
  font-family:'Playfair Display',serif;
  font-size:20px;font-weight:900;font-style:italic;
  color:var(--accent-light);
}
.band-sub{
  font-family:'IM Fell DW Pica',serif;
  font-size:12px;color:var(--accent);
  letter-spacing:0.1em;text-transform:uppercase;
  text-align:right;
}

/* ─── TIMELINE ─── */
.timeline{position:relative;padding-left:28px;}
.timeline::before{
  content:'';position:absolute;left:8px;top:0;bottom:0;
  width:1px;background:var(--rule);
}
.tl-item{
  position:relative;margin-bottom:20px;
  opacity:0;transform:translateX(16px);
  transition:opacity 0.6s ease,transform 0.6s ease;
}
.tl-item.visible{opacity:1;transform:translateX(0);}
.tl-dot{
  position:absolute;left:-24px;top:4px;
  width:12px;height:12px;border-radius:50%;
  background:var(--cream);border:2px solid var(--ink);
}
.tl-dot.gold{background:var(--accent);border-color:var(--accent2);}
.tl-year{
  font-family:'IM Fell DW Pica',serif;
  font-size:10px;letter-spacing:0.15em;text-transform:uppercase;
  color:var(--ink4);margin-bottom:2px;
}
.tl-title{
  font-family:'Playfair Display',serif;
  font-size:14px;font-weight:700;color:var(--ink);margin-bottom:3px;
}
.tl-desc{
  font-family:'Libre Baskerville',serif;
  font-size:12px;color:var(--ink2);line-height:1.6;
}

/* ─── ACTIVITY GRAPH ─── */
.graph-wrap{
  border:1px solid var(--rule);
  background:var(--cream);
  padding:16px;
  margin-top:0;
}
.graph-wrap img{width:100%;display:block;border:1px solid var(--col-border);}

/* ─── FOOTER ─── */
.gazette-footer{
  background:var(--ink);
  padding:20px 36px;
  display:flex;justify-content:space-between;align-items:center;
  flex-wrap:wrap;gap:10px;
  border-top:4px solid var(--accent);
}
.footer-gazette{
  font-family:'Playfair Display',serif;
  font-size:20px;font-weight:900;color:var(--accent-light);
}
.footer-meta{
  font-family:'IM Fell DW Pica',serif;
  font-size:11px;color:var(--accent);letter-spacing:0.1em;text-align:right;
}

/* ─── SCROLL REVEAL ─── */
.reveal{
  opacity:0;transform:translateY(20px);
  transition:opacity 0.7s ease,transform 0.7s ease;
}
.reveal.visible{opacity:1;transform:translateY(0);}

/* ─── RESPONSIVE ─── */
@media(max-width:700px){
  .hero-grid,.cols-3,.cols-2,.cols-2-eq{grid-template-columns:1fr;}
  .col{border-right:none;border-bottom:1px solid var(--col-border);}
  .hero-main{border-right:none;padding:20px 0;}
  .hero-sidebar{padding:20px 0;}
  .body{column-count:1;}
  .stats-row{grid-template-columns:repeat(3,1fr);}
  .gazette-title{font-size:52px;}
  .masthead-meta,.byline-strip{padding-left:16px;padding-right:16px;}
  .page{padding:0 16px 60px;}
  .accent-band{padding:16px 20px;}
}
</style>
</head>
<body>

<!-- ─── BREAKING TICKER ─── -->
<div class="ticker">
  <div class="ticker-inner" id="ticker">
    <span>⬛ KOMMI NITHIN &mdash; AI + FULL-STACK ENGINEER, SRM UNIVERSITY-AP</span>
    <span class="ticker-sep">✦</span>
    <span>MENTOR AI UNIBOT: PRODUCTION RAG SYSTEM WITH VOICE, FILE ANALYSIS & MULTI-MODEL ROUTING</span>
    <span class="ticker-sep">✦</span>
    <span>QUANTUMRAG: DOES QUANTUM BEAT CLASSICAL RETRIEVAL? ONGOING RESEARCH</span>
    <span class="ticker-sep">✦</span>
    <span>OPEN TO COLLABORATION &bull; NithinkMahendra@gmail.com</span>
    <span class="ticker-sep">✦</span>
    <span>23 PUBLIC REPOSITORIES &bull; PULL SHARK ACHIEVEMENT UNLOCKED</span>
    <span class="ticker-sep">✦</span>
    <span>STACK: NEXT.JS · FASTAPI · PYTHON · LANGCHAIN · OLLAMA · MONGODB · TYPESCRIPT</span>
    <span class="ticker-sep">✦</span>
    <!-- duplicate for seamless loop -->
    <span>⬛ KOMMI NITHIN &mdash; AI + FULL-STACK ENGINEER, SRM UNIVERSITY-AP</span>
    <span class="ticker-sep">✦</span>
    <span>MENTOR AI UNIBOT: PRODUCTION RAG SYSTEM WITH VOICE, FILE ANALYSIS & MULTI-MODEL ROUTING</span>
    <span class="ticker-sep">✦</span>
    <span>QUANTUMRAG: DOES QUANTUM BEAT CLASSICAL RETRIEVAL? ONGOING RESEARCH</span>
    <span class="ticker-sep">✦</span>
    <span>OPEN TO COLLABORATION &bull; NithinkMahendra@gmail.com</span>
    <span class="ticker-sep">✦</span>
    <span>23 PUBLIC REPOSITORIES &bull; PULL SHARK ACHIEVEMENT UNLOCKED</span>
    <span class="ticker-sep">✦</span>
    <span>STACK: NEXT.JS · FASTAPI · PYTHON · LANGCHAIN · OLLAMA · MONGODB · TYPESCRIPT</span>
    <span class="ticker-sep">✦</span>
  </div>
</div>

<!-- ─── MASTHEAD ─── -->
<div class="masthead">
  <div class="masthead-meta">
    <span>Established 2023 &bull; SRM University-AP, Amaravati, Andhra Pradesh</span>
    <span class="meta-live"><span class="live-dot"></span> Open to Collaborate</span>
    <span>Vol. III &bull; No. 23 &bull; June 2025</span>
  </div>
  <div class="masthead-title-wrap">
    <div class="edition-flag">The Builder's Gazette</div>
    <div class="title-ornament">&#10022; Forged in Code &bull; Tempered in Intelligence &#10022;</div>
    <div class="gazette-title" id="gtitle">KOMMI NITHIN</div>
    <div class="gazette-sub">"Build Intelligently &mdash; Ship Beautifully &mdash; Think Deeply"</div>
  </div>
  <div class="masthead-rule-set">
    <div class="rule-thick"></div>
    <div class="rule-accent"></div>
    <div class="rule-thin"></div>
  </div>
</div>

<!-- ─── BYLINE STRIP ─── -->
<div class="byline-strip">
  <span>AI ENGINEER &amp; FULL-STACK DEVELOPER</span>
  <span>B.TECH CSE &bull; GRADUATING 2027</span>
  <span>github.com/KOMMINITHIN</span>
</div>

<!-- ─── PAGE ─── -->
<div class="page">

  <!-- ════ HERO SECTION ════ -->
  <div class="section" style="padding-top:28px;">
    <div class="section-label">
      <div class="section-label-text">Front Page</div>
      <div class="section-label-line"></div>
      <div class="section-label-accent">Featured</div>
    </div>

    <div class="hero-grid reveal">
      <!-- MAIN STORY -->
      <div class="hero-main">
        <div class="kicker">Profile &bull; Intelligence & Interface</div>
        <h1 class="headline-xl">
          From Amaravati to the <em>Frontier</em> of Artificial Intelligence
        </h1>
        <p class="deck">
          A third-year engineer at SRM University-AP builds production AI systems, researches quantum-enhanced retrieval, and crafts full-stack experiences that feel like magic.
        </p>
        <div class="body">
          <p class="drop">Kommi Nithin is not a typical computer science undergraduate. While most students navigate textbook exercises and assigned lab work, Nithin ships production systems — a university AI chatbot handling voice input, multi-model routing, and real-time RAG over institutional knowledge. The kind of work that takes engineers years to learn, built in semesters.</p>
          <p>His interests sit precisely at the intersection most developers never reach: the frontier where intelligence meets interface. Where a model doesn't just produce output, but where that output arrives in an experience that feels immediate, responsive, and human.</p>
          <p>The QuantumRAG project exemplifies his ambition. While the broader community debates which classical RAG architecture retrieves fastest, Nithin asks whether quantum-enhanced retrieval can outperform them all — not as a thought experiment, but as a Jupyter-backed empirical research program.</p>
          <p>Alongside the AI work, he builds full-stack products. CONART, a creative platform in TypeScript. Mailcraft, an LLM-powered email assistant. Patrol, a JavaScript project. Each a different muscle group, trained in parallel.</p>
        </div>
        <div class="tw-block" style="margin-top:20px;">
          <span class="tw-prompt">nithin@srmap:~$</span>
          <span id="tw-text"></span>
        </div>
      </div>

      <!-- SIDEBAR -->
      <div class="hero-sidebar">
        <div class="avatar-block">
          <div class="avatar-frame">
            <img src="https://avatars.githubusercontent.com/u/178875725?v=4" alt="Kommi Nithin"/>
          </div>
          <div class="avatar-name">Kommi Nithin</div>
          <div class="avatar-title">AI Engineer &amp; Full-Stack Developer</div>
        </div>

        <div class="fact-rule"></div>
        <div class="pull-quote gold">
          "I don't just learn the tools &mdash; I build with them before the ink dries."
        </div>
        <div class="fact-rule"></div>

        <div style="margin-bottom:10px;">
          <div class="fact-label">University</div>
          <div class="fact-value">SRM University-AP</div>
          <div class="fact-small">Amaravati, Andhra Pradesh</div>
        </div>
        <div class="fact-rule"></div>
        <div style="margin-bottom:10px;">
          <div class="fact-label">Degree</div>
          <div class="fact-value">B.Tech Computer Science</div>
          <div class="fact-small">Class of 2027 &bull; 3rd Year</div>
        </div>
        <div class="fact-rule"></div>
        <div style="margin-bottom:10px;">
          <div class="fact-label">Achievement</div>
          <div class="fact-value">&#9875; Pull Shark</div>
          <div class="fact-small">Open source contributor &bull; 23 public repos</div>
        </div>
        <div class="fact-rule"></div>
        <div>
          <div class="fact-label">Specialisation</div>
          <div class="fact-value">AI Systems &amp; Web</div>
          <div class="fact-small">RAG · LLM · Full-Stack · Quantum ML</div>
        </div>
      </div>
    </div>
  </div>

  <!-- ════ STATS ROW ════ -->
  <div class="stats-row reveal">
    <div class="stat-cell">
      <div class="stat-num gold" data-target="23">0</div>
      <div class="stat-lbl">Repositories</div>
    </div>
    <div class="stat-cell">
      <div class="stat-num" data-target="4">0</div>
      <div class="stat-lbl">AI Projects</div>
    </div>
    <div class="stat-cell">
      <div class="stat-num gold" data-target="3">0</div>
      <div class="stat-lbl">Years Coding</div>
    </div>
    <div class="stat-cell">
      <div class="stat-num" data-target="9">0</div>
      <div class="stat-lbl">Stars Earned</div>
    </div>
    <div class="stat-cell">
      <div class="stat-num gold">2027</div>
      <div class="stat-lbl">Graduation</div>
    </div>
  </div>

  <!-- ════ TECH + PROJECTS ════ -->
  <div class="section">
    <div class="section-label">
      <div class="section-label-text">Craft &amp; Projects</div>
      <div class="section-label-line"></div>
    </div>
    <div class="cols-3 reveal">

      <!-- TECH STACK -->
      <div class="col">
        <div class="col-label gold">The Instruments</div>
        <div class="col-headline italic">A polyglot builder across the full vertical</div>

        <div style="margin-bottom:14px;">
          <div class="fact-label" style="margin-bottom:6px;">Frontend</div>
          <div class="tag-list">
            <span class="tag gold">React</span>
            <span class="tag gold">Next.js 14</span>
            <span class="tag">TypeScript</span>
            <span class="tag">Tailwind</span>
          </div>
        </div>
        <div style="margin-bottom:14px;">
          <div class="fact-label" style="margin-bottom:6px;">AI &amp; Backend</div>
          <div class="tag-list">
            <span class="tag gold">FastAPI</span>
            <span class="tag gold">LangChain</span>
            <span class="tag">Ollama</span>
            <span class="tag">Node.js</span>
            <span class="tag">RAG</span>
          </div>
        </div>
        <div style="margin-bottom:14px;">
          <div class="fact-label" style="margin-bottom:6px;">Data &amp; Infra</div>
          <div class="tag-list">
            <span class="tag">MongoDB</span>
            <span class="tag">MySQL</span>
            <span class="tag">Docker</span>
            <span class="tag">Git</span>
          </div>
        </div>
        <div>
          <div class="fact-label" style="margin-bottom:6px;">Languages</div>
          <div class="tag-list">
            <span class="tag gold">Python</span>
            <span class="tag">Java</span>
            <span class="tag">C++</span>
            <span class="tag">JavaScript</span>
          </div>
        </div>
      </div>

      <!-- PROFICIENCY BARS -->
      <div class="col">
        <div class="col-label">Proficiency Report</div>
        <div class="col-headline">Skills assessed by depth of use</div>
        <div style="margin-top:14px;" class="skill-bars-wrap">
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>Python / AI</span><span>95%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill gold" data-w="95"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>React / Next.js</span><span>90%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill gold" data-w="90"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>TypeScript</span><span>85%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-w="85"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>FastAPI / Node</span><span>85%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-w="85"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>LangChain / RAG</span><span>88%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill gold" data-w="88"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>C++ / Java / DSA</span><span>80%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-w="80"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>MongoDB / MySQL</span><span>82%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-w="82"></div></div>
          </div>
          <div class="skill-bar-wrap">
            <div class="skill-bar-label"><span>Docker / DevOps</span><span>70%</span></div>
            <div class="skill-bar-track"><div class="skill-bar-fill" data-w="70"></div></div>
          </div>
        </div>
      </div>

      <!-- PROJECTS -->
      <div class="col">
        <div class="col-label">Featured Works</div>

        <div class="proj-entry">
          <div class="proj-rank">Report No. I &bull; AI &bull; Flagship</div>
          <div class="proj-name"><a href="https://github.com/KOMMINITHIN/MENTOR_AI_-unibot-_SRMAP" target="_blank">MENTOR AI — Unibot</a></div>
          <div class="proj-desc">Production-ready university assistant. Voice chat, file analysis, multi-model routing, user auth, admin dashboard, scalable RAG. Next.js 14 + FastAPI + Ollama.</div>
          <div class="tag-list"><span class="tag" style="font-size:10px;">Next.js 14</span><span class="tag gold" style="font-size:10px;">RAG</span><span class="tag" style="font-size:10px;">Ollama</span></div>
        </div>

        <div class="proj-entry">
          <div class="proj-rank">Report No. II &bull; Research &bull; Quantum</div>
          <div class="proj-name"><a href="https://github.com/KOMMINITHIN/QUANTUMRAG" target="_blank">QuantumRAG</a></div>
          <div class="proj-desc">Empirical research: can quantum-enhanced retrieval outperform classical RAG in speed and accuracy? A Jupyter-backed investigation.</div>
          <div class="tag-list"><span class="tag gold" style="font-size:10px;">Quantum ML</span><span class="tag" style="font-size:10px;">Research</span></div>
        </div>

        <div class="proj-entry">
          <div class="proj-rank">Report No. III &bull; Full-Stack &bull; Creative</div>
          <div class="proj-name"><a href="https://github.com/KOMMINITHIN/CONART" target="_blank">CONART</a></div>
          <div class="proj-desc">A TypeScript creative platform connecting artists and collaborators with a polished full-stack experience. 1 ⭐</div>
          <div class="tag-list"><span class="tag" style="font-size:10px;">TypeScript</span><span class="tag gold" style="font-size:10px;">Full-Stack</span></div>
        </div>

        <div class="proj-entry">
          <div class="proj-rank">Report No. IV &bull; AI &bull; Productivity</div>
          <div class="proj-name"><a href="https://github.com/KOMMINITHIN/Mailcraft" target="_blank">Mailcraft</a></div>
          <div class="proj-desc">LLM-powered email drafting assistant — smart composition that makes every message count.</div>
          <div class="tag-list"><span class="tag" style="font-size:10px;">Python</span><span class="tag gold" style="font-size:10px;">LLM</span></div>
        </div>

        <div class="proj-entry">
          <div class="proj-rank">Report No. V &bull; JavaScript &bull; Utility</div>
          <div class="proj-name"><a href="https://github.com/KOMMINITHIN/patrol" target="_blank">Patrol</a></div>
          <div class="proj-desc">A JavaScript monitoring and patrol utility. Clean, functional, built to specification.</div>
          <div class="tag-list"><span class="tag" style="font-size:10px;">JavaScript</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ════ ACCENT BAND ════ -->
  <div class="accent-band reveal">
    <div>
      <div class="band-headline">"The best time to build was yesterday. The second best time is in production by tomorrow."</div>
    </div>
    <div class="band-sub">
      Kommi Nithin &bull; Builder, Researcher, Engineer<br/>
      SRM University-AP &bull; 2025
    </div>
  </div>

  <!-- ════ JOURNEY TIMELINE + CURRENTLY BUILDING ════ -->
  <div class="section">
    <div class="section-label">
      <div class="section-label-text">Chronicle &amp; Workbench</div>
      <div class="section-label-line"></div>
    </div>
    <div class="cols-2 reveal">

      <!-- TIMELINE -->
      <div class="col">
        <div class="col-label gold">The Journey So Far</div>
        <div class="timeline">

          <div class="tl-item">
            <div class="tl-dot gold"></div>
            <div class="tl-year">2023</div>
            <div class="tl-title">Enrolled at SRM University-AP</div>
            <div class="tl-desc">B.Tech Computer Science begins. First exposure to C, Python, and the fundamentals of computing that would become the bedrock of everything that followed.</div>
          </div>

          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-year">2024 — Early</div>
            <div class="tl-title">First full-stack projects ship</div>
            <div class="tl-desc">CONART, Patrol, and Mailcraft land in public repositories. TypeScript, Node.js, and JavaScript become familiar territory. 23 repos begin accumulating.</div>
          </div>

          <div class="tl-item">
            <div class="tl-dot gold"></div>
            <div class="tl-year">2024 — Mid</div>
            <div class="tl-title">Turn toward Artificial Intelligence</div>
            <div class="tl-desc">LangChain, Ollama, FastAPI, and RAG systems become the new focus. LLM integration moves from curiosity to core competency. Mailcraft ships as the first LLM-powered product.</div>
          </div>

          <div class="tl-item">
            <div class="tl-dot gold"></div>
            <div class="tl-year">2024 — Late</div>
            <div class="tl-title">MENTOR AI Unibot enters production</div>
            <div class="tl-desc">The flagship project launches: voice chat, multi-model routing, file analysis, admin dashboard, scalable RAG over university knowledge. Production Next.js 14 + FastAPI architecture.</div>
          </div>

          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-year">2025</div>
            <div class="tl-title">QuantumRAG research commences</div>
            <div class="tl-desc">A question no one in the room is asking yet: can quantum-enhanced retrieval outperform classical RAG? The investigation begins in Jupyter. Pull Shark achievement unlocked on GitHub.</div>
          </div>

          <div class="tl-item">
            <div class="tl-dot gold"></div>
            <div class="tl-year">2027</div>
            <div class="tl-title">Graduation &amp; beyond</div>
            <div class="tl-desc">B.Tech Computer Science complete. The pipeline from idea to production will be faster, the systems smarter, and the ambitions larger. Open to what comes next.</div>
          </div>
        </div>
      </div>

      <!-- CURRENTLY BUILDING -->
      <div class="col">
        <div class="col-label">On the Workbench Now</div>
        <div class="col-headline italic">Four fronts, active simultaneously</div>
        <div style="margin-top:16px;">
          <div class="build-item">
            <div class="build-num">01</div>
            <div class="build-body"><strong>AI-powered full-stack systems</strong> — LLM integrations, voice interfaces, intelligent pipelines. Where the model is invisible and the experience is everything.</div>
          </div>
          <div class="build-item">
            <div class="build-num">02</div>
            <div class="build-body"><strong>Advanced DSA &amp; System Design</strong> — The engineering fundamentals that separate good developers from the ones who architect systems that scale to millions.</div>
          </div>
          <div class="build-item">
            <div class="build-num">03</div>
            <div class="build-body"><strong>QuantumRAG research</strong> — Pushing the boundary of what retrieval-augmented generation can achieve by borrowing from quantum computing principles.</div>
          </div>
          <div class="build-item">
            <div class="build-num">04</div>
            <div class="build-body"><strong>Open source contributions</strong> — Pull Shark earned, more meaningful contributions in the pipeline. Building in public, learning in public.</div>
          </div>
        </div>

        <div class="pull-quote" style="margin-top:24px;">
          "Every project is a lesson in what I don't know yet."
        </div>

        <div style="margin-top:20px;">
          <div class="col-label">Philosophy</div>
          <div class="col-body">
            <p>Nithin believes the best way to learn a technology is to build something real with it before finishing the tutorial. This produces rougher early work, but engineers who understand failure modes rather than just success paths.</p>
            <p style="margin-top:10px;">The combination of AI and full-stack is not accidental. An AI system without a great interface is a research demo. A great interface without intelligence is increasingly obsolete. The intersection is where the work matters.</p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- ════ ACTIVITY GRAPH ════ -->
  <div class="section reveal">
    <div class="section-label">
      <div class="section-label-text">Contribution Record</div>
      <div class="section-label-line"></div>
    </div>
    <div class="graph-wrap">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=KOMMINITHIN&theme=minimal&hide_border=true&bg_color=f5f0e8&color=111008&line=c8922a&point=2d2a1e&area=true&area_color=f7e9cc&title_color=111008" alt="GitHub activity graph — Kommi Nithin"/>
    </div>
  </div>

  <!-- ════ CONTACT + CLOSING ════ -->
  <div class="section-last">
    <div class="section-label">
      <div class="section-label-text">Contact &amp; Directories</div>
      <div class="section-label-line"></div>
    </div>
    <div class="cols-2-eq reveal">
      <div class="col">
        <div class="col-label gold">Reach Kommi Nithin</div>
        <table class="social-table">
          <tr><td>GitHub</td><td><a href="https://github.com/KOMMINITHIN" target="_blank">github.com/KOMMINITHIN</a></td></tr>
          <tr><td>LinkedIn</td><td><a href="https://www.linkedin.com/in/nithinkmahendra/" target="_blank">linkedin.com/in/nithinkmahendra</a></td></tr>
          <tr><td>Email</td><td><a href="mailto:NithinkMahendra@gmail.com">NithinkMahendra@gmail.com</a></td></tr>
          <tr><td>Instagram</td><td><a href="https://instagram.com/nithinkmahendra" target="_blank">@nithinkmahendra</a></td></tr>
          <tr><td>Discord</td><td><a href="https://discordapp.com/users/1384805285536989254" target="_blank">KOMMINITHIN</a></td></tr>
          <tr><td>LeetCode</td><td><a href="https://leetcode.com/NithinkMahendra" target="_blank">NithinkMahendra</a></td></tr>
        </table>
        <div style="margin-top:18px;background:var(--paper2);border:1px solid var(--col-border);padding:14px 16px;">
          <div class="fact-label" style="margin-bottom:6px;">Open to</div>
          <div class="tag-list">
            <span class="tag gold">Collaborations</span>
            <span class="tag">Internships</span>
            <span class="tag">Research</span>
            <span class="tag">Open Source</span>
            <span class="tag">Freelance</span>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="col-label">Closing Statement</div>
        <div class="pull-quote gold" style="font-size:15px;">
          "If you're building something ambitious at the frontier of AI and web — I want to hear about it."
        </div>
        <div class="col-body" style="margin-top:14px;">
          <p>Kommi Nithin is a third-year computer science engineer at SRM University-AP, building production AI systems and full-stack applications while the rest of the world is still deciding which framework to use.</p>
          <p style="margin-top:12px;">He is available for meaningful collaboration, research partnerships, and ambitious projects. The work speaks for itself: 23 repositories, 4 flagship AI-integrated projects, a Quantum ML research programme, and a philosophy that the best way to learn is to ship.</p>
          <p style="margin-top:12px;">Reach out. Build something worth reading about.</p>
        </div>
        <div class="tw-block" style="margin-top:16px;font-size:11px;">
          <span class="tw-prompt">status:$</span>
          <span id="tw-text-2"></span>
        </div>
      </div>
    </div>
  </div>

</div>

<!-- ─── FOOTER ─── -->
<div class="gazette-footer">
  <div class="footer-gazette">The Builder's Gazette</div>
  <div class="footer-meta">
    KOMMI NITHIN &bull; SRM UNIVERSITY-AP, AMARAVATI<br/>
    B.TECH CSE 2023–2027 &bull; ALL RIGHTS RESERVED &copy; 2025
  </div>
</div>

<script>
/* ── TYPEWRITER 1 ── */
const phrases=['building AI that reasons','crafting full-stack experiences','researching QuantumRAG','turning ideas into production systems','open to collaborate'];
let pi=0,ci=0,del=false;
const tw=document.getElementById('tw-text');
function tick(){
  const w=phrases[pi];
  if(!del){tw.textContent=w.slice(0,++ci);if(ci===w.length){del=true;setTimeout(tick,2000);return;}}
  else{tw.textContent=w.slice(0,--ci);if(ci===0){del=false;pi=(pi+1)%phrases.length;setTimeout(tick,400);return;}}
  setTimeout(tick,del?36:58);
}
setTimeout(tick,1000);

/* ── TYPEWRITER 2 ── */
const phrases2=['available · building · shipping','open to ambitious collaborations','always learning · always building'];
let pi2=0,ci2=0,del2=false;
const tw2=document.getElementById('tw-text-2');
function tick2(){
  if(!tw2)return;
  const w=phrases2[pi2];
  if(!del2){tw2.textContent=w.slice(0,++ci2);if(ci2===w.length){del2=true;setTimeout(tick2,2200);return;}}
  else{tw2.textContent=w.slice(0,--ci2);if(ci2===0){del2=false;pi2=(pi2+1)%phrases2.length;setTimeout(tick2,400);return;}}
  setTimeout(tick2,del2?40:65);
}
setTimeout(tick2,2200);

/* ── INTERSECTION OBSERVER ── */
const obs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      obs.unobserve(e.target);
    }
  });
},{threshold:0.12});

document.querySelectorAll('.reveal,.proj-entry,.build-item,.tl-item').forEach(el=>obs.observe(el));

/* ── STAGGER PROJ ENTRIES ── */
document.querySelectorAll('.proj-entry').forEach((el,i)=>{
  el.style.transitionDelay=`${i*0.1}s`;
});
document.querySelectorAll('.build-item').forEach((el,i)=>{
  el.style.transitionDelay=`${i*0.12}s`;
});
document.querySelectorAll('.tl-item').forEach((el,i)=>{
  el.style.transitionDelay=`${i*0.1}s`;
});

/* ── COUNT-UP STATS ── */
const statObs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      const el=e.target;
      const target=parseInt(el.dataset.target);
      if(!target){el.classList.add('counted');return;}
      let current=0;
      el.classList.add('counted');
      const step=Math.max(1,Math.floor(target/30));
      const timer=setInterval(()=>{
        current=Math.min(current+step,target);
        el.textContent=current;
        if(current>=target)clearInterval(timer);
      },40);
      statObs.unobserve(el);
    }
  });
},{threshold:0.5});
document.querySelectorAll('.stat-num[data-target]').forEach(el=>statObs.observe(el));

/* ── SKILL BARS ── */
const barObs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.querySelectorAll('.skill-bar-fill').forEach(bar=>{
        setTimeout(()=>{bar.style.width=bar.dataset.w+'%';},200);
      });
      barObs.unobserve(e.target);
    }
  });
},{threshold:0.3});
document.querySelectorAll('.skill-bars-wrap').forEach(el=>barObs.observe(el));

/* ── MASTHEAD TITLE STAMP-IN ── */
const gt=document.getElementById('gtitle');
if(gt){
  const text=gt.textContent;gt.textContent='';
  gt.style.opacity='1';
  let idx=0;
  const stamp=setInterval(()=>{
    gt.textContent+=text[idx];
    idx++;
    if(idx>=text.length)clearInterval(stamp);
  },80);
}
</script>
</body>
</html>
