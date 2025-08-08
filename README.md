
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background: linear-gradient(to right, #ffecd2, #fcb69f);
      font-family: 'Arial', sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }
    h1 {
      font-size: 3em;
      margin-top: 40px;
      color: #333;
    }
    p {
      font-size: 1.2em;
      margin-bottom: 20px;
      color: #444;
    }
    .timer {
      font-size: 2em;
      font-weight: bold;
      margin-top: 20px;
      color: #222;
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
      margin-top: 20px;
    }
    button:hover {
      background-color: #ff4500;
    }
  </style>
</head>
<body>

  <h1>💖 Caio & Letícia 💖</h1>
  <p><strong>Música:</strong> Space & Time - Rafael Witt</p>

  <div class="timer" id="timer"></div>

  <button id="btnMusica" onclick="controlarMusica()">▶ Tocar Música</button>

  <audio id="musica" loop>
    <source src="musica.mp3" type="audio/mpeg">
    Seu navegador não suporta áudio.
  </audio>

  <script>
    // Data correta: 18h de 24 de maio de 2025
    const dataInicio = new Date("2025-05-24T18:00:00");
    const timer = document.getElementById('timer');

    function atualizarTempo() {
      const agora = new Date();
      const diff = agora - dataInicio;

      const dias = Math.floor(diff / (1000 * 60 * 60 * 24));
      const horas = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutos = Math.floor((diff / (1000 * 60)) % 60);
      const segundos = Math.floor((diff / 1000) % 60);

      timer.textContent = `${dias}d ${horas}h ${minutos}m ${segundos}s juntos 💕`;
    }

    setInterval(atualizarTempo, 1000);
    atualizarTempo();

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
  </script>

</body>
</html>
