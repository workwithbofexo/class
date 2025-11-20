<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Compact Button Layout</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary-color: #3b82f6;
            --secondary-color: #8b5cf6;
            --accent-color: #10b981;
            --dark-bg: #0f172a;
            --medium-bg: #1e293b;
            --light-text: #e2e8f0;
            --muted-text: #94a3b8;
            --card-bg: rgba(255, 255, 255, 0.1);
            --card-border: rgba(255, 255, 255, 0.2);
        }
        
        body {
            background: linear-gradient(135deg, var(--dark-bg), var(--medium-bg));
            color: var(--light-text);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            line-height: 1.6;
        }
        
        /* Header Styles */
        header {
            background: rgba(15, 23, 42, 0.9);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            width: 100%;
        }
        
        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 1.5rem;
        }
        
        .logo {
            font-size: clamp(1.5rem, 4vw, 1.8rem);
            font-weight: 700;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .logo i {
            font-size: clamp(1.5rem, 4vw, 2rem);
        }
        
        .nav-menu {
            display: flex;
            gap: 1.5rem;
        }
        
        .nav-link {
            color: var(--muted-text);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            font-size: clamp(0.9rem, 2vw, 1rem);
        }
        
        .nav-link:hover {
            color: var(--primary-color);
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--light-text);
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        /* Main Content Styles */
        main {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 2rem 1.5rem;
            width: 100%;
        }
        
        .page-title {
            text-align: center;
            margin-bottom: 3rem;
            max-width: 800px;
        }
        
        .page-title h1 {
            font-size: clamp(1.8rem, 5vw, 2.5rem);
            margin-bottom: 1rem;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .page-title p {
            font-size: clamp(1rem, 2.5vw, 1.1rem);
            color: var(--muted-text);
            max-width: 600px;
            margin: 0 auto;
        }
        
        /* Button Grid Styles */
        .button-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.2rem;
            max-width: 1200px;
            width: 100%;
        }
        
        /* Common Button Styles */
        .glass-button {
            background: var(--card-bg);
            backdrop-filter: blur(10px);
            border-radius: 16px;
            padding: 1.5rem 1rem;
            text-align: center;
            transition: all 0.4s ease;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
            cursor: pointer;
            display: block;
            text-decoration: none;
            color: inherit;
            height: 100%;
            border: 1px solid var(--card-border);
            aspect-ratio: 1 / 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        
        .glass-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
        }
        
        .button-content {
            position: relative;
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
            width: 100%;
        }
        
        .icon {
            font-size: clamp(2rem, 6vw, 2.8rem);
            margin-bottom: 0.8rem;
        }
        
        .btn-title {
            font-size: clamp(1rem, 3vw, 1.3rem);
            font-weight: 600;
            margin-bottom: 0.3rem;
            text-align: center;
        }
        
        .btn-desc {
            color: var(--muted-text);
            font-size: clamp(0.75rem, 2vw, 0.85rem);
            text-align: center;
            line-height: 1.4;
            padding: 0 0.5rem;
        }
        
        /* =============================== */
        /* BUTTON A STYLES - Glass Morphism */
        /* =============================== */
        .btn-a {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-a::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2));
            z-index: 1;
            transition: opacity 0.4s ease;
            opacity: 0;
        }
        
        .btn-a:hover::before {
            opacity: 1;
        }
        
        .btn-a .icon {
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        /* =============================== */
        /* BUTTON B STYLES - Neon Glow */
        /* =============================== */
        .btn-a {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-a::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2));
            z-index: 1;
            transition: opacity 0.4s ease;
            opacity: 0;
        }
        
        .btn-a:hover::before {
            opacity: 1;
        }
        
        .btn-a .icon {
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        /* =============================== */
        /* BUTTON C STYLES - Holographic */
        /* =============================== */
        .btn-a {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-a::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2));
            z-index: 1;
            transition: opacity 0.4s ease;
            opacity: 0;
        }
        
        .btn-a:hover::before {
            opacity: 1;
        }
        
        .btn-a .icon {
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        /* =============================== */
        /* BUTTON D STYLES - Cyberpunk */
        /* =============================== */
        .btn-a {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .btn-a::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.2), rgba(139, 92, 246, 0.2));
            z-index: 1;
            transition: opacity 0.4s ease;
            opacity: 0;
        }
        
        .btn-a:hover::before {
            opacity: 1;
        }
        
        .btn-a .icon {
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        /* Footer Styles */
        footer {
            background: rgba(15, 23, 42, 0.9);
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding: 2rem 0;
            margin-top: auto;
            width: 100%;
        }
        
        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 1.5rem;
        }
        
        .footer-logo {
            font-size: clamp(1.2rem, 3vw, 1.5rem);
            font-weight: 700;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .footer-links {
            display: flex;
            gap: 1.5rem;
        }
        
        .footer-links a {
            color: var(--muted-text);
            text-decoration: none;
            transition: color 0.3s ease;
            font-size: clamp(0.85rem, 2vw, 0.9rem);
        }
        
        .footer-links a:hover {
            color: var(--primary-color);
        }
        
        .copyright {
            color: var(--muted-text);
            font-size: clamp(0.8rem, 2vw, 0.9rem);
        }
        
        /* Responsive Styles */
        @media (max-width: 768px) {
            .header-container, .footer-container {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }
            
            .nav-menu {
                flex-direction: column;
                gap: 1rem;
                width: 100%;
                display: none;
            }
            
            .nav-menu.active {
                display: flex;
            }
            
            .mobile-menu-btn {
                display: block;
                position: absolute;
                right: 1.5rem;
                top: 1rem;
            }
            
            .button-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 1rem;
            }
            
            .glass-button {
                padding: 1.2rem 0.8rem;
                aspect-ratio: 1 / 1;
            }
            
            .footer-links {
                flex-wrap: wrap;
                justify-content: center;
                gap: 1rem;
            }
        }
        
        @media (min-width: 769px) and (max-width: 1024px) {
            .button-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .glass-button {
                padding: 1.8rem 1.2rem;
                aspect-ratio: 1 / 1;
            }
        }
        
        @media (min-width: 1025px) {
            .button-grid {
                grid-template-columns: repeat(4, 1fr);
            }
            
            .glass-button {
                aspect-ratio: 1 / 1;
            }
        }
        
        @media (max-width: 480px) {
            .header-container, .footer-container {
                padding: 0 1rem;
            }
            
            main {
                padding: 1.5rem 1rem;
            }
            
            .page-title {
                margin-bottom: 2rem;
            }
            
            .glass-button {
                padding: 1rem 0.5rem;
            }
            
            .btn-desc {
                display: none; /* Hide description on very small screens */
            }
        }
        
        @media (max-width: 360px) {
            .button-grid {
                grid-template-columns: 1fr;
            }
            
            .glass-button {
                aspect-ratio: auto;
                height: auto;
                min-height: 120px;
            }
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header>
        <div class="header-container">
            <div class="logo">
                <i class="fas fa-cube"></i>
                <span>BOFEXO</span>
            </div>
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            <nav class="nav-menu" id="navMenu">
                <a href="https://newbofexo.blogspot.com/2025/10/homepage.html" class="nav-link">Home</a>
                <a href="#" class="nav-link">All AI tools</a>
                <a href="https://newbofexo.blogspot.com/p/privacy-policy.html" class="nav-link">Our Privacy Policy</a>
              <a href="https://newbofexo.blogspot.com/p/terms-of-services.html" class="nav-link">Terms Of Services</a>
                <a href="https://newbofexo.blogspot.com/p/copyright-disclaimer.html" class="nav-link">Copyright Disclaimer</a>
              <a href="https://newbofexo.blogspot.com/p/contact-us.html" class="nav-link">Contact Us</a>
            </nav>
        </div>
    </header>

    <!-- Main Content Section -->
    <main>
        <div class="page-title">
            <h1>Select Your Choice</h1>
            <p>In Education</p>
        </div>
        
        <div class="button-grid">
            <!-- =============================== -->
            <!-- BUTTON A - School Exams -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/select-your-class-school-exams-page.html" class="glass-button btn-a">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-school"></i>
                    </div>
                    <div class="btn-title">School Exams</div>
                </div>
            </a>
            
            <!-- =============================== -->
            <!-- BUTTON B - Engineering -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-cogs"></i>
                    </div>
                    <div class="btn-title">Engineering</div>
                </div>
            </a>
            
            <!-- =============================== -->
            <!-- BUTTON C - Medical -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-c">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-stethoscope"></i>
                    </div>
                    <div class="btn-title">Medical</div>
                </div>
            </a>
            
            <!-- =============================== -->
            <!-- BUTTON D - Law -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-d">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-gavel"></i>
                    </div>
                    <div class="btn-title">Law</div>
                </div>
            </a>
            
            <!-- =============================== -->
            <!-- BUTTON E - Management -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-a">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-briefcase"></i>
                    </div>
                    <div class="btn-title">Management</div>
                </div>
            </a>
            
            <!-- =============================== -->
            <!-- BUTTON F - Defence -->
            <!-- =============================== -->
            <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-jet-fighter-up"></i>
                    </div>
                    <div class="btn-title">Defence</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-clipboard-list"></i>
                    </div>
                    <div class="btn-title">civil services</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-money-bill-wave"></i>
                    </div>
                    <div class="btn-title">Banking</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-chalkboard"></i>
                    </div>
                    <div class="btn-title">Teacher</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-monument"></i>
                    </div>
                    <div class="btn-title">Architecture</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-chart-bar"></i>
                    </div>
                    <div class="btn-title">Commerce</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-hotel"></i>
                    </div>
                    <div class="btn-title">Hotels</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-tractor"></i>
                    </div>
                    <div class="btn-title">Agriculture</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-palette"></i>
                    </div>
                    <div class="btn-title">Arts & Music</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-microscope"></i>
                    </div>
                    <div class="btn-title">Research</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-language"></i>
                    </div>
                    <div class="btn-title">Language</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-file-alt"></i>
                    </div>
                    <div class="btn-title">General Exam</div>
                </div>
            </a>
           <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-plane"></i>
                    </div>
                    <div class="btn-title">Aviation</div>
                </div>
            </a>
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-landmark"></i>
                    </div>
                    <div class="btn-title">Goverment</div>
                </div>
            </a>
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-balance-scale"></i>
                    </div>
                    <div class="btn-title">Judiciary</div>
                </div>
            </a>
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-pills"></i>
                    </div>
                    <div class="btn-title">Pharmacy</div>
                </div>
            </a>
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-book"></i>
                    </div>
                    <div class="btn-title">Humanities</div>
                </div>
            </a>
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-trophy"></i>
                    </div>
                    <div class="btn-title">Sports</div>
                </div>
            </a>
          
          <a href="https://newbofexo.blogspot.com/p/coming-soon-6.html" class="glass-button btn-b">
                <div class="button-content">
                    <div class="icon">
                        <i class="fas fa-question-circle"></i>
                    </div>
                    <div class="btn-title">Help</div>
                </div>
            </a>
        </div>
    </main>

    <!-- Footer Section -->
    <footer>
        <div class="footer-container">
            <div class="footer-logo">BOFEXO</div>
            <div class="copyright">© 2023 Bofexo Portal. All rights reserved.</div>
            <div class="footer-links">
                <a href="#">Privacy Policy</a>
                <a href="#">Terms of Service</a>
                <a href="#">Contact Us</a>
            </div>
        </div>
    </footer>

    <script>
        // Mobile menu functionality
        document.getElementById('mobileMenuBtn').addEventListener('click', function() {
            const navMenu = document.getElementById('navMenu');
            navMenu.classList.toggle('active');
            
            // Change icon based on menu state
            const icon = this.querySelector('i');
            if (navMenu.classList.contains('active')) {
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-times');
            } else {
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            }
        });
        
        // Close mobile menu when clicking on a link
        const navLinks = document.querySelectorAll('.nav-link');
        navLinks.forEach(link => {
            link.addEventListener('click', function() {
                const navMenu = document.getElementById('navMenu');
                const mobileMenuBtn = document.getElementById('mobileMenuBtn');
                const icon = mobileMenuBtn.querySelector('i');
                
                navMenu.classList.remove('active');
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            });
        });
    </script>
</body>
</html>
