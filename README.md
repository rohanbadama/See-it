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
  background:linear-gradient(180deg,#3b0a45,#1a0623);
  color:white;
  text-align:center;
  overflow:hidden;
}

.screen{display:none;height:100vh;padding:30px;box-sizing:border-box;}
.active{display:block;animation:fade 1s;}
@keyframes fade{from{opacity:0;transform:translateY(20px)}to{opacity:1}}

button{
  background:linear-gradient(45deg,#ff4d88,#ff85a2);
  border:none;padding:12px 28px;border-radius:30px;
  color:white;font-size:18px;margin-top:20px;cursor:pointer;
}

/* Cute bouncing cat emoji */
.cat{
  font-size:70px;
  animation:bounce 2s infinite;
}
@keyframes bounce{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-15px)}
}

/* Progress */
.bar{width:80%;height:15px;background:#ffffff22;margin:20px auto;border-radius:10px;}
.fill{height:100%;width:0;background:#ff4d88}

/* Shake */
.shake{animation:shake 0.4s linear 3}
@keyframes shake{
  0%{transform:translateX(0)}
  25%{transform:translateX(-6px)}
  50%{transform:translateX(6px)}
  75%{transform:translateX(-6px)}
  100%{transform:translateX(0)}
}

/* Reveal */
.reveal-box{
  background:#ffffff15;padding:15px;margin:12px;border-radius:15px;cursor:pointer;
}
.revealed{background:#ff4d88}

/* Typing effect */
.typing{
  display:inline-block;
  border-right:2px solid white;
  white-space:pre-wrap;
  overflow:hidden;
  animation:typing 6s steps(120,end) forwards;
  max-width:90%;
}
@keyframes typing{from{width:0}to{width:100%}}

/* Love glow */
.love-text{
  font-size:44px;color:#ff9acb;
  animation:glow 1.5s infinite alternate;
}
@keyframes glow{from{text-shadow:0 0 10px #ff4da6}to{text-shadow:0 0 35px #ff99cc}}

/* Hearts floating */
.hearts span{
  position:absolute;bottom:-20px;font-size:18px;
  animation:rise 6s linear infinite;
}
@keyframes rise{to{transform:translateY(-110vh);opacity:0}}
</style>
</head>
<body>

<div class="hearts"></div>

<!-- Screen 1 -->
<div class="screen active" id="s1">
  <div class="cat">😺</div>
  <h1>Hey cutiepie 🥰</h1>
  <p>Do you even know how cute you are?</p>
  <button onclick="start()">Let's check 💖</button>
</div>

<!-- Screen 2 -->
<div class="screen" id="s2">
  <h2>Measuring your cuteness... ⏳</h2>
  <h1 id="percent">0%</h1>
  <div class="bar"><div class="fill" id="fill"></div></div>
  <p id="warn" style="display:none;">⚠️ WARNING: Too cute to handle!</p>
  <button id="next2" style="display:none;" onclick="next(3)">Continue ➜</button>
</div>

<!-- Screen 3 -->
<div class="screen" id="s3">
  <h2>Tap each one to reveal 💌</h2>
  <div class="reveal-box" onclick="reveal(this,1)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,2)">Tap to reveal message</div>
  <div class="reveal-box" onclick="reveal(this,3)">Tap to reveal message</div>
  <button onclick="next(4)">See more ➜</button>
</div>

<!-- Screen 4 -->
<div class="screen" id="s4">
  <h2>A little note for you 💗</h2>
  <p>I’m truly sorry for every moment I made you feel sad. You deserve only love and happiness 🌹</p>
  <button onclick="next(5)">Open my heart ➜</button>
</div>

<!-- Screen 5 -->
<div class="screen" id="s5">
  <div class="cat">😿</div>
  <p class="typing">
I never meant to hurt you.  
If I ever made you feel unloved or unimportant, I am truly sorry.  
You are the most precious part of my life and my heart will always choose you.
  </p>
  <button onclick="next(6)">Last thing… ❤️</button>
</div>

<!-- Screen 6 -->
<div class="screen" id="s6">
  <h1 class="love-text">I Love You ❤️</h1>
</div>

<audio id="music">
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3" type="audio/mp3">
</audio>

<script>
const music=document.getElementById("music");

function start(){
  music.play().catch(()=>{});
  next(2);
}

function next(n){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('s'+n).classList.add('active');
  if(n===2) meter();
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
    }
  },40);
}

function reveal(el,n){
  if(!el.classList.contains("revealed")){
    if(n===1) el.innerText="I'm really sorry if I ever hurt you 🥺";
    if(n===2) el.innerText="You mean the world to me 💖";
    if(n===3) el.innerText="Please forgive me… I never want to lose you 💔";
    el.classList.add("revealed");
  }
}

/* Floating hearts */
setInterval(()=>{
  const h=document.createElement("span");
  h.innerHTML="💖";
  h.style.left=Math.random()*100+"vw";
  document.querySelector(".hearts").appendChild(h);
  setTimeout(()=>h.remove(),6000);
},600);
</script>

</body>
</html>
