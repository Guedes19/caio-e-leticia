<script>
  // Temporizador - data do namoro
  const dataInicio = new Date(2025, 4, 24, 18, 0, 0);
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

  // Controle da música
  const audio = document.getElementById('musica');
  const botao = document.getElementById('btnMusica');

  botao.addEventListener('click', () => {
    if (audio.paused) {
      audio.play().then(() => {
        botao.textContent = "⏸ Pausar Música";
      }).catch((erro) => {
        console.error("Erro ao tentar tocar a música:", erro);
        alert("O navegador bloqueou o áudio. Tente clicar novamente.");
      });
    } else {
      audio.pause();
      botao.textContent = "▶ Tocar Música";
    }
  });
</script>
