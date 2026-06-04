<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Caille d'Or — Ferme Premium · Madagascar</title>
  <meta name="description" content="Caille d'Or élève des cailles en plein air à Madagascar. Œufs frais, viande de caille premium, livraison rapide à Antananarivo." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #080a06;
      --bg-soft: #0e120a;
      --surface: rgba(255,255,255,0.05);
      --surface-strong: rgba(255,255,255,0.09);
      --stroke: rgba(255,255,255,0.1);
      --text: #f0ead8;
      --muted: #9a9080;
      --gold: #c9973a;
      --gold-light: #e8c87a;
      --gold-dim: rgba(201,151,58,0.18);
      --green: #4a7c3f;
      --green-light: #7ab86a;
      --green-dim: rgba(74,124,63,0.18);
      --cream: #f5ead0;
      --glow-gold: 0 0 28px rgba(201,151,58,0.28), 0 0 60px rgba(201,151,58,0.1);
      --glow-green: 0 0 22px rgba(74,124,63,0.3);
      --radius-xl: 28px;
      --radius-lg: 20px;
      --radius-md: 14px;
      --shadow: 0 12px 50px rgba(0,0,0,0.5);
      --max-width: 1240px;
      --nav-height: 80px;
      --transition: 300ms cubic-bezier(.2,.8,.2,1);
    }

    *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'DM Sans', sans-serif;
      background:
        radial-gradient(circle at 10% 15%, rgba(201,151,58,0.1), transparent 22%),
        radial-gradient(circle at 85% 5%, rgba(74,124,63,0.14), transparent 22%),
        radial-gradient(circle at 75% 75%, rgba(201,151,58,0.07), transparent 18%),
        linear-gradient(180deg, #050705 0%, #080b06 40%, #060807 100%);
      color: var(--text);
      overflow-x: hidden;
      min-height: 100vh;
    }

    body::before {
      content: "";
      position: fixed; inset: 0; z-index: 0; pointer-events: none;
      background-image:
        linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
      background-size: 52px 52px;
      mask-image: radial-gradient(ellipse at center, black 30%, transparent 85%);
    }

    canvas#bgCanvas {
      position: fixed; inset: 0; width: 100%; height: 100%;
      z-index: 0; opacity: 0.6; pointer-events: none;
    }

    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }
    button { font: inherit; border: none; background: none; color: inherit; cursor: pointer; }

    .container {
      width: min(100% - 32px, var(--max-width));
      margin: 0 auto;
      position: relative; z-index: 2;
    }

    .section { padding: 110px 0; position: relative; }

    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.2rem, 3.2vw, 3.6rem);
      font-weight: 600;
      line-height: 1.08;
      letter-spacing: -0.02em;
      margin-bottom: 18px;
    }

    .section-subtitle {
      max-width: 700px;
      color: var(--muted);
      font-size: 1.02rem;
      line-height: 1.8;
      font-weight: 300;
    }

    .eyebrow {
      display: inline-flex; align-items: center; gap: 10px;
      padding: 9px 16px; margin-bottom: 20px;
      border-radius: 999px;
      border: 1px solid rgba(201,151,58,0.25);
      background: rgba(201,151,58,0.08);
      color: #e8c87a;
      font-size: 0.88rem; font-weight: 500; letter-spacing: 0.06em;
      text-transform: uppercase; width: fit-content;
      backdrop-filter: blur(12px);
    }

    .eyebrow-dot {
      width: 8px; height: 8px; border-radius: 50%;
      background: linear-gradient(135deg, var(--gold), var(--green-light));
      box-shadow: 0 0 14px var(--gold);
    }

    .glass {
      background: linear-gradient(160deg, rgba(255,255,255,0.07), rgba(255,255,255,0.03));
      border: 1px solid var(--stroke);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
    }

    /* ─── NAVBAR ─── */
    .navbar {
      position: sticky; top: 0; z-index: 50;
      height: var(--nav-height);
      display: flex; align-items: center;
    }

    .navbar.scrolled .nav-shell {
      background: rgba(8,10,6,0.82);
      border-color: rgba(201,151,58,0.15);
      box-shadow: 0 8px 30px rgba(0,0,0,0.3);
    }

    .nav-shell {
      width: min(100% - 24px, var(--max-width));
      margin: 10px auto 0;
      padding: 12px 20px;
      border-radius: 18px;
      border: 1px solid transparent;
      display: flex; align-items: center; justify-content: space-between;
      transition: all var(--transition);
      position: relative; z-index: 2;
    }

    .brand {
      display: flex; align-items: center; gap: 12px;
      font-family: 'Cormorant Garamond', serif;
      font-weight: 700; font-size: 1.3rem; letter-spacing: 0.05em;
    }

    .brand-mark {
      width: 42px; height: 42px; border-radius: 14px;
      display: grid; place-items: center;
      background: linear-gradient(135deg, rgba(201,151,58,0.3), rgba(74,124,63,0.22));
      border: 1px solid rgba(201,151,58,0.28);
      box-shadow: var(--glow-gold);
      font-size: 1.3rem;
      position: relative; overflow: hidden;
    }

    .brand-mark::before {
      content: "";
      position: absolute; inset: -40%;
      background: conic-gradient(from 0deg, transparent, rgba(201,151,58,0.4), transparent, rgba(74,124,63,0.35), transparent);
      animation: spin 10s linear infinite;
    }

    .brand-mark span { position: relative; z-index: 1; }

    .nav-links {
      display: flex; align-items: center; gap: 28px;
    }

    .nav-links a {
      color: var(--muted); font-weight: 400; font-size: 0.95rem;
      position: relative; transition: color var(--transition);
    }

    .nav-links a:hover { color: var(--text); }

    .nav-links a::after {
      content: "";
      position: absolute; left: 0; bottom: -6px;
      width: 0; height: 1px; border-radius: 999px;
      background: linear-gradient(90deg, var(--gold), var(--green-light));
      transition: width var(--transition);
    }

    .nav-links a:hover::after { width: 100%; }

    .nav-actions { display: flex; align-items: center; gap: 12px; }

    .menu-toggle {
      display: none; width: 44px; height: 44px; border-radius: 12px;
      align-items: center; justify-content: center;
      border: 1px solid var(--stroke); background: rgba(255,255,255,0.04);
    }

    .menu-toggle span,
    .menu-toggle span::before,
    .menu-toggle span::after {
      width: 18px; height: 1.5px; background: var(--text); display: block;
      border-radius: 999px; position: relative;
      transition: transform var(--transition), opacity var(--transition), top var(--transition);
      content: "";
    }

    .menu-toggle span::before, .menu-toggle span::after { position: absolute; left: 0; }
    .menu-toggle span::before { top: -6px; }
    .menu-toggle span::after { top: 6px; }
    .menu-toggle.active span { background: transparent; }
    .menu-toggle.active span::before { top: 0; transform: rotate(45deg); }
    .menu-toggle.active span::after { top: 0; transform: rotate(-45deg); }

    /* ─── BUTTONS ─── */
    .btn {
      display: inline-flex; align-items: center; justify-content: center; gap: 10px;
      min-height: 50px; padding: 0 24px; border-radius: 14px; font-weight: 500;
      transition: transform var(--transition), box-shadow var(--transition), background var(--transition);
      position: relative; overflow: hidden; isolation: isolate; font-size: 0.95rem;
    }

    .btn:hover { transform: translateY(-2px); }

    .btn-primary {
      background: linear-gradient(135deg, rgba(201,151,58,0.22), rgba(74,124,63,0.18));
      border: 1px solid rgba(201,151,58,0.3);
      box-shadow: var(--glow-gold); color: var(--cream);
    }

    .btn-primary::before {
      content: "";
      position: absolute; inset: 0;
      background: linear-gradient(110deg, transparent, rgba(255,255,255,0.14), transparent);
      transform: translateX(-120%); transition: transform 700ms ease; z-index: -1;
    }

    .btn-primary:hover::before { transform: translateX(120%); }

    .btn-secondary {
      background: rgba(255,255,255,0.04);
      border: 1px solid var(--stroke); color: #d8d0c0;
    }

    /* ─── HERO ─── */
    .hero { padding-top: 36px; padding-bottom: 90px; overflow: hidden; }

    .hero-grid {
      display: grid; grid-template-columns: 1.15fr 0.85fr;
      align-items: center; gap: 50px;
      min-height: calc(100vh - 120px);
    }

    .hero-copy { position: relative; z-index: 3; }

    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3rem, 7vw, 6.4rem);
      line-height: 0.95; letter-spacing: -0.04em; margin-bottom: 24px;
    }

    .hero-title .gradient {
      background: linear-gradient(90deg, #f0ead8 0%, #e8c87a 30%, #a8d48a 65%, #c9973a 100%);
      -webkit-background-clip: text; background-clip: text; color: transparent;
    }

    .hero-description {
      max-width: 680px; color: var(--muted); font-size: 1.05rem;
      line-height: 1.9; margin-bottom: 30px; font-weight: 300;
    }

    .hero-actions { display: flex; flex-wrap: wrap; gap: 14px; margin-bottom: 36px; }

    .hero-metrics { display: flex; flex-wrap: wrap; gap: 16px; }

    .metric-chip {
      padding: 14px 18px; border-radius: 16px;
      border: 1px solid var(--stroke); background: rgba(255,255,255,0.04);
      min-width: 145px;
    }

    .metric-chip strong { display: block; font-size: 1.1rem; margin-bottom: 4px; color: var(--gold-light); }
    .metric-chip span { color: var(--muted); font-size: 0.9rem; }

    /* ─── HERO VISUAL ─── */
    .hero-visual {
      position: relative; min-height: 600px;
      display: flex; align-items: center; justify-content: center;
      perspective: 1200px;
    }

    .orb {
      position: absolute; border-radius: 50%;
      filter: blur(12px); opacity: 0.65;
      animation: floatY 9s ease-in-out infinite;
    }

    .orb-1 {
      width: 260px; height: 260px; top: 70px; right: 50px;
      background: radial-gradient(circle at 30% 30%, rgba(201,151,58,0.8), rgba(201,151,58,0.04) 65%);
    }

    .orb-2 {
      width: 200px; height: 200px; bottom: 110px; left: 10px;
      background: radial-gradient(circle at 30% 30%, rgba(74,124,63,0.9), rgba(74,124,63,0.04) 65%);
      animation-delay: -3s;
    }

    .orb-3 {
      width: 120px; height: 120px; top: 48%; right: 8%;
      background: radial-gradient(circle at 30% 30%, rgba(232,200,122,0.75), rgba(232,200,122,0.04) 65%);
      animation-delay: -5s;
    }

    .dashboard {
      width: min(100%, 540px); padding: 20px; border-radius: var(--radius-xl);
      position: relative; transform-style: preserve-3d;
      transform: rotateY(-10deg) rotateX(6deg);
      background: linear-gradient(160deg, rgba(255,255,255,0.08), rgba(255,255,255,0.03));
      border: 1px solid rgba(201,151,58,0.18);
      box-shadow: 0 24px 80px rgba(0,0,0,0.5), var(--glow-gold);
    }

    .dashboard::before {
      content: "";
      position: absolute; inset: 0; border-radius: inherit; padding: 1px;
      background: linear-gradient(135deg, rgba(201,151,58,0.5), rgba(74,124,63,0.35), rgba(232,200,122,0.25));
      -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
      -webkit-mask-composite: xor; mask-composite: exclude;
      opacity: 0.85; pointer-events: none;
    }

    .dashboard-top {
      display: flex; justify-content: space-between; align-items: center; margin-bottom: 18px;
    }

    .dashboard-title { font-weight: 600; font-size: 0.92rem; letter-spacing: 0.04em; color: var(--cream); }

    .status {
      display: inline-flex; align-items: center; gap: 8px;
      padding: 8px 14px; border-radius: 999px;
      background: rgba(74,124,63,0.12); color: #a8d48a;
      border: 1px solid rgba(74,124,63,0.22); font-size: 0.88rem;
    }

    .status::before {
      content: "";
      width: 7px; height: 7px; border-radius: 50%;
      background: var(--green-light); box-shadow: 0 0 14px var(--green-light);
    }

    .dashboard-grid { display: grid; grid-template-columns: 1.4fr 1fr; gap: 14px; }

    .panel {
      border-radius: 18px; padding: 16px;
      background: rgba(6, 8, 4, 0.6);
      border: 1px solid rgba(255,255,255,0.07);
    }

    .panel.large { min-height: 270px; }
    .panel.small { min-height: 130px; }

    .panel-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 14px; }
    .panel-header h4 { font-size: 0.9rem; color: var(--cream); font-weight: 500; }
    .panel-header span { color: var(--muted); font-size: 0.82rem; }

    .bars { display: flex; align-items: end; gap: 9px; height: 170px; }

    .bar {
      flex: 1; border-radius: 10px 10px 4px 4px;
      background: linear-gradient(180deg, rgba(201,151,58,0.95), rgba(74,124,63,0.3));
      box-shadow: 0 0 18px rgba(201,151,58,0.18);
      animation: rise 1.4s ease forwards;
      transform-origin: bottom; transform: scaleY(0.1);
    }

    .mini-cards { display: grid; gap: 12px; }

    .mini-card {
      padding: 14px; border-radius: 14px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.07);
    }

    .mini-card strong { display: block; font-size: 1.1rem; margin-bottom: 4px; color: var(--gold-light); }
    .mini-card span { color: var(--muted); font-size: 0.88rem; }

    .radial-wrap { position: relative; display: grid; place-items: center; height: 170px; }

    .radial {
      width: 130px; height: 130px; border-radius: 50%;
      background:
        radial-gradient(closest-side, #080b06 72%, transparent 73% 100%),
        conic-gradient(var(--gold) 0 82%, rgba(255,255,255,0.07) 82% 100%);
      display: grid; place-items: center;
      box-shadow: inset 0 0 24px rgba(0,0,0,0.3), 0 0 22px rgba(201,151,58,0.15);
    }

    .radial strong {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.7rem; font-weight: 600; color: var(--cream);
    }

    .floating-tag {
      position: absolute; padding: 9px 14px;
      border-radius: 999px;
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(201,151,58,0.2);
      color: #ddd5c0; font-size: 0.88rem;
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
    }

    .floating-tag.tag-1 { top: 8%; left: -6%; }
    .floating-tag.tag-2 { bottom: 10%; right: -8%; }
    .floating-tag.tag-3 { top: 50%; left: -10%; }

    /* ─── PRODUITS ─── */
    .produits-grid {
      margin-top: 46px;
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 22px;
    }

    .produit-card {
      padding: 28px; border-radius: 24px;
      position: relative; overflow: hidden;
      transition: transform var(--transition), border-color var(--transition), box-shadow var(--transition);
      transform-style: preserve-3d;
    }

    .produit-card:hover {
      transform: translateY(-8px) rotateX(2deg) rotateY(-2deg);
      border-color: rgba(201,151,58,0.25);
      box-shadow: 0 20px 50px rgba(0,0,0,0.35), var(--glow-gold);
    }

    .produit-card::before {
      content: "";
      position: absolute; inset: auto -8% -35% auto;
      width: 160px; height: 160px;
      background: radial-gradient(circle, rgba(201,151,58,0.12), transparent 70%);
      pointer-events: none;
    }

    .icon-box {
      width: 56px; height: 56px; border-radius: 16px;
      display: grid; place-items: center; margin-bottom: 18px;
      background: linear-gradient(135deg, rgba(201,151,58,0.2), rgba(74,124,63,0.15));
      border: 1px solid rgba(201,151,58,0.18);
      font-size: 1.5rem;
    }

    .produit-card h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.45rem; font-weight: 600; margin-bottom: 10px;
    }

    .produit-card p { color: var(--muted); line-height: 1.8; margin-bottom: 18px; font-size: 0.95rem; }

    .prix-line {
      display: flex; align-items: center; justify-content: space-between;
      margin-bottom: 16px;
    }

    .prix { font-size: 1.3rem; font-weight: 600; color: var(--gold-light); }
    .prix span { font-size: 0.82rem; color: var(--muted); font-weight: 300; }

    .card-link {
      display: inline-flex; align-items: center; gap: 8px;
      color: #c9973a; font-weight: 500; font-size: 0.9rem;
      transition: gap var(--transition);
    }

    .card-link:hover { gap: 12px; }

    /* ─── ABOUT ─── */
    .about-grid {
      display: grid; grid-template-columns: 1fr 1fr; gap: 28px;
      align-items: stretch; margin-top: 44px;
    }

    .about-panel { border-radius: 28px; padding: 32px; position: relative; overflow: hidden; }
    .about-panel p { color: var(--muted); line-height: 1.9; margin-bottom: 18px; font-size: 0.97rem; }

    .story-points { display: grid; gap: 14px; margin-top: 22px; }

    .story-item {
      display: flex; gap: 14px; align-items: flex-start;
      padding: 16px; border-radius: 16px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.07);
    }

    .story-item .bullet {
      flex: 0 0 10px; width: 10px; height: 10px; margin-top: 7px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--gold), var(--green-light));
      box-shadow: 0 0 14px rgba(201,151,58,0.5);
    }

    .story-item strong { display: block; margin-bottom: 4px; font-size: 0.95rem; }
    .story-item span { color: var(--muted); font-size: 0.9rem; line-height: 1.7; }

    .about-visual { display: grid; gap: 18px; }

    .vision-card, .mission-card {
      border-radius: 24px; padding: 26px; min-height: 200px;
      position: relative; overflow: hidden;
    }

    .vision-card h3, .mission-card h3 {
      font-family: 'Cormorant Garamond', serif;
      margin-bottom: 12px; font-size: 1.4rem; font-weight: 600;
    }

    .vision-card p, .mission-card p { color: var(--muted); line-height: 1.8; font-size: 0.95rem; }

    .signal-lines {
      display: flex; gap: 8px; align-items: end; height: 60px; margin-top: 18px;
    }

    .signal-lines span {
      width: 7px; border-radius: 999px;
      background: linear-gradient(180deg, var(--gold), var(--green));
      animation: pulseBar 1.5s ease-in-out infinite;
    }

    .signal-lines span:nth-child(1) { height: 20px; animation-delay: 0s; }
    .signal-lines span:nth-child(2) { height: 38px; animation-delay: .15s; }
    .signal-lines span:nth-child(3) { height: 56px; animation-delay: .3s; }
    .signal-lines span:nth-child(4) { height: 30px; animation-delay: .45s; }
    .signal-lines span:nth-child(5) { height: 48px; animation-delay: .6s; }

    /* ─── STATS ─── */
    .stats-grid {
      margin-top: 44px;
      display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px;
    }

    .stat-card { padding: 28px 22px; border-radius: 24px; position: relative; overflow: hidden; }

    .stat-number {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 4vw, 3.2rem); font-weight: 600;
      margin-bottom: 8px; display: flex; align-items: baseline; gap: 4px;
      color: var(--gold-light);
    }

    .stat-label { color: var(--muted); line-height: 1.7; font-size: 0.92rem; }

    /* ─── TESTIMONIALS ─── */
    .testimonials-grid {
      margin-top: 44px;
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 22px;
    }

    .testimonial-card { padding: 26px; border-radius: 24px; position: relative; overflow: hidden; }

    .testimonial-top { display: flex; align-items: center; gap: 14px; margin-bottom: 18px; }

    .avatar {
      width: 50px; height: 50px; border-radius: 16px;
      display: grid; place-items: center; font-weight: 700;
      font-family: 'Cormorant Garamond', serif; font-size: 1.2rem;
      color: var(--cream);
      background: linear-gradient(135deg, rgba(201,151,58,0.45), rgba(74,124,63,0.4));
      box-shadow: var(--glow-gold);
    }

    .testimonial-meta strong { display: block; margin-bottom: 3px; font-size: 0.95rem; }
    .testimonial-meta span { color: var(--muted); font-size: 0.88rem; }

    .testimonial-quote { color: #c8c0ae; line-height: 1.85; margin-bottom: 18px; font-size: 0.95rem; font-style: italic; }

    .stars { color: var(--gold); letter-spacing: 3px; }

    /* ─── CTA ─── */
    .cta-panel {
      margin-top: 28px; border-radius: 32px;
      padding: 44px 36px;
      display: grid; grid-template-columns: 1.1fr 0.9fr;
      gap: 28px; align-items: center;
      position: relative; overflow: hidden;
    }

    .cta-panel::before {
      content: "";
      position: absolute; inset: -20% auto auto -10%;
      width: 360px; height: 360px;
      background: radial-gradient(circle, rgba(201,151,58,0.14), transparent 65%);
      pointer-events: none;
    }

    .cta-panel::after {
      content: "";
      position: absolute; inset: auto -8% -30% auto;
      width: 340px; height: 340px;
      background: radial-gradient(circle, rgba(74,124,63,0.16), transparent 65%);
      pointer-events: none;
    }

    .cta-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.2vw, 3.2rem); line-height: 1.05; margin-bottom: 14px;
      font-weight: 600;
    }

    .cta-text { color: var(--muted); line-height: 1.85; }

    .cta-actions {
      display: flex; justify-content: flex-end; align-items: center;
      gap: 14px; flex-wrap: wrap;
    }

    /* ─── MODAL COMMANDE ─── */
    .modal-overlay {
      display: none; position: fixed; inset: 0;
      background: rgba(0,0,0,0.75); z-index: 200;
      align-items: center; justify-content: center;
      backdrop-filter: blur(6px);
    }

    .modal-overlay.active { display: flex; }

    .modal {
      background: linear-gradient(160deg, #0f1409, #080b06);
      border: 1px solid rgba(201,151,58,0.25);
      border-radius: 24px; padding: 40px;
      width: 90%; max-width: 440px; position: relative;
      box-shadow: 0 30px 80px rgba(0,0,0,0.6), var(--glow-gold);
    }

    .modal h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem; font-weight: 600; color: var(--cream); margin-bottom: 6px;
    }

    .modal .subtitle { font-size: 0.9rem; color: var(--muted); margin-bottom: 26px; }

    .close-modal {
      position: absolute; top: 16px; right: 16px;
      font-size: 20px; cursor: pointer; color: var(--muted);
      width: 34px; height: 34px; display: flex; align-items: center; justify-content: center;
      border-radius: 8px; border: 1px solid var(--stroke);
      background: rgba(255,255,255,0.04);
    }

    .form-group { margin-bottom: 16px; }

    .form-group label {
      display: block; font-size: 0.88rem; font-weight: 500;
      color: #c0b89e; margin-bottom: 7px;
    }

    .form-group input, .form-group select, .form-group textarea {
      width: 100%; padding: 12px 14px;
      border: 1px solid rgba(201,151,58,0.2);
      border-radius: 10px; font-size: 0.95rem;
      font-family: 'DM Sans', sans-serif;
      color: var(--cream); outline: none;
      background: rgba(255,255,255,0.04);
      transition: border-color var(--transition);
    }

    .form-group input:focus, .form-group select:focus {
      border-color: var(--gold);
    }

    .form-group select option { background: #0e120a; }

    .qty-control { display: flex; align-items: center; gap: 14px; }

    .qty-btn {
      width: 36px; height: 36px; border-radius: 50%;
      border: 1px solid rgba(201,151,58,0.3);
      background: rgba(201,151,58,0.08);
      font-size: 20px; cursor: pointer; color: var(--gold-light);
      display: flex; align-items: center; justify-content: center;
      transition: background var(--transition);
    }

    .qty-btn:hover { background: rgba(201,151,58,0.18); }

    .qty-display {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem; font-weight: 600; color: var(--cream);
      min-width: 36px; text-align: center;
    }

    .total-line {
      background: rgba(201,151,58,0.08);
      border: 1px solid rgba(201,151,58,0.2);
      border-radius: 12px; padding: 14px 18px;
      display: flex; justify-content: space-between; align-items: center;
      margin: 20px 0;
    }

    .total-line span { font-size: 0.9rem; color: #c9973a; }
    .total-line strong { font-size: 1.3rem; font-family: 'Cormorant Garamond', serif; color: var(--cream); }

    .wa-order-btn {
      width: 100%; background: #25D366; color: white; border: none;
      padding: 15px; border-radius: 12px; font-size: 1rem; font-weight: 500;
      cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 10px;
      font-family: 'DM Sans', sans-serif;
      transition: background var(--transition), transform var(--transition);
    }

    .wa-order-btn:hover { background: #1EBD59; transform: translateY(-1px); }

    /* ─── FOOTER ─── */
    .footer { padding: 30px 0 50px; }

    .footer-shell {
      padding: 24px 28px; border-radius: 22px;
      display: flex; justify-content: space-between; align-items: center;
      gap: 20px; flex-wrap: wrap;
    }

    .footer-left p { color: var(--muted); margin-top: 8px; font-size: 0.9rem; }

    .footer-links, .socials {
      display: flex; flex-wrap: wrap; align-items: center; gap: 16px;
    }

    .footer-links a { color: var(--muted); font-size: 0.9rem; transition: color var(--transition); }
    .footer-links a:hover { color: var(--text); }

    .socials a {
      width: 40px; height: 40px;
      display: grid; place-items: center; border-radius: 12px;
      border: 1px solid rgba(255,255,255,0.09);
      background: rgba(255,255,255,0.04); color: var(--muted);
      transition: color var(--transition), border-color var(--transition);
    }

    .socials a:hover { color: var(--gold); border-color: rgba(201,151,58,0.3); }

    /* ─── CURSOR AURA ─── */
    .cursor-aura {
      position: fixed; width: 200px; height: 200px;
      border-radius: 50%; pointer-events: none;
      background: radial-gradient(circle, rgba(201,151,58,0.09), rgba(74,124,63,0.05) 45%, transparent 70%);
      filter: blur(16px);
      transform: translate(-50%, -50%); z-index: 1;
      opacity: 0; transition: opacity 300ms ease;
    }

    body:hover .cursor-aura { opacity: 1; }

    /* ─── REVEAL ─── */
    .reveal {
      opacity: 0; transform: translateY(24px);
      transition: opacity 800ms ease, transform 800ms ease;
    }

    .reveal.is-visible { opacity: 1; transform: translateY(0); }

    /* ─── ANIMATIONS ─── */
    @keyframes spin { to { transform: rotate(360deg); } }
    @keyframes floatY {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-16px); }
    }
    @keyframes rise { to { transform: scaleY(1); } }
    @keyframes pulseBar {
      0%, 100% { opacity: 0.5; transform: scaleY(0.88); }
      50% { opacity: 1; transform: scaleY(1.1); }
    }

    /* ─── NAV MOBILE ─── */
    .nav-mobile {
      position: absolute; left: 0; right: 0; top: calc(100% + 10px);
      padding: 18px; border-radius: 18px;
      opacity: 0; visibility: hidden; transform: translateY(-8px);
      transition: all var(--transition);
      background: rgba(8,10,6,0.95);
      border: 1px solid rgba(201,151,58,0.2);
      backdrop-filter: blur(18px);
      display: grid; gap: 10px;
    }

    .nav-shell.open .nav-mobile { opacity: 1; visibility: visible; transform: translateY(0); }

    .nav-mobile a, .nav-mobile button {
      padding: 13px 16px; border-radius: 12px;
      background: rgba(255,255,255,0.04); color: #d8d0c0; font-weight: 500;
    }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 1100px) {
      .hero-grid, .about-grid, .cta-panel, .dashboard-grid { grid-template-columns: 1fr; }
      .hero-visual { min-height: 480px; }
      .produits-grid, .testimonials-grid { grid-template-columns: repeat(2, 1fr); }
      .stats-grid { grid-template-columns: repeat(2, 1fr); }
      .cta-actions { justify-content: flex-start; }
    }

    @media (max-width: 820px) {
      .nav-links, .nav-actions .btn-secondary { display: none; }
      .menu-toggle { display: inline-flex; }
    }

    @media (min-width: 821px) { .nav-mobile { display: none; } }

    @media (max-width: 680px) {
      .section { padding: 80px 0; }
      .hero { padding-top: 18px; }
      .hero-grid { min-height: auto; }
      .produits-grid, .stats-grid, .testimonials-grid { grid-template-columns: 1fr; }
      .dashboard { transform: none; }
      .floating-tag { display: none; }
      .hero-visual { min-height: 400px; }
    }

    @media (prefers-reduced-motion: reduce) {
      * { animation: none !important; transition: none !important; scroll-behavior: auto !important; }
      .reveal { opacity: 1 !important; transform: none !important; }
    }
  </style>
