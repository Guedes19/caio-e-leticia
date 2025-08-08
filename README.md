
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Arial', sans-serif;
      overflow-x: hidden;
      color: white;
      text-align: center;
    }

    /* Fundo com escurecimento por sobreposição */
    body::before {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.5); /* escurecimento */
      z-index: -1;
    }

    body::after {
      content: "";
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: url('fundo.jpg') no-repeat center center fixed;
      background-size: cover;
      z-index: -2;
    }

    h1 {
      font-size: 3em;
      margin-top: 40px;
      text-shadow: 1px 1px 4px black;
    }

    p {
      font-size: 1.2em;
      margin-bottom: 20px;
      text-shadow: 1px 1px 3px black;
    }

    .timer {
      font-size: 2em;
      font-weight: bold;
      margin-top: 20px;
      text-shadow: 1px 1px 3px black;
    }

    button {
      background-color: #ff7f50;
      color: white;
      border: none;
      padding: 15px 30px;
      font-size: 18px;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
      margin: 15px 10px;
      z-index: 1;
      position: relative;
    }

    button:hover {
      background-color: #ff4500;
    }

    .emoji {
      position: fixed;
      top: -2em;
      font-size: 24px;
      opacity: 1; /* 100% visível */
      animation: cair linear forwards;
      pointer-events: none;
      z-index: -1; /* atrás de tudo, exceto o fundo */
    }

    @keyframes cair {
      to {
        transform: translateY(100vh);
        opacity: 0;
      }
    }

    .foto-surpresa {
      margin-top: 20px;
      display: none;
      max-width: 90%;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
    }
  </style>
</head>
<body>

  <h1>💖 Caio & Letícia 💖</h1>
  <p><strong>Música:</strong> Space & Time - Rafael Witt</p>

  <div class="timer" id="timer"></div>

  <button id="btnMusica" onclick="controlarMusica()">▶ Tocar Música</button>
  <button onclick="mostrarFoto()">📸 Ver uma surpresa</button>

  <img id="fotoSurpresa" class="foto-surpresa" src="foto-surpresa.jpg" alt="Nossa Foto Juntos" />

  <audio id="musica" loop>
    <source src="musica.mp3" type="audio/mpeg">
    Seu navegador não suporta áudio.
  </audio>

  <script>
    // Timer
    const dataInicio = new Date("2025-05-24T18:00:00");
    const timer = document.getElementById('timer');

    function atualizarTempo() {
      const agora = new Date();
      const diff = agora - dataInicio;

      if (diff < 0) {
        timer.textContent = "Contagem ainda não começou 💞";
        return;
      }

      const dias = Math.floor(diff / (1000 * 60 * 60 * 24));
      const horas = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutos = Math.floor((diff / (1000 * 60)) % 60);
      const segundos = Math.floor((diff / 1000) % 60);

      timer.textContent = `${dias}d ${horas}h ${minutos}m ${segundos}s juntos 💕`;
    }

    setInterval(atualizarTempo, 1000);
    atualizarTempo();

    // Música
    const audio = document.getElementById('musica');
    const botao = document.getElementById('btnMusica');

    function controlarMusica() {
      if (audio.paused) {
        audio.play();
        botao.textContent = "⏸ Pausar Música";
      } else {
        audio.pause();
        botao.textContent = "▶ Tocar Música";
      }
    }

    // Mostrar foto surpresa
    function mostrarFoto() {
      const img = document.getElementById('fotoSurpresa');
      img.style.display = 'block';
    }

    // Chuva de corações
    const coracoes = ['💚', '💜'];

    function criarCoracao() {
      const emoji = document.createElement('div');
      emoji.classList.add('emoji');
      emoji.textContent = coracoes[Math.floor(Math.random() * coracoes.length)];
      emoji.style.left = `${Math.random() * 100}vw`;
      emoji.style.animationDuration = `${3 + Math.random() * 2}s`;
      emoji.style.fontSize = `${20 + Math.random() * 10}px`;
      document.body.appendChild(emoji);

      setTimeout(() => emoji.remove(), 6000);
    }

    setInterval(criarCoracao, 250);
  </script>

</body>
</html>
