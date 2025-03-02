<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nebula - School Society</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #121212;
            --secondary-color: #5b78a7;
            --accent-color: #8e44ad;
            --accent-color-2: #3498db;
            --text-light: #f8f9fa;
            --text-dark: #343a40;
            --bg-dark: #0a0a0a;
            --bg-light: #f5f5f7;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            line-height: 1.6;
            color: var(--text-light);
            background-color: var(--bg-dark);
            transition: var(--transition);
            overflow-x: hidden;
        }

        body.light-mode {
            color: var(--text-dark);
            background-color: var(--bg-light);
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative;
            z-index: 2;
        }

        /* Header Styles */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background-color: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
            transition: var(--transition);
        }

        body.light-mode header {
            background-color: rgba(245, 245, 247, 0.8);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }

        .logo {
            display: flex;
            align-items: center;
            text-decoration: none;
        }

        .logo h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            font-weight: 700;
            background: linear-gradient(120deg, #8e44ad, #3498db);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 10px rgba(142, 68, 173, 0.5);
            margin-left: 10px;
            letter-spacing: 2px;
            position: relative;
        }

        .logo h1::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 100%;
            height: 1px;
            background: linear-gradient(90deg, transparent, #8e44ad, #3498db, transparent);
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
            background: linear-gradient(135deg, #8e44ad, #3498db);
            color: white;
            font-size: 18px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 0 15px rgba(142, 68, 173, 0.7);
        }

        .logo-icon::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(transparent, rgba(255, 255, 255, 0.3), transparent 30%);
            animation: rotate 4s linear infinite;
        }

        @keyframes rotate {
            100% {
                transform: rotate(360deg);
            }
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 30px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-light);
            font-weight: 500;
            font-size: 16px;
            transition: var(--transition);
            position: relative;
            padding: 5px 0;
        }

        body.light-mode .nav-links a {
            color: var(--text-dark);
        }

        .nav-links a:hover {
            color: var(--accent-color);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--accent-color), var(--accent-color-2));
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .toggle-container {
            display: flex;
            align-items: center;
        }

        .theme-toggle {
            background: none;
            border: none;
            cursor: pointer;
            margin-left: 20px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: rgba(255, 255, 255, 0.1);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        body.light-mode .theme-toggle {
            background-color: rgba(0, 0, 0, 0.1);
        }

        .theme-toggle:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }

        body.light-mode .theme-toggle:hover {
            background-color: rgba(0, 0, 0, 0.2);
        }

        .hamburger {
            display: none;
            background: none;
            border: none;
            cursor: pointer;
            width: 30px;
            height: 20px;
            position: relative;
            z-index: 1001;
        }

        .hamburger span {
            display: block;
            width: 100%;
            height: 2px;
            background-color: var(--text-light);
            position: absolute;
            left: 0;
            transition: var(--transition);
        }

        body.light-mode .hamburger span {
            background-color: var(--text-dark);
        }

        .hamburger span:nth-child(1) {
            top: 0;
        }

        .hamburger span:nth-child(2) {
            top: 50%;
            transform: translateY(-50%);
        }

        .hamburger span:nth-child(3) {
            bottom: 0;
        }

        /* Background Effects */
        .space-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            overflow: hidden;
            background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);
        }

        .stars {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle var(--duration) infinite ease-in-out;
        }

        @keyframes twinkle {
            0%, 100% {
                opacity: 0.2;
                transform: scale(0.8);
            }
            50% {
                opacity: 1;
                transform: scale(1);
            }
        }

        .nebula {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 30% 50%, rgba(142, 68, 173, 0.3) 0%, transparent 40%),
                radial-gradient(circle at 70% 60%, rgba(52, 152, 219, 0.3) 0%, transparent 40%),
                radial-gradient(circle at 50% 30%, rgba(231, 76, 60, 0.2) 0%, transparent 50%);
            filter: blur(30px);
            mix-blend-mode: screen;
            opacity: 0.7;
            animation: nebula-move 60s infinite alternate ease-in-out;
        }

        @keyframes nebula-move {
            0% {
                transform: scale(1) translate(0, 0);
            }
            50% {
                transform: scale(1.1) translate(-2%, -2%);
            }
            100% {
                transform: scale(1) translate(2%, 2%);
            }
        }

        .cosmic-dust {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
            opacity: 0.05;
            mix-blend-mode: overlay;
        }

        /* Hero Section */
        .hero {
            position: relative;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            margin-bottom: 50px;
        }

        .hero-content {
            text-align: center;
            max-width: 800px;
            padding: 0 20px;
            z-index: 1;
            animation: fadeIn 1.5s ease-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            font-weight: 700;
            background: linear-gradient(120deg, #8e44ad, #3498db);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(142, 68, 173, 0.5);
            position: relative;
            display: inline-block;
        }

        .hero-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, #8e44ad, #3498db, transparent);
        }

        .hero-subtitle {
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.9);
            margin-bottom: 30px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            text-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }

        body.light-mode .hero-subtitle {
            color: rgba(0, 0, 0, 0.8);
            text-shadow: none;
        }

        .hero-btn {
            display: inline-block;
            padding: 12px 30px;
            background: linear-gradient(135deg, var(--accent-color), var(--accent-color-2));
            color: white;
            text-decoration: none;
            border-radius: 30px;
            font-weight: 600;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: var(--transition);
            border: 2px solid transparent;
            box-shadow: 0 0 20px rgba(142, 68, 173, 0.5);
            position: relative;
            overflow: hidden;
            z-index: 1;
        }

        .hero-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: var(--transition);
            z-index: -1;
        }

        .hero-btn:hover::before {
            left: 100%;
            transition: 0.7s;
        }

        .hero-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 30px rgba(142, 68, 173, 0.7);
        }

        /* About Section */
        .about {
            padding: 100px 0;
            position: relative;
            overflow: hidden;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .section-title h2 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(120deg, #8e44ad, #3498db);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
            text-shadow: 0 0 15px rgba(142, 68, 173, 0.5);
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 70px;
            height: 3px;
            background: linear-gradient(to right, var(--accent-color), var(--accent-color-2));
            border-radius: 3px;
        }

        .about-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 40px;
        }

        .about-text {
            flex: 1;
            min-width: 300px;
        }

        .about-text p {
            margin-bottom: 20px;
            font-size: 1.05rem;
            line-height: 1.8;
            color: rgba(255, 255, 255, 0.85);
            transition: var(--transition);
        }

        body.light-mode .about-text p {
            color: var(--text-dark);
        }

        .about-image {
            flex: 1;
            min-width: 300px;
            position: relative;
        }

        .about-card {
            width: 100%;
            aspect-ratio: 4/3;
            background-color: rgba(30, 30, 30, 0.5);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 0 30px rgba(142, 68, 173, 0.3);
            transition: var(--transition);
            transform: perspective(1000px) rotateY(0deg) rotateX(0deg);
            position: relative;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        body.light-mode .about-card {
            background-color: rgba(255, 255, 255, 0.7);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .about-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
            opacity: 0.8;
        }

        .about-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, rgba(45, 62, 80, 0.1), rgba(142, 68, 173, 0.3));
            z-index: 1;
        }

        /* Contact Section */
        .contact {
            padding: 100px 0;
            background-color: rgba(18, 18, 18, 0.5);
            position: relative;
            transition: var(--transition);
            backdrop-filter: blur(10px);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        body.light-mode .contact {
            background-color: rgba(245, 245, 247, 0.5);
            border-top: 1px solid rgba(0, 0, 0, 0.05);
        }

        .contact-info {
            max-width: 700px;
            margin: 0 auto;
            text-align: center;
        }

        .contact-info h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8rem;
            margin-bottom: 25px;
            background: linear-gradient(120deg, #8e44ad, #3498db);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
        }

        .contact-items {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
        }

        .contact-item {
            flex: 1;
            min-width: 200px;
            max-width: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 30px 20px;
            background: rgba(30, 30, 30, 0.5);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: var(--transition);
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        }

        body.light-mode .contact-item {
            background: rgba(255, 255, 255, 0.7);
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .contact-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(142, 68, 173, 0.2);
        }

        .contact-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent-color), var(--accent-color-2));
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
            box-shadow: 0 0 20px rgba(142, 68, 173, 0.4);
        }

        .contact-icon i {
            color: white;
            font-size: 24px;
        }

        .contact-text {
            text-align: center;
        }

        .contact-text h4 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--text-light);
            transition: var(--transition);
        }

        body.light-mode .contact-text h4 {
            color: var(--text-dark);
        }

        .contact-text p, .contact-text a {
            color: rgba(255, 255, 255, 0.7);
            transition: var(--transition);
            text-decoration: none;
        }

        body.light-mode .contact-text p, 
        body.light-mode .contact-text a {
            color: rgba(0, 0, 0, 0.7);
        }

        .contact-text a:hover {
            color: var(--accent-color);
        }

        /* Footer */
        footer {
            background-color: rgba(10, 10, 10, 0.9);
            color: white;
            padding: 30px 0;
            text-align: center;
            transition: var(--transition);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        body.light-mode footer {
            background-color: rgba(245, 245, 247, 0.9);
            color: var(--text-dark);
            border-top: 1px solid rgba(0, 0, 0, 0.05);
        }

        .footer-text {
            margin-bottom: 15px;
            color: rgba(255, 255, 255, 0.7);
        }

        body.light-mode .footer-text {
            color: rgba(0, 0, 0, 0.7);
        }

        .social-links {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 10px;
            transition: var(--transition);
            color: white;
            text-decoration: none;
            position: relative;
            overflow: hidden;
        }

        body.light-mode .social-link {
            background-color: rgba(0, 0, 0, 0.1);
            color: var(--text-dark);
        }

        .social-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: var(--transition);
        }

        .social-link:hover::before {
            left: 100%;
            transition: 0.7s;
        }

        .social-link:hover {
            background: linear-gradient(135deg, var(--accent-color), var(--accent-color-2));
            transform: translateY(-3px);
        }

        .copyright {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Responsive Styles */
        @media (max-width: 992px) {
            .hero-title {
                font-size: 3rem;
            }
        }

        @media (max-width: 768px) {
            .header-container {
                padding: 10px 0;
            }

            .hamburger {
                display: block;
            }

            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 250px;
                height: 100vh;
                background-color: rgba(10, 10, 10, 0.95);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: var(--transition);
                z-index: 1000;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
                backdrop-filter: blur(10px);
            }

            body.light-mode .nav-links {
                background-color: rgba(245, 245, 247, 0.95);
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links li {
                margin: 15px 0;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .hero-subtitle {
                font-size: 1rem;
            }

            .section-title h2 {
                font-size: 2rem;
            }

            .contact-items {
                flex-direction: column;
                align-items: center;
            }

            .contact-item {
                width: 100%;
                max-width: 100%;
            }
        }

        @media (max-width: 576px) {
            .hero-title {
                font-size: 2rem;
            }

            .about-card {
                margin-top: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Space Background -->
    <div class="space-background">
        <div class="stars" id="stars"></div>
        <div class="nebula"></div>
        <div class="cosmic-dust"></div>
    </div>

    <!-- Header -->
    <header>
        <div class="container header-container">
            <a href="#" class="logo">
                <div class="logo-icon">N</div>
                <h1>NEBULA</h1>
            </a>
            <button class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </button>
            <ul class="nav-links" id="nav-links">
                <li><a href="#" class="active">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
                    </svg>
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="moon-icon">
                        <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
                    </svg>
                </button>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container">
            <div class="hero-content">
                <h1 class="hero-title">Welcome to Nebula Society</h1>
                <p class="hero-subtitle">Exploring new horizons of knowledge and creativity at our school</p>
                <a href="#about" class="hero-btn">Learn More</a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="container">
            <div class="section-title">
                <h2>About Us</h2>
            </div>
            <div class="about-content">
                <div class="about-text">
                    <p>Nebula is a dynamic school society dedicated to fostering creativity, innovation, and academic excellence among students. Founded with the vision to create a collaborative space for learning and growth, our society brings together passionate individuals who are eager to explore new ideas.</p>
                    <p>Our activities range from interactive workshops and engaging discussions to exciting projects that challenge our members to think outside the box. At Nebula, we believe in the power of collective intelligence and the importance of creating an environment where every voice is heard and valued.</p>
                    <p>Join us in our journey of discovery and become part of a community that celebrates curiosity, embraces diversity, and strives for excellence in everything we do.</p>
                </div>
                <div class="about-image">
                    <div class="about-card" id="about-card">
                        <img src="https://picsum.photos/600/400?random=1" alt="Nebula Society Members">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="container">
            <div class="section-title">
                <h2>Contact Us</h2>
            </div>
            <div class="contact-info">
                <h3>Get In Touch</h3>
                <p>Have questions about Nebula Society or interested in joining us? Reach out through any of the following channels.</p>
                
                <div class="contact-items">
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i>
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                    <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                                </svg>
                            </i>
                        </div>
                        <div class="contact-text">
                            <h4>Phone</h4>
                            <p>(123) 456-7890</p>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i>
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                    <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                                    <polyline points="22,6 12,13 2,6"></polyline>
                                </svg>
                            </i>
                        </div>
                        <div class="contact-text">
                            <h4>Email</h4>
                            <a href="mailto:info@nebulasociety.edu">info@nebulasociety.edu</a>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <div class="contact-icon">
                            <i>
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                    <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
                                    <circle cx="12" cy="10" r="3"></circle>
                                </svg>
                            </i>
                        </div>
                        <div class="contact-text">
                            <h4>Location</h4>
                            <p>123 School Street, Academic City, AC 12345</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-text">
                <p>Connect with us on social media</p>
            </div>
            <div class="social-links">
                <a href="#" class="social-link">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path>
                    </svg>
                </a>
                <a href="#" class="social-link">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
                        <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                        <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
                    </svg>
                </a>
                <a href="#" class="social-link">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path>
                    </svg>
                </a>
            </div>
            <div class="copyright">
                <p>&copy; 2023 Nebula Society. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Create stars in the background
        function createStars() {
            const stars = document.getElementById('stars');
            const starsCount = 300; // Increased star count
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                
                // Random positioning
                const x = Math.random() * 100;
                const y = Math.random() * 100;
                
                // Random size
                const size = Math.random() * 3; // Larger stars
                
                // Random duration for twinkling
                const duration = 3 + Math.random() * 7;
                
                star.style.left = `${x}%`;
                star.style.top = `${y}%`;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                star.style.setProperty('--duration', `${duration}s`);
                
                // Add a subtle glow to some stars
                if (Math.random() > 0.7) {
                    star.style.boxShadow = `0 0 ${3 + Math.random() * 5}px rgba(255, 255, 255, 0.8)`;
                }
                
                stars.appendChild(star);
            }
        }

        // About card 3D effect
        function initAboutCard() {
            const card = document.getElementById('about-card');
            
            if (card) {
                document.addEventListener('mousemove', (e) => {
                    if (window.innerWidth > 768) {
                        const cardRect = card.getBoundingClientRect();
                        const cardCenterX = cardRect.left + cardRect.width / 2;
                        const cardCenterY = cardRect.top + cardRect.height / 2;
                        
                        const angleY = (e.clientX - cardCenterX) / 30;
                        const angleX = (cardCenterY - e.clientY) / 30;
                        
                        card.style.transform = `perspective(1000px) rotateY(${angleY}deg) rotateX(${angleX}deg)`;
                    }
                });
                
                // Reset transform when mouse leaves viewport
                document.addEventListener('mouseleave', () => {
                    card.style.transform = 'perspective(1000px) rotateY(0deg) rotateX(0deg)';
                });
            }
        }

        // Toggle theme mode
        function initThemeToggle() {
            const themeToggle = document.getElementById('theme-toggle');
            const sunIcon = document.querySelector('.sun-icon');
            const moonIcon = document.querySelector('.moon-icon');
            
            themeToggle.addEventListener('click', () => {
                document.body.classList.toggle('light-mode');
                
                // Update icons
                if (document.body.classList.contains('light-mode')) {
                    sunIcon.style.display = 'block';
                    moonIcon.style.display = 'none';
                    localStorage.setItem('theme', 'light');
                } else {
                    sunIcon.style.display = 'none';
                    moonIcon.style.display = 'block';
                    localStorage.setItem('theme', 'dark');
                }
            });
            
            // Check for saved theme preference
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme === 'light') {
                document.body.classList.add('light-mode');
                sunIcon.style.display = 'block';
                moonIcon.style.display = 'none';
            }
        }

        // Mobile navigation
        function initMobileNav() {
            const hamburger = document.getElementById('hamburger');
            const navLinks = document.getElementById('nav-links');
            
            hamburger.addEventListener('click', () => {
                navLinks.classList.toggle('active');
                document.body.classList.toggle('no-scroll');
            });
            
            // Close mobile nav when clicking on a link
            const links = document.querySelectorAll('.nav-links a');
            links.forEach(link => {
                link.addEventListener('click', () => {
                    navLinks.classList.remove('active');
                    document.body.classList.remove('no-scroll');
                });
            });
        }

        // Initialize everything when the DOM is loaded
        document.addEventListener('DOMContentLoaded', () => {
            createStars();
            initAboutCard();
            initThemeToggle();
            initMobileNav();
            
            // Smooth scrolling for anchor links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const targetId = this.getAttribute('href');
                    if (targetId === '#') return;
                    
                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        window.scrollTo({
                            top: targetElement.offsetTop - 70,
                            behavior: 'smooth'
                        });
                    }
                });
            });
            
            // Add parallax effect to nebula
            window.addEventListener('scroll', () => {
                const scrollY = window.scrollY;
                const nebula = document.querySelector('.nebula');
                nebula.style.transform = `translateY(${scrollY * 0.05}px)`;
            });
        });
    </script>
</body>
</html>