</head>
<body>

<canvas id="bgCanvas" aria-hidden="true"></canvas>
<div class="cursor-aura" id="cursorAura" aria-hidden="true"></div>

<!-- ─── NAVBAR ─── -->
<header class="navbar" id="navbar">
  <div class="nav-shell glass" id="navShell">
    <a href="#hero" class="brand" aria-label="Accueil Caille d'Or">
      <div class="brand-mark"><span>🥚</span></div>
      <div>Caille d'Or</div>
    </a>

    <nav class="nav-links" aria-label="Navigation principale">
      <a href="#produits">Produits</a>
      <a href="#ferme">Notre ferme</a>
      <a href="#chiffres">Chiffres</a>
      <a href="#avis">Avis clients</a>
    </nav>

    <div class="nav-actions">
      <a href="#ferme" class="btn btn-secondary">Notre histoire</a>
      <a href="#cta" class="btn btn-primary magnetic">Commander</a>
      <button class="menu-toggle" id="menuToggle" aria-label="Ouvrir le menu" aria-expanded="false"><span></span></button>
    </div>

    <div class="nav-mobile" id="navMobile">
      <a href="#produits">Produits</a>
      <a href="#ferme">Notre ferme</a>
      <a href="#chiffres">Chiffres</a>
      <a href="#avis">Avis clients</a>
      <a href="#cta" class="btn btn-primary" style="width:100%; justify-content:center;">Commander maintenant</a>
    </div>
  </div>
