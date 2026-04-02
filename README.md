<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CarePlus Clinic — Dr. Sharma</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --blue: #1a6fbe;
    --blue-dark: #135499;
    --blue-light: #e8f2fc;
    --blue-mid: #c5ddf5;
    --blue-pale: #f0f7ff;
    --accent: #2ec4b6;
    --white: #ffffff;
    --off-white: #f8fafd;
    --text: #1a2332;
    --text-mid: #4a5568;
    --text-light: #8898aa;
    --border: #dce8f5;
    --shadow: rgba(26, 111, 190, 0.1);
    --font-serif: 'DM Serif Display', serif;
    --font-sans: 'DM Sans', sans-serif;
    --radius: 16px;
    --radius-sm: 10px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }

  body {
    font-family: var(--font-sans);
    background: var(--white);
    color: var(--text);
    overflow-x: hidden;
    line-height: 1.6;
  }

  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: var(--off-white); }
  ::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 10px; }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 1000;
    background: rgba(255,255,255,0.92);
    backdrop-filter: blur(14px);
    border-bottom: 1px solid var(--border);
    padding: 0 5%;
    height: 68px;
    display: flex; align-items: center; justify-content: space-between;
    transition: box-shadow 0.3s;
  }
  nav.scrolled { box-shadow: 0 4px 24px var(--shadow); }

  .logo {
    display: flex; align-items: center; gap: 10px;
    text-decoration: none;
  }
  .logo-icon {
    width: 36px; height: 36px;
    background: var(--blue);
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }
  .logo-text { font-family: var(--font-serif); font-size: 1.3rem; color: var(--text); }
  .logo-text span { color: var(--blue); }

  .nav-links { display: flex; align-items: center; gap: 2rem; list-style: none; }
  .nav-links a {
    text-decoration: none;
    font-size: 0.88rem;
    font-weight: 500;
    color: var(--text-mid);
    transition: color 0.2s;
    letter-spacing: 0.2px;
  }
  .nav-links a:hover { color: var(--blue); }

  .btn-book {
    background: var(--blue);
    color: var(--white);
    padding: 9px 22px;
    border-radius: 50px;
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.3px;
    transition: background 0.25s, transform 0.2s, box-shadow 0.2s;
    display: inline-flex; align-items: center; gap: 6px;
  }
  .btn-book:hover {
    background: var(--blue-dark);
    transform: translateY(-1px);
    box-shadow: 0 6px 20px rgba(26,111,190,0.35);
  }

  .hamburger {
    display: none; flex-direction: column; gap: 5px;
    cursor: pointer; padding: 6px; background: none; border: none;
  }
  .hamburger span {
    display: block; width: 24px; height: 2px;
    background: var(--text); border-radius: 4px;
    transition: all 0.3s;
  }

  .mobile-menu {
    display: none;
    position: fixed; top: 68px; left: 0; right: 0;
    background: var(--white);
    border-bottom: 1px solid var(--border);
    padding: 1.5rem 5%;
    z-index: 999;
    flex-direction: column; gap: 1.2rem;
    box-shadow: 0 10px 30px var(--shadow);
  }
  .mobile-menu.open { display: flex; }
  .mobile-menu a {
    text-decoration: none; color: var(--text-mid);
    font-size: 0.95rem; font-weight: 500;
    padding: 6px 0;
    border-bottom: 1px solid var(--border);
    transition: color 0.2s;
  }
  .mobile-menu a:hover { color: var(--blue); }

  /* ── HERO ── */
  #home {
    min-height: 100vh;
    background: var(--blue-pale);
    display: flex; align-items: center;
    padding: 120px 5% 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg-shape {
    position: absolute;
    top: -100px; right: -80px;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(26,111,190,0.08) 0%, transparent 65%);
    pointer-events: none;
  }
  .hero-bg-dots {
    position: absolute; bottom: 0; left: 0;
    width: 100%; height: 300px;
    background-image: radial-gradient(circle, rgba(26,111,190,0.1) 1px, transparent 1px);
    background-size: 28px 28px;
    pointer-events: none;
    mask-image: linear-gradient(to top, white 20%, transparent 100%);
  }

  .hero-inner {
    display: grid;
    grid-template-columns: 1.1fr 0.9fr;
    gap: 4rem;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
    position: relative; z-index: 1;
  }

  .hero-tag {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--white);
    border: 1px solid var(--blue-mid);
    color: var(--blue);
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    padding: 6px 14px;
    border-radius: 50px;
    margin-bottom: 1.5rem;
  }
  .hero-tag .dot { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; }

  .hero-title {
    font-family: var(--font-serif);
    font-size: clamp(2.6rem, 5.5vw, 4rem);
    line-height: 1.15;
    color: var(--text);
    margin-bottom: 1.2rem;
  }
  .hero-title span { color: var(--blue); }

  .hero-desc {
    font-size: 1rem;
    color: var(--text-mid);
    line-height: 1.8;
    max-width: 480px;
    margin-bottom: 2.2rem;
  }

  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 3rem; }

  .btn-primary {
    background: var(--blue);
    color: var(--white);
    padding: 13px 28px;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 600;
    font-size: 0.9rem;
    transition: all 0.25s;
    display: inline-flex; align-items: center; gap: 7px;
    border: none; cursor: pointer;
  }
  .btn-primary:hover {
    background: var(--blue-dark);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(26,111,190,0.35);
  }

  .btn-secondary {
    background: transparent;
    color: var(--blue);
    padding: 13px 28px;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 600;
    font-size: 0.9rem;
    border: 2px solid var(--blue-mid);
    transition: all 0.25s;
    display: inline-flex; align-items: center; gap: 7px;
  }
  .btn-secondary:hover {
    background: var(--blue-light);
    border-color: var(--blue);
  }

  .hero-trust {
    display: flex; gap: 2.5rem; flex-wrap: wrap;
  }
  .trust-item { text-align: center; }
  .trust-num {
    font-family: var(--font-serif);
    font-size: 1.8rem;
    color: var(--blue);
    line-height: 1;
  }
  .trust-label { font-size: 0.75rem; color: var(--text-light); margin-top: 3px; letter-spacing: 0.3px; }

  /* Hero Card */
  .hero-visual { display: flex; justify-content: center; align-items: center; }

  .doctor-card {
    background: var(--white);
    border-radius: 24px;
    padding: 2.5rem;
    box-shadow: 0 20px 60px rgba(26,111,190,0.14);
    max-width: 360px;
    width: 100%;
    position: relative;
  }
  .doctor-card::before {
    content: '';
    position: absolute;
    top: -2px; left: -2px; right: -2px; bottom: -2px;
    border-radius: 26px;
    background: linear-gradient(135deg, rgba(26,111,190,0.2), transparent 60%);
    z-index: -1;
  }

  .card-header {
    display: flex; align-items: center; gap: 1rem; margin-bottom: 1.5rem;
  }
  .avatar-ring {
    width: 70px; height: 70px; border-radius: 50%;
    background: linear-gradient(135deg, var(--blue), var(--accent));
    display: flex; align-items: center; justify-content: center;
    font-size: 1.8rem;
    flex-shrink: 0;
  }
  .card-name { font-family: var(--font-serif); font-size: 1.2rem; color: var(--text); }
  .card-title { font-size: 0.8rem; color: var(--text-light); margin-top: 2px; }

  .card-badges {
    display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 1.5rem;
  }
  .badge {
    background: var(--blue-light);
    color: var(--blue);
    font-size: 0.72rem;
    font-weight: 600;
    padding: 5px 12px;
    border-radius: 50px;
    letter-spacing: 0.2px;
  }

  .card-divider { height: 1px; background: var(--border); margin-bottom: 1.5rem; }

  .card-timings { display: flex; flex-direction: column; gap: 10px; }
  .timing-row {
    display: flex; align-items: center; justify-content: space-between;
    font-size: 0.83rem;
  }
  .timing-day { color: var(--text-mid); font-weight: 500; display: flex; align-items: center; gap: 7px; }
  .timing-day .icon { color: var(--blue); }
  .timing-time { color: var(--blue); font-weight: 600; }

  .available-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: rgba(46,196,182,0.1);
    color: #1a9e94;
    font-size: 0.75rem;
    font-weight: 600;
    padding: 5px 12px;
    border-radius: 50px;
    margin-top: 1.2rem;
  }
  .available-badge .pulse {
    width: 7px; height: 7px; background: var(--accent);
    border-radius: 50%;
    animation: pulse 1.5s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.4); }
  }

  /* ── SECTIONS BASE ── */
  section { padding: 90px 5%; }
  .container { max-width: 1100px; margin: 0 auto; }

  .section-tag {
    display: inline-flex; align-items: center; gap: 6px;
    color: var(--blue);
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-bottom: 0.8rem;
  }
  .section-tag::before {
    content: '';
    display: inline-block;
    width: 20px; height: 2px;
    background: var(--blue);
    border-radius: 2px;
  }

  .section-title {
    font-family: var(--font-serif);
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    line-height: 1.2;
    color: var(--text);
    margin-bottom: 0.8rem;
  }
  .section-title span { color: var(--blue); }
  .section-desc { font-size: 0.95rem; color: var(--text-mid); line-height: 1.8; max-width: 520px; }

  /* ── ABOUT ── */
  #about { background: var(--white); }

  .about-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
    max-width: 1100px;
    margin: 0 auto;
  }

  .about-image-block { position: relative; }

  .about-card-main {
    background: var(--blue-pale);
    border-radius: 24px;
    padding: 3rem 2.5rem;
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }
  .about-card-main::after {
    content: '+';
    position: absolute;
    bottom: -30px; right: -20px;
    font-size: 12rem;
    color: rgba(26,111,190,0.05);
    font-weight: 900;
    line-height: 1;
    pointer-events: none;
  }

  .doc-info { display: flex; gap: 1rem; align-items: flex-start; margin-bottom: 2rem; }
  .doc-avatar {
    width: 80px; height: 80px; border-radius: 50%;
    background: linear-gradient(135deg, var(--blue), #5ba3e0);
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem; flex-shrink: 0;
    box-shadow: 0 8px 20px rgba(26,111,190,0.3);
  }
  .doc-name { font-family: var(--font-serif); font-size: 1.4rem; color: var(--text); }
  .doc-designation { font-size: 0.82rem; color: var(--blue); font-weight: 600; margin-top: 2px; }
  .doc-reg { font-size: 0.78rem; color: var(--text-light); margin-top: 3px; }

  .about-stats {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;
  }
  .about-stat {
    background: var(--white);
    border-radius: 14px;
    padding: 1rem 1.2rem;
    text-align: center;
    box-shadow: 0 2px 10px var(--shadow);
  }
  .about-stat-num { font-family: var(--font-serif); font-size: 1.6rem; color: var(--blue); }
  .about-stat-label { font-size: 0.72rem; color: var(--text-light); margin-top: 2px; }

  .about-text .section-desc { max-width: 100%; }

  .about-skills { display: flex; flex-direction: column; gap: 10px; margin-top: 2rem; }
  .skill-item { display: flex; flex-direction: column; gap: 5px; }
  .skill-label { font-size: 0.8rem; font-weight: 600; color: var(--text-mid); display: flex; justify-content: space-between; }
  .skill-bar { height: 5px; background: var(--border); border-radius: 10px; overflow: hidden; }
  .skill-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--blue), var(--accent));
    border-radius: 10px;
    transition: width 1.2s ease;
    width: 0%;
  }

  .about-highlights { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 2rem; }
  .highlight-pill {
    background: var(--blue-light);
    color: var(--blue);
    font-size: 0.8rem;
    font-weight: 600;
    padding: 7px 16px;
    border-radius: 50px;
    border: 1px solid var(--blue-mid);
  }

  /* ── SERVICES ── */
  #services { background: var(--off-white); }

  .services-header { text-align: center; margin-bottom: 3.5rem; }
  .services-header .section-desc { margin: 0 auto; }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    max-width: 1100px;
    margin: 0 auto;
  }

  .service-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 2.5rem 2rem;
    border: 1px solid var(--border);
    transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
    position: relative;
    overflow: hidden;
    cursor: default;
  }
  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--accent));
    transform: scaleX(0);
    transition: transform 0.3s;
  }
  .service-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 16px 40px rgba(26,111,190,0.12);
    border-color: var(--blue-mid);
  }
  .service-card:hover::before { transform: scaleX(1); }

  .service-icon-wrap {
    width: 56px; height: 56px;
    background: var(--blue-light);
    border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.6rem;
    margin-bottom: 1.5rem;
    transition: background 0.3s;
  }
  .service-card:hover .service-icon-wrap { background: var(--blue-mid); }

  .service-name {
    font-family: var(--font-serif);
    font-size: 1.3rem;
    color: var(--text);
    margin-bottom: 0.8rem;
  }
  .service-desc { font-size: 0.88rem; color: var(--text-mid); line-height: 1.7; margin-bottom: 1.5rem; }

  .service-list { list-style: none; display: flex; flex-direction: column; gap: 7px; }
  .service-list li {
    font-size: 0.82rem;
    color: var(--text-mid);
    display: flex; align-items: center; gap: 8px;
  }
  .service-list li::before {
    content: '✓';
    width: 18px; height: 18px;
    background: var(--blue-light);
    color: var(--blue);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.65rem;
    font-weight: 700;
    flex-shrink: 0;
  }

  /* ── APPOINTMENT ── */
  #appointment {
    background: linear-gradient(135deg, var(--blue) 0%, #135499 100%);
    position: relative; overflow: hidden;
  }
  #appointment::before {
    content: '';
    position: absolute; top: -100px; right: -100px;
    width: 500px; height: 500px;
    background: rgba(255,255,255,0.04);
    border-radius: 50%;
    pointer-events: none;
  }
  #appointment::after {
    content: '';
    position: absolute; bottom: -80px; left: -80px;
    width: 350px; height: 350px;
    background: rgba(46,196,182,0.08);
    border-radius: 50%;
    pointer-events: none;
  }

  .appt-inner {
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: 5rem;
    align-items: center;
    max-width: 1100px;
    margin: 0 auto;
    position: relative; z-index: 1;
  }

  .appt-text .section-tag { color: rgba(255,255,255,0.7); }
  .appt-text .section-tag::before { background: rgba(255,255,255,0.5); }
  .appt-text .section-title { color: var(--white); }
  .appt-text .section-desc { color: rgba(255,255,255,0.8); }

  .appt-features { display: flex; flex-direction: column; gap: 14px; margin-top: 2rem; }
  .appt-feature {
    display: flex; align-items: center; gap: 12px;
    color: rgba(255,255,255,0.9);
    font-size: 0.9rem;
    font-weight: 500;
  }
  .appt-feature-icon {
    width: 36px; height: 36px;
    background: rgba(255,255,255,0.12);
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem;
    flex-shrink: 0;
  }

  .appt-form-wrap {
    background: var(--white);
    border-radius: 24px;
    padding: 2.5rem;
    box-shadow: 0 20px 60px rgba(0,0,0,0.15);
  }

  .form-title {
    font-family: var(--font-serif);
    font-size: 1.4rem;
    color: var(--text);
    margin-bottom: 0.4rem;
  }
  .form-subtitle { font-size: 0.85rem; color: var(--text-light); margin-bottom: 2rem; }

  .form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 1.2rem; }
  .form-group label {
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 0.5px;
    color: var(--text-mid);
    text-transform: uppercase;
  }
  .form-group input,
  .form-group textarea,
  .form-group select {
    background: var(--off-white);
    border: 1.5px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 11px 14px;
    font-family: var(--font-sans);
    font-size: 0.9rem;
    color: var(--text);
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
    width: 100%;
    -webkit-appearance: none;
  }
  .form-group input:focus,
  .form-group textarea:focus,
  .form-group select:focus {
    border-color: var(--blue);
    box-shadow: 0 0 0 3px rgba(26,111,190,0.1);
    background: var(--white);
  }
  .form-group textarea { height: 100px; resize: none; }

  .btn-whatsapp {
    width: 100%;
    padding: 14px;
    background: #25D366;
    color: var(--white);
    border: none;
    border-radius: 50px;
    font-family: var(--font-sans);
    font-weight: 700;
    font-size: 0.9rem;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center; gap: 8px;
    transition: all 0.25s;
    text-decoration: none;
    letter-spacing: 0.3px;
  }
  .btn-whatsapp:hover {
    background: #1dab53;
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(37,211,102,0.35);
  }
  .btn-whatsapp svg { width: 20px; height: 20px; flex-shrink: 0; }

  .form-note { text-align: center; font-size: 0.75rem; color: var(--text-light); margin-top: 10px; }

  /* ── TESTIMONIALS ── */
  #testimonials { background: var(--white); }

  .testimonials-header { text-align: center; margin-bottom: 3.5rem; }
  .testimonials-header .section-desc { margin: 0 auto; }

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    max-width: 1100px;
    margin: 0 auto;
  }

  .testimonial-card {
    background: var(--blue-pale);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 2rem;
    transition: transform 0.3s, box-shadow 0.3s;
    position: relative;
  }
  .testimonial-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 32px rgba(26,111,190,0.1);
  }

  .quote-icon {
    font-family: Georgia, serif;
    font-size: 4rem;
    color: var(--blue-mid);
    line-height: 1;
    margin-bottom: -0.5rem;
    display: block;
  }

  .stars { color: #f6c90e; font-size: 0.9rem; margin-bottom: 1rem; letter-spacing: 1px; }

  .testimonial-text {
    font-size: 0.9rem;
    color: var(--text-mid);
    line-height: 1.8;
    margin-bottom: 1.8rem;
    font-style: italic;
  }

  .testimonial-author {
    display: flex; align-items: center; gap: 12px;
    border-top: 1px solid var(--border);
    padding-top: 1.2rem;
  }
  .author-avatar {
    width: 42px; height: 42px; border-radius: 50%;
    background: linear-gradient(135deg, var(--blue), var(--accent));
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }
  .author-name { font-weight: 700; font-size: 0.9rem; color: var(--text); }
  .author-tag { font-size: 0.75rem; color: var(--text-light); margin-top: 1px; }

  /* ── CONTACT ── */
  #contact { background: var(--off-white); }

  .contact-inner {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 4rem;
    align-items: start;
    max-width: 1100px;
    margin: 0 auto;
  }

  .contact-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 2.5rem;
    border: 1px solid var(--border);
    box-shadow: 0 4px 20px var(--shadow);
  }

  .contact-item {
    display: flex; gap: 1rem; align-items: flex-start;
    padding: 1.2rem 0;
    border-bottom: 1px solid var(--border);
  }
  .contact-item:last-child { border-bottom: none; }

  .contact-icon-wrap {
    width: 44px; height: 44px;
    background: var(--blue-light);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }
  .contact-label { font-size: 0.72rem; font-weight: 700; color: var(--text-light); letter-spacing: 0.8px; text-transform: uppercase; }
  .contact-val { font-size: 0.9rem; color: var(--text); font-weight: 500; margin-top: 2px; line-height: 1.5; }

  .map-placeholder {
    background: var(--white);
    border-radius: var(--radius);
    border: 1px solid var(--border);
    overflow: hidden;
    box-shadow: 0 4px 20px var(--shadow);
  }
  .map-header {
    padding: 1.5rem;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 10px;
  }
  .map-header-icon { font-size: 1.2rem; }
  .map-header-text { font-size: 0.88rem; font-weight: 700; color: var(--text); }
  .map-header-sub { font-size: 0.75rem; color: var(--text-light); }

  .map-visual {
    background: var(--blue-pale);
    height: 200px;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    gap: 10px;
    position: relative;
    overflow: hidden;
  }
  .map-visual::before {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(26,111,190,0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(26,111,190,0.06) 1px, transparent 1px);
    background-size: 30px 30px;
  }
  .map-pin {
    width: 50px; height: 50px;
    background: var(--blue);
    border-radius: 50% 50% 50% 0;
    transform: rotate(-45deg);
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 6px 20px rgba(26,111,190,0.4);
    position: relative; z-index: 1;
  }
  .map-pin-inner { transform: rotate(45deg); font-size: 1.2rem; }
  .map-label { font-size: 0.8rem; font-weight: 700; color: var(--blue); position: relative; z-index: 1; }

  .map-cta {
    padding: 1.5rem;
    display: flex; gap: 1rem; flex-wrap: wrap;
  }

  .btn-map {
    flex: 1;
    padding: 10px;
    border-radius: 50px;
    font-size: 0.82rem;
    font-weight: 700;
    text-align: center;
    text-decoration: none;
    transition: all 0.25s;
    min-width: 130px;
  }
  .btn-map.primary { background: var(--blue); color: var(--white); }
  .btn-map.primary:hover { background: var(--blue-dark); }
  .btn-map.outline { background: transparent; color: var(--blue); border: 1.5px solid var(--border); }
  .btn-map.outline:hover { border-color: var(--blue); background: var(--blue-light); }

  /* ── FOOTER ── */
  footer {
    background: var(--text);
    color: rgba(255,255,255,0.7);
    padding: 2.5rem 5%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .footer-logo { font-family: var(--font-serif); font-size: 1.2rem; color: var(--white); }
  .footer-logo span { color: #5ba3e0; }
  .footer-copy { font-size: 0.8rem; }
  .footer-links { display: flex; gap: 1.5rem; }
  .footer-links a { color: rgba(255,255,255,0.6); text-decoration: none; font-size: 0.8rem; transition: color 0.2s; }
  .footer-links a:hover { color: var(--white); }

  /* ── SCROLL ANIMATIONS ── */
  .reveal {
    opacity: 0; transform: translateY(25px);
    transition: opacity 0.65s ease, transform 0.65s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-left { opacity: 0; transform: translateX(-25px); transition: opacity 0.65s ease, transform 0.65s ease; }
  .reveal-left.visible { opacity: 1; transform: none; }
  .reveal-right { opacity: 0; transform: translateX(25px); transition: opacity 0.65s ease, transform 0.65s ease; }
  .reveal-right.visible { opacity: 1; transform: none; }

  /* ── RESPONSIVE ── */
  @media (max-width: 1024px) {
    .hero-inner { grid-template-columns: 1fr; gap: 3rem; }
    .hero-visual { display: none; }
    .about-inner { grid-template-columns: 1fr; gap: 3rem; }
    .services-grid { grid-template-columns: 1fr; }
    .appt-inner { grid-template-columns: 1fr; gap: 3rem; }
    .testimonials-grid { grid-template-columns: 1fr; }
    .contact-inner { grid-template-columns: 1fr; gap: 2.5rem; }
  }
  @media (max-width: 768px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    nav .btn-book { display: none; }
    section { padding: 70px 5%; }
    .hero-trust { gap: 1.5rem; }
    .about-stats { grid-template-columns: 1fr 1fr; }
    footer { flex-direction: column; text-align: center; }
    .footer-links { flex-wrap: wrap; justify-content: center; }
  }
  @media (max-width: 480px) {
    .hero-actions { flex-direction: column; }
    .btn-primary, .btn-secondary { text-align: center; width: 100%; justify-content: center; }
    .services-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav id="mainNav">
  <a href="#home" class="logo">
    <div class="logo-icon">🏥</div>
    <span class="logo-text">Care<span>Plus</span> Clinic</span>
  </a>
  <ul class="nav-links">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="https://wa.me/919876543210?text=Hello%20Dr.%20Sharma%2C%20I%20would%20like%20to%20book%20an%20appointment%20at%20CarePlus%20Clinic." target="_blank" class="btn-book">📅 Book Appointment</a>
  <button class="hamburger" id="hamburger" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<div class="mobile-menu" id="mobileMenu">
  <a href="#home" onclick="closeMobileMenu()">Home</a>
  <a href="#about" onclick="closeMobileMenu()">About Doctor</a>
  <a href="#services" onclick="closeMobileMenu()">Services</a>
  <a href="#appointment" onclick="closeMobileMenu()">Book Appointment</a>
  <a href="#testimonials" onclick="closeMobileMenu()">Reviews</a>
  <a href="#contact" onclick="closeMobileMenu()">Contact</a>
</div>

<!-- HERO -->
<section id="home">
  <div class="hero-bg-shape"></div>
  <div class="hero-bg-dots"></div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-tag"><span class="dot"></span> Trusted Care Since 2014</div>
      <h1 class="hero-title">Your Health,<br><span>Our Priority</span></h1>
      <p class="hero-desc">Compassionate, expert medical care for every stage of your life. Dr. Sharma and our dedicated team are here to keep you and your family healthy.</p>
      <div class="hero-actions">
        <a href="https://wa.me/919876543210?text=Hello%20Dr.%20Sharma%2C%20I%20would%20like%20to%20book%20an%20appointment." target="_blank" class="btn-primary">
          📅 Book an Appointment
        </a>
        <a href="#services" class="btn-secondary">Our Services →</a>
      </div>
      <div class="hero-trust">
        <div class="trust-item">
          <div class="trust-num">5000+</div>
          <div class="trust-label">Happy Patients</div>
        </div>
        <div class="trust-item">
          <div class="trust-num">10+</div>
          <div class="trust-label">Years Experience</div>
        </div>
        <div class="trust-item">
          <div class="trust-num">4.9★</div>
          <div class="trust-label">Patient Rating</div>
        </div>
      </div>
    </div>
    <div class="hero-visual">
      <div class="doctor-card">
        <div class="card-header">
          <div class="avatar-ring">👨‍⚕️</div>
          <div>
            <div class="card-name">Dr. Rajan Sharma</div>
            <div class="card-title">MBBS, MD — General Medicine</div>
          </div>
        </div>
        <div class="card-badges">
          <span class="badge">General Medicine</span>
          <span class="badge">Child Care</span>
          <span class="badge">Diabetes</span>
        </div>
        <div class="card-divider"></div>
        <div class="card-timings">
          <div class="timing-row">
            <span class="timing-day"><span class="icon">📅</span> Mon – Fri</span>
            <span class="timing-time">9:00 AM – 7:00 PM</span>
          </div>
          <div class="timing-row">
            <span class="timing-day"><span class="icon">📅</span> Saturday</span>
            <span class="timing-time">9:00 AM – 2:00 PM</span>
          </div>
          <div class="timing-row">
            <span class="timing-day"><span class="icon">📅</span> Sunday</span>
            <span class="timing-time">Emergency Only</span>
          </div>
        </div>
        <div class="available-badge">
          <span class="pulse"></span>
          Accepting New Patients
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-inner">
    <div class="about-image-block reveal-left">
      <div class="about-card-main">
        <div class="doc-info">
          <div class="doc-avatar">👨‍⚕️</div>
          <div>
            <div class="doc-name">Dr. Rajan Sharma</div>
            <div class="doc-designation">MBBS, MD (General Medicine)</div>
            <div class="doc-reg">Reg. No. MCI-456789</div>
          </div>
        </div>
        <div class="about-stats">
          <div class="about-stat">
            <div class="about-stat-num">10+</div>
            <div class="about-stat-label">Years Experience</div>
          </div>
          <div class="about-stat">
            <div class="about-stat-num">5000+</div>
            <div class="about-stat-label">Patients Treated</div>
          </div>
          <div class="about-stat">
            <div class="about-stat-num">3</div>
            <div class="about-stat-label">Specializations</div>
          </div>
          <div class="about-stat">
            <div class="about-stat-num">4.9★</div>
            <div class="about-stat-label">Average Rating</div>
          </div>
        </div>
      </div>
    </div>
    <div class="about-text reveal-right">
      <div class="section-tag">About the Doctor</div>
      <h2 class="section-title">Meet <span>Dr. Rajan Sharma</span></h2>
      <p class="section-desc">With over 10 years of dedicated service, Dr. Sharma brings warmth, precision, and genuine care to every consultation. Trained at KGMC Lucknow and post-graduated from AIIMS Delhi, he combines clinical expertise with a patient-first approach.</p>
      <p class="section-desc" style="margin-top:1rem;">His philosophy is simple: listen deeply, diagnose accurately, and treat compassionately. Whether it's a routine check-up or a complex chronic condition, every patient receives his full attention.</p>
      <div class="about-skills">
        <div class="skill-item">
          <div class="skill-label"><span>General Medicine</span><span>95%</span></div>
          <div class="skill-bar"><div class="skill-fill" data-width="95"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-label"><span>Pediatrics / Child Care</span><span>88%</span></div>
          <div class="skill-bar"><div class="skill-fill" data-width="88"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-label"><span>Diabetes & Endocrinology</span><span>90%</span></div>
          <div class="skill-bar"><div class="skill-fill" data-width="90"></div></div>
        </div>
      </div>
      <div class="about-highlights">
        <span class="highlight-pill">🎓 MBBS — KGMC Lucknow</span>
        <span class="highlight-pill">🎓 MD — AIIMS Delhi</span>
        <span class="highlight-pill">🏆 Best Doctor Award 2022</span>
        <span class="highlight-pill">❤️ 5000+ Lives Touched</span>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="services-header reveal">
    <div class="section-tag">What We Treat</div>
    <h2 class="section-title">Our Core <span>Services</span></h2>
    <p class="section-desc">Comprehensive healthcare services designed for you and your entire family — delivered with empathy and expertise.</p>
  </div>
  <div class="services-grid reveal">
    <div class="service-card">
      <div class="service-icon-wrap">🩺</div>
      <div class="service-name">General Checkup</div>
      <p class="service-desc">Thorough head-to-toe health assessments to detect early signs of illness and ensure you're at your healthiest.</p>
      <ul class="service-list">
        <li>Full physical examination</li>
        <li>Blood pressure & sugar check</li>
        <li>Fever, cold & infection treatment</li>
        <li>Prescription & health advice</li>
        <li>Preventive health screening</li>
      </ul>
    </div>
    <div class="service-card">
      <div class="service-icon-wrap">👶</div>
      <div class="service-name">Child Care</div>
      <p class="service-desc">Specialized pediatric consultations for your little ones — from newborns to teenagers — with a gentle, reassuring approach.</p>
      <ul class="service-list">
        <li>Newborn & infant care</li>
        <li>Vaccination schedule</li>
        <li>Growth & development monitoring</li>
        <li>Nutrition & diet guidance</li>
        <li>Respiratory & allergy care</li>
      </ul>
    </div>
    <div class="service-card">
      <div class="service-icon-wrap">🩸</div>
      <div class="service-name">Diabetes Care</div>
      <p class="service-desc">Comprehensive diabetes management with regular monitoring, lifestyle counseling, and evidence-based treatment plans.</p>
      <ul class="service-list">
        <li>Type 1 & Type 2 diabetes</li>
        <li>HbA1c & glucose monitoring</li>
        <li>Custom diet & exercise plan</li>
        <li>Insulin & medication management</li>
        <li>Complication prevention</li>
      </ul>
    </div>
  </div>
</section>

<!-- APPOINTMENT -->
<section id="appointment">
  <div class="appt-inner">
    <div class="appt-text reveal-left">
      <div class="section-tag">Quick & Easy</div>
      <h2 class="section-title" style="color:var(--white);">Book Your <span style="color:#7ec8f5">Appointment</span></h2>
      <p class="section-desc">Skip the queue. Fill the form and connect with Dr. Sharma on WhatsApp instantly for a confirmed slot.</p>
      <div class="appt-features">
        <div class="appt-feature">
          <div class="appt-feature-icon">⚡</div>
          Instant WhatsApp confirmation
        </div>
        <div class="appt-feature">
          <div class="appt-feature-icon">🕘</div>
          Flexible morning & evening slots
        </div>
        <div class="appt-feature">
          <div class="appt-feature-icon">🏠</div>
          Home visit available on request
        </div>
        <div class="appt-feature">
          <div class="appt-feature-icon">💊</div>
          Prescription on same day
        </div>
      </div>
    </div>
    <div class="reveal-right">
      <div class="appt-form-wrap">
        <div class="form-title">Request an Appointment</div>
        <div class="form-subtitle">Fill in details below — we'll reach out on WhatsApp</div>
        <div class="form-group">
          <label>Full Name</label>
          <input type="text" id="apptName" placeholder="e.g. Rahul Verma">
        </div>
        <div class="form-group">
          <label>Phone Number</label>
          <input type="tel" id="apptPhone" placeholder="+91 98765 43210">
        </div>
        <div class="form-group">
          <label>Service Needed</label>
          <select id="apptService">
            <option value="" disabled selected>Select service</option>
            <option>General Checkup</option>
            <option>Child Care</option>
            <option>Diabetes Care</option>
            <option>Other / Not Sure</option>
          </select>
        </div>
        <div class="form-group">
          <label>Message (Optional)</label>
          <textarea id="apptMessage" placeholder="Briefly describe your symptoms or request..."></textarea>
        </div>
        <a id="whatsappBtn" href="#" target="_blank" class="btn-whatsapp" onclick="buildWhatsAppLink(event)">
          <svg viewBox="0 0 24 24" fill="currentColor">
            <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/>
            <path d="M12 0C5.373 0 0 5.373 0 12c0 2.123.554 4.115 1.523 5.845L0 24l6.32-1.496A11.94 11.94 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.794 9.794 0 01-5.003-1.374l-.359-.213-3.72.88.927-3.618-.234-.372A9.772 9.772 0 012.182 12C2.182 6.574 6.574 2.182 12 2.182S21.818 6.574 21.818 12 17.426 21.818 12 21.818z"/>
          </svg>
          Book via WhatsApp
        </a>
        <p class="form-note">🔒 Your information is private & never shared</p>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="testimonials-header reveal">
    <div class="section-tag">Patient Stories</div>
    <h2 class="section-title">What Our <span>Patients Say</span></h2>
    <p class="section-desc">Real words from real patients who trusted us with their health.</p>
  </div>
  <div class="testimonials-grid reveal">
    <div class="testimonial-card">
      <span class="quote-icon">"</span>
      <div class="stars">★★★★★</div>
      <p class="testimonial-text">Dr. Sharma has been treating our family for over 5 years. He's incredibly patient, explains everything clearly, and never rushes the consultation. Our kids actually look forward to their checkups!</p>
      <div class="testimonial-author">
        <div class="author-avatar">👩</div>
        <div>
          <div class="author-name">Priya Agarwal</div>
          <div class="author-tag">Mother of two · Patient since 2019</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card">
      <span class="quote-icon">"</span>
      <div class="stars">★★★★★</div>
      <p class="testimonial-text">I was struggling with uncontrolled diabetes for years. Dr. Sharma redesigned my entire diet and medication plan. Within 3 months, my HbA1c dropped from 9.2 to 6.8. Truly life-changing care.</p>
      <div class="testimonial-author">
        <div class="author-avatar">👴</div>
        <div>
          <div class="author-name">Ramesh Gupta</div>
          <div class="author-tag">Diabetes Patient · 62 years old</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card">
      <span class="quote-icon">"</span>
      <div class="stars">★★★★★</div>
      <p class="testimonial-text">The best clinic I've visited in Lucknow. Clean, professional, and the WhatsApp booking system is so convenient. Dr. Sharma diagnosed my persistent cough as early-stage TB when two other doctors missed it.</p>
      <div class="testimonial-author">
        <div class="author-avatar">👨</div>
        <div>
          <div class="author-name">Sunil Mishra</div>
          <div class="author-tag">IT Professional · Patient since 2022</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-inner">
    <div class="reveal-left">
      <div class="section-tag">Find Us</div>
      <h2 class="section-title" style="margin-bottom:2rem;">Contact <span>Info</span></h2>
      <div class="contact-card">
        <div class="contact-item">
          <div class="contact-icon-wrap">📍</div>
          <div>
            <div class="contact-label">Address</div>
            <div class="contact-val">12-A, Medical Square, Hazratganj<br>Lucknow, Uttar Pradesh – 226001</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon-wrap">📞</div>
          <div>
            <div class="contact-label">Phone</div>
            <div class="contact-val">+91 98765 43210<br>+91 05224 56789</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon-wrap">⏰</div>
          <div>
            <div class="contact-label">Clinic Hours</div>
            <div class="contact-val">Mon–Fri: 9:00 AM – 7:00 PM<br>Saturday: 9:00 AM – 2:00 PM<br>Sunday: Emergency Only</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon-wrap">✉️</div>
          <div>
            <div class="contact-label">Email</div>
            <div class="contact-val">dr.sharma@carepluscliniclko.in</div>
          </div>
        </div>
      </div>
    </div>
    <div class="reveal-right">
      <div class="map-placeholder">
        <div class="map-header">
          <div class="map-header-icon">🗺️</div>
          <div>
            <div class="map-header-text">CarePlus Clinic</div>
            <div class="map-header-sub">12-A, Medical Square, Hazratganj, Lucknow</div>
          </div>
        </div>
        <div class="map-visual">
          <div class="map-pin"><div class="map-pin-inner">🏥</div></div>
          <div class="map-label">CarePlus Clinic — Hazratganj</div>
        </div>
        <div class="map-cta">
          <a href="https://wa.me/919876543210?text=Hi%20Dr.%20Sharma!%20I%20need%20directions%20to%20CarePlus%20Clinic." target="_blank" class="btn-map primary">📱 WhatsApp Us</a>
          <a href="https://maps.google.com/?q=Hazratganj+Lucknow" target="_blank" class="btn-map outline">🗺️ Open Maps</a>
        </div>
      </div>
      <div style="margin-top:1.5rem;">
        <a href="https://wa.me/919876543210?text=Hello%20Dr.%20Sharma%2C%20I%20would%20like%20to%20book%20an%20appointment%20at%20CarePlus%20Clinic." target="_blank" class="btn-primary" style="width:100%;justify-content:center;border-radius:14px;padding:15px;">
          📅 Book Appointment via WhatsApp
        </a>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Care<span>Plus</span> Clinic</div>
  <div class="footer-links">
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#services">Services</a>
    <a href="#contact">Contact</a>
  </div>
  <div class="footer-copy">© 2024 CarePlus Clinic, Lucknow. All rights reserved.</div>
</footer>

<script>
  // NAV SCROLL EFFECT
  const nav = document.getElementById('mainNav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 30);
  });

  // HAMBURGER
  const hamburger = document.getElementById('hamburger');
  const mobileMenu = document.getElementById('mobileMenu');
  hamburger.addEventListener('click', () => {
    mobileMenu.classList.toggle('open');
    const spans = hamburger.querySelectorAll('span');
    if (mobileMenu.classList.contains('open')) {
      spans[0].style.transform = 'rotate(45deg) translate(5px,5px)';
      spans[1].style.opacity = '0';
      spans[2].style.transform = 'rotate(-45deg) translate(5px,-5px)';
    } else {
      spans.forEach(s => { s.style.transform = ''; s.style.opacity = ''; });
    }
  });
  function closeMobileMenu() {
    mobileMenu.classList.remove('open');
    hamburger.querySelectorAll('span').forEach(s => { s.style.transform = ''; s.style.opacity = ''; });
  }

  // WHATSAPP FORM
  function buildWhatsAppLink(e) {
    const name = document.getElementById('apptName').value.trim() || 'A patient';
    const phone = document.getElementById('apptPhone').value.trim();
    const service = document.getElementById('apptService').value || 'General Checkup';
    const message = document.getElementById('apptMessage').value.trim();
    let text = `Hello Dr. Sharma! 👋\n\nAppointment Request:\n👤 Name: ${name}\n📱 Phone: ${phone || 'Not provided'}\n🏥 Service: ${service}`;
    if (message) text += `\n💬 Note: ${message}`;
    text += `\n\nPlease confirm my slot. Thank you!`;
    document.getElementById('whatsappBtn').href = `https://wa.me/919876543210?text=${encodeURIComponent(text)}`;
  }

  // SCROLL REVEAL
  const allReveals = document.querySelectorAll('.reveal, .reveal-left, .reveal-right');
  const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        revealObserver.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  allReveals.forEach(el => revealObserver.observe(el));

  // SKILL BARS ANIMATION
  const skillFills = document.querySelectorAll('.skill-fill');
  const skillObserver = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const target = e.target;
        const width = target.dataset.width;
        setTimeout(() => { target.style.width = width + '%'; }, 200);
        skillObserver.unobserve(target);
      }
    });
  }, { threshold: 0.3 });
  skillFills.forEach(el => skillObserver.observe(el));
</script>
</body>
</html>
