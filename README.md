
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>UtraLuna — Digital Art Commissions</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,500;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    *{box-sizing:border-box;margin:0;padding:0}
    :root{
      --bg:#0e0e12;--bg2:#16161d;--bg3:#1d1d26;
      --text:#e8e4dc;--muted:#8b8795;--accent:#c9a96e;
      --border:rgba(255,255,255,0.07);--border2:rgba(255,255,255,0.12);
    }
    body{background:var(--bg);color:var(--text);font-family:'Inter',sans-serif;font-size:15px;line-height:1.6}
    nav{display:flex;justify-content:space-between;align-items:center;padding:1.1rem 2rem;border-bottom:1px solid var(--border);position:sticky;top:0;background:var(--bg);z-index:100}
    .logo{font-family:'Lora',serif;font-size:17px;letter-spacing:.08em;color:var(--text)}
    .nav-links{display:flex;gap:1.5rem}
    .nav-links a{font-size:12px;letter-spacing:.12em;color:var(--muted);cursor:pointer;transition:color .2s;text-transform:uppercase;text-decoration:none}
    .nav-links a:hover,.nav-links a.active{color:var(--text)}
    .open-dot{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--accent);letter-spacing:.1em}
    .open-dot::before{content:'';width:7px;height:7px;border-radius:50%;background:#6fcf97;display:block}
    .page{display:none}.page.active{display:block}

    /* HOME */
    .hero{padding:3rem 2rem 2.5rem;display:flex;flex-direction:column;align-items:center;text-align:center}
    .hero-eyebrow{font-size:11px;letter-spacing:.25em;color:var(--accent);text-transform:uppercase;margin-bottom:1rem}
    .hero-name{font-family:'Lora',serif;font-size:clamp(36px,7vw,58px);font-weight:400;font-style:italic;line-height:1.1;margin-bottom:.5rem;color:var(--text)}
    .hero-name span{font-style:normal;color:var(--muted);font-size:.5em;letter-spacing:.2em;display:block;margin-bottom:.25em}
    .hero-sub{max-width:400px;font-size:13px;color:var(--muted);line-height:1.8;margin-bottom:1.75rem}
    .hero-ctas{display:flex;gap:10px;flex-wrap:wrap;justify-content:center}
    .btn-gold{padding:10px 24px;border-radius:2px;background:var(--accent);color:#0e0e12;border:none;font-size:12px;letter-spacing:.12em;text-transform:uppercase;cursor:pointer;font-weight:500;transition:opacity .2s}
    .btn-gold:hover{opacity:.85}
    .btn-ghost{padding:10px 24px;border-radius:2px;background:transparent;color:var(--text);border:1px solid var(--border2);font-size:12px;letter-spacing:.12em;text-transform:uppercase;cursor:pointer;transition:border-color .2s}
    .btn-ghost:hover{border-color:rgba(255,255,255,.3)}
    .home-grid{display:grid;grid-template-columns:repeat(3,1fr);border-top:1px solid var(--border)}
    .home-tile{padding:1.5rem;border-right:1px solid var(--border);cursor:pointer;transition:background .2s}
    .home-tile:last-child{border-right:none}
    .home-tile:hover{background:var(--bg2)}
    .tile-sym{font-size:10px;color:var(--accent);margin-bottom:.5rem;letter-spacing:.1em}
    .tile-title{font-family:'Lora',serif;font-size:16px;margin-bottom:.4rem;color:var(--text)}
    .tile-desc{font-size:12px;color:var(--muted);line-height:1.6}
    .tile-arrow{margin-top:1rem;font-size:16px;color:var(--accent)}
    .social-bar{display:flex;justify-content:center;gap:1.5rem;padding:1.25rem;border-top:1px solid var(--border)}
    .soc{font-size:11px;letter-spacing:.1em;color:var(--muted);text-decoration:none;transition:color .2s;text-transform:uppercase}
    .soc:hover{color:var(--text)}

    /* PRICES */
    .section-header{padding:3rem 2rem 0;max-width:700px;margin:0 auto;text-align:center}
    .sec-eyebrow{font-size:11px;letter-spacing:.25em;color:var(--accent);text-transform:uppercase;margin-bottom:.75rem}
    .sec-title{font-family:'Lora',serif;font-size:30px;font-style:italic;margin-bottom:.75rem;color:var(--text)}
    .sec-sub{font-size:13px;color:var(--muted);line-height:1.7;max-width:480px;margin:0 auto 2.5rem}
    .price-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border);margin:0 0 1px}
    .pcard{background:var(--bg);padding:1.75rem}
    .pcard-img{width:100%;aspect-ratio:3/4;background:var(--bg3);border-radius:2px;margin-bottom:1.25rem;display:flex;align-items:center;justify-content:center;overflow:hidden;position:relative}
    .pcard-img img{width:100%;height:100%;object-fit:cover;display:block}
    .pcard-img-placeholder{width:100%;height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:8px;color:var(--muted);font-size:11px;letter-spacing:.15em;text-transform:uppercase}
    .img-label{position:absolute;bottom:0;left:0;right:0;padding:1.5rem .75rem .5rem;background:linear-gradient(transparent,rgba(0,0,0,.7));font-size:10px;letter-spacing:.15em;color:rgba(255,255,255,.5);text-transform:uppercase}
    .pcard-type{font-size:10px;letter-spacing:.2em;color:var(--accent);text-transform:uppercase;margin-bottom:.5rem}
    .pcard-price{font-family:'Lora',serif;font-size:28px;margin-bottom:.25rem;color:var(--text)}
    .pcard-price sub{font-size:13px;color:var(--muted);font-family:'Inter',sans-serif}
    .pcard-desc{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:1rem}
    .pcard-extra{font-size:12px;color:var(--muted);border-top:1px solid var(--border);padding-top:.75rem}
    .pcard-extra span{color:var(--accent)}
    .addons{background:var(--bg2);padding:1.75rem;display:grid;grid-template-columns:repeat(4,1fr);gap:1rem}
    .addon{background:var(--bg3);padding:1rem;border-radius:2px;border:1px solid var(--border)}
    .addon-val{font-family:'Lora',serif;font-size:16px;color:var(--accent);margin-bottom:3px}
    .addon-label{font-size:12px;color:var(--muted)}
    .prices-note{padding:.75rem 2rem;font-size:12px;color:var(--muted);text-align:center;border-top:1px solid var(--border)}

    /* ABOUT */
    .about-wrap{max-width:720px;margin:0 auto;padding:0 2rem 4rem}
    .about-grid{display:grid;grid-template-columns:1fr 1fr;gap:2.5rem;margin-bottom:2rem;align-items:start}
    .about-text p{font-size:14px;color:var(--muted);line-height:1.9;margin-bottom:1rem}
    .about-text p b{color:var(--text);font-weight:500}
    .about-img{aspect-ratio:1;background:var(--bg3);border-radius:2px;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:8px;border:1px solid var(--border);overflow:hidden}
    .about-img img{width:100%;height:100%;object-fit:cover;display:block}
    .about-img-placeholder{display:flex;flex-direction:column;align-items:center;gap:8px;color:var(--muted);font-size:11px;letter-spacing:.1em;text-transform:uppercase}
    .chips{display:flex;flex-wrap:wrap;gap:8px;margin:1.25rem 0}
    .chip{font-size:11px;letter-spacing:.1em;text-transform:uppercase;padding:5px 12px;border:1px solid var(--border2);border-radius:1px;color:var(--muted)}
    .about-divider{border:none;border-top:1px solid var(--border);margin:1.75rem 0}
    .two-col{display:grid;grid-template-columns:1fr 1fr;gap:1rem}
    .list-box{background:var(--bg2);border:1px solid var(--border);padding:1.25rem;border-radius:2px}
    .list-box-title{font-size:10px;letter-spacing:.2em;color:var(--accent);text-transform:uppercase;margin-bottom:1rem}
    .li{font-size:13px;color:var(--muted);padding:6px 0;border-bottom:1px solid var(--border)}
    .li:last-child{border-bottom:none}
    .li::before{content:'✦ ';color:var(--accent);font-size:10px}

    /* TOS */
    .tos-wrap{max-width:640px;margin:0 auto;padding:0 2rem 4rem}
    .tos-note{background:var(--bg2);border-left:2px solid var(--accent);padding:1rem 1.25rem;font-size:13px;color:var(--muted);margin-bottom:2rem;line-height:1.7;border-radius:0 2px 2px 0}
    .tos-block{margin-bottom:1rem;border:1px solid var(--border);border-radius:2px;overflow:hidden}
    .tos-head{background:var(--bg2);padding:.9rem 1.25rem;display:flex;align-items:center;gap:10px}
    .tos-n{font-size:10px;color:var(--accent);letter-spacing:.15em;min-width:22px}
    .tos-t{font-size:14px;font-weight:500;color:var(--text)}
    .tos-body{padding:.75rem 1.25rem}
    .tli{font-size:13px;color:var(--muted);padding:5px 0;border-bottom:1px solid var(--border);line-height:1.6}
    .tli:last-child{border-bottom:none}
    .tli::before{content:'✦  ';color:var(--accent);font-size:9px}

    @media(max-width:600px){
      .home-grid,.price-cards,.addons,.two-col,.about-grid{grid-template-columns:1fr}
      .home-tile{border-right:none;border-bottom:1px solid var(--border)}
      nav{padding:.8rem 1rem}
      .nav-links{gap:1rem}
    }
  </style>
