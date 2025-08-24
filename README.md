<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb, #f5576c);
            background-size: 400% 400%;
            animation: gradientShift 8s ease infinite;
            color: #333;
            min-height: 100vh;
            padding: 20px;
        }
        
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 30px 80px rgba(0,0,0,0.2);
            backdrop-filter: blur(10px);
            animation: containerFloat 6s ease-in-out infinite;
        }
        
        @keyframes containerFloat {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .typing-text {
            font-size: 18px;
            line-height: 1.8;
            margin: 20px 0;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
            position: relative;
        }
        
        .typing-text:nth-child(1) { animation-delay: 0.2s; }
        .typing-text:nth-child(2) { animation-delay: 0.6s; }
        .typing-text:nth-child(3) { animation-delay: 1s; }
        .typing-text:nth-child(4) { animation-delay: 1.4s; }
        
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
        
        .dynamic-text {
            color: #667eea;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-block;
            position: relative;
            overflow: hidden;
        }
        
        .dynamic-text:hover {
            transform: scale(1.1);
            color: #f5576c;
        }
        
        .dynamic-text::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background: linear-gradient(45deg, #667eea, #f5576c);
            transition: width 0.3s ease;
        }
        
        .dynamic-text:hover::after {
            width: 100%;
        }
        
        .rotating-skills {
            display: inline-block;
            color: #f5576c;
            font-weight: bold;
            min-width: 150px;
            animation: colorPulse 2s ease-in-out infinite;
        }
        
        @keyframes colorPulse {
            0%, 100% { color: #f5576c; }
            50% { color: #667eea; }
        }
        
        .connect-section {
            margin: 30px 0;
            text-align: center;
            animation: slideInLeft 1s ease 1s both;
        }
        
        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .connect-btn {
            display: inline-block;
            margin: 10px;
            padding: 15px 30px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            position: relative;
            overflow: hidden;
        }
        
        .connect-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(255,255,255,0.2), transparent);
            transition: left 0.6s;
        }
        
        .connect-btn:hover::before {
            left: 100%;
        }
        
        .connect-btn:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.6);
        }
        
        .fun-fact {
            background: linear-gradient(135deg, #ffeaa7, #fab1a0);
            padding: 25px;
            border-radius: 15px;
            margin: 30px 0;
            font-style: italic;
            position: relative;
            overflow: hidden;
            cursor: pointer;
            animation: bounceIn 1.2s ease 1.6s both;
        }
        
        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
            70% {
                transform: scale(0.9);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }
        
        .fun-fact::before {
            content: '🎯';
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 30px;
            animation: spin 3s linear infinite;
        }
        
        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .skills-title {
            font-size: 28px;
            margin: 40px 0 20px 0;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-align: center;
            animation: slideInRight 1s ease 1.8s both;
        }
        
        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 20px;
            margin: 30px 0;
            animation: zoomIn 1s ease 2s both;
        }
        
        @keyframes zoomIn {
            from {
                opacity: 0;
                transform: scale(0.5);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }
        
        .skill-item {
            text-align: center;
            padding: 20px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }
        
        .skill-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 100%;
            background: linear-gradient(45deg, #667eea, #764ba2);
            transition: width 0.4s ease;
            z-index: 1;
        }
        
        .skill-item:hover::before {
            width: 100%;
        }
        
        .skill-item:hover {
            transform: translateY(-15px) rotateY(10deg);
            box-shadow: 0 25px 50px rgba(102, 126, 234, 0.4);
        }
        
        .skill-item img {
            width: 50px;
            height: 50px;
            transition: all 0.4s ease;
            position: relative;
            z-index: 2;
        }
        
        .skill-item:hover img {
            transform: scale(1.2) rotateZ(360deg);
            filter: brightness(0) invert(1);
        }
        
        .skill-name {
            margin-top: 10px;
            font-weight: 600;
            position: relative;
            z-index: 2;
            color: #333;
            transition: color 0.4s ease;
        }
        
        .skill-item:hover .skill-name {
            color: white;
        }
        
        .stats-section {
            margin: 50px 0;
            animation: fadeIn 1.5s ease 2.4s both;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin: 30px 0;
        }
        
        .stat-card {
            background: white;
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.1);
            transition: all 0.5s ease;
            position: relative;
            overflow: hidden;
        }
        
        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb, #f5576c);
            background-size: 300% 300%;
            animation: gradientShift 3s ease infinite;
        }
        
        .stat-card:hover {
            transform: translateY(-20px) rotateX(5deg);
            box-shadow: 0 40px 80px rgba(102, 126, 234, 0.3);
        }
        
        .stat-card img {
            width: 100%;
            height: auto;
            border-radius: 10px;
            transition: all 0.3s ease;
        }
        
        .stat-card:hover img {
            transform: scale(1.02);
        }
        
        .emoji {
            display: inline-block;
            animation: bounce 2s ease-in-out infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }
        
        .highlight-box {
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(245, 87, 108, 0.1));
            border-left: 4px solid #667eea;
            padding: 20px;
            margin: 20px 0;
            border-radius: 0 15px 15px 0;
            animation: slideInFromLeft 1s ease forwards;
            transform: translateX(-100px);
            opacity: 0;
        }
        
        @keyframes slideInFromLeft {
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="typing-text highlight-box">
            <span class="emoji">🚀</span> I'm currently enhancing my expertise in 
            <span class="rotating-skills" id="currentSkill">test automation</span> 
            while pursuing industry-recognized certifications to stay ahead in the world of software testing.
        </div>

        <div class="typing-text highlight-box">
            <span class="emoji">💡</span> Ask me about 
            <span class="dynamic-text" onclick="showSkillDialog()">automation testing, test strategies or improving software quality.</span>
        </div>

        <div class="connect-section">
            <a href="https://www.linkedin.com/in/aarishirfan/" target="_blank" class="connect-btn" onclick="trackClick('linkedin')">
                📱 Connect on LinkedIn
            </a>
            <a href="mailto:arishirfan98@gmail.com" class="connect-btn" onclick="trackClick('email')">
                ✉️ Send me an Email
            </a>
        </div>

        <div class="fun-fact" onclick="showRandomFact()">
            <span class="emoji">🎮</span> I love exploring new testing tools and techniques, but I also enjoy solving puzzles and logic games in my free time!
            <div style="font-size: 12px; margin-top: 10px; opacity: 0.7;">Click for a random testing fact!</div>
        </div>

        <h3 class="skills-title">🛠️ Languages and Tools</h3>

        <div class="skills-grid">
            <div class="skill-item" onclick="showSkillInfo('C#', 'Expert in C# for building robust test automation frameworks')">
                <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg" alt="C#">
                <div class="skill-name">C#</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Git', 'Version control master for collaborative testing projects')">
                <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="Git">
                <div class="skill-name">Git</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Java', 'Building enterprise-level test suites with Java')">
                <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java">
                <div class="skill-name">Java</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Jenkins', 'CI/CD pipeline automation and continuous testing')">
                <img src="https://www.vectorlogo.zone/logos/jenkins/jenkins-icon.svg" alt="Jenkins">
                <div class="skill-name">Jenkins</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Kibana', 'Data visualization and test analytics dashboard')">
                <img src="https://www.vectorlogo.zone/logos/elasticco_kibana/elasticco_kibana-icon.svg" alt="Kibana">
                <div class="skill-name">Kibana</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('MySQL', 'Database testing and data validation expert')">
                <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="MySQL">
                <div class="skill-name">MySQL</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Postman', 'API testing and automation specialist')">
                <img src="https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg" alt="Postman">
                <div class="skill-name">Postman</div>
            </div>
            <div class="skill-item" onclick="showSkillInfo('Selenium', 'Web automation testing champion')">
                <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/selenium-logo.svg" alt="Selenium">
                <div class="skill-name">Selenium</div>
            </div>
        </div>

        <div class="stats-section">
            <h3 class="skills-title">📊 Live GitHub Statistics</h3>
            <div class="stats-grid">
                <div class="stat-card">
                    <img id="langStats" src="https://github-readme-stats.vercel.app/api/top-langs?username=aarishirfan&show_icons=true&locale=en&layout=compact&theme=radical" alt="Top Languages">
                </div>
                <div class="stat-card">
                    <img id="githubStats" src="https://github-readme-stats.vercel.app/api?username=aarishirfan&show_icons=true&locale=en&theme=radical" alt="GitHub Stats">
                </div>
            </div>
            <div style="text-align: center; margin-top: 20px; opacity: 0.7; font-size: 14px;">
                📈 Stats auto-refresh every 30 seconds
            </div>
        </div>
    </div>

    <script>
        // Dynamic skill rotation
        const skills = [
            "test automation",
            "quality assurance", 
            "API testing",
            "performance testing",
            "CI/CD integration",
            "test strategy",
            "automation frameworks"
        ];
        let currentSkillIndex = 0;

        function rotateSkills() {
            const skillElement = document.getElementById('currentSkill');
            currentSkillIndex = (currentSkillIndex + 1) % skills.length;
            
            // Fade out
            skillElement.style.opacity = '0';
            skillElement.style.transform = 'translateY(-20px)';
            
            setTimeout(() => {
                skillElement.textContent = skills[currentSkillIndex];
                skillElement.style.opacity = '1';
                skillElement.style.transform = 'translateY(0)';
            }, 300);
        }

        // Rotate skills every 3 seconds
        setInterval(rotateSkills, 3000);

        // Dynamic skill info display
        function showSkillInfo(skill, description) {
            const modal = document.createElement('div');
            modal.style.cssText = `
                position: fixed;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: rgba(0,0,0,0.8);
                display: flex;
                align-items: center;
                justify-content: center;
                z-index: 1000;
                animation: fadeIn 0.3s ease;
            `;
            
            modal.innerHTML = `
                <div style="
                    background: white;
                    padding: 40px;
                    border-radius: 20px;
                    text-align: center;
                    max-width: 400px;
                    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
                    animation: slideInUp 0.3s ease;
                ">
                    <h3 style="color: #667eea; margin-bottom: 20px; font-size: 24px;">🎯 ${skill}</h3>
                    <p style="color: #333; line-height: 1.6; margin-bottom: 30px;">${description}</p>
                    <button onclick="this.parentElement.parentElement.remove()" style="
                        background: linear-gradient(45deg, #667eea, #764ba2);
                        color: white;
                        border: none;
                        padding: 12px 30px;
                        border-radius: 25px;
                        cursor: pointer;
                        font-weight: 600;
                        transition: all 0.3s ease;
                    " onmouseover="this.style.transform='scale(1.05)'" onmouseout="this.style.transform='scale(1)'">
                        Got it! 👍
                    </button>
                </div>
            `;
            
            document.body.appendChild(modal);
            
            // Add click outside to close
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    modal.remove();
                }
            });
        }

        // Random testing facts
        const testingFacts = [
            "🐛 The first computer bug was literally a bug - a moth trapped in a relay!",
            "🚀 NASA's software testing process is so rigorous, they have a 99.9% success rate!",
            "⚡ Automated testing can run 24/7, while manual testing needs coffee breaks!",
            "🎯 Good test automation can reduce testing time by up to 90%!",
            "🔍 The average software has 15-20 bugs per 1000 lines of code!",
            "💡 Test-driven development can reduce bug rates by up to 80%!",
            "🌟 A single critical bug fix can save companies millions of dollars!"
        ];

        function showRandomFact() {
            const randomFact = testingFacts[Math.floor(Math.random() * testingFacts.length)];
            const factElement = document.querySelector('.fun-fact');
            
            // Create notification
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background: linear-gradient(45deg, #667eea, #764ba2);
                color: white;
                padding: 20px;
                border-radius: 15px;
                box-shadow: 0 20px 40px rgba(0,0,0,0.2);
                z-index: 1000;
                max-width: 300px;
                animation: slideInFromRight 0.5s ease;
            `;
            notification.innerHTML = `
                <div style="font-weight: 600; margin-bottom: 10px;">💡 Testing Fact</div>
                <div style="font-size: 14px; line-height: 1.4;">${randomFact}</div>
            `;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.animation = 'slideOutToRight 0.5s ease forwards';
                setTimeout(() => notification.remove(), 500);
            }, 4000);
        }

        // Add CSS for notification animations
        const style = document.createElement('style');
        style.textContent = `
            @keyframes slideInFromRight {
                from {
                    transform: translateX(100%);
                    opacity: 0;
                }
                to {
                    transform: translateX(0);
                    opacity: 1;
                }
            }
            @keyframes slideOutToRight {
                from {
                    transform: translateX(0);
                    opacity: 1;
                }
                to {
                    transform: translateX(100%);
                    opacity: 0;
                }
            }
            @keyframes slideInUp {
                from {
                    transform: translateY(50px);
                    opacity: 0;
                }
                to {
                    transform: translateY(0);
                    opacity: 1;
                }
            }
        `;
        document.head.appendChild(style);

        // Skill dialog
        function showSkillDialog() {
            const skills = [
                "🎯 Test Automation Strategy",
                "🚀 CI/CD Integration", 
                "🔍 API Testing Excellence",
                "📊 Performance Testing",
                "🛡️ Security Testing",
                "📱 Mobile App Testing"
            ];
            
            const skillsList = skills.map(skill => `<li style="margin: 10px 0; color: #667eea;">${skill}</li>`).join('');
            
            const modal = document.createElement('div');
            modal.style.cssText = `
                position: fixed;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: rgba(0,0,0,0.8);
                display: flex;
                align-items: center;
                justify-content: center;
                z-index: 1000;
                animation: fadeIn 0.3s ease;
            `;
            
            modal.innerHTML = `
                <div style="
                    background: white;
                    padding: 40px;
                    border-radius: 20px;
                    text-align: center;
                    max-width: 500px;
                    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
                    animation: slideInUp 0.3s ease;
                ">
                    <h3 style="color: #667eea; margin-bottom: 20px;">💡 My Expertise Areas</h3>
                    <ul style="text-align: left; margin: 20px 0;">${skillsList}</ul>
                    <p style="color: #666; margin: 20px 0;">Ready to discuss how I can help improve your testing processes?</p>
                    <button onclick="this.parentElement.parentElement.remove()" style="
                        background: linear-gradient(45deg, #667eea, #764ba2);
                        color: white;
                        border: none;
                        padding: 12px 30px;
                        border-radius: 25px;
                        cursor: pointer;
                        font-weight: 600;
                        margin: 10px;
                    ">Let's Talk! 🚀</button>
                </div>
            `;
            
            document.body.appendChild(modal);
            modal.addEventListener('click', (e) => {
                if (e.target === modal) modal.remove();
            });
        }

        // Click tracking
        function trackClick(platform) {
            console.log(`📊 User clicked: ${platform}`);
            
            // Show success message
            const message = document.createElement('div');
            message.style.cssText = `
                position: fixed;
                bottom: 20px;
                right: 20px;
                background: linear-gradient(45deg, #00c851, #007e33);
                color: white;
                padding: 15px 25px;
                border-radius: 15px;
                z-index: 1000;
                animation: slideInFromRight 0.5s ease;
            `;
            message.textContent = `✅ Opening ${platform}...`;
            
            document.body.appendChild(message);
            setTimeout(() => message.remove(), 2000);
        }

        // Auto-refresh GitHub stats every 30 seconds
        function refreshStats() {
            const timestamp = Date.now();
            const langStats = document.getElementById('langStats');
            const githubStats = document.getElementById('githubStats');
            
            // Add loading effect
            [langStats, githubStats].forEach(img => {
                img.style.filter = 'blur(2px)';
                img.style.opacity = '0.7';
            });
            
            setTimeout(() => {
                langStats.src = `https://github-readme-stats.vercel.app/api/top-langs?username=aarishirfan&show_icons=true&locale=en&layout=compact&theme=radical&t=${timestamp}`;
                githubStats.src = `https://github-readme-stats.vercel.app/api?username=aarishirfan&show_icons=true&locale=en&theme=radical&t=${timestamp}`;
                
                // Remove loading effect
                setTimeout(() => {
                    [langStats, githubStats].forEach(img => {
                        img.style.filter = 'none';
                        img.style.opacity = '1';
                    });
                }, 1000);
            }, 500);
        }

        // Refresh stats every 30 seconds
        setInterval(refreshStats, 30000);

        // Initialize on page load
        document.addEventListener('DOMContentLoaded', function() {
            console.log('🚀 Dynamic profile loaded successfully!');
            
            // Add some entrance effects
            setTimeout(() => {
                document.querySelectorAll('.skill-item').forEach((item, index) => {
                    setTimeout(() => {
                        item.style.transform = 'scale(1.1)';
                        setTimeout(() => {
                            item.style.transform = 'scale(1)';
                        }, 200);
                    }, index * 100);
                });
            }, 3000);
        });

        // Add mouse trail effect
        let mouseTrail = [];
        document.addEventListener('mousemove', (e) => {
            mouseTrail.push({x: e.clientX, y: e.clientY, time: Date.now()});
            
            if (mouseTrail.length > 20) {
                mouseTrail.shift();
            }
            
            // Remove old trail points
            mouseTrail = mouseTrail.filter(point => Date.now() - point.time < 500);
        });
    </script>
</body>
</html>
