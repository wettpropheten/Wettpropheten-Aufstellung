<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro 3D</title>


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

min-height:100vh;

}





.container{

width:1600px;

margin:20px auto;

}





.layout{

display:grid;

grid-template-columns:380px 1fr;

gap:25px;

}





.panel{

background:
linear-gradient(145deg,#151515,#080808);

border-radius:25px;

padding:20px;

box-shadow:

15px 15px 35px #000,

inset -2px -2px 5px rgba(255,255,255,.05),

inset 2px 2px 5px rgba(255,255,255,.08);

}





h2{

margin-top:0;

text-align:center;

}





/* ======================
 SPIELTAG
====================== */


#matchInput{

width:100%;

height:260px;

background:#000;

color:white;

border:1px solid #444;

border-radius:15px;

padding:15px;

resize:none;

}



button{

width:100%;

margin-top:10px;

padding:15px;

background:#222;

color:white;

border:1px solid #555;

border-radius:12px;

font-weight:bold;

cursor:pointer;

transition:.2s;

}



button:hover{

background:#333;

transform:translateY(-2px);

}





.match-card{

background:#111;

border-radius:15px;

padding:15px;

margin-top:12px;

cursor:pointer;

box-shadow:

5px 5px 15px #000,

inset 1px 1px 3px rgba(255,255,255,.05);

transition:.2s;

}



.match-card:hover{

transform:translateX(5px);

background:#191919;

}



.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:18px;

font-weight:bold;

margin:5px;

}



.match-vs{

text-align:center;

color:#777;

}





/* ======================
 SCOREBOARD
====================== */


.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

padding-bottom:25px;

border-bottom:1px solid #333;

}





.team-name{

width:40%;

text-align:center;

font-size:36px;

font-weight:bold;

text-shadow:0 5px 15px #000;

}





.score{

font-size:75px;

font-weight:bold;

}





</style>


</head>


<body>


<div class="container">


<div class="layout">


<div class="panel">


<h2>
SPIELTAG
</h2>


<textarea id="matchInput"
placeholder="
29.08. 15:30
1. FC Köln
TSG Hoffenheim

29.08. 15:30
Bayern München
Borussia Dortmund
"></textarea>



<button onclick="loadMatches()">

SPIELE LADEN

</button>



<button onclick="saveMatchday()">

💾 SPIELTAG SPEICHERN

</button>



<button onclick="loadMatchday()">

↻ SPIELTAG LADEN

</button>



<div id="matchList">

</div>


</div>



<div class="panel">


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
<!-- ======================
 STATISTIK BEREICH
====================== -->


<style>


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

font-size:32px;

font-weight:bold;

}



.home-value{

color:var(--home-color);

}



.away-value{

color:var(--away-color);

}



.bar{

height:25px;

background:#111;

border-radius:20px;

overflow:hidden;

display:flex;

border:1px solid #333;

box-shadow:inset 0 0 10px #000;

}



.home-bar{

height:100%;

background:var(--home-color);

}



.away-bar{

height:100%;

background:var(--away-color);

}






/* ======================
 3D STAT BOXEN
====================== */


.stats-grid{

display:grid;

grid-template-columns:repeat(3,1fr);

gap:18px;

margin-top:35px;

}





.stat-box{

background:

linear-gradient(145deg,#1b1b1b,#080808);

border-radius:18px;

padding:20px;

text-align:center;

box-shadow:

8px 8px 20px #000,

inset 2px 2px 5px rgba(255,255,255,.08);

}



.box-title{

color:#aaa;

font-size:14px;

}



.box-value{

font-size:32px;

font-weight:bold;

margin-top:10px;

}





/* ======================
 EINGABE
====================== */


.input-area{

margin-top:35px;

background:#090909;

border-radius:20px;

padding:20px;

box-shadow:

inset 2px 2px 5px #222,

8px 8px 20px #000;

}



#dataInput{

width:100%;

height:240px;

background:#000;

color:white;

border:1px solid #444;

border-radius:15px;

padding:15px;

font-size:16px;

resize:none;

}





.save-buttons{

display:grid;

grid-template-columns:1fr 1fr;

gap:15px;

margin-top:20px;

}



</style>







<!-- ======================
 EXPECTED GOALS
====================== -->


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








<!-- ======================
 BALLBESITZ
====================== -->


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








<!-- ======================
 SPEICHER SPIEL
====================== -->


<div class="save-buttons">


<button onclick="saveGame()">

