# Healix
mental health depression 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Chill Quiz + Flappy Bird Game for Mental Health</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Poppins:wght@400;700&display=swap" rel="stylesheet" />
<style>
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(135deg, #4e54c8, #8f94fb);
    color: #fff;
    display: flex;
    justify-content: center;
    padding: 1rem;
    min-height: 100vh;
    flex-direction: column;
    align-items: center;
    user-select: none;
  }
  h1 {
    font-family: 'Fredoka One', cursive;
    font-size: 3rem;
    margin-bottom: 0.3rem;
    text-shadow: 0 0 15px #fff;
  }
  .container {
    background: rgba(0,0,0,0.75);
    border-radius: 25px;
    padding: 2rem 2.5rem;
    width: 100%;
    max-width: 700px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.7);
  }
  .intro, .quiz-section, .result-section, .game-section {
    margin-bottom: 2.5rem;
  }
  .intro h2 {
    font-family: 'Fredoka One', cursive;
    font-size: 2rem;
    margin-bottom: 1rem;
    color: #ffd700;
    text-shadow: 0 0 10px #000;
    user-select: text;
  }
  .intro p {
    font-size: 1.15rem;
    line-height: 1.5;
    user-select: text;
  }
  .tip-list {
    margin-top: 1rem;
    padding-left: 1.2rem;
  }
  .tip-list li {
    margin-bottom: 0.7rem;
    font-weight: 600;
  }
  form {
    user-select: none;
  }
  .question {
    margin-bottom: 1.5rem;
  }
  .question h3 {
    font-weight: 700;
    margin-bottom: 0.7rem;
    text-shadow: 0 0 8px #000;
  }
  label {
    display: block;
    margin-bottom: 0.4rem;
    cursor: pointer;
    font-weight: 500;
    font-size: 1.1rem;
    transition: color 0.2s;
  }
  label:hover {
    color: #ffd700;
  }
  input[type="radio"] {
    margin-right: 0.8rem;
    transform: scale(1.2);
    cursor: pointer;
    accent-color: #ffd700;
  }
  button {
    background: #ffd700;
    border: none;
    padding: 1rem 2rem;
    font-weight: 700;
    font-size: 1.3rem;
    border-radius: 50px;
    cursor: pointer;
    color: #111;
    box-shadow: 0 5px 15px #ffd700aa;
    transition: background 0.3s, transform 0.2s;
    width: 100%;
  }
  button:hover:enabled {
    background: #fff;
    transform: scale(1.05);
  }
  button:disabled {
    background: #aaa;
    cursor: not-allowed;
    box-shadow: none;
    transform: none;
  }
  #result {
    font-size: 1.4rem;
    font-weight: 700;
    padding: 1rem;
    border-radius: 20px;
    text-align: center;
    display: none;
    user-select: text;
  }
  #result.low {
    background: #55efc4;
    color: #006644;
    box-shadow: 0 0 15px #00b894;
  }
  #result.moderate {
    background: #fdcb6e;
    color: #6d4c41;
    box-shadow: 0 0 15px #e17055;
  }
  #result.high {
    background: #ff7675;
    color: #7f0000;
    box-shadow: 0 0 15px #d63031;
  }

  /* Flappy Bird Game Styles */
  #gameCanvas {
    background: linear-gradient(to bottom, #80d0c7, #13547a);
    border-radius: 20px;
    display: block;
    margin: 0 auto;
    box-shadow: 0 8px 30px #0009;
  }
  .game-instructions {
    color: #ffd700;
    font-weight: 600;
    margin-bottom: 0.8rem;
    user-select: none;
  }
  #startGameBtn {
    margin-top: 0.8rem;
    background: #ffd700;
    border: none;
    padding: 0.9rem 2rem;
    font-weight: 700;
    font-size: 1.2rem;
    border-radius: 50px;
    cursor: pointer;
    color: #111;
    box-shadow: 0 5px 15px #ffd700aa;
    transition: background 0.3s, transform 0.2s;
  }
  #startGameBtn:hover {
    background: #fff;
    transform: scale(1.05);
  }
  #scoreDisplay {
    margin-top: 0.7rem;
    font-size: 1.3rem;
    font-weight: 700;
    color: #fff;
    text-align: center;
    user-select: none;
  }
  audio {
    display: block;
    margin: 1.5rem auto 2rem;
    width: 100%;
    max-width: 400px;
    border-radius: 10px;
    box-shadow: 0 5px 15px #000a;
  }
  @media (max-width: 480px) {
    h1 {
      font-size: 2.2rem;
    }
    button, #startGameBtn {
      font-size: 1rem;
      padding: 0.8rem 1.6rem;
    }
  }
</style>
</head>
<body>

