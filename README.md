<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Someone Special 💖</title>
<style>
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(180deg, #2b0a2f, #3d0f3f);
  color: white;
  text-align: center;
  overflow: hidden;
}

.screen {
  display: none;
  height: 100vh;
  padding: 30px;
  box-sizing: border-box;
  animation: fadeIn 1s ease forwards;
}

.active { display: block; }

button {
  background: linear-gradient(45deg, #ff4d88, #ff6fa5);
  border: none;
  padding: 12px 25px;
  border-radius: 30px;
  color: white;
  font-size: 18px;
  margin-top: 20px;
  cursor: pointer;
}

@keyframes fadeIn {
  from {opacity:0; transform: translateY(20px);}
  to {opacity:1; transform: translateY(0);}
}

/* Cute floating animation */
.float {
  animation: float 2s ease-in-out infinite;
}
@keyframes float {
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-10px)}
}

/* Progress bar */
.bar {
  width: 80%;
  height: 15px;
  background: #fff2;
  border-radius: 10px;
  margin: 20px auto;
  overflow: hidden;
}
.fill {
  height: 100%;
  width: 0%;
  background: hotpink;
  transition: width 0.2s;
}

/* Tap reveal boxes */
.reveal-box {
  background: #ffffff10;
  padding: 15px;
  margin: 10px;
  border-radius: 15px;
  cursor: pointer;
}

.typing {
  border-right: 2px solid white;
  white-space: nowrap;
  overflow: hidden;
  width: 0;
  animation: typing 4s steps(40,end) forwards;
}
@keyframes typing { to { width: 100% } }

.love-text {
  font-size: 40px;
  color: #ff9acb;
  animation: glow 1.5s infinite alternate;
}
@keyframes glow {
  from { text-shadow: 0 0 10px #ff4da6; }
  to { text-shadow: 0 0 25px #ff99cc; }
}
</style>
</head>
<body>

<!-- Screen 1 -->
<div class="screen active" id="s1">
  <h1 class="float">Hey cutiepie 🥰</h1>
  <p>Do you even know how cute you are?</p>
  <button onclick="nextScreen(2)">Let's check 💖</button>
</div>

<!-- Screen 2 -->
<div class="screen" id="s2">
  <h2>Measuring your cuteness... ⏳</h2>
  <h1 id="percent">0%</h1>
  <div class="bar"><div class="fill" id="fill"></div></div>
  <p id="warn" style="display:none;">⚠️ WARNING: Too cute to handle!</p>
  <button id="contBtn" style="display:none;" onclick="nextScreen(3)">Continue ➜</button>
</div>

<!-- Screen 3 -->
<div class="screen" id="s3">
  <h2>Tap each one to reveal 💌</h2>
  <div class="reveal-box" onclick="reveal(this)">I'm really sorry if I ever hurt you even a little 🥺</div>
  <div class="reveal-box" onclick="reveal(this)">You mean more to me than I can ever explain 💖</div>
  <div class="reveal-box" onclick="reveal(this)">Please forgive me… I never want to lose you 💔</div>
  <button onclick="nextScreen(4)">See more ➜</button>
</div>

<!-- Screen 4 -->
<div class="screen" id="s4">
  <h2>A little note for you 💗</h2>
  <p>I’m truly sorry for every moment I made you feel sad. You deserve only love, respect, and happiness 🌹</p>
  <button onclick="nextScreen(5)">Open my heart ➜</button>
</div>

<!-- Screen 5 -->
<div class="screen" id="s5">
  <h2 class="float">🥺</h2>
  <p class="typing">I never meant to hurt you... You are the most precious person in my life.</p>
  <button onclick="nextScreen(6)">Last thing… ❤️</button>
</div>

<!-- Screen 6 -->
<div class="screen" id="s6">
  <h1 class="love-text">I Love You ❤️</h1>
</div>

<script>
function nextScreen(n){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('s'+n).classList.add('active');

  if(n===2) startMeter();
}

function startMeter(){
  let p=0;
  let interval=setInterval(()=>{
    p+=2;
    document.getElementById('percent').innerText=p+"%";
    document.getElementById('fill').style.width=p+"%";
    if(p>=120){
      clearInterval(interval);
      document.getElementById('warn').style.display="block";
      document.getElementById('contBtn').style.display="inline-block";
    }
  },40);
}

function reveal(el){
  el.style.background="#ff4d88";
}
</script>

</body>
</html>
