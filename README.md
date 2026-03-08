<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Taniya 🎂</title>

<style>

body{
margin:0;
font-family:Arial, sans-serif;
background:linear-gradient(135deg,#ff758c,#ff7eb3);
height:100vh;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
text-align:center;
overflow:hidden;
color:white;
}

.gift{
font-size:120px;
cursor:pointer;
animation:bounce 1.5s infinite;
}

@keyframes bounce{
0%,100%{transform:translateY(0)}
50%{transform:translateY(-15px)}
}

.container{
display:none;
padding:20px;
max-width:320px;
}

#message{
font-size:18px;
min-height:120px;
}

.cake{
font-size:80px;
margin-top:20px;
cursor:pointer;
transition:0.4s;
}

.cut{
transform:rotate(-10deg) scale(1.2);
}

canvas{
position:fixed;
top:0;
left:0;
pointer-events:none;
}

</style>
</head>

<body>

<div id="gift" class="gift">🎁</div>

<div id="content" class="container">

<h1>Happy Birthday Taniya 🎉</h1>

<p id="message"></p>

<div id="cake" class="cake">🎂</div>
<p>Tap the cake to cut it!</p>

</div>

<audio id="music">
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_4b7d25a6c2.mp3?filename=happy-birthday-to-you-piano-version-13976.mp3" type="audio/mpeg">
</audio>

<canvas id="confetti"></canvas>

<script>

/* Typing message */

const text = "Dear Taniya 💖\n\nWishing you the happiest birthday ever! May your day be filled with love, laughter and beautiful surprises. You deserve all the happiness in the world. Enjoy your special day! 🎉🎂";

let i = 0;

function typeWriter(){
if(i < text.length){
document.getElementById("message").innerHTML += text.charAt(i);
i++;
setTimeout(typeWriter,40);
}
}

/* Gift click */

document.getElementById("gift").onclick = function(){

this.style.display="none";

document.getElementById("content").style.display="block";

document.getElementById("music").play();

typeWriter();

startConfetti();

}

/* Cake cutting */

document.getElementById("cake").onclick=function(){

this.classList.add("cut");

setTimeout(()=>{

alert("Cake Cut! Happy Birthday Taniya 🎂🎉")

},500)

}

/* Confetti */

const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let pieces = [];

for(let i=0;i<120;i++){
pieces.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
size:Math.random()*8+4,
speed:Math.random()*3+2
});
}

function startConfetti(){

function update(){

ctx.clearRect(0,0,canvas.width,canvas.height);

pieces.forEach(p=>{

ctx.fillStyle="hsl("+Math.random()*360+",100%,50%)";
ctx.fillRect(p.x,p.y,p.size,p.size);

p.y+=p.speed;

if(p.y>canvas.height)p.y=0;

});

requestAnimationFrame(update);

}

update();

}

</script>

</body>
</html>
