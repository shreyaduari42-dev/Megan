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
    font-size
