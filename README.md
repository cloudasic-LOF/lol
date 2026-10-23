<html lang="ru">  
<head>  
<meta charset="utf-8">  
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">  
<title>Маше — с днём рождения</title>  
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Marck+Script&family=Lora:ital,wght@0,400;0,500;1,400&display=swap">  
<style>  
:root{  
  --night:#120a21; 
  --night2:#2c1543; 
  --rose:#e9a1b3; 
  --rose-d:#c06883; 
  --paper:#fffaf7;  
  --ink:#2d1b38; 
  --gold:#ebd095; 
  --gold-d:#b98a35;  
  box-sizing:border-box;  
  padding-top:env(safe-area-inset-top,0px); 
  padding-bottom:env(safe-area-inset-bottom,0px);  
}  
*,*::before,*::after{box-sizing:inherit}  
html,body{margin:0;min-height:100%;overflow-x:hidden}  
body{  
  background:radial-gradient(130% 100% at 50% 0%, var(--night2), var(--night) 80%) fixed;  
  color:var(--ink); 
  font-family:'Lora',Georgia,serif; 
  min-height:100vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
}  

#fx{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:10}  
.stars i{position:fixed;width:2px;height:2px;border-radius:50%;background:#fff;opacity:.6;animation:tw 3s infinite ease-in-out}  
@keyframes tw{50%{opacity:.1;transform:scale(.5)}}

/* ---------- Сцена с конвертом ---------- */
#stage{
  position:relative;
  min-height:100vh;
  width:100%;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  gap:2.5rem;
  padding:1.5rem;
  transition:opacity 0.8s ease, transform 0.8s ease;
  z-index:2;
}
#stage.gone{
  opacity:0;
  transform:scale(0.9) translateY(30px);
  pointer-events:none;
}

.env-wrapper {
  perspective: 1000px;
}

.env{
  position:relative;
  width:min(340px, 84vw);
  aspect-ratio:3/2;
  cursor:pointer;
  transform-style:preserve-3d;
  transition:transform 0.2s ease-out;
  filter:drop-shadow(0 20px 35px rgba(0,0,0,0.5));
  border:0;
  background:none;
  padding:0;
  -webkit-tap-highlight-color:transparent;
}

.env-inner {
  position:absolute;
  inset:0;
  transform-style:preserve-3d;
}

.env .back{
  position:absolute;
  inset:0;
  background:var(--rose-d);
  border-radius:8px;
  box-shadow:inset 0 0 20px rgba(0,0,0,0.15);
}

.env .sheet{
  position:absolute;
  inset:8% 6% auto 6%;
  height:84%;
  background:var(--paper);
  border-radius:6px;
  box-shadow:0 2px 8px rgba(0,0,0,0.1);
  transition:transform 0.8s 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
  z-index:2;
}

.env.open .sheet{
  transform:translateY(-80%) scale(1.02);
}

.env .front{
  position:absolute;
  inset:0;
  background:var(--rose);
  clip-path:polygon(0 0, 50% 50%, 100% 0, 100% 100%, 0 100%);
  border-radius:8px;
  z-index:3;
}

