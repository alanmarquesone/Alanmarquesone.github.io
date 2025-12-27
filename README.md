<!doctype html>
<html lang="pt-br">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Nativo Buggy | Passeios na Praia do Forte</title>
  <meta name="description" content="Passeios de Buggy, Quadriciclo e Lancha na Praia do Forte. Reserve seu roteiro exclusivo pelo WhatsApp." />

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700;800&family=Open+Sans:wght@400;500;600&display=swap" rel="stylesheet">
  <!-- Ícones -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

  <style>
    /* --- NOVA PALETA DE CORES (Vibe Tropical/Bahia) --- */
    :root{
      /* Verde Esmeralda/Turquesa (Mar & Mata) - Mais vibrante que o anterior */
      --brand: #009688;       
      --brand-dark: #00695c;
      
      /* Azul Oceano Profundo (Detalhes e Contraste) */
      --brand-2: #0277bd;     
      
      /* Laranja Pôr do Sol (Ação/Botões) - Bem chamativo */
      --cta: #ff6d00;         
      
      /* Tons Neutros e Fundo */
      --text: #263238;        /* Cinza escuro azulado para texto */
      --bg: #f5f7fa;          /* Fundo levemente acinzentado/azulado */
      --surface: #ffffff;     /* Branco puro para cards */
      
      --container: 1200px;
      --radius-xl: 16px;
    }

    /* Reset & Base */
    *{ box-sizing: border-box; margin: 0; padding: 0; }
    html{ scroll-behavior: smooth; }
    
    body{
      font-family: "Open Sans", sans-serif;
      color: var(--text);
      background: var(--bg);
      overflow-x: hidden;
      line-height: 1.6;
    }

    h1, h2, h3, .btn, .brand { font-family: "Montserrat", sans-serif; }
    .container{ width: min(var(--container), 90%); margin-inline: auto; }

    /* --- ANIMAÇÕES (SCROLL REVEAL) --- */
    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: all 0.8s ease-out;
    }
    .reveal.active {
      opacity: 1;
      transform: translateY(0);
    }
    /* Delays para elementos em sequência */
    .delay-100 { transition-delay: 0.1s; }
    .delay-200 { transition-delay: 0.2s; }
    .delay-300 { transition-delay: 0.3s; }


    /* --- HEADER --- */
    header {
      position: fixed; top: 0; width: 100%; z-index: 1000;
      padding: 1rem 0;
      transition: 0.4s ease;
      background: linear-gradient(to bottom, rgba(0,0,0,0.7), transparent);
    }
    header.scrolled {
      background: rgba(255,255,255,0.95);
      backdrop-filter: blur(10px);
      padding: 0.8rem 0;
      box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    }
    
    .nav-wrap { display: flex; justify-content: space-between; align-items: center; }
    
    /* Logo atualizado para Imagem */
    .logo { 
      display: flex; align-items: center; text-decoration: none; 
    }
    .logo img {
      height: 60px; /* Altura ajustada para o header */
      width: auto;
      transition: 0.3s;
    }
    
    /* Menu Desktop */
    .desktop-nav { display: flex; gap: 30px; align-items: center; }
    .desktop-nav a { 
      color: rgba(255,255,255,0.95); text-decoration: none; font-weight: 600; font-size: 0.9rem; 
      transition: 0.3s; text-transform: uppercase; letter-spacing: 0.5px;
      text-shadow: 0 1px 3px rgba(0,0,0,0.3);
    }
    .desktop-nav a:hover { color: var(--cta); }
    
    header.scrolled .desktop-nav a { color: var(--text); text-shadow: none; }
    header.scrolled .desktop-nav a:hover { color: var(--brand); }

    /* Botão CTA no Header */
    .header-btn {
      background: var(--cta); color: white !important;
      padding: 10px 25px; border-radius: 50px;
      box-shadow: 0 4px 15px rgba(255, 109, 0, 0.4);
      text-shadow: none !important;
    }
    .header-btn:hover { transform: translateY(-2px); background: #ff9100; }

    /* Menu Mobile Toggle */
    .menu-toggle { display: none; background: none; border: none; font-size: 1.8rem; color: white; cursor: pointer; }
    header.scrolled .menu-toggle { color: #333; }

    /* Menu Mobile Container */
    .mobile-menu {
      position: fixed; top: 0; right: -100%; width: 80%; max-width: 300px; height: 100vh;
      background: white; z-index: 1001;
      padding: 80px 30px;
      transition: 0.4s ease;
      box-shadow: -5px 0 20px rgba(0,0,0,0.1);
      display: flex; flex-direction: column; gap: 20px;
    }
    .mobile-menu.active { right: 0; }
    .mobile-menu a {
      text-decoration: none; color: #333; font-weight: 700; font-size: 1.1rem;
      border-bottom: 1px solid #eee; padding-bottom: 10px;
    }
    .mobile-overlay {
      position: fixed; top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5); z-index: 1000;
      opacity: 0; visibility: hidden; transition: 0.3s;
    }
    .mobile-overlay.active { opacity: 1; visibility: visible; }
    .close-menu { position: absolute; top: 20px; right: 20px; font-size: 1.5rem; background: none; border: none; cursor: pointer; }


    /* --- HERO SLIDER --- */
    .hero {
      position: relative; height: 100vh; min-height: 600px;
      display: flex; align-items: center; justify-content: center;
      overflow: hidden; text-align: center; color: white;
    }
    
    /* Wrapper para o Vídeo de Fundo */
    .hero-video-wrap {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 0;
      overflow: hidden;
      pointer-events: none; /* Impede clique no vídeo */
      background-color: black;
      /* Fallback image caso o vídeo não carregue (Low Power Mode) */
      background-image: url('https://i.ibb.co/cXxtrsTn/Save-Clip-App-503030168-17981302283833314-2897356735173353587-n.jpg');
      background-size: cover;
      background-position: center;
    }

    /* Ajuste para o vídeo cobrir a tela (Aspect Ratio Hack) */
    .hero-video-wrap iframe {
      position: absolute;
      top: 50%; left: 50%;
      width: 100vw; height: 100vh;
      transform: translate(-50%, -50%);
      object-fit: cover;
    }

    /* Media Queries para forçar o preenchimento total (zoom no vídeo se necessário) */
    @media (min-aspect-ratio: 16/9) {
      .hero-video-wrap iframe { height: 56.25vw; }
    }
    @media (max-aspect-ratio: 16/9) {
      .hero-video-wrap iframe { width: 177.78vh; }
    }
    
    .hero-overlay { background: linear-gradient(to bottom, rgba(0,50,40,0.3), rgba(0,0,0,0.7)); z-index: 1; position: absolute; top:0; left:0; width:100%; height:100%; }

    .hero-content { position: relative; z-index: 2; padding-top: 60px; max-width: 900px; }
    .hero h1 {
      font-size: clamp(2.5rem, 5vw, 4.5rem); font-weight: 800; line-height: 1.1; margin-bottom: 1.5rem;
      text-shadow: 0 4px 20px rgba(0,0,0,0.6); text-transform: uppercase;
      letter-spacing: -1px;
    }
    .hero p {
      font-size: 1.2rem; margin-bottom: 2.5rem; text-shadow: 0 2px 10px rgba(0,0,0,0.8); max-width: 700px; margin-inline: auto; font-weight: 500;
    }
    
    .btn-hero {
      display: inline-flex; align-items: center; justify-content: center; gap: 10px;
      padding: 16px 45px; border-radius: 50px; font-weight: 700; text-decoration: none;
      background: var(--cta); color: white; font-size: 1.1rem; border: none; cursor: pointer;
      box-shadow: 0 10px 30px rgba(255, 109, 0, 0.4); transition: 0.3s;
      text-transform: uppercase; letter-spacing: 0.5px;
    }
    .btn-hero:hover { transform: translateY(-5px); background: #ff9100; box-shadow: 0 15px 40px rgba(255, 109, 0, 0.5); }

    /* --- SEÇÕES --- */
    section { padding: 6rem 0; }
    .section-title { text-align: center; margin-bottom: 4rem; }
    .section-title h2 { 
      color: var(--brand); font-size: 2.5rem; margin-bottom: 0.5rem; text-transform: uppercase; letter-spacing: 1px;
      background: -webkit-linear-gradient(45deg, var(--brand), var(--brand-2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .section-title span { display: block; width: 80px; height: 5px; background: var(--cta); margin: 15px auto; border-radius: 10px; }
    .section-title p { color: #546e7a; max-width: 600px; margin: 0 auto; font-size: 1.1rem; }

    /* --- DESTAQUES (Ícones) --- */
    .features-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 30px; text-align: center; }
    .feature-box {
      background: var(--surface); padding: 40px 25px; border-radius: var(--radius-xl);
      box-shadow: 0 10px 30px rgba(0,0,0,0.03); transition: 0.3s; border: 1px solid rgba(0,0,0,0.05);
    }
    .feature-box:hover { transform: translateY(-10px); box-shadow: 0 20px 40px rgba(0,150,136,0.15); border-color: var(--brand); }
    .feature-box i { 
      font-size: 3rem; margin-bottom: 20px; 
      background: -webkit-linear-gradient(45deg, var(--brand), var(--brand-2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .feature-box h3 { font-size: 1.25rem; margin-bottom: 10px; color: var(--text); font-weight: 700; }
    .feature-box p { color: #78909c; }

    /* --- ROTEIROS (Cards) --- */
    .cards-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 2.5rem; }
    .tour-card {
      background: var(--surface); border-radius: var(--radius-xl); overflow: hidden;
      box-shadow: 0 15px 35px rgba(0,0,0,0.06); transition: 0.4s; position: relative;
      border: 1px solid rgba(0,0,0,0.03);
    }
    .tour-card:hover { transform: translateY(-10px); box-shadow: 0 25px 50px rgba(0,0,0,0.1); }
    
    .card-img-wrap { height: 260px; overflow: hidden; position: relative; }
    .card-img-wrap img { width: 100%; height: 100%; object-fit: cover; transition: 0.6s; }
    .tour-card:hover .card-img-wrap img { transform: scale(1.1); }
    
    .price-tag {
      position: absolute; top: 20px; right: 20px;
      background: var(--cta); color: white; padding: 6px 18px;
      border-radius: 30px; font-weight: 700; font-size: 0.85rem;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2); letter-spacing: 0.5px;
    }

    .card-body { padding: 2rem; }
    .card-body h3 { font-size: 1.5rem; color: var(--brand-dark); margin-bottom: 10px; font-weight: 800; }
    .card-details { display: flex; gap: 15px; margin: 15px 0; color: #546e7a; font-size: 0.9rem; font-weight: 600; }
    .card-details i { color: var(--brand); margin-right: 5px; }
    
    .btn-card {
      display: block; width: 100%; padding: 14px; text-align: center;
      background: transparent; border: 2px solid var(--brand); color: var(--brand);
      font-weight: 700; border-radius: 50px; text-decoration: none; transition: 0.3s;
      text-transform: uppercase; font-size: 0.9rem; letter-spacing: 0.5px;
    }
    .btn-card:hover { background: var(--brand); color: white; box-shadow: 0 5px 20px rgba(0,150,136,0.3); }

    /* --- SOBRE (Imagem + Texto) --- */
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; }
    .about-img { 
      position: relative; height: 500px; border-radius: var(--radius-xl); overflow: hidden;
      box-shadow: 20px 20px 0 var(--cta); 
    }
    .about-img img { width: 100%; height: 100%; object-fit: cover; }
    
    .about-text h3 { color: var(--cta); font-size: 1.1rem; text-transform: uppercase; margin-bottom: 15px; font-weight: 700; letter-spacing: 1px; }
    .about-text h2 { font-size: 2.8rem; color: var(--brand-dark); margin-bottom: 25px; line-height: 1.1; }
    .about-text p { color: #546e7a; margin-bottom: 20px; font-size: 1.05rem; }
    .about-text ul { list-style: none; margin-top: 30px; }
    .about-text li { margin-bottom: 15px; display: flex; align-items: center; gap: 15px; font-weight: 600; color: var(--text); }
    .about-text li i { color: var(--brand); font-size: 1.4rem; background: rgba(0,150,136,0.1); padding: 8px; border-radius: 50%; }

    /* --- DEPOIMENTOS --- */
    .reviews-scroll { display: flex; gap: 25px; overflow-x: auto; padding-bottom: 30px; scroll-snap-type: x mandatory; }
    .review-card {
      min-width: 320px; flex: 1; background: var(--surface); padding: 35px; border-radius: var(--radius-xl);
      scroll-snap-align: start; border-top: 5px solid var(--brand); border-bottom: none; border-left: none; border-right: none;
      box-shadow: 0 10px 30px rgba(0,0,0,0.05);
    }
    .stars { color: #ffab00; margin-bottom: 15px; }

    /* --- RESERVA (Formulário) --- */
    .booking-section { 
      background: linear-gradient(135deg, var(--brand) 0%, var(--brand-dark) 100%);
      position: relative;
    }
    /* Pattern overlay on css gradient */
    .booking-section::before {
      content: ""; position: absolute; top:0; left:0; width:100%; height:100%;
      background: url('https://www.transparenttextures.com/patterns/cubes.png'); opacity: 0.1;
    }
    
    .form-container {
      background: var(--surface); padding: 4rem; border-radius: var(--radius-xl);
      box-shadow: 0 30px 60px rgba(0,0,0,0.2); max-width: 800px; margin: 0 auto;
      border-top: none; position: relative; z-index: 2;
    }
    .form-container .section-title h2 { color: var(--brand-dark); background: none; -webkit-text-fill-color: initial; }
    
    .form-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 25px; }
    .form-group { margin-bottom: 0; }
    .form-group label { display: block; font-weight: 700; margin-bottom: 10px; color: #37474f; font-size: 0.9rem; text-transform: uppercase; }
    .form-group input, .form-group select {
      width: 100%; padding: 16px; border: 2px solid #e0e0e0; border-radius: 12px; font-family: inherit;
      background: #fafafa; transition: 0.3s; font-size: 1rem; color: #333;
    }
    .form-group input:focus, .form-group select:focus { border-color: var(--brand); outline: none; background: white; }
    .full-width { grid-column: span 2; }
    
    .btn-submit {
      width: 100%; padding: 20px; background: var(--cta); color: white; font-weight: 800; border: none;
      border-radius: 12px; font-size: 1.2rem; cursor: pointer; transition: 0.3s;
      display: flex; align-items: center; justify-content: center; gap: 15px;
      text-transform: uppercase; letter-spacing: 1px;
      box-shadow: 0 10px 25px rgba(255, 109, 0, 0.3);
    }
    .btn-submit:hover { background: #ff9100; transform: translateY(-3px); box-shadow: 0 15px 35px rgba(255, 109, 0, 0.4); }

    /* --- FOOTER --- */
    footer { background: #263238; color: #b0bec5; padding: 80px 0 30px; text-align: center; }
    .footer-logo { font-size: 2rem; color: white; font-weight: 800; margin-bottom: 25px; display: block; letter-spacing: 2px; }
    .footer-links { display: flex; justify-content: center; gap: 30px; margin-bottom: 50px; }
    .footer-links a { color: #b0bec5; text-decoration: none; transition: 0.3s; font-weight: 600; text-transform: uppercase; font-size: 0.9rem; }
    .footer-links a:hover { color: var(--cta); }
    .copyright { border-top: 1px solid #37474f; padding-top: 30px; font-size: 0.9rem; opacity: 0.7; }

    /* --- FLUTUANTES (WhatsApp + Instagram) --- */
    .wa-float, .ig-float {
      position: fixed; bottom: 30px; z-index: 999;
      width: 65px; height: 65px; border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 35px; color: white; text-decoration: none;
      box-shadow: 0 5px 20px rgba(0,0,0,0.3); transition: 0.3s;
    }
    
    .wa-float {
      right: 30px;
      background: #25D366;
      animation: pulse 2s infinite;
    }
    
    .ig-float {
      right: 110px; /* Posicionado à esquerda do WhatsApp */
      background: radial-gradient(circle at 30% 107%, #fdf497 0%, #fdf497 5%, #fd5949 45%, #d6249f 60%, #285AEB 90%);
    }

    .wa-float:hover, .ig-float:hover { transform: scale(1.1); }

    @keyframes pulse { 0% { box-shadow: 0 0 0 0 rgba(37,211,102,0.5); } 70% { box-shadow: 0 0 0 15px rgba(37,211,102,0); } 100% { box-shadow: 0 0 0 0 rgba(37,211,102,0); } }

    /* --- RESPONSIVO --- */
    @media (max-width: 900px) {
      .hero h1 { font-size: 2.5rem; }
      .desktop-nav { display: none; }
      .menu-toggle { display: block; }
      .about-grid { grid-template-columns: 1fr; gap: 2rem; }
      .about-img { height: 300px; box-shadow: 10px 10px 0 var(--cta); }
      .form-grid { grid-template-columns: 1fr; }
      .full-width { grid-column: span 1; }
      .form-container { padding: 2rem; }
      
      /* Ajuste dos ícones flutuantes no mobile */
      .wa-float, .ig-float { width: 55px; height: 55px; font-size: 28px; bottom: 20px; }
      .wa-float { right: 20px; }
      .ig-float { right: 85px; }
    }
  </style>
</head>
<body>

  <!-- Menu Mobile Overlay -->
  <div class="mobile-overlay" id="mobileOverlay"></div>
  <div class="mobile-menu" id="mobileMenu">
    <button class="close-menu" id="closeMenu">&times;</button>
    <a href="#home" class="mobile-link">Início</a>
    <a href="#roteiros" class="mobile-link">Roteiros</a>
    <a href="#destinos-arc" class="mobile-link">Destinos</a>
    <a href="#sobre" class="mobile-link">Sobre</a>
    <a href="#depoimentos" class="mobile-link">Depoimentos</a>
    <a href="#reserva" class="mobile-link" style="color: var(--brand);">Reservar Agora</a>
  </div>

  <!-- Header -->
  <header id="header">
    <div class="container nav-wrap">
      <!-- Logomarca Atualizada -->
      <a href="#" class="logo">
        <img src="https://i.ibb.co/0yPSC1c6/logo2.png" alt="Nativo Buggy">
      </a>
      
      <nav class="desktop-nav">
        <a href="#home">Início</a>
        <a href="#roteiros">Roteiros</a>
        <a href="#destinos-arc">Destinos</a>
        <a href="#sobre">Quem Somos</a>
        <a href="#depoimentos">Depoimentos</a>
        <a href="#reserva" class="header-btn">Reservar</a>
      </nav>
      
      <button class="menu-toggle" id="menuToggle"><i class="fas fa-bars"></i></button>
    </div>
  </header>

  <!-- HERO SLIDER -->
  <section class="hero" id="home">
    <div class="hero-video-wrap">
      <!-- Vídeo Vimeo Incorporado como Background -->
      <!-- Parâmetros extras adicionados: muted=1, playsinline=1 para Mobile -->
      <iframe 
        src="https://player.vimeo.com/video/1149330297?background=1&autoplay=1&loop=1&byline=0&title=0&badge=0&autopause=0&muted=1&playsinline=1" 
        frameborder="0" 
        allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media" 
        title="Nativo Buggy Video - Praia do Forte"
        style="pointer-events: none;"
        tabindex="-1">
      </iframe>
    </div>
    <div class="hero-overlay"></div>

    <div class="hero-content">
      <h1 class="reveal">Explore a Praia do Forte</h1>
      <p class="reveal delay-100">Viva a emoção de pilotar um buggy ou quadriciclo pelas trilhas da Reserva Sapiranga e descubra praias secretas.</p>
      <div class="reveal delay-200">
        <a href="#reserva" class="btn-hero"><i class="fab fa-whatsapp"></i> Agendar Aventura</a>
      </div>
    </div>
  </section>

  <!-- DESTAQUES -->
  <section id="destaques">
    <div class="container">
      <div class="features-grid">
        <div class="feature-box reveal">
          <i class="fas fa-map-marked-alt"></i>
          <h3>Roteiros Exclusivos</h3>
          <p>Trilhas que só os nativos conhecem.</p>
        </div>
        <div class="feature-box reveal delay-100">
          <i class="fas fa-shield-alt"></i>
          <h3>Segurança Total</h3>
          <p>Veículos revisados e guias experientes.</p>
        </div>
        <div class="feature-box reveal delay-200">
          <i class="fas fa-camera"></i>
          <h3>Fotos Incríveis</h3>
          <p>Paradas nos melhores ângulos da região.</p>
        </div>
        <div class="feature-box reveal delay-300">
          <i class="fas fa-clock"></i>
          <h3>Flexibilidade</h3>
          <p>Seu tempo, seu ritmo. Sem pressa.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ROTEIROS -->
  <section id="roteiros" style="background-color: #f5f7fa;">
    <div class="container">
      <div class="section-title reveal">
        <h2>Nossas Experiências</h2>
        <span></span>
        <p>Aventuras exclusivas com guias experientes. Segurança, conforto e a melhor vibe da Bahia.</p>
      </div>

      <div class="cards-grid">
        
        <!-- 1. Passeio de Buggy -->
        <div class="tour-card reveal">
          <div class="card-img-wrap">
            <span class="price-tag">Mais Vendido</span>
            <img src="https://i.ibb.co/4gZscfW5/passeio-buggy.jpg" alt="Passeio de Buggy">
          </div>
          <div class="card-body">
            <h3>Passeio de Buggy</h3>
            <div class="card-details">
              <span><i class="fas fa-clock"></i> 1h20 a 4h</span>
              <span><i class="fas fa-users"></i> Até 4 Pessoas</span>
            </div>
            <p>Roteiro completo pela Reserva Sapiranga e praias. Inclui paradas estratégicas para banho e fotos.</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

        <!-- 2. Passeio de Quadriciclo -->
        <div class="tour-card reveal delay-100">
          <div class="card-img-wrap">
            <span class="price-tag">Aventura</span>
            <img src="https://i.ibb.co/chhYXLZr/quadriciclo.jpg" alt="Passeio de Quadriciclo">
          </div>
          <div class="card-body">
            <h3>Passeio de Quadriciclo</h3>
            <div class="card-details">
              <span><i class="fas fa-clock"></i> 1h30 a 4h</span>
              <span><i class="fas fa-motorcycle"></i> Pilote Você</span>
            </div>
            <p>Emoção em trilhas na natureza. Guia acompanhando para orientação total e segurança.</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

        <!-- 3. Mergulho com Fotos -->
        <div class="tour-card reveal delay-200">
          <div class="card-img-wrap">
            <span class="price-tag">Fotos Inclusas</span>
            <img src="https://i.ibb.co/gMfBdXMX/melgulho.jpg" alt="Mergulho nas Piscinas Naturais">
          </div>
          <div class="card-body">
            <h3>Mergulho nas Piscinas</h3>
            <div class="card-details">
              <span><i class="fas fa-water"></i> Maré Baixa</span>
              <span><i class="fas fa-camera"></i> Fotos Subaquáticas</span>
            </div>
            <p>Mergulho nas piscinas naturais da Praia do Lord ou Papa Gente. Águas cristalinas e vida marinha.</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

        <!-- 4. Passeio para ver as Baleias -->
        <div class="tour-card reveal">
          <div class="card-img-wrap">
            <span class="price-tag">Sazonal</span>
            <img src="https://images.unsplash.com/photo-1568430462989-44163eb1752f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Observação de Baleias">
          </div>
          <div class="card-body">
            <h3>Observação de Baleias</h3>
            <div class="card-details">
              <span><i class="fas fa-calendar-alt"></i> Julho a Outubro</span>
              <span><i class="fas fa-binoculars"></i> Jubartes</span>
            </div>
            <p>Um espetáculo da natureza! Navegue para ver as gigantes Jubarte (conforme período permitido).</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

        <!-- 5. Passeio de Lancha -->
        <div class="tour-card reveal delay-100">
          <div class="card-img-wrap">
            <span class="price-tag">Premium</span>
            <img src="https://i.ibb.co/fYp4yvT0/Leave-this-boat-2k-202512251834.jpg" alt="Passeio de Lancha">
          </div>
          <div class="card-body">
            <h3>Passeio de Lancha</h3>
            <div class="card-details">
              <span><i class="fas fa-ship"></i> Litoral Norte</span>
              <span><i class="fas fa-glass-cheers"></i> Exclusivo</span>
            </div>
            <p>Navegue com conforto e exclusividade. Ideal para grupos, pôr do sol e conhecer a costa pelo mar.</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

        <!-- 6. City Tour -->
        <div class="tour-card reveal delay-200">
          <div class="card-img-wrap">
            <span class="price-tag">Cultural</span>
            <img src="https://i.ibb.co/Xx3c6Cqx/1908005507671fcf29a2b9c7-32617074.jpg" alt="City Tour Histórico">
          </div>
          <div class="card-body">
            <h3>City Tour</h3>
            <div class="card-details">
              <span><i class="fas fa-clock"></i> 4 a 8 Horas</span>
              <span><i class="fas fa-landmark"></i> História Local</span>
            </div>
            <p>Imersão na cultura e história da região. Roteiro guiado completo pelos principais pontos turísticos.</p>
            <br>
            <a href="#reserva" class="btn-card">Reservar</a>
          </div>
        </div>

      </div>

      <!-- Informações Adicionais (Pagamento/Cancelamento) -->
      <div style="margin-top: 50px; background: var(--surface); padding: 30px; border-radius: 16px; box-shadow: 0 5px 20px rgba(0,0,0,0.05); text-align: center; border: 1px solid rgba(0,0,0,0.03);" class="reveal">
        <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 30px; color: #555;">
          <div>
            <i class="fas fa-money-bill-wave" style="color: var(--brand); font-size: 1.5rem; margin-bottom: 10px;"></i>
            <h4 style="margin: 0; color: var(--text);">Pagamento Facilitado</h4>
            <p style="font-size: 0.9rem; margin: 5px 0 0; color: #78909c;">PIX, Dinheiro ou Combinado</p>
          </div>
          <div>
            <i class="fas fa-undo-alt" style="color: var(--brand); font-size: 1.5rem; margin-bottom: 10px;"></i>
            <h4 style="margin: 0; color: var(--text);">Cancelamento Flexível</h4>
            <p style="font-size: 0.9rem; margin: 5px 0 0; color: #78909c;">Devolução integral até 48h antes</p>
          </div>
          <div>
            <i class="fas fa-check-circle" style="color: var(--brand); font-size: 1.5rem; margin-bottom: 10px;"></i>
            <h4 style="margin: 0; color: var(--text);">Tudo Incluso</h4>
            <p style="font-size: 0.9rem; margin: 5px 0 0; color: #78909c;">Guia, Veículo e Roteiro Completo</p>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- SEÇÃO DESTINOS (SLIDER ARQUEADO) -->
  <section id="destinos-arc">
    <style>
      /* --- CSS ISOLADO (SCOPED) --- */
      #destinos-arc {
        background: #fff;
        padding: 80px 0;
        overflow: hidden;
        user-select: none; /* Evita seleção de texto ao arrastar */
      }

      #destinos-arc .arc-container {
        width: 100%;
        max-width: 1200px;
        margin: 0 auto;
        position: relative;
      }

      #destinos-arc .arc-title {
        text-align: center;
        margin-bottom: 50px;
      }

      #destinos-arc .arc-title h2 {
        font-family: "Montserrat", sans-serif;
        color: var(--brand);
        font-size: 2.5rem;
        margin-bottom: 10px;
        text-transform: uppercase;
      }

      #destinos-arc .arc-title p {
        color: #666;
        font-family: "Open Sans", sans-serif;
        max-width: 600px;
        margin: 0 auto;
      }

      /* Slider Area */
      #destinos-arc .arc-slider-viewport {
        width: 100%;
        overflow-x: scroll; /* Scroll nativo escondido */
        overflow-y: hidden;
        padding: 50px 0 80px 0; /* Espaço para scale e shadow */
        cursor: grab;
        /* Esconder barra de rolagem */
        scrollbar-width: none; /* Firefox */
        -ms-overflow-style: none; /* IE/Edge */
      }
      #destinos-arc .arc-slider-viewport::-webkit-scrollbar {
        display: none; /* Chrome/Safari */
      }
      #destinos-arc .arc-slider-viewport:active {
        cursor: grabbing;
      }

      #destinos-arc .arc-track {
        display: flex;
        gap: 20px;
        padding: 0 50vw; /* Espaço para centralizar o primeiro/último */
        width: max-content;
      }

      /* Cards */
      #destinos-arc .arc-card {
        width: 280px;
        height: 380px;
        background: #eee;
        border-radius: 20px;
        position: relative;
        flex-shrink: 0;
        overflow: hidden;
        box-shadow: 0 10px 30px rgba(0,0,0,0.15);
        transition: transform 0.1s linear; /* Animação via JS */
        transform-origin: center bottom;
        will-change: transform;
      }

      #destinos-arc .arc-card-img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        pointer-events: none; /* Evita arrastar a imagem */
      }

      #destinos-arc .arc-card-content {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
        padding: 40px 20px 20px;
        color: white;
        text-align: center;
        opacity: 0; /* Esconde conteúdo dos laterais */
        transition: opacity 0.3s;
      }

      #destinos-arc .arc-card.arc-active .arc-card-content {
        opacity: 1; /* Mostra conteúdo só no central */
      }

      #destinos-arc .arc-card-title {
        font-family: "Montserrat", sans-serif;
        font-size: 1.1rem;
        font-weight: 700;
        margin: 0;
        text-shadow: 0 2px 4px rgba(0,0,0,0.5);
      }
      
      #destinos-arc .arc-card-desc {
        font-size: 0.85rem;
        margin-top: 5px;
        opacity: 0.9;
        font-weight: 400;
      }

      /* Responsivo Específico */
      @media (max-width: 768px) {
        #destinos-arc .arc-card {
          width: 240px;
          height: 320px;
        }
        #destinos-arc .arc-title h2 { font-size: 2rem; }
      }
    </style>

    <div class="arc-container">
      <div class="arc-title">
        <h2>Destinos Incríveis</h2>
        <p>Arraste para explorar os cenários paradisíacos do nosso roteiro.</p>
      </div>

      <div class="arc-slider-viewport" id="arcViewport">
        <div class="arc-track" id="arcTrack">
          
          <!-- 1. Reserva Sapiranga -->
          <div class="arc-card">
            <img src="https://i.ibb.co/dwd1vpn1/sapiranga.jpg" class="arc-card-img" alt="Reserva Sapiranga">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Reserva Sapiranga</h3>
              <p class="arc-card-desc">Mata Atlântica preservada</p>
            </div>
          </div>

          <!-- 2. Cascatinha dos Índios -->
          <div class="arc-card">
            <img src="https://i.ibb.co/gLgJSmbG/photo1jpg.jpg" class="arc-card-img" alt="Cascatinha dos Índios">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Cascatinha dos Índios</h3>
              <p class="arc-card-desc">Banho refrescante na mata</p>
            </div>
          </div>

          <!-- 3. Rio Pojuca -->
          <div class="arc-card">
            <img src="https://i.ibb.co/3mHM7KNm/rio-pojuca.jpg" class="arc-card-img" alt="Rio Pojuca">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Rio Pojuca</h3>
              <p class="arc-card-desc">Natureza selvagem</p>
            </div>
          </div>

          <!-- 4. Meliponário -->
          <div class="arc-card">
            <img src="https://i.ibb.co/W4bQZxTJ/Recreate-this-image-2k-202512251353.jpg" class="arc-card-img" alt="Meliponário">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Meliponário</h3>
              <p class="arc-card-desc">Cultivo de abelhas nativas</p>
            </div>
          </div>

          <!-- 5. Centro de Educação Ambiental -->
          <div class="arc-card">
            <img src="https://i.ibb.co/NnjjsL9Z/conhecimento.jpg" class="arc-card-img" alt="Centro Ambiental">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Educação Ambiental</h3>
              <p class="arc-card-desc">Conhecimento local</p>
            </div>
          </div>

          <!-- 6. Castelo Garcia D’Ávila -->
          <div class="arc-card">
            <img src="https://i.ibb.co/7dSR4mc2/castelo.jpg" class="arc-card-img" alt="Castelo Garcia D'Ávila">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Castelo Garcia D’Ávila</h3>
              <p class="arc-card-desc">História e ruínas (Ingresso à parte)</p>
            </div>
          </div>

          <!-- 7. Praia do Lord -->
          <div class="arc-card">
            <img src="https://i.ibb.co/fYB7h6GD/lord.jpg" class="arc-card-img" alt="Praia do Lord">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia do Lord</h3>
              <p class="arc-card-desc">Piscinas naturais cristalinas</p>
            </div>
          </div>

          <!-- 8. Praia da Barra -->
          <div class="arc-card">
            <img src="https://i.ibb.co/9kzXb8Rb/Recreate-this-image-2k-202512251357.jpg" class="arc-card-img" alt="Praia da Barra">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia da Barra</h3>
              <p class="arc-card-desc">Encontro do rio com o mar</p>
            </div>
          </div>

          <!-- 9. Projeto TAMAR -->
          <div class="arc-card">
            <img src="https://i.ibb.co/XfKfJNkc/Recreate-this-image-2k-202512251348.jpg" class="arc-card-img" alt="Projeto TAMAR">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Projeto TAMAR</h3>
              <p class="arc-card-desc">Preservação das tartarugas</p>
            </div>
          </div>

          <!-- 10. Praia da Espera -->
          <div class="arc-card">
            <img src="https://i.ibb.co/20BQhrNm/espera.jpg" class="arc-card-img" alt="Praia da Espera">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia da Espera</h3>
              <p class="arc-card-desc">Calmaria e barcos de pesca</p>
            </div>
          </div>

          <!-- 11. Praia de Santo Antônio -->
          <div class="arc-card">
            <img src="https://i.ibb.co/V1Sdfp3/santo-antonio.jpg" class="arc-card-img" alt="Santo Antônio">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia de Santo Antônio</h3>
              <p class="arc-card-desc">Dunas e tranquilidade</p>
            </div>
          </div>

          <!-- 12. Praia de Itacimirim -->
          <div class="arc-card">
            <img src="https://i.ibb.co/DgM2JfpC/itacimirim-2.jpg" class="arc-card-img" alt="Itacimirim">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia de Itacimirim</h3>
              <p class="arc-card-desc">Beleza natural única</p>
            </div>
          </div>

          <!-- 13. Praia de Guarajuba -->
          <div class="arc-card">
            <img src="https://i.ibb.co/tPwTM6CC/Recreate-this-image-2k-202512251347.jpg" class="arc-card-img" alt="Guarajuba">
            <div class="arc-card-content">
              <h3 class="arc-card-title">Praia de Guarajuba</h3>
              <p class="arc-card-desc">Paraíso dos coqueiros</p>
            </div>
          </div>

        </div>
      </div>
    </div>

    <script>
      (function() {
        // --- JS ENCAPSULADO (IIFE) ---
        const viewport = document.getElementById('arcViewport');
        const cards = document.querySelectorAll('#destinos-arc .arc-card');
        
        let isDown = false;
        let startX;
        let scrollLeft;

        // Configuração visual do arco
        const MAX_SCALE = 1.15; // Tamanho do card central
        const MIN_SCALE = 0.85; // Tamanho dos cards laterais
        const MAX_TRANSLATE_Y = 0; // Posição do central
        const MIN_TRANSLATE_Y = 40; // O quanto os laterais descem (px)
        const ROTATION_FACTOR = 5; // Graus de rotação máxima nas pontas

        function updateCards() {
          const centerPoint = viewport.offsetWidth / 2;
          
          cards.forEach((card) => {
            const cardRect = card.getBoundingClientRect();
            // Pega o centro do viewport relativo ao card
            const cardCenter = cardRect.left + (cardRect.width / 2);
            // Distância do centro do viewport (em pixels)
            const distFromCenter = centerPoint - cardCenter;
            
            // Normaliza a distância (quanto maior, mais longe do centro)
            // 400px é a distância onde o efeito atinge o máximo
            const distanceNorm = Math.min(Math.abs(distFromCenter) / 400, 1); 

            // Cálculos de Transformação
            const scale = MAX_SCALE - (distanceNorm * (MAX_SCALE - MIN_SCALE));
            const translateY = distanceNorm * MIN_TRANSLATE_Y;
            
            // Rotação suave baseada na direção (esquerda negativo, direita positivo)
            // Se distFromCenter > 0, card está à esquerda.
            const rotate = (distFromCenter / 400) * -ROTATION_FACTOR;

            // Aplica estilos
            card.style.transform = `scale(${scale}) translateY(${translateY}px) rotate(${rotate}deg)`;
            card.style.zIndex = Math.round((1 - distanceNorm) * 100); // Central fica por cima
            
            // Classe ativa para conteúdo
            if (distanceNorm < 0.2) {
              card.classList.add('arc-active');
            } else {
              card.classList.remove('arc-active');
            }
          });

          requestAnimationFrame(updateCards);
        }

        // Inicia loop de animação
        requestAnimationFrame(updateCards);

        // Centraliza o slider no início
        window.addEventListener('load', () => {
          const trackWidth = document.getElementById('arcTrack').offsetWidth;
          viewport.scrollLeft = (trackWidth - viewport.offsetWidth) / 2;
        });

        // --- Lógica de Arraste (Drag Scroll) ---
        viewport.addEventListener('mousedown', (e) => {
          isDown = true;
          viewport.style.cursor = 'grabbing';
          startX = e.pageX - viewport.offsetLeft;
          scrollLeft = viewport.scrollLeft;
        });

        viewport.addEventListener('mouseleave', () => {
          isDown = false;
          viewport.style.cursor = 'grab';
        });

        viewport.addEventListener('mouseup', () => {
          isDown = false;
          viewport.style.cursor = 'grab';
        });

        viewport.addEventListener('mousemove', (e) => {
          if (!isDown) return;
          e.preventDefault();
          const x = e.pageX - viewport.offsetLeft;
          const walk = (x - startX) * 2; // Velocidade do scroll
          viewport.scrollLeft = scrollLeft - walk;
        });

      })();
    </script>
  </section>

  <!-- SOBRE -->
  <section id="sobre">
    <div class="container">
      <div class="about-grid">
        <div class="about-img reveal">
          <img src="https://i.ibb.co/4gZscfW5/passeio-buggy.jpg" alt="Nativo Buggy">
        </div>
        <div class="about-text reveal delay-100">
          <h3>Quem Somos</h3>
          <h2>Nascidos na Praia do Forte, Apaixonados por Aventura</h2>
          <p>A Nativo Buggy não é apenas uma agência de turismo, somos moradores locais que conhecem cada pedaço desse paraíso. Nosso objetivo é proporcionar uma experiência autêntica, segura e divertida.</p>
          <ul>
            <li><i class="fas fa-check-circle"></i> Equipe treinada e bilíngue</li>
            <li><i class="fas fa-check-circle"></i> Roteiros personalizados para famílias</li>
            <li><i class="fas fa-check-circle"></i> Compromisso com a preservação ambiental</li>
          </ul>
          <br>
          <a href="#reserva" class="btn-hero" style="padding: 12px 30px; font-size: 1rem;">Conhecer a Equipe</a>
        </div>
      </div>
    </div>
  </section>

  <!-- DEPOIMENTOS (ESTILO GOOGLE) -->
  <section id="depoimentos" style="background: var(--surface);">
    <style>
      /* Estilos Específicos para Avaliações Google */
      .google-header {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 15px;
        margin-bottom: 40px;
      }
      .google-header img { width: 40px; height: auto; }
      .google-rating { font-size: 2rem; font-weight: 700; color: #333; display: flex; align-items: center; gap: 10px; }
      .google-stars { color: #fbbc04; font-size: 1.5rem; letter-spacing: 2px; }
      
      .review-user {
        display: flex;
        align-items: center;
        gap: 12px;
        margin-bottom: 15px;
      }
      /* Ajuste para imagem de avatar */
      .user-avatar {
        width: 45px;
        height: 45px;
        border-radius: 50%;
        object-fit: cover; /* Garante que a foto não distorça */
      }
      .user-info h4 { font-size: 0.95rem; margin: 0; color: #333; font-weight: 700; }
      .user-info span { font-size: 0.8rem; color: #777; }
      
      .review-stars { color: #fbbc04; margin-bottom: 10px; font-size: 0.9rem; }
      .review-text { color: #555; font-size: 0.95rem; line-height: 1.6; font-style: normal; margin-bottom: 15px; }
      .google-icon-small { width: 20px; opacity: 0.6; align-self: flex-end; margin-top: auto; }

      .btn-google {
        display: inline-flex;
        align-items: center;
        gap: 10px;
        background: white;
        color: #333;
        border: 1px solid #dadce0;
        padding: 12px 30px;
        border-radius: 50px;
        font-weight: 600;
        text-decoration: none;
        transition: 0.3s;
        margin-top: 30px;
        box-shadow: 0 2px 5px rgba(0,0,0,0.05);
      }
      .btn-google:hover { background: #f1f3f4; transform: translateY(-2px); }
    </style>

    <div class="container">
      <!-- Cabeçalho com Nota Geral -->
      <div class="google-header reveal">
        <!-- Ícone ao lado do 5.0 -->
        <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" alt="Icon">
        <div class="google-rating">
          <span>5.0</span>
          <div class="google-stars">★★★★★</div>
        </div>
        <div style="text-align: left; font-size: 0.9rem; color: #666; line-height: 1.2;">
          <strong>Excelente</strong><br>Baseado em avaliações reais
        </div>
      </div>
      
      <!-- Slider de Avaliações -->
      <div class="reviews-scroll reveal delay-100">
        
        <!-- Avaliação 1 -->
        <div class="review-card">
          <div class="review-user">
            <!-- Avatar Atualizado -->
            <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="user-avatar" alt="Mariana Souza">
            <div class="user-info">
              <h4>Mariana Souza</h4>
              <span>Local Guide • 3 semanas atrás</span>
            </div>
          </div>
          <div class="review-stars">★★★★★</div>
          <p class="review-text">"Experiência incrível! O guia foi super atencioso e o passeio de buggy pela reserva foi o ponto alto da viagem. Recomendo muito!"</p>
          <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="google-icon-small" alt="Icon">
        </div>

        <!-- Avaliação 2 -->
        <div class="review-card">
          <div class="review-user">
            <!-- Avatar Atualizado -->
            <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="user-avatar" alt="Ricardo Alves">
            <div class="user-info">
              <h4>Ricardo Alves</h4>
              <span>Local Guide • 1 mês atrás</span>
            </div>
          </div>
          <div class="review-stars">★★★★★</div>
          <p class="review-text">"Fizemos o passeio de quadriciclo e foi pura adrenalina. Equipamentos novos e instrutor muito paciente. Voltarei com certeza."</p>
          <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="google-icon-small" alt="Icon">
        </div>

        <!-- Avaliação 3 -->
        <div class="review-card">
          <div class="review-user">
            <!-- Avatar Atualizado -->
            <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="user-avatar" alt="Fernanda Lima">
            <div class="user-info">
              <h4>Fernanda Lima</h4>
              <span>2 meses atrás</span>
            </div>
          </div>
          <div class="review-stars">★★★★★</div>
          <p class="review-text">"Lugar maravilhoso! O atendimento da Nativo Buggy foi impecável desde o WhatsApp até o fim do passeio. Nota 10!"</p>
          <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="google-icon-small" alt="Icon">
        </div>

        <!-- Avaliação 4 -->
        <div class="review-card">
          <div class="review-user">
            <!-- Avatar Atualizado -->
            <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="user-avatar" alt="João Pedro">
            <div class="user-info">
              <h4>João Pedro</h4>
              <span>Local Guide • 1 mês atrás</span>
            </div>
          </div>
          <div class="review-stars">★★★★★</div>
          <p class="review-text">"Melhor forma de conhecer a Praia do Forte. O guia explicou toda a história do Castelo. Foi muito enriquecedor."</p>
          <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" class="google-icon-small" alt="Icon">
        </div>

      </div>

      <div style="text-align: center;" class="reveal delay-200">
        <a href="https://maps.app.goo.gl/KnwSbSrkjEu2PU6g8" target="_blank" class="btn-google">
          <img src="https://i.ibb.co/7x5K3bnT/person-110935.png" style="width: 18px;" alt="Icon">
          Ver todas as avaliações no Google
        </a>
      </div>
    </div>
  </section>

  <!-- RESERVA -->
  <section id="reserva" class="booking-section">
    <div class="container">
      <div class="form-container reveal">
        <div class="section-title" style="margin-bottom: 2rem;">
          <h2>Reserve Sua Data</h2>
          <p>Preencha o formulário para verificar a disponibilidade. Retornamos rapidinho no WhatsApp!</p>
        </div>

        <form id="bookingForm">
          <div class="form-grid">
            <div class="form-group">
              <label>Seu Nome</label>
              <input type="text" id="nome" placeholder="Ex: João Silva" required>
            </div>
            <div class="form-group">
              <label>WhatsApp</label>
              <input type="tel" id="telefone" placeholder="(DD) 99999-9999" required>
            </div>
            <div class="form-group">
              <label>Data Desejada</label>
              <input type="date" id="data" required>
            </div>
            <div class="form-group">
              <label>Pessoas</label>
              <select id="pessoas">
                <option value="2">2 Pessoas</option>
                <option value="3">3 Pessoas</option>
                <option value="4">4 Pessoas</option>
                <option value="Grupo">Grupo (+5)</option>
              </select>
            </div>
            <div class="form-group full-width">
              <label>Interesse Principal</label>
              <select id="interesse">
                <option value="Buggy">Passeio de Buggy</option>
                <option value="Quadriciclo">Quadriciclo</option>
                <option value="Mergulho">Mergulho nas Piscinas</option>
                <option value="Lancha">Passeio de Lancha</option>
                <option value="Baleias">Observação de Baleias</option>
                <option value="CityTour">City Tour Histórico</option>
              </select>
            </div>
          </div>
          <button type="submit" class="btn-submit"><i class="fab fa-whatsapp"></i> Solicitar Orçamento</button>
        </form>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="container">
      <span class="footer-logo">NATIVO BUGGY</span>
      <div class="footer-links">
        <a href="#home">Início</a>
        <a href="#roteiros">Roteiros</a>
        <a href="#reserva">Contato</a>
      </div>
      <div class="copyright">
        &copy; 2025 Nativo Buggy. Todos os direitos reservados.
      </div>
    </div>
  </footer>

  <!-- Floating Icons -->
  <a href="https://www.instagram.com/nativopasseios/" target="_blank" class="ig-float" title="Siga nosso Instagram"><i class="fab fa-instagram"></i></a>
  <a href="#" class="wa-float" id="waFloat" title="Fale no WhatsApp"><i class="fab fa-whatsapp"></i></a>

  <script>
    // --- 1. MENU MOBILE ---
    const menuToggle = document.getElementById('menuToggle');
    const closeMenu = document.getElementById('closeMenu');
    const mobileMenu = document.getElementById('mobileMenu');
    const mobileOverlay = document.getElementById('mobileOverlay');
    const mobileLinks = document.querySelectorAll('.mobile-link');

    function toggleMenu() {
      mobileMenu.classList.toggle('active');
      mobileOverlay.classList.toggle('active');
    }

    if(menuToggle && closeMenu && mobileOverlay){
      menuToggle.addEventListener('click', toggleMenu);
      closeMenu.addEventListener('click', toggleMenu);
      mobileOverlay.addEventListener('click', toggleMenu);
      
      // Fecha o menu ao clicar em um link
      mobileLinks.forEach(link => {
        link.addEventListener('click', toggleMenu);
      });
    }

    // --- 2. SCROLL HEADER & REVEAL ---
    const header = document.getElementById('header');
    
    window.addEventListener('scroll', () => {
      // Header Effect
      if (window.scrollY > 50) header.classList.add('scrolled');
      else header.classList.remove('scrolled');

      // Reveal Animation
      const reveals = document.querySelectorAll('.reveal');
      const windowHeight = window.innerHeight;
      const elementVisible = 150;

      reveals.forEach((reveal) => {
        const elementTop = reveal.getBoundingClientRect().top;
        if (elementTop < windowHeight - elementVisible) {
          reveal.classList.add('active');
        }
      });
    });

    // --- 3. WHATSAPP ---
    // Configurado para +55 71 99978-3910
    const PHONE_NUMBER = "5571999783910"; 

    document.getElementById('bookingForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const nome = document.getElementById('nome').value;
      const telefone = document.getElementById('telefone').value;
      const data = document.getElementById('data').value;
      const interesse = document.getElementById('interesse').value;
      
      // Formata data para BR
      const dataFormatada = new Date(data).toLocaleDateString('pt-BR', {timeZone: 'UTC'});

      const msg = `*Nova Solicitação - Site Nativo Buggy*%0A--------------------------------%0A*Nome:* ${nome}%0A*WhatsApp:* ${telefone}%0A*Data:* ${dataFormatada}%0A*Interesse:* ${interesse}%0A--------------------------------%0AGostaria de saber a disponibilidade!`;
      
      window.open(`https://wa.me/${PHONE_NUMBER}?text=${msg}`, '_blank');
    });

    // Atualiza o clique do Ícone Flutuante
    document.getElementById('waFloat').addEventListener('click', function(e) {
      e.preventDefault();
      window.open(`https://wa.me/${PHONE_NUMBER}?text=Olá! Vim pelo site e tenho dúvidas sobre os passeios.`, '_blank');
    });

    // Dispara o scroll event uma vez para elementos já visíveis no topo
    window.dispatchEvent(new Event('scroll'));
  </script>

</body>
</html>
