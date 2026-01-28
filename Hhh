<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Someone Special 💖</title>

<style>
body{
  margin:0;
  font-family:'Segoe UI',sans-serif;
  background:radial-gradient(circle at top,#4b0d4f,#1f0524);
  color:white;
  text-align:center;
  overflow:hidden;
  transition:background 2s linear;
}

.screen{display:none;height:100vh;padding:30px;box-sizing:border-box;}
.active{display:block;animation:fade 1s;}
@keyframes fade{from{opacity:0;transform:translateY(20px)}to{opacity:1}}

button{
  background:linear-gradient(45deg,#ff4d88,#ff85a2);
  border:none;padding:12px 28px;border-radius:30px;
  color:white;font-size:18px;margin-top:20px;cursor:pointer;
  box-shadow:0 0 10px #ff4d88;
}

.cat{font-size:80px;animation:float 2.5s ease-in-out infinite;}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}

.bar{width:80%;height:15px;background:#ffffff22;margin:20px auto;border-radius:10px;}
.fill{height:100%;width:0;background:#ff4d88;transition:width 0.2s;}

.shake{animation:shake 0.4s linear 4;}
@keyframes shake{0%{transform:translateX(0)}25%{transform:translateX(-8px)}50%{transform:translateX(8px)}75%{transform:translateX(-8px)}100%{transform:translateX(0)}}

.reveal-box{background:#ffffff15;padding:15px;margin:12px;border-radius:15px;cursor:pointer;transition:0.3s;}
.revealed{background:#ff4d88;transform:scale(1.05);}

.typing{border-right:2px solid white;white-space:pre-wrap;overflow:hidden;animation:typing 8s steps(160,end) forwards;width:0;margin:auto;max-width:90%;}
@keyframes typing{to{width:100%}}

.love-text{font-size:46px;color:#ff9acb;animation:glow 1.5s infinite alternate;}
@keyframes glow{from{text-shadow:0 0 10px #ff4da6}to{text-shadow:0 0 40px #ff99cc}}

.hearts span{position:absolute;bottom:-20px;font-size:18px;animation:rise 6s linear infinite;}
@keyframes rise{to{transform:translateY(-110vh);opacity:0}}

.sparkle{position:fixed;pointer-events:none;font-size:14px;animation:sparkleFade 1s linear forwards;}
@keyframes sparkleFade{to{transform:translateY(-20px);opacity:0;}}

.burst-heart{position:fixed;font-size:18px;animation:burst 800ms ease-out forwards;}
@keyframes burst{to{transform:translateY(-40px) scale(1.8);opacity:0;}}

/* SHATTER PARTICLES */
.shard{
  position:fixed;
  width:8px;
  height:8px;
  background:white;
  pointer-events:none;
  animation:fall 2s linear forwards;
}
@keyframes fall{
  to{
    transform:translateY(100vh) rotate(720deg);
    opacity:0;
  }
}
</style>
</head>
<body>

<div class="hearts"></div>

<div class="screen active" id="s1">
  <div class="cat">😺</div>
  <h1>Hey cutiepie 🥰</h1>
  <p>Do you even know how cute you are?</p>
  <button onclick="startExperience(event)">Let's check 💖</button>
</div>

<div class="screen" id="s2">
  <h2>Measuring your cuteness... ⏳</h2>
  <h1 id="percent">0%</h1>
  <div class="bar"><div class="fill" id="fill"></div></div>
  <p id="warn" style="display:none;">⚠️ WARNING: Too cute to handle!</p>
  <button id="next2" style="display:none;" onclick="next(3,event)">Continue ➜</button>
</div>

<div class="screen" id="s3">
  <h2>Tap each one to reveal 💌</h2>
  <div class="reveal-box" onclick="reveal(this,1,event)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,2,event)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,3,event)">Tap to reveal message</div>
  <button onclick="next(4,event)">See more ➜</button>
</div>

<div class="screen" id="s4">
  <h2>A little note for you 💗</h2>
  <p>I’m truly sorry for every moment I made you feel sad. You deserve only love and happiness 🌹</p>
  <button onclick="next(5,event)">Open my heart ➜</button>
</div>

<div class="screen" id="s5">
  <div class="cat">😿</div>
  <p class="typing">
I never meant to hurt you, not even in the smallest way.  
If my words or actions ever made you feel unimportant, ignored, or unloved, I am deeply sorry.  
You are the most precious part of my life. Please forgive me. 💔💖
  </p>
  <button onclick="next(6,event)">Last thing… ❤️</button>
</div>

<div class="screen" id="s6">
  <h1 class="love-text">I Love You ❤️</h1>
  <button onclick="shatterScreen()">Touch My Heart 💔</button>
</div>

<audio id="music">
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3" type="audio/mp3">
</audio>

<script>
const music=document.getElementById("music");

function startExperience(e){
  music.play().catch(()=>{});
  heartBurst(e);
  next(2);
}

function next(n,e){
  heartBurst(e);
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('s'+n).classList.add('active');
  if(n===2) meter();
  vibrate();
}

function meter(){
  let p=0;
  let i=setInterval(()=>{
    p+=2;
    percent.innerText=p+"%";
    fill.style.width=p+"%";
    if(p>=120){
      clearInterval(i);
      warn.style.display="block";
      next2.style.display="inline-block";
      s2.classList.add("shake");
      vibrate([200,100,200]);
    }
  },40);
}

function reveal(el,n,e){
  heartBurst(e);
  if(!el.classList.contains("revealed")){
    if(n===1) el.innerText="I'm really sorry if I ever hurt you 🥺";
    if(n===2) el.innerText="You mean the world to me 💖";
    if(n===3) el.innerText="Please forgive me… I never want to lose you 💔";
    el.classList.add("revealed");
    vibrate();
  }
}

function vibrate(pattern=100){ if(navigator.vibrate) navigator.vibrate(pattern); }

document.addEventListener("mousemove", e=>createSparkle(e.clientX,e.clientY));
function createSparkle(x,y){
  const s=document.createElement("div");
  s.className="sparkle";
  s.innerHTML="✨";
  s.style.left=x+"px"; s.style.top=y+"px";
  document.body.appendChild(s);
  setTimeout(()=>s.remove(),1000);
}

function heartBurst(e){
  if(!e) return;
  for(let i=0;i<7;i++){
    const h=document.createElement("div");
    h.className="burst-heart";
    h.innerHTML="💖";
    h.style.left=e.clientX+"px";
    h.style.top=e.clientY+"px";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),800);
  }
}

setInterval(()=>{
  const h=document.createElement("span");
  h.innerHTML="💖";
  h.style.left=Math.random()*100+"vw";
  document.querySelector(".hearts").appendChild(h);
  setTimeout(()=>h.remove(),6000);
},500);

/* 💥 SHATTER EFFECT */
function shatterScreen(){
  document.body.style.background="black";
  for(let i=0;i<120;i++){
    const shard=document.createElement("div");
    shard.className="shard";
    shard.style.left=Math.random()*100+"vw";
    shard.style.top=Math.random()*100+"vh";
    shard.style.background=`hsl(${Math.random()*360},80%,70%)`;
    document.body.appendChild(shard);
    setTimeout(()=>shard.remove(),2000);
  }
}
</script>

</body>
</html>
