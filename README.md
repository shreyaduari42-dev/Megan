<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Message For Megan 💌</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #ffe6eb;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

#phone {
    width: 95%;
    max-width: 400px;
    height: 90vh;
    background: white;
    border-radius: 25px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    overflow: hidden;
    display: flex;
    flex-direction: column;
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
    background: #ff4d6d;
    color: white;
    align-self: flex-end;
}

.received {
    background: #f1f1f1;
    align-self: flex-start;
}

#startBtn {
    margin: 15px;
    padding: 12px;
    border: none;
    border-radius: 20px;
    background: #ff4d6d;
    color: white;
    font-size: 16px;
}

#game {
    display: none;
    flex: 1;
    position: relative;
    background: #fff0f5;
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
    background: #ff4d6d;
    color: white;
    font-weight: bold;
}

#finalMessage {
    display: none;
    text-align: center;
    padding: 25px;
    font-size: 18px;
    color: #ff4d6d;
}
</style>
</head>

<body>

<div id="phone">

    <div id="chat">
        <div class="message sent">Hey Megan 😊</div>
        <div class="message sent">I made something just for you...</div>
        <div class="message sent">But first you have to win a tiny game 💕</div>
        <div class="message received">Oh really? 👀</div>
        <div class="message sent">Catch 10 hearts and unlock your surprise 💖</div>
    </div>

    <button id="startBtn">Start Game 🎮</button>

    <div id="game">
        <div id="scoreBoard">Score: 0</div>
    </div>

    <div id="finalMessage">
        💖 Megan, you caught all the hearts! 💖<br><br>
        From the moment we started talking,  
        you've made my days brighter 🌸✨<br><br>
        So I wanted to ask you something special...<br><br>
        <strong>Will you be my Valentine? 💕</strong>
    </div>

</div>

<script>
const startBtn = document.getElementById("startBtn");
const game = document.getElementById("game");
const scoreBoard = document.getElementById("scoreBoard");
const finalMessage = document.getElementById("finalMessage");

let score = 0;
let maxScore = 10;
let gameInterval;

startBtn.onclick = function() {
    startBtn.style.display = "none";
    document.getElementById("chat").style.display = "none";
    game.style.display = "block";
    startGame();
}

function startGame() {
    gameInterval = setInterval(createHeart, 800);
}

function createHeart() {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "💖";
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
}
</script>

</body>
</html>