</head>
<body>

<nav><div class="logo">"UtraLuna"</div>
  <div class="logo">UtraLuna</div>
  <div class="nav-links">
    <a onclick="go('home')" id="n-home" class="active">Home</a>
    <a onclick="go('prices')" id="n-prices">Prices</a>
    <a onclick="go('about')" id="n-about">About</a>
    <a onclick="go('tos')" id="n-tos">T.O.S</a>
  </div>
  <div class="open-dot">Open</div>
</nav>

<!-- HOME -->
<div class="page active" id="p-home">
  <div class="hero">
    <div class="hero-eyebrow">✦ digital art commissions ✦</div>
    <h1 class="hero-name">
      <span>Art —</span>UtraLuna
    </h1>
    <p class="hero-sub"> Every commission is made with care and delivered with professionalism.</p>
    <div class="hero-ctas">
      <button class="btn-gold" onclick="go('prices')">View prices</button>
      <button class="btn-ghost" onclick="go('about')">About me</button>
    </div>
  </div>

  <div class="home-grid">
    <div class="home-tile" onclick="go('prices')">
      <div class="tile-sym">✦ COMISIONES</div>
      <div class="tile-title">Prices & options</div>
      <div class="tile-desc">Headshots, half body, full body — clear pricing, no surprises.</div>
      <div class="tile-arrow">→</div>
    </div>
    <div class="home-tile" onclick="go('about')">
      <div class="tile-sym">✦ SOBRE MÍ</div>
      <div class="tile-title">About me</div>
      <div class="tile-desc">Artist since 2021, always growing. Furry, anime, fanart & more.</div>
      <div class="tile-arrow">→</div>
    </div>
    <div class="home-tile" onclick="go('tos')">
      <div class="tile-sym">✦ TÉRMINOS</div>
      <div class="tile-title">Terms of service</div>
      <div class="tile-desc">Payment, process and rights — all transparent and fair.</div>
      <div class="tile-arrow">→</div>
    </div>
  </div>

  <div class="social-bar">
    <a class="soc" href="https://www.instagram.com/utraluna" target="_blank">Instagram</a>
    <a class="soc" href="https://www.tiktok.com/@utra_luna" target="_blank">TikTok</a>
    <a class="soc" href="https://x.com/utraluna" target="_blank">Twitter / X</a>
  </div>
