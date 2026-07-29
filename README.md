<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro 3D V2</title>


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

radial-gradient(circle at top,#444,#000 75%);

color:white;

min-height:100vh;

}




.container{

width:1500px;

margin:20px auto;

padding:25px;

background:

linear-gradient(145deg,#1d1d1d,#050505);

border-radius:35px;

box-shadow:

0 40px 100px #000,

inset 0 0 40px #333;

}




.layout{

display:grid;

grid-template-columns:380px 1fr;

gap:25px;

}





/* ======================
SPIELTAG
====================== */


.left-panel{

background:

linear-gradient(145deg,#252525,#080808);

border-radius:25px;

padding:20px;

height:950px;

overflow:auto;

border:1px solid #555;

box-shadow:

0 25px 50px #000,

inset 0 0 25px #333;

}




h2{

text-align:center;

}





#matchInput{

width:100%;

height:250px;

background:#000;

color:white;

border-radius:15px;

border:1px solid #555;

padding:15px;

resize:none;

}





button{

width:100%;

padding:15px;

margin-top:15px;

background:

linear-gradient(180deg,#666,#111);

color:white;

border:1px solid #777;

border-radius:15px;

font-weight:bold;

cursor:pointer;

box-shadow:

0 8px 0 #000;

}



button:hover{

transform:translateY(-3px);

}





.match-card{

margin-top:15px;

padding:18px;

background:

linear-gradient(145deg,#333,#111);

border-radius:18px;

border:1px solid #555;

box-shadow:

0 15px 30px #000;

cursor:pointer;

transition:.2s;

}



.match-card:hover{

transform:

translateY(-5px);

}





.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:18px;

font-weight:bold;

margin:8px 0;

}


.match-vs{

text-align:center;

color:#888;

}







/* ======================
HAUPTBEREICH
====================== */


.right-panel{

background:

linear-gradient(145deg,#181818,#050505);

border-radius:25px;

padding:30px;

box-shadow:

0 30px 70px #000,

inset 0 0 30px #333;

}





.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

padding:30px;

border-radius:25px;

background:

linear-gradient(

90deg,

#ffffff10,

transparent,

#ffffff10

);

box-shadow:

inset 0 0 30px #333,

0 20px 50px #000;

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

text-align:center;

text-shadow:

0 15px 35px #000;

}



</style>

</head>

<body>


<div class="container">


<div class="layout">


<div class="left-panel">


<h2>

SPIELTAG

</h2>


<textarea id="matchInput"

placeholder="

29.08. 15:30

1. FC Köln

TSG Hoffenheim

-

-

">

</textarea>


<button id="loadMatches">

SPIELE LADEN

</button>


<div id="matchList"></div>


</div>



<div class="right-panel">


<div class="scoreboard">


<div id="homeName"

class="team-name">

HEIM

</div>



<div class="score">

0 : 0

</div>




<div id="awayName"

class="team-name">

GAST

</div>


</div>

<!-- ==========================
     SPIELDATEN TABELLE
========================== -->


<div class="match-table-area">


<h2>

SPIELDATEN

</h2>



<table class="match-table">


<thead>

<tr>

<th>

STATISTIK

</th>

<th>

HEIM

</th>

<th>

GAST

</th>

</tr>

</thead>



<tbody>


<tr>
<td>Expected Goals (xG)</td>
<td id="tableXgHome">0.00</td>
<td id="tableXgAway">0.00</td>
</tr>


<tr>
<td>Ballbesitz</td>
<td id="tablePossHome">50%</td>
<td id="tablePossAway">50%</td>
</tr>


<tr>
<td>Schüsse</td>
<td id="tableShotsHome">0</td>
<td id="tableShotsAway">0</td>
</tr>


<tr>
<td>Schüsse aufs Tor</td>
<td id="tableTargetHome">0</td>
<td id="tableTargetAway">0</td>
</tr>


<tr>
<td>Großchancen</td>
<td id="tableChanceHome">0</td>
<td id="tableChanceAway">0</td>
</tr>


<tr>
<td>Ecken</td>
<td id="tableCornerHome">0</td>
<td id="tableCornerAway">0</td>
</tr>


<tr>
<td>Passquote</td>
<td id="tablePassRateHome">0%</td>
<td id="tablePassRateAway">0%</td>
</tr>


<tr>
<td>Pässe</td>
<td id="tablePassHome">0/0</td>
<td id="tablePassAway">0/0</td>
</tr>


<tr>
<td>Gelbe Karten</td>
<td id="tableCardHome">0</td>
<td id="tableCardAway">0</td>
</tr>


</tbody>

</table>


</div>









<!-- ==========================
     STATISTIK KÄSTCHEN
========================== -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-title">

Expected Goals (xG)

</div>

<div class="stat-value">

<span id="boxXgHome">0.00</span>

:

<span id="boxXgAway">0.00</span>

</div>

</div>






<div class="stat-box">

<div class="stat-title">

Ballbesitz

</div>

<div class="stat-value">

<span id="boxPossHome">50%</span>

:

<span id="boxPossAway">50%</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

SCHÜSSE

</div>

<div class="stat-value">

<span id="boxShotsHome">0</span>

:

<span id="boxShotsAway">0</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

SCHÜSSE AUFS TOR

</div>

<div class="stat-value">

<span id="boxTargetHome">0</span>

:

<span id="boxTargetAway">0</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

GROSSCHANCEN

</div>

<div class="stat-value">

<span id="boxChanceHome">0</span>

:

<span id="boxChanceAway">0</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

ECKEN

</div>

<div class="stat-value">

<span id="boxCornerHome">0</span>

:

<span id="boxCornerAway">0</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

PÄSSE

</div>

<div class="stat-value">

<span id="boxPassHome">0/0</span>

:

<span id="boxPassAway">0/0</span>

</div>

</div>







<div class="stat-box">

<div class="stat-title">

GELBE KARTEN

</div>

<div class="stat-value">

<span id="boxCardHome">0</span>

:

<span id="boxCardAway">0</span>

</div>

</div>




</div>









<!-- ==========================
     LIVE EINGABE
========================== -->


<div class="live-area">


<h2>

LIVE DATEN EINGEBEN

</h2>




<textarea id="liveInput"

placeholder="

Beispiel:

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




<button id="importData">

DATEN ÜBERNEHMEN

</button>



<div class="save-buttons">


<button id="saveGame">

💾 SPIEL SPEICHERN

</button>


<button id="loadGame">

📂 SPIEL LADEN

</button>


</div>



</div>









<style>


/* ==========================
   TABELLE
========================== */


.match-table-area{

margin-top:35px;

background:

linear-gradient(145deg,#222,#080808);

border-radius:25px;

padding:25px;

border:1px solid #555;

box-shadow:

0 25px 50px #000,

inset 0 0 25px #333;

}



.match-table{

width:100%;

border-collapse:collapse;

font-size:18px;

}



.match-table th{

padding:15px;

background:#111;

}



.match-table td{

padding:14px;

text-align:center;

border-bottom:1px solid #444;

}



.match-table td:first-child{

text-align:left;

color:#aaa;

}




.match-table td:nth-child(2){

color:var(--home-color);

font-weight:bold;

}



.match-table td:nth-child(3){

color:var(--away-color);

font-weight:bold;

}









/* ==========================
   KÄSTCHEN
========================== */


.stats-grid{

display:grid;

grid-template-columns:repeat(4,1fr);

gap:20px;

margin-top:35px;

}



.stat-box{

background:

linear-gradient(145deg,#252525,#090909);

border-radius:20px;

padding:25px;

text-align:center;

border:1px solid #555;

box-shadow:

0 15px 35px #000,

inset 0 0 20px #333;

transition:.2s;

}



.stat-box:hover{

transform:translateY(-5px);

}



.stat-title{

font-size:14px;

color:#aaa;

}



.stat-value{

font-size:32px;

font-weight:bold;

margin-top:12px;

}









/* ==========================
LIVE INPUT
========================== */


.live-area{

margin-top:35px;

background:

linear-gradient(145deg,#222,#080808);

border-radius:25px;

padding:25px;

}



#liveInput{

width:100%;

height:250px;

background:#000;

color:white;

border-radius:15px;

padding:15px;

font-size:16px;

}



.save-buttons{

display:flex;

gap:15px;

}


.save-buttons button{

flex:1;

}



</style>

<script>


/* =====================================
   LiveStats Pro 3D V2.0
   DATENMODELL
===================================== */


const database = {


games:{}


};



let currentGame = null;



let currentHome = "";

let currentAway = "";







/* =====================================
   STANDARD STATISTIK
===================================== */


function createEmptyStats(){


return {


xg:{

home:0,

away:0

},



possession:{

home:50,

away:50

},



shots:{

home:0,

away:0

},



target:{

home:0,

away:0

},



chances:{

home:0,

away:0

},



corners:{

home:0,

away:0

},



passes:{

homeComplete:0,

homeTotal:0,

awayComplete:0,

awayTotal:0

},



passRate:{

home:0,

away:0

},



cards:{

home:0,

away:0

}



};



}









/* =====================================
   SPIELTAG LADEN
===================================== */


document

.getElementById("loadMatches")

.onclick=function(){


loadMatchday();



};








function loadMatchday(){



let text =

document

.getElementById("matchInput")

.value;



let lines = text

.split("\n")

.map(x=>x.trim())

.filter(x=>x);



let container =

document

.getElementById("matchList");



container.innerHTML="";





for(let i=0;i<lines.length;i++){



if(

/\d{2}\.\d{2}/.test(lines[i])

){



let time = lines[i];



let teams=[];




for(

let j=i+1;

j<lines.length;

j++

){



if(lines[j]==="-")

break;



if(

lines[j] &&

!teams.includes(lines[j])

){


teams.push(lines[j]);


}


}





if(teams.length>=2){



addMatch(

time,

teams[0],

teams[1]

);



}



}



}



}









/* =====================================
   SPIELKARTE ERZEUGEN
===================================== */


function addMatch(time,home,away){



let div =

document.createElement("div");



div.className="match-card";



div.innerHTML=`

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





div.onclick=function(){


openGame(

home,

away

);



};




document

.getElementById("matchList")

.appendChild(div);



}









/* =====================================
   SPIEL ÖFFNEN
===================================== */


function openGame(home,away){



currentHome=home;

currentAway=away;



currentGame=

home+"_"+away;





if(!database.games[currentGame]){


database.games[currentGame]={


home:home,

away:away,

stats:createEmptyStats()


};



}





document

.getElementById("homeName")

.innerHTML=

home;



document

.getElementById("awayName")

.innerHTML=

away;





updateColors();



updateAll();



}









/* =====================================
   FARBEN
===================================== */


const colors={


"1. FC Köln":"#E30613",

"TSG Hoffenheim":"#005CA9",

"1. FC Union Berlin":"#E30613",

"Eintracht Frankfurt":"#C00000",

"FSV Mainz 05":"#C41230",

"SC Paderborn":"#005CA9",

"RB Leipzig":"#DD0000",

"Borussia Mönchengladbach":"#00A651",

"SV Elversberg":"#D4AF37",

"Bayer Leverkusen":"#E32221"


};







function updateColors(){



let homeColor=

colors[currentHome]

||

"#00b7ff";



let awayColor=

colors[currentAway]

||

"#ff4757";





document.documentElement

.style

.setProperty(

"--home-color",

homeColor

);



document.documentElement

.style

.setProperty(

"--away-color",

awayColor

);



}



/* =====================================
   HILFSFUNKTIONEN
===================================== */


function activeStats(){


if(!currentGame)

return null;



return database.games[currentGame].stats;


}







function numbersFrom(text){



return (

text

.match(/\d+(?:[.,]\d+)?/g)

||

[]

)

.map(

x=>

Number(

x.replace(",", ".")

)

);



}








/* =====================================
   PASSQUOTE BERECHNEN
===================================== */


function calculatePassRate(){


let s=activeStats();



if(!s)

return;




s.passRate.home =

s.passes.homeTotal

?

Math.round(

s.passes.homeComplete /

s.passes.homeTotal *

100

)

:

0;



s.passRate.away =

s.passes.awayTotal

?

Math.round(

s.passes.awayComplete /

s.passes.awayTotal *

100

)

:

0;



}








/* =====================================
   DATEN IMPORT
===================================== */


document

.getElementById("importData")

.onclick=function(){



importLiveData();



};









function importLiveData(){



if(!currentGame){


alert("Bitte zuerst ein Spiel auswählen");

return;


}



let text=

document

.getElementById("liveInput")

.value;



let lines=

text

.split("\n")

.map(x=>x.trim())

.filter(x=>x);




let stats=activeStats();







/* xG */


let xgIndex=

lines.findIndex(

x=>

x.includes("Expected Goals")

);



if(xgIndex>=0){



let a=

numbersFrom(

lines[xgIndex-1]

);



let b=

numbersFrom(

lines[xgIndex+1]

);



stats.xg.home=

a[0] || 0;



stats.xg.away=

b[0] || 0;


}










/* Ballbesitz */


let posIndex=

lines.findIndex(

x=>

x.toLowerCase()

.includes("ballbesitz")

);



if(posIndex>=0){


stats.possession.home=

numbersFrom(

lines[posIndex-1]

)[0]

||0;



stats.possession.away=

numbersFrom(

lines[posIndex+1]

)[0]

||0;


}









/* Schüsse */


readPair(

lines,

"Schüsse insgesamt",

stats.shots

);






/* Schüsse aufs Tor */


readPair(

lines,

"Schüsse aufs Tor",

stats.target

);






/* Großchancen */


readPair(

lines,

"Großchance",

stats.chances

);






/* Ecken */


readPair(

lines,

"Eckbälle",

stats.corners

);







/* Karten */


readPair(

lines,

"Gelbe Karten",

stats.cards

);









/* Pässe */




let passMatch=

text.match(

/(\d+)\/(\d+)/g

);



if(passMatch && passMatch.length>=2){



let home=

passMatch[0].split("/");

let away=

passMatch[1].split("/");



stats.passes.homeComplete=

Number(home[0]);



stats.passes.homeTotal=

Number(home[1]);



stats.passes.awayComplete=

Number(away[0]);



stats.passes.awayTotal=

Number(away[1]);



}







calculatePassRate();



updateAll();



}





/* =====================================
   PAARWERTE LESEN
===================================== */


function readPair(lines,title,target){



let index=

lines.findIndex(

x=>

x.toLowerCase()

.includes(

title.toLowerCase()

)

);



if(index<0)

return;



target.home=

numbersFrom(

lines[index-1]

)[0]

||0;



target.away=

numbersFrom(

lines[index+1]

)[0]

||0;



}









/* =====================================
   ALLES AKTUALISIEREN
===================================== */


function updateAll(){



let s=activeStats();



if(!s)

return;





/* Tabelle */


tableXgHome.innerHTML=

s.xg.home.toFixed(2);



tableXgAway.innerHTML=

s.xg.away.toFixed(2);




tablePossHome.innerHTML=

s.possession.home+"%";



tablePossAway.innerHTML=

s.possession.away+"%";




tableShotsHome.innerHTML=

s.shots.home;



tableShotsAway.innerHTML=

s.shots.away;





tableTargetHome.innerHTML=

s.target.home;



tableTargetAway.innerHTML=

s.target.away;





tableChanceHome.innerHTML=

s.chances.home;



tableChanceAway.innerHTML=

s.chances.away;





tableCornerHome.innerHTML=

s.corners.home;



tableCornerAway.innerHTML=

s.corners.away;





tablePassRateHome.innerHTML=

s.passRate.home+"%";



tablePassRateAway.innerHTML=

s.passRate.away+"%";





tablePassHome.innerHTML=

s.passes.homeComplete+

"/"+

s.passes.homeTotal;



tablePassAway.innerHTML=

s.passes.awayComplete+

"/"+

s.passes.awayTotal;





tableCardHome.innerHTML=

s.cards.home;



tableCardAway.innerHTML=

s.cards.away;










/* Kästchen */


boxXgHome.innerHTML=

s.xg.home.toFixed(2);



boxXgAway.innerHTML=

s.xg.away.toFixed(2);



boxPossHome.innerHTML=

s.possession.home+"%";



boxPossAway.innerHTML=

s.possession.away+"%";



boxShotsHome.innerHTML=

s.shots.home;



boxShotsAway.innerHTML=

s.shots.away;



boxTargetHome.innerHTML=

s.target.home;



boxTargetAway.innerHTML=

s.target.away;



boxChanceHome.innerHTML=

s.chances.home;



boxChanceAway.innerHTML=

s.chances.away;



boxCornerHome.innerHTML=

s.corners.home;



boxCornerAway.innerHTML=

s.corners.away;



boxPassHome.innerHTML=

s.passes.homeComplete+

"/"+

s.passes.homeTotal;



boxPassAway.innerHTML=

s.passes.awayComplete+

"/"+

s.passes.awayTotal;



boxCardHome.innerHTML=

s.cards.home;



boxCardAway.innerHTML=

s.cards.away;



}


/* =====================================
   SPEICHERN
===================================== */


document

.getElementById("saveGame")

.onclick=function(){



if(!currentGame)

return;



localStorage.setItem(

"LiveStats_"+currentGame,

JSON.stringify(

database.games[currentGame]

)

);



alert("Spiel gespeichert");



};









/* =====================================
   LADEN
===================================== */


document

.getElementById("loadGame")

.onclick=function(){



if(!currentGame)

return;



let saved=

localStorage.getItem(

"LiveStats_"+currentGame

);



if(saved){



database.games[currentGame]

=

JSON.parse(saved);



updateAll();



alert("Spiel geladen");



}



};









/* =====================================
   AUTOMATISCHES LADEN
===================================== */


window.onload=function(){



let oldMatchday=

localStorage.getItem(

"LiveStats_matchday"

);



if(oldMatchday){



document

.getElementById("matchInput")

.value=

oldMatchday;



}



};









/* =====================================
   SPIELTAG SPEICHERN
===================================== */


const oldLoadMatchday=

loadMatchday;



loadMatchday=function(){



oldLoadMatchday();



localStorage.setItem(

"LiveStats_matchday",

document

.getElementById("matchInput")

.value

);



};









/* =====================================
   TESTDATEN BUTTON (OPTIONAL)
===================================== */


function loadTestData(){



document

.getElementById("liveInput")

.value=`

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

1


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

`;



}






</script>



</div>

</div>


</body>

</html>
