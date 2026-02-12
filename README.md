<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Megan 💜</title>

<style>
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
    position: absolute;
    color: rgba(255,255,255,0.3);
    font-size: 20px;
    animation: floatUp 8s linear infinite;
}

@keyframes floatUp {
    from { transform: translateY(100vh); }
    to { transform: translateY(-10vh); }
}

#phone {
    width: 95%;
    max-width: 400px;
    height: 90vh;
    background: white;
    border-radius: 25px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    z-index: 2;
}

#chat {
    flex: 1;
    padding: 15px;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
}

.message {
    margin: 10px 0;
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

.received {
    background: #eee;
    align-self: flex-start;
}

button {
    margin: 10px;
    padding: 12px;
    border: none;
    border-radius: 20px;
    background: #6a11cb;
    color: white;
    font-size: 16px;
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
    font-size: 18px;
    color: #6a11cb;
}

.choiceBtns {
    display: none;
    text-align: center;
}

.confetti {
    position: absolute;
    width: 8px;
    height: 8px;
    background: red;
    top: 0;
    animation: fall 3s linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<!-- Floating Background Hearts -->
<script>
for (let i = 0; i < 20; i++) {
    const bgHeart = document.createElement("div");
    bgHeart.classList.add("bg-heart");
    bgHeart.innerHTML = "💜";
    bgHeart.style.left = Math.random() * 100 + "vw";
    bgHeart.style.animationDuration = (5 + Math.random()*5) + "s";
    document.body.appendChild(bgHeart);
}
</script>

<div id="phone">

    <div id="chat">
        <div class="message sent">Hey Megan 😊</div>
        <div class="message sent">I made something special for you...</div>
        <div class="message sent">Catch 10 hearts to unlock it 💜</div>
    </div>

    <button id="startBtn">Start Game 🎮</button>

    <div id="game">
        <div id="scoreBoard">Score: 0</div>
    </div>

    <div id="finalMessage">
        Megan 💜<br><br>
        Every time we talk, you make my day better.<br>
        You make me smile in ways you probably don't even realize.<br><br>
        So I just wanted to ask you something from the heart...<br><br>
        <strong>Will you be my Valentine? 💕</strong>
    </div>

    <div class="choiceBtns" id="choices">
        <button onclick="yesAnswer()">Yes 💖</button>
        <button onclick="noAnswer()">No 🙈</button>
    </div>

</div>

<script>
const startBtn = document.getElementById("startBtn");
const game = document.getElementById("game");
const scoreBoard = document.getElementById("scoreBoard");
const finalMessage = document.getElementById("finalMessage");
const choices = document.getElementById("choices");

let score = 0;
let maxScore = 10;
let gameInterval;

startBtn.onclick = function() {
    startBtn.style.display = "none";
    document.getElementById("chat").style.display = "none";
    game.style.display = "block";
    gameInterval = setInterval(createHeart, 800);
}

function createHeart() {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "💜";
    heart.style.left = Math.random() * (game.clientWidth - 30) + "px";
    heart.style.top = "0px";
    game.appendChild(heart);

    let fall = setInterval(() => {
        heart.style.top = heart.offsetTop + 5 + "px";
        if (heart.offsetTop > game.clientHeight) {
            heart.remove();
            clearInterval(fall);
        }
    }, 30);

    heart.onclick = function() {
        score++;
        scoreBoard.innerText = "Score: " + score;
        heart.remove();
        clearInterval(fall);

        if (score >= maxScore) {
            endGame();
        }
    }
}

function endGame() {
    clearInterval(gameInterval);
    game.style.display = "none";
    finalMessage.style.display = "block";
    choices.style.display = "block";
    launchConfetti();
}

function launchConfetti() {
    for (let i = 0; i < 60; i++) {
        const conf = document.createElement("div");
        conf.classList.add("confetti");
        conf.style.left = Math.random() * 100 + "vw";
        conf.style.background = 
            ["#ff4d6d","#ffd60a","#6a11cb","#00c2ff"][Math.floor(Math.random()*4)];
        document.body.appendChild(conf);
        setTimeout(() => conf.remove(), 3000);
    }
}

function yesAnswer() {
    finalMessage.innerHTML = "You just made me the happiest person right now 💜✨";
    choices.style.display = "none";
}

function noAnswer() {
    finalMessage.innerHTML = "That's okay 😊 I just wanted you to know how special you are to me 💜";
    choices.style.display = "none";
}
</script>

</body>
</html>
