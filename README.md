│
├── index.html        (Home + Map)
├── veri.html         (North Albania)
├── mes.html          (Central Albania)
├── jug.html          (South Albania)
│
├── style.css         (Design + animations)
├── script.js         (JavaScript logic)
│
└── audio/
    ├── veri.mp3
    ├── mes.mp3
    └── jug.mp3
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background-color: #f4f4f4;
    line-height: 1.6;
}

header {
    background-color: #b30000;
    color: white;
    padding: 25px;
    text-align: center;
}

nav {
    background-color: #333;
    padding: 12px;
    text-align: center;
}

nav a {
    color: white;
    margin: 0 15px;
    text-decoration: none;
    font-weight: bold;
}

nav a:hover {
    color: #ffcccc;
}

section {
    background-color: white;
    margin: 25px;
    padding: 25px;
    border-radius: 10px;
    animation: fadeIn 1.2s ease-in;
}

img {
    width: 100%;
    max-width: 500px;
    border-radius: 10px;
    margin-top: 15px;
}

button {
    background-color: #b30000;
    color: white;
    border: none;
    padding: 10px 18px;
    cursor: pointer;
    border-radius: 6px;
    margin: 5px;
}

button:hover {
    background-color: #800000;
}

footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 15px;
}

/* Map styling */
.map-container {
    text-align: center;
}

.map-container img {
    max-width: 400px;
    margin: 20px auto;
    display: block;
}

/* Animation */
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
let bgMusicPlaying = false;

/* Stop all audio */
function stopAllAudio() {
    const audios = document.querySelectorAll("audio");
    audios.forEach(audio => {
        audio.pause();
        audio.currentTime = 0;
    });
}

/* Play selected audio */
function playAudio(id) {
    stopAllAudio();
    document.getElementById(id).play();
}

/* Pause audio */
function pauseAudio(id) {
    document.getElementById(id).pause();
}

/* Volume slider */
function setVolume(value) {
    document.querySelectorAll("audio").forEach(audio => {
        audio.volume = value;
    });
}

/* Background music ON/OFF */
function toggleBackgroundMusic(id) {
    const audio = document.getElementById(id);

    if (!bgMusicPlaying) {
        stopAllAudio();
        audio.loop = true;
        audio.volume = 0.3;
        audio.play();
        bgMusicPlaying = true;
    } else {
        audio.pause();
        audio.currentTime = 0;
        bgMusicPlaying = false;
    }
}

/* Auto-stop when changing page */
window.addEventListener("beforeunload", stopAllAudio);
<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>Kultura dhe Folklori Shqiptar</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
    <h1>Kultura dhe Folklori Shqiptar</h1>
    <p>Veri • Mes • Jug</p>
</header>

<nav>
    <a href="index.html">Home</a>
    <a href="veri.html">Veriu</a>
    <a href="mes.html">Mes Shqipëria</a>
    <a href="jug.html">Jugu</a>
</nav>

<section>
    <h2>Mirë se vini</h2>
    <p>
        Ky projekt paraqet kulturën, folklorin, muzikën dhe traditat
        e Shqipërisë së Veriut, të Mesme dhe të Jugut.
    </p>

    <h2>Harta e Shqipërisë</h2>

    <div class="map-container">
        <img src="https://upload.wikimedia.org/wikipedia/commons/3/36/Albania_map.png"
             alt="Harta e Shqipërisë">

        <button onclick="location.href='veri.html'">Veriu</button>
        <button onclick="location.href='mes.html'">Mes Shqipëria</button>
        <button onclick="location.href='jug.html'">Jugu</button>
    </div>
</section>

<footer>
    <p>© 2026 | Projekt Shkollor</p>
</footer>

</body>
</html>
<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>Shqipëria e Veriut</title>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
</head>
<body>

<header>
    <h1>Shqipëria e Veriut</h1>
</header>

<nav>
    <a href="index.html">Home</a>
    <a href="veri.html">Veriu</a>
    <a href="mes.html">Mes Shqipëria</a>
    <a href="jug.html">Jugu</a>
</nav>

<section>
    <p>Folklor epik, lahutë dhe tradita të forta.</p>

    <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/Albanian_traditional_clothing_north.jpg">

    <audio id="audioVeri">
        <source src="audio/veri.mp3" type="audio/mpeg">
    </audio>

    <button onclick="playAudio('audioVeri')">▶ Luaj</button>
    <button onclick="pauseAudio('audioVeri')">⏸ Ndalo</button>
    <button onclick="toggleBackgroundMusic('audioVeri')">🎵 Muzikë në sfond</button>

    <h4>Volumi</h4>
    <input type="range" min="0" max="1" step="0.1" value="0.5"
           onchange="setVolume(this.value)">
</section>

<footer>
    <p>Folklori i Veriut Shqiptar</p>
</footer>

</body>
</html>