</header>

<main>
  <!-- ─── HERO ─── -->
  <section class="hero section" id="hero">
    <div class="container hero-grid">
      <div class="hero-copy reveal">
        <div class="eyebrow">
          <span class="eyebrow-dot"></span>
          Élevage naturel · Madagascar · Livraison 24h
        </div>

        <h1 class="hero-title">
          La finesse de la<br><span class="gradient">caille élevée</span><br>avec passion
        </h1>

        <p class="hero-description">
          Caille d'Or produit des œufs et de la viande de caille d'exception, directement depuis notre ferme à Madagascar.
          Élevage en plein air, alimentation naturelle, fraîcheur garantie. Du producteur à votre table.
        </p>

        <div class="hero-actions">
          <a href="#produits" class="btn btn-primary magnetic">
            Voir nos produits
            <svg width="17" height="17" viewBox="0 0 24 24" fill="none" aria-hidden="true">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
          <a href="#ferme" class="btn btn-secondary magnetic">Notre ferme</a>
        </div>

        <div class="hero-metrics">
          <div class="metric-chip glass">
            <strong>100%</strong>
            <span>plein air & naturel</span>
          </div>
          <div class="metric-chip glass">
            <strong>24h</strong>
            <span>livraison Antananarivo</span>
          </div>
          <div class="metric-chip glass">
            <strong>500+</strong>
            <span>clients fidèles</span>
          </div>
        </div>
      </div>

      <div class="hero-visual reveal" data-parallax data-speed="0.1">
        <div class="orb orb-1"></div>
        <div class="orb orb-2"></div>
        <div class="orb orb-3"></div>

        <div class="dashboard">
          <div class="dashboard-top">
            <div class="dashboard-title">CAILLE D'OR // Tableau de bord ferme</div>
            <div class="status">Production active</div>
          </div>

          <div class="dashboard-grid">
            <div class="panel large">
              <div class="panel-header">
                <h4>Production hebdomadaire</h4>
                <span>En direct</span>
              </div>
              <div class="bars">
                <div class="bar" style="height: 40%;"></div>
                <div class="bar" style="height: 62%;"></div>
                <div class="bar" style="height: 55%;"></div>
                <div class="bar" style="height: 78%;"></div>
                <div class="bar" style="height: 90%;"></div>
                <div class="bar" style="height: 97%;"></div>
              </div>
            </div>

            <div class="mini-cards">
              <div class="panel small">
                <div class="panel-header">
                  <h4>Satisfaction</h4>
                  <span>Clients</span>
                </div>
                <div class="mini-card">
                  <strong>98%</strong>
                  <span>taux de satisfaction sur la fraîcheur</span>
                </div>
              </div>

              <div class="panel small">
                <div class="panel-header">
                  <h4>Fraîcheur</h4>
                  <span>Qualité</span>
                </div>
                <div class="radial-wrap">
                  <div class="radial">
                    <strong>A+</strong>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="floating-tag tag-1">🌱 Bio</div>
          <div class="floating-tag tag-2">🚚 Express</div>
          <div class="floating-tag tag-3">⭐ Premium</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ─── PRODUITS ─── -->
  <section class="section" id="produits">
    <div class="container">
      <div class="eyebrow reveal"><span class="eyebrow-dot"></span>Notre catalogue</div>
      <h2 class="section-title reveal">Des produits d'exception,<br>directement de la ferme.</h2>
      <p class="section-subtitle reveal">
        Chaque plateau est collecté le matin même. Nos cailles sont élevées en plein air,
        nourries aux grains naturels, sans hormones ni additifs chimiques.
      </p>

      <div class="produits-grid">

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">🥚</div>
          <h3>Plateau 30 œufs</h3>
          <p>Idéal pour les familles. Œufs frais de caille, calibre standard, collectés le matin. Riches en protéines et vitamines.</p>
          <div class="prix-line">
            <div class="prix">3 500 Ar <span>/ plateau</span></div>
          </div>
          <button class="card-link" onclick="openModal('Plateau de 30 œufs', 3500)">
            Commander
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">🥚</div>
          <h3>Plateau 60 œufs</h3>
          <p>Notre offre économique préférée des familles nombreuses et des petits restaurateurs. Meilleur rapport qualité-prix.</p>
          <div class="prix-line">
            <div class="prix">6 500 Ar <span>/ plateau</span></div>
          </div>
          <button class="card-link" onclick="openModal('Plateau de 60 œufs', 6500)">
            Commander
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">🐦</div>
          <h3>Cailles vivantes</h3>
          <p>Pour ceux qui souhaitent élever ou consommer directement. Cailles saines, vaccinées, prêtes à livrer sur Antananarivo.</p>
          <div class="prix-line">
            <div class="prix">Sur devis</div>
          </div>
          <button class="card-link" onclick="openModal('Cailles vivantes', 0)">
            Demander un devis
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">🍖</div>
          <h3>Viande de caille</h3>
          <p>Viande tendre et savoureuse, abattage le jour même. Parfaite pour restaurants, traiteurs et événements gastronomiques.</p>
          <div class="prix-line">
            <div class="prix">Sur devis</div>
          </div>
          <button class="card-link" onclick="openModal('Viande de caille', 0)">
            Demander un devis
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">📦</div>
          <h3>Pack restaurant</h3>
          <p>Livraison hebdomadaire dédiée aux restaurants et hôtels. Volume garanti, prix négocié, livraison prioritaire.</p>
          <div class="prix-line">
            <div class="prix">À partir de 25 000 Ar <span>/ sem.</span></div>
          </div>
          <button class="card-link" onclick="openModal('Pack restaurant', 25000)">
            Souscrire
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

        <article class="produit-card glass reveal tilt-card">
          <div class="icon-box">🌾</div>
          <h3>Commande en gros</h3>
          <p>Pour revendeurs et grossistes. Tarifs dégressifs selon volume. Devis personnalisé sous 24h. Partenariat durable possible.</p>
          <div class="prix-line">
            <div class="prix">Prix dégressifs</div>
          </div>
          <button class="card-link" onclick="openModal('Commande en gros', 0)">
            Nous contacter
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none">
              <path d="M5 12H19M19 12L13 6M19 12L13 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </article>

      </div>
    </div>
  </section>

  <!-- ─── ABOUT ─── -->
  <section class="section" id="ferme">
    <div class="container">
      <div class="eyebrow reveal"><span class="eyebrow-dot"></span>Notre ferme</div>
      <h2 class="section-title reveal">Une passion pour l'élevage,<br>une exigence pour la qualité.</h2>
      <p class="section-subtitle reveal">
        Nous croyons que les meilleurs produits naissent d'un soin quotidien, d'un respect de l'animal
        et d'une relation directe avec nos clients.
      </p>

      <div class="about-grid">
        <div class="about-panel glass reveal">
          <div class="eyebrow" style="margin-bottom:16px;"><span class="eyebrow-dot"></span>Notre histoire</div>
          <p>
            Caille d'Or est née d'une conviction simple : Madagascar mérite des produits avicoles d'excellence,
            produits localement, avec soin et transparence. Nos cailles vivent en plein air, dans un environnement
            sain, loin des élevages industriels.
          </p>
          <p>
            Chaque jour, notre équipe collecte les œufs à la main, vérifie leur fraîcheur et prépare les commandes
            avec soin. Notre priorité : que vous receviez exactement ce que nous mangerions nous-mêmes.
          </p>

          <div class="story-points">
            <div class="story-item">
              <div class="bullet"></div>
              <div>
                <strong>Élevage en plein air</strong>
                <span>Nos cailles évoluent librement dans des enclos spacieux, à l'abri du stress et des traitements chimiques.</span>
              </div>
            </div>
            <div class="story-item">
              <div class="bullet"></div>
              <div>
                <strong>Alimentation naturelle</strong>
                <span>Grains, insectes, herbes fraîches — une nutrition complète pour des œufs d'une qualité supérieure.</span>
              </div>
            </div>
            <div class="story-item">
              <div class="bullet"></div>
              <div>
                <strong>Traçabilité totale</strong>
                <span>De la ferme à votre porte, chaque produit est suivi. Vous savez exactement ce que vous consommez.</span>
              </div>
            </div>
          </div>
        </div>

        <div class="about-visual reveal">
          <div class="vision-card glass">
            <h3>Notre vision</h3>
            <p>
              Devenir la référence malgache de l'élevage de caille premium, en alliant tradition agricole,
              modernité et respect du vivant. Un modèle durable, au service de la santé des Malgaches.
            </p>
            <div class="signal-lines" aria-hidden="true">
              <span></span><span></span><span></span><span></span><span></span>
            </div>
          </div>

          <div class="mission-card glass">
            <h3>Notre mission</h3>
            <p>
              Nourrir les familles, les restaurants et les hôtels de Madagascar avec des produits
              avicoles sains, savoureux et accessibles. Chaque commande est une promesse de qualité tenue.
            </p>
            <div class="signal-lines" aria-hidden="true">
              <span></span><span></span><span></span><span></span><span></span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ─── STATS ─── -->
  <section class="section" id="chiffres">
    <div class="container">
      <div class="eyebrow reveal"><span class="eyebrow-dot"></span>Nos chiffres</div>
      <h2 class="section-title reveal">Des indicateurs qui traduisent notre engagement envers la qualité.</h2>
      <p class="section-subtitle reveal">
        Derrière chaque chiffre, il y a une promesse : vous offrir le meilleur de notre ferme, chaque jour.
      </p>

      <div class="stats-grid">
        <div class="stat-card glass reveal">
          <div class="stat-number">
            <span class="counter" data-target="98">0</span><span>%</span>
          </div>
          <p class="stat-label">de clients satisfaits de la fraîcheur et de la qualité à chaque livraison.</p>
        </div>

        <div class="stat-card glass reveal">
          <div class="stat-number">
            <span class="counter" data-target="500">0</span><span>+</span>
          </div>
          <p class="stat-label">clients fidèles à Antananarivo et ses environs depuis notre lancement.</p>
        </div>

        <div class="stat-card glass reveal">
          <div class="stat-number">
            <span class="counter" data-target="7">0</span><span>j/7</span>
          </div>
          <p class="stat-label">collecte quotidienne pour garantir des œufs du jour à chaque commande.</p>
        </div>

        <div class="stat-card glass reveal">
          <div class="stat-number">
            <span class="counter" data-target="24">0</span><span>h</span>
          </div>
          <p class="stat-label">délai maximum de livraison après confirmation de votre commande WhatsApp.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ─── TESTIMONIALS ─── -->
  <section class="section" id="avis">
    <div class="container">
      <div class="eyebrow reveal"><span class="eyebrow-dot"></span>Avis clients</div>
      <h2 class="section-title reveal">Ils nous font confiance depuis le premier œuf.</h2>
      <p class="section-subtitle reveal">
        La satisfaction de nos clients est notre plus belle récompense.
      </p>

      <div class="testimonials-grid">
        <article class="testimonial-card glass reveal">
          <div class="testimonial-top">
            <div class="avatar">MR</div>
            <div class="testimonial-meta">
              <strong>Marie Rakoto</strong>
              <span>Cliente particulière · Antananarivo</span>
            </div>
          </div>
          <p class="testimonial-quote">
            "Des œufs d'une fraîcheur incomparable. Je commande toutes les semaines depuis six mois.
            La livraison est toujours ponctuelle et le service très agréable. Je recommande vivement !"
          </p>
          <div class="stars">★★★★★</div>
        </article>

        <article class="testimonial-card glass reveal">
          <div class="testimonial-top">
            <div class="avatar">JR</div>
            <div class="testimonial-meta">
              <strong>Jean Randria</strong>
              <span>Gérant · Restaurant Le Magnolia</span>
            </div>
          </div>
          <p class="testimonial-quote">
            "Nous utilisons les œufs de caille Caille d'Or dans nos entrées gastronomiques. La qualité est constante,
            le calibre régulier et le prix très compétitif pour un restaurant. Partenariat au top."
          </p>
          <div class="stars">★★★★★</div>
        </article>

        <article class="testimonial-card glass reveal">
          <div class="testimonial-top">
            <div class="avatar">FS</div>
            <div class="testimonial-meta">
              <strong>Fatima Solofo</strong>
              <span>Revendeuse · Marché Analakely</span>
            </div>
          </div>
          <p class="testimonial-quote">
            "Je revends les plateaux au marché et mes clients reviennent toujours. La différence de goût est réelle
            par rapport aux œufs industriels. Merci Caille d'Or pour ce partenariat si fiable."
          </p>
          <div class="stars">★★★★★</div>
        </article>
      </div>
    </div>
  </section>

  <!-- ─── CTA ─── -->
  <section class="section" id="cta">
    <div class="container">
      <div class="cta-panel glass reveal">
        <div>
          <div class="eyebrow" style="margin-bottom:16px;"><span class="eyebrow-dot"></span>Prêt à commander ?</div>
          <h2 class="cta-title">Du producteur<br>à votre table.</h2>
          <p class="cta-text">
            Passez commande directement via WhatsApp. Réponse rapide,
            livraison sous 24h à Antananarivo. Simple, frais, et garanti.
          </p>
        </div>
        <div class="cta-actions">
          <button class="btn btn-primary magnetic" onclick="openModal('Commande générale', 3500)">Passer ma commande</button>
          <a href="#produits" class="btn btn-secondary magnetic">Voir les produits</a>
        </div>
      </div>
    </div>
  </section>
