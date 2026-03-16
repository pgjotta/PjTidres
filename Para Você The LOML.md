<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PjTidres</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Quicksand:wght@400;500;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --primary:    #c4500a;
      --primary-lt: #e07640;
      --primary-dk: #8f3608;
      --bg:         #faf3e8;
      --bg-alt:     #f3e4cc;
      --card:       #fffbf5;
      --mid:        #d4956a;
      --pale:       #fdebd8;
      --border:     #e8c5a0;
      --dark:       #2d1a0a;
      --muted:      #8a5c3a;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      font-family: 'Quicksand', sans-serif;
      color: var(--dark);
      overflow-x: hidden;
    }



    /* ── HERO ── */
    .hero {
      position: relative;
      z-index: 1;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 2rem;
      background: linear-gradient(160deg, #faf3e8 60%, #f3e4cc 100%);
    }
    .hero-badge {
      font-size: .8rem;
      letter-spacing: .18em;
      text-transform: uppercase;
      color: var(--primary-lt);
      margin-bottom: 1rem;
    }
    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 8vw, 5.5rem);
      color: var(--primary);
      line-height: 1.1;
      margin-bottom: .4rem;
    }
    .hero h1 span { font-style: italic; }
    .hero-sub {
      font-size: 1.1rem;
      color: var(--muted);
      margin-bottom: 2.4rem;
    }

    .scroll-hint {
      position: absolute;
      bottom: 2rem;
      font-size: .8rem;
      color: var(--mid);
      animation: bounce 2s infinite;
    }
    @keyframes bounce {
      0%,100% { transform: translateY(0); }
      50%      { transform: translateY(6px); }
    }

    /* ── COUNTER ── */
    .counter-section {
      position: relative;
      z-index: 1;
      background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dk) 100%);
      color: #fff;
      padding: 5rem 2rem;
      text-align: center;
    }
    .counter-section h2 {
      font-family: 'Playfair Display', serif;
      font-size: 1.8rem;
      margin-bottom: 2.5rem;
      font-weight: 400;
      letter-spacing: .04em;
    }
    .counter-grid {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      flex-wrap: wrap;
    }
    .counter-box {
      background: rgba(255,255,255,.12);
      border: 1px solid rgba(255,255,255,.25);
      border-radius: 1.2rem;
      padding: 1.4rem 2rem;
      min-width: 110px;
      backdrop-filter: blur(8px);
    }
    .counter-num {
      font-family: 'Playfair Display', serif;
      font-size: 3rem;
      font-weight: 700;
      line-height: 1;
    }
    .counter-label {
      font-size: .75rem;
      letter-spacing: .12em;
      text-transform: uppercase;
      opacity: .8;
      margin-top: .3rem;
    }
    .counter-date {
      margin-top: 2rem;
      font-size: .9rem;
      opacity: .7;
    }

    /* ── SECTIONS ── */
    section {
      position: relative;
      z-index: 1;
      padding: 5rem 2rem;
      max-width: 860px;
      margin: 0 auto;
    }

    section:nth-child(odd)  { background: var(--bg); }
    section:nth-child(even) { background: var(--bg-alt); }
    section { max-width: 100%; padding-left: 0; padding-right: 0; }
    section > * { max-width: 860px; margin-left: auto; margin-right: auto; padding-left: 2rem; padding-right: 2rem; }
    section h2, section .section-tag { display: block; max-width: 860px; margin-left: auto; margin-right: auto; padding-left: 2rem; padding-right: 2rem; }

    .section-tag {
      display: inline-block;
      font-size: .72rem;
      letter-spacing: .16em;
      text-transform: uppercase;
      color: var(--primary);
      border: 1px solid var(--border);
      background: var(--pale);
      border-radius: 999px;
      padding: .3rem .9rem;
      margin-bottom: 1rem;
    }
    section h2 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.8rem, 4vw, 2.6rem);
      color: var(--primary);
      margin-bottom: 1.4rem;
    }

    /* ── US ── */
    .story-card {
      background: var(--card);
      border-radius: 1.5rem;
      padding: 2.2rem 2.4rem;
      box-shadow: 0 4px 30px rgba(180,80,20,.08);
      border-left: 4px solid var(--primary-lt);
      font-size: 1.05rem;
      line-height: 1.85;
      color: var(--dark);
    }
    .story-card p + p { margin-top: 1rem; }

    /* ── GALERIA ── */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .photo-slot {
      aspect-ratio: 1;
      background: linear-gradient(135deg, var(--pale), var(--bg-alt));
      border-radius: 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      border: 2px dashed var(--border);
      font-size: .8rem;
      color: var(--muted);
      gap: .5rem;
      cursor: pointer;
      transition: transform .2s, box-shadow .2s;
      overflow: hidden;
    }
    .photo-slot:hover { transform: scale(1.03); box-shadow: 0 8px 24px rgba(180,80,20,.14); }
    .photo-slot img {
      width: 100%; height: 100%;
      object-fit: cover;
      display: none;
    }
    .photo-slot.has-img img   { display: block; }
    .photo-slot.has-img .slot-placeholder { display: none; }
    .slot-placeholder { text-align: center; pointer-events: none; }

    /* ── CARTA ── */
    .carta-wrap {
      background: var(--card);
      border-radius: 1.8rem;
      padding: 2.8rem 3rem;
      box-shadow: 0 4px 40px rgba(180,80,20,.08);
      position: relative;
      overflow: hidden;
    }
    .carta-wrap::before {
      content: '';
    }
    .carta-wrap p {
      font-size: 1.05rem;
      line-height: 1.9;
      color: var(--dark);
      font-style: italic;
    }
    .carta-wrap p + p { margin-top: 1rem; }
    .carta-assinatura {
      margin-top: 1.8rem;
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      color: var(--primary);
      text-align: right;
    }

    /* ── MUSICA PLAYER ── */
    .music-bar {
      position: fixed;
      bottom: 1.5rem;
      left: 50%;
      transform: translateX(-50%);
      z-index: 999;
      background: rgba(255,251,245,.95);
      backdrop-filter: blur(14px);
      border: 1px solid var(--border);
      border-radius: 1.2rem;
      padding: .7rem 1rem;
      display: flex;
      align-items: center;
      gap: 1rem;
      box-shadow: 0 4px 24px rgba(180,80,20,.15);
      white-space: nowrap;
    }
    .music-label { display: flex; flex-direction: column; justify-content: center; }
    .music-title { font-weight: 700; font-size: .82rem; color: var(--primary); }
    .music-sub   { font-size: .7rem; color: var(--muted); margin-top: .1rem; }
    #yt-iframe   { width: 200px; height: 44px; border-radius: .6rem; }

    @media (max-width: 600px) {
      .music-bar { bottom: 1rem; padding: .5rem .7rem; gap: .6rem; }
      #yt-iframe { width: 160px; height: 40px; }
      .music-sub { display: none; }
    }

    /* ── FOOTER ── */
    footer {
      position: relative;
      z-index: 1;
      text-align: center;
      padding: 3rem 1rem 6rem;
      font-size: .85rem;
      color: var(--muted);
    }
    footer .footer-heart { color: var(--red); font-size: 1.2rem; }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 1rem;
      left: 50%;
      transform: translateX(-50%);
      z-index: 998;
      background: rgba(255,255,255,.85);
      backdrop-filter: blur(12px);
      border: 1px solid var(--border);
      border-radius: 999px;
      padding: .4rem .6rem;
      display: flex;
      gap: .3rem;
    }
    nav a {
      text-decoration: none;
      font-size: .78rem;
      font-weight: 600;
      color: var(--dark);
      padding: .35rem .8rem;
      border-radius: 999px;
      transition: background .2s, color .2s;
    }
    nav a:hover { background: var(--primary); color: #fff; }

    @media (max-width: 600px) {
      nav {
        top: auto;
        bottom: 5.5rem;
        padding: .3rem .4rem;
        gap: .15rem;
        max-width: 95vw;
        overflow-x: auto;
        white-space: nowrap;
      }
      nav a { font-size: .68rem; padding: .28rem .5rem; }

      .hero { padding: 5rem 1.2rem 4rem; }

      .counter-section { padding: 3.5rem 1rem; }
      .counter-grid { gap: .7rem; }
      .counter-box { padding: 1rem 1.1rem; min-width: 72px; }
      .counter-num { font-size: 2.2rem; }
      .counter-label { font-size: .65rem; }

      section { padding-top: 3rem; padding-bottom: 3rem; }
      section > *, section h2, section .section-tag {
        padding-left: 1.2rem;
        padding-right: 1.2rem;
      }

      .story-card { padding: 1.4rem 1.2rem; font-size: .97rem; }
      .carta-wrap  { padding: 1.8rem 1.2rem; }
      .carta-wrap p { font-size: .97rem; }

      .gallery-grid { grid-template-columns: repeat(2, 1fr); gap: .7rem; }

      .music-bar {
        bottom: 1rem;
        padding: .45rem .9rem .45rem .55rem;
        gap: .55rem;
        max-width: 88vw;
      }
      .music-info div:last-child { display: none; }
    }
  </style>
</head>
<body>

<!-- nav -->
<nav>
  <a href="#hero">Início</a>
  <a href="#contador">Contador</a>
  <a href="#historia">História</a>
  <a href="#fotos">Fotos</a>
  <a href="#carta">Carta</a>
</nav>

<!-- HERO -->
<div class="hero" id="hero">
  <p class="hero-badge">✦ nosso quartinho para especiais ✦</p>
  <h1>Miguel <span>&amp;</span><br>Lara</h1>
  <p class="hero-sub">desde 04 de janeiro de 2026</p>
  <div style="width:40px;height:2px;background:var(--primary);margin:1.6rem auto;border-radius:2px;opacity:.4;"></div>
  <p class="scroll-hint">↓ role para baixo ↓</p>
</div>

<!-- CONTADOR -->
<div class="counter-section" id="contador">
  <h2>Together for...</h2>
  <div class="counter-grid">
    <div class="counter-box">
      <div class="counter-num" id="cnt-dias">0</div>
      <div class="counter-label">dias</div>
    </div>
    <div class="counter-box">
      <div class="counter-num" id="cnt-horas">0</div>
      <div class="counter-label">horas</div>
    </div>
    <div class="counter-box">
      <div class="counter-num" id="cnt-min">0</div>
      <div class="counter-label">minutos</div>
    </div>
    <div class="counter-box">
      <div class="counter-num" id="cnt-seg">0</div>
      <div class="counter-label">segundos</div>
    </div>
  </div>
  <p class="counter-date">20 de setembro de 2025</p>
</div>

<!-- HISTÓRIA -->
<section id="historia">
  <span class="section-tag">Nossa história</span>
  <h2>Como começou</h2>
  <div class="story-card">
    <p>
      Foi em 2025 que eu conheci a minha beybae, a mais estilosa, a mais linda e mais prft q tudo q eu ja presenciei e que eu nao presenciei
    </p>
    <p>
      O gasola comentou q uma "garota japinha" gostou de mim e ia me "abocanhar" entao a gente começou a nossa historia meio conturbada...
    </p>
    <p>
      Me arrependo do meu passado sobre o que eu fiz, mas eu sou o cara mais feliz que eu poderia ser em toda minha vida.
      Vai ser daqui, pra sempre. 
      Eu te amo Melissa.                                                                                                  <p>-Pedro J.</p>            
    </p>
    <p style="font-style:italic; opacity:.7; font-size:.9rem; margin-top:1.4rem;">
    
    </p>
  </div>
</section>

<!-- GALERIA -->
<section id="fotos">
  <span class="section-tag">Nossas fotancias</span>
  <h2>Nossas recordações juntos </h2>
  <div class="gallery-grid" id="gallery">
    <!-- slots gerados por JS -->
  </div>
  <p style="font-size:.8rem; color:var(--muted); margin-top:1rem; text-align:center; padding:0 2rem;">
     
  </p>
</section>

<!-- CARTA -->
<section id="carta">
  <span class="section-tag">carta de Nayumi</span>
  <h2>Palavras de Nayumi</h2>
  <div class="carta-wrap">
    <p>Meu amor,</p>
    <p>
    quero que saiba como eu te amo e te admiro, não só como namorado mas como pessoa. Tudo sobre você é interessante, todas as manhãs eu espero pelo intervalo e saída da escola porque todo dia é mais especial com você, obrigada por me fazer feliz, te amo
    </p>
  
    <p>
      Te amo hoje, amanhã e sempre. 
    </p>
    <div class="carta-assinatura">— com amor, Nayumi </div>
    <p style="font-style:italic; opacity:.5; font-size:.8rem; margin-top:1.2rem;">
    
    </p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  Feito por mim Pedro Jorge, 1% do que eu faria por você &nbsp;·&nbsp; PJ &amp; Tidres
</footer>

<!-- MUSICA PLAYER -->
<div class="music-bar" id="musicBar">
  <div class="music-label">
    <div class="music-title">Feelz -Lil peep</div>
    <div class="music-sub">A musica que descreve nosso amor ♫</div>
  </div>
  <iframe
    id="yt-iframe"
    src="https://www.youtube.com/watch?v=4ncAL0RRy8k&list=RD4ncAL0RRy8k&start_radio=1"
    allow="autoplay; encrypted-media"
    allowfullscreen
    frameborder="0"
    style="border-radius:.7rem; flex-shrink:0;">
  </iframe>
</div>

<script>
  /* ── Counter ── */
  const startDate = new Date('2025-09-20T00:00:00');
  function updateCounter() {
    const now  = new Date();
    const diff = now - startDate;
    const dias  = Math.floor(diff / 86400000);
    const horas = Math.floor((diff % 86400000) / 3600000);
    const min   = Math.floor((diff % 3600000) / 60000);
    const seg   = Math.floor((diff % 60000) / 1000);
    document.getElementById('cnt-dias').textContent  = dias;
    document.getElementById('cnt-horas').textContent = String(horas).padStart(2,'0');
    document.getElementById('cnt-min').textContent   = String(min).padStart(2,'0');
    document.getElementById('cnt-seg').textContent   = String(seg).padStart(2,'0');
  }
  updateCounter();
  setInterval(updateCounter, 1000);

  /* ── Gallery Slots ── */
  const gallery = document.getElementById('gallery');
  for (let i = 1; i <= 6; i++) {
    const slot = document.createElement('div');
    slot.className = 'photo-slot';
    const img = document.createElement('img');
    img.alt = `foto ${i}`;
    img.src = `foto${i}.jpg`;
    img.onload  = () => slot.classList.add('has-img');
    img.onerror = () => slot.classList.remove('has-img');
    slot.innerHTML = `
      <div class="slot-placeholder">
        <div style="font-size:1.4rem; opacity:.5">foto${i}.jpg</div>
        <div style="font-size:.7rem; margin-top:.2rem; opacity:.6;">adicione o arquivo</div>
      </div>
    `;
    slot.appendChild(img);
    gallery.appendChild(slot);
  }

</script>
</body>
</html> 
 
