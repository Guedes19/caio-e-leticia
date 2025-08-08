
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Caio & Letícia</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Arial', sans-serif;
      color: #fff;
      background: url('fundo.jpg') no-repeat center center fixed;
      background-size: cover;
      position: relative;
      overflow-x: hidden;
    }

    body::before {
      content: '';
      position: fixed;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.6); /* fundo escuro */
      z-index: 0;
    }

    #hearts-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .heart {
      position: absolute;
      font-size: 24px;
      opacity: 1;
      animation: fall linear infinite;
    }

    @keyframes fall {
      0% {
        transform: translateY(-10px) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 1;
      }
    }

    .container {
      position: relative;
      z-index: 2;
      padding: 2rem;
      text-align: center;
    }

    h1 {
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    #countdown {
      font-size: 1.5rem;
      margin-bottom: 2rem;
    }

    button {
      padding: 10px 20px;
      font-size: 1rem;
      margin: 10px;
      cursor: pointer;
      border: none;
      border-radius: 5px;
    }

    #surpresa {
      display: none;
      margin-top: 2rem;
    }

    #surpresa img {
      max-width: 100%;
      height: auto;
      border-radius: 10px;
      margin-bottom: 1rem;
    }

    #mensagem {
      font-size: 1rem;
      white-space: pre-wrap;
      text-align: left;
      max-width: 500px;
      margin: auto;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 1.5rem;
      }

      #countdown {
        font-size: 1.2rem;
      }

      #mensagem {
        font-size: 0.9rem;
        padding: 0 1rem;
      }
    }
  </style>
</head>
<body>
  <div id="hearts-container"></div>

  <div class="container">
    <h1>Caio & Letícia</h1>
    <div id="countdown"></div>
    <button onclick="toggleAudio()">🎵 Tocar Música</button>
    <button onclick="mostrarSurpresa()">💌 Ver Surpresa</button>

    <div id="surpresa">
      <img src="foto-surpresa.jpg" alt="Foto Surpresa" />
      <p id="mensagem"></p>
    </div>
  </div>

  <audio id="audio" loop>
    <source src="space-time.mp3" type="audio/mpeg" />
    Seu navegador não suporta áudio.
  </audio>

  <script>
    // Temporizador
    const targetDate = new Date("2025-05-24T18:00:00").getTime();
    const countdown = document.getElementById("countdown");

    setInterval(() => {
      const now = new Date().getTime();
      const distance = targetDate - now;
      if (distance <= 0) {
        countdown.innerHTML = "Chegou o grande momento!";
        return;
      }
      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((distance % (1000 * 60)) / 1000);
      countdown.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
    }, 1000);

    // Música
    function toggleAudio() {
      const audio = document.getElementById("audio");
      audio.paused ? audio.play() : audio.pause();
    }

    // Máquina de escrever
    function mostrarSurpresa() {
      const surpresa = document.getElementById("surpresa");
      const mensagem = document.getElementById("mensagem");
      const texto = `Minha princesa, este temporizador marca o início oficial de nosso relacionamento diante de Deus e dos homens; E há quanto tempo eu sou o homem mais feliz, rico e sortudo desse universo.

Que essa simples página - mas dotada de muito amor e carinho - esteja acessível em qualquer dia, horas e lugar para nos (re)lembrar de quão maravilhoso é o nosso amor e que ele rompe qualquer barreira, passa por cima de qualquer empecilho e expulsa qualquer medo e orgulho, pois, com Cristo no barco, tudo vai muito bem.

E saiba que te honro, te admiro, te zelo, me inspiro em vocẽ e, por onde for, quero ser seu par.

Que sempre lembremos e creiamos nisto: “Nenhum de nós é tão bom quanto nós dois juntos!”

Te amo... Muitão!

Com muito amor, zelo, carinho, afeto e admiração, Seu amigo, parceiro e namorado: Caio.`;

      surpresa.style.display = "block";
      mensagem.textContent = "";
      let index = 0;
      const intervalo = setInterval(() => {
        if (index < texto.length) {
          mensagem.textContent += texto.charAt(index);
          index++;
        } else {
          clearInterval(intervalo);
        }
      }, 40);
    }

    // Corações caindo
    const heartContainer = document.getElementById("hearts-container");
    const cores = ['💚', '💜'];

    function criarCoracao() {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (6 + Math.random() * 2) + 's';
      heart.innerHTML = cores[Math.floor(Math.random() * cores.length)];
      heart.style.opacity = '1';
      heartContainer.appendChild(heart);

      setTimeout(() => heart.remove(), 8000);
    }

    setInterval(criarCoracao, 300);
  </script>
</body>
</html>
