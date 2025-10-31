<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Book of Love — For Impu ❤️</title>
  <style>
    :root {
      --bg: #ffb6c1;
      --neon-pink: #ff69b4;
      --bright-pink: #ff1493;
      --neon-blue: #00d9ff;
    }

    html, body {
      height: 100%;
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: radial-gradient(circle, var(--bg) 20%, #ff85c1 60%, #ff1493 100%);
      overflow: hidden;
      color: #fff;
    }

    canvas#heartsCanvas {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
    }

    .book-wrap {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
      position: relative;
      height: 90vh;
      perspective: 2000px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .page {
      width: 90%;
      height: 80%;
      position: absolute;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(8px);
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
      transition: transform 1s ease-in-out, opacity 0.6s ease-in-out;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 20px;
      transform-origin: left;
    }

    .hidden { opacity: 0; pointer-events: none; transform: rotateY(-180deg); }
    .visible { opacity: 1; transform: rotateY(0deg); }

    h1 {
      font-size: 1.8em;
      color: var(--bright-pink);
      text-shadow: 0 0 15px var(--neon-pink);
    }

    p {
      font-size: 1.1em;
      line-height: 1.6em;
      color: #fff;
      max-height: 60vh;
      overflow-y: auto;
    }

    button {
      background: var(--bright-pink);
      border: none;
      color: white;
      padding: 10px 20px;
      border-radius: 25px;
      margin-top: 20px;
      font-size: 1em;
      cursor: pointer;
      transition: all 0.3s;
    }

    button:hover {
      background: var(--neon-blue);
      box-shadow: 0 0 15px var(--neon-blue);
    }

    @media (max-width: 768px) {
      h1 { font-size: 1.4em; }
      p { font-size: 1em; }
      .book-wrap { height: 95vh; }
    }
  </style>
</head>
<body>
  <canvas id="heartsCanvas"></canvas>

  <div class="book-wrap">
    <div class="page visible" id="page1">
      <h1>Happy Birthday, Impu 💖</h1>
      <p>Hey my love — today is yours. Each heart you see reminds you of one thousand tiny reasons I cherish you. ❤️💙✨</p>
      <button onclick="nextPage(2)">Turn the page 📖</button>
    </div>

    <div class="page hidden" id="page2">
      <h1>To the Queen of my Heart 👑</h1>
      <p>To the Queen of my heart, I wanted to take a moment to express the depth of my feelings for you. You're the sunshine that brightens my days and this message is more than just a few lines on paper — it's a small piece of my heart reaching out to you. Your laughter is a sweet melody that fills my world with happiness and your presence is the gentle warmth that makes everything better. In you I found not just a girlfriend, but my best friend, my confidant, and the one with whom I want to share all of life's adventures. ❤️🌹</p>
      <button onclick="prevPage(1)">Back</button>
      <button onclick="nextPage(3)">Next</button>
    </div>

    <div class="page hidden" id="page3">
      <h1>Just You ✨</h1>
      <p>There was nothing before you, and there is nothing after you. My story begins with your smile, and it ends in your eyes. 💫</p>
      <button onclick="prevPage(2)">Back</button>
      <button onclick="nextPage(4)">Next</button>
    </div>

    <div class="page hidden" id="page4">
      <h1>My Forever Love 💞</h1>
      <p>Happy Birthday to the one who holds my whole heart! My love for you is not a choice I make, but a fundamental truth of who I am. It is unstoppable and unconditional — a force that simply is. No one in this world could ever stop me from loving you. You are my light, my adventure, and my most beautiful dream. 🎂💖🌟</p>
      <button onclick="prevPage(3)">Back</button>
      <button onclick="nextPage(5)">Open the final page</button>
    </div>

    <div class="page hidden" id="page5">
      <h1>Forever Yours, Deepu ❤️</h1>
      <p>This is the place where all my small promises gather — laughter, late-night talks, silly fights, and soft kisses. Today I celebrate you, the beautiful soul who changed everything. Here's to us — to the memories behind and the adventures ahead. I love you more than words can hold. 💗💙🎆</p>
      <button onclick="prevPage(4)">Back</button>
      <button onclick="nextPage(1)">Replay</button>
    </div>
  </div>

  <audio id="bgAudio" loop autoplay>
    <source src="https://www.youtube.com/embed/rIPtyodvaJk?autoplay=1&start=20" type="audio/mpeg">
  </audio>

  <script>
    const pages = document.querySelectorAll('.page');
    let currentPage = 1;

    function showPage(n) {
      pages.forEach((page, i) => {
        page.classList.add('hidden');
        page.classList.remove('visible');
        if (i === n - 1) {
          page.classList.add('visible');
          page.classList.remove('hidden');
        }
      });
      currentPage = n;
    }

    function nextPage(n) { showPage(n); }
    function prevPage(n) { showPage(n); }

    // Falling hearts animation
    const canvas = document.getElementById('heartsCanvas');
    const ctx = canvas.getContext('2d');
    let hearts = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }

    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class Heart {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height - canvas.height;
        this.size = Math.random() * 20 + 10;
        this.speed = Math.random() * 2 + 1;
        this.color = Math.random() > 0.5 ? '#ff1493' : '#ff69b4';
      }
      draw() {
        ctx.beginPath();
        const topCurveHeight = this.size * 0.3;
        ctx.moveTo(this.x, this.y + topCurveHeight);
        ctx.bezierCurveTo(this.x - this.size / 2, this.y - this.size / 2, this.x - this.size, this.y + this.size / 3, this.x, this.y + this.size);
        ctx.bezierCurveTo(this.x + this.size, this.y + this.size / 3, this.x + this.size / 2, this.y - this.size / 2, this.x, this.y + topCurveHeight);
        ctx.fillStyle = this.color;
        ctx.fill();
      }
      update() {
        this.y += this.speed;
        if (this.y > canvas.height + this.size) {
          this.y = -this.size;
          this.x = Math.random() * canvas.width;
        }
        this.draw();
      }
    }

    function createHearts() {
      for (let i = 0; i < 50; i++) {
        hearts.push(new Heart());
      }
    }

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      hearts.forEach(h => h.update());
      requestAnimationFrame(animate);
    }

    createHearts();
    animate();
  </script>
</body>
</html>
