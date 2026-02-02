<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vicky, Will You Be My Valentine? 💖</title>

<style>
body {
    margin: 0;
    min-height: 100vh;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #ff2d75, #ff758c, #ffc3a0);
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    color: white;
    text-align: center;
}

.card {
    background: rgba(255,255,255,0.15);
    padding: 30px 20px;
    border-radius: 25px;
    box-shadow: 0 20px 40px rgba(0,0,0,0.25);
    max-width: 90%;
    width: 400px;
    backdrop-filter: blur(10px);
    z-index: 2;
    position: relative;
}

h1 { font-size: 2rem; margin-bottom: 10px; }
h2 { font-weight: normal; }
.poem {
    font-size: 1rem;
    line-height: 1.5;
    margin: 20px 0;
}

button {
    padding: 12px 24px;
    font-size: 1rem;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    margin: 10px 5px;
    transition: transform 0.2s, left 0.3s, top 0.3s;
}

button:hover { transform: scale(1.05); }

.yes { background: #ff2d75; color: white; }
.no { background: white; color: #ff2d75; position: absolute; }
.music { background: rgba(255,255,255,0.3); color: white; margin-top: 15px; }

.signature {
    margin-top: 20px;
    font-style: italic;
    font-size: 0.9rem;
    opacity: 0.9;
}

.hearts span {
    position: absolute;
    animation: float 6s linear infinite;
    font-size: 20px;
}

@keyframes float {
    0% { transform: translateY(100vh); opacity: 0; }
    50% { opacity: 1; }
    100% { transform: translateY(-10vh); opacity: 0; }
}

@media(max-width: 400px){
    h1 { font-size: 1.6rem; }
    .poem { font-size: 0.95rem; }
    button { font-size: 0.9rem; padding: 10px 20px; }
}
</style>
</head>

<body>

<div class="hearts"></div>

<div class="card" id="card">
    <h1>Vicky 💕</h1>

    <div class="poem">
        Roses aren’t enough to say how I feel,<br>
        Because what I feel for you is honest and real.<br>
        In your smile I find my peace,<br>
        In your presence, my worries cease.<br><br>

        This Valentine’s, I choose you again,<br>
        Not just today, but again and again.<br>
        So here’s my heart, simple and true,<br>
        Hoping it finds a home in you. 💖
    </div>

    <h1>Will you be my Valentine? 💘</h1>

    <div style="position: relative; height: 60px;">
        <button class="yes" onclick="accept()" style="position: relative;">YES 💕</button>
        <button class="no" id="noBtn">No 🙈</button>
    </div>

    <button class="music" onclick="playMusic()">Play Music 🎶</button>

    <div class="signature">
        — From Shadrac Muthama ❤️
    </div>
</div>

<!-- Hidden YouTube Player (Try Me - Jason Derulo) -->
<iframe id="player" width="0" height="0"
src="https://www.youtube.com/embed/8k3Z3J6mV2U?enablejsapi=1"
frameborder="0" allow="autoplay"></iframe>

<script src="https://www.youtube.com/iframe_api"></script>

<script>
let player;

function playMusic() {
    if (!player) {
        player = new YT.Player('player', {
            events: {
                'onReady': function (event) {
                    event.target.playVideo();
                }
            }
        });
    } else {
        player.playVideo();
    }
}

function accept() {
    document.getElementById("card").innerHTML = `
        <h1>She Said YES 💖🎉</h1>
        <p style="font-size:1.1rem; line-height:1.5;">
            Vicky, thank you for choosing me.<br>
            This Valentine’s just became unforgettable.<br><br>
            I can’t wait to create beautiful memories with you ❤️
        </p>
        <h2>Happy Valentine’s Day 💘</h2>
        <div class="signature">— From Shadrac Muthama</div>
    `;
}

// NO button playful trick
const noBtn = document.getElementById('noBtn');
noBtn.addEventListener('mouseenter', () => {
    const cardRect = document.querySelector('.card').getBoundingClientRect();
    const btnWidth = noBtn.offsetWidth;
    const btnHeight = noBtn.offsetHeight;

    let x = Math.random() * (cardRect.width - btnWidth);
    let y = Math.random() * (60 - btnHeight);

    noBtn.style.transition = 'all 0.3s ease';
    noBtn.style.left = x + 'px';
    noBtn.style.top = y + 'px';
    noBtn.style.transform = `rotate(${Math.random()*60 - 30}deg) scale(1.1)`;
});

// Hearts animation
function createHearts() {
    const hearts = document.querySelector('.hearts');
    const heart = document.createElement('span');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 3 + 4) + 's';
    hearts.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
}

setInterval(createHearts, 500);
</script>

</body>
</html>
