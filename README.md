
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
      background: linear-gradient(to right, #c59e94, #e4b49f);
      position: relative;
      color: #fff;
      text-align: center;
    }

    .overlay {
      position: fixed;
      z-index: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
      pointer-events: none;
    }

    .heart {
      position: absolute;
      font-size: 24px;
      opacity: 1;
      animation: float 10s linear infinite;
    }

    @keyframes float {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translateY(-10vh) rotate(360deg);
        opacity: 1;
      }
    }

    h1 {
      font-size: 3em;
      margin-top: 40px;
      z-index: 1;
      position: relative;
    }

    p {
      font-size: 1.2em;
      margin-bottom: 20px;
      z-index: 1;
      position: relative;
    }

    .timer {
      font-size: 2em;
      font-weight: bold;
      margin-top: 20px;
      z-index: 1;
      position: relative;
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
      margin: 10px;
      z-index: 1;
      position: relative;
    }

    button:hover {
      background-color: #ff4500;
    }

    #surpresaContainer {
      display: none;
      margin-top: 40px;
      z-index: 2;
      position: relative;
      padding: 20px;
    }

    .foto-surpresa {
      max-width: 300px;
      border-radius: 20px;
      box-shadow: 0 0 15px rgba(0,0,0,0.6);
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

  <div class="overlay" id="hearts-container"></div>

  <h1>💖 Caio & Letícia 💖</h1>
  <p><strong>Música:</strong> Space & Time - Rafael Witt</p>

  <div class="timer" id="timer"></div>

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
    // Temporizador
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

    // Surpresa com efeito máquina de escrever
    function mostrarFoto() {
      const container = document.getElementById('surpresaContainer');
      const texto = `Minha princesa, este temporizador marca o início oficial de nosso relacionamento diante de Deus e dos homens; E há quanto tempo eu sou o homem mais feliz, rico e sortudo desse universo.

Que essa simples página - mas dotada de muito amor e carinho - esteja acessível em qualquer dia, horas e lugar para nos (re)lembrar de quão maravilhoso é o nosso amor e que ele rompe qualquer barreira, passa por cima de qualquer empecilho e expulsa qualquer medo e orgulho, pois, com Cristo no barco, tudo vai muito bem.

E saiba que te honro, te admiro, te zelo, me inspiro em você e, por onde for, quero ser seu par.

Que sempre lembremos e creiamos nisto:
“Nenhum de nós é tão bom quanto nós dois juntos!”

Te amo... Muitão!

Com muito amor, zelo, carinho, afeto e admiração, 
Seu amigo, parceiro e namorado: Caio.`;

      const textoElemento = document.getElementById('textoMaquina');
      container.style.display = 'block';
      textoElemento.textContent = '';

      let i = 0;
      const intervalo = setInterval(() => {
        textoElemento.textContent += texto.charAt(i);
        i++;
        if (i === texto.length) clearInterval(intervalo);
      }, 25);
    }

    // Emojis de coração animados
    const colors = ['💚', '💜'];
    const heartsContainer = document.getElementById('hearts-container');

    function criarCoração() {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (8 + Math.random() * 4) + 's';
      heart.textContent = colors[Math.floor(Math.random() * colors.length)];
      heartsContainer.appendChild(heart);

      setTimeout(() => {
        heartsContainer.removeChild(heart);
      }, 12000);
    }

    setInterval(criarCoração, 300);
  </script>
</body>
</html>
