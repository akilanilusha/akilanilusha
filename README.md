<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Loading Page</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #0d1117;
            color: #c9d1d9;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        
        .loading-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 20vh;
        }

        .github-logo {
            width: 80px;
            height: 80px;
            animation: spin 1.5s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .intro {
            margin-top: 20px;
            font-size: 1.2rem;
        }

        .chart-container {
            margin-top: 30px;
        }

        .contributions {
            display: grid;
            grid-template-columns: repeat(52, 12px);
            gap: 2px;
            justify-content: center;
        }

        .day {
            width: 12px;
            height: 12px;
            background-color: #161b22;
            border-radius: 2px;
            transition: background-color 0.5s ease-in-out;
        }

        .level-1 { background-color: #0e4429; }
        .level-2 { background-color: #006d32; }
        .level-3 { background-color: #26a641; }
        .level-4 { background-color: #39d353; }

        /* Skills Section */
        .skills-container {
            margin-top: 30px;
            text-align: left;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .skill {
            margin: 10px 0;
        }

        .skill-name {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .skill-bar {
            height: 10px;
            width: 100%;
            background-color: #161b22;
            border-radius: 5px;
            overflow: hidden;
            position: relative;
        }

        .skill-fill {
            height: 100%;
            background-color: #39d353;
            width: 0%;
            transition: width 2s ease-in-out;
        }

        /* Visitor Counter */
        .visitor-counter {
            margin-top: 30px;
            font-size: 1.2rem;
        }
    </style>
</head>
<body>

    <div class="loading-container">
        <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="GitHub Logo" class="github-logo">
    </div>

    <div class="intro">
        <h1>Hello, I'm Akila Nilusha 👋</h1>
        <p>💻 Undergraduate CS Student @ University of Ruhuna</p>
        <p>🚀 Web & Software Developer | DevOps Enthusiast</p>
        <p>⚡ Passionate about new technologies & challenges</p>
    </div>

    <div class="chart-container">
        <h2>My GitHub Contributions</h2>
        <div class="contributions"></div>
    </div>

    <div class="skills-container">
        <h2>My Skills</h2>

        <div class="skill">
            <div class="skill-name">React</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 90%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">CodeIgniter</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 85%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">Laravel</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 88%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">Flutter</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 80%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">PHP</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 92%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">SQL</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 87%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">Node.js</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 75%;"></div></div>
        </div>

        <div class="skill">
            <div class="skill-name">Python</div>
            <div class="skill-bar"><div class="skill-fill" style="width: 83%;"></div></div>
        </div>
    </div>

    <div class="visitor-counter">
        👀 Visitors: <span id="visitor-count">Loading...</span>
    </div>

    <script>
        function generateContributions() {
            const contributions = document.querySelector('.contributions');
            const weeks = 52;
            const daysPerWeek = 7;
            contributions.innerHTML = '';

            for (let i = 0; i < weeks * daysPerWeek; i++) {
                let div = document.createElement('div');
                div.classList.add('day');
                setTimeout(() => {
                    div.classList.add(getRandomContributionLevel());
                }, i * 15);
                contributions.appendChild(div);
            }
        }

        function getRandomContributionLevel() {
            const levels = ['', 'level-1', 'level-2', 'level-3', 'level-4'];
            return levels[Math.floor(Math.random() * levels.length)];
        }

        function animateSkills() {
            const skillFills = document.querySelectorAll('.skill-fill');
            skillFills.forEach(fill => {
                const width = fill.style.width;
                fill.style.width = '0%';
                setTimeout(() => {
                    fill.style.width = width;
                }, 500);
            });
        }

        function updateVisitorCount() {
            const visitorCount = localStorage.getItem("visitor_count") || 0;
            const newCount = parseInt(visitorCount) + 1;
            localStorage.setItem("visitor_count", newCount);
            document.getElementById("visitor-count").innerText = newCount;
        }

        window.onload = function() {
            generateContributions();
            animateSkills();
            updateVisitorCount();
        };
    </script>

</body>
</html>
