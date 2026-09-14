<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="theme-color" content="#0a0e27">
    <title>Волшебный Шар</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html, body { width: 100%; height: 100%; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; user-select: none; -webkit-user-select: none; touch-action: manipulation; overflow: hidden; }
        .container { width: 100%; height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; position: relative; overflow: hidden; transition: background 0.3s ease; }
        .container.dark { background: #0a0e27; }
        .container.light { background: #f5f5f5; }
        .container.stars { background: #0a0e27; }
        #starsCanvas { position: absolute; top: 0; left: 0; display: none; }
        .container.stars #starsCanvas { display: block; }
        .content { position: relative; z-index: 10; display: flex; flex-direction: column; align-items: center; gap: 40px; }
        .ball-container { width: 280px; height: 280px; cursor: pointer; perspective: 1000px; }
        .ball { width: 100%; height: 100%; border-radius: 50%; background: radial-gradient(circle at 30% 30%, #1a1a1a, #000); box-shadow: 0 20px 60px rgba(0,0,0,0.8), inset -2px -2px 10px rgba(0,0,0,0.5), inset 2px 2px 10px rgba(255,255,255,0.1); display: flex; align-items: center; justify-content: center; position: relative; transform-style: preserve-3d; transition: transform 0.05s; }
        .ball.shake { animation: shake 0.5s ease-in-out; }
        @keyframes shake { 0%, 100% { transform: rotateX(0) rotateY(0) rotateZ(0); } 10% { transform: rotateX(5deg) rotateY(-5deg) rotateZ(3deg); } 20% { transform: rotateX(-5deg) rotateY(5deg) rotateZ(-3deg); } 30% { transform: rotateX(3deg) rotateY(-3deg) rotateZ(4deg); } 40% { transform: rotateX(-4deg) rotateY(4deg) rotateZ(-4deg); } 50% { transform: rotateX(2deg) rotateY(-2deg) rotateZ(2deg); } 60% { transform: rotateX(-2deg) rotateY(2deg) rotateZ(-2deg); } 70% { transform: rotateX(1deg) rotateY(-1deg) rotateZ(1deg); } 80% { transform: rotateX(-1deg) rotateY(1deg) rotateZ(-1deg); } 90% { transform: rotateX(0.5deg) rotateY(-0.5deg) rotateZ(0.5deg); } }
        .inner-circle { width: 200px; height: 200px; border-radius: 50%; background: rgba(0, 0, 0, 0.9); display: flex; align-items: center; justify-content: center; position: relative; }
        .prediction { text-align: center; color: #fff; font-size: 18px; font-weight: 500; line-height: 1.4; padding: 20px; min-height: 80px; display: flex; align-items: center; justify-content: center; animation: fadeIn 0.6s ease-in-out; }
        .prediction.hidden { display: none; }
        @keyframes fadeIn { 0% { opacity: 0; transform: scale(0.8); } 100% { opacity: 1; transform: scale(1); } }
        .prompt { color: #888; font-size: 14px; text-align: center; animation: pulse 2s ease-in-out infinite; }
        @keyframes pulse { 0%, 100% { opacity: 0.6; } 50% { opacity: 1; } }
        .controls { display: flex; gap: 12px; z-index: 20; flex-wrap: wrap; justify-content: center; }
        button { padding: 10px 16px; border: 2px solid; border-radius: 8px; background: transparent; cursor: pointer; font-size: 13px; font-weight: 500; transition: all 0.2s ease; }
        .container.dark button { color: #fff; border-color: #444; }
        .container.light button { color: #000; border-color: #999; }
        .container.stars button { color: #fff; border-color: #444; }
        button:active { transform: scale(0.95); }
        button.active { background: rgba(100, 150, 255, 0.3); border-color: rgba(100, 150, 255, 0.6); }
        .info { position: absolute; bottom: 20px; left: 50%; transform: translateX(-50%); font-size: 12px; color: rgba(255, 255, 255, 0.4); z-index: 5; text-align: center; }
        .container.light .info { color: rgba(0, 0, 0, 0.4); }
    </style>
</head>
<body>
    <canvas id="starsCanvas"></canvas>
    <div class="container dark">
        <div class="content">
            <div class="ball-container" id="ballContainer">
                <div class="ball" id="ball">
                    <div class="inner-circle">
                        <div class="prediction hidden" id="prediction"></div>
                        <div class="prompt" id="prompt">Встряси меня</div>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="active" data-bg="dark">🌙 Темно</button>
                <button data-bg="light">☀️ Светло</button>
                <button data-bg="stars">⭐ Звёзды</button>
            </div>
        </div>
        <div class="info">Встряси телефон или свайпни по шару</div>
    </div>

    <script>
        const PREDICTIONS = {
            good: ['Да, определённо ✨','Твоя удача на пике 🌟','Успех гарантирован 🚀','Вероятность 99% 💎','Всё сложится идеально ⭐','Счастливый день впереди 🎉','Судьба на твоей стороне 💫','Отличная новость скоро 🌈'],
            neutral: ['Похоже, да 👍','Знаки благоприятны ✔️','Возможно, будет хорошо 🤔','Шансы неплохие 💭','Можешь попробовать 🎲'],
            bad: ['Не уверен в этом 😐','Сомневаюсь... 🌫️','Лучше подожди 🛑'],
            verybad: ['Нет, точно не стоит ❌','Судьба против тебя 🌑']
        };
        const allPredictions = [...PREDICTIONS.good,...PREDICTIONS.neutral,...PREDICTIONS.bad,...PREDICTIONS.verybad];
        const container = document.querySelector('.container');
        const ball = document.getElementById('ball');
        const prediction = document.getElementById('prediction');
        const prompt = document.getElementById('prompt');
        const ballContainer = document.getElementById('ballContainer');
        const buttons = document.querySelectorAll('button');
        let isShaking = false;
        let lastShakeTime = 0;
        const SHAKE_COOLDOWN = 800;

        function generateStars() {
            const canvas = document.getElementById('starsCanvas');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            const ctx = canvas.getContext('2d');
            ctx.fillStyle = '#0a0e27';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            const stars = [];
            for (let i = 0; i < 150; i++) {
                stars.push({x: Math.random() * canvas.width, y: Math.random() * canvas.height, radius: Math.random() * 1.5, opacity: Math.random() * 0.7 + 0.3, twinkle: Math.random() * 0.02});
            }
            function drawStars() {
                ctx.fillStyle = '#0a0e27';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                stars.forEach(star => {
                    ctx.fillStyle = `rgba(255, 255, 255, ${star.opacity})`;
                    ctx.beginPath();
                    ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
                    ctx.fill();
                    star.opacity += star.twinkle;
                    if (star.opacity <= 0.2 || star.opacity >= 0.9) {
                        star.twinkle *= -1;
                    }
                });
                requestAnimationFrame(drawStars);
            }
            drawStars();
        }

        function showPrediction() {
            if (Date.now() - lastShakeTime < SHAKE_COOLDOWN || isShaking) return;
            isShaking = true;
            lastShakeTime = Date.now();
            ball.classList.add('shake');
            prompt.style.display = 'none';
            setTimeout(() => {
                const randomPrediction = allPredictions[Math.floor(Math.random() * allPredictions.length)];
                prediction.textContent = randomPrediction;
                prediction.classList.remove('hidden');
            }, 400);
            setTimeout(() => {
                ball.classList.remove('shake');
                isShaking = false;
            }, 500);
        }

        let touchStartX = 0, touchStartY = 0;
        ballContainer.addEventListener('touchstart', (e) => {
            touchStartX = e.touches[0].clientX;
            touchStartY = e.touches[0].clientY;
        });
        ballContainer.addEventListener('touchend', (e) => {
            const diffX = Math.abs(e.changedTouches[0].clientX - touchStartX);
            const diffY = Math.abs(e.changedTouches[0].clientY - touchStartY);
            if (diffX > 30 || diffY > 30) showPrediction();
        });

        let mouseDownX = 0, mouseDownY = 0, isMouseDown = false;
        ballContainer.addEventListener('mousedown', (e) => {
            isMouseDown = true;
            mouseDownX = e.clientX;
            mouseDownY = e.clientY;
        });
        ballContainer.addEventListener('mouseup', (e) => {
            if (!isMouseDown) return;
            isMouseDown = false;
            const diffX = Math.abs(e.clientX - mouseDownX);
            const diffY = Math.abs(e.clientY - mouseDownY);
            if (diffX > 30 || diffY > 30) showPrediction();
        });

        let lastAcceleration = 0;
        if (window.DeviceMotionEvent) {
            window.addEventListener('devicemotion', (event) => {
                if (!event.acceleration) return;
                const x = event.acceleration.x || 0;
                const y = event.acceleration.y || 0;
                const z = event.acceleration.z || 0;
                const acceleration = Math.sqrt(x * x + y * y + z * z);
                if (acceleration > 25 && acceleration - lastAcceleration > 5) {
                    showPrediction();
                }
                lastAcceleration = acceleration;
            });
        }

        buttons.forEach(btn => {
            btn.addEventListener('click', (e) => {
                const theme = e.target.dataset.bg;
                container.className = 'container ' + theme;
                buttons.forEach(b => b.classList.remove('active'));
                e.target.classList.add('active');
                if (theme === 'stars') {
                    generateStars();
                }
            });
        });

        generateStars();
    </script>
</body>
</html>
