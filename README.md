<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Book of Love — For Impu ❤️</title>
  <style>
    :root{
      --bg1:#ffd6ea; /* soft pink */
      --bg2:#ff93c2; /* mid pink */
      --accent:#ff1493; /* bright pink */
      --neon-blue:#00d9ff;
      --text:#fff;
      --card: rgba(255,255,255,0.06);
    }
    html,body{height:100%;margin:0;font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; background:linear-gradient(180deg,var(--bg1),var(--bg2)); color:var(--text); -webkit-font-smoothing:antialiased;}

    /* full-window hearts canvas */
    #heartsCanvas{position:fixed;inset:0;z-index:0;pointer-events:none}
    #fireworks{position:fixed;inset:0;z-index:30;pointer-events:none}

    .app{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:18px;position:relative}

    /* BOOK container - mobile-first */
    .book-wrap{width:100%;max-width:980px;height:92vh;perspective:2200px;position:relative;z-index:10;display:flex;align-items:center;justify-content:center}
    .book{width:94%;height:86%;position:relative;transform-style:preserve-3d}

    /* sheet/page look */
    .sheet{position:absolute;inset:0;border-radius:18px;background:linear-gradient(180deg, rgba(255,255,255,0.06), rgba(255,255,255,0.02));box-shadow:0 18px 60px rgba(0,0,0,0.18);backdrop-filter:blur(6px);display:flex;flex-direction:column;align-items:center;justify-content:center;padding:28px;transform-origin:center;transition:transform 900ms cubic-bezier(.2,.9,.2,1),opacity 420ms ease}
    .sheet.hidden{opacity:0;pointer-events:none;transform: translateZ(-60px) rotateY(-12deg) scale(.995)}
    .sheet.flipping{transform: rotateY(-180deg) translateZ(-40px)}

    .page-inner{width:90%;max-width:820px;margin:0 auto;color:var(--text);text-align:left}
    .title{font-weight:800;font-size:clamp(20px,4vw,34px);text-align:center;background:linear-gradient(90deg,var(--accent),var(--neon-blue));-webkit-background-clip:text;background-clip:text;color:transparent;margin-bottom:6px}
    .subtitle{font-size:clamp(14px,2.4vw,18px);opacity:0.95;text-align:center;margin-bottom:12px}
    .message{font-size:clamp(16px,2.6vw,20px);line-height:1.7;color:rgba(255,255,255,0.98);max-height:56vh;overflow:auto;padding-right:8px}

    /* controls */
    .controls{position:absolute;right:16px;top:16px;display:flex;gap:10px;z-index:60}
    .btn{background:var(--card);border:1px solid rgba(255,255,255,0.06);color:var(--text);padding:10px 14px;border-radius:999px;font-weight:700;cursor:pointer}
    .big{padding:12px 18px;font-size:16px}

    .nav{position:absolute;left:50%;transform:translateX(-50%);bottom:16px;display:flex;gap:12px;z-index:60}
    .arrow{width:46px;height:46px;border-radius:10px;background:linear-gradient(180deg,rgba(0,0,0,0.08),rgba(255,255,255,0.02));display:flex;align-items:center;justify-content:center;cursor:pointer}

    /* dots */
    .dots{position:absolute;left:16px;top:16px;display:flex;gap:8px;z-index:60}
    .dot{width:10px;height:10px;border-radius:50%;background:rgba(255,255,255,0.06)}
    .dot.active{box-shadow:0 8px 24px rgba(255,20,147,0.12);background:var(--accent)}

    /* fade / glow animation for message */
    .message.fade-in{opacity:0;transform:translateY(8px);animation:fadeUp 900ms ease forwards}
    @keyframes fadeUp{to{opacity:1;transform:translateY(0)}}

    /* final big hearts */
    .final-hero{text-align:center}
    .final-hero h2{font-size:clamp(24px,6vw,44px);margin:0}
    .final-hero .big-heart{font-size:78px;margin-top:12px;text-shadow:0 18px 60px rgba(255,20,147,0.15)}

    /* responsive tweaks */
    @media (max-width:720px){
      .book-wrap{height:96vh}
      .sheet{padding:18px;border-radius:14px}
      .page-inner{width:96%}
      .nav{bottom:10px}
    }
  </style>
