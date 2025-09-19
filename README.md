<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Professional GitHub Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #0d1117;
            color: #e6edf3;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .profile-header {
            display: flex;
            gap: 30px;
            margin-bottom: 40px;
            opacity: 0;
            transform: translateY(30px);
            animation: slideInUp 0.8s ease forwards;
        }

        .profile-avatar {
            position: relative;
            flex-shrink: 0;
        }

        .avatar {
            width: 260px;
            height: 260px;
            border-radius: 50%;
            border: 4px solid #30363d;
            background: linear-gradient(135deg, #7c3aed, #3b82f6);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
            font-weight: bold;
            color: white;
            transition: all 0.3s ease;
            cursor: pointer;
            overflow: hidden;
        }

        .avatar:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px rgba(124, 58, 237, 0.5);
        }

        .status-badge {
            position: absolute;
            bottom: 20px;
            right: 20px;
            background: #238636;
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 500;
        }

        .profile-info {
            flex: 1;
        }

        .profile-name {
            font-size: 2.5rem;
            font-weight: 600;
            margin-bottom: 8px;
            background: linear-gradient(135deg, #7c3aed, #3b82f6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .profile-username {
            font-size: 1.25rem;
            color: #8b949e;
            margin-bottom: 20px;
        }

        .profile-bio {
            font-size: 1.1rem;
            margin-bottom: 20px;
            color: #e6edf3;
        }

        .profile-stats {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .stat {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 8px 12px;
            background: rgba(240, 246, 252, 0.05);
            border: 1px solid #30363d;
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .stat:hover {
            background: rgba(240, 246, 252, 0.1);
            transform: translateY(-2px);
        }

        .stat-icon {
            width: 16px;
            height: 16px;
            fill: #7c3aed;
        }

        .follow-btn {
            background: linear-gradient(135deg, #7c3aed, #3b82f6);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-right: 10px;
        }

        .follow-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(124, 58, 237, 0.3);
        }

        .content-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
            opacity: 0;
            transform: translateY(30px);
            animation: slideInUp 0.8s ease 0.3s forwards;
        }

        .repos-section {
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 20px;
            transition: all 0.3s ease;
        }

        .repos-section:hover {
            border-color: #7c3aed;
            box-shadow: 0 0 20px rgba(124, 58, 237, 0.1);
        }

        .section-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .repo-card {
            background: rgba(240, 246, 252, 0.03);
            border: 1px solid #30363d;
            border-radius: 8px;
            padding: 16px;
            margin-bottom: 12px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .repo-card:hover {
            border-color: #7c3aed;
            transform: translateX(5px);
            background: rgba(124, 58, 237, 0.05);
        }

        .repo-name {
            font-weight: 600;
            color: #58a6ff;
            margin-bottom: 8px;
        }

        .repo-description {
            color: #8b949e;
            margin-bottom: 12px;
            font-size: 0.9rem;
        }

        .repo-meta {
            display: flex;
            align-items: center;
            gap: 16px;
            font-size: 0.8rem;
            color: #8b949e;
        }

        .language-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
            margin-right: 4px;
        }

        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .contribution-graph {
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 20px;
            transition: all 0.3s ease;
        }

        .contribution-graph:hover {
            border-color: #7c3aed;
        }

        .graph-grid {
            display: grid;
            grid-template-columns: repeat(53, 1fr);
            gap: 3px;
            margin-top: 16px;
        }

        .graph-day {
            width: 10px;
            height: 10px;
            border-radius: 2px;
            background: #161b22;
            border: 1px solid #30363d;
            transition: all 0.2s ease;
        }

        .graph-day.level-1 { background: #0e4429; }
        .graph-day.level-2 { background: #006d32; }
        .graph-day.level-3 { background: #26a641; }
        .graph-day.level-4 { background: #39d353; }

        .graph-day:hover {
            transform: scale(1.2);
            box-shadow: 0 0 10px rgba(124, 58, 237, 0.5);
        }

        .achievements {
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 20px;
        }

        .achievement-badge {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px;
            background: rgba(240, 246, 252, 0.03);
            border: 1px solid #30363d;
            border-radius: 8px;
            margin-bottom: 12px;
            transition: all 0.3s ease;
        }

        .achievement-badge:hover {
            transform: translateX(5px);
            border-color: #7c3aed;
        }

        .achievement-icon {
            width: 32px;
            height: 32px;
            background: linear-gradient(135deg, #7c3aed, #3b82f6);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
        }

        @keyframes slideInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }

        .typing-animation {
            border-right: 2px solid #7c3aed;
            animation: pulse 1s infinite;
        }

        @media (max-width: 768px) {
            .profile-header {
                flex-direction: column;
                text-align: center;
            }
            
            .content-grid {
                grid-template-columns: 1fr;
            }
            
            .avatar {
                width: 200px;
                height: 200px;
                font-size: 60px;
                align-self: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="profile-header">
            <div class="profile-avatar">
                <div class="avatar" id="avatar">
                    <span>JD</span>
                </div>
                <div class="status-badge">Available for work</div>
            </div>
            <div class="profile-info">
                <h1 class="profile-name">John Developer</h1>
                <p class="profile-username">@john-developer</p>
                <p class="profile-bio">Full-stack developer passionate about creating amazing web experiences. <span class="typing-animation">Building the future, one line of code at a time</span> 🚀</p>
                
                <div class="profile-stats">
                    <div class="stat">
                        <svg class="stat-icon" viewBox="0 0 16 16">
                            <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
                        </svg>
                        <span>127 repositories</span>
                    </div>
                    <div class="stat">
                        <svg class="stat-icon" viewBox="0 0 16 16">
                            <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
                        </svg>
                        <span>2.3k followers</span>
                    </div>
                    <div class="stat">
                        <svg class="stat-icon" viewBox="0 0 16 16">
                            <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
                        </svg>
                        <span>892 following</span>
                    </div>
                </div>
                
                <button class="follow-btn">Follow</button>
                <button class="follow-btn" style="background: transparent; border: 1px solid #30363d;">Message</button>
            </div>
        </div>

        <div class="content-grid">
            <div class="repos-section">
                <h2 class="section-title">
                    <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
                        <path d="M2 2.5A2.5 2.5 0 014.5 0h8.75a.75.75 0 01.75.75v12.5a.75.75 0 01-.75.75h-2.5a.75.75 0 110-1.5h1.75v-2h-8a1 1 0 00-.714 1.7.75.75 0 01-1.072 1.05A2.495 2.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU 00.4.2l1.47wQbNPTDJp9hMYdvogK2hAUiHsGeiybwaWe36bwtRQ3UTpYV7YuZ8FV5j9nauFCWwcjM6dTzpL5s2N79Rp5unwdMvc8ZKU25.25z"/>
                    </svg>
                    Popular repositories
                </h2>
                
                <div class="repo-card">
                    <h3 class="repo-name">awesome-web-components</h3>
                    <p class="repo-description">A collection of reusable web components built with modern JavaScript frameworks. Perfect for rapid prototyping and production apps.</p>
                    <div class="repo-meta">
                        <span><span class="language-dot" style="background: #f1e05a;"></span>JavaScript</span>
                        <span>⭐ 1.2k</span>
                        <span>🍴 234</span>
                        <span>Updated 2 days ago</span>
                    </div>
                </div>

                <div class="repo-card">
                    <h3 class="repo-name">react-dashboard-pro</h3>
                    <p class="repo-description">Professional React dashboard template with TypeScript, charts, and responsive design. Used by 500+ developers worldwide.</p>
                    <div class="repo-meta">
                        <span><span class="language-dot" style="background: #61dafb;"></span>TypeScript</span>
                        <span>⭐ 2.8k</span>
                        <span>🍴 456</span>
                        <span>Updated 1 week ago</span>
                    </div>
                </div>

                <div class="repo-card">
                    <h3 class="repo-name">api-gateway-nodejs</h3>
                    <p class="repo-description">Scalable API gateway built with Node.js and Express. Features rate limiting, authentication, and microservice routing.</p>
                    <div class="repo-meta">
                        <span><span class="language-dot" style="background: #8cc84b;"></span>Node.js</span>
                        <span>⭐ 890</span>
                        <span>🍴 167</span>
                        <span>Updated 3 days ago</span>
                    </div>
                </div>

                <div class="repo-card">
                    <h3 class="repo-name">ml-prediction-engine</h3>
                    <p class="repo-description">Machine learning prediction engine using Python and TensorFlow. Deployed on AWS with Docker containerization.</p>
                    <div class="repo-meta">
                        <span><span class="language-dot" style="background: #3572a5;"></span>Python</span>
                        <span>⭐ 756</span>
                        <span>🍴 123</span>
                        <span>Updated 5 days ago</span>
                    </div>
                </div>
            </div>

            <div class="sidebar">
                <div class="contribution-graph">
                    <h3 class="section-title">Contribution Activity</h3>
                    <p style="color: #8b949e; font-size: 0.9rem; margin-bottom: 16px;">1,247 contributions in the last year</p>
                    <div class="graph-grid" id="contributionGraph"></div>
                </div>

                <div class="achievements">
                    <h3 class="section-title">Achievements</h3>
                    
                    <div class="achievement-badge">
                        <div class="achievement-icon">🏆</div>
                        <div>
                            <h4 style="color: #e6edf3; margin-bottom: 4px;">Arctic Code Vault Contributor</h4>
                            <p style="color: #8b949e; font-size: 0.8rem;">Contributed code in 2020 GitHub Archive Program</p>
                        </div>
                    </div>

                    <div class="achievement-badge">
                        <div class="achievement-icon">🔥</div>
                        <div>
                            <h4 style="color: #e6edf3; margin-bottom: 4px;">Quickdraw</h4>
                            <p style="color: #8b949e; font-size: 0.8rem;">Merged a pull request within 1 hour of opening</p>
                        </div>
                    </div>

                    <div class="achievement-badge">
                        <div class="achievement-icon">⭐</div>
                        <div>
                            <h4 style="color: #e6edf3; margin-bottom: 4px;">Starstruck</h4>
                            <p style="color: #8b949e; font-size: 0.8rem;">Created a repository with 16+ stars</p>
                        </div>
                    </div>

                    <div class="achievement-badge">
                        <div class="achievement-icon">💻</div>
                        <div>
                            <h4 style="color: #e6edf3; margin-bottom: 4px;">Pull Shark</h4>
                            <p style="color: #8b949e; font-size: 0.8rem;">Opened a pull request that was merged</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Generate contribution graph
        function generateContributionGraph() {
            const graph = document.getElementById('contributionGraph');
            const days = 365;
            
            for (let i = 0; i < days; i++) {
                const day = document.createElement('div');
                day.className = 'graph-day';
                
                // Random contribution levels
                const random = Math.random();
                if (random > 0.9) day.classList.add('level-4');
                else if (random > 0.7) day.classList.add('level-3');
                else if (random > 0.5) day.classList.add('level-2');
                else if (random > 0.3) day.classList.add('level-1');
                
                // Add hover effect with delay
                day.addEventListener('mouseenter', function() {
                    this.style.transform = 'scale(1.2)';
                    this.style.zIndex = '10';
                });
                
                day.addEventListener('mouseleave', function() {
                    this.style.transform = 'scale(1)';
                    this.style.zIndex = '1';
                });
                
                graph.appendChild(day);
            }
        }

        // Avatar interaction
        const avatar = document.getElementById('avatar');
        avatar.addEventListener('click', function() {
            this.style.transform = 'rotate(360deg) scale(1.1)';
            setTimeout(() => {
                this.style.transform = 'rotate(0deg) scale(1)';
            }, 600);
        });

        // Typing animation
        function startTypingAnimation() {
            const typingElement = document.querySelector('.typing-animation');
            const text = 'Building the future, one line of code at a time';
            let index = 0;
            
            function type() {
                if (index < text.length) {
                    typingElement.textContent = text.slice(0, index + 1);
                    index++;
                    setTimeout(type, 100);
                } else {
                    setTimeout(() => {
                        index = 0;
                        typingElement.textContent = '';
                        type();
                    }, 3000);
                }
            }
            
            type();
        }

        // Add floating animation to repo cards
        function addFloatingAnimation() {
            const repoCards = document.querySelectorAll('.repo-card');
            repoCards.forEach((card, index) => {
                card.style.animationDelay = `${index * 0.1}s`;
                card.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-5px) translateX(5px)';
                    this.style.boxShadow = '0 10px 20px rgba(124, 58, 237, 0.2)';
                });
                
                card.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0) translateX(0)';
                    this.style.boxShadow = 'none';
                });
            });
        }

        // Initialize all animations
        document.addEventListener('DOMContentLoaded', function() {
            generateContributionGraph();
            startTypingAnimation();
            addFloatingAnimation();
            
            // Add stagger animation to stats
            const stats = document.querySelectorAll('.stat');
            stats.forEach((stat, index) => {
                stat.style.opacity = '0';
                stat.style.transform = 'translateY(20px)';
                setTimeout(() => {
                    stat.style.transition = 'all 0.6s ease';
                    stat.style.opacity = '1';
                    stat.style.transform = 'translateY(0)';
                }, 800 + (index * 200));
            });
        });

        // Add parallax effect on scroll
        window.addEventListener('scroll', function() {
            const scrolled = window.pageYOffset;
            const avatar = document.getElementById('avatar');
            avatar.style.transform = `translateY(${scrolled * 0.5}px) scale(${1 + scrolled * 0.0002})`;
        });
    </script>
</body>
</html>