💾 SPIEL SPEICHERN

</button>



<button onclick="loadGame()">

↻ SPIEL LADEN

</button>


</div>









<!-- ======================
 STATISTIK KÄSTEN
====================== -->


<div class="stats-grid">



<div class="stat-box">

<div class="box-title">
SCHÜSSE
</div>

<div class="box-value">

<span id="shotsHome"
class="home-value">

0

</span>

:

<span id="shotsAway"
class="away-value">

0

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
SCHÜSSE AUFS TOR
</div>

<div class="box-value">

<span id="targetHome"
class="home-value">

0

</span>

:

<span id="targetAway"
class="away-value">

0

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
GROSSCHANCEN
</div>

<div class="box-value">

<span id="chanceHome"
class="home-value">

0

</span>

:

<span id="chanceAway"
class="away-value">

0

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
ECKBÄLLE
</div>

<div class="box-value">

<span id="cornerHome"
class="home-value">

0

</span>

:

<span id="cornerAway"
class="away-value">

0

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
PASSQUOTE
</div>

<div class="box-value">

<span id="passHome"
class="home-value">

0%

</span>

:

<span id="passAway"
class="away-value">

0%

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
PÄSSE
</div>

<div class="box-value">

<span id="passesHome"
class="home-value">

0/0

</span>

:

<span id="passesAway"
class="away-value">

0/0

</span>

</div>

</div>





<div class="stat-box">

<div class="box-title">
GELBE KARTEN
</div>

<div class="box-value">

<span id="cardsHome"
class="home-value">

0

</span>

:

<span id="cardsAway"
class="away-value">

0

</span>

</div>

</div>



</div>







<!-- ======================
 LIVE DATEN
====================== -->


<div class="input-area">


<h2>

LIVE DATEN EINGEBEN

</h2>



<textarea id="dataInput"
placeholder="
Statistiken einfügen...

Expected Goals
Ballbesitz
Schüsse
Pässe
Karten
">

</textarea>



<button onclick="updateStats()">

AKTUALISIEREN

</button>



</div>
<script>


/* ==========================
   VEREINSFARBEN
========================== */


const teams={


"BVB":"#FDE100",
"Borussia Dortmund":"#FDE100",


"SV Werder Bremen":"#00875A",
"Werder Bremen":"#00875A",


"FC Bayern München":"#DC052D",
"Bayern München":"#DC052D",


"Bayer 04 Leverkusen":"#E32221",
"Bayer Leverkusen":"#E32221",


"RB Leipzig":"#777777",


"VfB Stuttgart":"#777777",


"Eintracht Frankfurt":"#777777",


"Borussia Mönchengladbach":"#777777",


"TSG 1899 Hoffenheim":"#005CA9",
"TSG Hoffenheim":"#005CA9",


"SC Freiburg":"#E30613",


"FC Augsburg":"#00875A",


"1. FC Köln":"#E30613",


"1. FSV Mainz 05":"#C41230",
"FSV Mainz 05":"#C41230",


"1. FC Union Berlin":"#E30613",


"FC Schalke 04":"#004C99",
"Schalke 04":"#004C99",


"Hamburger SV":"#005CA9",


"SC Paderborn 07":"#005CA9",
"SC Paderborn":"#005CA9",


"SV Elversberg":"#D4AF37"


};




let currentGame="";






/* ==========================
 SPIELTAG LADEN
========================== */


function loadMatches(){


let text=
document.getElementById("matchInput").value;



let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let list=
document.getElementById("matchList");



list.innerHTML="";



for(let i=0;i<lines.length;i++){


if(lines[i].match(/\d{2}\.\d{2}/)){



let date=lines[i];


let teamsFound=[];



for(let j=i+1;j<lines.length;j++){



if(lines[j]=="-")
break;



if(
!teamsFound.includes(lines[j])
){

teamsFound.push(lines[j]);

}



}



if(teamsFound.length>=2){



createMatch(
date,
teamsFound[0],
teamsFound[1]
);



}



}



}



saveMatchday();


}







