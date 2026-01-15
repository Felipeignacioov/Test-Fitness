<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Test de Alimentación | Zero Shake</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #f4fefe;
      color: #0f2f2f;
      margin: 0;
      padding: 20px;
    }

    .container {
      max-width: 600px;
      margin: auto;
      background: #ffffff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.08);
    }

    h1 {
      text-align: center;
      color: #00a6a6;
    }

    h2 {
      margin-top: 30px;
      font-size: 18px;
    }

    p {
      font-size: 15px;
      line-height: 1.5;
    }

    .question {
      margin-top: 25px;
    }

    label {
      display: block;
      margin: 8px 0;
      cursor: pointer;
    }

    button {
      margin-top: 30px;
      width: 100%;
      padding: 14px;
      font-size: 16px;
      background: #00a6a6;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    button:hover {
      background: #008b8b;
    }

    .result {
      display: none;
      margin-top: 30px;
      padding: 20px;
      border-radius: 10px;
    }

    .alerta { background: #ffecec; }
    .medio { background: #fff7db; }
    .bien { background: #e8fff1; }

    .cta {
      margin-top: 20px;
      text-align: center;
      font-weight: bold;
    }
  </style>
</head>

<body>

<div class="container">

  <h1>🥗 Test de Alimentación</h1>

  <p>
    Tu cuerpo te habla todos los días.<br>
    Este test no es para juzgarte, sino para ayudarte a entender
    <strong>qué tan bien lo estás cuidando hoy</strong>.
  </p>

  <form id="test">

    <!-- PREGUNTAS -->
    <div class="question">
      <h2>1. ¿Consumes alimentos reales la mayoría de los días?</h2>
      <label><input type="radio" name="q1" value="1"> Casi nunca</label>
      <label><input type="radio" name="q1" value="2"> A veces</label>
      <label><input type="radio" name="q1" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>2. ¿Incluyes proteína suficiente en tus comidas?</h2>
      <label><input type="radio" name="q2" value="1"> Casi nunca</label>
      <label><input type="radio" name="q2" value="2"> A veces</label>
      <label><input type="radio" name="q2" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>3. ¿Te sientes con energía estable durante el día?</h2>
      <label><input type="radio" name="q3" value="1"> Casi nunca</label>
      <label><input type="radio" name="q3" value="2"> A veces</label>
      <label><input type="radio" name="q3" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>4. ¿Evitas bajones fuertes de hambre o cansancio?</h2>
      <label><input type="radio" name="q4" value="1"> Casi nunca</label>
      <label><input type="radio" name="q4" value="2"> A veces</label>
      <label><input type="radio" name="q4" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>5. ¿Tu consumo de azúcar está bajo control?</h2>
      <label><input type="radio" name="q5" value="1"> Casi nunca</label>
      <label><input type="radio" name="q5" value="2"> A veces</label>
      <label><input type="radio" name="q5" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>6. ¿Tu alimentación ayuda a tu concentración y claridad mental?</h2>
      <label><input type="radio" name="q6" value="1"> Casi nunca</label>
      <label><input type="radio" name="q6" value="2"> A veces</label>
      <label><input type="radio" name="q6" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>7. ¿Tienes horarios más o menos ordenados para comer?</h2>
      <label><input type="radio" name="q7" value="1"> Casi nunca</label>
      <label><input type="radio" name="q7" value="2"> A veces</label>
      <label><input type="radio" name="q7" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>8. ¿Comes sin culpa ni extremos?</h2>
      <label><input type="radio" name="q8" value="1"> Casi nunca</label>
      <label><input type="radio" name="q8" value="2"> A veces</label>
      <label><input type="radio" name="q8" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>9. ¿Tu alimentación te acerca a la vida que quieres?</h2>
      <label><input type="radio" name="q9" value="1"> Casi nunca</label>
      <label><input type="radio" name="q9" value="2"> A veces</label>
      <label><input type="radio" name="q9" value="3"> Casi siempre</label>
    </div>

    <div class="question">
      <h2>10. ¿Crees que podrías sentirte mejor con pequeños ajustes?</h2>
      <label><input type="radio" name="q10" value="1"> Casi nunca</label>
      <label><input type="radio" name="q10" value="2"> A veces</label>
      <label><input type="radio" name="q10" value="3"> Casi siempre</label>
    </div>

    <button type="button" onclick="calcular()">Ver resultado</button>

  </form>

  <div id="resultado" class="result"></div>

</div>

<script>
function calcular() {
  let total = 0;
  for (let i = 1; i <= 10; i++) {
    const pregunta = document.querySelector(`input[name="q${i}"]:checked`);
    if (!pregunta) {
      alert("Responde todas las preguntas");
      return;
    }
    total += parseInt(pregunta.value);
  }

  const r = document.getElementById("resultado");
  r.style.display = "block";

  if (total <= 17) {
    r.className = "result alerta";
    r.innerHTML = `
      <h2>🔴 Tu cuerpo necesita apoyo</h2>
      <p>No estás fallando. Tu cuerpo simplemente necesita más cuidado y orden.</p>
      <p><strong>Zero Shake</strong> puede ayudarte a empezar de forma simple.</p>
    `;
  } else if (total <= 24) {
    r.className = "result medio";
    r.innerHTML = `
      <h2>🟡 Vas bien, pero puedes sentirte mejor</h2>
      <p>Tienes buenos hábitos, pero con pequeños ajustes podrías mejorar mucho.</p>
      <p><strong>Zero Shake</strong> es un gran apoyo diario.</p>
    `;
  } else {
    r.className = "result bien";
    r.innerHTML = `
      <h2>🟢 Estás alimentando bien a tu cuerpo</h2>
      <p>Tu alimentación está alineada con tu bienestar.</p>
      <p><strong>Zero Shake</strong> te ayuda a mantener y optimizar.</p>
    `;
  }

  r.innerHTML += `
    <div class="cta">
      ¿Quieres una recomendación personalizada?<br>
      Escríbenos y te ayudamos.
    </div>
  `;
}
</script>

</body>
</html>
