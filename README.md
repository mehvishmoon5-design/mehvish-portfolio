<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mehvish Ashraf — Graphic Designer</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=DM+Mono:wght@300;400;500&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --ink: #0e0d0b;
    --cream: #f5f0e8;
    --warm: #e8dfc8;
    --rust: #c4512a;
    --rust-light: #d46740;
    --gold: #b89a5a;
    --muted: #7a7060;
    --divider: #d4caba;
    --fs-xs: clamp(0.65rem, 1vw, 0.75rem);
    --fs-sm: clamp(0.8rem, 1.2vw, 0.9rem);
    --fs-base: clamp(0.95rem, 1.5vw, 1.05rem);
    --fs-md: clamp(1.1rem, 2vw, 1.3rem);
    --fs-lg: clamp(1.4rem, 3vw, 1.8rem);
    --fs-xl: clamp(2rem, 5vw, 3.5rem);
    --fs-2xl: clamp(3rem, 8vw, 6rem);
    --fs-3xl: clamp(4rem, 12vw, 9rem);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Cormorant Garamond', Georgia, serif;
    background: var(--cream);
    color: var(--ink);
    overflow-x: hidden;
    cursor: none;
  }

  /* ── CURSOR ── */
  .cursor {
    position: fixed; top: 0; left: 0; z-index: 9999;
    pointer-events: none;
  }
  .cursor-dot {
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--rust);
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease;
  }
  .cursor-ring {
    width: 36px; height: 36px; border-radius: 50%;
    border: 1.5px solid var(--rust);
    transform: translate(-50%, -50%);
    transition: width 0.3s, height 0.3s, opacity 0.3s, transform 0.15s ease;
    position: absolute; top: 0; left: 0;
    opacity: 0.6;
  }
  body:has(a:hover) .cursor-ring,
  body:has(button:hover) .cursor-ring {
    width: 56px; height: 56px; opacity: 1;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.6rem 4rem;
    mix-blend-mode: multiply;
  }
  .nav-logo {
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 0.75rem;
  }
  .nav-logo-icon {
    position: relative;
    width: 42px;
    height: 42px;
    flex-shrink: 0;
  }
  .nav-logo-icon svg { width: 100%; height: 100%; }
  .nav-logo-text-wrap {
    display: flex;
    flex-direction: column;
    line-height: 1.1;
  }
  .nav-logo-first {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    font-weight: 900;
    font-style: italic;
    color: var(--ink);
    letter-spacing: -0.01em;
  }
  .nav-logo-last {
    font-family: 'DM Mono', monospace;
    font-size: 0.6rem;
    font-weight: 500;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--rust);
  }
  .nav-links {
    display: flex; gap: 2.5rem; list-style: none;
  }
  .nav-links a {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    font-weight: 400;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink);
    text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--rust); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    overflow: hidden;
  }
  .hero-left {
    display: flex; flex-direction: column; justify-content: flex-end;
    padding: 10rem 4rem 5rem;
    position: relative; z-index: 2;
  }
  .hero-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--rust);
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.3s ease forwards;
  }
  .hero-name {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-3xl);
    font-weight: 900;
    line-height: 0.92;
    letter-spacing: -0.03em;
    color: var(--ink);
    opacity: 0;
    animation: fadeUp 0.9s 0.5s ease forwards;
  }
  .hero-name em {
    font-style: italic;
    color: var(--rust);
  }
  .hero-tagline {
    margin-top: 2rem;
    font-size: var(--fs-md);
    font-style: italic;
    color: var(--muted);
    line-height: 1.6;
    max-width: 420px;
    opacity: 0;
    animation: fadeUp 0.9s 0.7s ease forwards;
  }
  .hero-cta {
    margin-top: 3rem;
    display: flex; gap: 1.5rem; align-items: center;
    opacity: 0;
    animation: fadeUp 0.9s 0.9s ease forwards;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 0.6rem;
    background: var(--rust);
    color: var(--cream);
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 0.9rem 2.2rem;
    border: none; cursor: none;
    transition: background 0.25s, transform 0.2s;
  }
  .btn-primary:hover { background: var(--rust-light); transform: translateY(-2px); }
  .btn-secondary {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    border-bottom: 1px solid var(--divider);
    padding-bottom: 2px;
    transition: color 0.2s, border-color 0.2s;
  }
  .btn-secondary:hover { color: var(--rust); border-color: var(--rust); }

  .hero-right {
    position: relative;
    overflow: hidden;
  }
  .hero-image-frame {
    position: absolute; inset: 6rem 0 0 2rem;
    background: var(--warm);
    overflow: hidden;
    animation: fadeIn 1.2s 0.4s ease forwards;
    opacity: 0;
  }
  .hero-image-frame::before {
    content: '';
    position: absolute; inset: 0;
    background:
      repeating-linear-gradient(
        45deg,
        transparent,
        transparent 30px,
        rgba(196,81,42,0.04) 30px,
        rgba(196,81,42,0.04) 31px
      );
  }
  .hero-image-frame::after {
    content: 'M.A';
    position: absolute; bottom: 2rem; right: 2rem;
    font-family: 'Playfair Display', serif;
    font-size: clamp(4rem, 10vw, 8rem);
    font-weight: 900;
    font-style: italic;
    color: rgba(196,81,42,0.12);
    line-height: 1;
    letter-spacing: -0.04em;
  }
  .hero-floating-tag {
    position: absolute;
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.08em;
    background: var(--ink);
    color: var(--cream);
    padding: 0.5rem 1rem;
    animation: fadeIn 1s 1.2s ease forwards;
    opacity: 0;
  }
  .tag-1 { top: 9rem; right: 2rem; }
  .tag-2 { bottom: 3rem; left: 4rem; background: var(--rust); }

  .hero-scroll-hint {
    position: absolute; bottom: 3rem; left: 4rem;
    display: flex; align-items: center; gap: 1rem;
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    z-index: 2;
    opacity: 0;
    animation: fadeUp 0.8s 1.3s ease forwards;
  }
  .scroll-line {
    width: 40px; height: 1px;
    background: var(--muted);
    position: relative; overflow: hidden;
  }
  .scroll-line::after {
    content: '';
    position: absolute; top: 0; left: -100%;
    width: 100%; height: 100%;
    background: var(--rust);
    animation: scrollPulse 2s 1.5s ease-in-out infinite;
  }

  /* ── MARQUEE ── */
  .marquee-bar {
    background: var(--ink);
    color: var(--cream);
    overflow: hidden;
    padding: 0.9rem 0;
    white-space: nowrap;
  }
  .marquee-track {
    display: inline-flex; gap: 0;
    animation: marquee 18s linear infinite;
  }
  .marquee-item {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: var(--fs-base);
    padding: 0 2rem;
    border-right: 1px solid rgba(255,255,255,0.15);
  }
  .marquee-dot {
    color: var(--rust);
    font-style: normal;
  }

  /* ── SECTION STYLES ── */
  section { padding: 7rem 4rem; }
  .section-header {
    display: flex; align-items: baseline; gap: 2rem;
    margin-bottom: 5rem;
  }
  .section-number {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    color: var(--rust);
    letter-spacing: 0.15em;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-xl);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -0.02em;
  }
  .section-title em { font-style: italic; color: var(--rust); }
  .section-rule {
    flex: 1;
    height: 1px;
    background: var(--divider);
    margin-left: 1rem;
    align-self: center;
  }

  /* ── ABOUT ── */
  #about {
    background: var(--ink);
    color: var(--cream);
  }
  #about .section-title em { color: var(--gold); }
  #about .section-rule { background: rgba(255,255,255,0.1); }
  #about .section-number { color: var(--gold); }
  .about-grid {
    display: grid;
    grid-template-columns: 1.4fr 1fr;
    gap: 6rem;
    align-items: start;
  }
  .about-bio {
    font-size: var(--fs-md);
    line-height: 1.8;
    color: rgba(245,240,232,0.85);
    font-style: italic;
  }
  .about-bio strong { color: var(--gold); font-style: normal; }
  .about-bio p + p { margin-top: 1.4rem; }
  .about-details { display: flex; flex-direction: column; gap: 2rem; }
  .about-stat {
    border-top: 1px solid rgba(255,255,255,0.1);
    padding-top: 1.5rem;
  }
  .about-stat-num {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-xl);
    font-weight: 900;
    color: var(--gold);
    line-height: 1;
  }
  .about-stat-label {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    margin-top: 0.4rem;
  }
  .about-skills {
    margin-top: 3rem;
    display: flex; flex-wrap: wrap; gap: 0.6rem;
  }
  .skill-tag {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    border: 1px solid rgba(184,154,90,0.4);
    color: var(--gold);
    padding: 0.4rem 1rem;
    transition: background 0.2s, color 0.2s;
  }
  .skill-tag:hover {
    background: var(--gold);
    color: var(--ink);
  }

  /* ── WORK / PORTFOLIO ── */
  #work { background: var(--cream); }
  .work-grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 2rem;
  }
  .work-item {
    position: relative; overflow: hidden;
    cursor: none;
    background: var(--warm);
  }
  .work-item:nth-child(1) { grid-column: span 7; grid-row: span 2; }
  .work-item:nth-child(2) { grid-column: span 5; }
  .work-item:nth-child(3) { grid-column: span 5; }
  .work-item:nth-child(4) { grid-column: span 4; }
  .work-item:nth-child(5) { grid-column: span 4; }
  .work-item:nth-child(6) { grid-column: span 4; }

  .work-thumb {
    width: 100%;
    aspect-ratio: 4/3;
    display: flex; align-items: center; justify-content: center;
    overflow: hidden;
    position: relative;
  }
  .work-item:nth-child(1) .work-thumb { aspect-ratio: 4/5; }

  .work-visual {
    width: 100%; height: 100%;
    transition: transform 0.6s cubic-bezier(0.16,1,0.3,1);
  }
  .work-item:hover .work-visual { transform: scale(1.05); }

  /* SVG placeholder visuals */
  .vis-1 { background: linear-gradient(135deg, #1a0f0a 0%, #3d1a0e 50%, #c4512a 100%); }
  .vis-2 { background: linear-gradient(45deg, #2d2015 0%, #b89a5a 100%); }
  .vis-3 { background: linear-gradient(160deg, #0e0d0b 0%, #2a3040 100%); }
  .vis-4 { background: linear-gradient(135deg, #e8dfc8 0%, #c4512a 100%); }
  .vis-5 { background: linear-gradient(45deg, #1a2030 0%, #4a6080 100%); }
  .vis-6 { background: linear-gradient(135deg, #2d1a10 0%, #8a4520 100%); }

  /* decorative SVG overlays inside thumbnails */
  .work-thumb svg {
    position: absolute; inset: 0;
    width: 100%; height: 100%;
  }

  .work-overlay {
    position: absolute; inset: 0;
    background: rgba(14,13,11,0.88);
    display: flex; flex-direction: column;
    justify-content: flex-end;
    padding: 2rem;
    opacity: 0;
    transition: opacity 0.35s ease;
  }
  .work-item:hover .work-overlay { opacity: 1; }
  .work-cat {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--rust);
    margin-bottom: 0.5rem;
  }
  .work-title {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-lg);
    font-style: italic;
    color: var(--cream);
    line-height: 1.2;
  }
  .work-arrow {
    position: absolute; top: 1.5rem; right: 1.5rem;
    width: 40px; height: 40px;
    border: 1px solid rgba(245,240,232,0.3);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    color: var(--cream);
    font-size: 1.2rem;
    transform: rotate(45deg);
    transition: background 0.2s, border-color 0.2s;
  }
  .work-item:hover .work-arrow {
    background: var(--rust);
    border-color: var(--rust);
  }
  .work-info {
    padding: 1.2rem 1.5rem;
    display: flex; justify-content: space-between; align-items: baseline;
  }
  .work-info-title {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-base);
    font-style: italic;
  }
  .work-info-year {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    color: var(--muted);
  }

  /* ── SERVICES ── */
  #services { background: var(--warm); }
  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0;
  }
  .service-item {
    padding: 3rem;
    border-right: 1px solid var(--divider);
    border-bottom: 1px solid var(--divider);
    position: relative;
    transition: background 0.3s;
  }
  .service-item:nth-child(3n) { border-right: none; }
  .service-item:nth-last-child(-n+3) { border-bottom: none; }
  .service-item:hover { background: rgba(196,81,42,0.06); }
  .service-num {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    color: var(--rust);
    letter-spacing: 0.1em;
    margin-bottom: 1.5rem;
  }
  .service-icon {
    width: 40px; height: 40px;
    margin-bottom: 1.5rem;
    color: var(--rust);
  }
  .service-name {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-lg);
    font-weight: 700;
    margin-bottom: 1rem;
    line-height: 1.2;
  }
  .service-desc {
    font-size: var(--fs-base);
    color: var(--muted);
    line-height: 1.7;
    font-style: italic;
  }

  /* ── PROCESS ── */
  #process {
    background: var(--cream);
  }
  .process-list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 3rem;
  }
  .process-step { position: relative; }
  .process-step::after {
    content: '→';
    position: absolute;
    top: 1.5rem; right: -1.5rem;
    font-size: var(--fs-lg);
    color: var(--divider);
  }
  .process-step:last-child::after { display: none; }
  .process-step-num {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.5rem, 5vw, 4rem);
    font-weight: 900;
    color: var(--warm);
    line-height: 1;
    margin-bottom: 1rem;
  }
  .process-step-name {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-md);
    font-weight: 700;
    margin-bottom: 0.8rem;
  }
  .process-step-desc {
    font-size: var(--fs-sm);
    color: var(--muted);
    line-height: 1.7;
    font-style: italic;
  }

  /* ── TESTIMONIALS ── */
  #testimonials {
    background: var(--ink);
    color: var(--cream);
    position: relative; overflow: hidden;
  }
  #testimonials::before {
    content: '"';
    position: absolute;
    font-family: 'Playfair Display', serif;
    font-size: 40rem;
    font-weight: 900;
    color: rgba(255,255,255,0.02);
    top: -8rem; left: -2rem;
    line-height: 1;
    pointer-events: none;
  }
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
  }
  .testimonial-card {
    border-top: 1px solid rgba(255,255,255,0.1);
    padding-top: 2rem;
  }
  .testimonial-stars {
    color: var(--gold);
    font-size: 0.9rem;
    letter-spacing: 0.1em;
    margin-bottom: 1.2rem;
  }
  .testimonial-text {
    font-style: italic;
    font-size: var(--fs-md);
    line-height: 1.75;
    color: rgba(245,240,232,0.85);
    margin-bottom: 2rem;
  }
  .testimonial-author {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--gold);
  }
  .testimonial-role {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.06em;
    color: var(--muted);
    margin-top: 0.3rem;
  }

  /* ── CONTACT ── */
  #contact {
    background: var(--cream);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: start;
  }
  .contact-left {}
  .contact-invite {
    font-size: var(--fs-xl);
    font-family: 'Playfair Display', serif;
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 2rem;
  }
  .contact-invite em { color: var(--rust); font-style: italic; }
  .contact-sub {
    font-style: italic;
    font-size: var(--fs-md);
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 3rem;
  }
  .contact-details { display: flex; flex-direction: column; gap: 1.5rem; }
  .contact-item {
    display: flex; gap: 1.5rem; align-items: flex-start;
  }
  .contact-item-label {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--rust);
    min-width: 80px;
    padding-top: 0.1rem;
  }
  .contact-item-val {
    font-size: var(--fs-base);
    color: var(--ink);
  }
  .contact-right {}
  .contact-form { display: flex; flex-direction: column; gap: 1.5rem; }
  .form-group { display: flex; flex-direction: column; gap: 0.5rem; }
  .form-label {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
  }
  .form-input, .form-textarea {
    font-family: 'Cormorant Garamond', serif;
    font-size: var(--fs-base);
    color: var(--ink);
    background: transparent;
    border: none;
    border-bottom: 1px solid var(--divider);
    padding: 0.8rem 0;
    outline: none;
    transition: border-color 0.2s;
    resize: none;
  }
  .form-input:focus, .form-textarea:focus { border-color: var(--rust); }
  .form-input::placeholder, .form-textarea::placeholder { color: var(--divider); }
  .form-textarea { min-height: 120px; }
  .form-submit {
    margin-top: 0.5rem;
    align-self: flex-start;
    display: inline-flex; align-items: center; gap: 0.8rem;
    background: var(--ink);
    color: var(--cream);
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    border: none; cursor: none;
    padding: 1rem 2.5rem;
    transition: background 0.25s, transform 0.2s;
  }
  .form-submit:hover { background: var(--rust); transform: translateY(-2px); }

  /* ── FOOTER ── */
  footer {
    background: var(--ink);
    color: var(--cream);
    padding: 3rem 4rem;
    display: flex; align-items: center; justify-content: space-between;
  }
  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: var(--fs-md);
    font-weight: 700;
    font-style: italic;
    color: var(--cream);
  }
  .footer-copy {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    color: var(--muted);
    letter-spacing: 0.06em;
  }
  .footer-socials { display: flex; gap: 2rem; }
  .footer-socials a {
    font-family: 'DM Mono', monospace;
    font-size: var(--fs-xs);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .footer-socials a:hover { color: var(--gold); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }
  @keyframes scrollPulse {
    0% { left: -100%; }
    100% { left: 100%; }
  }

  /* scroll reveal */
  .reveal {
    opacity: 0; transform: translateY(32px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.35s; }
  .reveal-delay-4 { transition-delay: 0.5s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 1024px) {
    nav { padding: 1.4rem 2rem; }
    section { padding: 5rem 2rem; }
    #hero { grid-template-columns: 1fr; min-height: auto; }
    .hero-left { padding: 9rem 2rem 4rem; }
    .hero-right { height: 50vw; }
    .hero-image-frame { inset: 1rem; }
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .services-grid { grid-template-columns: 1fr 1fr; }
    .work-item:nth-child(1) { grid-column: span 12; }
    .work-item:nth-child(n+2) { grid-column: span 6; }
    .process-list { grid-template-columns: 1fr 1fr; gap: 2rem; }
    .testimonials-grid { grid-template-columns: 1fr; }
    #contact { grid-template-columns: 1fr; gap: 3rem; padding: 5rem 2rem; }
    footer { flex-direction: column; gap: 1.5rem; text-align: center; }
  }
  @media (max-width: 600px) {
    nav .nav-links { display: none; }
    .services-grid { grid-template-columns: 1fr; }
    .work-item { grid-column: span 12 !important; }
    .process-list { grid-template-columns: 1fr; }
    .process-step::after { display: none; }
  }
</style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor">
  <div class="cursor-ring"></div>
  <div class="cursor-dot"></div>
</div>

<!-- Navigation -->
<nav>
  <a href="#" class="nav-logo">
    <div class="nav-logo-icon">
      <svg viewBox="0 0 42 42" fill="none" xmlns="http://www.w3.org/2000/svg">
        <!-- Outer square rotated -->
        <rect x="6" y="6" width="30" height="30" rx="2" fill="#0e0d0b"/>
        <!-- Inner decorative diamond -->
        <path d="M21 10 L32 21 L21 32 L10 21 Z" fill="none" stroke="#c4512a" stroke-width="1.2"/>
        <!-- M A initials -->
        <text x="21" y="25" font-family="Georgia,serif" font-size="13" font-weight="bold" font-style="italic" fill="#f5f0e8" text-anchor="middle" letter-spacing="-1">MA</text>
        <!-- Corner dots -->
        <circle cx="6" cy="6" r="1.5" fill="#c4512a"/>
        <circle cx="36" cy="6" r="1.5" fill="#c4512a"/>
        <circle cx="6" cy="36" r="1.5" fill="#c4512a"/>
        <circle cx="36" cy="36" r="1.5" fill="#c4512a"/>
      </svg>
    </div>
    <div class="nav-logo-text-wrap">
      <span class="nav-logo-first">Mehvish Ashraf</span>
      <span class="nav-logo-last">Graphic Designer</span>
    </div>
  </a>
  <ul class="nav-links">
    <li><a href="#work">Work</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- Hero -->
<section id="hero">
  <div class="hero-left">
    <p class="hero-eyebrow">— Graphic Designer & Visual Storyteller</p>
    <h1 class="hero-name">
      Crafting<br><em>Visual</em><br>Worlds
    </h1>
    <p class="hero-tagline">
      Where bold ideas meet refined execution — design that speaks before words do.
    </p>
    <div class="hero-cta">
      <a href="#work" class="btn-primary">View Portfolio ↗</a>
      <a href="#contact" class="btn-secondary">Let's collaborate</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-image-frame">
      <!-- Abstract decorative artwork -->
      <svg viewBox="0 0 500 600" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:100%;object-fit:cover;">
        <rect width="500" height="600" fill="#1a0f0a"/>
        <circle cx="250" cy="280" r="180" fill="none" stroke="#c4512a" stroke-width="0.5" opacity="0.4"/>
        <circle cx="250" cy="280" r="140" fill="none" stroke="#b89a5a" stroke-width="0.5" opacity="0.3"/>
        <circle cx="250" cy="280" r="100" fill="none" stroke="#c4512a" stroke-width="0.5" opacity="0.5"/>
        <path d="M70 280 Q250 80 430 280 Q250 480 70 280Z" fill="none" stroke="#c4512a" stroke-width="1" opacity="0.3"/>
        <line x1="250" y1="0" x2="250" y2="600" stroke="#b89a5a" stroke-width="0.3" opacity="0.2"/>
        <line x1="0" y1="300" x2="500" y2="300" stroke="#b89a5a" stroke-width="0.3" opacity="0.2"/>
        <polygon points="250,120 370,320 130,320" fill="none" stroke="#c4512a" stroke-width="0.8" opacity="0.5"/>
        <polygon points="250,440 370,240 130,240" fill="none" stroke="#b89a5a" stroke-width="0.8" opacity="0.3"/>
        <circle cx="250" cy="280" r="8" fill="#c4512a" opacity="0.9"/>
        <circle cx="250" cy="120" r="4" fill="#b89a5a" opacity="0.7"/>
        <circle cx="250" cy="440" r="4" fill="#b89a5a" opacity="0.7"/>
        <circle cx="430" cy="280" r="4" fill="#b89a5a" opacity="0.7"/>
        <circle cx="70" cy="280" r="4" fill="#b89a5a" opacity="0.7"/>
        <text x="250" y="568" font-family="Georgia,serif" font-size="11" fill="#b89a5a" opacity="0.5" text-anchor="middle" letter-spacing="8">MEHVISH ASHRAF</text>
      </svg>
    </div>
    <div class="hero-floating-tag tag-1">Visual Identity</div>
    <div class="hero-floating-tag tag-2">Available for work ✦</div>
  </div>
  <div class="hero-scroll-hint">
    <div class="scroll-line"></div>
    Scroll to explore
  </div>
</section>

<!-- Marquee -->
<div class="marquee-bar" aria-hidden="true">
  <div class="marquee-track">
    <span class="marquee-item">Brand Identity <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Visual Design <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Print & Editorial <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Typography <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Art Direction <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Packaging Design <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Brand Identity <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Visual Design <span class="marquare-dot">✦</span></span>
    <span class="marquee-item">Print & Editorial <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Typography <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Art Direction <span class="marquee-dot">✦</span></span>
    <span class="marquee-item">Packaging Design <span class="marquee-dot">✦</span></span>
  </div>
</div>

<!-- About -->
<section id="about">
  <div class="section-header reveal">
    <span class="section-number">01</span>
    <h2 class="section-title">About <em>Me</em></h2>
    <div class="section-rule"></div>
  </div>
  <div class="about-grid">
    <div class="about-bio reveal reveal-delay-1">
      <p>I'm <strong>Mehvish Ashraf</strong>, a graphic designer with a deep belief that design is more than aesthetics — it's a conversation between a brand and its audience.</p>
      <p>With over <strong>6 years of experience</strong>, I've helped startups find their visual voice, guided established brands through transformation, and crafted stories told entirely through image, color, and form.</p>
      <p>My work lives at the intersection of <strong>cultural sensitivity and contemporary design thinking</strong> — rooted in concept, refined in execution, and always in service of meaning.</p>
      <div class="about-skills">
        <span class="skill-tag">Illustrator</span>
        <span class="skill-tag">Photoshop</span>
        <span class="skill-tag">InDesign</span>
        <span class="skill-tag">Figma</span>
        <span class="skill-tag">After Effects</span>
        <span class="skill-tag">Blender</span>
        <span class="skill-tag">Brand Strategy</span>
        <span class="skill-tag">Typography</span>
      </div>
    </div>
    <div class="about-details reveal reveal-delay-2">
      <div class="about-stat">
        <div class="about-stat-num">6+</div>
        <div class="about-stat-label">Years of Experience</div>
      </div>
      <div class="about-stat">
        <div class="about-stat-num">85+</div>
        <div class="about-stat-label">Projects Delivered</div>
      </div>
      <div class="about-stat">
        <div class="about-stat-num">40+</div>
        <div class="about-stat-label">Happy Clients</div>
      </div>
      <div class="about-stat">
        <div class="about-stat-num">12</div>
        <div class="about-stat-label">Design Awards</div>
      </div>
    </div>
  </div>
</section>

<!-- Work -->
<section id="work">
  <div class="section-header reveal">
    <span class="section-number">02</span>
    <h2 class="section-title">Selected <em>Work</em></h2>
    <div class="section-rule"></div>
  </div>
  <div class="work-grid">

    <!-- Project 1: large -->
    <div class="work-item reveal">
      <div class="work-thumb">
        <div class="work-visual vis-1"></div>
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <circle cx="200" cy="220" r="120" fill="none" stroke="rgba(196,81,42,0.6)" stroke-width="1"/>
          <circle cx="200" cy="220" r="80" fill="none" stroke="rgba(184,154,90,0.4)" stroke-width="0.8"/>
          <text x="200" y="215" font-family="Georgia,serif" font-size="32" fill="#f5f0e8" text-anchor="middle" opacity="0.9" font-style="italic">Zeyna</text>
          <text x="200" y="240" font-family="monospace" font-size="8" fill="#b89a5a" text-anchor="middle" letter-spacing="6" opacity="0.7">BRAND IDENTITY</text>
          <line x1="160" y1="260" x2="240" y2="260" stroke="#c4512a" stroke-width="0.8" opacity="0.6"/>
          <rect x="20" y="20" width="40" height="40" fill="none" stroke="rgba(184,154,90,0.3)" stroke-width="0.6"/>
          <rect x="340" y="440" width="40" height="40" fill="none" stroke="rgba(196,81,42,0.3)" stroke-width="0.6"/>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Brand Identity</div>
          <div class="work-title">Zeyna — Luxury Fashion House</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Zeyna Identity</span>
        <span class="work-info-year">2024</span>
      </div>
    </div>

    <!-- Project 2 -->
    <div class="work-item reveal reveal-delay-1">
      <div class="work-thumb">
        <div class="work-visual vis-2"></div>
        <svg viewBox="0 0 300 225" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <polygon points="150,20 280,200 20,200" fill="none" stroke="rgba(245,240,232,0.3)" stroke-width="1"/>
          <text x="150" y="135" font-family="Georgia,serif" font-size="20" fill="#0e0d0b" text-anchor="middle" font-style="italic" opacity="0.8">Amber</text>
          <text x="150" y="155" font-family="monospace" font-size="7" fill="#0e0d0b" text-anchor="middle" letter-spacing="4" opacity="0.5">PERFUMERY</text>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Packaging</div>
          <div class="work-title">Amber Perfumery — Bottle & Box Design</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Amber Packaging</span>
        <span class="work-info-year">2024</span>
      </div>
    </div>

    <!-- Project 3 -->
    <div class="work-item reveal reveal-delay-2">
      <div class="work-thumb">
        <div class="work-visual vis-3"></div>
        <svg viewBox="0 0 300 225" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <line x1="0" y1="112" x2="300" y2="112" stroke="rgba(245,240,232,0.1)" stroke-width="0.5"/>
          <text x="150" y="100" font-family="Georgia,serif" font-size="28" fill="#f5f0e8" text-anchor="middle" font-weight="bold" opacity="0.9">ATLAS</text>
          <text x="150" y="124" font-family="monospace" font-size="7" fill="#c4512a" text-anchor="middle" letter-spacing="5">QUARTERLY MAGAZINE</text>
          <rect x="30" y="30" width="240" height="165" fill="none" stroke="rgba(245,240,232,0.1)" stroke-width="0.5"/>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Editorial</div>
          <div class="work-title">Atlas — Magazine Layout & Typography</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Atlas Magazine</span>
        <span class="work-info-year">2023</span>
      </div>
    </div>

    <!-- Project 4 -->
    <div class="work-item reveal">
      <div class="work-thumb">
        <div class="work-visual vis-4"></div>
        <svg viewBox="0 0 300 225" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <circle cx="150" cy="112" r="60" fill="rgba(14,13,11,0.4)"/>
          <text x="150" y="107" font-family="Georgia,serif" font-size="14" fill="#f5f0e8" text-anchor="middle" font-style="italic">Noor</text>
          <text x="150" y="124" font-family="monospace" font-size="6" fill="#f5f0e8" text-anchor="middle" letter-spacing="3">WELLNESS</text>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Brand Identity</div>
          <div class="work-title">Noor — Wellness Brand System</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Noor Wellness</span>
        <span class="work-info-year">2023</span>
      </div>
    </div>

    <!-- Project 5 -->
    <div class="work-item reveal reveal-delay-1">
      <div class="work-thumb">
        <div class="work-visual vis-5"></div>
        <svg viewBox="0 0 300 225" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <rect x="60" y="50" width="180" height="125" fill="none" stroke="rgba(245,240,232,0.2)" stroke-width="0.7"/>
          <rect x="75" y="65" width="150" height="95" fill="none" stroke="rgba(245,240,232,0.1)" stroke-width="0.5"/>
          <text x="150" y="118" font-family="monospace" font-size="12" fill="#f5f0e8" text-anchor="middle" letter-spacing="3" opacity="0.8">VERTEX</text>
          <text x="150" y="132" font-family="monospace" font-size="6" fill="#c4512a" text-anchor="middle" letter-spacing="4">TECH BRANDING</text>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Digital</div>
          <div class="work-title">Vertex — Tech Startup Branding</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Vertex Tech</span>
        <span class="work-info-year">2023</span>
      </div>
    </div>

    <!-- Project 6 -->
    <div class="work-item reveal reveal-delay-2">
      <div class="work-thumb">
        <div class="work-visual vis-6"></div>
        <svg viewBox="0 0 300 225" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%">
          <path d="M150 30 L270 195 L30 195 Z" fill="none" stroke="rgba(245,240,232,0.2)" stroke-width="0.7"/>
          <text x="150" y="155" font-family="Georgia,serif" font-size="13" fill="#f5f0e8" text-anchor="middle" font-style="italic" opacity="0.9">Rumi Reads</text>
          <text x="150" y="173" font-family="monospace" font-size="6" fill="#b89a5a" text-anchor="middle" letter-spacing="3">BOOKSHOP IDENTITY</text>
        </svg>
        <div class="work-overlay">
          <div class="work-cat">Identity</div>
          <div class="work-title">Rumi Reads — Independent Bookshop</div>
          <div class="work-arrow">↗</div>
        </div>
      </div>
      <div class="work-info">
        <span class="work-info-title">Rumi Reads</span>
        <span class="work-info-year">2022</span>
      </div>
    </div>

  </div>
</section>

<!-- Services -->
<section id="services">
  <div class="section-header reveal">
    <span class="section-number">03</span>
    <h2 class="section-title">What I <em>Offer</em></h2>
    <div class="section-rule"></div>
  </div>
  <div class="services-grid">
    <div class="service-item reveal">
      <div class="service-num">01</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="20" cy="20" r="14" stroke="currentColor" stroke-width="1"/>
        <circle cx="20" cy="20" r="6" stroke="currentColor" stroke-width="1"/>
        <line x1="20" y1="6" x2="20" y2="14" stroke="currentColor" stroke-width="1"/>
        <line x1="20" y1="26" x2="20" y2="34" stroke="currentColor" stroke-width="1"/>
        <line x1="6" y1="20" x2="14" y2="20" stroke="currentColor" stroke-width="1"/>
        <line x1="26" y1="20" x2="34" y2="20" stroke="currentColor" stroke-width="1"/>
      </svg>
      <h3 class="service-name">Brand Identity</h3>
      <p class="service-desc">Complete visual identity systems — logo, color palette, typography, guidelines. Everything your brand needs to speak consistently across every touchpoint.</p>
    </div>
    <div class="service-item reveal reveal-delay-1">
      <div class="service-num">02</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="6" y="8" width="28" height="24" rx="1" stroke="currentColor" stroke-width="1"/>
        <line x1="6" y1="14" x2="34" y2="14" stroke="currentColor" stroke-width="0.8"/>
        <line x1="14" y1="8" x2="14" y2="32" stroke="currentColor" stroke-width="0.8"/>
      </svg>
      <h3 class="service-name">Print & Editorial</h3>
      <p class="service-desc">Magazines, annual reports, brochures, and books. Thoughtful layouts where every page turn is a designed experience with intention and rhythm.</p>
    </div>
    <div class="service-item reveal reveal-delay-2">
      <div class="service-num">03</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M8 32 L16 20 L22 26 L28 14 L32 22" stroke="currentColor" stroke-width="1" stroke-linejoin="round"/>
        <circle cx="32" cy="10" r="5" stroke="currentColor" stroke-width="1"/>
      </svg>
      <h3 class="service-name">Packaging Design</h3>
      <p class="service-desc">Packaging that earns its place on the shelf. From concept through print-ready artwork, with full material and production awareness.</p>
    </div>
    <div class="service-item reveal">
      <div class="service-num">04</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="10" y="10" width="20" height="20" stroke="currentColor" stroke-width="1"/>
        <rect x="14" y="14" width="12" height="12" stroke="currentColor" stroke-width="0.8"/>
        <line x1="10" y1="10" x2="14" y2="14" stroke="currentColor" stroke-width="0.5"/>
        <line x1="30" y1="10" x2="26" y2="14" stroke="currentColor" stroke-width="0.5"/>
        <line x1="10" y1="30" x2="14" y2="26" stroke="currentColor" stroke-width="0.5"/>
        <line x1="30" y1="30" x2="26" y2="26" stroke="currentColor" stroke-width="0.5"/>
      </svg>
      <h3 class="service-name">Typography & Type</h3>
      <p class="service-desc">Custom lettering, bespoke typographic compositions, and type-led visual systems. Words as visual objects with weight, texture, and personality.</p>
    </div>
    <div class="service-item reveal reveal-delay-1">
      <div class="service-num">05</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <polygon points="20,6 34,28 6,28" stroke="currentColor" stroke-width="1" fill="none"/>
        <line x1="13" y1="28" x2="27" y2="28" stroke="currentColor" stroke-width="0.8"/>
        <circle cx="20" cy="34" r="3" stroke="currentColor" stroke-width="1"/>
      </svg>
      <h3 class="service-name">Art Direction</h3>
      <p class="service-desc">Creative leadership for campaigns, shoots, and content. Developing the visual language and ensuring every asset speaks as a coherent whole.</p>
    </div>
    <div class="service-item reveal reveal-delay-2">
      <div class="service-num">06</div>
      <svg class="service-icon" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="20" cy="14" r="7" stroke="currentColor" stroke-width="1"/>
        <path d="M6 34 C6 26 34 26 34 34" stroke="currentColor" stroke-width="1"/>
      </svg>
      <h3 class="service-name">Brand Consulting</h3>
      <p class="service-desc">Strategic brand reviews, competitive analysis, and positioning workshops. Building the conceptual foundation before a single pixel is placed.</p>
    </div>
  </div>
</section>

<!-- Process -->
<section id="process">
  <div class="section-header reveal">
    <span class="section-number">04</span>
    <h2 class="section-title">My <em>Process</em></h2>
    <div class="section-rule"></div>
  </div>
  <div class="process-list">
    <div class="process-step reveal">
      <div class="process-step-num">01</div>
      <h3 class="process-step-name">Discover</h3>
      <p class="process-step-desc">Deep listening. Understanding your brand, your audience, your ambitions, and the competitive landscape you inhabit.</p>
    </div>
    <div class="process-step reveal reveal-delay-1">
      <div class="process-step-num">02</div>
      <h3 class="process-step-name">Conceive</h3>
      <p class="process-step-desc">Research, moodboards, and strategic creative concepts — three directions, each with a distinct point of view and rationale.</p>
    </div>
    <div class="process-step reveal reveal-delay-2">
      <div class="process-step-num">03</div>
      <h3 class="process-step-name">Refine</h3>
      <p class="process-step-desc">Collaborative iteration on the chosen direction. Craft, precision, and attention to every detail until the work feels inevitable.</p>
    </div>
    <div class="process-step reveal reveal-delay-3">
      <div class="process-step-num">04</div>
      <h3 class="process-step-name">Deliver</h3>
      <p class="process-step-desc">Production-ready files, comprehensive guidelines, and ongoing support to ensure your brand lives well in the world.</p>
    </div>
  </div>
</section>

<!-- Testimonials -->
<section id="testimonials">
  <div class="section-header reveal">
    <span class="section-number" style="color:var(--gold)">05</span>
    <h2 class="section-title" style="color:var(--cream)">Kind <em style="color:var(--gold)">Words</em></h2>
    <div class="section-rule" style="background:rgba(255,255,255,0.1)"></div>
  </div>
  <div class="testimonials-grid">
    <div class="testimonial-card reveal">
      <div class="testimonial-stars">★★★★★</div>
      <p class="testimonial-text">"Mehvish brought a depth of thought and a precision of craft that completely transformed how our brand presents itself. The final identity felt both timeless and entirely ours."</p>
      <div class="testimonial-author">Sara Al-Mansoori</div>
      <div class="testimonial-role">Founder, Zeyna Fashion</div>
    </div>
    <div class="testimonial-card reveal reveal-delay-1">
      <div class="testimonial-stars">★★★★★</div>
      <p class="testimonial-text">"Working with Mehvish was a revelation. She asked questions no one had asked before, and the work reflected that depth. Our packaging now does the selling for us."</p>
      <div class="testimonial-author">Tariq Mahmoud</div>
      <div class="testimonial-role">Creative Director, Amber Perfumery</div>
    </div>
    <div class="testimonial-card reveal reveal-delay-2">
      <div class="testimonial-stars">★★★★★</div>
      <p class="testimonial-text">"The Atlas rebrand was our most ambitious project. Mehvish navigated every constraint with elegance. Readers have remarked on the magazine's new visual identity without prompting."</p>
      <div class="testimonial-author">Layla Nazari</div>
      <div class="testimonial-role">Editor-in-Chief, Atlas Quarterly</div>
    </div>
  </div>
</section>

<!-- Contact -->
<section id="contact">
  <div class="contact-left reveal">
    <div class="section-number" style="margin-bottom:1rem">06</div>
    <h2 class="contact-invite">Let's make<br>something <em>great</em><br>together.</h2>
    <p class="contact-sub">I take on a limited number of projects each quarter to ensure dedicated attention. Reach out early if you have a project in mind.</p>
    <div class="contact-details">
      <div class="contact-item">
        <span class="contact-item-label">Email</span>
        <span class="contact-item-val">mehvishmoon05@gmail.com</span>
      </div>
      <div class="contact-item">
        <span class="contact-item-label">Based</span>
        <span class="contact-item-val">Gujrat, Pakistan — Available Worldwide</span>
      </div>
      <div class="contact-item">
        <span class="contact-item-label">Availability</span>
        <span class="contact-item-val">Open for new projects from July 2026</span>
      </div>
    </div>
  </div>
  <div class="contact-right reveal reveal-delay-1">
    <form class="contact-form" onsubmit="handleSubmit(event)">
      <div class="form-group">
        <label class="form-label" for="name">Your Name</label>
        <input class="form-input" id="name" type="text" placeholder="Full name">
      </div>
      <div class="form-group">
        <label class="form-label" for="email">Email Address</label>
        <input class="form-input" id="email" type="email" placeholder="name@company.com">
      </div>
      <div class="form-group">
        <label class="form-label" for="project">Project Type</label>
        <input class="form-input" id="project" type="text" placeholder="Brand Identity, Packaging, Editorial…">
      </div>
      <div class="form-group">
        <label class="form-label" for="message">Your Message</label>
        <textarea class="form-textarea" id="message" placeholder="Tell me about your project, timeline, and budget…"></textarea>
      </div>
      <button class="form-submit" type="submit">
        Send Message
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8h12M9 4l5 4-5 4" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </button>
      <div id="form-success" style="display:none;font-family:'DM Mono',monospace;font-size:0.75rem;color:var(--rust);letter-spacing:0.1em;margin-top:1rem">✦ Message sent — I'll be in touch soon.</div>
    </form>
  </div>
</section>

<!-- Footer -->
<footer>
  <div class="footer-logo">Mehvish Ashraf</div>
  <div class="footer-copy">© 2026 — All rights reserved</div>
  <nav class="footer-socials">
    <a href="#">Behance</a>
    <a href="#">Instagram</a>
    <a href="#">LinkedIn</a>
    <a href="#">Dribbble</a>
  </nav>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const dot = cursor.querySelector('.cursor-dot');
  const ring = cursor.querySelector('.cursor-ring');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    dot.style.left = mx + 'px';
    dot.style.top = my + 'px';
  });

  function animateRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => io.observe(el));

  // Form
  function handleSubmit(e) {
    e.preventDefault();
    document.getElementById('form-success').style.display = 'block';
    e.target.reset();
  }

  // Nav blend on scroll
  const nav = document.querySelector('nav');
  window.addEventListener('scroll', () => {
    if (window.scrollY > 60) {
      nav.style.background = 'rgba(245,240,232,0.95)';
      nav.style.mixBlendMode = 'normal';
      nav.style.backdropFilter = 'blur(12px)';
      nav.style.borderBottom = '1px solid rgba(196,81,42,0.1)';
    } else {
      nav.style.background = 'transparent';
      nav.style.mixBlendMode = 'multiply';
      nav.style.backdropFilter = 'none';
      nav.style.borderBottom = 'none';
    }
  });
</script>
</body>
</html>
