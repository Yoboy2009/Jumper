#jumper
<!DOCTYPE html>
<html>
<head>
  <title>Advanced Jump Over Blocks!</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap');

    body {
      margin: 0;
      overflow: hidden;
      background-color: #000;
      font-family: 'Orbitron', sans-serif;
      color: #00ffcc;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    #gameContainer {
      position: relative;
    }
    canvas {
      display: block;
      background: linear-gradient(#111, #333);
      border: 2px solid #00ffcc;
      border-radius: 10px;
    }
    #score, #highScore, #lives {
      position: absolute;
      top: 10px;
      font-size: 1.5em;
      text-shadow: 0 0 5px #00ffcc;
    }
    #score {
      left: 10px;
    }
    #highScore {
      right: 10px;
    }
    #lives {
      left: 50%;
      transform: translateX(-50%);
    }
    #startButton {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px 40px;
      font-size: 2em;
      background: linear-gradient(45deg, #00ffcc, #00ccff);
      color: #000;
      border: none;
      cursor: pointer;
      border-radius: 10px;
      box-shadow: 0 0 10px #00ffcc;
    }
    #gameOverWrapper {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      display: none;
      text-align: center;
      background: rgba(0, 0, 0, 0.8);
      padding: 20px;
      border-radius: 10px;
    }
    #gameOverWrapper #gameOver {
      font-size: 3em;
      margin-bottom: 20px;
      text-shadow: 0 0 10px #ff6699;
    }
    #gameOverWrapper #restartButton {
      padding: 15px 30px;
      font-size: 2em;
      background: linear-gradient(45deg, #00ffcc, #00ccff);
      color: #000;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div id="gameContainer">
    <canvas id="gameCanvas" width="600" height="400"></canvas>
    <div id="score">Score: 0</div>
    <div id="highScore">High Score: 0</div>
    <div id="lives">Lives: 3</div>
    <button id="startButton" onclick="startGame()">Start Game</button>
    <div id="gameOverWrapper">
      <div id="gameOver">Game Over!</div>
      <button id="restartButton" onclick="restartGame()">Restart</button>
    </div>
  </div>

  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    // Audio
    const jumpSound = new Audio('https://cdn.pixabay.com/audio/2022/03/10/audio_6b6b1f1e8d.mp3');
    const powerUpSound = new Audio('https://cdn.pixabay.com/audio/2022/03/10/audio_5e5b7e7f1e.mp3');
    const hitSound = new Audio('https://cdn.pixabay.com/audio/2022/03/10/audio_3e4b7e7f1e.mp3');

    // Game state
    let guyX = 50;
    let guyY = canvas.height - 80;
    let guyVelocityY = 0;
    let guyIsJumping = false;
    let isInvincible = false;
    let invincibilityTimer = 0;
    let isSpeedBoost = false;
    let speedBoostTimer = 0;
    let score = 0;
    let lives = 3;
    let highScore = localStorage.getItem('highScore') ? parseInt(localStorage.getItem('highScore')) : 0;
    let gameSpeed = 5;
    let backgroundX = 0;
    const blocks = [];
    const powerUps = [];
    const particles = [];
    let gameLoop;
    let blockInterval;
    let powerUpInterval;
    let difficultyTimer = 0;

    // ... (rest of the JavaScript code is the same) ...

    function jump() {
      if (!guyIsJumping) {
        jumpSound.play();
        guyVelocityY = -15;
        guyIsJumping = true;
        createParticles();
      }
    }
//...
        if (guyX < powerUps[i].x + powerUps[i].width &&
            guyX + 30 > powerUps[i].x &&
            guyY < powerUps[i].y + powerUps[i].height &&
            guyY + 60 > powerUps[i].y) {
          powerUpSound.play();
//...
      if (checkCollision()) {
        hitSound.play();
//...
    window.addEventListener('touchstart', jump);
    window.addEventListener('mousedown', jump);
    window.addEventListener('keydown', (e) => {
      if (e.code === 'Space') jump();
    });
  </script>
</body>
</html>
