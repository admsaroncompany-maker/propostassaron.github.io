<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0"/>
  <meta name="theme-color" content="#0D0D0D"/>
  <title>Saron Company — Proposta de Serviços</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400&family=Inter:wght@300;400;500;600;700&family=Cinzel:wght@400;600;700&display=swap');

    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

    :root {
      --gold:       #C9A84C;
      --gold-light: #E8C97A;
      --gold-dim:   rgba(201,168,76,.12);
      --black:      #0D0D0D;
      --card:       #181818;
      --border:     #272727;
      --text:       #E5E5E5;
      --muted:      #7A7A7A;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--text);
      font-family: 'Inter', -apple-system, sans-serif;
      font-size: 15px;
      line-height: 1.6;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
      padding-bottom: 80px; /* space for fixed CTA bar */
    }

    /* ── BARRA FIXA INFERIOR ── */
    .cta-bar {
      position: fixed; bottom: 0; left: 0; right: 0; z-index: 999;
      background: rgba(13,13,13,.96);
      backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
      border-top: 1px solid var(--border);
      padding: 12px 20px;
      display: flex; gap: 10px;
    }
    .cta-bar-btn {
      flex: 1; padding: 14px 10px;
      border-radius: 12px; text-align: center;
      font-size: 13px; font-weight: 700; letter-spacing: 1px;
      text-transform: uppercase; text-decoration: none;
      display: flex; align-items: center; justify-content: center; gap: 6px;
    }
    .cta-bar-wpp  { background: var(--gold); color: var(--black); }
    .cta-bar-mail { background: var(--card); color: var(--text); border: 1px solid var(--border); }

    /* ── NAV ── */
    .nav {
      position: sticky; top: 0; z-index: 100;
      background: rgba(13,13,13,.95);
      backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      padding: 0 20px; height: 52px;
      display: flex; align-items: center; justify-content: space-between;
    }
    .nav-logo { font-family:'Cinzel',serif; font-size: 13px; font-weight: 700; color: var(--gold); letter-spacing: 5px; text-decoration: none; }
    .nav-menu-btn { background: none; border: none; cursor: pointer; display: flex; flex-direction: column; gap: 5px; padding: 4px; }
    .nav-menu-btn span { display: block; width: 20px; height: 1.5px; background: var(--muted); border-radius: 2px; transition: all .25s; }

    /* drawer menu */
    .drawer {
      position: fixed; inset: 0; z-index: 200;
      background: var(--black);
      transform: translateX(100%);
      transition: transform .35s cubic-bezier(.4,0,.2,1);
      display: flex; flex-direction: column;
      padding: 0 32px 40px;
    }
    .drawer.open { transform: translateX(0); }
    .drawer-top {
      height: 52px; display: flex; align-items: center; justify-content: space-between;
      border-bottom: 1px solid var(--border); margin-bottom: 40px;
    }
    .drawer-close {
      background: none; border: none; cursor: pointer;
      font-size: 22px; color: var(--muted); line-height: 1; padding: 4px;
    }
    .drawer-links { display: flex; flex-direction: column; gap: 0; }
    .drawer-links a {
      font-family:'Cinzel',serif; font-size: 20px; font-weight: 600;
      color: var(--text); text-decoration: none;
      padding: 18px 0; border-bottom: 1px solid var(--border);
      letter-spacing: 2px; transition: color .2s;
      display: flex; align-items: center; justify-content: space-between;
    }
    .drawer-links a::after { content: '→'; font-family:'Inter',sans-serif; font-size: 16px; color: var(--gold); }
    .drawer-links a:hover { color: var(--gold); }

    /* ── HERO ── */
    .hero {
      min-height: 100svh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      text-align: center;
      padding: 80px 28px 120px;
      position: relative;
      background: radial-gradient(ellipse 90% 55% at 50% 50%, rgba(201,168,76,.07), transparent 70%), var(--black);
    }
    .hero-tag { font-family:'Cinzel',serif; font-size: 10px; letter-spacing: 6px; text-transform: uppercase; color: var(--gold); margin-bottom: 28px; }
    .hero-name { font-family:'Cinzel',serif; font-size: clamp(64px,18vw,110px); font-weight: 700; color: #fff; line-height: .9; letter-spacing: 4px; }
    .hero-co   { font-family:'Cinzel',serif; font-size: clamp(16px,5vw,28px); font-weight: 400; color: var(--gold); letter-spacing: 12px; margin-top: 8px; }
    .hero-line { width: 1px; height: 56px; background: linear-gradient(to bottom, transparent, var(--gold), transparent); margin: 32px auto; }
    .hero-tagline { font-family:'Playfair Display',serif; font-style:italic; font-size: 16px; color: var(--muted); line-height: 1.7; max-width: 280px; }
    .hero-scroll { position: absolute; bottom: 36px; left: 0; right: 0; text-align: center; }
    .hero-scroll span { font-size: 9px; letter-spacing: 4px; text-transform: uppercase; color: #444; display: block; margin-bottom: 8px; }
    .hero-scroll-bar { width: 1px; height: 36px; background: linear-gradient(to bottom, var(--gold), transparent); margin: 0 auto; animation: pulse 2s ease-in-out infinite; }
    @keyframes pulse { 0%,100%{opacity:.25} 50%{opacity:1} }

    /* ── FRENTES ── */
    .frentes { border-top: 1px solid var(--border); }
    .frente-cell {
      display: block; text-decoration: none;
      padding: 44px 28px; border-bottom: 1px solid var(--border);
      position: relative; overflow: hidden;
    }
    .frente-cell:last-child { border-bottom: none; }
    .frente-n { font-family:'Cinzel',serif; font-size: 72px; font-weight: 700; color: #1e1e1e; line-height: 1; margin-bottom: 12px; display: block; }
    .frente-h { font-family:'Playfair Display',serif; font-size: 24px; color: #fff; margin-bottom: 10px; }
    .frente-p { font-size: 14px; color: var(--muted); line-height: 1.7; margin-bottom: 20px; }
    .frente-arrow { display: inline-flex; align-items: center; gap: 8px; font-size: 11px; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); font-weight: 600; }

    /* ── SECTION HEADER ── */
    .s-head { padding: 56px 28px 32px; }
    .s-tag { display: block; font-size: 10px; letter-spacing: 5px; text-transform: uppercase; color: var(--gold); font-weight: 600; margin-bottom: 10px; }
    .s-title { font-family:'Playfair Display',serif; font-size: 32px; font-weight: 700; color: #fff; line-height: 1.15; margin-bottom: 10px; }
    .s-desc { font-size: 14px; color: var(--muted); line-height: 1.7; }

    /* ── PLANOS — cards deslizantes ── */
    .plans-section { border-top: 1px solid var(--border); }
    .plans-track-wrap {
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
      scroll-snap-type: x mandatory;
      scrollbar-width: none;
      padding: 0 28px 32px;
      display: flex; gap: 14px;
    }
    .plans-track-wrap::-webkit-scrollbar { display: none; }

    /* dots indicator */
    .plans-dots { display: flex; justify-content: center; gap: 6px; padding-bottom: 8px; }
    .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--border); transition: background .3s, width .3s; }
    .dot.active { width: 18px; border-radius: 3px; background: var(--gold); }

    .plan-card {
      scroll-snap-align: start;
      flex-shrink: 0;
      width: 300px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 28px 24px;
      display: flex; flex-direction: column;
      position: relative; overflow: hidden;
    }
    .plan-card.is-featured {
      border-color: var(--gold);
      background: linear-gradient(170deg, #1d1a0e 0%, #1a1a18 100%);
    }
    .plan-card.is-featured::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0; height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), var(--gold-light), transparent);
    }

    .plan-badge {
      display: inline-block; font-size: 9px; font-weight: 700; letter-spacing: 2px;
      text-transform: uppercase; padding: 4px 12px; border-radius: 40px;
      margin-bottom: 16px;
    }
    .badge-gold  { background: var(--gold); color: var(--black); }
    .badge-soft  { background: transparent; border: 1px solid var(--border); color: var(--muted); }

    .plan-name     { font-family:'Cinzel',serif; font-size: 11px; font-weight: 600; color: var(--gold); letter-spacing: 4px; text-transform: uppercase; margin-bottom: 4px; }
    .plan-headline { font-family:'Playfair Display',serif; font-size: 18px; color: #fff; margin-bottom: 8px; line-height: 1.3; }
    .plan-desc     { font-size: 12px; color: var(--muted); line-height: 1.6; margin-bottom: 20px; }

    /* big creative count */
    .plan-count     { font-family:'Playfair Display',serif; font-size: 52px; font-weight: 700; color: #fff; line-height: 1; }
    .plan-count-lbl { font-size: 10px; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; margin-top: 2px; }
    .plan-count-unit{ font-size: 10px; color: var(--gold); font-weight: 700; background: var(--gold-dim); border-radius: 4px; padding: 3px 8px; display: inline-block; margin: 6px 0 18px; }

    /* price */
    .plan-price { margin-bottom: 6px; }
    .plan-cur   { font-size: 14px; color: var(--gold); font-weight: 500; vertical-align: super; line-height: 1; }
    .plan-val   { font-family:'Playfair Display',serif; font-size: 40px; font-weight: 700; color: #fff; line-height: 1; }
    .plan-period{ font-size: 11px; color: var(--muted); margin-bottom: 14px; }

    /* breakdown */
    .breakdown {
      background: rgba(201,168,76,.05); border: 1px solid rgba(201,168,76,.15);
      border-radius: 10px; padding: 12px 14px; margin-bottom: 14px;
    }
    .br-row { display: flex; justify-content: space-between; font-size: 12px; padding: 3px 0; }
    .br-row span:first-child { color: var(--muted); }
    .br-row span:last-child  { color: var(--text); font-weight: 500; }
    .br-row.br-total { border-top: 1px solid rgba(201,168,76,.15); margin-top: 6px; padding-top: 8px; }
    .br-row.br-total span { color: var(--gold); font-weight: 700; }

    .plan-contract { font-size: 10px; color: var(--muted); border: 1px solid var(--border); border-radius: 4px; padding: 3px 8px; display: inline-block; margin-bottom: 16px; }
    .plan-sep { height: 1px; background: var(--border); margin-bottom: 16px; }

    /* features */
    .plan-feats { list-style: none; display: flex; flex-direction: column; gap: 10px; margin-bottom: 20px; flex: 1; }
    .plan-feats li { font-size: 13px; color: var(--text); display: flex; align-items: flex-start; gap: 8px; line-height: 1.4; }
    .f-dot { width: 14px; height: 14px; border-radius: 50%; background: var(--gold-dim); border: 1px solid rgba(201,168,76,.3); display: flex; align-items: center; justify-content: center; flex-shrink: 0; margin-top: 1px; font-size: 7px; color: var(--gold); }

    .plan-ideal { font-size: 11px; color: var(--muted); font-style: italic; padding-top: 12px; border-top: 1px solid var(--border); margin-bottom: 16px; line-height: 1.5; }
    .plan-ideal strong { color: var(--gold); font-style: normal; }

    .plan-btn {
      display: block; width: 100%; padding: 13px;
      border-radius: 10px; text-align: center;
      font-size: 11px; letter-spacing: 2px; text-transform: uppercase; font-weight: 700;
      text-decoration: none; margin-top: auto;
    }
    .btn-gold    { background: var(--gold); color: var(--black); }
    .btn-outline { background: transparent; color: var(--gold); border: 1px solid rgba(201,168,76,.35); }

    /* ── NOTICE ── */
    .notice {
      margin: 0 28px 40px;
      padding: 20px 22px;
      border-left: 3px solid var(--gold);
      background: var(--card); border-radius: 0 12px 12px 0;
      font-size: 13px; color: var(--muted); line-height: 1.75;
    }
    .notice strong { color: var(--text); }

    /* ── DESIGN ── */
    .design-section { border-top: 1px solid var(--border); }
    .design-track-wrap {
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
      scroll-snap-type: x mandatory;
      scrollbar-width: none;
      padding: 0 28px 32px;
      display: flex; gap: 14px;
    }
    .design-track-wrap::-webkit-scrollbar { display: none; }
    .design-card-m {
      scroll-snap-align: start;
      flex-shrink: 0;
      width: 280px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 28px 24px;
      display: flex; flex-direction: column;
      position: relative; overflow: hidden;
    }
    .design-card-m.is-highlight {
      border-color: var(--gold);
      background: linear-gradient(170deg, #1d1a0e 0%, #1a1a18 100%);
    }
    .design-card-m.is-highlight::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0; height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), var(--gold-light), transparent);
    }
    .design-pkg-name {
      font-family: 'Cinzel', serif; font-size: 10px; font-weight: 600;
      color: var(--gold); letter-spacing: 4px; text-transform: uppercase; margin-bottom: 4px;
    }
    .design-count {
      font-family: 'Playfair Display', serif; font-size: 64px; font-weight: 700;
      color: #fff; line-height: 1; margin-bottom: 2px;
    }
    .design-count-lbl {
      font-size: 10px; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 20px;
    }

    /* ── PROJETOS — accordion ── */
    .projects-section { border-top: 1px solid var(--border); }
    .proj-list { padding: 0 28px 40px; display: flex; flex-direction: column; gap: 12px; }

    .proj-item { background: var(--card); border: 1px solid var(--border); border-radius: 16px; overflow: hidden; }
    .proj-item.proj-hero { border-color: rgba(201,168,76,.25); background: linear-gradient(135deg, #151208, var(--card)); }
    .proj-trigger {
      width: 100%; background: none; border: none; cursor: pointer;
      padding: 22px 22px; text-align: left; color: inherit;
      display: flex; align-items: center; justify-content: space-between; gap: 12px;
    }
    .proj-trigger-left { display: flex; flex-direction: column; gap: 4px; }
    .proj-tag-sm { font-size: 9px; letter-spacing: 3px; text-transform: uppercase; color: var(--gold); font-weight: 600; }
    .proj-name-sm { font-family:'Playfair Display',serif; font-size: 17px; color: #fff; line-height: 1.2; }
    .proj-price-sm { font-family:'Playfair Display',serif; font-size: 18px; color: var(--gold); font-weight: 700; white-space: nowrap; flex-shrink: 0; }
    .proj-chevron { font-size: 14px; color: var(--muted); transition: transform .3s; flex-shrink: 0; }
    .proj-item.open .proj-chevron { transform: rotate(180deg); }

    .proj-body {
      max-height: 0; overflow: hidden;
      transition: max-height .4s cubic-bezier(.4,0,.2,1);
      padding: 0 22px;
    }
    .proj-item.open .proj-body { max-height: 600px; padding: 0 22px 22px; }
    .proj-body-desc { font-size: 13px; color: var(--muted); line-height: 1.7; margin-bottom: 14px; }
    .proj-body-list { display: flex; flex-direction: column; gap: 7px; }
    .proj-body-list span { font-size: 13px; color: var(--text); display: flex; align-items: center; gap: 8px; }
    .proj-body-list span::before { content: ''; width: 12px; height: 1px; background: var(--gold); flex-shrink: 0; }
    .proj-body-note { font-size: 11px; color: var(--muted); font-style: italic; margin-top: 10px; }

    /* ── NICHOS ── */
    .nichos-section { border-top: 1px solid var(--border); background: linear-gradient(180deg, #0D0D0D, #111008); }
    .nichos-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; padding: 0 28px 40px; }
    .nicho {
      border: 1px solid var(--border); border-radius: 12px;
      padding: 18px 16px; display: flex; flex-direction: column; align-items: flex-start; gap: 8px;
    }
    .nicho-ico { font-size: 22px; }
    .nicho-name { font-size: 13px; font-weight: 600; color: var(--text); line-height: 1.3; }
    .nicho-sub  { font-size: 10px; color: var(--muted); line-height: 1.4; }

    /* ── DIFERENCIAIS ── */
    .diff-section { border-top: 1px solid var(--border); }
    .diff-list { padding: 0 28px 40px; display: flex; flex-direction: column; gap: 2px; border-radius: 16px; overflow: hidden; }
    .diff-item { background: var(--card); padding: 28px 24px; display: flex; gap: 16px; align-items: flex-start; }
    .diff-ico { font-size: 22px; flex-shrink: 0; margin-top: 2px; }
    .diff-title { font-family:'Playfair Display',serif; font-size: 17px; color: #fff; margin-bottom: 6px; }
    .diff-txt   { font-size: 13px; color: var(--muted); line-height: 1.7; }

    /* ── CTA FINAL ── */
    .cta-final {
      border-top: 1px solid var(--border);
      min-height: 70svh; display: flex; align-items: center; justify-content: center;
      text-align: center; padding: 80px 28px 40px;
      background: radial-gradient(ellipse 80% 55% at 50% 60%, rgba(201,168,76,.06), transparent);
    }
    .cta-final-inner { max-width: 340px; }
    .cta-final-tag { display: block; font-size: 10px; letter-spacing: 5px; text-transform: uppercase; color: var(--gold); font-weight: 600; margin-bottom: 18px; }
    .cta-final-title { font-family:'Cinzel',serif; font-size: 36px; font-weight: 700; color: #fff; line-height: 1.05; letter-spacing: 2px; margin-bottom: 14px; }
    .cta-final-title em { color: var(--gold); font-style: normal; }
    .cta-final-sub { font-family:'Playfair Display',serif; font-style: italic; font-size: 16px; color: var(--muted); line-height: 1.7; }

    /* ── FOOTER ── */
    .footer { border-top: 1px solid var(--border); padding: 32px 28px; text-align: center; }
    .footer-logo { font-family:'Cinzel',serif; font-size: 13px; color: var(--gold); letter-spacing: 5px; font-weight: 600; display: block; margin-bottom: 8px; }
    .footer-sub  { font-size: 11px; color: var(--muted); }
    .footer-tag  { font-family:'Playfair Display',serif; font-style: italic; font-size: 11px; color: #333; margin-top: 4px; }

    /* ── REVEAL ── */
    .reveal { opacity: 0; transform: translateY(24px); transition: opacity .6s ease, transform .6s ease; }
    .reveal.in { opacity: 1; transform: none; }
  </style>
</head>
<body>

<!-- BARRA CTA FIXA -->
<div class="cta-bar">
  <a href="https://wa.me/5562982456003" class="cta-bar-btn cta-bar-wpp">
    <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
    WhatsApp
  </a>
  <a href="mailto:adm.saroncompany@gmail.com" class="cta-bar-btn cta-bar-mail">E-mail</a>
</div>

<!-- NAV -->
<nav class="nav">
  <a href="#top" class="nav-logo">SARON</a>
  <button class="nav-menu-btn" id="menuBtn" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- DRAWER -->
<div class="drawer" id="drawer">
  <div class="drawer-top">
    <span class="nav-logo">SARON</span>
    <button class="drawer-close" id="drawerClose">✕</button>
  </div>
  <nav class="drawer-links">
    <a href="#pacotes" onclick="closeDrawer()">Pacotes</a>
    <a href="#design" onclick="closeDrawer()">Design</a>
    <a href="#projetos" onclick="closeDrawer()">Projetos</a>
    <a href="#nichos" onclick="closeDrawer()">Segmentos</a>
    <a href="#diferenciais" onclick="closeDrawer()">Diferenciais</a>
    <a href="#contato" onclick="closeDrawer()">Contato</a>
  </nav>
</div>

<!-- HERO -->
<section id="top" class="hero">
  <div class="hero-tag">Audiovisual · Tráfego Pago · Resultados Reais</div>
  <h1 class="hero-name">SARON</h1>
  <div class="hero-co">COMPANY</div>
  <div class="hero-line"></div>
  <p class="hero-tagline">Conteúdo que converte. Tráfego que vende. Parcerias que crescem.</p>
  <div class="hero-scroll">
    <span>Explore</span>
    <div class="hero-scroll-bar"></div>
  </div>
</section>

<!-- FRENTES -->
<div class="frentes" id="frentes">
  <a href="#pacotes" class="frente-cell reveal">
    <span class="frente-n">01</span>
    <h2 class="frente-h">Pacotes Mensais</h2>
    <p class="frente-p">Parceria contínua com entrega recorrente de criativos e gestão de tráfego. Contrato mínimo 4 meses.</p>
    <span class="frente-arrow">Ver planos →</span>
  </a>
  <a href="#projetos" class="frente-cell reveal">
    <span class="frente-n">02</span>
    <h2 class="frente-h">Projetos Pontuais</h2>
    <p class="frente-p">Entregas específicas para lançamentos, campanhas sazonais e produção de conteúdo avulso.</p>
    <span class="frente-arrow">Ver projetos →</span>
  </a>
  <a href="#design" class="frente-cell reveal">
    <span class="frente-n">03</span>
    <h2 class="frente-h">Design</h2>
    <p class="frente-p">Artes estáticas e carrosséis com identidade visual sob medida para suas redes sociais.</p>
    <span class="frente-arrow">Ver preços →</span>
  </a>
</div>

<!-- PACOTES MENSAIS -->
<section id="pacotes" class="plans-section">
  <div class="s-head reveal">
    <span class="s-tag">Frente 01 — Recorrência</span>
    <h2 class="s-title">Pacotes Mensais</h2>
    <p class="s-desc">Deslize para ver todos os planos. Quanto mais volume, menor o custo por criativo.</p>
  </div>

  <div class="plans-track-wrap" id="plansTrack">

    <!-- INÍCIO -->
    <div class="plan-card">
      <div class="plan-name">Início</div>
      <div class="plan-headline">Presença Digital Essencial</div>
      <p class="plan-desc">Para quem está começando no digital e precisa de presença e geração de leads consistente.</p>
      <div class="plan-count">5</div>
      <div class="plan-count-lbl">criativos / mês</div>
      <div class="plan-count-unit">R$ 250 por criativo</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">1.750</span></div>
      <div class="plan-period">total mensal · tráfego incluso</div>
      <div class="breakdown">
        <div class="br-row"><span>Serviço Saron</span><span>R$ 1.250</span></div>
        <div class="br-row"><span>Verba de tráfego</span><span>R$ 500</span></div>
        <div class="br-row br-total"><span>Total mensal</span><span>R$ 1.750</span></div>
      </div>
      <div class="plan-contract">Contrato mínimo: 4 meses</div>
      <div class="plan-sep"></div>
      <ul class="plan-feats">
        <li><span class="f-dot">✦</span>5 criativos/mês (vídeos, reels ou estáticas)</li>
        <li><span class="f-dot">✦</span>Roteirização e edição inclusos</li>
        <li><span class="f-dot">✦</span>Gestão de tráfego — Meta Ads</li>
        <li><span class="f-dot">✦</span>Copy dos anúncios</li>
        <li><span class="f-dot">✦</span>Relatório mensal · 1 reunião/mês</li>
      </ul>
      <div class="plan-ideal"><strong>Ideal para:</strong> Negócios que estão dando os primeiros passos no digital e querem resultados consistentes desde o início</div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Quero este plano</a>
    </div>

    <!-- CRESCIMENTO -->
    <div class="plan-card">
      <div class="plan-name">Crescimento</div>
      <div class="plan-headline">Presença Acelerada</div>
      <p class="plan-desc">Para quem quer maior frequência de conteúdo e presença em múltiplas plataformas.</p>
      <div class="plan-count">10</div>
      <div class="plan-count-lbl">criativos / mês</div>
      <div class="plan-count-unit">R$ 150 por criativo</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">2.500</span></div>
      <div class="plan-period">total mensal · tráfego incluso</div>
      <div class="breakdown">
        <div class="br-row"><span>Serviço Saron</span><span>R$ 1.500</span></div>
        <div class="br-row"><span>Verba de tráfego</span><span>R$ 1.000</span></div>
        <div class="br-row br-total"><span>Total mensal</span><span>R$ 2.500</span></div>
      </div>
      <div class="plan-contract">Contrato mínimo: 4 meses</div>
      <div class="plan-sep"></div>
      <ul class="plan-feats">
        <li><span class="f-dot">✦</span>10 criativos/mês (vídeos, reels ou estáticas)</li>
        <li><span class="f-dot">✦</span>Roteirização e edição inclusos</li>
        <li><span class="f-dot">✦</span>Gestão de tráfego — Meta Ads + Google Ads</li>
        <li><span class="f-dot">✦</span>Copy estratégico dos anúncios</li>
        <li><span class="f-dot">✦</span>Relatório quinzenal · 2 reuniões/mês</li>
      </ul>
      <div class="plan-ideal"><strong>Ideal para:</strong> Negócios em crescimento que precisam de mais volume de conteúdo e presença em múltiplas plataformas</div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Quero este plano</a>
    </div>

    <!-- ESCALA (featured) -->
    <div class="plan-card is-featured">
      <span class="plan-badge badge-gold">Melhor custo-benefício</span>
      <div class="plan-name">Escala</div>
      <div class="plan-headline">Autoridade & Volume</div>
      <p class="plan-desc">Para negócios que querem dominar o digital com alto volume de conteúdo e estratégia avançada.</p>
      <div class="plan-count">20</div>
      <div class="plan-count-lbl">criativos / mês</div>
      <div class="plan-count-unit">R$ 100 por criativo</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">3.500</span></div>
      <div class="plan-period">total mensal · tráfego incluso</div>
      <div class="breakdown">
        <div class="br-row"><span>Serviço Saron</span><span>R$ 2.000</span></div>
        <div class="br-row"><span>Verba de tráfego</span><span>R$ 1.500</span></div>
        <div class="br-row br-total"><span>Total mensal</span><span>R$ 3.500</span></div>
      </div>
      <div class="plan-contract">Contrato mínimo: 4 meses</div>
      <div class="plan-sep"></div>
      <ul class="plan-feats">
        <li><span class="f-dot">✦</span>20 criativos/mês (vídeos, reels ou estáticas)</li>
        <li><span class="f-dot">✦</span>Roteirização estratégica avançada + edição</li>
        <li><span class="f-dot">✦</span>Gestão de tráfego — Meta + Google + extras</li>
        <li><span class="f-dot">✦</span>Copy + A/B testing dos anúncios</li>
        <li><span class="f-dot">✦</span>Relatório semanal + dashboard · reuniões semanais</li>
      </ul>
      <div class="plan-ideal"><strong>Ideal para:</strong> Negócios que querem dominar o digital com alto volume de conteúdo e estratégia avançada de tráfego</div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-gold">Quero este plano</a>
    </div>

    <!-- ELITE -->
    <div class="plan-card">
      <span class="plan-badge badge-soft">Sob medida</span>
      <div class="plan-name">Elite</div>
      <div class="plan-headline">Estratégia Personalizada</div>
      <p class="plan-desc">Para empresas que precisam de volume e estrutura totalmente customizados.</p>
      <div class="plan-count" style="font-size:42px;color:var(--gold);">∞</div>
      <div class="plan-count-lbl">volume personalizado</div>
      <div class="plan-count-unit" style="visibility:hidden;">—</div>
      <div class="plan-price"><span class="plan-val" style="font-size:26px;color:var(--gold);">Sob consulta</span></div>
      <div class="plan-period">proposta personalizada</div>
      <div class="breakdown" style="border-color:rgba(201,168,76,.08);">
        <div class="br-row"><span>Serviço Saron</span><span>A definir</span></div>
        <div class="br-row"><span>Verba de tráfego</span><span>A definir</span></div>
        <div class="br-row br-total"><span>Total mensal</span><span>Sob proposta</span></div>
      </div>
      <div class="plan-contract">Contrato mínimo: 4 meses</div>
      <div class="plan-sep"></div>
      <ul class="plan-feats">
        <li><span class="f-dot">✦</span>Volume de criativos personalizado</li>
        <li><span class="f-dot">✦</span>Equipe dedicada à conta</li>
        <li><span class="f-dot">✦</span>Multi-plataformas sem limitação</li>
        <li><span class="f-dot">✦</span>Estratégia de conteúdo completa</li>
        <li><span class="f-dot">✦</span>Relatórios e reuniões conforme demanda</li>
      </ul>
      <div class="plan-ideal"><strong>Ideal para:</strong> Empresas que precisam de uma solução exclusiva, com volume e estrutura totalmente personalizados</div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Solicitar proposta</a>
    </div>

  </div><!-- /plans-track-wrap -->

  <!-- dots -->
  <div class="plans-dots" id="plansDots">
    <div class="dot active"></div>
    <div class="dot"></div>
    <div class="dot"></div>
    <div class="dot"></div>
  </div>

  <div class="notice reveal">
    <strong>Transparência total:</strong> Todos os planos já incluem a verba de tráfego no valor total — sem surpresas. O valor do serviço Saron cobre gestão, criativos, roteirização e edição. Contrato mínimo de <strong>4 meses</strong> para calibrar campanhas e gerar resultados consistentes.
  </div>
</section>

<!-- DESIGN -->
<section id="design" class="design-section">
  <div class="s-head reveal">
    <span class="s-tag">Frente 03 — Design</span>
    <h2 class="s-title">Design</h2>
    <p class="s-desc">Artes e carrosséis com identidade visual alinhada à sua marca. Deslize para ver os preços.</p>
  </div>

  <div class="design-track-wrap">

    <!-- 6 ARTES -->
    <div class="design-card-m">
      <div class="design-pkg-name">Pacote</div>
      <div class="design-count">6</div>
      <div class="design-count-lbl">artes estáticas</div>
      <div class="plan-count-unit">≈ R$ 67 por arte</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">400</span></div>
      <div class="plan-period">por pacote</div>
      <div class="breakdown">
        <div class="br-row br-total"><span>Total do pacote</span><span>R$ 400</span></div>
      </div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Solicitar</a>
    </div>

    <!-- 10 ARTES -->
    <div class="design-card-m">
      <div class="design-pkg-name">Pacote</div>
      <div class="design-count">10</div>
      <div class="design-count-lbl">artes estáticas</div>
      <div class="plan-count-unit">R$ 65 por arte</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">650</span></div>
      <div class="plan-period">por pacote</div>
      <div class="breakdown">
        <div class="br-row br-total"><span>Total do pacote</span><span>R$ 650</span></div>
      </div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Solicitar</a>
    </div>

    <!-- 15 ARTES -->
    <div class="design-card-m">
      <div class="design-pkg-name">Pacote</div>
      <div class="design-count">15</div>
      <div class="design-count-lbl">artes estáticas</div>
      <div class="plan-count-unit">≈ R$ 53 por arte</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">800</span></div>
      <div class="plan-period">por pacote</div>
      <div class="breakdown">
        <div class="br-row br-total"><span>Total do pacote</span><span>R$ 800</span></div>
      </div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-outline">Solicitar</a>
    </div>

    <!-- CARROSSEL AVULSO -->
    <div class="design-card-m is-highlight">
      <div class="design-pkg-name">Carrossel</div>
      <div class="design-count">1</div>
      <div class="design-count-lbl">unidade · avulso</div>
      <div class="plan-count-unit">preço por peça</div>
      <div class="plan-price"><span class="plan-cur">R$</span><span class="plan-val">100</span></div>
      <div class="plan-period">por carrossel</div>
      <div class="breakdown">
        <div class="br-row br-total"><span>Valor unitário</span><span>R$ 100</span></div>
      </div>
      <a href="https://wa.me/5562982456003" class="plan-btn btn-gold">Solicitar</a>
    </div>

  </div>
</section>

<!-- PROJETOS PONTUAIS -->
<section id="projetos" class="projects-section">
  <div class="s-head reveal">
    <span class="s-tag">Frente 02 — Pontual</span>
    <h2 class="s-title">Projetos Pontuais</h2>
    <p class="s-desc">Entregas específicas sem recorrência. Toque em cada projeto para ver os detalhes.</p>
  </div>
  <div class="proj-list">

    <div class="proj-item proj-hero open">
      <button class="proj-trigger" onclick="toggleProj(this)">
        <div class="proj-trigger-left">
          <span class="proj-tag-sm">Projeto Premium</span>
          <span class="proj-name-sm">Lançamento de Marca</span>
        </div>
        <span class="proj-price-sm">R$ 4.997</span>
        <span class="proj-chevron">▾</span>
      </button>
      <div class="proj-body">
        <p class="proj-body-desc">Estratégia completa de 30 a 60 dias para apresentar sua marca ao mercado com impacto real.</p>
        <div class="proj-body-list">
          <span>Estratégia de lançamento (30 a 60 dias)</span>
          <span>12 a 15 criativos com roteiro e edição</span>
          <span>Gestão de tráfego durante o período</span>
          <span>Copy completo dos anúncios</span>
          <span>Relatório de resultados ao final</span>
        </div>
        <p class="proj-body-note">Verba de tráfego à parte</p>
      </div>
    </div>

    <div class="proj-item">
      <button class="proj-trigger" onclick="toggleProj(this)">
        <div class="proj-trigger-left">
          <span class="proj-tag-sm">Produção</span>
          <span class="proj-name-sm">Kit Identidade Digital</span>
        </div>
        <span class="proj-price-sm">R$ 1.997</span>
        <span class="proj-chevron">▾</span>
      </button>
      <div class="proj-body">
        <p class="proj-body-desc">Conjunto de criativos que estabelecem presença e autoridade da marca nas redes desde o primeiro dia.</p>
        <div class="proj-body-list">
          <span>5 a 8 criativos temáticos</span>
          <span>Roteirização completa de cada peça</span>
          <span>Edição com identidade visual da marca</span>
        </div>
      </div>
    </div>

    <div class="proj-item">
      <button class="proj-trigger" onclick="toggleProj(this)">
        <div class="proj-trigger-left">
          <span class="proj-tag-sm">Campanha</span>
          <span class="proj-name-sm">Campanha Sazonal</span>
        </div>
        <span class="proj-price-sm">R$ 2.997</span>
        <span class="proj-chevron">▾</span>
      </button>
      <div class="proj-body">
        <p class="proj-body-desc">Para datas especiais, ofertas pontuais ou períodos de alta demanda.</p>
        <div class="proj-body-list">
          <span>Estratégia e briefing da campanha</span>
          <span>6 a 10 criativos com roteiro e edição</span>
          <span>Gestão de tráfego por 30 dias</span>
        </div>
      </div>
    </div>

    <div class="proj-item">
      <button class="proj-trigger" onclick="toggleProj(this)">
        <div class="proj-trigger-left">
          <span class="proj-tag-sm">Conteúdo</span>
          <span class="proj-name-sm">Pacote de Criativos Avulso</span>
        </div>
        <span class="proj-price-sm">a partir de R$ 1.497</span>
        <span class="proj-chevron">▾</span>
      </button>
      <div class="proj-body">
        <p class="proj-body-desc">Para quem já tem estrutura de tráfego e precisa de criativos de qualidade.</p>
        <div class="proj-body-list">
          <span>Pacote de 5, 10 ou 20 criativos</span>
          <span>Roteiro + edição inclusos</span>
          <span>Sem gestão de tráfego inclusa</span>
        </div>
      </div>
    </div>

    <div class="proj-item">
      <button class="proj-trigger" onclick="toggleProj(this)">
        <div class="proj-trigger-left">
          <span class="proj-tag-sm">Audiovisual</span>
          <span class="proj-name-sm">Vídeo Institucional</span>
        </div>
        <span class="proj-price-sm">Sob consulta</span>
        <span class="proj-chevron">▾</span>
      </button>
      <div class="proj-body">
        <p class="proj-body-desc">Produção audiovisual específica para apresentação corporativa ou pitch de captação.</p>
        <div class="proj-body-list">
          <span>Roteirização e direção conceitual</span>
          <span>Produção e edição profissional</span>
          <span>Adaptação para múltiplos formatos</span>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- NICHOS -->
<section id="nichos" class="nichos-section">
  <div class="s-head reveal">
    <span class="s-tag">Quem atendemos</span>
    <h2 class="s-title">Segmentos</h2>
    <p class="s-desc">Especialistas nos mercados onde conteúdo e tráfego fazem mais diferença.</p>
  </div>
  <div class="nichos-grid">
    <div class="nicho reveal"><span class="nicho-ico">🤝</span><div class="nicho-name">Consórcio</div><div class="nicho-sub">Geração de leads · Autoridade</div></div>
    <div class="nicho reveal"><span class="nicho-ico">🏠</span><div class="nicho-name">Imóveis</div><div class="nicho-sub">Captação de compradores</div></div>
    <div class="nicho reveal"><span class="nicho-ico">⚖️</span><div class="nicho-name">Advogados</div><div class="nicho-sub">Autoridade · Captação</div></div>
    <div class="nicho reveal"><span class="nicho-ico">🚀</span><div class="nicho-name">Infoprodutores</div><div class="nicho-sub">Lançamentos · Escala</div></div>
    <div class="nicho reveal"><span class="nicho-ico">🏗️</span><div class="nicho-name">Construtoras</div><div class="nicho-sub">Lançamentos imobiliários</div></div>
    <div class="nicho reveal"><span class="nicho-ico">💼</span><div class="nicho-name">Agentes</div><div class="nicho-sub">Geração de oportunidades</div></div>
    <div class="nicho reveal"><span class="nicho-ico">🛒</span><div class="nicho-name">Supermercados</div><div class="nicho-sub">Promoções · Local</div></div>
    <div class="nicho reveal"><span class="nicho-ico">🍽️</span><div class="nicho-name">Restaurantes</div><div class="nicho-sub">Delivery · Reservas</div></div>
    <div class="nicho reveal" style="grid-column: 1/-1;flex-direction:row;align-items:center;gap:12px;"><span class="nicho-ico">👗</span><div><div class="nicho-name">Lojas de Roupas</div><div class="nicho-sub">Moda · Lançamentos · Tráfego físico e online</div></div></div>
  </div>
</section>

<!-- DIFERENCIAIS -->
<section id="diferenciais" class="diff-section">
  <div class="s-head reveal">
    <span class="s-tag">Por que a Saron</span>
    <h2 class="s-title">Nossos Diferenciais</h2>
    <p class="s-desc">Não somos apenas uma agência. Somos parceiros no resultado do seu negócio.</p>
  </div>
  <div class="diff-list reveal">
    <div class="diff-item"><span class="diff-ico">🎬</span><div><div class="diff-title">Audiovisual + Tráfego</div><p class="diff-txt">Produção de criativos e gestão de tráfego em um único parceiro. Menos fricção, mais resultado.</p></div></div>
    <div class="diff-item"><span class="diff-ico">🎯</span><div><div class="diff-title">Foco em Resultado</div><p class="diff-txt">Cada criativo e cada real investido têm uma finalidade: gerar leads qualificados e conversões reais.</p></div></div>
    <div class="diff-item"><span class="diff-ico">📊</span><div><div class="diff-title">Transparência Total</div><p class="diff-txt">Serviço e verba separados com clareza. Você sabe exatamente onde cada real é investido.</p></div></div>
    <div class="diff-item"><span class="diff-ico">🌱</span><div><div class="diff-title">Crescimento Conjunto</div><p class="diff-txt">Crescemos junto com o seu negócio. Nossos planos escalam conforme sua demanda evolui.</p></div></div>
    <div class="diff-item"><span class="diff-ico">⚡</span><div><div class="diff-title">Especialização por Nicho</div><p class="diff-txt">Conhecemos a linguagem e as objeções do seu mercado. Isso acelera os resultados.</p></div></div>
    <div class="diff-item"><span class="diff-ico">✦</span><div><div class="diff-title">Compromisso Perpétuo</div><p class="diff-txt">Assim como a Rosa de Sarom, nosso compromisso com a qualidade e o seu crescimento é inabalável.</p></div></div>
  </div>
</section>

<!-- CTA FINAL -->
<section id="contato" class="cta-final">
  <div class="cta-final-inner">
    <span class="cta-final-tag">Próximo passo</span>
    <h2 class="cta-final-title">Pronto para <em>crescer</em>?</h2>
    <p class="cta-final-sub">Uma conversa de 30 minutos pode transformar como o seu negócio aparece no digital.</p>
  </div>
</section>

<!-- FOOTER -->
<footer class="footer">
  <span class="footer-logo">SARON COMPANY</span>
  <p class="footer-sub">Audiovisual · Tráfego Pago · 2026</p>
  <p class="footer-tag">A planície fértil do seu negócio começa aqui.</p>
</footer>

<script>
  // Menu drawer
  function closeDrawer() {
    document.getElementById('drawer').classList.remove('open');
  }
  document.getElementById('menuBtn').addEventListener('click', () => {
    document.getElementById('drawer').classList.add('open');
  });
  document.getElementById('drawerClose').addEventListener('click', closeDrawer);
  document.getElementById('drawer').addEventListener('click', e => {
    if (e.target === e.currentTarget) closeDrawer();
  });

  // Smooth anchor scroll
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      const t = document.querySelector(a.getAttribute('href'));
      if (t) { e.preventDefault(); window.scrollTo({ top: t.getBoundingClientRect().top + scrollY - 56, behavior: 'smooth' }); }
    });
  });

  // Plans track dots
  const track = document.getElementById('plansTrack');
  const dots  = document.querySelectorAll('#plansDots .dot');
  const cards = track.querySelectorAll('.plan-card');
  if (track && dots.length) {
    track.addEventListener('scroll', () => {
      const idx = Math.round(track.scrollLeft / (cards[0].offsetWidth + 14));
      dots.forEach((d, i) => d.classList.toggle('active', i === idx));
    }, { passive: true });
  }

  // Accordion projetos
  function toggleProj(btn) {
    const item = btn.closest('.proj-item');
    item.classList.toggle('open');
  }

  // Scroll reveal
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); } });
  }, { threshold: 0.08 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
</script>
</body>
</html>