<div class="container">

  <h1>Chill Quiz + Flappy Bird for Your Mood</h1>

  <div class="intro">
    <h2>Welcome!</h2>
    <p>Before diving into the quiz, here are some quick mental health tips & info to help you feel calm and ready:</p>
    <ul class="tip-list">
      <li>Take deep breaths — even a few can help your brain reset.</li>
      <li>Remember: It’s okay to not be okay. You're not alone.</li>
      <li>Talking about how you feel is a strength, not a weakness.</li>
      <li>Physical activity can boost your mood — even a short walk helps.</li>
      <li>If you feel overwhelmed, consider reaching out to a trusted adult or counselor.</li>
    </ul>
    <p style="margin-top:1rem; font-style:italic; font-size:0.9rem;">
      Source: <a href="https://www.nimh.nih.gov/health/topics/depression" target="_blank" style="color:#ffd700;">NIMH - Depression Info</a>
    </p>
  </div>

  <form id="quizForm" class="quiz-section" aria-label="Depression quiz form">
    <!-- Questions inserted by JS -->
  </form>

  <button id="submitBtn" disabled>Check My Mood</button>

  <div id="result" role="alert" aria-live="polite"></div>

  <div class="game-section" style="display:none;">
    <p class="game-instructions">After the quiz, take a break and try the Flappy Bird mini-game! Press space or tap/click to flap.</p>
    <canvas id="gameCanvas" width="400" height="500" aria-label="Flappy Bird mini-game"></canvas>
    <button id="startGameBtn">Start Flappy Bird</button>
    <div id="scoreDisplay" aria-live="polite"></div>
  </div>

  <audio controls autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2023/03/30/audio_9879d5d299.mp3?filename=chill-lofi-beats-11354.mp3" type="audio/mpeg" />
    Your browser does not support the audio element.
  </audio>
</div>

