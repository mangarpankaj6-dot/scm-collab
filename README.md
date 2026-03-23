<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SCM Collab - Influencer Marketing Agency</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: #1e40af;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: #1e40af;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            padding-top: 80px;
        }

        .hero-content {
            text-align: center;
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 700;
            color: #1e3a8a;
            margin-bottom: 1.5rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards;
        }

        .hero .subheadline {
            font-size: clamp(1.1rem, 2.5vw, 1.5rem);
            color: #475569;
            margin-bottom: 1rem;
            font-weight: 400;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease 0.2s forwards;
        }

        .hero .short-line {
            font-size: 1.2rem;
            color: #64748b;
            margin-bottom: 3rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease 0.4s forwards;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(135deg, #1e40af 0%, #1d4ed8 100%);
            color: white;
            padding: 1.2rem 3rem;
            font-size: 1.2rem;
            font-weight: 600;
            border-radius: 12px;
            text-decoration: none;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(30, 64, 175, 0.3);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease 0.6s forwards;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 20px 40px rgba(30, 64, 175, 0.4);
        }

        /* Features Section */
        .features {
            padding: 120px 0;
            background: white;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            font-weight: 700;
            color: #1e3a8a;
            margin-bottom: 4rem;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .feature-card {
            text-align: center;
            padding: 2.5rem 2rem;
            border-radius: 16px;
            background: #f8fafc;
            transition: all 0.3s ease;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease forwards;
        }

        .feature-card:nth-child(2) { animation-delay: 0.2s; }
        .feature-card:nth-child(3) { animation-delay: 0.4s; }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.1);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            display: block;
        }

        .feature-card h3 {
            font-size: 1.5rem;
            font-weight: 600;
            color: #1e3a8a;
            margin-bottom: 1rem;
        }

        .feature-card p {
            color: #64748b;
            font-size: 1rem;
        }

        /* How It Works */
        .how-it-works {
            padding: 120px 0;
            background: #f1f5f9;
        }

        .steps-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 4rem;
        }

        .step {
            text-align: center;
            padding: 2.5rem;
            background: white;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            position: relative;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease forwards;
        }

        .step:nth-child(2) { animation-delay: 0.2s; }
        .step:nth-child(3) { animation-delay: 0.4s; }

        .step-number {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #1e40af, #1d4ed8);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: 700;
            margin: 0 auto 1.5rem;
        }

        .step h3 {
            font-size: 1.3rem;
            font-weight: 600;
            color: #1e3a8a;
            margin-bottom: 1rem;
        }

        /* CTA Section */
        .final-cta {
            padding: 120px 0;
            background: linear-gradient(135deg, #1e40af 0%, #1d4ed8 100%);
            text-align: center;
            color: white;
        }

        .final-cta h2 {
            font-size: clamp(2rem, 4vw, 3rem);
            font-weight: 700;
            margin-bottom: 2rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards;
        }

        .final-cta .cta-button {
            background: white;
            color: #1e40af;
            font-weight: 600;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease 0.3s forwards;
        }

        .final-cta .cta-button:hover {
            background: #f8fafc;
            transform: translateY(-3px);
        }

        /* Footer */
        footer {
            background: #1f2937;
            color: white;
            text-align: center;
            padding: 3rem 0 1.5rem;
        }

        .footer-content h3 {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: #1e40af;
        }

        .footer-content p {
            color: #9ca3af;
            margin-bottom: 1rem;
        }

        .footer-email {
            color: #60a5fa;
            text-decoration: none;
            font-weight: 500;
        }

        /* Animations */
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero {
                padding-top: 100px;
                min-height: calc(100vh - 100px);
            }

            .features, .how-it-works, .final-cta {
                padding: 80px 0;
            }

            .steps-grid, .features-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <nav class="container">
            <div class="logo">SCM Collab</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#apply">Apply</a></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Grow Your Brand with Creators 🚀</h1>
                <div class="subheadline">
                    We connect brands with creators in Fitness 💪 | AI 🤖 | Skincare ✨
                </div>
                <div class="short-line">
                    Get high-performing content, reach & real results
                </div>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSfTa0LAywCMBgX9x5m88iPyRvjy9M4dYRgIJFbHQ9vTS6RFVw/viewform?usp=publish-editor" 
                   class="cta-button" target="_blank">🚀 Apply Now</a>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="about" class="features">
        <div class="container">
            <h2 class="section-title">Why Choose SCM Collab</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <span class="feature-icon">📈</span>
                    <h3>Increase Reach</h3>
                    <p>Tap into our curated network of engaged creators to expand your audience and boost visibility</p>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">🤝</span>
                    <h3>Creator Network</h3>
                    <p>Access pre-vetted creators in Fitness, AI, and Skincare who deliver authentic content</p>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">💰</span>
                    <h3>Drive Sales</h3>
                    <p>Get measurable results with creators who convert followers into customers</p>
                </div>
            </div>
        </div>
    </section>

    <!-- How It Works -->
    <section class="how-it-works">
        <div class="container">
            <h2 class="section-title" style="color: #1e3a8a;">How It Works</h2>
            <div class="steps-grid">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>Apply using the form</h3>
                    <p>Tell us about your brand or creator profile in 2 minutes</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>We connect you</h3>
                    <p>Our team matches you with perfect brand/creator partnerships</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>Start collaborations</h3>
                    <p>Launch campaigns and see real results</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Final CTA -->
    <section id="apply" class="final-cta">
        <div class="container">
            <h2>Ready to start brand deals?</h2>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSfTa0LAywCMBgX9x5m88iPyRvjy9M4dYRgIJFbHQ9vTS6RFVw/viewform?usp=publish-editor" 
               class="cta-button" target="_blank">Apply Now 🚀</a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container footer-content">
            <h3>SCM Collab</h3>
            <p>Influencer Marketing Agency</p>
            <p><a href="mailto:pankaj1collabs@gmail.com" class="footer-email">pankaj1collabs@gmail.com</a></p>
             <p><a href="Dmto:SCM_collab" class="footer-insta">DM :- SCM_collab</a></p>
             <p><a href="phone:8329717847" class="footer-insta">phone :- 8329717847</a></p>
        </div>
    </footer>
</body>
</html>
