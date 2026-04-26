<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Museo Virtual de Rusia - Experto Final</title>

<style>
body{margin:0;font-family:sans-serif;background:#0a0a0a;color:white}
header{background:#8b0000;padding:40px;text-align:center}
nav{background:#111;padding:10px;text-align:center}
nav button{margin:5px;padding:10px;cursor:pointer}
.sala{display:none;padding:40px;max-width:1000px;margin:auto}
.sala.active{display:block}
.card{background:#1a1a1a;padding:15px;margin:10px;border-radius:10px;cursor:pointer}
.card:hover{background:#333}
.mapa div{display:inline-block;background:#222;padding:20px;margin:10px;cursor:pointer}
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.9);justify-content:center;align-items:center;}
.modal-content{background:#111;padding:20px;border-radius:10px;max-width:600px;text-align:center;}
.close{color:red;cursor:pointer}
button{margin:5px;padding:10px}
footer{text-align:center;padding:20px;background:#111}
</style>

</head>
<body>

<header>
<h1>Museo Virtual de Rusia</h1>
<p>Experiencia completa con contenido histórico</p>
<button onclick="tour()">🧭 Recorrido automático</button>
</header>

<nav>
<button onclick="ir('sala1')">Imperio</button>
<button onclick="ir('sala2')">Revolución</button>
<button onclick="ir('sala3')">Stalin</button>
<button onclick="ir('sala4')">WW2</button>
<button onclick="ir('mapa')">Mapa</button>
<button onclick="ir('quiz')">Quiz</button>
</nav>

<!-- SALA 1 -->
<div id="sala1" class="sala active">
<h2>Imperio Ruso</h2>
<p>Antes de la revolución, Rusia era un imperio gobernado por el zar Nicolás II. La desigualdad social, la pobreza y la falta de reformas provocaron descontento.</p>

<div class="card" onclick="evento('Rasputin','Grigori Rasputin fue un místico que ganó influencia sobre la familia Romanov. Su presencia debilitó la confianza en el gobierno y contribuyó a la caída del imperio.','https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg')">
Rasputin
</div>
</div>

<!-- SALA 2 -->
<div id="sala2" class="sala">
<h2>Revolución Rusa</h2>
<p>En 1917, el pueblo ruso se rebeló contra el gobierno. Las causas incluyeron hambre, participación en la Primera Guerra Mundial y desigualdad económica.</p>

<div class="card" onclick="evento('Revolución Rusa','La Revolución de Octubre fue liderada por Lenin y los bolcheviques, quienes establecieron el primer estado comunista del mundo.','https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg')">
Revolución 1917
</div>
</div>

<!-- SALA 3 -->
<div id="sala3" class="sala">
<h2>Stalin y la URSS</h2>
<p>Tras la muerte de Lenin, Stalin tomó el poder. Implementó planes industriales y colectivización agrícola, pero también realizó purgas políticas.</p>

<div class="card" onclick="evento('Stalin','Joseph Stalin gobernó con mano dura. Durante su régimen, millones de personas fueron enviadas a campos de trabajo llamados gulags.','https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg')">
Gobierno de Stalin
</div>
</div>

<!-- SALA 4 -->
<div id="sala4" class="sala">
<h2>Segunda Guerra Mundial</h2>
<p>La Unión Soviética jugó un papel crucial en la derrota de la Alemania nazi. La batalla de Stalingrado fue uno de los puntos decisivos.</p>

<div class="card" onclick="evento('Stalingrado','La batalla de Stalingrado (1942-1943) fue una de las más sangrientas de la historia y marcó el inicio de la derrota alemana.','https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg')">
Batalla de Stalingrado
</div>

<iframe width="100%" height="300"
src="https://www.youtube.com/embed/1CqGeAmVu1I"
title="Historia de la URSS" allowfullscreen></iframe>

</div>

<!-- MAPA -->
<div id="mapa" class="sala">
<h2>Mapa interactivo</h2>
<p>Explora lugares clave en la historia de Rusia.</p>

<div class="mapa">
<div onclick="evento('Moscú','Capital de Rusia y centro político e histórico.','https://upload.wikimedia.org/wikipedia/commons/e/e3/Moscow.jpg')">Moscú</div>
<div onclick="evento('Stalingrado','Escenario de una de las batallas más importantes de la Segunda Guerra Mundial.','https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg')">Stalingrado</div>
</div>
</div>

<!-- QUIZ -->
<div id="quiz" class="sala">
<h2>Quiz Final</h2>

<p>1. ¿Quién lideró la Revolución Rusa?</p>
<button onclick="check('mal')">Stalin</button>
<button onclick="check('bien')">Lenin</button>

<p>2. ¿Qué batalla fue clave en la Segunda Guerra Mundial?</p>
<button onclick="check('bien')">Stalingrado</button>
<button onclick="check('mal')">Londres</button>

<p>Puntaje: <span id="score">0</span></p>
</div>

<!-- MODAL -->
<div class="modal" id="modal">
<div class="modal-content">
<span class="close" onclick="cerrar()">X</span>
<h2 id="t"></h2>
<img id="img" style="width:100%">
<p id="txt"></p>
<button onclick="voz()">🎧 Escuchar</button>
</div>
</div>

<footer>
<p>Fuentes: Wikipedia y material histórico educativo</p>
</footer>

<script>
let score=0;

// navegación
function ir(id){
document.querySelectorAll('.sala').forEach(s=>s.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

// eventos
function evento(t,txt,img){
document.getElementById("modal").style.display="flex";
document.getElementById("t").innerText=t;
document.getElementById("txt").innerText=txt;
document.getElementById("img").src=img;
}

// audio
function voz(){
let m=new SpeechSynthesisUtterance(document.getElementById("txt").innerText);
speechSynthesis.speak(m);
}

// cerrar
function cerrar(){document.getElementById("modal").style.display="none";}

// quiz
function check(r){
if(r==="bien"){score++;}
document.getElementById("score").innerText=score;
}

// tour
function tour(){
alert("Recorrido iniciado");
let salas=["sala1","sala2","sala3","sala4"];
let i=0;
let intervalo=setInterval(()=>{
if(i>=salas.length){clearInterval(intervalo);return;}
ir(salas[i]);
i++;
},3000);
}
</script>

</body>
</html>
