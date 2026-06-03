# Deltamax.com
W products
cat > /mnt/user-data/outputs/delta-max.html << 'HTMLEOF'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Delta Max — Premium Store</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,700&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
:root {
  --y: #C8960C;
  --y2: #E8B84B;
  --y3: #F5D07A;
  --yg: linear-gradient(135deg,#7a5a00,#C8960C 30%,#F5D07A 55%,#C8960C 75%,#7a5a00);
  --yg2: linear-gradient(90deg,#7a5a00,#E8B84B 40%,#fff8e7 55%,#E8B84B 70%,#7a5a00);
  --matte: #1A1A1A;
  --matte2: #141414;
  --matte3: #101010;
  --card: #1E1E1E;
  --border: rgba(200,150,12,0.18);
  --border2: rgba(200,150,12,0.08);
  --text: #F0EDE8;
  --muted: #5a5550;
  --glow: rgba(200,150,12,0.3);
  --r: 20px;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  background:var(--matte);
  color:var(--text);
  font-family:'Outfit',sans-serif;
  overflow-x:hidden;
  cursor:auto;
}

/* ── GOLD TEXT UTILITY ── */
.gold {
  background: var(--yg2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ── NOISE GRAIN ── */
body::after{
  content:'';position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.75' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='.025'/%3E%3C/svg%3E");
  pointer-events:none;z-index:998;opacity:.4;
}

/* ── LOADER ── */
#loader{
  position:fixed;inset:0;background:var(--matte3);
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  z-index:9997;transition:opacity .9s ease,visibility .9s;
}
#loader.hide{opacity:0;visibility:hidden;pointer-events:none}
.load-logo{
  font-family:'Cormorant Garamond',serif;font-size:3.2rem;font-weight:700;
  letter-spacing:10px;text-transform:uppercase;
  background:var(--yg2);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  animation:loadPulse 1.6s ease infinite;
}
.load-bar{width:180px;height:1px;background:#2a2a2a;margin-top:36px;overflow:hidden;border-radius:1px}
.load-fill{height:100%;background:var(--yg2);animation:loadFill 1.9s ease forwards}
@keyframes loadPulse{0%,100%{opacity:.3}50%{opacity:1}}
@keyframes loadFill{0%{width:0}100%{width:100%}}

/* ── NAV ── */
nav{
  position:fixed;top:16px;left:50%;transform:translateX(-50%);z-index:500;
  width:calc(100% - 48px);max-width:1200px;
  padding:0 36px;height:64px;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(20,20,20,0.7);
  border:1px solid var(--border);
  border-radius:var(--r);
  backdrop-filter:blur(20px);
  transition:background .4s,box-shadow .4s;
}
nav.scrolled{
  background:rgba(16,16,16,0.95);
  box-shadow:0 8px 40px rgba(0,0,0,.6),0 0 0 1px var(--border);
}
.logo{
  font-family:'Cormorant Garamond',serif;
  font-size:1.4rem;font-weight:700;letter-spacing:5px;text-transform:uppercase;
  display:flex;align-items:center;gap:10px;
  background:var(--yg2);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.logo-dot{
  width:6px;height:6px;
  background:var(--y2);border-radius:50%;flex-shrink:0;
  animation:blink 2s ease infinite;
  -webkit-text-fill-color:initial;
}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.15}}
.nav-links{display:flex;gap:36px;list-style:none}
.nav-links a{
  color:var(--muted);font-size:.75rem;font-weight:500;
  letter-spacing:2.5px;text-transform:uppercase;
  text-decoration:none;transition:color .25s;position:relative;
}
.nav-links a::after{
  content:'';position:absolute;bottom:-3px;left:0;
  width:0;height:1px;
  background:var(--yg2);transition:width .3s;
}
.nav-links a:hover{color:var(--y2)}
.nav-links a:hover::after{width:100%}
.nav-cart{
  position:relative;background:transparent;
  border:1px solid var(--border);border-radius:10px;
  color:var(--y2);padding:8px 22px;font-family:'Outfit',sans-serif;
  font-size:.75rem;font-weight:500;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;transition:all .25s;
}
.nav-cart:hover{background:rgba(200,150,12,.1);border-color:var(--y2);box-shadow:0 0 20px var(--glow)}
.cart-badge{
  position:absolute;top:-8px;right:-8px;
  background:var(--yg);color:var(--matte3);
  font-size:.55rem;font-weight:700;
  width:18px;height:18px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  opacity:0;transition:opacity .2s;
}
.cart-badge.vis{opacity:1}

/* ── HERO ── */
.hero{
  min-height:100vh;position:relative;
  display:flex;align-items:center;
  padding:140px 60px 100px;
  overflow:hidden;
}
.orb{position:absolute;border-radius:50%;filter:blur(100px);pointer-events:none}
.orb1{
  width:700px;height:700px;
  background:radial-gradient(circle,rgba(200,150,12,.14),transparent 70%);
  right:-200px;top:-150px;
  animation:orbFloat 9s ease-in-out infinite;
}
.orb2{
  width:500px;height:500px;
  background:radial-gradient(circle,rgba(200,150,12,.07),transparent 70%);
  left:-150px;bottom:-80px;
  animation:orbFloat 12s ease-in-out infinite reverse;
}
@keyframes orbFloat{
  0%,100%{transform:translate(0,0) scale(1)}
  33%{transform:translate(40px,-50px) scale(1.06)}
  66%{transform:translate(-25px,25px) scale(.96)}
}
.hero-grid{
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(200,150,12,.035) 1px,transparent 1px),
    linear-gradient(90deg,rgba(200,150,12,.035) 1px,transparent 1px);
  background-size:80px 80px;
  mask-image:radial-gradient(ellipse 70% 70% at 60% 40%,black,transparent);
}
.hero-content{position:relative;z-index:2;max-width:780px}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:10px;
  border:1px solid var(--border);padding:6px 18px;border-radius:40px;
  font-size:.68rem;font-weight:500;letter-spacing:3px;text-transform:uppercase;
  color:var(--y2);margin-bottom:40px;
  background:rgba(200,150,12,.06);
  animation:fadeUp .8s .3s both;
}
.hero-eyebrow-dot{width:5px;height:5px;background:var(--y2);border-radius:50%;animation:blink 1.5s infinite;flex-shrink:0}
.hero h1{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(4rem,9vw,8rem);
  font-weight:700;line-height:.92;
  letter-spacing:-2px;
  margin-bottom:36px;
  animation:fadeUp .8s .5s both;
}
.hero h1 em{
  font-style:italic;
  background:var(--yg2);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.hero h1 .line2{display:block;color:rgba(240,237,232,.15)}
.hero-sub{
  font-size:1rem;color:var(--muted);line-height:1.9;
  max-width:460px;margin-bottom:52px;
  animation:fadeUp .8s .7s both;
}
.hero-actions{display:flex;gap:16px;flex-wrap:wrap;animation:fadeUp .8s .9s both}
.btn-gold{
  background:var(--yg);color:var(--matte3);border:none;
  padding:16px 44px;font-family:'Outfit',sans-serif;
  font-weight:600;font-size:.8rem;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;position:relative;overflow:hidden;transition:all .35s;
  border-radius:12px;
}
.btn-gold::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(90deg,transparent,rgba(255,255,255,.25),transparent);
  transform:translateX(-100%);transition:transform .5s;
}
.btn-gold:hover{box-shadow:0 0 50px var(--glow),0 4px 20px rgba(0,0,0,.4);transform:translateY(-2px)}
.btn-gold:hover::before{transform:translateX(100%)}
.btn-outline{
  background:transparent;color:var(--text);
  border:1px solid rgba(255,255,255,.1);
  padding:16px 44px;font-family:'Outfit',sans-serif;
  font-weight:400;font-size:.8rem;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;transition:all .3s;border-radius:12px;
}
.btn-outline:hover{border-color:var(--y);color:var(--y2);background:rgba(200,150,12,.05)}
.hero-badge{
  position:absolute;right:80px;bottom:130px;
  width:110px;height:110px;
  border:1px solid var(--border);border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  animation:spin 22s linear infinite;opacity:.5;
}
.hero-badge-text{
  font-family:'Cormorant Garamond',serif;
  font-size:.5rem;font-weight:600;letter-spacing:3px;
  text-transform:uppercase;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  text-align:center;
}
@keyframes spin{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
@keyframes fadeUp{from{opacity:0;transform:translateY(32px)}to{opacity:1;transform:translateY(0)}}

/* ── MARQUEE ── */
.marquee-wrap{
  overflow:hidden;padding:16px 0;position:relative;z-index:2;
  border-top:1px solid var(--border);border-bottom:1px solid var(--border);
  background:rgba(14,14,14,.8);
}
.marquee-track{display:flex;width:max-content;animation:marquee 20s linear infinite}
.marquee-track span{
  font-family:'Cormorant Garamond',serif;
  font-size:.85rem;font-weight:600;letter-spacing:4px;text-transform:uppercase;
  padding:0 44px;white-space:nowrap;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.marquee-track span::after{content:'✦';margin-left:44px;opacity:.3}
@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ── SECTION BASE ── */
.section{padding:120px 60px}
.s-tag{
  font-size:.62rem;font-weight:600;letter-spacing:4px;
  text-transform:uppercase;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  display:flex;align-items:center;gap:12px;margin-bottom:18px;
}
.s-tag::before{content:'';width:28px;height:1px;background:var(--y);flex-shrink:0}
.s-title{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(2.2rem,4vw,3.8rem);font-weight:700;
  letter-spacing:-1px;margin-bottom:18px;line-height:1.1;
}
.s-sub{color:var(--muted);font-size:.9rem;line-height:1.9;max-width:460px;margin-bottom:64px}

/* ── PRODUCTS ── */
.products-section{background:var(--matte2)}
.products-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(300px,1fr));
  gap:20px;
}
.p-card{
  background:var(--card);
  border:1px solid var(--border2);
  border-radius:18px;
  position:relative;overflow:hidden;
  transition:transform .4s cubic-bezier(.25,.46,.45,.94),border-color .3s,box-shadow .4s;
  cursor:pointer;
}
.p-card:hover{
  transform:translateY(-6px);
  border-color:rgba(200,150,12,.35);
  box-shadow:0 20px 60px rgba(0,0,0,.5),0 0 30px rgba(200,150,12,.08);
  z-index:2;
}
.p-card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(200,150,12,.05),transparent 60%);
  opacity:0;transition:opacity .35s;border-radius:18px;
}
.p-card:hover::before{opacity:1}
.p-img{
  height:220px;
  display:flex;align-items:center;justify-content:center;
  font-size:5rem;
  background:linear-gradient(145deg,#111,#181818);
  position:relative;overflow:hidden;
  border-radius:18px 18px 0 0;
}
.p-img-glow{
  position:absolute;inset:0;
  background:radial-gradient(circle at 50% 70%,rgba(200,150,12,.12),transparent 65%);
  opacity:0;transition:opacity .4s;
}
.p-card:hover .p-img-glow{opacity:1}
.p-tag{
  position:absolute;top:14px;left:14px;
  font-size:.58rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;
  padding:5px 12px;border-radius:20px;
  background:var(--yg);color:var(--matte3);
}
.p-body{padding:24px 24px 20px}
.p-cat{
  font-size:.62rem;font-weight:600;letter-spacing:3px;text-transform:uppercase;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  margin-bottom:8px;
}
.p-name{font-family:'Cormorant Garamond',serif;font-size:1.45rem;font-weight:700;letter-spacing:-.3px;margin-bottom:8px}
.p-desc{font-size:.8rem;color:var(--muted);line-height:1.75;margin-bottom:20px}
.p-foot{display:flex;align-items:center;justify-content:space-between}
.p-price{
  font-family:'Cormorant Garamond',serif;font-size:1.7rem;font-weight:700;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.p-btn{
  background:transparent;border:1px solid var(--border);border-radius:10px;
  color:var(--y2);padding:8px 20px;font-family:'Outfit',sans-serif;
  font-size:.72rem;font-weight:500;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;transition:all .25s;
}
.p-btn:hover{background:var(--yg);color:var(--matte3);border-color:transparent;box-shadow:0 4px 20px var(--glow)}

/* ── STATS ── */
.stats-section{
  background:var(--matte3);
  padding:80px 60px;
  display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:40px;
  border-top:1px solid var(--border);border-bottom:1px solid var(--border);
}
.stat{text-align:center}
.stat-num{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(2.5rem,5vw,4.2rem);font-weight:700;
  letter-spacing:-2px;display:block;margin-bottom:8px;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.stat-label{font-size:.65rem;font-weight:500;letter-spacing:3px;text-transform:uppercase;color:var(--muted)}

/* ── FEATURES ── */
.features-section{background:var(--matte)}
.features-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:24px}
.feat{
  padding:40px 32px;
  border:1px solid var(--border2);border-radius:18px;
  background:var(--card);
  position:relative;overflow:hidden;transition:border-color .3s,box-shadow .3s;
}
.feat:hover{
  border-color:rgba(200,150,12,.3);
  box-shadow:0 12px 40px rgba(0,0,0,.4),0 0 20px rgba(200,150,12,.06);
}
.feat::after{
  content:'';position:absolute;bottom:0;left:0;right:0;height:2px;border-radius:0 0 18px 18px;
  background:var(--yg2);transform:scaleX(0);transition:transform .4s;
}
.feat:hover::after{transform:scaleX(1)}
.feat-icon{font-size:2.2rem;margin-bottom:22px;display:block}
.feat-num{
  font-family:'Cormorant Garamond',serif;font-size:3.5rem;font-weight:700;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  opacity:.12;
  position:absolute;top:20px;right:20px;letter-spacing:-3px;
}
.feat-title{font-family:'Cormorant Garamond',serif;font-size:1.25rem;font-weight:700;margin-bottom:10px}
.feat-desc{font-size:.8rem;color:var(--muted);line-height:1.8}

/* ── TESTIMONIALS ── */
.test-section{background:var(--matte2)}
.test-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:20px}
.test-card{
  padding:36px;border:1px solid var(--border2);border-radius:18px;
  background:var(--card);
  position:relative;overflow:hidden;transition:border-color .3s;
}
.test-card:hover{border-color:rgba(200,150,12,.25)}
.test-quote{
  font-family:'Cormorant Garamond',serif;font-size:1.05rem;
  font-style:italic;line-height:1.85;color:rgba(240,237,232,.75);
  margin-bottom:28px;position:relative;
}
.test-quote::before{
  content:'"';position:absolute;top:-20px;left:-8px;
  font-size:6rem;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  opacity:.1;line-height:1;
}
.test-author{display:flex;align-items:center;gap:14px}
.test-avatar{
  width:42px;height:42px;border-radius:50%;
  background:var(--yg);
  display:flex;align-items:center;justify-content:center;
  font-size:1rem;color:var(--matte3);font-weight:700;flex-shrink:0;
}
.test-name{font-size:.85rem;font-weight:500;margin-bottom:3px}
.test-stars{
  font-size:.7rem;letter-spacing:2px;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}

/* ── NEWSLETTER ── */
.newsletter-section{
  background:var(--matte3);padding:120px 60px;
  display:flex;flex-direction:column;align-items:center;text-align:center;
  border-top:1px solid var(--border);
}
.nl-form{display:flex;gap:0;margin-top:24px;max-width:520px;width:100%;border-radius:14px;overflow:hidden;border:1px solid var(--border)}
.nl-input{
  flex:1;background:var(--matte2);border:none;
  padding:16px 24px;
  font-family:'Outfit',sans-serif;font-size:.9rem;color:var(--text);outline:none;
}
.nl-input::placeholder{color:var(--muted)}
.nl-btn{
  background:var(--yg);color:var(--matte3);border:none;
  padding:16px 32px;font-family:'Outfit',sans-serif;font-weight:600;
  font-size:.78rem;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;transition:opacity .25s;white-space:nowrap;
}
.nl-btn:hover{opacity:.85}
.nl-note{font-size:.72rem;color:var(--muted);margin-top:16px;letter-spacing:1.5px}

/* ── FOOTER ── */
footer{
  background:var(--matte3);border-top:1px solid var(--border);
  padding:60px;
  display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:60px;
}
.f-brand p{font-size:.8rem;color:var(--muted);line-height:1.8;max-width:220px;margin-top:14px}
.f-col h4{
  font-size:.62rem;font-weight:600;letter-spacing:3px;
  text-transform:uppercase;margin-bottom:20px;
  background:var(--yg2);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.f-col ul{list-style:none;display:flex;flex-direction:column;gap:10px}
.f-col ul a{font-size:.8rem;color:var(--muted);text-decoration:none;transition:color .2s}
.f-col ul a:hover{color:var(--y2)}
.f-bottom{
  grid-column:1/-1;border-top:1px solid var(--border2);padding-top:32px;
  display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:16px;
}
.f-copy{font-size:.7rem;color:#2a2620;letter-spacing:1.5px}

/* ── TOAST ── */
.toast{
  position:fixed;bottom:40px;right:40px;z-index:600;
  background:var(--yg);color:var(--matte3);
  padding:16px 28px;font-weight:600;font-size:.8rem;letter-spacing:1.5px;
  text-transform:uppercase;border-radius:12px;
  box-shadow:0 8px 30px rgba(0,0,0,.5);
  transform:translateY(80px);opacity:0;
  transition:all .45s cubic-bezier(.34,1.56,.64,1);
}
.toast.show{transform:translateY(0);opacity:1}

/* ── DIVIDER CURVE ── */
.curve-divider{
  width:100%;overflow:hidden;line-height:0;
  background:var(--matte2);
}
.curve-divider svg{display:block;width:100%;height:60px}
.curve-divider.flip{transform:rotate(180deg)}

@media(max-width:900px){
  nav{top:10px;width:calc(100% - 24px);padding:0 20px}
  .nav-links{display:none}
  .hero,.section{padding-left:24px;padding-right:24px}
  .hero-badge{display:none}
  .stats-section{padding:60px 24px}
  footer{grid-template-columns:1fr 1fr;padding:40px 24px}
  .newsletter-section{padding:80px 24px}
}
@media(max-width:600px){
  footer{grid-template-columns:1fr}
  .nl-form{flex-direction:column;border-radius:14px}
}
</style>
</head>
<body>

<!-- LOADER -->
<div id="loader">
  <div class="load-logo">Delta Max</div>
  <div class="load-bar"><div class="load-fill"></div></div>
</div>

<!-- NAV -->
<nav id="nav">
  <div class="logo">Delta<span style="opacity:.5;font-weight:300;margin:0 4px">&nbsp;</span>Max<div class="logo-dot"></div></div>
  <ul class="nav-links">
    <li><a href="#products">Shop</a></li>
    <li><a href="#features">About</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#newsletter">Contact</a></li>
  </ul>
  <div>
    <button class="nav-cart" id="navCart">
      Cart
      <span class="cart-badge" id="badge">0</span>
    </button>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">
      <span class="hero-eyebrow-dot"></span>
      Premium Global Store — Est. 2024
    </div>
    <h1>
      Redefine<br>
      <em>Excellence.</em>
      <span class="line2">Delivered.</span>
    </h1>
    <p class="hero-sub">Delta Max brings you the world's finest curated products — engineered for those who demand more than ordinary.</p>
    <div class="hero-actions">
      <a href="#products" class="btn-gold">Explore Collection</a>
      <a href="#features" class="btn-outline">Our Promise</a>
    </div>
  </div>
  <div class="hero-badge">
    <div class="hero-badge-text">Premium · Worldwide · Verified</div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <span>Delta Max</span><span>Premium Drops</span><span>Global Shipping</span><span>Curated Excellence</span>
    <span>Luxury Essentials</span><span>Free Returns</span><span>Verified Quality</span><span>New Arrivals</span>
    <span>Delta Max</span><span>Premium Drops</span><span>Global Shipping</span><span>Curated Excellence</span>
    <span>Luxury Essentials</span><span>Free Returns</span><span>Verified Quality</span><span>New Arrivals</span>
  </div>
</div>

<!-- PRODUCTS -->
<section class="section products-section" id="products">
  <div class="s-tag">Collection</div>
  <div class="s-title">Curated Drops</div>
  <p class="s-sub">Each product is hand-selected for quality, demand, and design. Nothing average. Ever.</p>
  <div class="products-grid">

    <div class="p-card">
      <div class="p-img">⌚<div class="p-img-glow"></div><span class="p-tag">Bestseller</span></div>
      <div class="p-body">
        <div class="p-cat">Wearables</div>
        <div class="p-name">Apex Smart Watch</div>
        <p class="p-desc">Military-grade casing, health monitoring & 14-day battery. Engineered for peak performance.</p>
        <div class="p-foot">
          <span class="p-price">$89.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

    <div class="p-card">
      <div class="p-img">🎧<div class="p-img-glow"></div><span class="p-tag">New</span></div>
      <div class="p-body">
        <div class="p-cat">Audio</div>
        <div class="p-name">Noir ANC Pro</div>
        <p class="p-desc">Hybrid active noise cancellation. 40-hour playtime. Audiophile-tuned sound signature.</p>
        <div class="p-foot">
          <span class="p-price">$129.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

    <div class="p-card">
      <div class="p-img">💼<div class="p-img-glow"></div></div>
      <div class="p-body">
        <div class="p-cat">Lifestyle</div>
        <div class="p-name">Executive Folio</div>
        <p class="p-desc">Full-grain vegan leather. Holds 15" laptop, passport, cards. Understated luxury.</p>
        <div class="p-foot">
          <span class="p-price">$74.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

    <div class="p-card">
      <div class="p-img">🔦<div class="p-img-glow"></div><span class="p-tag">Limited</span></div>
      <div class="p-body">
        <div class="p-cat">Tech</div>
        <div class="p-name">Lux Beam 2000</div>
        <p class="p-desc">Aircraft-aluminum tactical flashlight. 2000 lumens. Magnetic base & waterproof.</p>
        <div class="p-foot">
          <span class="p-price">$49.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

    <div class="p-card">
      <div class="p-img">🎒<div class="p-img-glow"></div></div>
      <div class="p-body">
        <div class="p-cat">Travel</div>
        <div class="p-name">Stealth Daypack</div>
        <p class="p-desc">Anti-theft 30L backpack. Hidden pockets, USB-C passthrough & waterproof zips.</p>
        <div class="p-foot">
          <span class="p-price">$94.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

    <div class="p-card">
      <div class="p-img">🕯️<div class="p-img-glow"></div><span class="p-tag">Popular</span></div>
      <div class="p-body">
        <div class="p-cat">Home</div>
        <div class="p-name">Noir Ambiance Set</div>
        <p class="p-desc">Premium soy-wax candle trio. 60-hour burn each. Notes of cedar, amber, and musk.</p>
        <div class="p-foot">
          <span class="p-price">$44.99</span>
          <button class="p-btn" onclick="addCart(this)">Add to Cart</button>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- STATS -->
<div class="stats-section">
  <div class="stat"><span class="stat-num" data-target="24000">0</span><span class="stat-label">Customers Worldwide</span></div>
  <div class="stat"><span class="stat-num" data-target="800">0</span><span class="stat-label">Premium Products</span></div>
  <div class="stat"><span class="stat-num" data-target="98">0</span><span class="stat-label">% Satisfaction</span></div>
  <div class="stat"><span class="stat-num" data-target="40">0</span><span class="stat-label">Countries Served</span></div>
</div>

<!-- FEATURES -->
<section class="section features-section" id="features">
  <div class="s-tag">Why Delta Max</div>
  <div class="s-title">The Delta Standard</div>
  <p class="s-sub">A different level of care goes into everything we do — from sourcing to your doorstep.</p>
  <div class="features-grid">
    <div class="feat">
      <span class="feat-num">01</span>
      <span class="feat-icon">🔬</span>
      <div class="feat-title">Verified Quality</div>
      <p class="feat-desc">Every product passes our 12-point quality audit before it earns a place in our catalog.</p>
    </div>
    <div class="feat">
      <span class="feat-num">02</span>
      <span class="feat-icon">🌍</span>
      <div class="feat-title">Global Reach</div>
      <p class="feat-desc">We ship to over 40 countries with full tracking and premium packaging on every order.</p>
    </div>
    <div class="feat">
      <span class="feat-num">03</span>
      <span class="feat-icon">↩️</span>
      <div class="feat-title">Free Returns</div>
      <p class="feat-desc">Not happy? Return within 30 days — no questions, no hassle, no restocking fee.</p>
    </div>
    <div class="feat">
      <span class="feat-num">04</span>
      <span class="feat-icon">🛡️</span>
      <div class="feat-title">Buyer Protection</div>
      <p class="feat-desc">Shop with confidence. Every order is secured with full buyer protection and encryption.</p>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="section test-section" id="testimonials">
  <div class="s-tag">Reviews</div>
  <div class="s-title">What They Say</div>
  <p class="s-sub">Thousands of satisfied customers across the globe trust Delta Max.</p>
  <div class="test-grid">
    <div class="test-card">
      <p class="test-quote">The packaging alone made me feel like I'd bought something truly premium. The watch exceeded every expectation I had. Delta Max is different.</p>
      <div class="test-author">
        <div class="test-avatar">J</div>
        <div>
          <div class="test-name">James Arkwright</div>
          <div class="test-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="test-card">
      <p class="test-quote">Ordered from London, arrived in 6 days to Dubai. Flawless product, flawless experience. This is what online shopping should feel like.</p>
      <div class="test-author">
        <div class="test-avatar">S</div>
        <div>
          <div class="test-name">Sofia Al-Hassan</div>
          <div class="test-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="test-card">
      <p class="test-quote">I've tried plenty of dropshipping stores. Delta Max is on another level. The curation, the service, the brand feel — nothing comes close.</p>
      <div class="test-author">
        <div class="test-avatar">M</div>
        <div>
          <div class="test-name">Marcus Chen</div>
          <div class="test-stars">★★★★★</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- NEWSLETTER -->
<section class="newsletter-section" id="newsletter">
  <div class="s-tag" style="justify-content:center">Exclusive Access</div>
  <div class="s-title" style="text-align:center">Join the Inner Circle</div>
  <p class="s-sub" style="text-align:center;margin:0 auto 40px">Get early access to drops, exclusive discounts, and members-only offers. No spam — ever.</p>
  <div class="nl-form">
    <input class="nl-input" type="email" placeholder="your@email.com"/>
    <button class="nl-btn">Join Now</button>
  </div>
  <p class="nl-note">✦ First order discount included on signup</p>
</section>

<!-- FOOTER -->
<footer>
  <div class="f-brand">
    <div class="logo" style="font-size:1.3rem">Delta Max</div>
    <p>Premium curated goods for those who demand excellence. Worldwide shipping, unmatched quality.</p>
  </div>
  <div class="f-col">
    <h4>Shop</h4>
    <ul>
      <li><a href="#">New Arrivals</a></li>
      <li><a href="#">Bestsellers</a></li>
      <li><a href="#">Limited Drops</a></li>
      <li><a href="#">Sale</a></li>
    </ul>
  </div>
  <div class="f-col">
    <h4>Support</h4>
    <ul>
      <li><a href="#">Track Order</a></li>
      <li><a href="#">Returns</a></li>
      <li><a href="#">FAQ</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </div>
  <div class="f-col">
    <h4>Company</h4>
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Privacy</a></li>
      <li><a href="#">Terms</a></li>
      <li><a href="#">Careers</a></li>
    </ul>
  </div>
  <div class="f-bottom">
    <span class="f-copy">© 2026 Delta Max. All rights reserved.</span>
    <div class="logo" style="font-size:1rem;letter-spacing:4px">Delta Max</div>
  </div>
</footer>

<div class="toast" id="toast">✓ Added to Cart</div>

<script>
// Loader
window.addEventListener('load',()=>{
  setTimeout(()=>document.getElementById('loader').classList.add('hide'),2000);
});

// Nav scroll
window.addEventListener('scroll',()=>{
  document.getElementById('nav').classList.toggle('scrolled',scrollY>60);
});

// Cart
let n=0;
function addCart(btn){
  n++;
  const b=document.getElementById('badge');
  b.textContent=n;b.classList.add('vis');
  const t=document.getElementById('toast');
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2400);
  btn.textContent='✓ Added';
  setTimeout(()=>{btn.textContent='Add to Cart';},1800);
}

// Counter animation
const counters=document.querySelectorAll('[data-target]');
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(!e.isIntersecting)return;
    const el=e.target,target=+el.dataset.target,step=target/110;
    let val=0;
    const t=setInterval(()=>{
      val=Math.min(val+step,target);
      el.textContent=target>=1000?Math.floor(val).toLocaleString():Math.floor(val);
      if(val>=target){el.textContent=target>=1000?target.toLocaleString():target;clearInterval(t);}
    },16);
    obs.unobserve(el);
  });
},{threshold:.4});
counters.forEach(c=>obs.observe(c));

// Scroll reveal
const ro=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){e.target.style.opacity='1';e.target.style.transform='translateY(0)';}
  });
},{threshold:.08});
document.querySelectorAll('.p-card,.feat,.test-card').forEach((el,i)=>{
  el.style.opacity='0';
  el.style.transform='translateY(28px)';
  el.style.transition=`opacity .65s ${i*.08}s ease, transform .65s ${i*.08}s ease, border-color .3s, box-shadow .4s`;
  ro.observe(el);
});

// Newsletter
document.querySelector('.nl-btn').addEventListener('click',()=>{
  const inp=document.querySelector('.nl-input');
  if(inp.value.includes('@')){
    inp.value='';
    const t=document.getElementById('toast');
    t.textContent='✦ Welcome to Delta Max!';
    t.classList.add('show');
    setTimeout(()=>{t.classList.remove('show');t.textContent='✓ Added to Cart';},3000);
  }
});
</script>
</body>
</html>
HTMLEOF
