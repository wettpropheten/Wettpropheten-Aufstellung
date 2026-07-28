<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro</title>


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
background:#000;
color:white;

}



.container{

width:1500px;
margin:20px auto;
background:#050505;
padding:20px;
border-radius:20px;

}



.layout{

display:grid;
grid-template-columns:360px 1fr;
gap:20px;

}







/* ======================
   SPIELTAG LINKS
====================== */


.left-panel{

background:#0b0b0b;
border:1px solid #333;
border-radius:15px;
padding:15px;
height:950px;
overflow-y:auto;

}



.left-panel h2{

text-align:center;

}



#matchInput{

width:100%;
height:260px;

background:#000;
color:white;

border:1px solid #444;
border-radius:10px;

padding:12px;

font-size:15px;

}



.load-button{

width:100%;

margin-top:10px;

padding:14px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-weight:bold;

cursor:pointer;

}



.load-button:hover{

background:#333;

}





.match-card{

background:#111;

border:1px solid #333;

border-radius:10px;

padding:12px;

margin-top:10px;

cursor:pointer;

}



.match-card:hover{

background:#222;

}



.match-time{

font-size:13px;

color:#aaa;

}



.match-team{

font-size:16px;

font-weight:bold;

margin:5px 0;

}



.match-vs{

text-align:center;

color:#777;

}







/* ======================
   RECHTS STATISTIK
====================== */


.right-panel{

background:#050505;

border-radius:15px;

padding:25px;

}



.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

border-bottom:1px solid #333;

padding-bottom:20px;

}



.team-name{

width:40%;

text-align:center;

font-size:30px;

font-weight:bold;

}



.score{

font-size:65px;

font-weight:bold;

}

<style>


/* ======================
   STATISTIK BEREICH
====================== */


.stat{

margin-top:35px;

}



.stat-title{

text-align:center;

font-size:22px;

font-weight:bold;

margin-bottom:12px;

}



.values{

display:flex;

justify-content:space-between;

font-size:28px;

font-weight:bold;

}



.home-value{

color:var(--home-color);

}



.away-value{

color:var(--away-color);

}



.bar{

height:22px;

width:100%;

background:#111;

border:1px solid #333;

border-radius:20px;

overflow:hidden;

display:flex;

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
   BUTTONS
====================== */


.save-area{

display:flex;

gap:10px;

margin-top:20px;

}



.action-button{

flex:1;

padding:14px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-weight:bold;

cursor:pointer;

}



.action-button:hover{

background:#333;

}







/* ======================
   STATISTIK BOXEN
====================== */


.stats-grid{

display:grid;

grid-template-columns:repeat(3,1fr);

gap:15px;

margin-top:35px;

}



.stat-box{

background:#111;

border:1px solid #333;

border-radius:12px;

padding:18px;

text-align:center;

}



.stat-box-title{

font-size:14px;

color:#aaa;

}



.stat-number{

font-size:30px;

font-weight:bold;

margin-top:10px;

}



.home-text{

color:var(--home-color);

}



.away-text{

color:var(--away-color);

}







/* ======================
   DATENEINGABE
====================== */


.input-area{

margin-top:35px;

background:#0b0b0b;

border:1px solid #333;

border-radius:15px;

padding:20px;

}



#dataInput{

width:100%;

height:220px;

background:#000;

color:white;

border:1px solid #444;

border-radius:10px;

padding:15px;

font-size:16px;

}



.update-button{

width:100%;

margin-top:12px;

padding:15px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-weight:bold;

font-size:18px;

cursor:pointer;

}


</style>





<!-- ======================
     SPIEL ANZEIGE
====================== -->


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


<span id="xgHome" class="home-value">
0.00
</span>


<span id="xgAway" class="away-value">
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


<span id="posHome" class="home-value">
50%
</span>


<span id="posAway" class="away-value">
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







<!-- SPEICHER BUTTONS -->


<div class="save-area">


<button 
class="action-button"
onclick="saveCurrentGame()">

SPIEL SPEICHERN

</button>



<button
class="action-button"
onclick="deleteCurrentGame()">

SPIEL LÖSCHEN

</button>


</div>









<!-- STATISTIK BOXEN -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-box-title">
SCHÜSSE
</div>


<div class="stat-number">

<span id="shotsHome" class="home-text">0</span>

:

<span id="shotsAway" class="away-text">0</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
SCHÜSSE AUFS TOR
</div>


<div class="stat-number">

<span id="targetHome" class="home-text">0</span>

:

<span id="targetAway" class="away-text">0</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
GROSSCHANCEN
</div>


<div class="stat-number">

<span id="chanceHome" class="home-text">0</span>

:

<span id="chanceAway" class="away-text">0</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
ECKBÄLLE
</div>


<div class="stat-number">

<span id="cornerHome" class="home-text">0</span>

:

<span id="cornerAway" class="away-text">0</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
PASSQUOTE
</div>


<div class="stat-number">

<span id="passHome" class="home-text">0%</span>

:

<span id="passAway" class="away-text">0%</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
PÄSSE GESAMT
</div>


<div class="stat-number">

<span id="passesHome" class="home-text">0/0</span>

:

<span id="passesAway" class="away-text">0/0</span>

</div>

</div>





<div class="stat-box">

<div class="stat-box-title">
GELBE KARTEN
</div>


<div class="stat-number">

<span id="cardsHome" class="home-text">0</span>

:

<span id="cardsAway" class="away-text">0</span>

</div>

</div>



</div>







<!-- DATEN EINGABE -->


