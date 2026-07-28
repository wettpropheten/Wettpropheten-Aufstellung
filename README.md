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

min-height:100vh;

background:

radial-gradient(
circle at top,
#555,
#000 70%
);

color:white;

}





.container{

width:1500px;

margin:20px auto;

padding:25px;


background:

linear-gradient(
145deg,
#181818,
#050505
);


border-radius:35px;


box-shadow:

0 50px 100px #000,

inset 0 0 50px #333;


}




.layout{

display:grid;

grid-template-columns:380px 1fr;

gap:25px;


}





/* =====================
   SPIELTAG
===================== */


.left-panel{


height:950px;


padding:20px;


background:

linear-gradient(
145deg,
#292929,
#080808
);


border-radius:25px;


border:1px solid #555;


box-shadow:

0 25px 60px #000,

inset 0 0 30px #333;


overflow-y:auto;


}



.left-panel h2{


text-align:center;

font-size:30px;


}





#matchInput{


width:100%;


height:260px;


background:#000;


color:white;


border:1px solid #555;


border-radius:15px;


padding:15px;


font-size:15px;


}




button{


background:

linear-gradient(
180deg,
#666,
#111
);


color:white;


border:1px solid #777;


border-radius:15px;


padding:15px;


font-weight:bold;


cursor:pointer;


box-shadow:

0 8px 0 #000;


transition:.2s;


}



button:hover{

transform:translateY(-3px);

}




button:active{

transform:translateY(3px);

}





.load-button{

width:100%;

margin-top:15px;


}





.match-card{


margin-top:15px;


padding:18px;


background:

linear-gradient(
145deg,
#333,
#111
);


border-radius:18px;


border:1px solid #666;


box-shadow:

0 15px 35px #000;


cursor:pointer;


transition:.25s;


}




.match-card:hover{


transform:

translateY(-5px)
scale(1.03);


}




.match-time{

font-size:13px;

color:#aaa;


}




.match-team{


font-size:17px;

font-weight:bold;

margin:8px 0;


}




.match-vs{

text-align:center;

color:#888;

}







/* =====================
   RECHTE SEITE
===================== */



.right-panel{


padding:30px;


background:

linear-gradient(
145deg,
#151515,
#050505
);


border-radius:30px;


box-shadow:

0 35px 80px #000,

inset 0 0 40px #333;


}




.scoreboard{


display:flex;


justify-content:space-between;


align-items:center;


border-bottom:1px solid #444;


padding-bottom:25px;


}





.team-name{


width:40%;


text-align:center;


font-size:36px;


font-weight:bold;


text-shadow:

0 10px 25px #000;


}





.score{


font-size:80px;


font-weight:bold;


text-shadow:

0 15px 35px #000;


}




</style>


</head>


<body>



<div class="container">


<div class="layout">



<!-- SPIELTAG -->

<div class="left-panel">


<h2>

SPIELTAG

</h2>



<textarea

id="matchInput"

placeholder="

29.08. 15:30

1. FC Köln

TSG Hoffenheim

-

-

29.08. 15:30

RB Leipzig

Borussia Mönchengladbach

-

-

">

</textarea>




<button

class="load-button"

onclick="loadMatches()"

>

SPIELE LADEN

</button>




<div id="matchList">

</div>


</div>





<!-- HAUPTBEREICH -->


<div class="right-panel">



<div class="scoreboard">



<div 
id="homeName"
class="team-name">

HEIM

</div>




<div class="score">

0 : 0

</div>




<div 
id="awayName"
class="team-name">

GAST

</div>



</div>
<style>


/* =====================
   STATISTIK
===================== */


.stat{

margin-top:35px;

}




.stat-title{


text-align:center;

font-size:25px;

font-weight:bold;

margin-bottom:15px;


}




.values{


display:flex;

justify-content:space-between;


font-size:34px;

font-weight:bold;


}



.home-value{

color:var(--home-color);


text-shadow:

0 0 20px var(--home-color);


}



.away-value{

color:var(--away-color);


text-shadow:

0 0 20px var(--away-color);


}





.bar{


height:30px;


display:flex;


background:#000;


border-radius:20px;


overflow:hidden;


border:1px solid #555;


box-shadow:

inset 0 5px 15px #000;


}




.home-bar{


height:100%;


background:

linear-gradient(
180deg,
white,
transparent
),
var(--home-color);


transition:.5s;


}



.away-bar{


height:100%;


background:

linear-gradient(
180deg,
white,
transparent
),
var(--away-color);


transition:.5s;


}






/* =====================
   STATISTIK BOXEN
===================== */


.stats-grid{


display:grid;


grid-template-columns:

repeat(3,1fr);


gap:18px;


margin-top:35px;


}





