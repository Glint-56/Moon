# Moon
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>القمر — رفيق الليل الأبدي</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&family=Noto+Naskh+Arabic:wght@400;600;700&family=Scheherazade+New:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #070c1a;
    --gold: #c8a84b;
    --gold-light: #e8c96a;
    --silver: #b8c8d8;
    --moonwhite: #f0ead8;
    --deep: #0a1228;
    --mid: #142040;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body { background: var(--ink); color: var(--moonwhite); font-family: 'Tajawal', sans-serif; overflow-x: hidden; cursor: none; }

  .cursor { width:10px;height:10px;background:var(--gold);border-radius:50%;position:fixed;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:transform .15s; }
  .cursor-trail { width:28px;height:28px;border:1px solid rgba(200,168,75,.4);border-radius:50%;position:fixed;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:transform .35s ease,opacity .3s; }

  /* NAV */
  nav { position:fixed;top:0;left:0;right:0;z-index:100;display:flex;justify-content:space-between;align-items:center;padding:1.4rem 4rem;background:linear-gradient(to bottom,rgba(7,12,26,.95),transparent);backdrop-filter:blur(4px); }
  .logo { font-family:'Scheherazade New',serif;font-size:1.9rem;color:var(--gold); }
  .nav-links { display:flex;gap:2.5rem;list-style:none; }
  .nav-links a { color:var(--silver);text-decoration:none;font-size:.9rem;font-weight:300;transition:color .3s;position:relative; }
  .nav-links a::after { content:'';position:absolute;bottom:-4px;right:0;width:0;height:1px;background:var(--gold);transition:width .3s; }
  .nav-links a:hover { color:var(--gold-light); }
  .nav-links a:hover::after { width:100%; }

  /* HERO */
  #hero { min-height:100vh;display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden; }
  .star-field { position:absolute;inset:0;overflow:hidden; }
  @keyframes twinkle { 0%,100%{opacity:.4;transform:scale(1)}50%{opacity:1;transform:scale(1.3)} }
  .moon-wrap { position:absolute;top:50%;left:50%;transform:translate(-50%,-50%); }
  .moon-glow { width:340px;height:340px;border-radius:50%;background:radial-gradient(circle at 40% 35%,rgba(240,234,216,.15) 0%,rgba(200,168,75,.08) 50%,transparent 70%);animation:pulseGlow 5s ease-in-out infinite;position:absolute;top:50%;left:50%;transform:translate(-50%,-50%); }
  @keyframes pulseGlow { 0%,100%{transform:translate(-50%,-50%) scale(1);opacity:.6}50%{transform:translate(-50%,-50%) scale(1.08);opacity:1} }
  .moon-svg { width:220px;height:220px;filter:drop-shadow(0 0 40px rgba(200,168,75,.25)) drop-shadow(0 0 80px rgba(200,168,75,.1));animation:floatMoon 8s ease-in-out infinite; }
  @keyframes floatMoon { 0%,100%{transform:translateY(0)}50%{transform:translateY(-14px)} }

  .hero-content { position:relative;z-index:10;text-align:center;padding-top:120px; }
  .hero-label { font-size:.75rem;letter-spacing:.3em;color:var(--gold);margin-bottom:1rem;animation:fadeUp 1s ease both; }

  /* ✨ DECORATIVE TITLE */
  .hero-title {
    font-family: 'Scheherazade New', serif;
    font-size: clamp(5rem, 12vw, 11rem);
    font-weight: 700;
    line-height: 1;
    color: var(--moonwhite);
    animation: fadeUp 1s ease 0.2s both;
    text-shadow: 0 0 60px rgba(200,168,75,.3), 0 0 120px rgba(200,168,75,.1);
    display: inline-block;
    position: relative;
  }
  .hero-title::after {
    content: '';
    display: block;
    width: 55%;
    height: 2px;
    margin: 0.5rem auto 0;
    background: linear-gradient(to left, transparent, var(--gold), transparent);
  }

  .hero-sub { font-family:'Noto Naskh Arabic',serif;font-size:1.15rem;font-style:italic;color:var(--silver);margin-top:1.8rem;max-width:500px;margin-inline:auto;line-height:2;animation:fadeUp 1s ease .4s both; }
  .scroll-hint { margin-top:3.5rem;display:flex;flex-direction:column;align-items:center;gap:.5rem;color:var(--gold);font-size:.75rem;letter-spacing:.15em;animation:fadeUp 1s ease .8s both; }
  .scroll-line { width:1px;height:50px;background:linear-gradient(to bottom,var(--gold),transparent);animation:scrollDrop 2s ease-in-out infinite; }
  @keyframes scrollDrop { 0%{transform:scaleY(0);transform-origin:top}50%{transform:scaleY(1);transform-origin:top}51%{transform:scaleY(1);transform-origin:bottom}100%{transform:scaleY(0);transform-origin:bottom} }
  @keyframes fadeUp { from{opacity:0;transform:translateY(30px)}to{opacity:1;transform:translateY(0)} }

  /* DIVIDER */
  .divider { display:flex;align-items:center;gap:1.5rem;margin:0 auto 4rem;max-width:200px; }
  .divider-line { flex:1;height:1px;background:linear-gradient(to left,transparent,var(--gold)); }
  .divider-line.rev { background:linear-gradient(to right,transparent,var(--gold)); }
  .divider-dot { width:6px;height:6px;background:var(--gold);border-radius:50%;box-shadow:0 0 8px var(--gold); }

  /* SECTIONS */
  section { padding:6rem 4rem;max-width:1100px;margin:0 auto; }
  .section-label { font-size:.7rem;letter-spacing:.3em;color:var(--gold);margin-bottom:.8rem; }

  /* ✨ SECTION TITLES with underline accent */
  .section-title {
    font-family: 'Scheherazade New', serif;
    font-size: clamp(2.2rem, 4vw, 3.5rem);
    font-weight: 700;
    color: var(--moonwhite);
    line-height: 1.2;
    margin-bottom: .4rem;
    display: inline-block;
  }
  .section-title::after {
    content: '';
    display: block;
    width: 45%;
    height: 1.5px;
    margin-top: .35rem;
    background: linear-gradient(to left, transparent, var(--gold) 80%);
  }
  .section-text { font-size:1rem;font-weight:300;color:var(--silver);line-height:2;max-width:620px;margin-top:1.2rem; }

  /* READ MORE SYSTEM */
  .read-more-btn {
    display: inline-flex;
    align-items: center;
    gap: .5rem;
    margin-top: 1.4rem;
    padding: .55rem 1.4rem;
    border: 1px solid rgba(200,168,75,.35);
    border-radius: 2px;
    background: transparent;
    color: var(--gold);
    font-family: 'Tajawal', sans-serif;
    font-size: .85rem;
    letter-spacing: .08em;
    cursor: pointer;
    transition: background .3s, border-color .3s;
  }
  .read-more-btn:hover { background:rgba(200,168,75,.08);border-color:var(--gold); }
  .read-more-btn .arrow { display:inline-block;transition:transform .3s ease;font-size:.75rem; }
  .read-more-btn.open .arrow { transform:rotate(180deg); }

  .expandable { max-height:0;overflow:hidden;transition:max-height .65s cubic-bezier(.4,0,.2,1),opacity .4s ease;opacity:0; }
  .expandable.open { max-height:1400px;opacity:1; }
  .expand-inner { padding-top:1.8rem;border-top:1px solid rgba(200,168,75,.1);margin-top:1.8rem; }
  .expand-inner p { font-size:.95rem;color:var(--silver);line-height:2;margin-bottom:1rem;font-weight:300; }
  .expand-inner h4 { font-family:'Scheherazade New',serif;font-size:1.3rem;color:var(--gold-light);margin:1.4rem 0 .6rem; }
  .expand-inner ul { list-style:none;padding:0; }
  .expand-inner ul li { font-size:.9rem;color:var(--silver);padding:.45rem 0;border-bottom:1px solid rgba(255,255,255,.04);display:flex;gap:.6rem;align-items:baseline; }
  .expand-inner ul li::before { content:'☽';color:var(--gold);font-size:.65rem;flex-shrink:0; }

  /* FACTS GRID */
  .facts-grid { display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:1.5px;margin-top:3rem;background:rgba(200,168,75,.1);border:1px solid rgba(200,168,75,.12);border-radius:2px;overflow:hidden; }
  .fact-card { background:var(--deep);padding:2.5rem 2rem;text-align:center;transition:background .4s;cursor:default; }
  .fact-card:hover { background:var(--mid); }
  .fact-number { font-family:'Scheherazade New',serif;font-size:2.8rem;font-weight:700;color:var(--gold);display:block;line-height:1;margin-bottom:.5rem; }
  .fact-unit { font-size:.75rem;color:var(--gold-light);letter-spacing:.1em;display:block;margin-bottom:.8rem; }
  .fact-label { font-size:.85rem;color:var(--silver);font-weight:300; }

  /* PHASES */
  #phases { background:var(--deep);border-radius:4px; }
  .phases-grid { display:grid;grid-template-columns:repeat(4,1fr);gap:2rem;margin-top:3rem; }
  .phase-item { text-align:center;padding:1.5rem;border:1px solid rgba(200,168,75,.08);border-radius:2px;transition:border-color .3s,transform .3s; }
  .phase-item:hover { border-color:rgba(200,168,75,.3);transform:translateY(-4px); }
  .phase-moon { width:70px;height:70px;margin:0 auto 1.2rem; }
  .phase-name { font-family:'Scheherazade New',serif;font-size:1.15rem;color:var(--moonwhite);margin-bottom:.5rem; }
  .phase-desc { font-size:.8rem;color:var(--silver);font-weight:300;line-height:1.7; }

  /* DEEP DIVE CARDS */
  .deep-cards { display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:1.5rem;margin-top:3rem; }
  .deep-card { border:1px solid rgba(200,168,75,.1);border-radius:3px;background:rgba(255,255,255,.02);overflow:hidden;transition:border-color .3s; }
  .deep-card:hover { border-color:rgba(200,168,75,.28); }
  .deep-card-header { padding:1.5rem 1.8rem;border-bottom:1px solid rgba(200,168,75,.08);display:flex;align-items:center;gap:1rem; }
  .deep-card-icon { font-size:1.8rem; }
  .deep-card-title { font-family:'Scheherazade New',serif;font-size:1.25rem;color:var(--moonwhite); }
  .deep-card-body { padding:1.5rem 1.8rem;font-size:.88rem;color:var(--silver);line-height:1.9;font-weight:300; }
  .deep-card .read-more-btn { margin:0 1.8rem 1.5rem; }

  /* QUOTE */
  #quote-section { text-align:center;border-top:1px solid rgba(200,168,75,.1);border-bottom:1px solid rgba(200,168,75,.1);padding:5rem 4rem;position:relative;overflow:hidden; }
  #quote-section::before { content:'☽';position:absolute;font-size:18rem;color:rgba(200,168,75,.03);top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none; }
  blockquote { font-family:'Scheherazade New',serif;font-size:clamp(1.5rem,3vw,2.3rem);font-weight:400;color:var(--moonwhite);line-height:1.7;max-width:700px;margin:0 auto 1.5rem;position:relative;z-index:1; }
  blockquote::before,blockquote::after { content:'"';color:var(--gold);font-size:3rem;line-height:0;vertical-align:-.4em; }
  cite { font-size:.8rem;color:var(--gold);letter-spacing:.15em; }

  /* TIMELINE */
  .timeline { margin-top:3rem;position:relative; }
  .timeline::before { content:'';position:absolute;right:22px;top:0;bottom:0;width:1px;background:linear-gradient(to bottom,transparent,var(--gold) 10%,var(--gold) 90%,transparent);opacity:.3; }
  .tl-item { display:grid;grid-template-columns:1fr 60px;gap:1.5rem;margin-bottom:3rem;align-items:start; }
  .tl-content { padding:1.5rem 2rem;background:rgba(255,255,255,.02);border:1px solid rgba(200,168,75,.08);border-radius:2px;transition:border-color .3s; }
  .tl-content:hover { border-color:rgba(200,168,75,.25); }
  .tl-year { font-family:'Scheherazade New',serif;font-size:1.3rem;color:var(--gold);margin-bottom:.5rem; }
  .tl-title { font-size:1rem;font-weight:500;color:var(--moonwhite);margin-bottom:.4rem; }
  .tl-text { font-size:.85rem;color:var(--silver);font-weight:300;line-height:1.8; }
  .tl-dot { width:44px;height:44px;border-radius:50%;border:1px solid rgba(200,168,75,.3);background:var(--deep);display:flex;align-items:center;justify-content:center;font-size:1.2rem;margin-top:.8rem; }

  /* FOOTER */
  footer { text-align:center;padding:3rem;border-top:1px solid rgba(200,168,75,.08);color:rgba(184,200,216,.4);font-size:.8rem;letter-spacing:.1em; }
  .footer-moon { font-size:2rem;margin-bottom:1rem;display:block;opacity:.6; }

  /* REVEAL */
  .reveal { opacity:0;transform:translateY(40px);transition:opacity .8s ease,transform .8s ease; }
  .reveal.visible { opacity:1;transform:translateY(0); }
  .reveal-delay-1 { transition-delay:.15s; }
  .reveal-delay-2 { transition-delay:.3s; }
  .reveal-delay-3 { transition-delay:.45s; }

  @media(max-width:768px){
    nav{padding:1.2rem 1.5rem}
    .nav-links{gap:1.2rem}
    section{padding:4rem 1.5rem}
    .phases-grid{grid-template-columns:repeat(2,1fr)}
    .timeline::before{right:16px}
    .tl-item{grid-template-columns:1fr 40px}
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<nav>
  <div class="logo">☽ القمر</div>
  <ul class="nav-links">
    <li><a href="#facts">حقائق</a></li>
    <li><a href="#phases">الأطوار</a></li>
    <li><a href="#deepdive">استكشاف</a></li>
    <li><a href="#history">التاريخ</a></li>
  </ul>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="star-field" id="starField"></div>
  <div class="moon-wrap">
    <div class="moon-glow"></div>
    <svg class="moon-svg" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <radialGradient id="hg" cx="38%" cy="32%" r="65%">
          <stop offset="0%" stop-color="#fffef5"/>
          <stop offset="45%" stop-color="#f0e8c0"/>
          <stop offset="100%" stop-color="#c8a84b"/>
        </radialGradient>
        <radialGradient id="craterG" cx="50%" cy="50%" r="50%">
          <stop offset="0%" stop-color="rgba(0,0,0,0.25)"/>
          <stop offset="100%" stop-color="rgba(0,0,0,0)"/>
        </radialGradient>
        <filter id="glow2">
          <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
          <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
        </filter>
      </defs>
      <circle cx="100" cy="100" r="96" fill="url(#hg)" filter="url(#glow2)"/>
      <circle cx="78" cy="72" r="10" fill="url(#craterG)" opacity="0.5"/>
      <circle cx="130" cy="90" r="6" fill="url(#craterG)" opacity="0.4"/>
      <circle cx="95" cy="128" r="8" fill="url(#craterG)" opacity="0.45"/>
      <circle cx="58" cy="115" r="5" fill="url(#craterG)" opacity="0.35"/>
      <circle cx="145" cy="130" r="7" fill="url(#craterG)" opacity="0.38"/>
      <circle cx="112" cy="58" r="4" fill="url(#craterG)" opacity="0.3"/>
      <ellipse cx="80" cy="75" rx="18" ry="14" fill="white" opacity="0.12" transform="rotate(-20,80,75)"/>
    </svg>
  </div>

  <div class="hero-content">
    <p class="hero-label">رفيق الليل الأبدي</p>
    <h1 class="hero-title">القمر</h1>
    <p class="hero-sub">
      منذ فجر البشرية وهو يُضيء السماء، يُلهم الشعراء، ويُوجّه البحّارة.
      تعرّف على أسرار الجرم السماوي الأقرب إلى الأرض.
    </p>
    <div class="scroll-hint">
      <span>اكتشف المزيد</span>
      <div class="scroll-line"></div>
    </div>
  </div>
</div>

<!-- FACTS -->
<section id="facts">
  <div class="reveal">
    <p class="section-label">أرقام وحقائق</p>
    <h2 class="section-title">القمر بالأرقام</h2>
    <p class="section-text">القمر هو القمر الطبيعي الوحيد للأرض، ويُعدّ الجرم الأكثر سطوعاً في سمائنا الليلية بعد الشمس.</p>
    <button class="read-more-btn" onclick="toggle('facts-more',this)">
      <span>اقرأ المزيد عن خصائص القمر</span><span class="arrow">▾</span>
    </button>
    <div class="expandable" id="facts-more">
      <div class="expand-inner">
        <h4>التركيب الداخلي</h4>
        <p>يتكون القمر من قشرة خارجية يبلغ سمكها نحو 50 كيلومتراً، أكثر سماكةً على الجانب البعيد عن الأرض. تحتها طبقة الوشاح الممتدة حتى عمق 1400 كم، وفي المركز نواة صغيرة نصف قطرها نحو 350 كيلومتراً.</p>
        <h4>الغلاف الجوي</h4>
        <p>القمر يمتلك غلافاً جوياً شديد الرقة يُسمى "إكسوسفير" — جزيئاته نادرة جداً ولا تتصادم مع بعضها. لذلك لا يوجد طقس على القمر، ولا رياح ولا سحاب ولا صوت ينتقل عبر الهواء.</p>
        <h4>المياه على القمر</h4>
        <p>اكتشف العلماء جليداً مائياً في الفوهات القطبية حيث لا تصلها الشمس أبداً. هذا الاكتشاف فتح آفاقاً لإمكانية إنشاء قواعد بشرية دائمة على سطح القمر مستقبلاً.</p>
        <ul>
          <li>عمر القمر يُقدَّر بنحو 4.5 مليار سنة، أي بنفس عمر المجموعة الشمسية</li>
          <li>القمر يبتعد عن الأرض بمعدل 3.8 سنتيمتر كل عام</li>
          <li>جاذبية القمر تسبب ظاهرة المدّ والجزر في المحيطات</li>
          <li>سطح القمر مُغطّى بطبقة من الغبار الدقيق تُسمّى الريجوليث</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="divider reveal reveal-delay-1">
    <div class="divider-line"></div><div class="divider-dot"></div><div class="divider-line rev"></div>
  </div>

  <div class="facts-grid reveal reveal-delay-2">
    <div class="fact-card"><span class="fact-number">384,400</span><span class="fact-unit">كيلومتر</span><span class="fact-label">المسافة من الأرض</span></div>
    <div class="fact-card"><span class="fact-number">1,737</span><span class="fact-unit">كيلومتر</span><span class="fact-label">نصف القطر</span></div>
    <div class="fact-card"><span class="fact-number">27.3</span><span class="fact-unit">يوماً أرضياً</span><span class="fact-label">دورة كاملة حول الأرض</span></div>
    <div class="fact-card"><span class="fact-number">-173</span><span class="fact-unit">درجة مئوية</span><span class="fact-label">أدنى درجة حرارة</span></div>
    <div class="fact-card"><span class="fact-number">127</span><span class="fact-unit">درجة مئوية</span><span class="fact-label">أعلى درجة حرارة</span></div>
    <div class="fact-card"><span class="fact-number">1/6</span><span class="fact-unit">من جاذبية الأرض</span><span class="fact-label">قوة الجاذبية</span></div>
  </div>
</section>

<!-- PHASES -->
<section id="phases" style="max-width:100%;padding:6rem 0;">
  <div style="max-width:1100px;margin:0 auto;padding:0 4rem;">
    <div class="reveal">
      <p class="section-label">دورة القمر</p>
      <h2 class="section-title">أطوار القمر الثمانية</h2>
      <p class="section-text">يمرّ القمر بثمانية أطوار متعاقبة خلال دورة شهرية واحدة، تبدأ بالمحاق وتنتهي به مجدداً.</p>
      <button class="read-more-btn" onclick="toggle('phases-more',this)">
        <span>تأثير الأطوار على الحياة</span><span class="arrow">▾</span>
      </button>
      <div class="expandable" id="phases-more">
        <div class="expand-inner">
          <h4>تأثير القمر على المدّ والجزر</h4>
          <p>يُعدّ القمر المتحكم الرئيسي في ظاهرة المدّ والجزر. عند اكتمال القمر أو محاقه، تتوافق جاذبية الشمس والقمر مما يُسبّب "المدّ الربيعي" الأعلى. أما في التربيعين فيحدث "المدّ المحاقي" الأهدأ.</p>
          <h4>القمر في الثقافة العربية</h4>
          <p>اعتمد العرب على القمر في التقويم الهجري منذ أكثر من 1400 عام. ارتبطت أطواره بالعبادات والمواسم والزراعة، وأبدع الشعراء العرب في وصفه وتشبيه وجوه الحسان به.</p>
          <ul>
            <li>يبدأ الشهر العربي بظهور الهلال الجديد بعد المحاق</li>
            <li>البدر يصادف منتصف الشهر القمري دائماً</li>
            <li>كسوف الشمس يحدث في طور المحاق، وخسوف القمر في طور البدر</li>
            <li>بعض الثقافات تربط زراعة المحاصيل بأطوار القمر حتى اليوم</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="phases-grid reveal reveal-delay-1">
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#0a1228" stroke="rgba(200,168,75,0.2)" stroke-width="1"/></svg>
        <p class="phase-name">المحاق</p><p class="phase-desc">لا يُرى القمر، يقع بين الأرض والشمس</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#0a1228"/><path d="M35,5 A30,30 0 0,1 35,65 A18,30 0 0,0 35,5Z" fill="#f0e8c0" opacity="0.85"/></svg>
        <p class="phase-name">الهلال المتزايد</p><p class="phase-desc">شريط رفيع من الضوء يظهر في الغرب</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#0a1228"/><path d="M35,5 A30,30 0 0,1 35,65 L35,5Z" fill="#f0e8c0" opacity="0.85"/></svg>
        <p class="phase-name">التربيع الأول</p><p class="phase-desc">نصف القمر مضاء في الجانب الأيمن</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#f0e8c0" opacity="0.85"/><path d="M35,5 A30,30 0 0,0 35,65 A12,30 0 0,1 35,5Z" fill="#0a1228"/></svg>
        <p class="phase-name">الأحدب المتزايد</p><p class="phase-desc">معظم القمر مضاء ويقترب من البدر</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70">
          <defs><radialGradient id="fm" cx="40%" cy="35%" r="60%"><stop offset="0%" stop-color="#fffef5"/><stop offset="100%" stop-color="#c8a84b"/></radialGradient></defs>
          <circle cx="35" cy="35" r="30" fill="url(#fm)"/>
        </svg>
        <p class="phase-name">البدر</p><p class="phase-desc">القمر كامل مضيء ومواجه للأرض تماماً</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#f0e8c0" opacity="0.85"/><path d="M35,5 A30,30 0 0,1 35,65 A12,30 0 0,0 35,5Z" fill="#0a1228"/></svg>
        <p class="phase-name">الأحدب المتناقص</p><p class="phase-desc">القمر يبدأ بالتناقص بعد اكتماله</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#0a1228"/><path d="M35,5 A30,30 0 0,0 35,65 L35,5Z" fill="#f0e8c0" opacity="0.85"/></svg>
        <p class="phase-name">التربيع الأخير</p><p class="phase-desc">نصف القمر مضاء في الجانب الأيسر</p>
      </div>
      <div class="phase-item">
        <svg class="phase-moon" viewBox="0 0 70 70"><circle cx="35" cy="35" r="30" fill="#0a1228"/><path d="M35,5 A30,30 0 0,0 35,65 A18,30 0 0,1 35,5Z" fill="#f0e8c0" opacity="0.85"/></svg>
        <p class="phase-name">الهلال المتناقص</p><p class="phase-desc">آخر مشهد قبل عودة المحاق</p>
      </div>
    </div>
  </div>
</section>

<!-- DEEP DIVE -->
<section id="deepdive">
  <div class="reveal">
    <p class="section-label">استكشاف معمّق</p>
    <h2 class="section-title">اعرف أكثر</h2>
    <p class="section-text">اختر موضوعاً وتعمّق في أسرار القمر التي لا تنتهي.</p>
  </div>

  <div class="deep-cards reveal reveal-delay-1">

    <div class="deep-card">
      <div class="deep-card-header"><span class="deep-card-icon">🌊</span><p class="deep-card-title">القمر والمحيطات</p></div>
      <div class="deep-card-body">جاذبية القمر تشدّ مياه المحيطات مسبّبةً ظاهرة المدّ والجزر التي تتكرر مرتين يومياً في معظم سواحل العالم.</div>
      <button class="read-more-btn" onclick="toggle('ocean-more',this)"><span>اقرأ المزيد</span><span class="arrow">▾</span></button>
      <div class="expandable" id="ocean-more">
        <div class="expand-inner">
          <p>يُشكّل المدّ والجزر أحد أهم الأنظمة البيئية الساحلية. تعتمد عليه الأسماك والطيور البحرية في دورة حياتها. الفرق بين أعلى مدّ وأدنى جزر في خليج فاندي بكندا يصل إلى 16 متراً — كافٍ لابتلاع مبنى من خمسة طوابق!</p>
          <ul>
            <li>تستغل بعض الدول طاقة المدّ والجزر لتوليد الكهرباء النظيفة</li>
            <li>المدّ الربيعي الأعلى يحدث مرتين شهرياً: عند البدر والمحاق</li>
            <li>جاذبية القمر تُبطئ دوران الأرض حول نفسها بشكل طفيف جداً</li>
            <li>قبل مليار عام، كان اليوم الأرضي لا يتجاوز 18 ساعة بسبب هذا التباطؤ</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="deep-card">
      <div class="deep-card-header"><span class="deep-card-icon">🔬</span><p class="deep-card-title">جيولوجيا القمر</p></div>
      <div class="deep-card-body">سطح القمر يحمل ذاكرة المجموعة الشمسية منذ مليارات السنين، محفوظة في الفوهات النيزكية والصخور البركانية.</div>
      <button class="read-more-btn" onclick="toggle('geo-more',this)"><span>اقرأ المزيد</span><span class="arrow">▾</span></button>
      <div class="expandable" id="geo-more">
        <div class="expand-inner">
          <p>لا يوجد على القمر تآكل ناجم عن الرياح أو المياه، فتبقى الفوهات محفوظة لمليارات السنين مما يجعله أرشيفاً جيولوجياً نادراً. خلال مهام أبولو، أُحضر نحو 382 كيلوغراماً من الصخور القمرية كشفت أن القمر تشكّل من اصطدام ضخم بين الأرض المبكرة وجرم فضائي بحجم المريخ.</p>
          <ul>
            <li>أقدم الصخور القمرية يعود عمرها إلى 4.4 مليار سنة</li>
            <li>سطح القمر مغطى بالريجوليث: غبار دقيق وحاد جداً</li>
            <li>توجد براكين خامدة على القمر، آخرها كان نشطاً قبل مليار سنة</li>
            <li>الجانب البعيد من القمر يختلف جيولوجياً كثيراً عن الجانب القريب</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="deep-card">
      <div class="deep-card-header"><span class="deep-card-icon">🚀</span><p class="deep-card-title">مستقبل الاستكشاف</p></div>
      <div class="deep-card-body">يتنافس العالم اليوم على العودة للقمر — ليس فقط لزرع الأقدام، بل لبناء قواعد دائمة وتعدين الموارد.</div>
      <button class="read-more-btn" onclick="toggle('future-more',this)"><span>اقرأ المزيد</span><span class="arrow">▾</span></button>
      <div class="expandable" id="future-more">
        <div class="expand-inner">
          <p>برنامج أرتميس يهدف لإعادة الإنسان للقمر وإقامة محطة "Gateway" في مداره كنقطة انطلاق نحو المريخ. الصين أيضاً تطمح ببناء محطة قمرية دولية بحلول 2035 بالتعاون مع روسيا.</p>
          <ul>
            <li>الهيليوم-3 على القمر قد يكون وقوداً للمفاعلات النووية المستقبلية</li>
            <li>جليد الماء القطبي سيُستخدم لإنتاج وقود صاروخي وماء صالح للشرب</li>
            <li>شركات خاصة كـ SpaceX وBlue Origin تتسابق لإيصال البشر للقمر</li>
            <li>أول امرأة ستطأ القمر متوقع أن تكون ضمن مهام أرتميس القادمة</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="deep-card">
      <div class="deep-card-header"><span class="deep-card-icon">🎨</span><p class="deep-card-title">القمر في الفن والأدب</p></div>
      <div class="deep-card-body">ألهم القمر الشعراء والفنانين والموسيقيين عبر كل الحضارات والعصور، من هوميروس إلى بيتهوفن.</div>
      <button class="read-more-btn" onclick="toggle('art-more',this)"><span>اقرأ المزيد</span><span class="arrow">▾</span></button>
      <div class="expandable" id="art-more">
        <div class="expand-inner">
          <p>في الشعر العربي، ضُرب القمر مثلاً للجمال منذ أقدم العصور. وصفه المتنبي وابن الرومي والبحتري بأروع الأوصاف، وجعلوه رمزاً للكمال ومرآةً للمحبوب. أما بيتهوفن فأهدى سوناتا "ضوء القمر" للتاريخ عام 1801.</p>
          <ul>
            <li>في الميثولوجيا اليونانية، سيلين ربة القمر تجوب السماء على عربة فضية</li>
            <li>المصريون القدماء قدّسوا القمر في شخصية الإله "تحوت"</li>
            <li>الهلال رمز ديني ذو مكانة خاصة في الثقافة الإسلامية منذ قرون</li>
            <li>أول لوحة تصوّر الإنسان على القمر رسمها الفنان ميلييه عام 1865</li>
          </ul>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- QUOTE -->
<div id="quote-section">
  <blockquote>حين أنظر إلى القمر، أدرك أنّ البشرية جمعاء نتشارك نفس الضوء</blockquote>
  <cite>— حكمة إنسانية خالدة</cite>
</div>

<!-- HISTORY -->
<section id="history">
  <div class="reveal">
    <p class="section-label">عبر التاريخ</p>
    <h2 class="section-title">علاقة الإنسان بالقمر</h2>
    <p class="section-text">منذ آلاف السنين والإنسان يرنو إلى القمر بدهشة وتأمّل، حتى وطئته قدماه في النهاية.</p>
    <button class="read-more-btn" onclick="toggle('history-more',this)">
      <span>الاستكشاف غير المأهول بالتفصيل</span><span class="arrow">▾</span>
    </button>
    <div class="expandable" id="history-more">
      <div class="expand-inner">
        <h4>سباق الفضاء بين القوتين العظميين</h4>
        <p>بعد إطلاق سبوتنيك عام 1957، دخلت أمريكا والاتحاد السوفيتي في سباق محموم نحو القمر. أرسل الطرفان عشرات المسابير قبل أن تحقق أبولو 11 الحلم الإنساني الأكبر. أرسل السوفييت مركبة "لونوخود" المتجوّلة عام 1970، أول مركبة آلية تجوب سطح جرم سماوي آخر في التاريخ.</p>
        <ul>
          <li>إجمالي البشر الذين وطئوا القمر: 12 رائد فضاء، جميعهم أمريكيون</li>
          <li>آخر إنسان مشى على القمر: يوجين سيرنان، ديسمبر 1972</li>
          <li>الصين هبطت على الجانب البعيد من القمر عام 2019 لأول مرة في التاريخ</li>
          <li>ناسا تخطط لإعادة الإنسان للقمر بحلول 2027</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="timeline">
    <div class="tl-item reveal reveal-delay-1">
      <div class="tl-content"><p class="tl-year">٣٠٠٠ ق.م</p><p class="tl-title">التقاويم القمرية</p><p class="tl-text">استخدمت الحضارات القديمة في بابل ومصر القمر لقياس الوقت وتنظيم الزراعة والمواسم.</p></div>
      <div class="tl-dot">📜</div>
    </div>
    <div class="tl-item reveal reveal-delay-1">
      <div class="tl-content"><p class="tl-year">١٦٠٩ م</p><p class="tl-title">غاليليو يرسم القمر</p><p class="tl-text">رصد غاليليو جاليلي القمر بالتلسكوب لأول مرة ورسم خرائط دقيقة لسطحه الوعر.</p></div>
      <div class="tl-dot">🔭</div>
    </div>
    <div class="tl-item reveal reveal-delay-2">
      <div class="tl-content"><p class="tl-year">١٩٥٩ م</p><p class="tl-title">لونا ٢ — أول مسبار يصل القمر</p><p class="tl-text">أطلق الاتحاد السوفيتي أول مركبة فضائية تصل إلى سطح القمر، وكان ذلك بداية عصر استكشاف الفضاء.</p></div>
      <div class="tl-dot">🚀</div>
    </div>
    <div class="tl-item reveal reveal-delay-2">
      <div class="tl-content"><p class="tl-year">٢٠ يوليو ١٩٦٩</p><p class="tl-title">أبولو ١١ — الإنسان على القمر</p><p class="tl-text">وطئ نيل أرمسترونج سطح القمر وقال جملته الخالدة: "خطوة صغيرة لإنسان، قفزة عظيمة للبشرية."</p></div>
      <div class="tl-dot">👨‍🚀</div>
    </div>
    <div class="tl-item reveal reveal-delay-3">
      <div class="tl-content"><p class="tl-year">المستقبل</p><p class="tl-title">برنامج أرتميس والعودة للقمر</p><p class="tl-text">تسعى وكالة ناسا وشركاؤها إلى إعادة الإنسان للقمر وإقامة قاعدة دائمة هناك كمنطلق لاستكشاف المريخ.</p></div>
      <div class="tl-dot">🌕</div>
    </div>
  </div>
</section>

<footer>
  <span class="footer-moon">☽</span>
  <p>صُمِّم بعناية واهتمام · جميع المعلومات علمية موثّقة</p>
  <p style="margin-top:.5rem;font-size:.7rem;opacity:.5;">القمر — رفيق الليل الأبدي</p>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const trail = document.getElementById('cursorTrail');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
    setTimeout(() => { trail.style.left = e.clientX + 'px'; trail.style.top = e.clientY + 'px'; }, 80);
  });

  // Stars
  const sf = document.getElementById('starField');
  const svgEl = document.createElementNS('http://www.w3.org/2000/svg','svg');
  svgEl.style.cssText = 'position:absolute;inset:0;width:100%;height:100%;';
  for (let i = 0; i < 120; i++) {
    const s = document.createElementNS('http://www.w3.org/2000/svg','circle');
    s.setAttribute('cx', Math.random()*100+'%');
    s.setAttribute('cy', Math.random()*100+'%');
    s.setAttribute('r', (Math.random()*1.5+0.5).toFixed(1));
    s.setAttribute('fill', Math.random()>.5 ? '#ffffff' : '#fff9cc');
    s.style.opacity = (Math.random()*.5+.3).toFixed(2);
    s.style.animation = `twinkle ${(Math.random()*3+1.5).toFixed(1)}s ease-in-out infinite ${(Math.random()*2).toFixed(1)}s`;
    svgEl.appendChild(s);
  }
  sf.appendChild(svgEl);

  // Toggle expand/collapse
  function toggle(id, btn) {
    const el = document.getElementById(id);
    const isOpen = el.classList.contains('open');
    el.classList.toggle('open', !isOpen);
    btn.classList.toggle('open', !isOpen);
    const label = btn.querySelector('span:first-child');
    if (!isOpen) { label.dataset.orig = label.textContent; label.textContent = 'إخفاء'; }
    else { label.textContent = label.dataset.orig || label.textContent; }
  }

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if(e.isIntersecting){e.target.classList.add('visible');observer.unobserve(e.target);} });
  }, { threshold: 0.12 });
  document.querySelectorAll('.reveal').forEach(r => observer.observe(r));

  // Active nav highlight
  window.addEventListener('scroll', () => {
    const y = window.scrollY;
    document.querySelectorAll('.nav-links a').forEach(a => {
      const sec = document.querySelector(a.getAttribute('href'));
      if(sec){ const t=sec.offsetTop-100; a.style.color=(y>=t&&y<t+sec.offsetHeight)?'var(--gold-light)':''; }
    });
  });
</script>
</body>
</html>
