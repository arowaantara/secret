<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine ❤️</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(to bottom right, #ff758c, #ff7eb3);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  font-family: Arial, sans-serif;
}

.container {
  background: white;
  padding: 30px 40px;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
  z-index: 2;
}

h1 {
  color: #ff3366;
}

.buttons {
  margin-top: 20px;
  position: relative;
  height: 80px;
}

button {
  padding: 12px 25px;
  font-size: 18px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
}

#yesBtn {
  background: #ff3366;
  color: white;
}

#noBtn {
  background: #ccc;
  position: absolute;
}

/* Floating Hearts */

.heart {
  position: absolute;
  width: 20px;
  height: 20px;
  background: red;
  transform: rotate(45deg);
  animation: float 8s linear infinite;
}

.heart::before,
.heart::after {
  content: "";
  position: absolute;
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
}

.heart::before {
  top: -10px;
  left: 0;
}

.heart::after {
  left: -10px;
  top: 0;
}

@keyframes float {
  0% {
    bottom: -50px;
    opacity: 1;
  }
  100% {
    bottom: 110%;
    opacity: 0;
  }
}

/* Music Button */

#musicBtn {
position: fixed;
bottom: 20px;
right: 20px;
padding: 10px 15px;
border-radius: 50%;
border: none;
font-size: 18px;
cursor: pointer;
z-index: 5;
}
</style>
</head>

<body>

<!-- Music -->
<audio id="bgMusic" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<button id="musicBtn">🔊</button>

<div class="container" id="box">
  <h1>Will You Be My Valentine? 💘</h1>

  <div class="buttons">
    <button id="yesBtn">Yes ❤️</button>
    <button id="noBtn">No 💔</button>
  </div>
</div>

<script>

// No Button Escape 😈
const noBtn = document.getElementById("noBtn");

noBtn.addEventListener("mouseover", () => {
  const x = Math.random() * (window.innerWidth - 100);
  const y = Math.random() * (window.innerHeight - 100);

  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";
});

// YES Button Action ❤️
document.getElementById("yesBtn").addEventListener("click", () => {
  document.getElementById("box").innerHTML = `
    <h1>I knew you would say YES 😍</h1>
    <p>Let's meet today 💖</p>
    <h2>📍 Hotel: Rose Garden Hotel</h2>
    <h2>⏰ Time: 7:00 PM</h2>
    <h1>❤️❤️❤️</h1>
  `;
});

// Floating Hearts Generator 💕
function createHeart() {
  const heart = document.createElement("div");
  heart.classList.add("heart");

  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = Math.random() * 3 + 5 + "s";

  document.body.appendChild(heart);

  setTimeout(() => {
    heart.remove();
  }, 8000);
}

setInterval(createHeart, 400);

// Background Music Control 🎵

const music = document.getElementById("bgMusic");
const musicBtn = document.getElementById("musicBtn");

let isPlaying = false;

// Auto play after first click
document.body.addEventListener("click", () => {
  if (!isPlaying) {
    music.play();
    isPlaying = true;
  }
});

// Mute / Unmute
musicBtn.addEventListener("click", () => {
  if (music.paused) {
    music.play();
    musicBtn.innerHTML = "🔊";
  } else {
    music.pause();
    musicBtn.innerHTML = "🔇";
  }
});

</script>

</body>
</html>