.stat-box{


background:

linear-gradient(
145deg,
#292929,
#080808
);


border-radius:20px;


padding:20px;


text-align:center;


border:1px solid #555;


box-shadow:

0 20px 40px #000,

inset 0 0 20px #333;


}




.stat-title-small{


font-size:14px;


color:#aaa;


}




.stat-number{


font-size:34px;


font-weight:bold;


margin-top:12px;


}




.home-text{

color:var(--home-color);

}



.away-text{

color:var(--away-color);

}






/* =====================
   DATEN
===================== */


.input-area{


margin-top:35px;


padding:25px;


background:

linear-gradient(
145deg,
#222,
#080808
);


border-radius:25px;


border:1px solid #555;


box-shadow:

0 25px 50px #000;


}




#dataInput{


width:100%;


height:260px;


background:#000;


color:white;


border-radius:15px;


border:1px solid #555;


padding:15px;


font-size:16px;


}




.update-button{


width:100%;


margin-top:15px;


}





/* =====================
 SPEICHER UNTEN
===================== */


.save-area{


display:flex;


gap:15px;


margin-top:30px;


}



.save-area button{


flex:1;


}


</style>







<!-- =====================
   xG
===================== -->


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









<!-- =====================
   BALLBESITZ
===================== -->


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









<!-- =====================
 STATISTIK KARTEN
===================== -->


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

ECKEN

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

PÄSSE

</div>


<div class="stat-number">


<span id="passesHome"
class="home-text">

0

</span>


:


<span id="passesAway"
class="away-text">

0

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








<!-- =====================
 LIVE EINGABE
===================== -->


<div class="input-area">


<h2>

LIVE DATEN EINGEBEN

</h2>



<textarea

id="dataInput"

placeholder="

Hier die Live-Statistik einfügen:

1.24
Expected Goals (xG)
0.80

50%
Ballbesitz
50%

10
Schüsse insgesamt
12

3
Schüsse aufs Tor
5

2
Großchance
3

3
Eckbälle
4

86%
(454/526)
Pässe
89%
(464/524)

0
Gelbe Karten
1

">

</textarea>




<button

class="update-button"

onclick="updateStats()"

>

AKTUALISIEREN

</button>


</div>








<div class="save-area">


<button onclick="saveGame()">

💾 SPIEL SPEICHERN

</button>


<button onclick="loadGame()">

📂 SPIEL LADEN

</button>


</div>
<script>


/* ==========================
 TEAM FARBEN
========================== */


const teamColors={


"1. FC Köln":{
main:"#E30613",
alt:"#FFFFFF"
},


"TSG Hoffenheim":{
main:"#005CA9",
alt:"#FFFFFF"
},


"1. FC Union Berlin":{
main:"#E30613",
alt:"#FFFFFF"
},


"Eintracht Frankfurt":{
main:"#C00000",
alt:"#FFFFFF"
},


"FSV Mainz 05":{
main:"#C41230",
alt:"#FFFFFF"
},


"SC Paderborn":{
main:"#005CA9",
alt:"#FFFFFF"
},


"RB Leipzig":{
main:"#DD0000",
alt:"#FFFFFF"
},


"Borussia Mönchengladbach":{
main:"#008F39",
alt:"#FFFFFF"
},


"SV Elversberg":{
main:"#D4AF37",
alt:"#111111"
},


"Bayer Leverkusen":{
main:"#E32221",
alt:"#FFFFFF"
}


};



let currentGame="";








/* ==========================
 SPIELTAG SPEICHERN
========================== */


function saveMatchday(){


localStorage.setItem(

"saved_matchday",

document.getElementById("matchInput").value

);


}







function loadMatchday(){


let data=

localStorage.getItem(
"saved_matchday"
);



if(data){


document.getElementById("matchInput").value=data;


loadMatches();


}


}








/* ==========================
 SPIELTAG LADEN
========================== */


function loadMatches(){


saveMatchday();



let lines=

document.getElementById("matchInput")
.value
.split("\n")
.map(x=>x.trim())
.filter(Boolean);



let list=

document.getElementById("matchList");


list.innerHTML="";




for(let i=0;i<lines.length;i++){


if(lines[i].match(/\d{2}\.\d{2}/)){



let time=lines[i];

let clubs=[];



for(let j=i+1;j<lines.length;j++){


if(lines[j]=="-")
break;



if(!clubs.includes(lines[j])){


clubs.push(lines[j]);


}


}



if(clubs.length>=2){


createMatch(

time,

clubs[0],

clubs[1]

);


}


}


}


}










