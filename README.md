<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JungwooShin - Backend Developer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            color: #e0e6ed;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
        }

        /* Animated background particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            background: rgba(64, 224, 208, 0.1);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); opacity: 0.3; }
            50% { transform: translateY(-20px) rotate(180deg); opacity: 0.8; }
        }

        /* Header Section */
        .header {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .name {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 800;
            background: linear-gradient(45deg, #40e0d0, #48cae4, #0096c7);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
            margin-bottom: 1rem;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .subtitle {
            font-size: 1.2rem;
            color: #b0b8c4;
            margin-bottom: 0.5rem;
            animation: slideInUp 0.8s ease-out 0.3s both;
        }

        .description {
            font-size: 1rem;
            color: #8892b0;
            animation: slideInUp 0.8s ease-out 0.5s both;
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Environment Setup */
        .section {
            margin-bottom: 3rem;
            animation: slideInUp 0.8s ease-out both;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 2rem;
            position: relative;
            color: #40e0d0;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background: linear-gradient(45deg, #40e0d0, #48cae4);
            border-radius: 2px;
        }

        .env-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .env-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(64, 224, 208, 0.2);
            border-radius: 15px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .env-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(64, 224, 208, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .env-card:hover::before {
            left: 100%;
        }

        .env-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(64, 224, 208, 0.2);
            border-color: rgba(64, 224, 208, 0.5);
        }

        .env-purpose {
            font-weight: 600;
            color: #40e0d0;
            margin-bottom: 0.5rem;
        }

        .env-os {
            color: #e0e6ed;
            font-size: 1.1rem;
        }

        /* Tech Stack */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .tech-category {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(64, 224, 208, 0.15);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .tech-category::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(64, 224, 208, 0.03) 0%, transparent 70%);
            opacity: 0;
            transition: opacity 0.3s ease;
            pointer-events: none;
        }

        .tech-category:hover::before {
            opacity: 1;
        }

        .tech-category:hover {
            transform: translateY(-3px);
            border-color: rgba(64, 224, 208, 0.3);
        }

        .tech-title {
            font-size: 1.3rem;
            font-weight: 600;
            color: #40e0d0;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .tech-title::before {
            content: '';
            width: 8px;
            height: 8px;
            background: #40e0d0;
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.7; }
        }

        .tech-list {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .tech-item {
            background: rgba(64, 224, 208, 0.1);
            color: #e0e6ed;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            font-size: 0.9rem;
            border: 1px solid rgba(64, 224, 208, 0.2);
            transition: all 0.3s ease;
            cursor: default;
        }

        .tech-item:hover {
            background: rgba(64, 224, 208, 0.2);
            border-color: rgba(64, 224, 208, 0.5);
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(64, 224, 208, 0.2);
        }

        /* Exploring Section */
        .exploring-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        .exploring-category {
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.02));
            backdrop-filter: blur(10px);
            border: 1px solid rgba(72, 202, 228, 0.2);
            border-radius: 15px;
            padding: 1.5rem;
            transition: all 0.3s ease;
        }

        .exploring-category:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(72, 202, 228, 0.15);
            border-color: rgba(72, 202, 228, 0.4);
        }

        .exploring-title {
            font-size: 1.1rem;
            font-weight: 600;
            color: #48cae4;
            margin-bottom: 1rem;
        }

        .exploring-list {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
        }

        .exploring-item {
            background: rgba(72, 202, 228, 0.1);
            color: #e0e6ed;
            padding: 0.4rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
            border: 1px solid rgba(72, 202, 228, 0.2);
            transition: all 0.3s ease;
        }

        .exploring-item:hover {
            background: rgba(72, 202, 228, 0.2);
            border-color: rgba(72, 202, 228, 0.5);
            transform: scale(1.05);
        }

        /* Footer */
        .footer {
            text-align: center;
            margin-top: 4rem;
            padding: 2rem;
            background: rgba(255, 255, 255, 0.02);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            border: 1px solid rgba(64, 224, 208, 0.1);
        }

        .footer-text {
            font-size: 1.2rem;
            color: #40e0d0;
            font-weight: 500;
            animation: fadeIn 1s ease-out 1s both;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .tech-grid {
                grid-template-columns: 1fr;
            }
            
            .env-grid {
                grid-template-columns: 1fr;
            }
            
            .exploring-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="particles" id="particles"></div>
    
    <div class="container">
        <!-- Header -->
        <header class="header">
            <h1 class="name">JungwooShin</h1>
            <p class="subtitle">Backend developer passionate about Linux and crafting practical solutions</p>
            <p class="description">Specialized in Java/Spring with expertise in infrastructure optimization</p>
        </header>

        <!-- Environment Setup -->
        <section class="section">
            <h2 class="section-title">🖥️ Environment Setup</h2>
            <div class="env-grid">
                <div class="env-card">
                    <div class="env-purpose">Development</div>
                    <div class="env-os">Arch Linux (BTW)</div>
                </div>
                <div class="env-card">
                    <div class="env-purpose">Server</div>
                    <div class="env-os">Proxmox + Ubuntu</div>
                </div>
                <div class="env-card">
                    <div class="env-purpose">Mobile</div>
                    <div class="env-os">Android</div>
                </div>
                <div class="env-card">
                    <div class="env-purpose">Gaming</div>
                    <div class="env-os">Windows 11 + Nintendo Switch + Steam</div>
                </div>
            </div>
        </section>

        <!-- Tech Stack -->
        <section class="section">
            <h2 class="section-title">🚀 Tech Stack</h2>
            <div class="tech-grid">
                <div class="tech-category">
                    <h3 class="tech-title">Languages & Core Skills</h3>
                    <div class="tech-list">
                        <span class="tech-item">Java</span>
                        <span class="tech-item">Lua</span>
                        <span class="tech-item">Bash</span>
                        <span class="tech-item">JavaScript</span>
                        <span class="tech-item">TypeScript</span>
                        <span class="tech-item">HTML5</span>
                        <span class="tech-item">CSS3</span>
                        <span class="tech-item">YAML</span>
                        <span class="tech-item">Markdown</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3 class="tech-title">Backend & Databases</h3>
                    <div class="tech-list">
                        <span class="tech-item">Spring Framework</span>
                        <span class="tech-item">Oracle</span>
                        <span class="tech-item">JWT</span>
                        <span class="tech-item">Redis</span>
                        <span class="tech-item">MySQL</span>
                        <span class="tech-item">MariaDB</span>
                        <span class="tech-item">Gradle</span>
                        <span class="tech-item">Maven</span>
                        <span class="tech-item">Hibernate</span>
                        <span class="tech-item">Swagger</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3 class="tech-title">DevOps & Infrastructure</h3>
                    <div class="tech-list">
                        <span class="tech-item">Git</span>
                        <span class="tech-item">GitHub</span>
                        <span class="tech-item">Nginx</span>
                        <span class="tech-item">Jenkins</span>
                        <span class="tech-item">Apache Tomcat</span>
                        <span class="tech-item">Docker</span>
                        <span class="tech-item">Cloudflare</span>
                        <span class="tech-item">AWS</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3 class="tech-title">Frontend & UI</h3>
                    <div class="tech-list">
                        <span class="tech-item">Svelte</span>
                        <span class="tech-item">React</span>
                        <span class="tech-item">NPM</span>
                        <span class="tech-item">Vite</span>
                        <span class="tech-item">Thymeleaf</span>
                        <span class="tech-item">Prettier</span>
                        <span class="tech-item">ESLint</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3 class="tech-title">Development Tools</h3>
                    <div class="tech-list">
                        <span class="tech-item">Vim</span>
                        <span class="tech-item">Obsidian</span>
                        <span class="tech-item">Nextcloud</span>
                        <span class="tech-item">Zed</span>
                        <span class="tech-item">VS Code</span>
                        <span class="tech-item">IntelliJ IDEA</span>
                        <span class="tech-item">Postman</span>
                        <span class="tech-item">Notion</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- Exploring -->
        <section class="section">
            <h2 class="section-title">🌟 Exploring</h2>
            <div class="exploring-grid">
                <div class="exploring-category">
                    <h3 class="exploring-title">Infrastructure & DevOps</h3>
                    <div class="exploring-list">
                        <span class="exploring-item">Kubernetes</span>
                        <span class="exploring-item">NixOS & Nix</span>
                    </div>
                </div>

                <div class="exploring-category">
                    <h3 class="exploring-title">Programming Languages</h3>
                    <div class="exploring-list">
                        <span class="exploring-item">Rust</span>
                        <span class="exploring-item">Perl</span>
                        <span class="exploring-item">Haskell</span>
                        <span class="exploring-item">C</span>
                        <span class="exploring-item">PHP</span>
                    </div>
                </div>

                <div class="exploring-category">
                    <h3 class="exploring-title">Frameworks & Tools</h3>
                    <div class="exploring-list">
                        <span class="exploring-item">Laravel</span>
                        <span class="exploring-item">FastAPI</span>
                        <span class="exploring-item">Flutter</span>
                        <span class="exploring-item">TailwindCSS</span>
                        <span class="exploring-item">Apache Kafka</span>
                        <span class="exploring-item">MongoDB</span>
                        <span class="exploring-item">Firebase</span>
                        <span class="exploring-item">Playwright & Selenium</span>
                    </div>
                </div>

                <div class="exploring-category">
                    <h3 class="exploring-title">Platforms</h3>
                    <div class="exploring-list">
                        <span class="exploring-item">Rocky Linux</span>
                        <span class="exploring-item">Vercel</span>
                        <span class="exploring-item">Jira</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="footer">
            <p class="footer-text">✨ Thanks for visiting my profile! ✨</p>
        </footer>
    </div>

    <script>
        // Create animated particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                
                const size = Math.random() * 4 + 2;
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                
                particle.style.left = `${Math.random() * 100}%`;
                particle.style.top = `${Math.random() * 100}%`;
                
                particle.style.animationDuration = `${Math.random() * 4 + 4}s`;
                particle.style.animationDelay = `${Math.random() * 2}s`;
                
                particlesContainer.appendChild(particle);
            }
        }

        // Staggered animation for sections
        function animateSections() {
            const sections = document.querySelectorAll('.section');
            sections.forEach((section, index) => {
                section.style.animationDelay = `${index * 0.2}s`;
            });
        }

        // Mouse movement parallax effect
        document.addEventListener('mousemove', (e) => {
            const particles = document.querySelectorAll('.particle');
            const x = e.clientX / window.innerWidth;
            const y = e.clientY / window.innerHeight;
            
            particles.forEach((particle, index) => {
                const speed = (index % 5 + 1) * 0.5;
                const xOffset = (x - 0.5) * speed;
                const yOffset = (y - 0.5) * speed;
                
                particle.style.transform = `translate(${xOffset}px, ${yOffset}px)`;
            });
        });

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            animateSections();
        });

        // Add scroll-triggered animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        });

        document.querySelectorAll('.tech-category, .env-card, .exploring-category').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
