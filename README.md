<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Xurshida uchun Premium Tasbeh</title>

<link href="https://fonts.googleapis.com/css2?family=Amiri&display=swap" rel="stylesheet">

<style>
body{
margin:0;
font-family:Arial;
background:linear-gradient(135deg,#1e3c72,#2a5298);
display:flex;
justify-content:center;
align-items:center;
height:100vh;
overflow:hidden;
color:white;
}

.container{
width:390px;
background:rgba(255,255,255,0.1);
backdrop-filter:blur(15px);
padding:20px;
border-radius:25px;
box-shadow:0 20px 50px rgba(0,0,0,0.5);
text-align:center;
position:relative;
}

h2{margin-bottom:5px;}

.count{
font-size:60px;
margin:10px 0;
transition:0.2s;
}

.bounce{
transform:scale(1.2);
}

.arabic{
font-family:'Amiri', serif;
font-size:30px;
}

.read{font-weight:bold;margin-top:5px;}
.tarjima{font-size:14px;color:#ddd;}

input{
width:100%;
padding:8px;
margin-top:8px;
border-radius:10px;
border:none;
}

.buttons{
display:flex;
justify-content:center;
gap:10px;
margin-top:15px;
}

button{
padding:12px 20px;
font-size:18px;
border:none;
border-radius:12px;
cursor:pointer;
transition:0.2s;
}

.plus{
background:#00ff99;
color:black;
}
.plus:active{
transform:scale(0.9);
}

.reset{background:#ff4d4d;color:white;}

.finish{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.8);
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
color:white;
font-size:22px;
display:none;
text-align:center;
padding:20px;
}

.dark{
background:linear-gradient(135deg,#000000,#434343);
}
</style>
</head>
<body>

<div class="container">

<h2>🤍 Xurshida uchun Tasbeh</h2>

<div class="count" id="count">0</div>

<div class="arabic" id="arabic"></div>
<div class="read" id="read"></div>
<div class="tarjima" id="tarjima"></div>

<input type="text" id="limitInput" placeholder="Necha marta aytasiz? (masalan 33 yoki 0=cheksiz)">

<input type="text" id="newArabic" placeholder="Arabcha zikr">
<input type="text" id="newRead" placeholder="O'qilishi">
<input type="text" id="newTarjima" placeholder="Tarjimasi">

<div class="buttons">
<button class="plus" onclick="plus()">+</button>
<button class="reset" onclick="resetCount()">Reset</button>
</div>

</div>

<div class="finish" id="finish">
<div id="finishText"></div>
<br>
<button onclick="closeFinish()">Yopish</button>
</div>

<audio id="music">
<source src="https://www.soundjay.com/buttons/sounds/button-3.mp3">
</audio>

<script>
let count=0;

function plus(){
let arabic=document.getElementById("newArabic").value;
let read=document.getElementById("newRead").value;
let tarjima=document.getElementById("newTarjima").value;
let limit=parseInt(document.getElementById("limitInput").value);

if(!arabic) return;

document.getElementById("arabic").innerText=arabic;
document.getElementById("read").innerText=read;
document.getElementById("tarjima").innerText=tarjima;

count++;
document.getElementById("count").innerText=count;

let c=document.getElementById("count");
c.classList.add("bounce");
setTimeout(()=>c.classList.remove("bounce"),200);

if(limit && limit>0 && count>=limit){
document.getElementById("music").play();
document.getElementById("finish").style.display="flex";
document.getElementById("finishText").innerHTML=
"🌿 MashaAlloh 🌿<br><br>" +
limit + " marta zikr yakunlandi 🤍<br><br>" +
"Alloh Xurshida opaning duolarini qabul qilsin 🤲✨";
}
}

function resetCount(){
count=0;
document.getElementById("count").innerText=count;
}

function closeFinish(){
document.getElementById("finish").style.display="none";
resetCount();
}

document.body.addEventListener("dblclick",()=>{
document.body.classList.toggle("dark");
});
</script>

</body>
</html>