function createMatch(time,home,away){


let card=document.createElement("div");


card.className="match-card";



card.innerHTML=

`

<div class="match-time">

${time}

</div>


<div class="match-team">

${home}

</div>


<div class="match-vs">

VS

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
 TEAMS SETZEN
========================== */


function setTeams(home,away){



currentGame=

home+"_"+away;



homeName.innerHTML=home;

awayName.innerHTML=away;




let homeTeam=

teamColors[home] ||

{
main:"#00b7ff",
alt:"#FFFFFF"
};



let awayTeam=

teamColors[away] ||

{
main:"#ff4757",
alt:"#FFFFFF"
};





/* gleiche Farbe vermeiden */


if(homeTeam.main===awayTeam.main){


awayTeam.main=awayTeam.alt;


}





document.documentElement
.style
.setProperty(

"--home-color",

homeTeam.main

);




document.documentElement
.style
.setProperty(

"--away-color",

awayTeam.main

);



}










/* ==========================
 STATISTIK PARSER
========================== */


function getLines(){


return document
.getElementById("dataInput")
.value
.split("\n")
.map(x=>x.trim())
.filter(Boolean);


}







function numberFrom(text){


let n=

parseFloat(

text
.replace("%","")
.replace(",", ".")

);



return isNaN(n)
?

null

:

n;


}








function findStat(title){



let lines=getLines();



let index=

lines.findIndex(

x=>

x.toLowerCase()
.includes(
title.toLowerCase()
)

);




if(index===-1)

return [0,0];





let before=null;


if(index>0){


let n=

numberFrom(
lines[index-1]
);


if(n!==null)

before=n;


}





let after=[];



for(
let i=index+1;

i<lines.length;

i++

){



let n=

numberFrom(
lines[i]
);



if(n!==null){


after.push(n);


}



if(after.length===2)

break;



if(
n===null &&
after.length>0
)

break;


}






/* Titel mit Wert davor */


if(
title
.includes("Expected")
){


return [

before ?? 0,

after[0] ?? 0

];

}





return [

after[0] ?? 0,

after[1] ?? 0

];



}






/* Pässe extra */


function findPasses(){


let text=

document
.getElementById("dataInput")
.value;



let values=

text.match(
(/\(\d+\/\d+\)/g)
);



if(
values &&
values.length>=2
){



return [

parseInt(
values[0]
.match(/\d+/)[0]
),


parseInt(
values[1]
.match(/\d+/)[0]
)

];


}



return [0,0];


}
 
/* ==========================
   STATISTIK AKTUALISIEREN
========================== */


function updateStats(){



/* xG */


let xg=

findStat(
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


let possession=

findStat(
"Ballbesitz"
);



posHome.innerHTML=

possession[0]+"%";


posAway.innerHTML=

possession[1]+"%";



posHomeBar.style.width=

possession[0]+"%";


posAwayBar.style.width=

possession[1]+"%";







/* normale Werte */


let stats=[


["Schüsse insgesamt",
"shotsHome",
"shotsAway"],


["Schüsse",
"shotsHome",
"shotsAway"],



["Schüsse aufs Tor",
"targetHome",
"targetAway"],



["Großchance",
"chanceHome",
"chanceAway"],



["Großchancen",
"chanceHome",
"chanceAway"],



["Eckbälle",
"cornerHome",
"cornerAway"],



["Ecken",
"cornerHome",
"cornerAway"],



["Gelbe Karten",
"cardsHome",
"cardsAway"]


];





stats.forEach(item=>{


let value=

findStat(item[0]);



document
.getElementById(item[1])
.innerHTML=value[0];



document
.getElementById(item[2])
.innerHTML=value[1];



});







/* Pässe */


let passes=

findPasses();



passesHome.innerHTML=

passes[0];


passesAway.innerHTML=

passes[1];






saveGame();



}










/* ==========================
   BALKEN
========================== */


function setBar(home,away,left,right){



let total=

home+away;



if(total<=0)

return;



document
.getElementById(left)
.style.width=

(home/total*100)+"%";




document
.getElementById(right)
.style.width=

(away/total*100)+"%";


}









/* ==========================
   SPIEL SPEICHERN
========================== */


function saveGame(){



if(!currentGame)

return;




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
   SPIEL LADEN
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





data=

JSON.parse(data);





Object.keys(data)
.forEach(id=>{



let element=

document.getElementById(id);



if(element){


element.innerHTML=data[id];


}



});




}








/* ==========================
 START
========================== */


window.onload=function(){


loadMatchday();


};


 
/* ==========================
   AUTOMATISCH SPIELTAG LADEN
========================== */


document.addEventListener(
"DOMContentLoaded",
function(){


loadMatchday();



}
);





</script>


</div>


</div>


</body>


</html>
