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

border-radius:20px;

padding:20px;

}



.layout{

display:grid;

grid-template-columns:360px 1fr;

gap:20px;

}





/* =====================
LINKER SPIELTAG
===================== */


.left-panel{

background:#0b0b0b;

border:1px solid #333;

border-radius:15px;

padding:15px;

height:950px;

overflow:auto;

}



.left-panel h2{

text-align:center;

}



#matchInput{

width:100%;

height:230px;

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

padding:12px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-weight:bold;

cursor:pointer;

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



.team{

font-size:16px;

font-weight:bold;

margin:5px;

}



.vs{

text-align:center;

color:#777;

}






/* =====================
RECHTE STATISTIK
===================== */


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


/* =====================
   STATISTIK BEREICH
===================== */


.stat{

margin-top:35px;

}



.stat-title{

text-align:center;

font-size:22px;

font-weight:bold;

margin-bottom:10px;

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

height:20px;

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






/* =====================
   STATISTIK KÄSTCHEN
===================== */


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







/* =====================
   DATEN EINGABE
===================== */


.input-area{

margin-top:35px;

background:#0b0b0b;

border:1px solid #333;

border-radius:15px;

padding:20px;

}



#dataInput{

width:100%;

height:230px;

background:#000;

color:white;

border:1px solid #444;

border-radius:10px;

padding:15px;

font-size:16px;

}



.update-button{

width:100%;

margin-top:10px;

padding:15px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-size:18px;

font-weight:bold;

cursor:pointer;

}


</style>





<!-- =====================
   HTML START
===================== -->


<div class="container">


<div class="layout">



<!-- LINKER BEREICH -->


<div class="left-panel">


<h2>
SPIELTAG
</h2>


<textarea 
id="matchInput"
placeholder="Spieltag hier einfügen...">
</textarea>


<button 
class="load-button"
onclick="loadMatches()">

SPIELE LADEN

</button>


<div id="matchList">

</div>


</div>







<!-- RECHTER BEREICH -->


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








<!-- xG -->


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

<!-- =====================
 STATISTIK KÄSTCHEN
===================== -->


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



</div>

</div>






<script>


/* =====================
 MANNSCHAFTSFARBEN
===================== */


const teams={


"1. FC Union Berlin":"#e30613",
"Eintracht Frankfurt":"#777777",
"Bayern München":"#dc052d",
"Bayer Leverkusen":"#e32221",
"Werder Bremen":"#00875a",
"SV Werder Bremen":"#00875a",
"Schalke 04":"#004c99",
"HSV":"#005ca9",
"Hamburger SV":"#005ca9",
"Borussia Dortmund":"#fde100",
"Borussia Mönchengladbach":"#777777",
"TSG Hoffenheim":"#005ca9",
"1. FC Köln":"#777777",
"FSV Mainz 05":"#c41230",
"SC Freiburg":"#e30613",
"FC Augsburg":"#ba3733",
"SC Paderborn":"#005ca9",
"VfB Stuttgart":"#777777",
"SV Elversberg":"#444444",
"RB Leipzig":"#777777"

};







/* =====================
 SPIELE LADEN
===================== */


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



let teams=[];


/* nächste 6 Zeilen prüfen */

for(let j=i+1;j<i+7 && j<lines.length;j++){


if(
lines[j]!=="-" &&
!lines[j].match(/\d{2}\.\d{2}\./)
){

if(
teams.length===0 ||
teams[teams.length-1]!==lines[j]
){

teams.push(lines[j]);

}

}


}



let home=teams[0];

let away=teams[1];



if(home && away){



let card=document.createElement("div");

card.className="match-card";



card.innerHTML=`

<div class="match-time">
${time}
</div>

<div class="team">
${home}
</div>

<div class="vs">
-
</div>

<div class="team">
${away}
</div>

`;



card.onclick=function(){

setTeams(home,away);

};



list.appendChild(card);


}



}



}



}







/* =====================
 FARBEN SETZEN
===================== */


function setTeams(home,away){



document.getElementById("homeName").innerHTML=home;

document.getElementById("awayName").innerHTML=away;



let hc=teams[home] || "#00b7ff";

let ac=teams[away] || "#ff4757";



if(hc===ac){

ac="#777777";

}



document.documentElement.style
.setProperty("--home-color",hc);



document.documentElement.style
.setProperty("--away-color",ac);



}







/* =====================
 ZAHLEN FINDEN
===================== */


function findNumbers(text,name){


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



let numbers=[];



for(let i=index-1;i>=0;i--){


let m=lines[i].match(/\d+([.,]\d+)?/);


if(m){

numbers.unshift(
Number(m[0].replace(",","."))
);

break;

}


}



for(let i=index+1;i<lines.length;i++){


let m=lines[i].match(/\d+([.,]\d+)?/);


if(m){

numbers.push(
Number(m[0].replace(",","."))
);

break;

}


}



return numbers.length===2 ? numbers:[0,0];

}





function set(id,value){

document.getElementById(id).innerHTML=value;

}





function updateStats(){



let text=document
.getElementById("dataInput")
.value;



let xg=findNumbers(text,"Expected Goals");



set("xgHome",xg[0].toFixed(2));

set("xgAway",xg[1].toFixed(2));



let pos=findNumbers(text,"Ballbesitz");



set("posHome",pos[0]+"%");

set("posAway",pos[1]+"%");



document.getElementById("posHomeBar").style.width=pos[0]+"%";

document.getElementById("posAwayBar").style.width=pos[1]+"%";



let stats=[

["Schüsse","shotsHome","shotsAway"],

["Schüsse aufs Tor","targetHome","targetAway"],

["Großchance","chanceHome","chanceAway"],

["Eckbälle","cornerHome","cornerAway"],

["Gelbe Karten","cardsHome","cardsAway"]

];



stats.forEach(s=>{


let v=findNumbers(text,s[0]);


set(s[1],v[0]);

set(s[2],v[1]);


});



localStorage.setItem(
"liveStats",
text
);


}





</script>


</body>

</html>