</main>

<!-- ─── FOOTER ─── -->
<footer class="footer">
  <div class="container">
    <div class="footer-shell glass">
      <div class="footer-left">
        <div class="brand">
          <div class="brand-mark"><span>🥚</span></div>
          <div>Caille d'Or</div>
        </div>
        <p>Élevage premium · Antananarivo, Madagascar</p>
      </div>

      <div class="footer-links">
        <a href="#produits">Produits</a>
        <a href="#ferme">Notre ferme</a>
        <a href="#chiffres">Chiffres</a>
        <a href="#avis">Avis</a>
      </div>

      <div class="socials" aria-label="Réseaux sociaux">
        <a href="#" aria-label="Facebook">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none">
            <path d="M18 2H15C13.67 2 12.4 2.53 11.46 3.46C10.53 4.4 10 5.67 10 7V10H7V14H10V22H14V14H17L18 10H14V7C14 6.73 14.11 6.48 14.29 6.29C14.48 6.11 14.74 6 15 6H18V2Z" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
        <a href="#" aria-label="Instagram">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none">
            <rect x="3" y="3" width="18" height="18" rx="5" stroke="currentColor" stroke-width="1.6"/>
            <circle cx="12" cy="12" r="4" stroke="currentColor" stroke-width="1.6"/>
            <circle cx="17.5" cy="6.5" r="1" fill="currentColor"/>
          </svg>
        </a>
        <a href="#" aria-label="WhatsApp">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none">
            <path d="M3 21L4.7 15.1C3.6 13.2 3 11.1 3 9C3 5.7 5.7 3 9 3H15C18.3 3 21 5.7 21 9V15C21 18.3 18.3 21 15 21H9C7.1 21 5.4 20.4 3.7 19.4L3 21Z" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>
    </div>
  </div>
