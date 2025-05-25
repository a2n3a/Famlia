<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Carta do Coração</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      background: linear-gradient(135deg, #ffe0e0, #fff0f5);
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
    }
    .container {
      text-align: center;
      padding: 40px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 0 20px rgba(255, 0, 98, 0.3);
      max-width: 600px;
      position: relative;
      animation: aparecer 2s ease-in-out;
    }

    .heart {
      width: 100px;
      height: 90px;
      background: red;
      position: absolute;
      top: -50px;
      left: calc(50% - 50px);
      transform: rotate(-45deg);
      animation: pulsar 1s infinite;
    }

    .heart:before,
    .heart:after {
      content: "";
      width: 100px;
      height: 90px;
      background: red;
      position: absolute;
      border-radius: 50%;
    }

    .heart:before {
      top: -50px;
      left: 0;
    }

    .heart:after {
      left: 50px;
      top: 0;
    }

    @keyframes pulsar {
      0%, 100% {
        transform: scale(1) rotate(-45deg);
      }
      50% {
        transform: scale(1.2) rotate(-45deg);
      }
    }

    h1 {
      color: #c70039;
      margin-top: 60px;
      font-size: 2.5rem;
    }

    p {
      font-size: 1.2rem;
      margin-top: 20px;
      color: #333;
    }

    .typing {
      border-right: 2px solid #c70039;
      white-space: nowrap;
      overflow: hidden;
      width: 0;
      animation: typing 6s steps(80, end), blink .75s step-end infinite;
    }

    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }

    @keyframes blink {
      from, to { border-color: transparent }
      50% { border-color: #c70039 }
    }

    audio {
      display: none;
    }

    .botao {
      margin-top: 30px;
      background: #c70039;
      color: white;
      padding: 12px 24px;
      border: none;
      border-radius: 30px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s;
    }

    .botao:hover {
      background: #900028;
    }

    @keyframes aparecer {
      from {
        opacity: 0;
        transform: translateY(-50px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="heart"></div>
    <h1>Para minha família querida</h1>
    <p id="mensagem" class="typing"></p>
    <button class="botao" onclick="reiniciar()">Ver de novo</button>
  </div>

  <audio id="musica" autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>

  <script>
    const mensagem = "Vocês são meu alicerce, minha alegria e minha maior bênção. Que nunca falte amor, união e sorrisos entre nós. Amo cada um com todo meu coração!";
    let i = 0;
    const velocidade = 50;
    const p = document.getElementById("mensagem");

    function escrever() {
      if (i < mensagem.length) {
        p.textContent += mensagem.charAt(i);
        i++;
        setTimeout(escrever, velocidade);
      }
    }

    function reiniciar() {
      i = 0;
      p.textContent = "";
      escrever();
    }

    window.onload = () => {
      escrever();
      document.getElementById('musica').volume = 0.3;
    };
  </script>
</body>
</html>
