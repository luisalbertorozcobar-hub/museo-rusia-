<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Museo Virtual de Rusia - Nivel Final</title>

<style>
body{margin:0;font-family:'Segoe UI';background:#0a0a0a;color:white;scroll-behavior:smooth;}
#progress{position:fixed;top:0;left:0;height:5px;background:red;width:0%;z-index:2000;}

header{background:linear-gradient(120deg,#8b0000,#000);padding:80px;text-align:center;}
nav{position:sticky;top:0;background:#111;padding:10px;text-align:center;}
nav a{color:white;margin:10px;text-decoration:none;}

section{padding:80px 20px;max-width:1100px;margin:auto;opacity:0;transform:translateY(40px);transition:.6s;}
section.visible{opacity:1;transform:translateY(0);}

.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:25px;}
.card{background:#1a1a1a;border-radius:15px;overflow:hidden;cursor:pointer;transition:.3s;}
.card:hover{transform:scale(1.05);}
.card img{width:100%;height:200px;object-fit:cover;}

.modal,.zoom{
display:none;position:fixed;top:0;left:0;width:100%;height:100%;
background:rgba(0,0,0,.9);justify-content:center;align-items:center;
}
.modal-content{
background:#111;padding:20px;border-radius:10px;max-width:600px;text-align:center;
}
.zoom img{max-width:90%;max-height:90%;}
.close{color:red;cursor:pointer;font-size:20px}

button{padding:10px;margin:5px;cursor:pointer;}

footer{text-align:center;padding:20px;background:#111;}
</style>

</head>
<body>

<div id="progress"></div>

<header>
<h1>Museo Virtual de Rusia</h1>
<p>Experiencia completa interactiva</p>
<button onclick="tour()">🧭 Iniciar recorrido</button>
</header>

<nav>
<a href="#timeline">Historia</a>
<a href="#video">Video</a>
<a href="#quiz">Quiz</a>
</nav>

<section id="timeline" class="visible">
<h2>Línea del Tiempo</h2>

<div class="cards">

<div class="card" onclick="evento('Rasputin','Místico que influyó en los Romanov.','https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg">
<h3>Rasputin</h3>
</div>

<div class="card" onclick="evento('Revolución Rusa','En 1917 Lenin lideró la revolución.','https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg">
<h3>Revolución</h3>
</div>

<div class="card" onclick="evento('Stalin','Industrialización y control total.','https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg">
<h3>Stalin</h3>
</div>

<div class="card" onclick="evento('WW2','Batalla de Stalingrado decisiva.','https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg">
<h3>WW2</h3>
</div>

</div>
</section>

<section id="video">
<h2>Video histórico</h2>
<iframe width="100%" height="400"
src="https://www.youtube.com/embed/1CqGeAmVu1I"
allowfullscreen></iframe>
</section>

<section id="quiz">
<h2>Quiz</h2>
<p>¿Quién lideró la Revolución Rusa?</p>
<button onclick="res('mal')">Stalin</button>
<button onclick="res('bien')">Lenin</button>
<button onclick="res('mal')">Rasputin</button>
<p id="resultado"></p>
<p>Puntaje: <span id="score">0</span></p>
</section>

<!-- MODAL INFO -->
<div class="modal" id="modal">
<div class="modal-content">
<span class="close" onclick="cerrar()">X</span>
<h2 id="t"></h2>
<img id="img">
<p id="txt"></p>
<button onclick="voz()">🎧 Escuchar</button>
</div>
</div>

<!-- ZOOM -->
<div class="zoom" id="zoom" onclick="cerrarZoom()">
<img id="zoomimg">
</div>

<footer>
<p>Museo Virtual - Nivel Final</p>
</footer>

<script>
// SCROLL + PROGRESS
const sections=document.querySelectorAll("section");
window.addEventListener("scroll",()=>{
sections.forEach(sec=>{
if(sec.getBoundingClientRect().top<window.innerHeight-100){
sec.classList.add("visible");
}
});
let s=document.documentElement.scrollTop;
let h=document.documentElement.scrollHeight-document.documentElement.clientHeight;
document.getElementById("progress").style.width=(s/h)*100+"%";
});

// EVENTO
function evento(t,txt,img){
document.getElementById("modal").style.display="flex";
document.getElementById("t").innerText=t;
document.getElementById("txt").innerText=txt;
document.getElementById("img").src=img;
document.getElementById("img").onclick=()=>zoom(img);
}

// AUDIO
function voz(){
let m=new SpeechSynthesisUtterance(document.getElementById("txt").innerText);
speechSynthesis.speak(m);
}

// ZOOM
function zoom(img){
document.getElementById("zoom").style.display="flex";
document.getElementById("zoomimg").src=img;
}
function cerrarZoom(){
document.getElementById("zoom").style.display="none";
}

// CERRAR
function cerrar(){
document.getElementById("modal").style.display="none";
}

// QUIZ
let score=0;
function res(r){
if(r==="bien"){score++;document.getElementById("resultado").innerText="✅ Correcto";}
else{document.getElementById("resultado").innerText="❌ Incorrecto";}
document.getElementById("score").innerText=score;
}

// TOUR GUIADO
function tour(){
alert("Iniciando recorrido...");
document.getElementById("timeline").scrollIntoView({behavior:'smooth'});
setTimeout(()=>evento('Rasputin','Figura clave del fin del Imperio ruso.','https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg'),2000);
}
</script>

</body>
</html>