<div class="input-area">


<h2>
LIVE DATEN EINFÜGEN
</h2>



<textarea
id="dataInput"
placeholder="Statistik hier einfügen...">
</textarea>



<button
class="update-button"
onclick="updateStats()">

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


"SVW":"#00875A",
"SV Werder Bremen":"#00875A",
"Werder Bremen":"#00875A",


"FCB":"#DC052D",
"FC Bayern München":"#DC052D",
"Bayern München":"#DC052D",


"B04":"#E32221",
"Bayer 04 Leverkusen":"#E32221",
"Bayer Leverkusen":"#E32221",


"RBL":"#FFFFFF",
"RB Leipzig":"#FFFFFF",


"VFB":"#FFFFFF",
"VfB Stuttgart":"#FFFFFF",


"SGE":"#777777",
"Eintracht Frankfurt":"#777777",


"BMG":"#FFFFFF",
"Borussia Mönchengladbach":"#FFFFFF",


"TSG":"#005CA9",
"TSG 1899 Hoffenheim":"#005CA9",
"TSG Hoffenheim":"#005CA9",


"SCF":"#E30613",
"SC Freiburg":"#E30613",


"FCA":"#00875A",
"FC Augsburg":"#00875A",


"FCK":"#E30613",
"1. FC Köln":"#E30613",


"M05":"#C41230",
"1. FSV Mainz 05":"#C41230",
"FSV Mainz 05":"#C41230",


"FCU":"#E30613",
"1. FC Union Berlin":"#E30613",


"S04":"#004C99",
"FC Schalke 04":"#004C99",
"Schalke 04":"#004C99",


"HSV":"#005CA9",
"Hamburger SV":"#005CA9",


"SCP":"#005CA9",
"SC Paderborn 07":"#005CA9",
"SC Paderborn":"#005CA9",


"SVE":"#D4AF37",
"SV Elversberg":"#D4AF37"


};







let currentGame="";






/* ==========================
   SPIELE LADEN
========================== */


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


if(lines[i].match(/\d{2}\.\d{2}\./)){


let time=lines[i];


let names=[];



for(
let j=i+1;
j<lines.length && names.length<2;
j++
){


if(
lines[j] !== "-" &&
!lines[j].match(/\d{2}\.\d{2}\./)
){


if(
names.length===0 ||
names[names.length-1]!==lines[j]
){

names.push(lines[j]);

}


}


}




if(names.length===2){


let home=names[0];

let away=names[1];



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

loadCurrentGame();

};



list.appendChild(card);


}



}


}


}








/* ==========================
   SPIEL SETZEN
========================== */


function setTeams(home,away){



currentGame=home+"_"+away;



document
.getElementById("homeName")
.innerHTML=home;



document
.getElementById("awayName")
.innerHTML=away;





let homeColor=
teams[home] || "#00b7ff";


let awayColor=
teams[away] || "#ff4757";





if(homeColor===awayColor){

homeColor="#777777";

awayColor="#777777";

}





document.documentElement
.style.setProperty(
"--home-color",
homeColor
);



document.documentElement
.style.setProperty(
"--away-color",
awayColor
);



}








/* ==========================
   SPEICHERN
========================== */


function saveCurrentGame(){


if(!currentGame){

alert("Kein Spiel ausgewählt");

return;

}



let data={


xgHome:xgHome.innerHTML,
xgAway:xgAway.innerHTML,


posHome:posHome.innerHTML,
posAway:posAway.innerHTML,


shotsHome:shotsHome.innerHTML,
shotsAway:shotsAway.innerHTML,


targetHome:targetHome.innerHTML,
targetAway:targetAway.innerHTML,


chanceHome:chanceHome.innerHTML,
chanceAway:chanceAway.innerHTML,


cornerHome:cornerHome.innerHTML,
cornerAway:cornerAway.innerHTML,


passHome:passHome.innerHTML,
passAway:passAway.innerHTML,


passesHome:passesHome.innerHTML,
passesAway:passesAway.innerHTML,


cardsHome:cardsHome.innerHTML,
cardsAway:cardsAway.innerHTML


};



localStorage.setItem(
"match_"+currentGame,
JSON.stringify(data)
);



alert("Spiel gespeichert");

}





/* ==========================
   LADEN
========================== */


function loadCurrentGame(){


let data=
localStorage.getItem(
"match_"+currentGame
);



if(!data){

return;

}



data=JSON.parse(data);



Object.keys(data).forEach(id=>{


if(document.getElementById(id)){


document.getElementById(id)
.innerHTML=data[id];


}


});



}






/* ==========================
   LÖSCHEN
========================== */


function deleteCurrentGame(){


if(!currentGame)
return;



localStorage.removeItem(
"match_"+currentGame
);



alert("Spiel gelöscht");


}







/* ==========================
   STATISTIK UPDATE
========================== */


function updateStats(){


let text=document
.getElementById("dataInput")
.value;



function numbers(name){


let r=text.match(
new RegExp(
"(\\d+)\\s*"+name+"\\s*(\\d+)",
"i"
)
);



return r ? [r[1],r[2]]:[0,0];

}



let xg=numbers("xG");


xgHome.innerHTML=xg[0];

xgAway.innerHTML=xg[1];



let pos=numbers("%");


posHome.innerHTML=pos[0]+"%";

posAway.innerHTML=pos[1]+"%";



posHomeBar.style.width=pos[0]+"%";

posAwayBar.style.width=pos[1]+"%";



}






</script>


</div>

</div>


</body>

</html>
