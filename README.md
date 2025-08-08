
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      padding: 0;
      overflow-x: hidden;
      font-family: 'Arial', sans-serif;
      text-align: center;
      position: relative;
      color: white;
    }
    /* Fundo escurecido + imagem de fundo */
    body::before {
      content: "";
      background: url('fundo.jpg') no-repeat center center fixed;
      background-size: cover;
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      opacity: 0.5; /* escurece */
      z-index: -2;
    }
    .hearts {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: -1; /* atrás dos botões e texto */
    }
    .heart {
      position: absolute;
      font-size: 24px;
      opacity: 1;
      animation: cair 3s linear infinite;
    }
    @keyframes cair {
      0% {
        transform: translateY(-10vh);
      }
      100% {
        transform: translateY(110vh);
      }
    }
    h1, p.timer, button {
      position: relative;
      z-index: 1;
      text-shadow: 1px 1px 3px black;
    }
    button {
      background-color: #ff7f50;
      color: white;
      border: none;
      padding: 12px 25px;
      font-size: 18px;
      border-radius: 8px;
      cursor: pointer;
      margin: 10px;
    }
    #surpresaContainer {
      display: none;
      position: relative;
      z-index: 1;
      margin-top: 30px;
    }
    .foto-surpresa {
      max-width: 300px;
      border-radius: 20px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.6);
    }
    #textoMaquina {
      white-space: pre-wrap;
      font-size: 1.2em;
      margin-top: 20px;
      padding: 0 20px;
      color: white;
      text-shadow: 1px 1px 3px black;
    }
  </style>
</head>
<body>
  <div class="hearts" id="heartsContainer"></div>

  <h1>💖 Caio & Letícia 💖</h1>
  <p><strong>Música:</strong> Space & Time - Rafael Witt</p>
  <p class="timer" id="timer"></p>
  <button id="btnMusica" onclick="controlarMusica()">▶ Tocar Música</button>
  <button onclick="mostrarFoto()">🎁 Ver Surpresa</button>

  <audio id="musica" loop>
    <source src="musica.mp3" type="audio/mpeg">
    Seu navegador não suporta áudio.
  </audio>

  <div id="surpresaContainer">
    <img class="foto-surpresa" src="foto-surpresa.jpg" alt="Nossa Foto Juntos">
    <p id="textoMaquina"></p>
  </div>

  <script>
    const dataInicio = new Date("2025-05-24T18:00:00");
    const timer = document.getElementById('timer');
    setInterval(() => {
      const diff = Date.now() - dataInicio;
      const dias = Math.floor(diff / (1000*60*60*24));
      const horas = Math.floor((diff / (1000*60*60)) % 24);
      const minutos = Math.floor((diff / (1000*60)) % 60);
      const segundos = Math.floor((diff / 1000) % 60);
      timer.textContent = `${dias}d ${horas}h ${minutos}m ${segundos}s juntos 💕`;
    }, 1000);

    const audio = document.getElementById('musica');
    const btn = document.getElementById('btnMusica');
    btn.addEventListener('click', () => {
      if (audio.paused) {
        audio.play();
        btn.textContent = "⏸ Pausar Música";
      } else {
        audio.pause();
        btn.textContent = "▶ Tocar Música";
      }
    });

    function mostrarFoto() {
      const container = document.getElementById('surpresaContainer');
      const texto = `Minha princesa, este temporizador marca o início oficial de nosso relacionamento diante de Deus e dos homens... (seu texto completo aqui)`;
      const el = document.getElementById('textoMaquina');
      container.style.display = 'block';
      el.textContent = '';
      let i = 0;
      const id = setInterval(() => {
        el.textContent += texto[i++];
        if (i >= texto.length) clearInterval(id);
      }, 25);
    }

    const heartsContainer = document.getElementById('heartsContainer');
    const emojis = ['💚', '💜'];
    setInterval(() => {
      const h = document.createElement('div');
      h.className = 'heart';
      h.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      h.style.left = Math.random() * 100 + 'vw';
      h.style.animationDuration = 3 + Math.random() * 2 + 's';
      heartsContainer.appendChild(h);
      setTimeout(() => heartsContainer.removeChild(h), 5000);
    }, 300);
  </script>
</body>
</html>
