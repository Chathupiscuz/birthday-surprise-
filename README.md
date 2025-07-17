<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday Mage Sosa Mala 💖</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
      text-align: center;
      color: white;
    }

    h1, h2, p {
      opacity: 0;
      transform: translateY(20px);
      transition: all 1.5s ease;
    }

    .show {
      opacity: 1 !important;
      transform: translateY(0) !important;
    }

    .container {
      padding: 30px 20px;
      position: relative;
      z-index: 2;
    }

    .heart {
      font-size: 2rem;
      animation: float 2s infinite ease-in-out;
    }

    @keyframes float {
      0% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0); }
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0;
      pointer-events: none;
    }

    audio {
      display: none;
    }
  </style>
</head>
<body>

  <audio autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_9c510c0f36.mp3" type="audio/mpeg">
  </audio>

  <div class="container">
    <h1 id="line1">Hi Mage Sosa Mala 😘💖</h1>
    <h2 id="line2">🎉🥳 Happy Birthday My Beautiful Girl 💕</h2>
    <p id="line3">මගේ සොස මල 💋 — You make my world bloom with love.</p>
    <p id="line4">May your heart overflow with joy, love & kisses 😘</p>
    <p class="heart" id="line5">💖💖💖</p>
    <p id="line6">I love you beyond words 💋</p>
  </div>

  <canvas id="canvas"></canvas>

  <script>
    // Fade-in sequence
    const ids = ["line1", "line2", "line3", "line4", "line5", "line6"];
    ids.forEach((id, i) => {
      setTimeout(() => {
        document.getElementById(id).classList.add('show');
      }, i * 1500);
    });

    // Fireworks/Confetti
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    class Particle {
      constructor(x, y) {
        this.x = x;
        this.y = y;
        this.size = Math.random() * 5 + 2;
        this.color = `hsl(${Math.random() * 360}, 100%, 70%)`;
        this.velocityX = (Math.random() - 0.5) * 8;
        this.velocityY = (Math.random() - 0.5) * 8;
        this.alpha = 1;
      }

      update() {
        this.x += this.velocityX;
        this.y += this.velocityY;
        this.alpha -= 0.01;
      }

      draw() {
        ctx.save();
        ctx.globalAlpha = this.alpha;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fillStyle = this.color;
        ctx.fill();
        ctx.restore();
      }
    }

    const particles = [];

    function explode(x, y) {
      for (let i = 0; i < 50; i++) {
        particles.push(new Particle(x, y));
      }
    }

    setInterval(() => {
      explode(Math.random() * canvas.width, Math.random() * canvas.height / 1.5);
    }, 1000);

    function animate() {
      ctx.fillStyle = "rgba(0,0,0,0.1)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      particles.forEach((p, index) => {
        p.update();
        p.draw();
        if (p.alpha <= 0) particles.splice(index, 1);
      });
      requestAnimationFrame(animate);
    }

    animate();
  </script>

</body>
</html>
