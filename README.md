
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      position: relative;
      overflow-x: hidden;
      color: white;
    }
    .background {
      position: fixed;
      top: 0; left: 0;
      width: 100vw;
      height: 100vh;
      background: url('fundo.jpg') center/cover no-repeat;
      z-index: -3;
    }
    .overlay {
      position: fixed;
      top: 0; left: 0;
      width: 100vw;
      height: 100vh;
      background-color: rgba(0, 0, 0, 0.6);
      z-index: -2;
    }
    .emoji {
      position: fixed;
      font-size: 24px;
      opacity: 1;
      z-index: -1;
      pointer-events: none;
      animation: fall linear forwards;
    }
    @keyframes fall {
      from {
        transform: translateY(-50px) rotate(0deg);
        opacity: 1;
      }
      to {
        transform: translateY(110vh) rotate(360deg);
        opacity: 1;
      }
    }
    .container {
      position: relative;
      z-index: 1;
      padding: 2rem;
      text-align: center;
    }
    #temporizador {
      font-size: 1.8rem;
      margin: 1rem 0 2rem 0;
      text-shadow: 0 0 6px black;
    }
    #musicaBtn {
      cursor: pointer;
      padding: 10px 20px;
      font-size: 18px;
      background-color: #a855f7;
      border: none;
      border-radius: 8px;
      color: white;
      margin-bottom: 20px;
      transition: background-color 0.3s ease;
    }
    #musicaBtn:hover {
      background-color: #7b3bd4;
    }
    #surpriseBtn {
      cursor: pointer;
      padding: 10px 20px;
      font-size: 18px;
      background-color: #34d399;
      border: none;
      border-radius: 8px;
      color: white;
      margin-bottom: 20px;
      transition: background-color 0.3s ease;
    }
    #surpriseBtn:hover {
      background-color: #22c55e;
    }
    #photo {
      display: none;
      max-width: 80%;
      border-radius: 12px;
      margin: 1rem auto 0 auto;
      box-shadow: 0 0 15px rgba(0,0,0,0.7);
    }
    #typed-text {
      margin: 1rem auto 0 auto;
      white-space: pre-wrap;
      font-size: 1.1rem;
      max-width: 800px;
      text-align: justify;
      border-left: 3px solid #a855f7;
      padding-left: 12px;
      display: none;
      text-shadow: 0 0 4px black;
    }
  </style>
</head>
<body>
  <div class="background"></div>
  <div class="overlay"></div>

  <div class="container">
    <h1>Caio & Letícia</h1>
    <div id="temporizador">Carregando tempo juntos...</div>

    <button id="musicaBtn">▶ Tocar Música</button><br />
    <button id="surpriseBtn">🎁 Mostrar Surpresa</button>

    <audio id="musica" loop>
      <source src="musica.mp3" type="audio/mpeg" />
      Seu navegador não suporta áudio.
    </audio>

    <img id="photo" src="foto.jpg" alt="Foto Surpresa" />
    <p id="typed-text"></p>
  </div>

  <script>
    // Temporizador
    const inicio = new Date("2025-05-24T18:00:00");
    const temporizador = document.getElementById('temporizador');
    function atualizarTempo() {
      const agora = new Date();
      const diff = agora - inicio;
      if (diff < 0) {
        temporizador.textContent = "Nosso relacionamento ainda não começou!";
        return;
      }
      const dias = Math.floor(diff / (1000 * 60 * 60 * 24));
      const horas = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutos = Math.floor((diff / (1000 * 60)) % 60);
      const segundos = Math.floor((diff / 1000) % 60);
      temporizador.textContent = `${dias}d ${horas}h ${minutos}m ${segundos}s juntos 💕`;
    }
    atualizarTempo();
    setInterval(atualizarTempo, 1000);

    // Música
    const musica = document.getElementById('musica');
    const musicaBtn = document.getElementById('musicaBtn');
    musicaBtn.addEventListener('click', () => {
      if (musica.paused) {
        musica.play();
        musicaBtn.textContent = "⏸ Pausar Música";
      } else {
        musica.pause();
        musicaBtn.textContent = "▶ Tocar Música";
      }
    });

    // Corações
    const emojis = ["💚", "💜"];
    function criarCoracao() {
      const coracao = document.createElement('div');
      coracao.classList.add('emoji');
      coracao.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      coracao.style.left = Math.random() * 100 + "vw";
      coracao.style.animationDuration = (Math.random() * 3 + 4) + "s";
      document.body.appendChild(coracao);
      setTimeout(() => coracao.remove(), 8000);
    }
    setInterval(criarCoracao, 200);

    // Surpresa
    const surpriseBtn = document.getElementById('surpriseBtn');
    const photo = document.getElementById('photo');
    const typedText = document.getElementById('typed-text');

    const textoCompleto = `Minha princesa, este temporizador marca o início oficial de nosso relacionamento diante de Deus e dos homens; E há quanto tempo eu sou o homem mais feliz, rico e sortudo desse universo.

Que essa simples página - mas dotada de muito amor e carinho - esteja acessível em qualquer dia, horas e lugar para nos (re)lembrar de quão maravilhoso é o nosso amor e que ele rompe qualquer barreira, passa por cima de qualquer empecilho e expulsa qualquer medo e orgulho, pois, com Cristo no barco, tudo vai muito bem.

E saiba que te honro, te admiro, te zelo, me inspiro em vocẽ e, por onde for, quero ser seu par.

Que sempre lembremos e creiamos nisto: “Nenhum de nós é tão bom quanto nós dois juntos!”

Te amo... Muitão!

Com muito amor, zelo, carinho, afeto e admiração,  
Seu amigo, parceiro e namorado: Caio.`;

    function escreverTexto(elemento, texto, indice = 0) {
      if (indice === 0) {
        elemento.style.display = "block";
        elemento.textContent = "";
      }
      if (indice < texto.length) {
        elemento.textContent += texto.charAt(indice);
        setTimeout(() => escreverTexto(elemento, texto, indice + 1), 30);
      }
    }

    surpriseBtn.addEventListener('click', () => {
      photo.style.display = "block";
      escreverTexto(typedText, textoCompleto);
    });
  </script>
</body>
</html>