</div>

<!-- PRICES -->
<div class="page" id="p-prices">
  <div class="section-header">
    <div class="sec-eyebrow">✦ commission prices ✦</div>
    <h2 class="sec-title">What I offer</h2>
    <p class="sec-sub">Prices may vary depending on complexity. Feel free to reach out if you're unsure which option fits your idea.</p>
  </div>

  <div class="price-cards">
    <div class="pcard">
      <div class="pcard-img">
        <!-- REEMPLAZA ESTO: <img src="headshot-ejemplo.jpg" alt="Headshot example"> -->
        <div class="pcard-img-placeholder">
          <svg width="36" height="36" viewBox="0 0 40 40" fill="none" opacity=".3"><circle cx="20" cy="15" r="8" stroke="#e8e4dc" stroke-width="1.5"/><path d="M6 36c0-7.7 6.3-14 14-14s14 6.3 14 14" stroke="#e8e4dc" stroke-width="1.5" stroke-linecap="round"/></svg>
          <div>your art here</div>
        </div>
        <div class="img-label">headshot / bust</div>
      </div>
      <div class="pcard-type">✦ headshot / bust</div>
      <div class="pcard-price">$12 <sub>USD</sub></div>
      <div class="pcard-desc">Portrait-style illustration. Great for profile pictures and character references.</div>
      <div class="pcard-extra">Extra character <span>+80%</span></div>
    </div>

    <div class="pcard" style="border:1px solid rgba(201,169,110,0.2)">
      <div class="pcard-img">
        <!-- REEMPLAZA ESTO: <img src="halfbody-ejemplo.jpg" alt="Half body example"> -->
        <div class="pcard-img-placeholder">
          <svg width="36" height="36" viewBox="0 0 40 40" fill="none" opacity=".3"><circle cx="20" cy="10" r="7" stroke="#e8e4dc" stroke-width="1.5"/><path d="M6 28c0-7.7 6.3-14 14-14s14 6.3 14 14v8" stroke="#e8e4dc" stroke-width="1.5" stroke-linecap="round"/></svg>
          <div>your art here</div>
        </div>
        <div class="img-label">half / mid body</div>
      </div>
      <div class="pcard-type">✦ half / mid body</div>
      <div class="pcard-price">$25 <sub>USD</sub></div>
      <div class="pcard-desc">Waist-up illustration with more detail, expression and pose variety.</div>
      <div class="pcard-extra">Extra character <span>+65%</span></div>
    </div>

    <div class="pcard">
      <div class="pcard-img">
        <!-- REEMPLAZA ESTO: <img src="fullbody-ejemplo.jpg" alt="Full body example"> -->
        <div class="pcard-img-placeholder">
          <svg width="36" height="36" viewBox="0 0 40 40" fill="none" opacity=".3"><circle cx="20" cy="8" r="6" stroke="#e8e4dc" stroke-width="1.5"/><path d="M10 16c0 0 2 4 10 4s10-4 10-4v18" stroke="#e8e4dc" stroke-width="1.5" stroke-linecap="round"/><path d="M16 34v-8M24 34v-8" stroke="#e8e4dc" stroke-width="1.5" stroke-linecap="round"/></svg>
          <div>your art here</div>
        </div>
        <div class="img-label">full body</div>
      </div>
      <div class="pcard-type">✦ full body</div>
      <div class="pcard-price">$40 <sub>USD</sub></div>
      <div class="pcard-desc">Head to toe — full character showcase with complete detail and pose.</div>
      <div class="pcard-extra">Extra character <span>+60%</span></div>
    </div>
  </div>

  <div class="addons">
    <div class="addon"><div class="addon-val">+$15–30</div><div class="addon-label">Detailed background</div></div>
    <div class="addon"><div class="addon-val">+$5–15</div><div class="addon-label">Complex design</div></div>
    <div class="addon"><div class="addon-val">+$15</div><div class="addon-label">Rush order</div></div>
    <div class="addon"><div class="addon-val">TBD</div><div class="addon-label">Commercial use</div></div>
  </div>
  <p class="prices-note">✦ Prices may change over time · Payment via PayPal only ✦</p>