</head>
<body>
  <canvas id="heartsCanvas"></canvas>
  <div id="fireworks"></div>

  <div class="app">
    <div class="book-wrap">
      <div class="book" id="book">

        <!-- Page 1 -->
        <div class="sheet" id="page-1" data-index="0">
          <div class="page-inner">
            <div class="title">Happy Birthday, Impu 💖</div>
            <div class="subtitle">A little surprise — just for you</div>
            <div class="message fade-in" id="m1">Hey my love — today is yours. Each heart you see reminds you of one thousand tiny reasons I cherish you. ❤️💙✨</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><button class="btn big" id="next1">Turn the page 📖</button></div>
          </div>
        </div>

        <!-- Page 2 -->
        <div class="sheet hidden" id="page-2" data-index="1">
          <div class="page-inner">
            <div class="title">To the Queen of my Heart 👑</div>
            <div class="subtitle">A piece of my heart</div>
            <div class="message" id="m2">To the Queen of my heart, I wanted to take a moment to express the depth of my feelings for you. You're the sunshine that brightens my days and this message is more than just a few lines on paper — it's a small piece of my heart reaching out to you. Your laughter is a sweet melody that fills my world with happiness and your presence is the gentle warmth that makes everything better. In you I found not just a girlfriend, but my best friend, my confidant, and the one with whom I want to share all of life's adventures. As we navigate the journey of life together, I want you to know how much you mean to me. You bring so much joy, love, and laughter into my life and I cherish every moment we spend together. Here's to the countless memories we've created and to the many more we'll make in the days ahead. ❤️🌹</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><div class="arrow btn" id="back2">◀</div><button class="btn big" id="next2">Next</button></div>
          </div>
        </div>

        <!-- Page 3 -->
        <div class="sheet hidden" id="page-3" data-index="2">
          <div class="page-inner">
            <div class="title">Just you ✨</div>
            <div class="subtitle">My beginning & my end</div>
            <div class="message" id="m3">There was nothing before you, and there is nothing after you. My story begins with your smile, and it ends in your eyes. 💫</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><div class="arrow btn" id="back3">◀</div><button class="btn big" id="next3">Next</button></div>
          </div>
        </div>

        <!-- Page 4 -->
        <div class="sheet hidden" id="page-4" data-index="3">
          <div class="page-inner">
            <div class="title">My Forever Love 💞</div>
            <div class="subtitle">A Birthday Wish for You</div>
            <div class="message" id="m4">Happy Birthday to the one who holds my whole heart!

My love for you is not a choice I make, but a fundamental truth of who I am. It is unstoppable and unconditional — a force that simply is. No one in this world could ever stop me from loving you.

