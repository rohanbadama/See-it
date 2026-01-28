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
}

/* Floating hearts background */
.hearts span{
  position:absolute;
  bottom:-50px;
  font-size:20px;
  animation:rise 8s linear infinite;
}
@keyframes rise{
  from{transform:translateY(0);opacity:1;}
  to{transform:translateY(-110vh);opacity:0;}
}

.screen{
  display:none;
  height:100vh;
  padding:30px;
  box-sizing:border-box;
  animation:fade 1s ease forwards;
}
.active{display:block;}

@keyframes fade{from{opacity:0;transform:translateY(20px);}to{opacity:1;}}

button{
  background:linear-gradient(45deg,#ff4d88,#ff85a2);
  border:none;
  padding:12px 28px;
  border-radius:30px;
  color:white;
  font-size:18px;
  margin-top:20px;
  cursor:pointer;
  box-shadow:0 0 10px #ff4d88;
}

/* Cat */
.cat{
  width:130px;
  animation:float 2.5s ease-in-out infinite;
}
@keyframes float{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-15px)}
}

/* Shake */
.shake{animation:shake 0.4s linear 3;}
@keyframes shake{
  0%{transform:translateX(0)}
  25%{transform:translateX(-8px)}
  50%{transform:translateX(8px)}
  75%{transform:translateX(-8px)}
  100%{transform:translateX(0)}
}

/* Meter */
.bar{width:80%;height:15px;background:#ffffff22;margin:20px auto;border-radius:10px;overflow:hidden;}
.fill{height:100%;width:0;background:#ff4d88;transition:width 0.2s;}

.reveal-box{
  background:#ffffff15;
  padding:15px;
  margin:12px;
  border-radius:15px;
  cursor:pointer;
  transition:0.3s;
}
.revealed{background:#ff4d88;}

.typing{
  border-right:2px solid white;
  white-space:normal;
  overflow:hidden;
  animation:fadeText 5s ease forwards;
}
@keyframes fadeText{from{opacity:0}to{opacity:1}}

.love-text{
  font-size:44px;
  color:#ff9acb;
  animation:glow 1.5s infinite alternate;
}
@keyframes glow{
  from{text-shadow:0 0 10px #ff4da6;}
  to{text-shadow:0 0 35px #ff99cc;}
}

/* Sparkle trail */
.sparkle{
  position:fixed;
  pointer-events:none;
  font-size:14px;
  animation:sparkleFade 1s linear forwards;
}
@keyframes sparkleFade{to{transform:translateY(-20px);opacity:0;}}

/* Heart burst */
.burst-heart{
  position:fixed;
  font-size:16px;
  animation:burst 800ms ease-out forwards;
}
@keyframes burst{
  to{transform:translateY(-40px) scale(1.5);opacity:0;}
}
</style>
</head>
<body>

<div class="hearts"></div>

<!-- SCREEN 1 -->
<div class="screen active" id="s1">
  <img src="https://media.tenor.com/8QfKZ5n1nEoAAAAi/cute-cat.gif" class="cat">
  <h1>Hey cutiepie 🥰</h1>
  <p>Do you even know how cute you are?</p>
  <button onclick="startExperience(event)">Let's check 💖</button>
</div>

<!-- SCREEN 2 -->
<div class="screen" id="s2">
  <h2>Measuring your cuteness... ⏳</h2>
  <h1 id="percent">0%</h1>
  <div class="bar"><div class="fill" id="fill"></div></div>
  <p id="warn" style="display:none;">⚠️ WARNING: Too cute to handle!</p>
  <button id="next2" style="display:none;" onclick="next(3,event)">Continue ➜</button>
</div>

<!-- SCREEN 3 -->
<div class="screen" id="s3">
  <h2>Tap each one to reveal 💌</h2>
  <div class="reveal-box" onclick="reveal(this,1,event)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,2,event)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,3,event)">Tap to reveal message</div>
  <button onclick="next(4,event)">See more ➜</button>
</div>

<!-- SCREEN 4 -->
<div class="screen" id="s4">
  <h2>A little note for you 💗</h2>
  <p>I’m truly sorry for every moment I made you feel sad. You deserve only love, respect, and happiness 🌹</p>
  <button onclick="next(5,event)">Open my heart ➜</button>
</div>

<!-- SCREEN 5 -->
<div class="screen" id="s5">
  <img src="https://media.tenor.com/x9vYpQ4R0vAAAAAi/crying-cat.gif" class="cat">
  <p class="typing">
    I never meant to hurt you, not even in the smallest way.  
    If my words or actions ever made you feel unimportant, ignored, or unloved, I am deeply sorry.  
    You are the most precious part of my life, the person who makes my world softer, warmer, and brighter.  
    Losing your smile, even for a moment, hurts me more than I can explain.  
    Please forgive me, because my heart has always been yours and always will be. 💔💖  
    No matter what happens, my care for you will never fade.
  </p>
  <button onclick="next(6,event)">Last thing… ❤️</button>
</div>

<!-- SCREEN 6 -->
<div class="screen" id="s6">
  <h1 class="love-text">I Love You ❤️</h1>
</div>

<audio id="bgMusic" loop>
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3" type="audio/mp3">
</audio>

<script>
const music=document.getElementById("bgMusic");

function startExperience(e){
  heartBurst(e);
  music.play();
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
      document.getElementById("s2").classList.add("shake");
      vibrate([200,100,200]);
    }
  },40);
}

function reveal(el,num,e){
  heartBurst(e);
  if(!el.classList.contains("revealed")){
    if(num===1) el.innerText="I'm really sorry if I ever hurt you even a little 🥺";
    if(num===2) el.innerText="You mean more to me than I can ever explain 💖";
    if(num===3) el.innerText="Please forgive me… I never want to lose you 💔";
    el.classList.add("revealed");
    vibrate();
  }
}

function vibrate(pattern=100){
  if(navigator.vibrate) navigator.vibrate(pattern);
}

/* Sparkle trail */
document.addEventListener("mousemove", e=>createSparkle(e.clientX,e.clientY));
document.addEventListener("touchmove", e=>{
  const t=e.touches[0]; createSparkle(t.clientX,t.clientY);
});
function createSparkle(x,y){
  const s=document.createElement("div");
  s.className="sparkle";
  s.innerHTML="✨";
  s.style.left=x+"px";
  s.style.top=y+"px";
  document.body.appendChild(s);
  setTimeout(()=>s.remove(),1000);
}

/* Heart burst */
function heartBurst(e){
  if(!e) return;
  for(let i=0;i<6;i++){
    const h=document.createElement("div");
    h.className="burst-heart";
    h.innerHTML="💖";
    h.style.left=(e.clientX||window.innerWidth/2)+"px";
    h.style.top=(e.clientY||window.innerHeight/2)+"px";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),800);
  }
}

/* Floating hearts */
setInterval(()=>{
  const heart=document.createElement("span");
  heart.innerHTML="💖";
  heart.style.left=Math.random()*100+"vw";
  heart.style.fontSize=(Math.random()*20+10)+"px";
  document.querySelector(".hearts").appendChild(heart);
  setTimeout(()=>heart.remove(),8000);
},500);
</script>

</body>
</html>
