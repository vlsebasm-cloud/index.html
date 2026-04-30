# index.html
<html lang="es"><head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Evans_Line — Moda &amp; Estilo</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&amp;family=Montserrat:wght@300;400;500;600&amp;display=swap" rel="stylesheet">
<style>
    :root {
        --black: #0a0a0a;
        --white: #faf8f5;
        --gold: #c9a84c;
        --gold-light: #e8d08a;
        --cream: #f2ede4;
        --dark-gray: #1c1c1c;
        --mid-gray: #5a5a5a;
        --border: #d4c9b0;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
        background: var(--white);
        color: var(--black);
        font-family: 'Montserrat', sans-serif;
        font-weight: 300;
        overflow-x: hidden;
    }

    /* ─── CURSOR ─── */
    .cursor {
        width: 10px; height: 10px;
        background: var(--gold);
        border-radius: 50%;
        position: fixed;
        pointer-events: none;
        z-index: 9999;
        transition: transform 0.15s ease;
        mix-blend-mode: multiply;
    }

    /* ─── NAVBAR ─── */
    nav {
        position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
        display: flex; align-items: center; justify-content: space-between;
        padding: 1.5rem 4rem;
        background: rgba(250, 248, 245, 0.92);
        backdrop-filter: blur(12px);
        border-bottom: 1px solid var(--border);
        transition: all 0.3s ease;
    }

    .nav-logo {
        font-family: 'Cormorant Garamond', serif;
        font-size: 1.8rem;
        font-weight: 600;
        letter-spacing: 0.08em;
        color: var(--black);
        text-decoration: none;
    }

    .nav-logo span { color: var(--gold); }

    .nav-links {
        display: flex; gap: 2.5rem; list-style: none;
    }

    .nav-links a {
        font-size: 0.72rem;
        letter-spacing: 0.18em;
        text-transform: uppercase;
        text-decoration: none;
        color: var(--mid-gray);
        transition: color 0.3s;
        position: relative;
    }

    .nav-links a::after {
        content: '';
        position: absolute; bottom: -4px; left: 0; right: 0;
        height: 1px; background: var(--gold);
        transform: scaleX(0);
        transition: transform 0.3s ease;
    }

    .nav-links a:hover { color: var(--black); }
    .nav-links a:hover::after { transform: scaleX(1); }

    .nav-icons { display: flex; gap: 1.4rem; align-items: center; }

    .nav-icons button {
        background: none; border: none; cursor: pointer;
        color: var(--mid-gray); font-size: 1.1rem;
        transition: color 0.3s; padding: 0;
    }

    .nav-icons button:hover { color: var(--gold); }

    .cart-btn {
        background: var(--gold) !important;
        color: var(--white) !important;
        padding: 0.5rem 1.2rem !important;
        font-size: 0.68rem !important;
        letter-spacing: 0.15em;
        text-transform: uppercase;
        font-family: 'Montserrat', sans-serif !important;
        font-weight: 500;
        transition: background 0.3s !important;
    }
    .cart-btn:hover { background: var(--black) !important; }

    /* ─── HERO ─── */
    #hero {
        height: 100vh;
        display: grid;
        grid-template-columns: 1fr 1fr;
        margin-top: 0;
        overflow: hidden;
    }

    .hero-left {
        background: var(--dark-gray);
        display: flex; flex-direction: column;
        justify-content: center; padding: 8rem 5rem;
        position: relative; overflow: hidden;
    }

    .hero-left::before {
        content: '';
        position: absolute; top: -50%; left: -50%;
        width: 200%; height: 200%;
        background: radial-gradient(circle at 30% 60%, rgba(201,168,76,0.12) 0%, transparent 60%);
        pointer-events: none;
    }

    .hero-tag {
        font-size: 0.65rem; letter-spacing: 0.25em; text-transform: uppercase;
        color: var(--gold); margin-bottom: 2rem;
        display: flex; align-items: center; gap: 1rem;
    }

    .hero-tag::before {
        content: ''; display: block;
        width: 40px; height: 1px; background: var(--gold);
    }

    .hero-title {
        font-family: 'Cormorant Garamond', serif;
        font-size: clamp(3rem, 5vw, 5.5rem);
        font-weight: 300;
        line-height: 1.08;
        color: var(--white);
        margin-bottom: 2rem;
    }

    .hero-title em {
        font-style: italic; color: var(--gold-light);
    }

    .hero-sub {
        font-size: 0.78rem; letter-spacing: 0.08em; line-height: 1.9;
        color: rgba(250,248,245,0.55); max-width: 360px;
        margin-bottom: 3rem;
    }

    .btn-primary {
        display: inline-block;
        padding: 1rem 2.5rem;
        background: var(--gold);
        color: var(--white);
        text-decoration: none;
        font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
        font-weight: 500;
        transition: all 0.3s ease;
        position: relative; overflow: hidden;
    }

    .btn-primary::before {
        content: '';
        position: absolute; inset: 0;
        background: var(--white);
        transform: translateX(-100%);
        transition: transform 0.3s ease;
    }

    .btn-primary:hover { color: var(--black); }
    .btn-primary:hover::before { transform: translateX(0); }
    .btn-primary span { position: relative; z-index: 1; }

    .btn-outline {
        display: inline-block;
        padding: 0.9rem 2.2rem;
        border: 1px solid var(--border);
        color: var(--mid-gray);
        text-decoration: none;
        font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
        transition: all 0.3s ease;
        margin-left: 1rem;
    }

    .btn-outline:hover {
        border-color: var(--gold);
        color: var(--gold);
    }

    .hero-right {
        position: relative; overflow: hidden;
        background: linear-gradient(135deg, #e8e0d0 0%, #d4c9b0 100%);
    }

    .hero-img-placeholder {
        width: 100%; height: 100%;
        display: flex; flex-direction: column;
        align-items: center; justify-content: center;
        gap: 1rem;
        background:
            linear-gradient(135deg, rgba(201,168,76,0.08) 0%, transparent 50%),
            repeating-linear-gradient(45deg, transparent, transparent 30px, rgba(201,168,76,0.04) 30px, rgba(201,168,76,0.04) 31px);
    }

    .hero-visual-icon { font-size: 5rem; opacity: 0.4; }

    .hero-visual-text {
        font-family: 'Cormorant Garamond', serif;
        font-size: 1rem; letter-spacing: 0.3em;
        text-transform: uppercase; color: var(--mid-gray);
        opacity: 0.6;
    }

    .hero-badge {
        position: absolute; bottom: 3rem; right: 3rem;
        width: 90px; height: 90px;
        border: 1px solid var(--gold);
        border-radius: 50%;
        display: flex; align-items: center; justify-content: center;
        font-family: 'Cormorant Garamond', serif;
        font-size: 0.65rem; letter-spacing: 0.12em; text-align: center;
        color: var(--gold); line-height: 1.5;
        animation: rotateBadge 12s linear infinite;
    }

    @keyframes rotateBadge {
        from { transform: rotate(0deg); }
        to { transform: rotate(360deg); }
    }

    /* ─── CATEGORY STRIP ─── */
    .categories-strip {
        display: flex;
        border-top: 1px solid var(--border);
        border-bottom: 1px solid var(--border);
    }

    .cat-item {
        flex: 1;
        padding: 2rem 1.5rem;
        text-align: center;
        border-right: 1px solid var(--border);
        cursor: pointer;
        transition: background 0.3s;
        text-decoration: none;
        display: flex; flex-direction: column; align-items: center; gap: 0.6rem;
    }

    .cat-item:last-child { border-right: none; }
