
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow-x: hidden;
      font-family: 'Arial', sans-serif;
    }

    body {
      background: url('sua-imagem-de-fundo.jpg') no-repeat center center fixed;
      background-size: cover;
      position: relative;
      color: white;
    }

    /* Camada escura */
    body::before {
      content: "";
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 0;
    }

    .content {
      position: relative;
      z-index: 2;
      padding: 2rem 1rem;
      text-align: center;
    }

    h1 {
      font-size: 2rem;
    }

    .timer {
      font-size: 1.5rem;
      margin: 1rem 0;
    }

    .surpresa {
      margin: 2rem auto;
      max-width: 100%;
      padding: 1rem;
    }

    .foto {
      max-width: 100%;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0,0,0,0.4);
    }

    .maquina {
      margin-top: 1rem;
      white-space: pre-line;
      border-right: 2px solid white;
      font-size: 1rem;
      overflow: hidden;
      white-space: nowrap;
      animation: typing 8s steps(100, end), blink 0.75s step-end infinite;
    }

    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }

    @keyframes blink {
      50% { border-color: transparent }
    }

    /* Corações */
    .heart {
      position: fixed;
      top: -50px;
      font-size: 2rem;
      opacity: 1;
      z-index: 1;
      animation: fall 6s linear infinite;
      pointer-events: none;
    }

    @keyframes fall {
      to {
        transform: translateY(110vh) rotate(360deg);
        opacity: 1;
      }
    }

    /* Remover link azul (GitHub Pages hack) */
    a[href^="https://github.com"] {
      display: none !important;
    }

    @media (max-width: 600px) {
      h1 { font-size: 1.5rem; }
      .timer { font-size: 1.2rem; }
    }
  </style>
</head>
<body>
  <audio autoplay loop>
    <source src="musica.mp3" type="audio/mpeg" />
    Seu navegador não suporta áudio.
  </audio>

  <div class="content">
    <h1>Caio & Letícia</h1>
    <div class="timer" id="timer">Carregando o tempo...</div>

    <div class="surpresa">
      <img src="foto-surpresa.jpg" alt="Surpresa" class="foto" />
      <div class="maquina" id="maquina">
        <!-- Texto será digitado aqui -->
      </div>
    </div>
  </div>

  <!-- Script do Temporizador -->
  <script>
    const dataAlvo = new Date("2025-05-24T18:00:00").getTime();
    const timer = document.getElementById("timer");

    setInterval(() => {
      const agora = new Date().getTime();
      const distancia = agora - dataAlvo;

      const dias = Math.floor(distancia / (1000 * 60 * 60 * 24));
      const horas = Math.floor((distancia % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutos = Math.floor((distancia % (1000 * 60 * 60)) / (1000 * 60));
      const segundos = Math.floor((distancia % (1000 * 60)) / 1000);

      timer.innerText = `${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos de relacionamento!`;
    }, 1000);
  </script>

  <!-- Script da Máquina de Escrever -->
  <script>
    const texto = `Minha princesa, este temporizador marca o início oficial de nosso relacionamento diante de Deus e dos homens; E há quanto tempo eu sou o homem mais feliz, rico e sortudo desse universo.

Que essa simples página - mas dotada de muito amor e carinho - esteja acessível em qualquer dia, horas e lugar para nos (re)lembrar de quão maravilhoso é o nosso amor e que ele rompe qualquer barreira, passa por cima de qualquer empecilho e expulsa qualquer medo e orgulho, pois, com Cristo no barco, tudo vai muito bem.

E saiba que te honro, te admiro, te zelo, me inspiro em vocẽ e, por onde for, quero ser seu par.

Que sempre lembremos e creiamos nisto: “Nenhum de nós é tão bom quanto nós dois juntos!”

Te amo... Muitão!

Com muito amor, zelo, carinho, afeto e admiração, Seu amigo, parceiro e namorado: Caio.`;

    const maquina = document.getElementById("maquina");
    let i = 0;

    function escrever() {
      if (i < texto.length) {
        maquina.innerHTML += texto.charAt(i);
        i++;
        setTimeout(escrever, 35);
      }
    }
    escrever();
  </script>

  <!-- Script dos Corações -->
  <script>
    const emojis = ["💚", "💜"];
    const createHeart = () => {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (Math.random() * 2 + 4) + "s";
      heart.style.opacity = "1";
      heart.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      heart.style.color = heart.textContent === "💚" ? "#00FF00" : "#800080";
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 6000);
    };
    setInterval(createHeart, 300);
  </script>
</body>
</html>