You are my light, my adventure, and my most beautiful dream. I wish you a birthday filled with as much happiness, warmth, and magic as you bring into my life every single day. 🎂💖🌟</div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><div class="arrow btn" id="back4">◀</div><button class="btn big" id="next4">Open the final page</button></div>
          </div>
        </div>

        <!-- Page 5 Final -->
        <div class="sheet hidden" id="page-5" data-index="4">
          <div class="page-inner final-hero">
            <h2>I LOVE YOU, IMPU</h2>
            <div class="big-heart">💗💙🎆</div>
            <div style="height:12px"></div>
            <div class="message" id="m5">This is the place where all my small promises gather — laughter, late-night talks, silly fights, and soft kisses. Today I celebrate you, the beautiful soul who changed everything. Here's to us — to the memories behind and the adventures ahead. I love you more than words can hold. <br><br> <strong>Forever Yours, Deepu ❤️</strong></div>
            <div style="height:18px"></div>
            <div style="display:flex;gap:12px;justify-content:center"><div class="arrow btn" id="back5">◀</div><button class="btn big" id="replay">Replay</button></div>
          </div>
        </div>

      </div>

      <!-- UI -->
      <div class="controls">
        <div class="btn" id="musicBtn">Play Music 🎵</div>
      </div>
      <div class="dots" id="dots"></div>
      <div class="nav">
        <div class="arrow btn" id="prevAll">◀</div>
        <div class="btn big" id="nextAll">Turn Page ▶</div>
      </div>

    </div>
  </div>

  <!-- Hidden YouTube player (IFrame API) -->
  <div id="yt-player" style="display:none"></div>

  <script>
    // --- Hearts canvas (falling pink hearts) ---
    const canvas = document.getElementById('heartsCanvas'); const ctx = canvas.getContext('2d'); function resize(){ canvas.width = innerWidth; canvas.height = innerHeight; } window.addEventListener('resize', resize); resize();
    const hearts = [];
    function newHeart(){ return { x: Math.random()*canvas.width, y: -40 - Math.random()*200, size: 10 + Math.random()*36, vx: (Math.random()-0.5)*0.8, vy: 0.8 + Math.random()*1.6, rot: Math.random()*Math.PI*2, color: Math.random()>0.5?getComputedStyle(document.documentElement).getPropertyValue('--accent'):getComputedStyle(document.documentElement).getPropertyValue('--neon-blue') }; }
    // spawn
    setInterval(()=>{ if(hearts.length < 160) hearts.push(newHeart()); }, 220);
    function draw(){ ctx.clearRect(0,0,canvas.width,canvas.height); for(let i=hearts.length-1;i>=0;i--){ const h=hearts[i]; h.x += h.vx; h.y += h.vy; h.rot += 0.01; // draw heart
        ctx.save(); ctx.translate(h.x, h.y); ctx.rotate(h.rot); const s = h.size; ctx.beginPath(); ctx.moveTo(0,s/4); ctx.bezierCurveTo(-s, -s/4, -s, s/2, 0, s); ctx.bezierCurveTo(s, s/2, s, -s/4, 0, s/4); ctx.closePath(); const g = ctx.createLinearGradient(-s, -s, s, s); g.addColorStop(0, h.color); g.addColorStop(0.6, 'rgba(255,255,255,0.06)'); ctx.fillStyle = g; ctx.fill(); ctx.restore(); if(h.y - h.size > canvas.height + 40) hearts.splice(i,1); } requestAnimationFrame(draw); } draw();

    // --- Fireworks (final page) ---
    const fireworksRoot = document.getElementById('fireworks');
    function fireworksBurst(){ const cvs = document.createElement('canvas'); cvs.width = innerWidth; cvs.height = innerHeight; cvs.style.position='absolute'; cvs.style.inset='0'; fireworksRoot.appendChild(cvs); const c = cvs.getContext('2d'); const parts = []; for(let i=0;i<180;i++){ parts.push({x: innerWidth/2 + (Math.random()-0.5)*500, y: innerHeight/3 + (Math.random()-0.5)*250, vx:(Math.random()-0.5)*8, vy:(Math.random()-1.8)*8, life:40+Math.random()*80, color: Math.random()>0.5?getComputedStyle(document.documentElement).getPropertyValue('--accent'):getComputedStyle(document.documentElement).getPropertyValue('--neon-blue')}); } let t=0; const id=setInterval(()=>{ c.fillStyle='rgba(0,0,0,0.12)'; c.fillRect(0,0,cvs.width,cvs.height); parts.forEach(p=>{ p.x+=p.vx; p.y+=p.vy; p.vy+=0.12; p.life--; c.beginPath(); c.arc(p.x,p.y, Math.max(1,p.life/12),0,Math.PI*2); c.fillStyle=p.color; c.fill(); }); t++; if(t>160){ clearInterval(id); setTimeout(()=>cvs.remove(),500); } },30); }

    // --- Page flip logic (center-open feel) ---
    const sheets = Array.from(document.querySelectorAll('.sheet'));
    let current = 0; sheets.forEach((s,i)=>{ if(i!==0) s.classList.add('hidden'); });
    const dotsRoot = document.getElementById('dots'); sheets.forEach((s,i)=>{ const d=document.createElement('div'); d.className='dot'+(i===0?' active':''); dotsRoot.appendChild(d); });
    function setActiveDot(i){ Array.from(dotsRoot.children).forEach((d,ii)=> d.classList.toggle('active', ii===i)); }

    function flipTo(target){ if(target===current) return; const from = sheets[current]; const to = sheets[target]; // animate
      from.classList.add('flipping'); setTimeout(()=>{ from.classList.add('hidden'); from.classList.remove('flipping'); },900);
      to.classList.remove('hidden'); // apply fade-in to message
      const msg = to.querySelector('.message'); if(msg){ msg.classList.remove('fade-in'); void msg.offsetWidth; msg.classList.add('fade-in'); }
      current = target; setActiveDot(current);
      if(current === sheets.length-1){ fireworksBurst(); for(let i=0;i<26;i++){ setTimeout(()=>{ if(hearts.length<260) hearts.push(newHeart()); }, i*90); } }
    }

    // wire buttons
    document.getElementById('next1').addEventListener('click', ()=> flipTo(1));
    document.getElementById('next2').addEventListener('click', ()=> flipTo(2));
    document.getElementById('next3').addEventListener('click', ()=> flipTo(3));
    document.getElementById('next4').addEventListener('click', ()=> flipTo(4));
    document.getElementById('back2').addEventListener('click', ()=> flipTo(0));
    document.getElementById('back3').addEventListener('click', ()=> flipTo(1));
    document.getElementById('back4').addEventListener('click', ()=> flipTo(2));
    document.getElementById('back5').addEventListener('click', ()=> flipTo(3));
    document.getElementById('replay').addEventListener('click', ()=> flipTo(0));
    document.getElementById('nextAll').addEventListener('click', ()=> flipTo(Math.min(sheets.length-1, current+1)));
    document.getElementById('prevAll').addEventListener('click', ()=> flipTo(Math.max(0, current-1)));

    // keyboard nav and tap-to-next (tap only advances, not auto)
    document.addEventListener('keydown', e=>{ if(e.key==='ArrowRight') flipTo(Math.min(sheets.length-1, current+1)); if(e.key==='ArrowLeft') flipTo(Math.max(0,current-1)); if(e.key==='Enter') flipTo(Math.min(sheets.length-1, current+1)); });
    document.querySelector('.book-wrap').addEventListener('click', (e)=>{ if(e.target.closest('.btn') || e.target.closest('.arrow')) return; flipTo(Math.min(sheets.length-1, current+1)); });

    // --- YouTube IFrame API for music looping from 20s to video end ---
    const YT_ID = 'rIPtyodvaJk'; // provided by you
    let player, playerReady=false, loopChecker=null, playRequested=false; const START_SEG = 20; // start at 20s
    const tag = document.createElement('script'); tag.src='https://www.youtube.com/iframe_api'; document.head.appendChild(tag);
    function onYouTubeIframeAPIReady(){ player = new YT.Player('yt-player', { height: '0', width: '0', videoId: YT_ID, playerVars:{autoplay:0,controls:0,rel:0,modestbranding:1,iv_load_policy:3,playsinline:1}, events:{'onReady': onPlayerReady,'onStateChange': onPlayerStateChange}}); }
    function onPlayerReady(e){ playerReady=true; player.mute(); if(playRequested) startLoop(); }
    function onPlayerStateChange(e){ if(e.data===YT.PlayerState.ENDED){ // if video truly ends, seek back
        player.seekTo(START_SEG,true); player.playVideo(); }
    }
    function startLoop(){ if(!playerReady){ playRequested=true; return; } player.seekTo(START_SEG, true); player.unMute(); player.playVideo(); if(loopChecker) clearInterval(loopChecker); loopChecker = setInterval(()=>{ try{ const t = player.getCurrentTime(); const dur = player.getDuration(); if(dur && t >= dur - 0.14){ player.seekTo(START_SEG, true); } }catch(e){} }, 300); }
    function stopLoop(){ if(loopChecker) clearInterval(loopChecker); try{ player.pauseVideo(); }catch(e){} }

    document.getElementById('musicBtn').addEventListener('click', ()=>{
      if(!playerReady){ playRequested=true; document.getElementById('musicBtn').textContent='Loading... 🎵'; return; }
      const state = player.getPlayerState(); if(state===YT.PlayerState.PLAYING || state===YT.PlayerState.BUFFERING){ stopLoop(); document.getElementById('musicBtn').textContent='Play Music 🎵'; } else { startLoop(); document.getElementById('musicBtn').textContent='Music On 🎵'; }
    });

    // ensure first page message animation triggered
    document.addEventListener('DOMContentLoaded', ()=>{ const m=document.querySelector('#page-1 .message'); if(m){ m.classList.add('fade-in'); } });
  </script>
</body>
</html>