function createMatch(date,home,away){



let card=
document.createElement("div");



card.className="match-card";



card.innerHTML=`

<div class="match-time">
${date}
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






/* ==========================
 SPIELTAG SPEICHERN
========================== */


function saveMatchday(){


let value=
document.getElementById("matchInput").value;



localStorage.setItem(
"matchday",
value
);



}







function loadMatchday(){


let data=
localStorage.getItem(
"matchday"
);



if(data){


document.getElementById("matchInput").value=data;


loadMatches();


}


}







/* ==========================
 SPIEL AUSWÄHLEN
========================== */


function setTeams(home,away){



currentGame=
home+"_"+away;



document.getElementById("homeName")
.innerHTML=home;



document.getElementById("awayName")
.innerHTML=away;




let homeColor=
teams[home] || "#00b7ff";



let awayColor=
teams[away] || "#ff4757";





document.documentElement.style
.setProperty(
"--home-color",
homeColor
);



document.documentElement.style
.setProperty(
"--away-color",
awayColor
);



}
/* ==========================
 SPIEL STATISTIK SPEICHERN
========================== */


function saveGame(){


if(!currentGame){

alert("Kein Spiel ausgewählt");

return;

}



let save={};



let ids=[

"xgHome",
"xgAway",

"posHome",
"posAway",

"shotsHome",
"shotsAway",

"targetHome",
"targetAway",

"chanceHome",
"chanceAway",

"cornerHome",
"cornerAway",

"passHome",
"passAway",

"passesHome",
"passesAway",

"cardsHome",
"cardsAway"

];



ids.forEach(id=>{


let element=
document.getElementById(id);



if(element){

save[id]=element.innerHTML;

}


});



localStorage.setItem(

"game_"+currentGame,

JSON.stringify(save)

);


}









/* ==========================
 SPIEL STATISTIK LADEN
========================== */


function loadGame(){



if(!currentGame)
return;



let data=
localStorage.getItem(
"game_"+currentGame
);



if(!data)
return;



data=JSON.parse(data);



Object.keys(data).forEach(id=>{


let element=
document.getElementById(id);



if(element){

element.innerHTML=data[id];

}


});



}









/* ==========================
 STATISTIK AUSLESEN
========================== */


function findPair(text,keyword){



let lines=
text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let index=
lines.findIndex(

x=>
x.toLowerCase()
.includes(keyword.toLowerCase())

);



if(index<0)
return [0,0];



let values=[];



for(let i=index-1;i<=index+3;i++){


if(i>=0 && i<lines.length){


let number=
lines[i]
.match(/\d+(?:[.,]\d+)?/);



if(number){


values.push(
Number(
number[0].replace(",",".")
)
);


}


}



if(values.length==2)
break;


}



return values.length==2
?
values
:
[0,0];


}









/* ==========================
 BALKEN
========================== */


function setBar(a,b,left,right){



let total=a+b;



if(total<=0)
return;



document.getElementById(left)
.style.width=
(a/total*100)+"%";



document.getElementById(right)
.style.width=
(b/total*100)+"%";


}









/* ==========================
 DATEN AKTUALISIEREN
========================== */


function updateStats(){



let text=
document.getElementById("dataInput")
.value;



if(!text.trim()){

alert("Keine Daten eingefügt");

return;

}







/* xG */


let xg=
findPair(
text,
"Expected Goals"
);



xgHome.innerHTML=
xg[0].toFixed(2);



xgAway.innerHTML=
xg[1].toFixed(2);



setBar(
xg[0],
xg[1],
"xgHomeBar",
"xgAwayBar"
);









/* Ballbesitz */


let pos=
findPair(
text,
"Ballbesitz"
);



posHome.innerHTML=
pos[0]+"%";



posAway.innerHTML=
pos[1]+"%";



posHomeBar.style.width=
pos[0]+"%";



posAwayBar.style.width=
pos[1]+"%";









/* normale Werte */


let stats=[


["Schüsse","shotsHome","shotsAway"],


["Schüsse aufs Tor","targetHome","targetAway"],


["Großchancen","chanceHome","chanceAway"],


["Ecken","cornerHome","cornerAway"],


["Gelbe Karten","cardsHome","cardsAway"]


];





stats.forEach(item=>{


let value=
findPair(
text,
item[0]
);



document.getElementById(item[1])
.innerHTML=value[0];



document.getElementById(item[2])
.innerHTML=value[1];



});






/* Pässe */


let pass=
findPair(
text,
"Pässe"
);



if(pass[0] || pass[1]){


passesHome.innerHTML=
pass[0];



passesAway.innerHTML=
pass[1];


}







/* automatisch speichern */


saveGame();



alert("Statistik gespeichert");



}







/* ==========================
 START
========================== */


window.onload=function(){


loadMatchday();


};
</script>
</div>
</div>
</body>
</html>