<script>
  const questions = [
    "1. How often do you feel like the main character in a sad movie? (aka lowkey sad?)",
    "2. How often do you find yourself binge-watching shows to avoid feelings?",
    "3. How often do you struggle to get out of bed without hitting snooze 10 times?",
    "4. How often do you feel overwhelmed like when your phone battery hits 1%?",
    "5. How often do you feel like your brain is buffering (slow loading thoughts)?",
    "6. How often do you feel hopeless, like your Wi-Fi connection?",
    "7. How often do you find it hard to enjoy your favorite memes?",
    "8. How often do you get angry at small stuff? (Like losing your charger)",
    "9. How often do you feel tired but can’t sleep, like scrolling till 3 AM?",
    "10. How often do you skip meals or forget to eat because you’re 'too busy'?",
    "11. How often do you feel worthless, like a 404 error?",
    "12. How often do you avoid talking to friends because it feels exhausting?",
    "13. How often do you have trouble focusing, like when your laptop is lagging?",
    "14. How often do you feel anxious about things that might never happen?",
    "15. How often do you feel lonely even in a crowded room?",
    "16. How often do you feel like screaming but stay quiet?",
    "17. How often do you get easily distracted by random TikToks?",
    "18. How often do you feel like you’re stuck in a loop of bad vibes?",
    "19. How often do you feel guilty about not doing enough?",
    "20. How often do you have thoughts that scare you or make you uncomfortable?"
  ];

  const answers = [
    "Not at all", "Several days", "More than half the days", "Nearly every day"
  ];

  const form = document.getElementById('quizForm');
  const submitBtn = document.getElementById('submitBtn');
  const resultDiv = document.getElementById('result');
  const gameSection = document.querySelector('.game-section');
  const startGameBtn = document.getElementById('startGameBtn');
  const scoreDisplay = document.getElementById('scoreDisplay');
  const canvas = document.getElementById('gameCanvas');
  const ctx = canvas.getContext('2d');

  // Build questions dynamically
  questions.forEach((q, i) => {
    const div = document.createElement('div');
    div.className = 'question';
    div.innerHTML = `<h3>${q}</h3>` +
      answers.map((ans, idx) => `
        <label>
          <input type="radio" name="q${i}" value="${idx}" aria-label="${ans} for question ${i + 1}" />
          ${ans}
        </label>
      `).join('');
    form.appendChild(div);
  });

  // Enable submit button only if all answered
  form.addEventListener('change', () => {
    const allAnswered = [...form.querySelectorAll('div.question')].every(div => {
      return div.querySelector('input[type="radio"]:checked');
    });
    submitBtn.disabled = !allAnswered;
  });

  // On submit, calculate score & show result
  submitBtn.addEventListener('click', e => {
    e.preventDefault();
    let score = 0;
    for(let i = 0; i < questions.length; i++) {
      const selected = form.querySelector(`input[name="q${i}"]:checked`);
      if(selected) score += parseInt(selected.value);
    }
    // Score ranges roughly 0 - 60 (max 3 * 20)
    let mood = '';
    resultDiv.style.display = 'block';

    if(score <= 15) {
      mood = 'low';
      resultDiv.textContent = `Your answers suggest low signs of depression. Keep up with those good vibes! 🌟 (Score: ${score})`;
    } else if(score <= 35) {
      mood = 'moderate';
      resultDiv.textContent = `You might be feeling moderate symptoms. Remember, it’s okay to ask for help and take time for yourself. 🤗 (Score: ${score})`;
    } else {
      mood = 'high';
      resultDiv.textContent = `Your answers suggest higher signs of depression. Consider talking to someone you trust or a mental health professional. 💙 (Score: ${score})`;
    }
    resultDiv.className = mood;
    // Show game section after result
    gameSection.style.display = 'block';
    window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'});
  });

  /* Flappy Bird Mini-Game Code */
  let gameRunning = false;
  let bird = { x: 60, y: 150, radius: 12, velocity: 0 };
  let gravity = 0.5;
  let jump = -10;
  let pipes = [];
  let pipeWidth = 50;
  let pipeGap = 130;
  let frameCount = 0;
  let score = 0;

  function resetGame() {
    bird = { x: 60, y: 150, radius: 12, velocity: 0 };
    pipes = [];
    frameCount = 0;
    score = 0;
    scoreDisplay.textContent = 'Score: 0';
  }

  function createPipe() {
    let topPipeHeight = Math.random() * (canvas.height - pipeGap - 100) + 50;
    pipes.push({
      x: canvas.width,
      top: topPipeHeight,
      bottom: topPipeHeight + pipeGap
    });
  }

  function drawBird() {
    ctx.fillStyle = '#ffd700';
    ctx.beginPath();
    ctx.ellipse(bird.x, bird.y, bird.radius + 3, bird.radius, 0, 0, 2 * Math.PI);
    ctx.fill();

    // Eye
    ctx.fillStyle = '#222';
    ctx.beginPath();
    ctx.arc(bird.x + 5, bird.y - 3, 3, 0, 2 * Math.PI);
    ctx.fill();

    // Beak
    ctx.fillStyle = '#ff6f00';
    ctx.beginPath();
    ctx.moveTo(bird.x + 12, bird.y);
    ctx.lineTo(bird.x + 20, bird.y - 5);
    ctx.lineTo(bird.x + 20, bird.y + 5);
    ctx.closePath();
    ctx.fill();
  }

  function drawPipes() {
    ctx.fillStyle = '#228b22';
    pipes.forEach(pipe => {
      // Top pipe
      ctx.fillRect(pipe.x, 0, pipeWidth, pipe.top);
      // Bottom pipe
      ctx.fillRect(pipe.x, pipe.bottom, pipeWidth, canvas.height - pipe.bottom);
      // Pipe caps for style
      ctx.fillStyle = '#1e6b1e';
      ctx.fillRect(pipe.x - 3, pipe.top - 10, pipeWidth + 6, 10);
      ctx.fillRect(pipe.x - 3, pipe.bottom, pipeWidth + 6, 10);
      ctx.fillStyle = '#228b22';
    });
  }

  function detectCollision() {
    if(bird.y + bird.radius > canvas.height || bird.y - bird.radius < 0) return true;
    for(let p of pipes) {
      if(bird.x + bird.radius > p.x && bird.x - bird.radius < p.x + pipeWidth) {
        if(bird.y - bird.radius < p.top || bird.y + bird.radius > p.bottom) {
          return true;
        }
      }
    }
    return false;
  }

  function gameLoop() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Draw background gradient again
    let bgGradient = ctx.createLinearGradient(0, 0, 0, canvas.height);
    bgGradient.addColorStop(0, '#80d0c7');
    bgGradient.addColorStop(1, '#13547a');
    ctx.fillStyle = bgGradient;
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    drawPipes();

    // Bird physics
    bird.velocity += gravity;
    bird.y += bird.velocity;
    drawBird();

    // Move pipes
    pipes.forEach(pipe => pipe.x -= 2);

    // Remove offscreen pipes and update score
    if(pipes.length && pipes[0].x < -pipeWidth) {
      pipes.shift();
      score++;
      scoreDisplay.textContent = 'Score: ' + score;
    }

    // Create new pipe every 120 frames (~2 seconds at 60fps)
    frameCount++;
    if(frameCount % 120 === 0) createPipe();

    if(detectCollision()) {
      gameRunning = false;
      startGameBtn.textContent = 'Restart Flappy Bird';
      scoreDisplay.textContent += ' — Game Over!';
    }

    if(gameRunning) {
      requestAnimationFrame(gameLoop);
    }
  }

  function flap() {
    if(!gameRunning) return;
    bird.velocity = jump;
  }

  // Start game button
  startGameBtn.addEventListener('click', () => {
    if(gameRunning) return;
    resetGame();
    gameRunning = true;
    startGameBtn.textContent = 'Playing... Tap/Space to flap';
    scoreDisplay.textContent = 'Score: 0';
    gameLoop();
  });

  // Control bird flap on spacebar or click/tap
  window.addEventListener('keydown', e => {
    if(e.code === 'Space' && gameRunning) {
      e.preventDefault();
      flap();
    }
  });
  canvas.addEventListener('mousedown', e => {
    if(gameRunning) flap();
  });
  canvas.addEventListener('touchstart', e => {
    if(gameRunning) {
      e.preventDefault();
      flap();
    }
  });

</script>
</body>
</html>
