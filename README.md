# Gamertag-generator
A gamer tag generator for anyone
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Legendary Gamertag Generator</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
:root{
--bg:#020617;--card:#020617;--text:#fff;--accent:#3b82f6;
}
.light{
--bg:#e5e7eb;--card:#fff;--text:#020617;
}
body{
background:var(--bg);color:var(--text);
font-family:Arial,sans-serif;
display:flex;justify-content:center;align-items:center;
min-height:100vh;
}
.box{
background:var(--card);padding:25px;border-radius:14px;
width:420px;box-shadow:0 0 30px rgba(0,0,0,.7);
}
h2{text-align:center;}
input,select,button{
width:100%;padding:10px;margin-top:10px;
border-radius:6px;border:none;font-size:15px;
}
button{background:var(--accent);color:#fff;cursor:pointer;}
.result div{
background:#0f172a;padding:8px;margin-top:6px;
border-radius:6px;
display:flex;align-items:center;justify-content:space-between;
gap:6px;
}
.badge{font-size:12px;padding:2px 6px;border-radius:6px;}
.avail{background:#22c55e;}
.taken{background:#ef4444;}
.rare{background:#f59e0b;}
.toggle{background:#22c55e;}
</style>
</head>

<body>
<div class="box">
<h2>🏆 Legendary Gamertags</h2>

<input id="clan" placeholder="Clan Tag (optional)" />

<select id="game">
<option>Roblox</option>
<option>Call of Duty</option>
<option>Fortnite</option>
<option>Any Game</option>
</select>

<button onclick="generate()">Generate Usernames</button>
<button class="toggle" onclick="toggleMode()">Toggle Dark / Light</button>

<div class="result" id="result"></div>
</div>

<script>
const parts1=["Shadow","Void","Storm","Ghost","Iron","Frost","Dark","Night"];
const parts2=["X","Z","V","ix","on","er","yx",""];
const suffix=["","HD","OG","FPS","Prime",""];

function availability(){
const r=Math.random();
if(r<0.6) return ["Available","avail"];
if(r<0.85) return ["Taken","taken"];
return ["Rare","rare"];
}

function generate(){
result.innerHTML="";
const clan=clanInput.value;

for(let i=0;i<6;i++){
let base=
parts1[Math.floor(Math.random()*parts1.length)]+
parts2[Math.floor(Math.random()*parts2.length)]+
suffix[Math.floor(Math.random()*suffix.length)];

let num=Math.floor(Math.random()*999);
let name=(clan?clan:"")+base+num;

let [label,cls]=availability();

const div=document.createElement("div");
div.innerHTML=`
<span>${name}</span>
<span class="badge ${cls}">${label}</span>
<button onclick="navigator.clipboard.writeText('${name}')">📋</button>
`;
result.appendChild(div);
}
}

function toggleMode(){
document.body.classList.toggle("light");
}

const clanInput=document.getElementById("clan");
const result=document.getElementById("result");
</script>
</body>
</html>
