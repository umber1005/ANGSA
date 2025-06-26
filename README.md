<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <title>Game Menetaskan Telur Angsa</title>
  <style>
    body {
      background-image: url('https://cdn.pixabay.com/photo/2020/07/13/07/54/lake-5400025_1280.jpg');
      background-size: cover;
      background-position: center;
      font-family: "Comic Sans MS", cursive, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      flex-direction: column;
    }

    h1 {
      margin-bottom: 10px;
      color: #fff;
      text-shadow: 2px 2px 4px #000;
    }

    #game-container {
      position: relative;
      width: 500px;
      height: 400px;
      background: rgba(255, 255, 255, 0.8);
      border: 5px solid #888;
      border-radius: 20px;
      box-shadow: 4px 4px 10px rgba(0,0,0,0.3);
      overflow: hidden;
    }

    #goose {
      position: absolute;
      width: 180px;
      bottom: 80px;
      left: 30px;
    }

    #egg {
      position: absolute;
      width: 90px;
      bottom: 60px;
      left: 300px;
      cursor: pointer;
      transition: transform 0.1s;
    }

    #chick {
      position: absolute;
      width: 90px;
      bottom: 60px;
      left: 300px;
      display: none;
    }

    #clicks {
      margin-top: 10px;
      font-size: 18px;
      color: #fff;
      text-shadow: 1px 1px 2px #000;
    }

    #message {
      font-size: 20px;
      color: yellow;
      margin-top: 10px;
      text-shadow: 1px 1px 2px #000;
    }
  </style>
</head>
<body>

  <h1>Menetaskan Telur Angsa</h1>
  <div id="game-container">
    <img id="goose" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/White_goose_in_profile.jpg/480px-White_goose_in_profile.jpg" alt="Induk Angsa" />
    <img id="egg" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Egg_cartoon.svg/512px-Egg_cartoon.svg.png" alt="Telur Angsa" />
    <img id="chick" src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/Chick_cartoon.png/512px-Chick_cartoon.png" alt="Anak Angsa" />
    <audio id="crack-sound" src="https://cdn.pixabay.com/audio/2021/08/08/audio_d767d0d2b6.mp3" preload="auto"></audio>
  </div>

  <div id="clicks">Tekan telur untuk menetaskan!</div>
  <div id="message"></div>

  <script>
    const egg = document.getElementById("egg");
    const chick = document.getElementById("chick");
    const clicksText = document.getElementById("clicks");
    const message = document.getElementById("message");
    const crackSound = document.getElementById("crack-sound");

    let clicks = 0;
    const maxClicks = 7;

    egg.addEventListener("click", () => {
      clicks++;
      crackSound.currentTime = 0;
      crackSound.play();
      egg.style.transform = "scale(1.05)";
      setTimeout(() => egg.style.transform = "scale(1)", 100);

      if (clicks < maxClicks) {
        clicksText.textContent = `Mengetuk telur... (${clicks}/${maxClicks})`;
      } else {
        egg.style.display = "none";
        chick.style.display = "block";
        message.textContent = "Telur menetas! Anak angsa lahir!";
        clicksText.textContent = "";
      }
    });
  </script>
</body>
</html>
