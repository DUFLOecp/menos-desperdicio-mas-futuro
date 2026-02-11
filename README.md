<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Menos Desperdicio, Más Futuro</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700;800&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Montserrat', sans-serif;
    background-color: #f4f7f6;
}

.header {
    background: #ffffff;
    border-bottom: 4px solid #2e7d32;
    padding: 15px 25px;
}

.header-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    height: 55px;
}

.titulo-campaña {
    text-align: center;
    margin: 15px 0 5px;
    font-size: 36px;
    font-weight: 800;
    color: #2e7d32;
}

.subtitulo {
    text-align: center;
    font-size: 16px;
    color: #555;
    margin-bottom: 10px;
}

.contenedor {
    max-width: 420px;
    margin: 40px auto;
    background: white;
    padding: 30px;
    border-radius: 16px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.12);
}

h2 {
    text-align: center;
    color: #c62828;
    font-size: 22px;
}

label {
    font-weight: 600;
}

input {
    width: 100%;
    padding: 12px;
    margin-top: 8px;
    margin-bottom: 18px;
    font-size: 16px;
    border-radius: 8px;
    border: 1px solid #ccc;
}

button {
    width: 100%;
    padding: 14px;
    background-color: #2e7d32;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 17px;
    font-weight: 700;
    cursor: pointer;
}

button:hover {
    background-color: #256428;
}

.resultado {
    margin-top: 25px;
    background: #eef5f0;
    padding: 18px;
    border-radius: 10px;
}

.resultado p {
    font-size: 15px;
    margin: 12px 0;
}

.mensaje {
    margin-top: 15px;
    font-size: 13px;
    color: #444;
    text-align: center;
}
</style>
</head>

<body>

<div class="header">
    <div class="header-top">
        <img src="ecopetrol.png" class="logo" alt="Ecopetrol">
        <img src="duflo.png" class="logo" alt="Duflo Servicios Integrales">
    </div>

    <div class="titulo-campaña">MENOS DESPERDICIO, MÁS FUTURO</div>
    <div class="subtitulo">
        Concientización sobre el impacto ambiental del desperdicio de alimentos
    </div>
</div>

<div class="contenedor">
    <h2>Impacto del Desperdicio de Alimentos</h2>

    <label for="peso">Peso del alimento desechado (kg)</label>
    <input type="number" id="peso" step="0.01" placeholder="Ejemplo: 1.50">

    <button onclick="calcularImpacto()">Calcular impacto</button>

    <div class="resultado" id="resultado" style="display:none;">
        <p>💧 <strong>Agua utilizada:</strong> <span id="agua"></span> litros</p>
        <p>⚡ <strong>Energía utilizada:</strong> <span id="energia"></span> kWh</p>
        <p>🌫️ <strong>Emisiones de CO₂:</strong> <span id="co2"></span> kg</p>

        <div class="mensaje">
            Cada residuo cuenta. Reducir el desperdicio protege el agua, la energía y el clima.
        </div>
    </div>
</div>

<script>
function calcularImpacto() {
    const peso = parseFloat(document.getElementById("peso").value);

    if (isNaN(peso) || peso <= 0) {
        alert("Ingresa un peso válido.");
        return;
    }

    const agua = peso * 1300;
    const energia = peso * 4;
    const co2 = peso * 2.5;

    document.getElementById("agua").innerText = agua.toFixed(0);
    document.getElementById("energia").innerText = energia.toFixed(2);
    document.getElementById("co2").innerText = co2.toFixed(2);

    document.getElementById("resultado").style.display = "block";

    fetch("https://script.google.com/macros/s/AKfycbwWXSt7hiZdFdKWl-UFc2SM8jKd9qUR9q8LZ0hGOKIyhvo_ASnOlYbbmUvgkVYmQ-4e/exec", {
        method: "POST",
        body: JSON.stringify({
            peso: peso,
            agua: agua,
            energia: energia,
            co2: co2
        })
    });
}
</script>

</body>
</html>
