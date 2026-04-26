<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Museo Virtual de Rusia - Nivel Extremo</title>

<style>
body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:#0a0a0a;
color:white;
scroll-behavior:smooth;
}

/* BARRA PROGRESO */
#progress{
position:fixed;
top:0;
left:0;
height:5px;
background:red;
width:0%;
z-index:2000;
}

/* HEADER */
header{
background:linear-gradient(120deg,#8b0000,#000);
padding:80px 20px;
text-align:center;
}
header h1{margin:0;font-size:3em}

/* NAV */
nav{
position:sticky;
top:0;
background:#111;
padding:10px;
text-align:center;
z-index:1000;
}
nav a{
color:white;
margin:10px;
text-decoration:none;
}
nav a:hover{color:red}

/* SECTIONS */
section{
padding:80px 20px;
max-width:1100px;
margin:auto;
opacity:0;
transform:translateY(40px);
transition:.6s;
}
section.visible{
opacity:1;
transform:translateY(0);
}

/* CARDS */
.cards{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:25px;
}
.card{
background:#1a1a1a;
border-radius:15px;
overflow:hidden;
cursor:pointer;
transition:.3s;
}
.card:hover{transform:scale(1.05);}
.card img{
width:100%;
height:200px;
object-fit:cover;
}
.card h3{padding:15px;}

/* MODAL */
.modal{
display:none;
position:fixed;
top:0;left:0;
width:100%;height:100%;
background:rgba(0,0,0,.9);
justify-content:center;
align-items:center;
}
.modal-content{
background:#111;
padding:20px;
border-radius:10px;
max-width:600px;
text-align:center;
}
.modal img{width:100%;}
.close{cursor:pointer;color:red;font-size:20px}

/* MAPA */
iframe{
width:100%;
height:400px;
border:none;
border-radius:10px;
}

/* VIDEO */
video{
width:100%;
border-radius:10px;
}

/* FOOTER */
footer{
text-align:center;
padding:20px;
background:#111;
}
</style>

</head>
<body>

<div id="progress"></div>

<header>
<h1>Museo Virtual de Rusia</h1>
<p>Experiencia interactiva completa</p>
</header>

<nav>
<a href="#inicio">Inicio</a>
<a href="#timeline">Historia</a>
<a href="#mapa">Mapa</a>
<a href="#video">Video</a>
</nav>

<section id="inicio" class="visible">
<h2>Bienvenido</h2>
<p>Recorre la historia de Rusia como si estuvieras en un museo real.</p>
<button onclick="hablar()">🎧 Escuchar guía</button>
</section>

<section id="timeline">
<h2>Línea de Tiempo</h2>

<div class="cards">

<div class="card" onclick="openModal('Rasputin','Figura clave antes de la revolución.','https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg">
<h3>Rasputin</h3>
</div>

<div class="card" onclick="openModal('Revolución Rusa','1917 cambia la historia.','https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg">
<h3>Revolución</h3>
</div>

<div class="card" onclick="openModal('Stalin','Control total del Estado.','https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg">
<h3>Stalin</h3>
</div>

<div class="card" onclick="openModal('WW2','Victoria en Stalingrado.','https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg')">
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg">
<h3>WW2</h3>
</div>

</div>
</section>

<section id="mapa">
<h2>Mapa interactivo</h2>
<iframe src="https://www.google.com/maps?q=Rusia&output=embed"></iframe>
</section>

<section id="video">
<h2>Video histórico</h2>
<video controls>
<source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
</video>
</section>

<!-- MODAL -->
<div class="modal" id="modal">
<div class="modal-content">
<span class="close" onclick="closeModal()">X</span>
<h2 id="modal-title"></h2>
<img id="modal-img">
<p id="modal-text"></p>
</div>
</div>

<footer>
<p>Museo Virtual - Nivel Extremo</p>
</footer>

<script>
// SCROLL ANIMATION
const sections=document.querySelectorAll("section");
window.addEventListener("scroll",()=>{
sections.forEach(sec=>{
const top=sec.getBoundingClientRect().top;
if(top<window.innerHeight-100){
sec.classList.add("visible");
}
});

// PROGRESS BAR
let scrollTop=document.documentElement.scrollTop;
let height=document.documentElement.scrollHeight-document.documentElement.clientHeight;
document.getElementById("progress").style.width=(scrollTop/height)*100+"%";
});

// MODAL
function openModal(t,txt,img){
document.getElementById("modal").style.display="flex";
document.getElementById("modal-title").innerText=t;
document.getElementById("modal-text").innerText=txt;
document.getElementById("modal-img").src=img;
}
function closeModal(){
document.getElementById("modal").style.display="none";
}

// AUDIO GUÍA
function hablar(){
let msg=new SpeechSynthesisUtterance("Bienvenido al museo virtual de Rusia.");
speechSynthesis.speak(msg);
}
</script>

</body>
</html>
