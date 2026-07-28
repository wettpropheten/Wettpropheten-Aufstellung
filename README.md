<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats 3D Pro</title>


<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


:root{

--home-color:#00b7ff;
--away-color:#ff4757;

}



body{

margin:0;

background:
radial-gradient(circle at top,#222,#000 60%);

color:white;

}





.container{

width:1500px;

margin:20px auto;

background:rgba(10,10,10,.95);

padding:20px;

border-radius:25px;

box-shadow:
0 30px 80px #000,
inset 0 0 40px #111;

}





.layout{

display:grid;

grid-template-columns:360px 1fr;

gap:20px;

}






/* ==========================
   LINKER SPIELTAG
========================== */


.left-panel{

background:
linear-gradient(145deg,#151515,#050505);

border-radius:20px;

padding:15px;

height:950px;

overflow:auto;

box-shadow:

10px 10px 25px #000,
inset 0 0 20px #222;

}



.left-panel h2{

text-align:center;

font-size:26px;

}





#matchInput{

width:100%;

height:250px;

background:#000;

color:white;

border-radius:15px;

border:1px solid #444;

padding:15px;

resize:none;

}





.load-button{

width:100%;

margin-top:10px;

padding:15px;

background:#222;

color:white;

border-radius:12px;

border:1px solid #555;

font-weight:bold;

cursor:pointer;

transition:.3s;

}



.load-button:hover{

transform:translateY(-3px);

background:#333;

}







.match-card{

background:

linear-gradient(145deg,#222,#111);

padding:15px;

margin-top:12px;

border-radius:15px;

border:1px solid #444;

cursor:pointer;

box-shadow:

5px 5px 15px #000;

transition:.3s;

}



.match-card:hover{

transform:
translateY(-5px)
scale(1.02);

box-shadow:

10px 15px 30px #000;

}





.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:17px;

font-weight:bold;

margin:6px 0;

}



.match-vs{

text-align:center;

color:#777;

}









/* ==========================
   RECHTE SEITE
========================== */


.right-panel{

background:

linear-gradient(145deg,#111,#050505);

border-radius:20px;

padding:25px;

box-shadow:

inset 0 0 30px #222,
10px 10px 30px #000;

}






.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

border-bottom:1px solid #333;

padding-bottom:25px;

}





.team-name{

width:40%;

text-align:center;

font-size:34px;

font-weight:bold;

text-shadow:

0 5px 10px #000;

}





.score{

font-size:70px;

font-weight:bold;

}





/* ==========================
   STATISTIK BALKEN
========================== */


.stat{

margin-top:35px;

}





.stat-title{

text-align:center;

font-size:24px;

font-weight:bold;

margin-bottom:15px;

}





.values{

display:flex;

justify-content:space-between;

font-size:30px;

font-weight:bold;

}





.home-value{

color:var(--home-color);

}



.away-value{

color:var(--away-color);

}





.bar{

height:28px;

background:#000;

border-radius:20px;

overflow:hidden;

display:flex;

border:1px solid #444;

box-shadow:

inset 0 0 15px #000;

}





.home-bar{

height:100%;

background:var(--home-color);

box-shadow:

0 0 15px var(--home-color);

}





.away-bar{

height:100%;

background:var(--away-color);

box-shadow:

0 0 15px var(--away-color);

}







/* ==========================
   SPEICHER BUTTON
========================== */


.save-area{

display:flex;

gap:15px;

margin-top:25px;

}



.action-button{

flex:1;

padding:15px;

background:#222;

color:white;

border-radius:15px;

border:1px solid #555;

font-weight:bold;

cursor:pointer;

transition:.3s;

}



.action-button:hover{

transform:translateY(-3px);

background:#333;

}






/* ==========================
   STATISTIK BOXEN
========================== */


.stats-grid{

display:grid;

grid-template-columns:repeat(3,1fr);

gap:15px;

margin-top:35px;

}





.stat-box{

background:

linear-gradient(145deg,#222,#101010);

border-radius:15px;

padding:20px;

text-align:center;

border:1px solid #444;

box-shadow:

8px 8px 20px #000;

}





.stat-title-small{

color:#aaa;

font-size:14px;

}





.stat-number{

font-size:32px;

font-weight:bold;

margin-top:10px;

}





.home-text{

color:var(--home-color);

}



.away-text{

color:var(--away-color);

}






/* ==========================
   DATEN
========================== */


.input-area{

margin-top:35px;

background:#0b0b0b;

padding:20px;

border-radius:20px;

border:1px solid #333;

}



#dataInput{

width:100%;

height:220px;

background:#000;

color:white;

border-radius:15px;

padding:15px;

font-size:16px;

}



.update-button{

width:100%;

margin-top:15px;

padding:15px;

background:#222;

color:white;

border-radius:15px;

border:1px solid #555;

font-size:18px;

font-weight:bold;

cursor:pointer;

}
</style>

</head>


<body>


<div class="container">


<div class="layout">



<!-- ==========================
     LINKE SPIELTAGSLISTE
========================== -->


<div class="left-panel">


<h2>
SPIELTAG
</h2>



<textarea id="matchInput"
placeholder="
Beispiel:

29.08. 15:30
1. FC Köln
1. FC Köln
TSG Hoffenheim
TSG Hoffenheim
-
-
"></textarea>



<button class="load-button"
onclick="loadMatches()">

SPIELE LADEN

</button>



<div id="matchList">

</div>


</div>








<!-- ==========================
     RECHTE SEITE
========================== -->


<div class="right-panel">



<div class="scoreboard">


<div class="team-name" id="homeName">

HEIM

</div>



<div class="score">

0 : 0

</div>



<div class="team-name" id="awayName">

GAST

</div>


</div>







<!-- XG -->


<div class="stat">


<div class="stat-title">

Expected Goals (xG)

</div>


<div class="values">


<span id="xgHome"
class="home-value">

0.00

</span>



<span id="xgAway"
class="away-value">

0.00

</span>


</div>



<div class="bar">


<div id="xgHomeBar"
class="home-bar"
style="width:50%">

</div>



<div id="xgAwayBar"
class="away-bar"
style="width:50%">

</div>


</div>


</div>







<!-- BALLBESITZ -->


<div class="stat">


<div class="stat-title">

Ballbesitz

</div>


<div class="values">


<span id="posHome"
class="home-value">

50%

</span>



<span id="posAway"
class="away-value">

50%

</span>


</div>



<div class="bar">


<div id="posHomeBar"
class="home-bar"
style="width:50%">

</div>



<div id="posAwayBar"
class="away-bar"
style="width:50%">

</div>


</div>


</div>








<!-- SPEICHER -->


<div class="save-area">


<button class="action-button"
onclick="saveGame()">

SPIEL SPEICHERN

</button>



<button class="action-button"
onclick="loadGame()">

SPIEL LADEN

</button>



<button class="action-button"
onclick="deleteGame()">

LÖSCHEN

</button>


</div>










<!-- STATISTIK BOXEN -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE

</div>


<div class="stat-number">

<span id="shotsHome"
class="home-text">

0

</span>

:

<span id="shotsAway"
class="away-text">

0

</span>


</div>

</div>







<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE AUFS TOR

</div>


<div class="stat-number">


<span id="targetHome"
class="home-text">

0

</span>

:

<span id="targetAway"
class="away-text">

0

</span>


</div>

</div>








<div class="stat-box">

<div class="stat-title-small">

GROSSCHANCEN

</div>


<div class="stat-number">


<span id="chanceHome"
class="home-text">

0

</span>

:

<span id="chanceAway"
class="away-text">

0

</span>


</div>

</div>








<div class="stat-box">

<div class="stat-title-small">

ECKBÄLLE

</div>


<div class="stat-number">


<span id="cornerHome"
class="home-text">

0

</span>

:

<span id="cornerAway"
class="away-text">

0

</span>


</div>

</div>








<div class="stat-box">

<div class="stat-title-small">

PASSQUOTE

</div>


<div class="stat-number">


<span id="passHome"
class="home-text">

0%

</span>

:

<span id="passAway"
class="away-text">

0%

</span>


</div>

</div>








<div class="stat-box">

<div class="stat-title-small">

PÄSSE GESAMT

</div>


<div class="stat-number">


<span id="passesHome"
class="home-text">

0/0

</span>

:

<span id="passesAway"
class="away-text">

0/0

</span>


</div>

</div>








<div class="stat-box">

<div class="stat-title-small">

GELBE KARTEN

</div>


<div class="stat-number">


<span id="cardsHome"
class="home-text">

0

</span>

:

<span id="cardsAway"
class="away-text">

0

</span>


</div>

</div>


</div>








<!-- LIVE DATEN -->


<div class="input-area">


<h2>

LIVE DATEN EINFÜGEN

</h2>



<textarea id="dataInput"

placeholder="
Statistik einfügen:

Expected Goals
Ballbesitz
Schüsse
Pässe
Karten
">

</textarea>



<button class="update-button"
onclick="updateStats()">

AKTUALISIEREN

</button>


</div>

<script>


const teams={

"Borussia Dortmund":"#FDE100",
"BVB":"#FDE100",

"FC Bayern München":"#DC052D",
"Bayern München":"#DC052D",

"Bayer 04 Leverkusen":"#E32221",
"Bayer Leverkusen":"#E32221",

"RB Leipzig":"#FFFFFF",

"VfB Stuttgart":"#FFFFFF",

"Eintracht Frankfurt":"#777777",

"Borussia Mönchengladbach":"#00A651",

"TSG Hoffenheim":"#005CA9",

"SC Freiburg":"#E30613",

"FC Augsburg":"#00875A",

"1. FC Köln":"#E30613",

"FSV Mainz 05":"#C41230",

"1. FSV Mainz 05":"#C41230",

"1. FC Union Berlin":"#E30613",

"FC Schalke 04":"#004C99",

"Schalke 04":"#004C99",

"Hamburger SV":"#005CA9",

"HSV":"#005CA9",

"SC Paderborn":"#005CA9",

"SC Paderborn 07":"#005CA9",

"SV Elversberg":"#D4AF37",

"SV Werder Bremen":"#00875A",

"Werder Bremen":"#00875A"

};



let currentGame="";





/* SPIELTAG LADEN */

function loadMatches(){


let text=document
.getElementById("matchInput")
.value;


let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let list=document
.getElementById("matchList");


list.innerHTML="";


for(let i=0;i<lines.length;i++){


if(lines[i].match(/\d{2}\.\d{2}/)){


let time=lines[i];

let teams=[];



for(let j=i+1;j<lines.length;j++){


if(lines[j]=="-")
break;


if(!teams.includes(lines[j])){

teams.push(lines[j]);

}


}



if(teams.length>=2){


createMatch(
time,
teams[0],
teams[1]
);


}


}


}


}






function createMatch(time,home,away){


let card=document.createElement("div");

card.className="match-card";



card.innerHTML=`

<div class="match-time">
${time}
</div>

<div class="match-team">
${home}
</div>

<div class="match-vs">
-
</div>

<div class="match-team">
${away}
</div>

`;



card.onclick=function(){


setTeams(home,away);

loadGame();


};



document
.getElementById("matchList")
.appendChild(card);


}








/* SPIEL AUSWÄHLEN */


function setTeams(home,away){


currentGame=
home+"_"+away;



homeName.innerHTML=home;

awayName.innerHTML=away;



let hc=teams[home] || "#00b7ff";

let ac=teams[away] || "#ff4757";



document.documentElement
.style.setProperty(
"--home-color",
hc
);


document.documentElement
.style.setProperty(
"--away-color",
ac
);



}









/* STATISTIK AUSLESEN */


function findValues(name){


let text=
dataInput.value;



let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let index=lines.findIndex(

x=>x.toLowerCase()
.includes(name.toLowerCase())

);



if(index<0)
return [0,0];



let nums=[];



for(let i=index+1;i<lines.length;i++){


let n=lines[i]
.match(/\d+([.,]\d+)?/);



if(n){

nums.push(
Number(
n[0].replace(",",".")
)
);

}



if(nums.length==2)
break;


}



return nums.length==2?
nums:
[0,0];


}








function updateStats(){



let xg=findValues("Expected Goals");


xgHome.innerHTML=
xg[0].toFixed(2);


xgAway.innerHTML=
xg[1].toFixed(2);





updateBar(
xg[0],
xg[1],
"xgHomeBar",
"xgAwayBar"
);






let pos=findValues("Ballbesitz");


posHome.innerHTML=
pos[0]+"%";


posAway.innerHTML=
pos[1]+"%";



posHomeBar.style.width=
pos[0]+"%";


posAwayBar.style.width=
pos[1]+"%";






let stats=[


["Schüsse","shotsHome","shotsAway"],

["Schüsse aufs Tor","targetHome","targetAway"],

["Großchancen","chanceHome","chanceAway"],

["Eckbälle","cornerHome","cornerAway"],

["Gelbe Karten","cardsHome","cardsAway"]


];



stats.forEach(s=>{


let v=findValues(s[0]);



document
.getElementById(s[1])
.innerHTML=v[0];


document
.getElementById(s[2])
.innerHTML=v[1];



});




saveGame();



}









function updateBar(a,b,left,right){


let total=a+b;


if(total<=0)
return;



document
.getElementById(left)
.style.width=
(a/total*100)+"%";



document
.getElementById(right)
.style.width=
(b/total*100)+"%";


}









/* SPIEL SPEICHERN */


function saveGame(){


if(!currentGame)
return;



let data={};



document.querySelectorAll("[id]")
.forEach(e=>{


if(
e.id!="matchInput" &&
e.id!="matchList" &&
e.id!="dataInput"
){

data[e.id]=e.innerHTML;

}


});



localStorage.setItem(

"LiveStats_"+currentGame,

JSON.stringify(data)

);



}









/* SPIEL LADEN */


function loadGame(){


if(!currentGame)
return;



let data=
localStorage.getItem(
"LiveStats_"+currentGame
);



if(!data)
return;



data=JSON.parse(data);



Object.keys(data)
.forEach(id=>{


let e=document.getElementById(id);



if(e){

e.innerHTML=data[id];

}


});


}









/* SPIEL LÖSCHEN */


function deleteGame(){


if(!currentGame)
return;



localStorage.removeItem(
"LiveStats_"+currentGame
);



alert("Spiel gelöscht");


}






</script>


</div>

</div>


</body>

</html>
