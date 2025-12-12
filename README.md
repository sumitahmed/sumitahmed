<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anime Tech Banner</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0a0a;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        .banner-container {
            width: 1600px;
            height: 400px;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, #0f0f0f 0%, #1a1a1a 50%, #0f0f0f 100%);
        }

        /* Animated background elements */
        .particle {
            position: absolute;
            background: rgba(255, 50, 80, 0.15);
            border-radius: 50%;
            animation: float 8s infinite ease-in-out;
        }

        .particle:nth-child(1) {
            width: 200px;
            height: 200px;
            top: -50px;
            right: 10%;
            background: radial-gradient(circle, rgba(255, 50, 80, 0.2) 0%, transparent 70%);
            animation-delay: 0s;
        }

        .particle:nth-child(2) {
            width: 150px;
            height: 150px;
            bottom: -30px;
            left: 15%;
            background: radial-gradient(circle, rgba(0, 150, 255, 0.15) 0%, transparent 70%);
            animation-delay: 2s;
        }

        .particle:nth-child(3) {
            width: 100px;
            height: 100px;
            top: 50%;
            right: 25%;
            background: radial-gradient(circle, rgba(255, 50, 80, 0.1) 0%, transparent 70%);
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% {
                transform: translate(0, 0) scale(1);
                opacity: 0.3;
            }
            50% {
                transform: translate(30px, -30px) scale(1.1);
                opacity: 0.5;
            }
        }

        /* Sakura petals */
        .sakura {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(255, 100, 150, 0.6);
            border-radius: 50%;
            animation: fall linear infinite;
        }

        @keyframes fall {
            0% {
                transform: translateY(-10px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(410px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Code fragments */
        .code-fragment {
            position: absolute;
            font-family: 'Courier New', monospace;
            font-size: 10px;
            color: rgba(0, 200, 255, 0.3);
            animation: drift 15s linear infinite;
        }

        @keyframes drift {
            0% {
                transform: translateX(-100px);
                opacity: 0;
            }
            10% {
                opacity: 0.4;
            }
            90% {
                opacity: 0.4;
            }
            100% {
                transform: translateX(1700px);
                opacity: 0;
            }
        }

        /* Circuit lines */
        .circuit {
            position: absolute;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(0, 150, 255, 0.3), transparent);
            animation: pulse 3s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 0.2;
            }
            50% {
                opacity: 0.6;
            }
        }

        /* Content layer */
        .content {
            position: relative;
            z-index: 10;
            height: 100%;
            display: flex;
            align-items: center;
            padding: 0 80px;
        }

        .character-container {
            flex-shrink: 0;
            width: 320px;
            height: 320px;
            position: relative;
        }

        .character-glow {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255, 50, 80, 0.3) 0%, transparent 60%);
            filter: blur(30px);
            animation: glow-pulse 3s ease-in-out infinite;
        }

        @keyframes glow-pulse {
            0%, 100% {
                transform: scale(0.95);
                opacity: 0.6;
            }
            50% {
                transform: scale(1.05);
                opacity: 0.8;
            }
        }

        .character-image {
            position: relative;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 3px solid rgba(255, 50, 80, 0.5);
            background: linear-gradient(135deg, #1a1a1a, #2a2a2a);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            box-shadow: 0 0 40px rgba(255, 50, 80, 0.3);
        }

        .character-placeholder {
            font-size: 120px;
            opacity: 0.3;
        }

        .info-container {
            margin-left: 60px;
            flex: 1;
        }

        .name {
            font-size: 52px;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 8px;
            text-shadow: 0 0 20px rgba(255, 50, 80, 0.5);
            letter-spacing: 2px;
        }

        .username {
            font-size: 24px;
            color: #888;
            margin-bottom: 24px;
        }

        .bio {
            font-size: 18px;
            color: #aaa;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .bio-item {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }

        .bio-icon {
            margin-right: 12px;
            font-size: 20px;
        }

        .tech-badge {
            display: inline-block;
            padding: 6px 14px;
            margin: 4px 6px 4px 0;
            background: rgba(255, 50, 80, 0.15);
            border: 1px solid rgba(255, 50, 80, 0.3);
            border-radius: 6px;
            font-size: 13px;
            color: #ff6b9d;
            font-weight: 500;
        }

        .tech-badge.blue {
            background: rgba(0, 150, 255, 0.15);
            border-color: rgba(0, 150, 255, 0.3);
            color: #4da6ff;
        }

        .stats-container {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }

        .stat {
            font-size: 14px;
            color: #666;
        }

        .stat-value {
            font-size: 20px;
            font-weight: 700;
            color: #fff;
            margin-right: 4px;
        }
    </style>
</head>
<body>
    <div class="banner-container">
        <!-- Background particles -->
        <div class="particle"></div>
        <div class="particle"></div>
        <div class="particle"></div>

        <!-- Sakura petals -->
        <script>
            for (let i = 0; i < 20; i++) {
                const sakura = document.createElement('div');
                sakura.className = 'sakura';
                sakura.style.left = Math.random() * 100 + '%';
                sakura.style.animationDuration = (Math.random() * 5 + 8) + 's';
                sakura.style.animationDelay = Math.random() * 5 + 's';
                sakura.style.width = (Math.random() * 3 + 2) + 'px';
                sakura.style.height = sakura.style.width;
                document.querySelector('.banner-container').appendChild(sakura);
            }

            // Code fragments
            const codeSnippets = ['const', 'function', '{...}', 'async', '=>', 'import', 'export'];
            for (let i = 0; i < 8; i++) {
                const code = document.createElement('div');
                code.className = 'code-fragment';
                code.textContent = codeSnippets[Math.floor(Math.random() * codeSnippets.length)];
                code.style.top = Math.random() * 380 + 'px';
                code.style.animationDelay = Math.random() * 15 + 's';
                document.querySelector('.banner-container').appendChild(code);
            }

            // Circuit lines
            for (let i = 0; i < 5; i++) {
                const circuit = document.createElement('div');
                circuit.className = 'circuit';
                circuit.style.top = Math.random() * 400 + 'px';
                circuit.style.left = Math.random() * 30 + '%';
                circuit.style.width = Math.random() * 200 + 100 + 'px';
                circuit.style.animationDelay = Math.random() * 3 + 's';
                document.querySelector('.banner-container').appendChild(circuit);
            }
        </script>

        <!-- Content -->
        <div class="content">
            <div class="character-container">
                <div class="character-glow"></div>
                <div class="character-image">
                    <div class="character-placeholder">👤</div>
                </div>
            </div>

            <div class="info-container">
                <div class="name">Sk Sumit Ahmed</div>
                <div class="username">sumitahmed</div>
                
                <div class="bio">
                    <div class="bio-item">
                        <span class="bio-icon">💻</span>
                        <span>Full Stack Dev | Java, Python | DevOps & Cyber Security Enthusiast</span>
                    </div>
                    <div class="bio-item">
                        <span class="bio-icon">🚀</span>
                        <span>Building innovative solutions • Open Source Contributor</span>
                    </div>
                </div>

                <div>
                    <span class="tech-badge">React</span>
                    <span class="tech-badge">Node.js</span>
                    <span class="tech-badge blue">Python</span>
                    <span class="tech-badge blue">Java</span>
                    <span class="tech-badge">FastAPI</span>
                    <span class="tech-badge blue">Docker</span>
                    <span class="tech-badge">MongoDB</span>
                </div>

                <div class="stats-container">
                    <div class="stat">
                        <span class="stat-value">28</span>Repos
                    </div>
                    <div class="stat">
                        <span class="stat-value">194</span>Stars
                    </div>
                    <div class="stat">
                        <span class="stat-value">802</span>Commits
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
