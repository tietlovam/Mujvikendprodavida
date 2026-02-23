<!DOCTYPE html>  
<html lang="cs">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
<title>Víkend pro Davida 💫</title>  
  
<style>  
body {  
    margin: 0;  
    font-family: Arial, sans-serif;  
    background: linear-gradient(180deg, #1a1a2e, #0f3460, #000000);  
    color: white;  
    display: flex;  
    justify-content: center;  
    align-items: center;  
    height: 100vh;  
    text-align: center;  
    flex-direction: column;  
    overflow: hidden;  
    transition: background 2s ease;  
}  
  
h1 { font-size: 2.5em; margin-bottom: 10px; }  
  
.subtitle { font-size: 1.2em; opacity: 0.9; margin-bottom: 20px; }  
  
.countdown { font-size: 2em; letter-spacing: 3px; margin: 20px 0; }  
  
.dailyMessage { margin-top: 20px; font-size: 1.3em; min-height: 60px; }  
  
.secret { margin-top: 25px; font-size: 1.2em; opacity: 0; transition: opacity 1s ease; }  
  
.visible { opacity: 1; }  
  
/* Hvězdy */  
.stars {  
    position: fixed;  
    width: 100%;  
    height: 100%;  
    background: transparent;  
    overflow: hidden;  
    z-index: -1;  
}  
  
.star {  
    position: absolute;  
    width: 2px;  
    height: 2px;  
    background: white;  
    animation: twinkle 2s infinite alternate;  
}  
  
@keyframes twinkle {  
    from { opacity: 0.2; }  
    to { opacity: 1; }  
}  
</style>  
</head>  
<body onclick="revealSecret()">  
  
<div class="stars" id="stars"></div>  
  
<h1>Davide… 💫</h1>  
<div class="subtitle">tohle je jenom tvůj víkend ode mě. Jen pro tebe.</div>  
  
<div class="countdown" id="countdown"></div>  
<div class="dailyMessage" id="dailyMessage"></div>  
<div class="secret" id="secretMessage"></div>  
  
<script>  
// ==== ODPOČET ====  
const targetDate = new Date("March 7, 2026 18:00:00 GMT+0100").getTime();  
  
setInterval(function() {  
    const now = new Date().getTime();  
    const distance = targetDate - now;  
  
    const days = Math.floor(distance / (1000 * 60 * 60 * 24));  
    const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));  
    const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));  
    const seconds = Math.floor((distance % (1000 * 60)) / 1000);  
  
    document.getElementById("countdown").innerHTML =  
        days + "d " + hours + "h "  
        + minutes + "m " + seconds + "s ";  
}, 1000);  
  
// ==== DENNÍ TEXT ====  
const messages = [  
"Nemáš tušení, jak moc se na ten víkend těším…",  
"Chci, aby ses cítil vybraný.",  
"Možná začnu polibkem, který nebude chtít skončit.",  
"Tentokrát začnu já.",  
"Budu ti blíž, než čekáš.",  
"Tenhle víkend je jen náš."  
];  
  
const today = new Date();  
const dayIndex = today.getDate() % messages.length;  
document.getElementById("dailyMessage").innerText = messages[dayIndex];  
  
// ==== TAJNÁ ZPRÁVA ====  
const secrets = [  
"Davide… budu tě mít jen pro sebe.",  
"Připrav se. Tentokrát řídím večer já.",  
"Možná zjistíš, jak moc dokážu být iniciativní.",  
"Nenechám tě jen tak usnout."  
];  
  
function revealSecret() {  
    const randomIndex = Math.floor(Math.random() * secrets.length);  
    const el = document.getElementById("secretMessage");  
    el.innerText = secrets[randomIndex];  
    el.classList.add("visible");  
}  
  
// ==== NOČNÍ REŽIM PO PŮLNOCI ====  
const hour = new Date().getHours();  
if (hour >= 0 && hour < 5) {  
    document.body.style.background = "black";  
    createStars();  
}  
  
function createStars() {  
    const starsContainer = document.getElementById("stars");  
    for (let i = 0; i < 80; i++) {  
        let star = document.createElement("div");  
        star.className = "star";  
        star.style.top = Math.random() * 100 + "%";  
        star.style.left = Math.random() * 100 + "%";  
        starsContainer.appendChild(star);  
    }  
}  
</script>  
  
</body>  
</html>  