</footer>

<!-- ─── MODAL COMMANDE ─── -->
<div class="modal-overlay" id="modal">
  <div class="modal">
    <button class="close-modal" onclick="closeModal()" aria-label="Fermer">✕</button>
    <h3>Passer commande</h3>
    <p class="subtitle" id="modal-product-name">Plateau de 30 œufs</p>

    <div class="form-group">
      <label>Votre nom complet</label>
      <input type="text" id="client-name" placeholder="Ex : Marie Rakoto">
    </div>

    <div class="form-group">
      <label>Adresse / Quartier de livraison</label>
      <input type="text" id="client-address" placeholder="Ex : Analakely, près du marché">
    </div>

    <div class="form-group">
      <label>Quantité (plateaux ou unités)</label>
      <div class="qty-control">
        <button class="qty-btn" onclick="changeQty(-1)">−</button>
        <div class="qty-display" id="qty-display">1</div>
        <button class="qty-btn" onclick="changeQty(1)">+</button>
      </div>
    </div>

    <div class="total-line">
      <span>💰 Total estimé</span>
      <strong id="total-display">3 500 Ar</strong>
    </div>

    <button class="wa-order-btn" onclick="sendWhatsAppOrder()">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="white">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
      </svg>
      Envoyer ma commande sur WhatsApp
    </button>
  </div>
