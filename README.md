<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔥 FF PRO TRAINING HUB v2.0</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap');
        
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: linear-gradient(-45deg, #ff0000, #ff6600, #ffaa00, #ffff00);
            background-size: 400% 400%;
            animation: gradientShift 8s ease infinite;
            font-family: 'Orbitron', monospace;
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
        }
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .particles {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none; z-index: 1;
        }
        .particle {
            position: absolute; width: 4px; height: 4px; 
            background: #fff; border-radius: 50%;
            animation: float 6s infinite linear;
        }
        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
        }
        
        .container { 
            max-width: 1400px; margin: 0 auto; padding: 20px; 
            position: relative; z-index: 2;
        }
        .header {
            text-align: center; margin: 30px 0;
            text-shadow: 0 0 20px #ff4444;
        }
        h1 { 
            font-size: 4.5em; font-weight: 900; 
            background: linear-gradient(45deg, #fff, #ffaa00);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            animation: glow 2s ease-in-out infinite alternate;
        }
        @keyframes glow {
            from { filter: drop-shadow(0 0 10px #ff4444); }
            to { filter: drop-shadow(0 0 30px #ffaa00); }
        }
        
        .stats-global {
            display: flex; justify-content: center; gap: 30px; margin: 20px 0;
            font-size: 1.5em; font-weight: 700;
        }
        .stat { 
            background: rgba(0,0,0,0.7); padding: 15px 25px; 
            border-radius: 50px; border: 2px solid #fff;
            box-shadow: 0 0 20px rgba(255,255,255,0.3);
        }
        
        .grid { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(420px, 1fr)); 
            gap: 30px; margin: 40px 0;
        }
        .card { 
            background: rgba(0,0,0,0.9); 
            padding: 30px; border-radius: 25px; 
            border: 3px solid transparent;
            background-clip: padding-box;
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
        }
        .card::before {
            content: ''; position: absolute; top: -50%; left: -50%;
            width: 200%; height: 200%; background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            transform: rotate(45deg); transition: all 0.6s;
        }
        .card:hover::before { transform: rotate(45deg) translateX(100%) translateY(100%); }
        .card:hover { 
            transform: translateY(-15px) scale(1.02); 
            border-color: #ff4444;
            box-shadow: 0 30px 60px rgba(255,68,68,0.4);
        }
        
        .card h2 { 
            font-size: 2em; margin-bottom: 20px; 
            background: linear-gradient(45deg, #ff4444, #ffaa00);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        
        canvas { 
            border: 4px solid #fff; border-radius: 20px; 
            background: linear-gradient(135deg, #111, #333);
            display: block; margin: 20px auto;
            box-shadow: 0 10px 30px rgba(0,0,0,0.7);
        }
        
        .btn-neon {
            background: linear-gradient(45deg, #ff4444, #ff8800);
            color: white; border: none; padding: 15px 30px; 
            border-radius: 50px; font-size: 18px; font-weight: 700;
            cursor: pointer; margin: 10px; position: relative;
            overflow: hidden; transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(255,68,68,0.4);
        }
        .btn-neon:hover {
            transform: translateY(-3px); box-shadow: 0 10px 25px rgba(255,68,68,0.6);
        }
        .btn-neon:active { transform: translateY(-1px); }
        
        .input-group { 
            margin: 20px 0; text-align: center;
        }
        input, select { 
            padding: 12px 20px; border-radius: 25px; 
            border: 2px solid #fff; background: rgba(255,255,255,0.1);
            color: #fff; font-size: 16px; width: 250px;
            backdrop-filter: blur(10px);
        }
        input:focus, select:focus { outline: none; border-color: #ff4444; box-shadow: 0 0 20px rgba(255,68,68,0.5); }
        
        .results { 
            margin-top: 20px; padding: 20px; 
            background: rgba(255,255,255,0.1); border-radius: 15px;
            backdrop-filter: blur(10px); font-size: 1.2em;
        }
        
        .mobile-warning {
            background: rgba(0,0,0,0.9); padding: 20px; border-radius: 15px;
            text-align: center; margin: 20px 0; border-left: 5px solid #ff4444;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2.5em; }
            .grid { grid-template-columns: 1fr; }
            canvas { width: 100%; height: auto; }
        }
    </style>
</head>
<body>
    <!-- PARTICLE SYSTEM -->
    <div class="particles" id="particles"></div>
    
    <div class="container">
        <div class="header">
            <h1>🔥 FF PRO TRAINING</h1>
            <p style="font-size: 1.4em; margin-top: 10px;">Legal Skill Training • No Bot • Pure Pro Practice 🏆</p>
        </div>
        
        <div class="stats-global">
            <div class="stat">🎯 Total Score: <span id="globalScore">0</span></div>
            <div class="stat">⚡ Best Acc: <span id="globalAcc">0%</span></div>
            <div class="stat">🏆 Sessions: <span id="globalSessions">0</span></div>
        </div>
        
        <div class="grid">
            <!-- AIM TRAINER ULTRA -->
            <div class="card">
                <h2>🎯 ULTRA AIM TRAINER</h2>
                <canvas id="aimCanvas" width="450" height="350"></canvas>
                <div style="text-align: center;">
                    <div class="stats">
                        Score: <span id="aimScore">0</span> | 
                        Acc: <span id="aimAcc">0%</span> | 
                        Speed: <span id="aimSpeed">Normal</span>
                    </div>
                    <button class="btn-neon" onclick="startAimTrainer()">🚀 START TRAINING</button>
                    <button class="btn-neon" onclick="resetAimTrainer()">🔄 RESET</button>
                    <select id="difficulty" onchange="setDifficulty()">
                        <option value="easy">🐣 Easy</option>
                        <option value="normal" selected>⚡ Normal</option>
                        <option value="hard">💀 Hard</option>
                        <option value="pro">👑 PRO</option>
                    </select>
                </div>
            </div>
            
            <!-- SENSITIVITY CALCULATOR PRO -->
            <div class="card">
                <h2>⚙️ PRO SENSITIVITY</h2>
                <div class="input-group">
                    <input type="number" id="dpi" value="400" min="100" max="2000" placeholder="DPI">
                    <label style="font-size: 0.9em;">Mouse/HP DPI</label>
                </div>
                <div class="input-group">
                    <label>General: <input type="range" id="general" min="0" max="100" value="85"><span id="genVal">85</span>%</label>
                </div>
                <div class="input-group">
                    <label>Red Dot: <input type="range" id="reddot" min="0" max="100" value="75"><span id="rdVal">75</span>%</label>
                </div>
                <div class="input-group">
                    <label>2x Scope: <input type="range" id="scope2" min="0" max="100" value="65"><span id="s2Val">65</span>%</label>
                </div>
                <button class="btn-neon" onclick="calcProSensi()">🎮 GENERATE PRO CONFIG</button>
                <div id="sensiResult" class="results"></div>
            </div>
            
            <!-- GLOO WALL SIMULATOR -->
            <div class="card">
                <h2>🧱 GLOO WALL SIM</h2>
                <canvas id="glooCanvas" width="450" height="350"></canvas>
                <div style="text-align: center;">
                    <div class="stats">
                        Walls: <span id="wallsPlaced">0</span> | 
                        Perfect: <span id="perfectWalls">0</span>
                    </div>
                    <button class="btn-neon" onclick="startGlooSim()">🎯 PRACTICE</button>
                    <button class="btn-neon" onclick="resetGloo()">RESET</button>
                    <p style="font-size: 0.9em; opacity: 0.8;">Click to place perfect gloo walls!</p>
                </div>
            </div>
            
            <!-- ROOM ID GENERATOR -->
            <div class="card">
                <h2>📱 CUSTOM ROOM FINDER</h2>
                <div class="input-group">
                    <input type="text" id="roomId" placeholder="Masukkan Room ID">
                    <button class="btn-neon" onclick="joinRoom()">🚪 JOIN ROOM</button>
                </div>
                <div id="roomInfo" class="results">
                    <h3>Quick Rooms</h3>
                    <div style="font-size: 1.1em; line-height: 2;">
                        - TDM: 1234-5678-9012<br>
                        - CS: 9876-5432-1098<br>
                        - 1v1: 1111-2222-3333
                    </div>
                </div>
            </div>
        </div>
        
        <div class="mobile-warning">
            <strong>📱 Mobile OK!</strong> Zoom out jika perlu. Semua fitur work di HP!
        </div>
    </div>

    <script>
        // PARTICLE SYSTEM
        function createParticles() {
            const particles = document.getElementById('particles');
            setInterval(() => {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
                particle.style.animationDelay = Math.random() * 2 + 's';
                particles.appendChild(particle);
                setTimeout(() => particle.remove(), 6000);
            }, 300);
        }
        createParticles();
        
        // GLOBAL STATS
        let globalScore = 0, globalSessions = 0;
        function updateGlobalStats(score, acc) {
            globalScore += score;
            globalSessions++;
            document.getElementById('globalScore').textContent = globalScore;
            document.getElementById('globalAcc').textContent = Math.max(acc, parseInt(document.getElementById('globalAcc').textContent) || 0) + '%';
            document.getElementById('globalSessions').textContent = globalSessions;
        }
        
        // AIM TRAINER
        let targets = [], aimScore = 0, aimHits = 0, aimShots = 0, difficulty = 1000;
        const aimCtx = document.getElementById('aimCanvas').getContext('2d');
        
        function drawAim() {
            aimCtx.clearRect(0, 0, 450, 350);
            targets.forEach((target, i) => {
                aimCtx.fillStyle = target.hit ? '#00ff00' : '#ff4444';
                aimCtx.beginPath();
                aimCtx.arc(target.x, target.y, target.size, 0, Math.PI * 2);
                aimCtx.fill();
                aimCtx.strokeStyle = '#fff';
                aimCtx.lineWidth = 3;
                aimCtx.stroke();
            });
        }
        
        function spawnTarget() {
            targets.push({
                x: Math.random() * 430 + 10,
                y: Math.random() * 330 + 10,
                size: 25 + Math.random() * 15,
                hit: false,
                life: difficulty
            });
        }
        
        document.getElementById('aimCanvas').addEventListener('click', (e) => {
            const rect = e.target.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;
            
            for (let i = targets.length - 1; i >= 0; i--) {
                const target = targets[i];
                const dist = Math.sqrt((x - target.x)**2 + (y - target.y)**2);
                if (dist < target.size) {
                    target.hit = true;
                    aimScore += 100;
                    aimHits++;
                    break;
                }
            }
            aimShots++;
            updateAimStats();
            drawAim();
        });
        
        function startAimTrainer() {
            aimScore = aimHits = aimShots = 0;
            targets = [];
            setInterval(spawnTarget, difficulty);
            const interval = setInterval(() => {
                targets = targets.filter(t => t.life-- > 0);
                targets.forEach(t => t.life--);
                drawAim();
                updateAimStats();
                if (targets.length === 0) clearInterval(interval);
            }, 50);
        }
        
        function updateAimStats() {
            document.getElementById('aimScore').textContent = aimScore;
            const acc = aimShots ? Math.round((aimHits / aimShots) * 100) : 0;
            document.getElementById('aimAcc').textContent = acc + '%';
            document.getElementById('aimSpeed').textContent = ['Easy', 'Normal', 'Hard', 'PRO'][['easy','normal','hard','pro'].indexOf(difficulty)];
        }
        
        function setDifficulty() {
            const diff = document.getElementById('difficulty').value;
            difficulty = {easy: 1500, normal: 1000, hard: 700, pro: 400}[diff];
        }
        
        function resetAimTrainer() {
            aimScore = aimHits = aimShots = 0;
            targets = [];
            drawAim();
            updateAimStats();
        }
        
        // SENSITIVITY CALCULATOR
        document.querySelectorAll('input[type="range"]').forEach(range => {
            range.addEventListener('input', function() {
                document.getElementById(this.id.replace('general','genVal').replace('reddot','rdVal').replace('scope2','s2Val')).textContent = this.value;
            });
        });
        
        function calcProSensi() {
            const dpi = document.getElementById('dpi').value;
            const general = document.getElementById('general').value;
            const reddot = document.getElementById('reddot').value;
            const scope2 = document.getElementById('scope2').value;
            
            const result = document.getElementById('sensiResult');
            result.innerHTML = `
                <h3>🎮 PRO CONFIG (${dpi} DPI)</h3>
                <div style="font-family: monospace; font-size: 1.3em; line-height: 2;">
                    General: <strong>${general}%</strong><br>
                    Red Dot: <strong>${reddot}%</strong><br>
                    2x Scope: <strong>${scope2}%</strong><br>
                    4x Scope: <strong>${Math.round(scope2 * 0.85)}%</strong><br>
                    Sniper: <strong>${Math.round(general * 0.6)}%</strong><br
