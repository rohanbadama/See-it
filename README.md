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
  transition:background 4s linear;
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
@keyframes float{50%{transform:translateY(-18px)}}

.love-text{font-size:52px;color:#ff9acb;text-shadow:0 0 20px #ff4da6}

/* Typing */
#typingText{
  max-width:90%;
  margin:auto;
  font-size:18px;
  line-height:1.6;
  min-height:120px;
  border-right:2px solid white;
}

/* Falling text shards */
.text-shard{
  position:fixed;
  font-weight:bold;
  animation:fall 5s linear forwards;
}
@keyframes fall{
  to{
    transform:translateY(110vh) rotate(40deg);
    opacity:0;
  }
}

/* Dark fade overlay */
#fadeOverlay{
  position:fixed;
  inset:0;
  background:black;
  opacity:0;
  pointer-events:none;
  transition:opacity 5s linear;
}
</style>
</head>
<body>

<div id="fadeOverlay"></div>

<!-- Screen 1 -->
<div class="screen active" id="s1">
  <div class="cat">😺</div>
  <h1>Hey cutiepie 🥰</h1>
  <p>I made something just for you...</p>
  <button onclick="startExperience()">Open it 💖</button>
</div>

<!-- Screen 5 Typing Screen -->
<div class="screen" id="s5">
  <div class="cat">😿</div>
  <p id="typingText"></p>
  <button onclick="next(6)">Last thing… ❤️</button>
</div>

<!-- Final Screen -->
<div class="screen" id="s6">
  <h1 class="love-text" id="loveText">I Love You ❤️</h1>
  <button onclick="shatterLove()">Touch My Heart 💔</button>
</div>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/10/25/audio_946f4dd0a6.mp3" type="audio/mp3">
</audio>

<script>
const music=document.getElementById("music");

function startExperience(){
  music.play().catch(()=>{});
  next(5);
  startTyping();
}

function next(n){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('s'+n).classList.add('active');
}

/* ❤️ TYPEWRITER EFFECT */
const message = `I never wanted to hurt you… not even for a second.
If my words ever made you feel small, I’m truly sorry.
You are the most beautiful part of my life.
Your smile is my peace, your happiness is my wish.
I promise to be better, to love you louder, and hold you tighter.
Please forgive me… because my heart has always been yours. 💔`;

function startTyping(){
  let i=0;
  const speed=35;
  const el=document.getElementById("typingText");
  function type(){
    if(i<message.length){
      el.innerHTML += message.charAt(i);
      i++;
      setTimeout(type,speed);
    }else{
      el.style.borderRight="none";
    }
  }
  type();
}

/* 💔 SHATTER TEXT */
function shatterLove(){
  const textEl=document.getElementById("loveText");
  const rect=textEl.getBoundingClientRect();
  const words=["I","Love","You","❤️"];

  textEl.style.visibility="hidden";

  words.forEach((word,index)=>{
    const span=document.createElement("div");
    span.className="text-shard";
    span.innerText=word;
    span.style.left=(rect.left + index*rect.width/4)+"px";
    span.style.top=rect.top+"px";
    span.style.fontSize="42px";
    document.body.appendChild(span);
  });

  // Slow fade to black
  document.getElementById("fadeOverlay").style.opacity=1;
}
</script>

</body>
</html>
