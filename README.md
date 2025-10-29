<!-- 将以下完整代码复制到 https://html-pastebin.com/ 或类似服务 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I Choose You</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', sans-serif; background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%); color: white; min-height: 100vh; overflow: hidden; display: flex; justify-content: center; align-items: center; }
        .container { text-align: center; z-index: 10; position: relative; }
        h1 { font-size: 5rem; margin-bottom: 20px; text-shadow: 0 0 15px rgba(255, 105, 180, 0.7); animation: pulse 3s infinite ease-in-out; letter-spacing: 2px; background: linear-gradient(45deg, #ff69b4, #ff1493, #ff69b4); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-size: 200% 200%; animation: gradient 4s ease infinite, pulse 3s infinite ease-in-out; }
        .hearts-container { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 1; }
        .heart { position: absolute; width: 20px; height: 20px; background: linear-gradient(45deg, #ff69b4, #ff1493); transform: rotate(45deg); opacity: 0; animation: float 8s infinite ease-in-out; }
        .heart:before, .heart:after { content: ''; width: 20px; height: 20px; background: inherit; border-radius: 50%; position: absolute; }
        .heart:before { top: -10px; left: 0; }
        .heart:after { top: 0; left: -10px; }
        .sparkle { position: absolute; width: 4px; height: 4px; background-color: white; border-radius: 50%; animation: sparkle 3s infinite; }
        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.05); } 100% { transform: scale(1); } }
        @keyframes float { 0% { transform: translateY(100vh) rotate(45deg) scale(0.5); opacity: 0; } 10% { opacity: 0.8; } 90% { opacity: 0.7; } 100% { transform: translateY(-100px) rotate(45deg) scale(1.2); opacity: 0; } }
        @keyframes sparkle { 0% { opacity: 0; transform: scale(0); } 50% { opacity: 1; transform: scale(1); } 100% { opacity: 0; transform: scale(0); } }
        @keyframes gradient { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }
        @media (max-width: 768px) { h1 { font-size: 3rem; } }
    </style>
</head>
<body>
    <div class="hearts-container" id="heartsContainer"></div>
    <div class="container"><h1>I Choose You</h1></div>
    <script>
        function createHearts(count) { const container = document.getElementById('heartsContainer'); for (let i = 0; i < count; i++) { const heart = document.createElement('div'); heart.classList.add('heart'); const left = Math.random() * 100; heart.style.left = `${left}vw`; const size = Math.random() * 20 + 15; heart.style.width = `${size}px`; heart.style.height = `${size}px`; const delay = Math.random() * 6; heart.style.animationDelay = `${delay}s`; const hue = Math.random() * 30 + 320; heart.style.background = `linear-gradient(45deg, hsl(${hue}, 100%, 65%), hsl(${hue}, 100%, 55%))`; container.appendChild(heart); } }
        function createSparkles() { const container = document.getElementById('heartsContainer'); setInterval(() => { const sparkle = document.createElement('div'); sparkle.classList.add('sparkle'); sparkle.style.left = `${Math.random() * 100}vw`; sparkle.style.top = `${Math.random() * 100}vh`; const size = Math.random() * 3 + 2; sparkle.style.width = `${size}px`; sparkle.style.height = `${size}px`; const delay = Math.random() * 3; sparkle.style.animationDelay = `${delay}s`; container.appendChild(sparkle); setTimeout(() => { sparkle.remove(); }, 3000); }, 300); }
        createHearts(25); createSparkles(); setInterval(() => { createHearts(5); }, 3000);
    </script>
</body>
</html>
