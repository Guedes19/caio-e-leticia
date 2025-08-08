
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
  <style>
    /* Hack para esconder a faixa azul do GitHub Pages */
    #github-banner, .github-banner {
      display: none !important;
    }

    html, body {
      margin: 0;
      padding: 0;
      overflow-x: hidden; /* Evita scroll horizontal */
      width: 100%;
      height: 100%;
      font-family: 'Arial', sans-serif;
      color: white;
      background: url('fundo.jpg') center/cover no-repeat fixed;
      position: relative;
      box-sizing: border-box;
    }
    /* Fundo escurecido */
    .overlay {
      position: fixed;
      top: 0; left: 0;
      width: 100vw;
      height: 100vh;
      background-color: rgba(0, 0, 0, 0.6);
      z-index: -1;
    }
    /* Corações caindo */
    .emoji {
      position: absolute;
      font-size: 24px;
      pointer-events: none;
      animation: fall linear forwards;
      opacity: 1;
      z-index: 0;
      will-change: transform;
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
    /* Container */
    .container {
      max-width: 600px;
      width: 95%;
      margin: auto;
      padding: 1rem 1rem 3rem 1rem;
      box-sizing: border-box;
      text-align: center;
      position: relative;
      z-index: 1;
    }
    h1 {
      font-size: 2.5rem;
      margin-bottom: 0.5rem;
      word-break: break-word;
    }
    #temporizador {
      font-size: 1.4rem;
      margin: 1rem 0 2rem 0;
      text-shadow: 0 0 6px black;
      word-break: break-word;
    }
    button {
      width: 100%;
      padding: 12px 0;
      font-size: 1.1rem;
      border-radius: 8px;
      border: none;
      margin-bottom: 15px;
      cursor: pointer;
      user-select: none;
      color: white;
      transition: background-color 0.3s ease;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: none;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    #musicaBtn {
      background-color: #a855f7;
    }
    #musicaBtn:hover {
      background-color: #7b3bd4;
    }
    #surpriseBtn {
      background-color: #34d399;
    }
    #surpriseBtn:hover {
      background-color: #22c55e;
    }
    /* Carrossel */
    #carousel-container {
      margin: 1rem auto;
      max-width: 100%;
      text-align: center;
    }
    #carousel-container button {
      width: auto;
      padding: 8px 15px;
      margin: 0 5px 10px;
      border-radius: 6px;
      background: #34d399;
      border: none;
      color: white;
      cursor: pointer;
      font-size: 1.2rem;
      user-select: none;
    }
    #carouselImage {
      max-width: 100%;
      max-height: 300px;
      border-radius: 12px;
      box-shadow: 0 0 15px rgba(0,0,0,0.7);
      object-fit: contain;
    }
    /* Texto surpresa */
    #typed-text {
      margin: 1rem auto 0 auto;
      white-space: pre-wrap;
      font-size: 1rem;
      max-width: 100%;
      text-align: justify;
      border-left: 3px solid #a855f7;
      padding-left: 12px;
      display: none;
      text-shadow: 0 0 4px black;
      line-height: 1.5em;
      box-sizing: border-box;
    }
    /* Responsivo */
    @media (max-width: 400px) {
      h1 {
        font-size: 1.8rem;
      }
      #temporizador {
        font-size: 1.1rem;
      }
      button {
        font-size: 1rem;
        padding: 10px 0;
        max-width: 100%;
      }
      #typed-text {
        font-size: 0.9rem;
        max-width: 100%;
      }
      #carouselImage {
        max-height: 220px;
      }
    }
  </style>
</head>
<body>
  <div class="overlay"></div>

  <div class="container">
    <h1>Caio & Letícia</h1>
    <div id="temporizador">Carregando tempo juntos...</div>

    <button id="musicaBtn" title="Tocar ou pausar música">▶ Tocar Música</button>
    <button id="surpriseBtn" title="Mostrar foto e mensagem surpresa">🎁 Mostrar Surpresa</button>

    <audio id="musica" loop>
      <source src="musica.mp3" type="audio/mpeg" />
      Seu navegador não suporta áudio.
    </audio>

    <div id="carousel-container" style="display:none;">
      <button id="prevBtn" aria-label="Imagem anterior">←</button>
      <button id="nextBtn" aria-label="Próxima imagem">→</button>
      <br />
      <img id="carouselImage" src="" alt="Imagem Surpresa" />
    </div>

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
      coracao.style.left = Math.random() * (document.body.clientWidth - 30) + "px";
      coracao.style.top = "-50px";
      coracao.style.animationDuration = (Math.random() * 3 + 4) + "s";
      document.body.appendChild(coracao);
      setTimeout(() => coracao.remove(), 8000);
    }
    setInterval(criarCoracao, 200);

    // Surpresa - Carrossel
    const surpriseBtn = document.getElementById('surpriseBtn');
    const carouselContainer = document.getElementById('carousel-container');
    const carouselImage = document.getElementById('carouselImage');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const typedText = document.getElementById('typed-text');

    const imagens = [
      'foto-surpresa1.jpg',
      'foto-surpresa2.jpg',
      'foto-surpresa3.jpg'
      // Adicione suas imagens aqui
    ];

    let indexImagem = 0;
    let intervalId;

    function mostrarImagem(i) {
      if (i < 0) i = imagens.length - 1;
      if (i >= imagens.length) i = 0;
      indexImagem = i;
      carouselImage.src = imagens[indexImagem];
    }

    function iniciarSlideAutomatico() {
      intervalId = setInterval(() => {
        mostrarImagem(indexImagem + 1);
      }, 4000);
    }

    function reiniciarSlideAutomatico() {
      clearInterval(intervalId);
      iniciarSlideAutomatico();
    }

    prevBtn.addEventListener('click', () => {
      mostrarImagem(indexImagem - 1);
      reiniciarSlideAutomatico();
    });

    nextBtn.addEventListener('click', () => {
      mostrarImagem(indexImagem + 1);
      reiniciarSlideAutomatico();
    });

    // Texto da surpresa
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
      carouselContainer.style.display = 'block';
      typedText.style.display = 'block';
      mostrarImagem(0);
      escreverTexto(typedText, textoCompleto);
      iniciarSlideAutomatico();
    });
  </script>
</body>
</html>
