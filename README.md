<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Megan 💜</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #6a11cb, #b91372);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: hidden;
}

/* Floating Hearts Background */
.bg-heart {
  position: fixed;
  color: rgba(255,255,255,0.25);
  font-size: 20px;
  animation: floatUp linear infinite;
}

@keyframes floatUp {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); }
}

#phone {
  width: 95%;
  max-width: 400px;
  height: 92vh;
  background: white;
  border-radius: 25px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  position: relative;
  z-index: 2;
}

#chat {
  flex: 1;
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.message {
  padding: 10px 15px;
  border-radius: 20px;
  max-width: 75%;
  font-size: 15px;
}

.sent {
  background: #6a11cb;
  color: white;
  align-self: flex-end;
}

button {
  margin: 10px;
  padding: 12px;
  border: none;
  border-radius: 20px;
  background: #6a11cb;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:active {
  transform: scale(0.97);
}

#game {
  display: none;
  flex: 1;
  position: relative;
  background: #f3e8ff;
  overflow: hidden;
}

.heart {
  position: absolute;
  font-size: 28px;
  cursor: pointer;
}

#scoreBoard {
  text-align: center;
  padding: 10px;
  background: #6a11cb;
  color: white;
  font-weight: bold;
}

#finalMessage {
  display: none;
  text-align: center;
  padding: 20px;
  font-size: 17px;
  color: #6a11cb;
}

.choiceBtns {
  display: none;
  text-align: center;
  padding-bottom: 15px;
}

.confetti {
  position: fixed;
  width: 8px;
  height: 8px;
  top: -10px;
  animation: fall 3s linear forwards;
}

@keyframes fall {
  to {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div id="phone">

  <div id="chat">
    <div class="message sent">Hey Megan 😊</div>
    <div class="message sent">I made something special just for you...</div>
    <div class="message sent">Catch 10 hearts to unlock it 💜</div>
  </div>

  <button id="startBtn">Start Game 🎮</button>

  <div id="game">
    <div id="scoreBoard">Score: 0</div>
  </div>

  <div id="finalMessage">
    Megan 💜<br><br>
    You genuinely make my days better.<br>
    Talking to you always makes me smile.<br><br>
    So I wanted to ask you something from the heart...<br><br>
    <strong>Will you be my Valentine? 💕</strong>
  </div>

  <div class="choiceBtns" id="choices">
    <button onclick="yesAnswer()">Yes 💖</button>
    <button onclick="noAnswer()">No 🙈</button>
  </div>

</div>

<script>
/* Floating Background Hearts */
for (let i = 0; i < 25; i++) {
  const heart = document.createElement("div");
  heart.className = "bg-heart";
  heart.innerHTML = "💜";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = (6 + Math.random() * 6) + "s";
  document.body.appendChild(heart);
}

const startBtn = document.getElementById("startBtn");
const game = document.getElementById("game");
const scoreBoard = document.getElementById("scoreBoard");
const finalMessage = document.getElementById("finalMessage");
const choices = document.getElementById("choices");

let score = 0;
const maxScore = 10;
let gameInterval;

startBtn.addEventListener("click", () => {
  startBtn.style.display = "none";
  document.getElementById("chat").style.display = "none";
  game.style.display = "block";
  gameInterval = setInterval(createHeart, 800);
});

function createHeart() {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "💜";
  heart.style.left = Math.random() * (game.clientWidth - 30) + "px";
  heart.style.top = "0px";
  game.appendChild(heart);

  const fall = setInterval(() => {
    heart.style.top = heart.offsetTop + 5 + "px";
    if (heart.offsetTop > game.clientHeight) {
      heart.remove();
      clearInterval(fall);
    }
  }, 30);

  heart.addEventListener("click", () => {
    score++;
    scoreBoard.innerText = "Score: " + score;
    heart.remove();
    clearInterval(fall);

    if (score >= maxScore) endGame();
  });
}

function endGame() {
  clearInterval(gameInterval);
  game.style.display = "none";
  finalMessage.style.display = "block";
  choices.style.display = "block";
  launchConfetti();
}

function launchConfetti() {
  const colors = ["#ff4d6d", "#ffd60a", "#6a11cb", "#00c2ff"];
  for (let i = 0; i < 70; i++) {
    const conf = document.createElement("div");
    conf.className = "confetti";
    conf.style.left = Math.random() * 100 + "vw";
    conf.style.background = colors[Math.floor(Math.random() * colors.length)];
    document.body.appendChild(conf);
    setTimeout(() => conf.remove(), 3000);
  }
}

function yesAnswer() {
  finalMessage.innerHTML = "You just made me the happiest person right now 💜✨";
  choices.style.display = "none";
}

function noAnswer() {
  finalMessage.innerHTML = "That’s okay 😊 I just wanted you to know how special you are to me 💜";
  choices.style.display = "none";
}
</script>

</body>
</html>
