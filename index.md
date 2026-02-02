<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>RadioStars FM</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:radial-gradient(circle at top, #071b2e, #000);
  font-family:Arial, sans-serif;
  color:#fff;
}
.player{
  background:#071b2e;
  padding:30px;
  border-radius:20px;
  box-shadow:0 0 30px rgba(0,180,255,.6);
  text-align:center;
  width:320px;
}
.player img{
  width:160px;
  margin-bottom:15px;
}
.status{
  margin:10px 0;
  color:#0ff;
}
button{
  width:120px;
  padding:12px;
  margin:5px;
  border:none;
  border-radius:30px;
  font-size:16px;
  cursor:pointer;
}
.play{background:#00cfff;color:#000;}
.stop{background:#ff0033;color:#fff;}
.listeners{
  margin-top:10px;
  color:#aaa;
  font-size:14px;
}
</style>
</head>

<body>

<div class="player">
  <img src="LOGOSTARS2.png" alt="RadioStars FM">
  <div class="status" id="status">🔴 OFF AIR</div>

  <button class="play" onclick="playRadio()">▶ PLAY</button>
  <button class="stop" onclick="stopRadio()">■ STOP</button>

  <div class="listeners">👥 Pendengar: <span id="listeners">10</span></div>
</div>

<audio id="radio" preload="none"></audio>

<script>
const radio = document.getElementById("radio");
const statusText = document.getElementById("status");

function playRadio(){
  radio.src = "http://45.64.97.82:8114/stream";
  radio.play().then(()=>{
    statusText.innerText = "🔴 LIVE ON AIR";
  }).catch(()=>{
    statusText.innerText = "❌ Klik PLAY sekali lagi";
  });
}

function stopRadio(){
  radio.pause();
  radio.src="";
  statusText.innerText = "⏹ STOPPED";
}

// fake listeners
let l=10;
setInterval(()=>{
  l += Math.floor(Math.random()*3)-1;
  if(l<10)l=10;
  document.getElementById("listeners").innerText=l;
},5000);
</script>

</body>
</html>
