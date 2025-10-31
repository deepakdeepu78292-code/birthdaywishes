<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Book of Love — For Impu ❤️</title>
  <style>
    :root{--bg:#07060a;--neon-blue:#00d9ff;--neon-red:#ff2d95}
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,'Helvetica Neue',Arial;background:radial-gradient(1200px 600px at 10% 10%, rgba(0,0,0,0.25), transparent),var(--bg);color:#fff;overflow:hidden}

    /* App shell */
    .app{height:100vh;display:flex;align-items:center;justify-content:center;position:relative;padding:20px}
    .vignette{position:fixed;inset:0;pointer-events:none;z-index:220;background:radial-gradient(60% 40% at 50% 30%, rgba(255,255,255,0.02), transparent 15%),linear-gradient(180deg, rgba(0,0,0,0.18), rgba(0,0,0,0.55));mix-blend-mode:soft-light}

    /* hearts canvas */
    #heartsCanvas{position:fixed;inset:0;z-index:2;pointer-events:none}

    /* book container (center-open style) */
    .book-wrap{width:min(1100px,96vw);height:min(760px,94vh);position:relative;z-index:10;perspective:2200px}
    .book{width:100%;height:100%;position:relative;transform-style:preserve-3d}

    /* each page is a sheet that flips from its centre (like opening a real book) */
    .page{position:absolute;inset:0;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.22));border-radius:18px;box-shadow:0 18px 60px rgba(0,0,0,0.7);overflow:hidden;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:36px;backdrop-filter: blur(6px);transform-origin:center center;transform:rotateY(0deg);transition:transform 900ms cubic-bezier(.2,.9,.2,1), box-shadow 600ms}
    .page.hidden{opacity:0;pointer-events:none}
    .page.flipping{transform: rotateY(-180deg) translateZ(-30px); box-shadow:0 8px 40px rgba(0,0,0,0.6)}

    /* content */
    .content{width:78%;max-width:880px;margin:0 auto;color:#fff}
    .neon-title{font-size:34px;font-weight:800;letter-spacing:0.6px;background:linear-gradient(90deg,var(--neon-red),var(--neon-blue));-webkit-background-clip:text;background-clip:text;color:transparent;text-shadow:0 8px 30px rgba(0,0,0,0.6)}
    .title{font-weight:700;font-size:22px;margin-bottom:8px}
    .text{font-size:20px;line-height:1.8;white-space:pre-wrap;text-align:left;overflow:auto;max-height:62vh;padding-right:8px}

    /* controls */
    .controls{position:absolute;right:18px;top:18px;display:flex;gap:10px;z-index:240}
    .btn{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.04);padding:10px 14px;border-radius:999px;cursor:pointer;font-weight:600;color:#fff}
    .big{padding:14px 20px}

    .dots{position:absolute;left:18px;top:18px;display:flex;gap:8px;z-index:240}
    .dot{width:10px;height:10px;border-radius:50%;background:rgba(255,255,255,0.06);box-shadow:0 4px 14px rgba(0,0,0,0.5)}
    .dot.active{background:var(--neon-red);box-shadow:0 6px 20px rgba(255,45,149,0.14)}

    .nav{position:absolute;left:50%;transform:translateX(-50%);bottom:18px;display:flex;gap:12px;z-index:240}

    /* final emphasis */
    .final-hero{font-size:28px;font-weight:800;text-align:center}
    .final-hero .big-heart{font-size:72px;margin-top:8px;text-shadow:0 10px 40px rgba(255,45,149,0.15)}

    /* responsive */
    @media (max-width:760px){ .text{font-size:18px} .neon-title{font-size:28px} .book-wrap{height:92vh} }

    /* hidden youtube iframe container */
    #yt-player{display:none; visibility:hidden; width:0; height:0}
  </style>
</head>
<body>
  <!-- hearts and effects -->
  <canvas id="heartsCanvas"></canvas>
  <div id="fireworks" style="position:fixed;inset:0;pointer-events:none;z-index:5"></div>
  <div class="vignette"></div>

  <div class="app">
    <div class="book-wrap" role="main" aria-label="Book of love for Impu">
      <div class="book" id="book">

        <!-- PAGE 1 -->
        <section class="page" data-index="0" id="page-1">
          <div class="content">
            <div class="neon-title">Happy Birthday, Impu 💖</div>
            <div style="height:16px"></div>
            <div class="title">A little surprise — just for you</div>
            <div class="text" id="p1text">Hey my love — today is yours. Close your eyes (not now 😄) and open them when the page flips. I hope each heart you see reminds you of one thousand tiny reasons I cherish you. ❤️💙✨</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn big" id="nextBtn1">Turn the page 📖</button></div>
          </div>
        </section>

        <!-- PAGE 2 -->
        <section class="page hidden" data-index="1" id="page-2">
          <div class="content">
            <div class="neon-title">To the Queen of my Heart 👑</div>
            <div style="height:12px"></div>
            <div class="title">A piece of my heart</div>
            <div class="text" id="p2text">To the Queen of my heart, I wanted to take a moment to express the depth of my feelings for you. You're the sunshine that brightens my days and this message is more than just a few lines on paper — it's a small piece of my heart reaching out to you. Your laughter is a sweet melody that fills my world with happiness and your presence is the gentle warmth that makes everything better. In you I found not just a girlfriend, but my best friend, my confidant, and the one with whom I want to share all of life's adventures. As we navigate the journey of life together, I want you to know how much you mean to me. You bring so much joy, love, and laughter into my life and I cherish every moment we spend together. Here's to the countless memories we've created and to the many more we'll make in the days ahead. ❤️🌹</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn" id="prevBtn2">Back</button><button class="btn" id="nextBtn2">Next</button></div>
          </div>
        </section>

        <!-- PAGE 3 -->
        <section class="page hidden" data-index="2" id="page-3">
          <div class="content">
            <div class="neon-title">Just you ✨</div>
            <div style="height:12px"></div>
            <div class="title">My beginning & my end</div>
            <div class="text" id="p3text">There was nothing before you, and there is nothing after you. My story begins with your smile, and it ends in your eyes. 💫</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn" id="prevBtn3">Back</button><button class="btn" id="nextBtn3">Next</button></div>
          </div>
        </section>

        <!-- PAGE 4 -->
        <section class="page hidden" data-index="3" id="page-4">
          <div class="content">
            <div class="neon-title">My Forever Love 💞</div>
            <div style="height:12px"></div>
            <div class="title">A Birthday Wish for You</div>
            <div class="text" id="p4text">Happy Birthday to the one who holds my whole heart!

My love for you is not a choice I make, but a fundamental truth of who I am. It is unstoppable and unconditional — a force that simply is. No one in this world could ever stop me from loving you.

You are my light, my adventure, and my most beautiful dream. I wish you a birthday filled with as much happiness, warmth, and magic as you bring into my life every single day. 🎂💖🌟</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn" id="prevBtn4">Back</button><button class="btn" id="nextBtn4">Open the final page</button></div>
          </div>
        </section>

        <!-- FINAL PAGE -->
        <section class="page hidden" data-index="4" id="page-5">
          <div class="content">
            <div class="neon-title">Forever Yours, Deepu ❤️</div>
            <div style="height:12px"></div>
            <div class="title">I LOVE YOU, IMPU</div>
            <div class="text" id="p5text">This is the place where all my small promises gather — laughter, late-night talks, silly fights, and soft kisses. Today I celebrate you, the beautiful soul who changed everything. Here's to us — to the memories behind and the adventures ahead. I love you more than words can hold. 💗💙🎆</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn" id="prevBtn5">Back</button><button class="btn" id="replay">Replay</button></div>
          </div>
        </section>

      </div>

      <!-- UI controls -->
      <div class="controls">
        <div class="btn" id="musicBtn">Play Music 🎵</div>
      </div>

      <div class="dots" id="dots"></div>

      <div class="nav">
        <div class="btn" id="prevAll">◀ Back</div>
        <div class="btn big" id="nextAll">Turn Page ▶</div>
      </div>

    </div>
  </div>

  <!-- YouTube player container (hidden) -->
  <div id="yt-player"></div>

  <script>
    /***********************
      HEARTS CANVAS
    ***********************/
    const canvas = document.getElementById('heartsCanvas');
    const ctx = canvas.getContext('2d');
    function resize(){ canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
    window.addEventListener('resize', resize); resize();

    const hearts = [];
    function newHeart(){ const size = 12 + Math.random()*42; return {x: Math.random()*canvas.width, y: -50 - Math.random()*200, vx:(Math.random()-0.5)*0.6, vy:1+Math.random()*1.6, size, life:0, rot: Math.random()*Math.PI*2, color: Math.random()>0.5?getComputedStyle(document.documentElement).getPropertyValue('--neon-red'):getComputedStyle(document.documentElement).getPropertyValue('--neon-blue')}; }

    // spawn rate
    setInterval(()=>{ if(hearts.length < 140) hearts.push(newHeart()); }, 240);

    function drawHeart(x,y,s,rot,color){ ctx.save(); ctx.translate(x,y); ctx.rotate(rot); ctx.beginPath(); const top = -s/4; ctx.moveTo(0, s/4); ctx.bezierCurveTo(-s, top, -s, s, 0, s); ctx.bezierCurveTo(s, s, s, top, 0, s/4); ctx.closePath(); const g = ctx.createRadialGradient(-s*0.2, -s*0.2, 1, 0, 0, s); g.addColorStop(0, color); g.addColorStop(0.6, 'rgba(255,255,255,0.06)'); g.addColorStop(1, 'rgba(0,0,0,0)'); ctx.fillStyle = g; ctx.fill(); ctx.restore(); }

    function step(){ ctx.clearRect(0,0,canvas.width, canvas.height); for(let i=hearts.length-1;i>=0;i--){ const h = hearts[i]; h.x += h.vx; h.y += h.vy; h.vy += 0.02; h.rot += 0.01 * (h.vx>0?1:-1); h.life += 1; drawHeart(h.x, h.y, h.size, h.rot, h.color); if(h.y - h.size > canvas.height + 40) hearts.splice(i,1); } requestAnimationFrame(step); }
    step();

    /***********************
      FIREWORKS (final)
    ***********************/
    const fireworksRoot = document.getElementById('fireworks');
    function fireworksBurst(){
      const cvs = document.createElement('canvas');
      cvs.width = window.innerWidth; cvs.height = window.innerHeight;
      cvs.style.position='absolute'; cvs.style.inset='0'; fireworksRoot.appendChild(cvs);
      const c = cvs.getContext('2d'); const parts=[];
      for(let i=0;i<160;i++){ parts.push({x: cvs.width/2 + (Math.random()-0.5)*400, y: cvs.height/3 + (Math.random()-0.5)*200, vx:(Math.random()-0.5)*8, vy:(Math.random()-1.8)*8, life:60+Math.random()*80, color: Math.random()>0.5?getComputedStyle(document.documentElement).getPropertyValue('--neon-red'):getComputedStyle(document.documentElement).getPropertyValue('--neon-blue')}); }
      let t=0; const id = setInterval(()=>{ c.fillStyle='rgba(0,0,0,0.18)'; c.fillRect(0,0,cvs.width,cvs.height); parts.forEach(p=>{ p.x+=p.vx; p.y+=p.vy; p.vy+=0.12; p.life--; c.beginPath(); c.arc(p.x,p.y, Math.max(1,p.life/12),0,Math.PI*2); c.fillStyle=p.color; c.fill(); }); t++; if(t>160){ clearInterval(id); setTimeout(()=>cvs.remove(),400); } },30);
    }

    /***********************
      PAGE FLIP (center-open)
    ***********************/
    const pages = Array.from(document.querySelectorAll('.page'));
    let current = 0;
    pages.forEach((p,i)=>{ if(i!==0) p.classList.add('hidden'); });

    // dots
    const dots = document.getElementById('dots');
    pages.forEach((p,i)=>{ const d = document.createElement('div'); d.className='dot'+(i===0?' active':''); dots.appendChild(d); });
    function setActiveDot(i){ Array.from(dots.children).forEach((d,ii)=> d.classList.toggle('active', ii===i)); }

    function flipTo(target){
      if(target===current) return;
      const from = pages[current];
      const to = pages[target];
      from.classList.add('flipping');
      setTimeout(()=>{ from.classList.add('hidden'); from.classList.remove('flipping'); },900);
      to.classList.remove('hidden');
      current = target; setActiveDot(current);
      if(current === pages.length-1){
        fireworksBurst();
        for(let i=0;i<18;i++){ setTimeout(()=>{ if(hearts.length < 220) hearts.push(newHeart()); }, i*120); }
      }
    }

    // wire nav
    document.getElementById('nextBtn1').addEventListener('click', ()=> flipTo(1));
    document.getElementById('nextBtn2').addEventListener('click', ()=> flipTo(2));
    document.getElementById('nextBtn3').addEventListener('click', ()=> flipTo(3));
    document.getElementById('nextBtn4').addEventListener('click', ()=> flipTo(4));

    document.getElementById('prevBtn2').addEventListener('click', ()=> flipTo(0));
    document.getElementById('prevBtn3').addEventListener('click', ()=> flipTo(1));
    document.getElementById('prevBtn4').addEventListener('click', ()=> flipTo(2));
    document.getElementById('prevBtn5').addEventListener('click', ()=> flipTo(3));
    document.getElementById('replay').addEventListener('click', ()=> flipTo(0));

    document.getElementById('nextAll').addEventListener('click', ()=> flipTo(Math.min(pages.length-1, current+1)));
    document.getElementById('prevAll').addEventListener('click', ()=> flipTo(Math.max(0, current-1)));

    document.addEventListener('keydown', (e)=>{ if(e.key==='ArrowRight') flipTo(Math.min(pages.length-1, current+1)); if(e.key==='ArrowLeft') flipTo(Math.max(0,current-1)); if(e.key==='Enter') flipTo(Math.min(pages.length-1, current+1)); });

    // allow tap anywhere to go next (ignore buttons)
    document.querySelector('.book-wrap').addEventListener('click',(e)=>{ if(e.target.closest('.btn')) return; flipTo(Math.min(pages.length-1, current+1)); });

    /***********************
      YOUTUBE PLAYER for 20s loop
      (uses IFrame API)
    ***********************/

    // 1) Create script tag to load API
    const tag = document.createElement('script');
    tag.src = "https://www.youtube.com/iframe_api";
    document.head.appendChild(tag);

    // 2) YouTube player variables
    // Replace VIDEO_ID below with the id from your link.
    // Your provided link: https://youtu.be/rIPtyodvaJk?si=wNA2SoBiwatQCGuQ
    // Video id is: rIPtyodvaJk
    const YT_VIDEO_ID = "rIPtyodvaJk";
    let player, isPlayerReady = false;
    let playRequested = false;

    // 3) API will call this function when ready
    function onYouTubeIframeAPIReady() {
      player = new YT.Player('yt-player', {
        height: '0', width: '0', videoId: YT_VIDEO_ID,
        playerVars: {
          autoplay: 0,
          controls: 0,
          modestbranding: 1,
          rel: 0,
          disablekb: 1,
          fs: 0,
          iv_load_policy: 3,
          playsinline: 1
        },
        events: {
          'onReady': onPlayerReady,
          'onStateChange': onPlayerStateChange
        }
      });
    }

    function onPlayerReady(e){
      isPlayerReady = true;
      // ensure it's muted initially to comply with some autoplay policies
      // but we will unmute when play is requested by user.
      player.mute();
      if(playRequested) startLoopedSegment();
    }

    // loop control: we want to loop from 0s to 20s repeatedly
    const SEG_START = 0;
    const SEG_END = 20; // seconds
    let loopChecker = null;
    function startLoopedSegment(){
      if(!isPlayerReady) { playRequested = true; return; }
      // seek to start and play
      player.seekTo(SEG_START, true);
      player.playVideo();
      player.unMute();
      // set an interval to watch currentTime and seek back when > SEG_END
      if(loopChecker) clearInterval(loopChecker);
      loopChecker = setInterval(()=>{
        try {
          const t = player.getCurrentTime();
          if(t >= SEG_END - 0.12) {
            player.seekTo(SEG_START, true);
          }
        } catch(e){}
      }, 200);
    }

    function stopLoopedSegment(){
      if(loopChecker) { clearInterval(loopChecker); loopChecker = null; }
      if(player && isPlayerReady){ player.pauseVideo(); }
    }

    // Play button wiring
    const musicBtn = document.getElementById('musicBtn');
    musicBtn.addEventListener('click', ()=>{
      if(!player || !isPlayerReady){
        // user clicked before player ready; request play once ready
        playRequested = true;
        musicBtn.textContent = "Loading... 🎵";
        return;
      }
      // If playing, stop; else start the 20s loop
      const state = player.getPlayerState();
      if(state === YT.PlayerState.PLAYING || state === YT.PlayerState.BUFFERING){
        stopLoopedSegment();
        musicBtn.textContent = "Play Music 🎵";
      } else {
        startLoopedSegment();
        musicBtn.textContent = "Music On 🎵";
      }
    });

    // In case user clicked before API loaded, handle later readiness by checking a flag
    // (onPlayerReady handles playRequested)

    /***********************
      Notes / UX
      - Browser autoplay policies require a user gesture to start audio. Click "Play Music" once.
      - The YouTube player is hidden (0x0 size). It only provides audio.
      - If network blocks YouTube, use an MP3 file hosted on your site instead and replace the player logic.
    ***********************/

    // ensure initial focus
    document.getElementById('nextBtn1').focus();
  </script>
</body>
</html>
