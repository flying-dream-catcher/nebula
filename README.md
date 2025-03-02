<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nebula Student Union</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Orbitron:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-bg: #0f0f1a;
            --secondary-bg: #151528;
            --card-bg: #1a1a2e;
            --accent-color: #6649d8;
            --accent-glow: rgba(102, 73, 216, 0.4);
            --text-primary: #e6e6ff;
            --text-secondary: #b8b8d4;
            --nebula-purple: #9d4edd;
            --nebula-blue: #5390d9;
            --nebula-pink: #ff5e78;
            --nebula-teal: #48bfe3;
            --neumorphic-shadow1: rgba(0, 0, 0, 0.7);
            --neumorphic-shadow2: rgba(30, 30, 60, 0.2);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--primary-bg);
            color: var(--text-primary);
            overflow-x: hidden;
            position: relative;
            min-height: 100vh;
        }

        /* Star Background Animation */
        .stars-container {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
            overflow: hidden;
        }

        .star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            opacity: 0;
            animation: twinkle var(--duration) linear var(--delay) infinite;
        }

        @keyframes twinkle {
            0% { opacity: 0; }
            50% { opacity: var(--opacity); }
            100% { opacity: 0; }
        }

        /* Nebula Gradient Background */
        .nebula-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 70% 20%, rgba(30, 27, 205, 0.516), transparent 40%),
                        radial-gradient(circle at 20% 80%, rgba(61, 54, 141, 0.427), transparent 40%),
                        radial-gradient(circle at 50% 50%, rgba(222, 222, 222, 0.342), transparent 60%);
            z-index: -2;
            pointer-events: none;
        }

        /* Header Styles */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            padding: 1.5rem;
            background: rgba(5, 5, 8, 0.8);
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }

        header.scrolled {
            padding: 1rem 1.5rem;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1400px;
            margin: 0 auto;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .logo-text {
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            font-size: 1.8rem;
            background: linear-gradient(to right, var(--nebula-purple), var(--nebula-blue));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 2px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links li a {
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 500;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            position: relative;
            padding: 0.3rem 0;
        }

        .nav-links li a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(to right, var(--nebula-purple), var(--nebula-blue));
            transition: width 0.3s ease;
        }

        .nav-links li a:hover {
            color: var(--nebula-purple);
        }

        .nav-links li a:hover::after {
            width: 100%;
        }

        .hamburger {
            display: none;
            cursor: pointer;
            background: none;
            border: none;
            color: var(--text-primary);
            font-size: 1.5rem;
        }

        /* Main Content Styles */
        main {
            padding-top: 100px;
        }

        section {
            padding: 6rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            text-align: center;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(to right, var(--nebula-purple), var(--nebula-blue));
            border-radius: 3px;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            padding: 0 2rem;
        }

        .hero-content {
            text-align: center;
            max-width: 900px;
            z-index: 2;
        }

        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 4rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(to right, var(--nebula-purple), var(--nebula-blue), var(--nebula-teal));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            line-height: 1.2;
            animation: fadeInUp 1s ease-out;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            color: var(--text-secondary);
            margin-bottom: 2.5rem;
            animation: fadeInUp 1s ease-out 0.2s backwards;
        }

        .hero-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            animation: fadeInUp 1s ease-out 0.4s backwards;
        }

        .btn {
            padding: 0.8rem 2rem;
            border-radius: 30px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            border: none;
            box-shadow: 0 5px 15px rgba(102, 73, 216, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(102, 73, 216, 0.6);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-primary);
            border: 2px solid var(--nebula-purple);
        }

        .btn-secondary:hover {
            background: rgba(157, 78, 221, 0.1);
            transform: translateY(-3px);
        }

        .scroll-down {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
            color: var(--text-primary);
            font-size: 2rem;
            cursor: pointer;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0) translateX(-50%); }
            40% { transform: translateY(-20px) translateX(-50%); }
            60% { transform: translateY(-10px) translateX(-50%); }
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .about-text p {
            color: var(--text-secondary);
            line-height: 1.8;
            font-size: 1.1rem;
        }

        .about-image {
            position: relative;
        }

        .about-card {
            width: 100%;
            aspect-ratio: 4/3;
            border-radius: 20px;
            background: var(--card-bg);
            box-shadow: 12px 12px 24px var(--neumorphic-shadow1), 
                        -12px -12px 24px var(--neumorphic-shadow2);
            overflow: hidden;
            position: relative;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .about-card:hover {
            transform: translateY(-10px);
            box-shadow: 15px 15px 30px var(--neumorphic-shadow1), 
                        -15px -15px 30px var(--neumorphic-shadow2);
        }

        .about-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.8;
            transition: opacity 0.3s ease;
        }

        .about-card:hover img {
            opacity: 1;
        }

        .about-card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, transparent, rgba(15, 15, 26, 0.7));
            pointer-events: none;
        }

        .about-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            margin-top: 4rem;
        }

        .stat-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            box-shadow: 8px 8px 16px var(--neumorphic-shadow1), 
                        -8px -8px 16px var(--neumorphic-shadow2);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-10px);
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 1.1rem;
        }

        /* Events Section */
        .events-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 2.5rem;
        }

        .event-card {
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 10px 10px 20px var(--neumorphic-shadow1), 
                        -10px -10px 20px var(--neumorphic-shadow2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
        }

        .event-card:hover {
            transform: translateY(-10px);
            box-shadow: 15px 15px 30px var(--neumorphic-shadow1), 
                        -15px -15px 30px var(--neumorphic-shadow2);
        }

        .event-image {
            width: 100%;
            height: 200px;
            overflow: hidden;
        }

        .event-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .event-card:hover .event-image img {
            transform: scale(1.1);
        }

        .event-content {
            padding: 1.5rem;
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .event-date {
            display: inline-block;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            padding: 0.4rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            align-self: flex-start;
        }

        .event-title {
            font-size: 1.4rem;
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .event-description {
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
            line-height: 1.6;
            flex: 1;
        }

        .event-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding-top: 1rem;
        }

        .event-location {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .event-btn {
            font-size: 0.9rem;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            background: transparent;
            color: var(--nebula-purple);
            border: 1px solid var(--nebula-purple);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .event-btn:hover {
            background: var(--nebula-purple);
            color: white;
        }

        /* Team Section */
        .team-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 3rem;
        }

        .team-card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            box-shadow: 8px 8px 16px var(--neumorphic-shadow1), 
                        -8px -8px 16px var(--neumorphic-shadow2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .team-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(157, 78, 221, 0.1), transparent);
            transform: rotate(45deg);
            transition: transform 0.6s ease;
            z-index: 0;
        }

        .team-card:hover {
            transform: translateY(-10px);
            box-shadow: 12px 12px 24px var(--neumorphic-shadow1), 
                        -12px -12px 24px var(--neumorphic-shadow2);
        }

        .team-card:hover::before {
            transform: rotate(45deg) translate(50%, 50%);
        }

        .team-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            margin: 0 auto 1.5rem;
            overflow: hidden;
            border: 3px solid transparent;
            background: linear-gradient(var(--card-bg), var(--card-bg)) padding-box,
                        linear-gradient(to right, var(--nebula-purple), var(--nebula-blue)) border-box;
            position: relative;
            z-index: 1;
        }

        .team-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .team-name {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            position: relative;
            z-index: 1;
        }

        .team-role {
            color: var(--nebula-purple);
            font-size: 1rem;
            margin-bottom: 1.5rem;
            position: relative;
            z-index: 1;
        }

        .team-bio {
            color: var(--text-secondary);
            font-size: 0.95rem;
            line-height: 1.6;
            margin-bottom: 1.5rem;
            position: relative;
            z-index: 1;
        }

        .team-social {
            display: flex;
            justify-content: center;
            gap: 1rem;
            position: relative;
            z-index: 1;
        }

        .team-social a {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--secondary-bg);
            color: var(--text-primary);
            transition: all 0.3s ease;
            box-shadow: 4px 4px 8px var(--neumorphic-shadow1), 
                        -4px -4px 8px var(--neumorphic-shadow2);
        }

        .team-social a:hover {
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            transform: translateY(-3px);
        }

        /* Gallery Section */
       

        /* Contact Section */
        .contact-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }

        .contact-info h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
        }

        .contact-info p {
            color: var(--text-secondary);
            line-height: 1.8;
            font-size: 1.1rem;
            margin-bottom: 2rem;
        }

        .contact-method {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .contact-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--card-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            color: var(--nebula-purple);
            box-shadow: 5px 5px 10px var(--neumorphic-shadow1), 
                        -5px -5px 10px var(--neumorphic-shadow2);
        }

        .contact-details {
            flex: 1;
        }

        .contact-details h4 {
            font-size: 1.1rem;
            margin-bottom: 0.3rem;
        }

        .contact-details p, .contact-details a {
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .contact-details a:hover {
            color: var(--nebula-purple);
        }

        .contact-social {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }

        .contact-social a {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: var(--card-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-primary);
            font-size: 1.2rem;
            transition: all 0.3s ease;
            box-shadow: 5px 5px 10px var(--neumorphic-shadow1), 
                        -5px -5px 10px var(--neumorphic-shadow2);
        }

        .contact-social a:hover {
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            transform: translateY(-5px);
        }

        .contact-form {
            background: var(--card-bg);
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 10px 10px 20px var(--neumorphic-shadow1), 
                        -10px -10px 20px var(--neumorphic-shadow2);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.8rem;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 1rem;
            border-radius: 10px;
            background: var(--secondary-bg);
            border: none;
            color: var(--text-primary);
            font-size: 1rem;
            box-shadow: inset 4px 4px 8px var(--neumorphic-shadow1), 
                        inset -4px -4px 8px var(--neumorphic-shadow2);
            transition: all 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            box-shadow: inset 6px 6px 12px var(--neumorphic-shadow1), 
                        inset -6px -6px 12px var(--neumorphic-shadow2);
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        .submit-btn {
            width: 100%;
            padding: 1rem;
            border: none;
            border-radius: 10px;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 5px 5px 10px var(--neumorphic-shadow1);
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 8px 8px 16px var(--neumorphic-shadow1);
        }

        /* Footer */
        footer {
            background: var(--secondary-bg);
            padding: 4rem 2rem 2rem;
            position: relative;
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 3rem;
        }

        .footer-col h4 {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
            position: relative;
            display: inline-block;
            padding-bottom: 0.5rem;
        }

        .footer-col h4::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50px;
            height: 2px;
            background: linear-gradient(to right, var(--nebula-purple), var(--nebula-blue));
        }

        .footer-col p {
            color: var(--text-secondary);
            line-height: 1.6;
            margin-bottom: 1.5rem;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.3s ease;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .footer-links a:hover {
            color: var(--nebula-purple);
            transform: translateX(5px);
        }

        .footer-newsletter p {
            margin-bottom: 1rem;
        }

        .newsletter-form {
            display: flex;
            gap: 0.5rem;
        }

        .newsletter-input {
            flex: 1;
            padding: 0.8rem;
            border-radius: 8px;
            background: var(--primary-bg);
            border: none;
            color: var(--text-primary);
            box-shadow: inset 3px 3px 6px var(--neumorphic-shadow1), 
                        inset -3px -3px 6px var(--neumorphic-shadow2);
        }

        .newsletter-input:focus {
            outline: none;
        }

        .newsletter-btn {
            padding: 0.8rem 1rem;
            border-radius: 8px;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .newsletter-btn:hover {
            transform: translateY(-3px);
            box-shadow: 3px 3px 6px var(--neumorphic-shadow1);
        }

        .footer-bottom {
            max-width: 1400px;
            margin: 0 auto;
            padding-top: 2rem;
            margin-top: 3rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .footer-social {
            display: flex;
            gap: 1rem;
        }

        .footer-social a {
            color: var(--text-secondary);
            transition: color 0.3s ease;
            font-size: 1.2rem;
        }

        .footer-social a:hover {
            color: var(--nebula-purple);
        }

        /* Back to Top Button */
        .back-to-top {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--nebula-purple), var(--nebula-blue));
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            cursor: pointer;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            box-shadow: 5px 5px 10px var(--neumorphic-shadow1);
            z-index: 999;
        }

        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            transform: translateY(-5px);
            box-shadow: 8px 8px 16px var(--neumorphic-shadow1);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Responsive Styles */
        @media (max-width: 1200px) {
            .footer-content {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 992px) {
            .about-content,
            .contact-container {
                grid-template-columns: 1fr;
                gap: 3rem;
            }

            .about-image {
                order: -1;
            }

            .hero-title {
                font-size: 3rem;
            }

            .hero-subtitle {
                font-size: 1.3rem;
            }

            .section-title {
                font-size: 2.2rem;
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background: var(--secondary-bg);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: right 0.3s ease;
                z-index: 1001;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
            }

            .nav-links.active {
                right: 0;
            }

            .hamburger {
                display: block;
                z-index: 1002;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .hero-subtitle {
                font-size: 1.1rem;
            }

            .hero-buttons {
                flex-direction: column;
                gap: 1rem;
            }

            .btn {
                width: 100%;
                justify-content: center;
            }

            .events-container,
            .gallery-container {
                grid-template-columns: 1fr;
            }

            .about-stats {
                grid-template-columns: 1fr;
            }

            .team-container {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }

            .footer-content {
                grid-template-columns: 1fr;
            }

            .footer-bottom {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }
        }

        @media (max-width: 480px) {
            .hero-title {
                font-size: 2rem;
            }

            .section-title {
                font-size: 1.8rem;
            }

            .contact-form {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Stars Background -->
    <div class="stars-container" id="stars-container"></div>
    
    <!-- Nebula Background -->
    <div class="nebula-bg"></div>

    <!-- Header -->
    <header id="header">
        <nav>
            <a href="#" class="logo">
                <div class="logo-icon">
                    <i class="fas fa-galaxy"></i>
                </div>
                <div class="logo-text">NEBULA</div>
            </a>
            <ul class="nav-links" id="nav-links">
                <li><a href="#hero">首頁</a></li>
                <li><a href="#about">關於</a></li>
                <li><a href="#events">活動</a></li>
                <li><a href="#team">成員</a></li>
                <li><a href="#contact">聯係我們</a></li>
            </ul>
            <button class="hamburger" id="hamburger">
                <i class="fas fa-bars"></i>
            </button>
        </nav>
    </header>

    <!-- Main Content -->
    <main>
        <!-- Hero Section -->
        <section class="hero" id="hero">
            <div class="hero-content">
                <h1 class="hero-title">Wlecome to Nebula</h1>
                <p class="hero-subtitle">聖公會基孝中學25-26學生會 1 號候選内閣</p>
                <div class="hero-buttons">
                    <a href="#about" class="btn btn-primary">
                        <i class="fas fa-meteor"></i> 瞭解 Nebula
                    </a>
                    <a href="#events" class="btn btn-secondary">
                        <i class="fas fa-calendar-alt"></i> 來年活動
                    </a>
                </div>
            </div>
            <a href="#about" class="scroll-down">
                <i class="fas fa-chevron-down"></i>
            </a>
        </section>

        <!-- About Section -->
        <section id="about" class="about">
            <h2 class="section-title">關於 Nebula</h2>
            <div class="about-content">
                <div class="about-text fade-in">
                    <p>Nebula，意指星雲，象徵著孕育與創造的起點。在星雲中，氣體與塵埃逐漸聚集，最終大到足以形成光芒四射的恆星。這個名字承載著我們的期望——願學生會如同星雲一般，凝聚師生的力量，讓每一份力量、每一點光芒都能彙集成我們共同的校園願景，構築出一個充滿生機、和諧、溫暖的校園，讓每位同學都能在這片天地中閃耀出屬於自己的光芒。</p>
                    <p>Nebula會以歷代學生會作借鑒，正所謂「擇其善者而從之，其不善者而改之。」使同學可享有更優質，更無微不至，更非同凡響的服務</p>
                    <p>以學生為本，追求實事求是，保障學生利益，亦會設立意見箱，傾聽各位同學的意見，並為其發聲，成為我校與學生雙方溝通的橋樑，增強同學對我校的歸屬感。</p>
                </div>
                <div class="about-image fade-in">
                    <div class="about-card">
                        <img src="https://picsum.photos/id/1025/800/600" alt="Nebula Student Union">
                    </div>
                </div>
            </div>
            <div class="about-stats">
                <div class="stat-card fade-in">
                    <div class="stat-number">8</div>
                    <div class="stat-label">位精英</div>
                </div>
                <div class="stat-card fade-in">
                    <div class="stat-number">688 B+</div>
                    <div class="stat-label">腦細胞</div>
                </div>
                <div class="stat-card fade-in">
                    <div class="stat-number">15</div>
                    <div class="stat-label">來年活動</div>
                </div>
            </div>
        </section>

        <!-- Events Section -->
        <section id="events" class="events">
            <h2 class="section-title">來年活動</h2>
            <div class="events-container">
                <div class="event-card fade-in">
                    <div class="event-image">
                        <img src="https://picsum.photos/id/1071/600/400" alt="Leadership Summit">
                    </div>
                    <div class="event-content">
                        <span class="event-date">May 15, 2023</span>
                        <h3 class="event-title">Annual Leadership Summit</h3>
                        <p class="event-description">Join us for a day of inspiring talks, workshops, and networking opportunities with industry leaders and successful alumni.</p>
                        <div class="event-footer">
                            <div class="event-location">
                                <i class="fas fa-map-marker-alt"></i>
                                <span>Main Auditorium</span>
                            </div>
                          
                        </div>
                    </div>
                </div>
                
                <div class="event-card fade-in">
                    <div class="event-image">
                        <img src="https://picsum.photos/id/1070/600/400" alt="Tech Hackathon">
                    </div>
                    <div class="event-content">
                        <span class="event-date">June 2-4, 2023</span>
                        <h3 class="event-title">Cosmic Code Hackathon</h3>
                        <p class="event-description">A 48-hour coding marathon where teams compete to build innovative solutions for real-world problems. Great prizes to be won!</p>
                        <div class="event-footer">
                            <div class="event-location">
                                <i class="fas fa-map-marker-alt"></i>
                                <span>Innovation Hub</span>
                            </div>
                          
                        </div>
                    </div>
                </div>
                
                <div class="event-card fade-in">
                    <div class="event-image">
                        <img src="https://picsum.photos/id/1082/600/400" alt="Cultural Festival">
                    </div>
                    <div class="event-content">
                        <span class="event-date">July 10, 2023</span>
                        <h3 class="event-title">Stellar Cultural Festival</h3>
                        <p class="event-description">Celebrate diversity through music, dance, art, and culinary experiences from around the world. A day of cultural exchange and fun.</p>
                        <div class="event-footer">
                            <div class="event-location">
                                <i class="fas fa-map-marker-alt"></i>
                                <span>Campus Plaza</span>
                            </div>
                          
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Team Section -->
        <section id="team" class="team">
            <h2 class="section-title">團隊精英</h2>
            <div class="team-container">
                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1027/300/300" alt="Sarah Johnson">
                    </div>
                    <h3 class="team-name">丘莉欣</h3>
                    <div class="team-role">主席</div>
                    <p class="team-bio">Astrophysics major with a passion for leadership and community building. Sarah has been instrumental in expanding Nebula's reach across campus.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>
                
                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1012/300/300" alt="David Chen">
                    </div>
                    <h3 class="team-name">李逸塵</h3>
                    <div class="team-role">外務副主席</div>
                    <p class="team-bio">Computer Science enthusiast and hackathon champion. David leads our tech initiatives and mentorship programs for first-year students.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>
                
                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1000/300/300" alt="Aisha Patel">
                    </div>
                    <h3 class="team-name">黃俊天</h3>
                    <div class="team-role">内務副主席</div>
                    <p class="team-bio">Business Administration major with exceptional organizational skills. Aisha ensures all our events run smoothly and create memorable experiences.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>
                
                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1074/300/300" alt="Miguel Rodriguez">
                    </div>
                    <h3 class="team-name">陳敏琳</h3>
                    <div class="team-role">秘書</div>
                    <p class="team-bio">Economics major with a keen eye for financial management. Miguel ensures our resources are allocated effectively to maximize impact.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>

                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1000/300/300" alt="Aisha Patel">
                    </div>
                    <h3 class="team-name">何索妮</h3>
                    <div class="team-role">財政</div>
                    <p class="team-bio">Business Administration major with exceptional organizational skills. Aisha ensures all our events run smoothly and create memorable experiences.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>

                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1000/300/300" alt="Aisha Patel">
                    </div>
                    <h3 class="team-name">黎子僖</h3>
                    <div class="team-role">宣傳</div>
                    <p class="team-bio">Business Administration major with exceptional organizational skills. Aisha ensures all our events run smoothly and create memorable experiences.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>

                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1000/300/300" alt="Aisha Patel">
                    </div>
                    <h3 class="team-name">余綽霖</h3>
                    <div class="team-role">康樂</div>
                    <p class="team-bio">Business Administration major with exceptional organizational skills. Aisha ensures all our events run smoothly and create memorable experiences.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>

                <div class="team-card fade-in">
                    <div class="team-avatar">
                        <img src="https://picsum.photos/id/1000/300/300" alt="Aisha Patel">
                    </div>
                    <h3 class="team-name">梁程</h3>
                    <div class="team-role">福利</div>
                    <p class="team-bio">Business Administration major with exceptional organizational skills. Aisha ensures all our events run smoothly and create memorable experiences.</p>
                    <div class="team-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fas fa-envelope"></i></a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Gallery Section -->
        
        <!-- Contact Section -->
        <section id="contact" class="contact">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-container">
                <div class="contact-info fade-in">
                    <h3>聯係我們</h3>
                    <p>有任何疑問嗎？透過以下任何渠道聯絡我們或填寫表格。我們很高興收到您的來信！</p>
                    
                    <div class="contact-method">
                        <div class="contact-icon">
                            <i class="fas fa-map-marker-alt"></i>
                        </div>
                        <div class="contact-details">
                            <h4>Location</h4>
                            <p>SKH Kei Hau Secondary School<br>5 Kai Tin Rd, Lam Tin</p>
                        </div>
                    </div>
                    
                    <div class="contact-method">
                        <div class="contact-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <div class="contact-details">
                            <h4>Email</h4>
                            <a href="mailto:info@nebulastudentunion.org">info@nebulastudentunion.org</a>
                        </div>
                    </div>
                    
                    <div class="contact-method">
                        <div class="contact-icon">
                            <i class="fas fa-phone-alt"></i>
                        </div>
                        <div class="contact-details">
                            <h4>Phone</h4>
                            <a href="tel:+85223460252">(852) 2346 0252</a>
                        </div>
                    </div>
                    
                    
                    
                    <div class="contact-social">
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
                
                <div class="contact-form fade-in">
                    <form id="contactForm">
                        
                        <div class="form-group">
                            <label for="email">Your Email</label>
                            <input type="email" id="email" class="form-control" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="message">Message</label>
                            <textarea id="message" class="form-control" required></textarea>
                        </div>
                        
                        <button type="submit" class="submit-btn">
                            <i class="fas fa-paper-plane"></i> Send Message
                        </button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-col">
                <h4>Nebula</h4>
                <p>秉承著「Nebula」的信念，在未來的一年裡，帶領大家勇敢面對挑戰，攜手跨越重重難關。我們不僅會真誠聆聽每一位同學的聲音，虛心接受各方意見，還將恪盡職守，以滿腔熱忱，全心全意地為大家服務。成為全校師生最堅實的依靠！
                </p>
                <div class="footer-social">
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="https://www.youtube.com/"><i class="fab fa-youtube"></i></a>
                </div>
            </div>
            
            <div class="footer-col">
                <h4>快速導航</h4>
                <ul class="footer-links">
                    <li><a href="#hero"><i class="fas fa-chevron-right"></i> 主頁</a></li>
                    <li><a href="#about"><i class="fas fa-chevron-right"></i> 關於我們</a></li>
                    <li><a href="#events"><i class="fas fa-chevron-right"></i> 活動</a></li>
                    <li><a href="#team"><i class="fas fa-chevron-right"></i> 成員</a></li>
                    <li><a href="#contact"><i class="fas fa-chevron-right"></i> 聯絡</a></li>
                </ul>
            </div>
            
           
            
            </div>
        </div>
        
        <div class="footer-bottom">
            <div class="copyright">
                &copy; 2025 Nebula Student Union. All Rights Reserved.
            </div>

            <div class="footer-links-bottom">
                *我們並不代表聖公會基孝中學 如欲聯絡
                <a href="http://www.keihau.edu.hk/">請點擊鏈接</a> 
            </div>
           
        </div>
    </footer>

    <!-- Back to Top Button -->
    <div class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </div>

    <!-- Scripts -->
    <script>
        // Create stars for background
        document.addEventListener('DOMContentLoaded', function() {
            const starsContainer = document.getElementById('stars-container');
            const starsCount = 200;
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                
                // Random properties
                const size = Math.random() * 3 + 1;
                const opacity = Math.random() * 0.7 + 0.3;
                const duration = Math.random() * 5 + 3;
                const delay = Math.random() * 5;
                
                // Set styles
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                star.style.left = `${Math.random() * 100}%`;
                star.style.top = `${Math.random() * 100}%`;
                star.style.setProperty('--opacity', opacity);
                star.style.setProperty('--duration', `${duration}s`);
                star.style.setProperty('--delay', `${delay}s`);
                
                starsContainer.appendChild(star);
            }
            
            // Header scroll effect
            const header = document.getElementById('header');
            window.addEventListener('scroll', function() {
                if (window.scrollY > 50) {
                    header.classList.add('scrolled');
                } else {
                    header.classList.remove('scrolled');
                }
            });
            
            // Mobile menu toggle
            const hamburger = document.getElementById('hamburger');
            const navLinks = document.getElementById('nav-links');
            
            hamburger.addEventListener('click', function() {
                navLinks.classList.toggle('active');
                const isOpen = navLinks.classList.contains('active');
                hamburger.innerHTML = isOpen ? '<i class="fas fa-times"></i>' : '<i class="fas fa-bars"></i>';
            });
            
            // Close mobile menu when clicking on a link
            const navItems = document.querySelectorAll('.nav-links a');
            navItems.forEach(item => {
                item.addEventListener('click', function() {
                    navLinks.classList.remove('active');
                    hamburger.innerHTML = '<i class="fas fa-bars"></i>';
                });
            });
            
            // Fade in elements on scroll
            const fadeElements = document.querySelectorAll('.fade-in');
            const backToTop = document.getElementById('backToTop');
            
            function checkFade() {
                const triggerBottom = window.innerHeight * 0.8;
                
                fadeElements.forEach(element => {
                    const elementTop = element.getBoundingClientRect().top;
                    if (elementTop < triggerBottom) {
                        element.classList.add('visible');
                    }
                });
                
                // Show/hide back to top button
                if (window.scrollY > 500) {
                    backToTop.classList.add('visible');
                } else {
                    backToTop.classList.remove('visible');
                }
            }
            
            window.addEventListener('scroll', checkFade);
            checkFade(); // Initial check
            
            // Back to top functionality
            backToTop.addEventListener('click', function() {
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            });
            
            // Form submission
            const contactForm = document.getElementById('contactForm');
            if (contactForm) {
                contactForm.addEventListener('submit', function(e) {
                    e.preventDefault();
                    // Form validation and submission logic would go here
                    alert('Thank you for your message! We will get back to you soon.');
                    contactForm.reset();
                });
            }
            
           
            
            // Smooth scrolling for all anchor links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const targetId = this.getAttribute('href');
                    if (targetId === '#') return;
                    
                    const targetElement = document.querySelector(targetId);
                    if (targetElement) {
                        window.scrollTo({
                            top: targetElement.offsetTop - 80,
                            behavior: 'smooth'
                        });
                    }
                });
            });
        });
    </script>
</body>
</html>