</div>

<!-- ABOUT -->
<div class="page" id="p-about">
  <div class="section-header">
    <div class="sec-eyebrow">✦ the artist ✦</div>
    <h2 class="sec-title">About me</h2>
  </div>
  <div class="about-wrap">
    <div class="about-grid">
      <div class="about-text">
        <p>Hi, I'm <b>Lucca</b> — a digital and traditional artist. I mainly create art focused on furry characters, but I also love drawing anime, fanart, humans and exploring different fandoms.</p>
        <p>I've been taking art seriously since <b>2021</b>, constantly pushing my skills forward. On the side, I'm an 18-year-old finance student who also loves Investing.</p>
        <p>Commissions aren't just a side hustle — every piece gets my full attention and care.</p>
      </div>
      <div class="about-img">
        <!-- REEMPLAZA ESTO: <img src="profile.jpg" alt="Lucca"> -->
        <div class="about-img-placeholder">
          <svg width="40" height="40" viewBox="0 0 44 44" fill="none" opacity=".2"><circle cx="22" cy="16" r="9" stroke="#e8e4dc" stroke-width="1.5"/><path d="M6 40c0-8.8 7.2-16 16-16s16 7.2 16 16" stroke="#e8e4dc" stroke-width="1.5" stroke-linecap="round"/></svg>
          <span style="font-size:11px;letter-spacing:.1em;color:#8b8795;text-transform:uppercase">profile art</span>
        </div>
      </div>
    </div>
    <div class="chips">
      <span class="chip">Furry art</span><span class="chip">OCs</span><span class="chip">Fanart</span>
      <span class="chip">Digital art</span><span class="chip">Character design</span>
      <span class="chip">Illustration</span><span class="chip">Traditional</span>
    </div>
    <hr class="about-divider">
    <div class="two-col">
      <div class="list-box">
        <div class="list-box-title">What I draw</div>
        <div class="li">Furry characters</div>
        <div class="li">Anime-style art</div>
        <div class="li">Fanart & fandom pieces</div>
        <div class="li">Human characters</div>
        <div class="li">OC & character design</div>
      </div>
      <div class="list-box">
        <div class="list-box-title">What I don't draw</div>
        <div class="li">NSFW (for now)</div>
        <div class="li">Heavy gore</div>
        <div class="li">Hyperrealistic style</div>
        <div class="li">Mechas / complex machinery</div>
        <div class="li">Hateful or offensive content</div>
      </div>
    </div>
  </div>
