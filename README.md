<html lang="pl">
<head>
<meta charset="UTF-8">
<title>Walentynki 💖</title>

<style>
body {
    background: #111827;
    color: white;
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
    overflow: hidden;
}

.box {
    background: #1e293b;
    padding: 30px;
    border-radius: 20px;
    box-shadow: 0 0 30px rgba(255, 100, 100, 0.4);
    position: relative;
    z-index: 2;
}

img {
    width: 200px;
    border-radius: 15px;
    margin-bottom: 20px;
}

button {
    padding: 12px 25px;
    font-size: 18px;
    border-radius: 12px;
    border: none;
    cursor: pointer;
    margin: 10px;
    transition: all 0.2s ease;
}

#yes {
    background: #ef4444;
    color: white;
}

#no {
    background: #475569;
    color: white;
    position: relative;
}

.confetti {
    position: fixed;
    width: 10px;
    height: 10px;
    top: -10px;
    animation: fall 2.5s linear forwards;
    z-index: 1;
}

@keyframes fall {
    to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<div class="box" id="app">
    <img src="tuff.jpeg" alt="Walentynka">
    <h1>Czy zostaniesz moją walentynką? 🤔</h1>
    <button id="yes" onclick="yes()">TAK</button>
    <button id="no" onclick="no()">NIE</button>
</div>

<audio id="popSound" preload="auto">
    <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_4c8a2b8c6b.mp3" type="audio/mpeg">
</audio>

<script>
let yesSize = 1;
let noSize = 1;

function no() {
    yesSize += 0.15;
    document.getElementById("yes").style.transform = `scale(${yesSize})`;

    noSize -= 0.1;
    if (noSize < 0.3) noSize = 0.3;

    const noBtn = document.getElementById("no");
    const x = Math.random() * 200 - 100;
    const y = Math.random() * 200 - 100;
    noBtn.style.transform = `translate(${x}px, ${y}px) scale(${noSize})`;
}

function yes() {
    document.getElementById("popSound").play();

    for (let i = 0; i < 120; i++) {
        createConfetti();
    }

    document.getElementById("app").innerHTML = `
        <p>Mega tuff 😎</p>
    `;
}

function createConfetti() {
    const confetti = document.createElement("div");
    confetti.classList.add("confetti");

    const colors = ["#ef4444", "#fb7185", "#facc15", "#22c55e", "#38bdf8"];
    confetti.style.background = colors[Math.floor(Math.random() * colors.length)];

    confetti.style.left = Math.random() * 100 + "vw";
    confetti.style.animationDuration = (Math.random() * 2 + 2) + "s";

    document.body.appendChild(confetti);

    setTimeout(() => {
        confetti.remove();
    }, 3000);
}
</script>

</body>
</html>
