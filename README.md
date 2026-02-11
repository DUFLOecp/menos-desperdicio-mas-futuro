<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Menos Desperdicio, Más Futuro</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
    margin:0;
    font-family: 'Segoe UI', Arial, sans-serif;
    background:#f4f6f5;
    color:#333;
}
header{
    background:#ffffff;
    padding:15px 30px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    border-bottom:4px solid #2e7d32;
}
header img{
    height:55px;
}
header h1{
    font-size:20px;
    color:#2e7d32;
    text-align:center;
    margin:0;
    flex:1;
}

.contenedor{
    max-width:520px;
    margin:30px auto;
    background:#ffffff;
    padding:30px;
    border-radius:14px;
    box-shadow:0 6px 15px rgba(0,0,0,0.1);
}

h2{
    text-align:center;
    color:#c62828;
    margin-bottom:10px;
}
.subtitulo{
    text-align:center;
    font-size:14px;
    margin-bottom:25px;
    color:#555;
}

label{
    font-weight:bold;
    display:block;
    margin-bottom:8px;
}
input{
    width:100%;
    padding:12px;
    font-size:18px;
    border-radius:8px;
    border:1px solid #ccc;
    margin-bottom:20px;
}

button{
    width:100%;
    background:#2e7d32;
    color:#fff;
    font-size:18px;
    padding:14px;
    border:none;
    border-radius:10px;
    cursor:pointer;
}
button:hover{
    background:#256428;
}

.resultado{
    margin-top:25px;
    background:#eef5f0;
    padding:20px;
    border-radius:12px;
}
.resultado p{
    font-size:16px;
    margin:10px 0;
}

.destacado{
    font-size:18px;
    font-weight:bold;
    color:#c62828;
    margin-top:15px;
    text-align:center;
}

.footer{
    text-align:center;
    font-size:13px;
    color:#555;
    margin-top:20px;
}
</style>
</head>

<body>

<header>
    <img src="ecopetrol.png" alt="Ecopetrol">
    <h1>MENOS DESPERDICIO, MÁS FUTURO</h1>
    <img src="duflo.png" alt="Duflo Servicios Integrales">
</header>

<div class="contenedor">

<h2>Impacto del Desperdicio de Alimentos</h2>
<p class="subtitulo">
Cada kilogramo de alimento desperdiciado consume recursos vitales y genera emisiones innecesarias.
</p>

<label for="peso">Peso del alimento desechado (kg)</label>
<input type="number" id="peso" step="0.01" placeholder="Ejemplo: 1.50">

<button onclick="calcularImpacto()">Calcular impacto</button>

<div class="resultado" id="resultado" style="display:none;">
    <p>💧 <strong>Agua utilizada:</strong> <span id="agua"></span> litros</p>
    <p>⚡ <strong>Energía utilizada:</strong> <span id="energia"></span> kWh</p>
    <p>🌫️ <strong>Emisiones de CO₂:</strong> <span id="co2"></span> kg</p>
    <p>🍽️ <strong>Personas que pudieron alimentarse:</strong> <span id="personas"></span></p>

    <p class="destacado">
        Este desperdicio pudo haberse convertido en alimento y bienestar.
    </p>
</div>

<div class="footer">
Campaña ambiental – Duflo Servicios Integrales & Ecopetrol
</div>

</div>

<script>
function calcularImpacto(){

    let peso = parseFloat(document.getElementById("peso").value);
    if(isNaN(peso) || peso <= 0){
        alert("Ingresa un peso válido.");
        return;
    }

    let agua = peso * 1300;
    let energia = peso * 4;
    let co2 = peso * 2.5;
    let personas = peso / 0.5;

    document.getElementById("agua").innerText = agua.toFixed(0);
    document.getElementById("energia").innerText = energia.toFixed(2);
    document.getElementById("co2").innerText = co2.toFixed(2);
    document.getElementById("personas").innerText = personas.toFixed(0);

    document.getElementById("resultado").style.display = "block";

    fetch("https://script.google.com/macros/s/AKfycbw_-Ggeo7cqC20fZQP5M2UJz38pE0oOGxkadQjkdNGfpSw4elBBx_ugg8JP_D632m16/exec",{
        method:"POST",
        body:JSON.stringify({
            peso:peso,
            agua:agua,
            energia:energia,
            co2:co2,
            personas:personas,
            fecha:new Date().toISOString()
        })
    });
}
</script>

</body>
</html>