</div>

<!-- TOS -->
<div class="page" id="p-tos">
  <div class="section-header">
    <div class="sec-eyebrow">✦ before ordering ✦</div>
    <h2 class="sec-title">Terms of service</h2>
  </div>
  <div class="tos-wrap">
    <div class="tos-note">By requesting a commission, you confirm you've read and agreed to all terms below. These apply to every commission, no exceptions.</div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">01</span><span class="tos-t">General</span></div><div class="tos-body"><div class="tli">These terms apply to all commissions without exception.</div><div class="tli">I reserve the right to decline if I'm not comfortable with a request.</div></div></div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">02</span><span class="tos-t">Payment</span></div><div class="tos-body"><div class="tli">Full payment before I start working — no exceptions.</div><div class="tli">Price is agreed upon before payment. No surprises.</div><div class="tli">Non-refundable once work has started.</div><div class="tli">PayPal only.</div></div></div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">03</span><span class="tos-t">Process & revisions</span></div><div class="tos-body"><div class="tli">I'll provide progress updates when needed.</div><div class="tli">Minor revisions are included.</div><div class="tli">Major changes after approval may have an additional fee.</div></div></div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">04</span><span class="tos-t">Turnaround time</span></div><div class="tos-body"><div class="tli">Depends on complexity and current workload.</div><div class="tli">Typical timeframe: 1–2 weeks.</div><div class="tli">I'll inform you of any delays.</div></div></div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">05</span><span class="tos-t">Rights & credit</span></div><div class="tos-body"><div class="tli">I may post commissioned work on my portfolio and social media.</div><div class="tli">Do not claim the artwork as your own.</div><div class="tli">Credit is always appreciated when sharing online.</div></div></div>
    <div class="tos-block"><div class="tos-head"><span class="tos-n">06</span><span class="tos-t">Refunds & cancellations</span></div><div class="tos-body"><div class="tli">No refunds once work has begun.</div><div class="tli">If I can't complete it, a full refund will be issued.</div></div></div>
  </div>
</div>

<script>
  function go(id){
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('active'));
    document.getElementById('p-'+id).classList.add('active');
    document.getElementById('n-'+id).classList.add('active');
    window.scrollTo(0,0);
  }
</script>
</body>
</html>