</div>

<script>
  // ─── NAVBAR SCROLL ───
  const navbar = document.getElementById("navbar");
  const navShell = document.getElementById("navShell");
  const menuToggle = document.getElementById("menuToggle");
  const navMobile = document.getElementById("navMobile");

  window.addEventListener("scroll", () => {
    navbar.classList.toggle("scrolled", window.scrollY > 20);
  });

  menuToggle.addEventListener("click", () => {
    const isOpen = navShell.classList.toggle("open");
    menuToggle.classList.toggle("active", isOpen);
    menuToggle.setAttribute("aria-expanded", isOpen ? "true" : "false");
  });

  navMobile.querySelectorAll("a").forEach(link => {
    link.addEventListener("click", () => {
      navShell.classList.remove("open");
      menuToggle.classList.remove("active");
    });
  });

  // ─── REVEAL ───
  const revealEls = document.querySelectorAll(".reveal");
  const revealObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add("is-visible"); revealObs.unobserve(e.target); }
    });
  }, { threshold: 0.14 });
  revealEls.forEach(el => revealObs.observe(el));

  // ─── COUNTERS ───
  const counters = document.querySelectorAll(".counter");
  const animateCounter = (el) => {
    const target = parseFloat(el.dataset.target);
    const isFloat = String(target).includes(".");
    const duration = 1600;
    const startTime = performance.now();
    const update = (now) => {
      const progress = Math.min((now - startTime) / duration, 1);
      const eased = 1 - Math.pow(1 - progress, 3);
      const value = target * eased;
      el.textContent = isFloat ? value.toFixed(1) : Math.floor(value);
      if (progress < 1) requestAnimationFrame(update);
      else el.textContent = isFloat ? target.toFixed(1) : target;
    };
    requestAnimationFrame(update);
  };

  let countersStarted = false;
  const statsObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting && !countersStarted) {
        counters.forEach(c => animateCounter(c));
        countersStarted = true;
      }
    });
  }, { threshold: 0.3 });
  statsObs.observe(document.getElementById("chiffres"));

  // ─── PARALLAX ───
  const parallaxEls = document.querySelectorAll("[data-parallax]");
  window.addEventListener("scroll", () => {
    const sy = window.scrollY;
    parallaxEls.forEach(el => {
      el.style.transform = `translateY(${sy * parseFloat(el.dataset.speed || 0.1)}px)`;
    });
  }, { passive: true });

  // ─── MAGNETIC ───
  document.querySelectorAll(".magnetic").forEach(item => {
    item.addEventListener("mousemove", (e) => {
      const r = item.getBoundingClientRect();
      const x = e.clientX - r.left - r.width / 2;
      const y = e.clientY - r.top - r.height / 2;
      item.style.transform = `translate(${x * 0.07}px, ${y * 0.07}px)`;
    });
    item.addEventListener("mouseleave", () => { item.style.transform = ""; });
  });

  // ─── TILT CARDS ───
  document.querySelectorAll(".tilt-card").forEach(card => {
    card.addEventListener("mousemove", (e) => {
      const r = card.getBoundingClientRect();
      const x = e.clientX - r.left;
      const y = e.clientY - r.top;
      const rx = ((y / r.height) - 0.5) * -9;
      const ry = ((x / r.width) - 0.5) * 9;
      card.style.transform = `translateY(-8px) rotateX(${rx}deg) rotateY(${ry}deg)`;
    });
    card.addEventListener("mouseleave", () => { card.style.transform = ""; });
  });

  // ─── CURSOR AURA ───
  const cursorAura = document.getElementById("cursorAura");
  window.addEventListener("mousemove", (e) => {
    cursorAura.style.left = `${e.clientX}px`;
    cursorAura.style.top = `${e.clientY}px`;
  });

  // ─── CANVAS PARTICLES ───
  const canvas = document.getElementById("bgCanvas");
  const ctx = canvas.getContext("2d");
  let particles = [], w, h;

  function resizeCanvas() {
    w = canvas.width = window.innerWidth;
    h = canvas.height = window.innerHeight;
    createParticles();
  }

  function createParticles() {
    const count = Math.min(60, Math.floor(window.innerWidth / 22));
    particles = Array.from({ length: count }, () => ({
      x: Math.random() * w, y: Math.random() * h,
      r: Math.random() * 1.6 + 0.5,
      vx: (Math.random() - 0.5) * 0.22,
      vy: (Math.random() - 0.5) * 0.22,
      gold: Math.random() > 0.5
    }));
  }

  function drawParticles() {
    ctx.clearRect(0, 0, w, h);
    particles.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0 || p.x > w) p.vx *= -1;
      if (p.y < 0 || p.y > h) p.vy *= -1;
      ctx.beginPath();
      ctx.fillStyle = p.gold ? "rgba(201,151,58,0.75)" : "rgba(74,124,63,0.75)";
      ctx.shadowBlur = 16; ctx.shadowColor = ctx.fillStyle;
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fill();
    });
    ctx.shadowBlur = 0;
    for (let i = 0; i < particles.length; i++) {
      for (let j = i + 1; j < particles.length; j++) {
        const a = particles[i], b = particles[j];
        const dx = a.x - b.x, dy = a.y - b.y;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < 120) {
          ctx.beginPath();
          ctx.strokeStyle = `rgba(200,170,100,${0.07 - dist / 2000})`;
          ctx.lineWidth = 1;
          ctx.moveTo(a.x, a.y); ctx.lineTo(b.x, b.y); ctx.stroke();
        }
      }
    }
    requestAnimationFrame(drawParticles);
  }

  resizeCanvas(); drawParticles();
  window.addEventListener("resize", resizeCanvas);

  // ─── ACTIVE NAV ───
  const sections = document.querySelectorAll("main section[id]");
  const navLinks = document.querySelectorAll(".nav-links a, .nav-mobile a");
  window.addEventListener("scroll", () => {
    let current = "";
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 140) current = s.id;
    });
    navLinks.forEach(l => {
      l.style.color = l.getAttribute("href")?.replace("#", "") === current ? "#f0ead8" : "";
    });
  }, { passive: true });

  // ─── MODAL COMMANDE ───
  let currentPrice = 3500, currentProduct = '', qty = 1;

  function openModal(product, price) {
    currentProduct = product; currentPrice = price; qty = 1;
    document.getElementById('modal-product-name').textContent = product;
    document.getElementById('qty-display').textContent = qty;
    updateTotal();
    document.getElementById('modal').classList.add('active');
  }

  function closeModal() { document.getElementById('modal').classList.remove('active'); }

  function changeQty(delta) {
    qty = Math.max(1, qty + delta);
    document.getElementById('qty-display').textContent = qty;
    updateTotal();
  }

  function updateTotal() {
    if (currentPrice === 0) {
      document.getElementById('total-display').textContent = 'Sur devis';
    } else {
      document.getElementById('total-display').textContent = (qty * currentPrice).toLocaleString('fr-MG') + ' Ar';
    }
  }

  function sendWhatsAppOrder() {
    const name = document.getElementById('client-name').value || 'Client';
    const address = document.getElementById('client-address').value || 'Non précisée';
    const totalText = currentPrice === 0 ? 'Sur devis' : (qty * currentPrice).toLocaleString('fr-MG') + ' Ar';
    const msg = `🥚 *Nouvelle commande - Caille d'Or*\n\n👤 Nom: ${name}\n📦 Produit: ${currentProduct}\n🔢 Quantité: ${qty}\n📍 Adresse: ${address}\n💰 Total: ${totalText}\n\n_Merci de confirmer la disponibilité et le délai de livraison._`;
    window.open('https://wa.me/261000000000?text=' + encodeURIComponent(msg), '_blank');
  }

  document.getElementById('modal').addEventListener('click', function(e) {
    if (e.target === this) closeModal();
  });
</script>

</body>
</html>
