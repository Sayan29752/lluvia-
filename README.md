<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Linda nocheeeeeeeeee</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
      font-family: Arial, sans-serif;
      color: white;
      text-align: center;
      background: transparent; /* 🔧 Quitamos fondo negro */
    }

    /* Video de fondo */
    #bgVideo {
      position: fixed;
      top: 50%;
      left: 50%;
      min-width: 100%;
      min-height: 100%;
      width: auto;
      height: auto;
      transform: translate(-50%, -50%);
      z-index: -1;
      filter: brightness(0.7);
    }

    /* Botón centrado */
    .boton {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px 40px;
      font-size: 24px;
      background-color: rgba(255, 64, 129, 0.9);
      color: white;
      border

    }
    .boton:hover {
      transform: translate(-50%, -50%) scale(1.1);
    }

    /* Contenedor del mensaje */
    .mensaje {
      opacity: 0;
      transition: opacity 1s;
      position: absolute;
      top: 20%;
      width: 100%;
      z-index: 2;
    }

    /* Líneas de texto */
    .linea {
      opacity: 0;
      margin: 15px 0;
      transition: opacity 2s ease-in-out;
      font-size: 30px;
      text-shadow: 0 0 15px white;
    }
    .linea.visible {
      opacity: 1 !important;
    }

    /* Contenedor para la animación de la última línea */
    #textoAnimado p {
      margin: 10px 0;
    }
  </style>
</head>
<body>

  <!-- Video de fondo -->
  <video id="bgVideo" autoplay muted loop playsinline>
    <source src="lluvia de estrellas.mp4" type="video/mp4" />
    Tu navegador no soporta video de fondo.
  </video>

  <!-- Botón -->
  <button class="boton" onclick="mostrarMensaje()">DA CLICK AQUÍ</button>

  <!-- Mensaje -->
  <div class="mensaje" id="mensaje">
    <div class="linea" id="linea1">NO TE VI</div>
    <div class="linea" id="linea2">PERO SÉ QUE HOY ESTUVISTE TAN BONITA :D</div>
    <div class="linea" id="linea3">QUE LE DAS CELOS AL CIELO</div>
    <div class="linea" id="linea4">Esperaaaa........</div>
    <div class="linea" id="linea5"><div id="textoAnimado"></div></div>
  </div>

  <!-- Audio -->
  <audio id="musica" src="La Mujer Perfecta.mp3" preload="auto"></audio>

  <script>
    const musica = document.getElementById('musica');

    function mostrarMensaje() {
      // Intentar reproducir audio
      musica.play().catch(err => {
        alert("No se pudo reproducir el audio automáticamente. Por favor, activa el sonido o inténtalo en otro navegador.");
        console.log(err);
      });

      // Ocultar botón
      document.querySelector('.boton').style.display = 'none';

      // Mostrar contenedor mensaje
      const mensaje = document.getElementById('mensaje');
      mensaje.style.opacity = 1;

      // Animar líneas una por una
      setTimeout(() => document.getElementById('linea1').classList.add('visible'), 1000);
      setTimeout(() => document.getElementById('linea2').classList.add('visible'), 4000);
      setTimeout(() => document.getElementById('linea3').classList.add('visible'), 7000);
      setTimeout(() => document.getElementById('linea4').classList.add('visible'), 9000);
      setTimeout(() => escribirLinea5(), 14000);
    }

    // Versos para la última línea animada
    const versos = [
      "En la noche, tu luz es la más brillante.",
      "Más que mil estrellas en el cielo distante.",
      "Tu sonrisa eclipsa la luna y su reflejo,",
      "y tu belleza hace al universo pequeño."
    ];

    function escribirLinea5() {
      const contenedor = document.getElementById("textoAnimado");
      let versoIndex = 0;

      document.getElementById('linea5').classList.add('visible');

      function escribirVerso() {
        if (versoIndex >= versos.length) return;

        const verso = versos[versoIndex];
        let letraIndex = 0;
        const p = document.createElement("p");
        contenedor.appendChild(p);

        const intervalo = setInterval(() => {
          if (letraIndex < verso.length) {
            p.textContent += verso[letraIndex];
            letraIndex++;
          } else {
            clearInterval(intervalo);
            versoIndex++;
            setTimeout(escribirVerso, 500);
          }
        }, 50);
      }

      escribirVerso();
    }
  </script>

</body>
</html>
