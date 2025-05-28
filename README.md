<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Rodrigo e Natasha 💖</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #ffe6e6;
      color: #b30000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
    }

    .loader-container, .countdown-container {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .loader-text {
      font-size: 2rem;
      margin-bottom: 20px;
    }

    .heart {
      font-size: 2rem;
      animation: pulse 1s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); color: #ff6666; }
      50% { transform: scale(1.3); color: #ff1a1a; }
      100% { transform: scale(1); color: #ff6666; }
    }

    .countdown {
      font-size: 2.5rem;
      margin-top: 20px;
      font-weight: bold;
    }

    .footer-text {
      margin-top: 20px;
      font-size: 1.5rem;
      font-weight: bold;
      color: #990000;
    }
  </style>
</head>
<body>

  <div class="loader-container" id="loader">
    <div class="loader-text" id="loadingText">Carregando... 0%</div>
    <div class="heart">❤️</div>
  </div>

  <div class="countdown-container" id="countdownContainer" style="display: none;">
    <div class="heart">❤️</div>
    <div class="countdown" id="countdown">00:00:00:00</div>
    <div class="footer-text">Rodrigo e Natasha 1 ano juntos 💕</div>
  </div>

  <script>
    // Simula carregamento de 0 a 100%
    let percent = 0;
    const loadingText = document.getElementById("loadingText");
    const loader = document.getElementById("loader");
    const countdownContainer = document.getElementById("countdownContainer");

    const interval = setInterval(() => {
      percent++;
      loadingText.textContent = `Carregando... ${percent}%`;
      if (percent >= 100) {
        clearInterval(interval);
        loader.style.display = "none";
        countdownContainer.style.display = "flex";
        startCountdown();
      }
    }, 30); // velocidade do carregamento

    // Contagem regressiva até 15/06/2025
    function startCountdown() {
      const countdownEl = document.getElementById("countdown");
      const targetDate = new Date("2025-06-15T00:00:00");

      function updateCountdown() {
        const now = new Date();
        const diff = targetDate - now;

        if (diff <= 0) {
          countdownEl.textContent = "Chegou o grande dia!";
          return;
        }

        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
        const minutes = Math.floor((diff / (1000 * 60)) % 60);
        const seconds = Math.floor((diff / 1000) % 60);

        countdownEl.textContent = 
          `${days.toString().padStart(2, "0")}d ` +
          `${hours.toString().padStart(2, "0")}h ` +
          `${minutes.toString().padStart(2, "0")}m ` +
          `${seconds.toString().padStart(2, "0")}s`;
      }

      updateCountdown();
      setInterval(updateCountdown, 1000);
    }
  </script>
</body>
</html>