.env .side{
  position:absolute;
  inset:0;
  background:linear-gradient(135deg, var(--rose), #f3b9c7);
  clip-path:polygon(0 0, 48% 50%, 0 100%);
  border-radius:8px;
  z-index:3;
}

.env .flap{
  position:absolute;
  inset:0 0 auto 0;
  height:60%;
  background:linear-gradient(#f7bdca, var(--rose));
  clip-path:polygon(0 0, 100% 0, 50% 100%);
  transform-origin:top center;
  transition:transform 0.6s 0.2s ease-in-out, z-index 0s 0.5s;
  z-index:4;
  border-radius:8px 8px 0 0;
}

.env.open .flap{
  transform:rotateX(180deg);
  z-index:1;
}

.seal{
  position:absolute;
  left:50%;
  top:48%;
  width:52px;
  height:52px;
  margin:-26px 0 0 -26px;
  border-radius:50%;
  z-index:5;
  background:radial-gradient(circle at 35% 30%, #fcebc2, var(--gold) 50%, var(--gold-d));
  display:grid;
  place-items:center;
  color:#63420d;
  font-family:'Marck Script',cursive;
  font-size:1.8rem;
  box-shadow:0 4px 12px rgba(0,0,0,0.35), inset 0 0 4px rgba(255,255,255,0.6);
  transition:transform 0.4s ease, opacity 0.4s ease;
  animation:pulse-seal 2.5s infinite ease-in-out;
}

@keyframes pulse-seal {
  0%, 100% { transform:scale(1); box-shadow:0 4px 12px rgba(0,0,0,0.35); }
  50% { transform:scale(1.08); box-shadow:0 6px 18px rgba(232,194,122,0.6); }
}

.env.open .seal{
  opacity:0;
  transform:scale(0.2) rotate(45deg);
  animation:none;
}

.hint{
  font-family:'Marck Script',cursive;
  color:#fbe4ec;
  font-size:1.8rem;
  text-align:center;
  margin:0;
  letter-spacing:1px;
  text-shadow:0 2px 10px rgba(0,0,0,0.3);
  animation:bounce-hint 2s infinite ease-in-out;
}

@keyframes bounce-hint {
  0%, 100% { transform:translateY(0); opacity:0.9; }
  50% { transform:translateY(-6px); opacity:0.6; }
}

/* ---------- Настоящее письмо ---------- */
#letter{
  display:none;
  width:min(580px, 92vw);
  margin:2rem auto;
  position:relative;
  z-index:20;
}
#letter.show{
  display:block;
}

.paper{
  background:var(--paper);
  border-radius:12px;
  padding:3rem 2.2rem 2.6rem;
  position:relative;
  box-shadow:0 25px 50px -12px rgba(0,0,0,0.5);
  background-image:linear-gradient(rgba(212,128,154,0.08) 1px, transparent 1px);
  background-size:100% 36px;
  transform-origin:top center;
  animation:unfold 1.2s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

@keyframes unfold{
  0%{ opacity:0; transform:translateY(80px) scale(0.85); }
  100%{ opacity:1; transform:translateY(0) scale(1); }
}

h1{
  font-family:'Marck Script',cursive;
  font-weight:400;
  font-size:clamp(2.6rem, 8vw, 3.6rem);
  line-height:1.1;
  margin:0 0 1.8rem;
  color:var(--rose-d);
  text-shadow: 1px 1px 0px rgba(0,0,0,0.05);
}

.line{
  font-size:1.15rem;
  line-height:36px;
  margin:0 0 36px;
  color:var(--ink);
  opacity:0;
  transform:translateY(12px);
  animation:fadeInLine 0.8s ease forwards;
}

@keyframes fadeInLine{
  to{ opacity:1; transform:translateY(0); }
}

.sign{
  font-family:'Marck Script',cursive;
  font-size:2.2rem;
  color:var(--rose-d);
  margin:1rem 0 0;
  text-align:right;
  opacity:0;
  animation:fadeInLine 0.8s 4.8s ease forwards;
}

.reply{
  display:inline-block;
  margin:2.5rem auto 0;
  padding:0.9rem 2.8rem;
  border-radius:50px;
  text-decoration:none;
  font-family:'Marck Script',cursive;
  font-size:1.8rem;
  color:#422806;
  background:linear-gradient(135deg, #fcebc2, var(--gold) 50%, var(--gold-d));
  box-shadow:0 10px 25px rgba(0,0,0,0.3);
  opacity:0;
  animation:fadeInLine 0.8s 5.5s ease forwards, glowPulse 3s infinite 6.3s;
  transition:transform 0.25s ease, box-shadow 0.25s ease;
  text-align:center;
}

.reply-container {
  text-align:center;
}

.reply:hover{
  transform:translateY(-3px) scale(1.05);
  box-shadow:0 15px 30px rgba(232,194,122,0.5);
}
.reply:active{
  transform:scale(0.98);
}

@keyframes glowPulse{
  50%{ box-shadow:0 10px 35px rgba(232,194,122,0.8); }
}

@media (prefers-reduced-motion:reduce){
  *,::before,::after{animation-duration:.01s!important;animation-delay:0s!important;transition-duration:.01s!important}
}
</style>  
</head>  
<body>  

<div class="stars" id="stars" aria-hidden="true"></div>  
<canvas id="fx" aria-hidden="true"></canvas>  

<main id="stage">  
  <div class="env-wrapper">
    <button class="env" id="env" aria-label="Открыть письмо">  
      <div class="env-inner">
        <div class="back"></div>  
        <div class="sheet"></div>  
        <div class="side"></div>  
        <div class="front"></div>  
        <div class="flap"></div>  
        <div class="seal">М</div>  
      </div>
    </button>  
  </div>
  <p class="hint">Тебе особое послание, Маша ✨</p>  
</main>  

<article id="letter" aria-live="polite">  
  <div class="paper">  
    <h1>Дорогая Маша!</h1>  
    
    <p class="line" style="animation-delay: 0.8s">
      С днём рождения! Пусть этот новый год твоей жизни принесёт столько же тепла, сколько ты сама даришь окружающим.
    </p>  
    
    <p class="line" style="animation-delay: 1.8s">
      Желаю тебе невероятного вдохновения, искренней радости в каждой мелочи, ярких путешествий и людей рядом, с которыми можно быть настоящей и счастливой.
    </p>  
    
    <p class="line" style="animation-delay: 2.9s">
      Пусть все даже самые смелые задумки складываются легко и красиво, а каждый день оставляет после себя приятный и теплый след.
    </p>  
    
    <p class="line" style="animation-delay: 3.9s">
      Спасибо за то, какая ты замечательная. Пусть у тебя всё обязательно сбывается!
    </p>  
    
    <p class="sign">С наилучшими пожеланиями ♡</p>  
    
    <div class="reply-container">
      <a class="reply" href="https://t.me/cloudasic" target="_blank" rel="noopener noreferrer">Ответить</a>  
    </div>
  </div>  
</article>  

<script>  
// 1. Создание звёздного неба  
(function(){
  var s = document.getElementById('stars'), h = '';  
  for(var i = 0; i < 50; i++){
    h += '<i style="left:' + (Math.random() * 100) + '%;top:' + (Math.random() * 100) + '%;animation-delay:' + (Math.random() * 3) + 's"></i>';
  }  
  s.innerHTML = h;
})();  

// 2. Эффект лепестков и конфетти на Canvas
var cv = document.getElementById('fx'), cx = cv.getContext('2d'), P = [], W, H;  
function rs(){ W = cv.width = innerWidth; H = cv.height = innerHeight; } 
rs(); 
addEventListener('resize', rs);  

var cols = ['#e9a1b3', '#f6dca2', '#fff8f4', '#d4809a', '#c3a1ff', '#ffd1dc'];  

function burst(){  
  for(var i = 0; i < 120; i++){
    var a = Math.random() * Math.PI * 2, v = 5 + Math.random() * 9;  
    P.push({
      x: W / 2, y: H * 0.45, 
      vx: Math.cos(a) * v, vy: Math.sin(a) * v - 5, 
      r: 4 + Math.random() * 5, 
      c: cols[i % cols.length],  
      rot: Math.random() * 6, 
      vr: (Math.random() - 0.5) * 0.3, 
      life: 1, 
      petal: i % 2 === 0
    });
  }  
}  

function rain(){  
  if(P.length < 50) {
    P.push({
      x: Math.random() * W, y: -15, 
      vx: (Math.random() - 0.5) * 1.5, vy: 0.8 + Math.random() * 1.2, 
      r: 4 + Math.random() * 5,  
      c: cols[(Math.random() * cols.length) | 0], 
      rot: Math.random() * 6, 
      vr: (Math.random() - 0.5) * 0.08, 
      life: 1, 
      petal: true, 
      soft: true
    });  
  }
}  

var raining = false;  
function tick(){  
  cx.clearRect(0, 0, W, H);
  if(raining && Math.random() < 0.15) rain();  
  
  for(var i = P.length - 1; i >= 0; i--){
    var p = P[i];  
    if(!p.soft){ p.vy += 0.22; p.vx *= 0.98; p.life -= 0.008; } 
    else { p.vx += Math.sin(p.y / 50) * 0.02; }  
    
    p.x += p.vx; p.y += p.vy; p.rot += p.vr;  
    if(p.life <= 0 || p.y > H + 20){ P.splice(i, 1); continue; }  
    
    cx.save();
    cx.globalAlpha = Math.max(0, Math.min(1, p.life)) * (p.soft ? 0.8 : 1);
    cx.translate(p.x, p.y);
    cx.rotate(p.rot);
    cx.fillStyle = p.c;  
    
    if(p.petal){
      cx.beginPath();
      cx.ellipse(0, 0, p.r, p.r * 0.55, 0, 0, 6.28);
      cx.fill();
    } else {
      cx.fillRect(-p.r/2, -p.r/4, p.r, p.r/2);
    }  
    cx.restore();  
  }  
  requestAnimationFrame(tick);  
}  
tick();  

// 3. Параллакс конверта за курсором (Tilt Effect)
var envEl = document.getElementById('env');
document.addEventListener('mousemove', function(e){
  if(opened) return;
  var cx = window.innerWidth / 2;
  var cy = window.innerHeight / 2;
  var dx = (e.clientX - cx) / cx;
  var dy = (e.clientY - cy) / cy;
  envEl.style.transform = 'rotateY(' + (dx * 12) + 'deg) rotateX(' + (-dy * 12) + 'deg)';
});

// 4. Открытие конверта и анимация
var opened = false;  
envEl.addEventListener('click', function(){  
  if(opened) return;
  opened = true;
  
  envEl.style.transform = 'none';
  envEl.classList.add('open');  
  document.querySelector('.hint').style.opacity = '0';  
  
  setTimeout(function(){  
    document.getElementById('stage').classList.add('gone');  
    var l = document.getElementById('letter');
    l.classList.add('show');  
    burst();
    raining = true;  
    
    setTimeout(function(){
      document.getElementById('stage').style.display = 'none';
      window.scrollTo({top: 0, behavior: 'smooth'});
    }, 800);  
  }, 1500);  
});  
</script>  
</body>  
</html>
