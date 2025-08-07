<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Caio & Letícia</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      background: linear-gradient(to right, #ffecd2, #fcb69f);
      font-family: 'Arial', sans-serif;
      text-align: center;
      padding: 40px 20px;
      color: #333;
    }
    h1 {
      font-size: 2em;
      margin-bottom: 10px;
    }
    p {
      font-size: 1.2em;
      margin-top: 0;
      margin-bottom: 30px;
      font-style: italic;
    }
    #timer {
      font-size: 1.5em;
      font-weight: bold;
    }
    #playButton {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 1em;
      cursor: pointer;
      border: none;
      border-radius: 5px;
      background-color: #fcb69f;
      color: #fff;
      transition: background-color 0.3s ease;
    }
    #playButton:hover {
      background-color: #ff8c5e;
    }
  </style>
</head>
<body>
  <h1>Caio & Letícia</h1>
  <p>"Ele orou por ela;<br />Ela orou por ele;<br />Deus sorriu pra eles."</p>
  <div id="timer">Carregando...</div>

  <button id="playButton">Tocar música</button>

  <audio id="backgroundAudio" loop>
    <source src="SPACE_AND_TIME.mp3" type="audio/mpeg" />
    Seu navegador não suporta áudio.
  </audio>

  <script>
    // Timer atualizado com cálculo correto
    const startDate = new Date("2025-05-24T18:00:00");

    function updateTimer() {
      const now = new Date();
      let years = now.getFullYear() - startDate.getFullYear();
      let months = now.getMonth() - startDate.getMonth();
      let days = now.getDate() - startDate.getDate();
      let hours = now.getHours() - startDate.getHours();
      let minutes = now.getMinutes() - startDate.getMinutes();
      let seconds = now.getSeconds() - startDate.getSeconds();

      if (seconds < 0) {
        seconds += 60;
        minutes--;
      }
      if (minutes < 0) {
        minutes += 60;
        hours--;
      }
      if (hours < 0) {
        hours += 24;
        days--;
      }
      if (days < 0) {
        const prevMonth = new Date(now.getFullYear(), now.getMonth(), 0);
        days += prevMonth.getDate();
        months--;
      }
      if (months < 0) {
        months += 12;
        years--;
      }

      document.getElementById("timer").innerHTML =
        `${years} anos, ${months} meses, ${days} dias, ` +
        `${hours} horas, ${minutes} minutos, ${seconds} segundos`;
    }
    setInterval(updateTimer, 1000);
    updateTimer();

    // Controle do botão para tocar música
    const playButton = document.getElementById("playButton");
    const audio = document.getElementById("backgroundAudio");

    playButton.addEventListener("click", () => {
      audio.play().then(() => {
        playButton.style.display = "none"; // Esconde o botão quando começar a tocar
      }).catch((error) => {
        alert("Não foi possível tocar a música: " + error);
      });
    });
  </script>
</body>
</html>
