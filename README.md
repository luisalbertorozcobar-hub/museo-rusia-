# museo-rusia-
museo virtual de rusia sobre la segunda guerra mundial y rasputin 
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Museo Virtual: Historia de Rusia</title>
<style>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background: #0f0f0f;
    color: #f5f5f5;
}
header {
    background: linear-gradient(90deg, #8B0000, #300000);
    padding: 30px;
    text-align: center;
}
header h1 {
    margin: 0;
    font-size: 2.5em;
}
nav {
    background: #1c1c1c;
    padding: 10px;
    text-align: center;
    position: sticky;
    top: 0;
}
nav a {
    color: #fff;
    margin: 10px;
    text-decoration: none;
    font-weight: bold;
}
nav a:hover {
    color: #ff4444;
}
section {
    padding: 60px 20px;
    border-bottom: 1px solid #222;
    max-width: 1000px;
    margin: auto;
}
.card {
    background: #1a1a1a;
    padding: 20px;
    border-radius: 10px;
    margin-top: 20px;
    box-shadow: 0 0 10px rgba(255,0,0,0.2);
}
img {
    width: 100%;
    max-width: 500px;
    border-radius: 10px;
    margin-top: 10px;
}
footer {
    text-align: center;
    padding: 20px;
    background: #111;
    color: #777;
}
</style>
</head>
<body>

<header>
<h1>Museo Virtual de Rusia</h1>
<p>De Rasputin a la Segunda Guerra Mundial</p>
</header>

<nav>
<a href="#rasputin">Rasputin</a>
<a href="#revolucion">Revolución</a>
<a href="#guerra">Guerra Civil</a>
<a href="#stalin">Stalin</a>
<a href="#purga">Purgas</a>
<a href="#ww2">WW2</a>
</nav>

<section id="rasputin">
<h2>Rasputin y el fin del Imperio</h2>
<div class="card">
<p>Grigori Rasputin influyó en la familia Romanov y se convirtió en símbolo del colapso del Imperio ruso.</p>
<img src="https://upload.wikimedia.org/wikipedia/commons/7/7c/Rasputin_PA.jpg">
</div>
</section>

<section id="revolucion">
<h2>Revolución Rusa</h2>
<div class="card">
<p>En 1917, Lenin lideró la revolución bolchevique que cambió el destino de Rusia.</p>
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/Lenin.jpg">
</div>
</section>

<section id="guerra">
<h2>Guerra Civil Rusa</h2>
<div class="card">
<p>Rojos contra Blancos en una guerra que definió el futuro de la URSS.</p>
<img src="https://upload.wikimedia.org/wikipedia/commons/4/4c/Russian_civil_war.jpg">
</div>
</section>

<section id="stalin">
<h2>Stalin y el poder absoluto</h2>
<div class="card">
<p>Stalin consolidó un régimen autoritario con control total del Estado soviético.</p>
<img src="https://upload.wikimedia.org/wikipedia/commons/3/3c/Joseph_Stalin.jpg">
</div>
</section>

<section id="purga">
<h2>Purgas e industrialización</h2>
<div class="card">
<p>La URSS se industrializó rápidamente mientras millones fueron víctimas de las purgas.</p>
</div>
</section>

<section id="ww2">
<h2>Segunda Guerra Mundial</h2>
<div class="card">
<p>La Unión Soviética fue clave en la derrota de la Alemania nazi, especialmente en Stalingrado.</p>
<img src="https://upload.wikimedia.org/wikipedia/commons/7/7e/Stalingrad.jpg">
</div>
</section>

<footer>
<p>Museo Virtual de Historia de Rusia - Proyecto educativo</p>
</footer>

</body>
</html>
<section id="timeline">
    <div class="container">
        <h2>Línea de Tiempo Histórica</h2>

        <div class="cards">

            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/7/7c/Lenin_in_1920.jpg">
                <div class="card-content">
                    <h3>Lenin (1917)</h3>
                    <p>Líder de la Revolución Bolchevique y fundador de la Unión Soviética.</p>
                </div>
            </div>

            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/October_Revolution.jpg">
                <div class="card-content">
                    <h3>Revolución Rusa</h3>
                    <p>Caída del zarismo y nacimiento del comunismo en Rusia.</p>
                </div>
            </div>

            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/3/3e/Joseph_Stalin_1942.jpg">
                <div class="card-content">
                    <h3>Stalin</h3>
                    <p>Industrialización acelerada y control total del Estado soviético.</p>
                </div>
            </div>

            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/5/5c/Battle_of_Stalingrad.jpg">
                <div class="card-content">
                    <h3>Segunda Guerra Mundial</h3>
                    <p>La URSS derrota a la Alemania nazi en Stalingrado.</p>
                </div>
            </div>

        </div>
    </div>
</section>
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    margin-top: 30px;
}

.card {
    background: #1c1c1c;
    border-radius: 15px;
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
    cursor: pointer;
}

.card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.card-content {
    padding: 15px;
}

.card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 25px rgba(0,0,0,0.7);
}
