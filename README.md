<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro</title>


<style>


*{

box-sizing:border-box;

font-family:Arial, Helvetica, sans-serif;

}



body{

margin:0;

background:
linear-gradient(135deg,#061326,#12345f);

color:white;

min-height:100vh;

}



.container{

width:95%;

max-width:1100px;

margin:auto;

padding:30px 0;

}



/* HEADER */


.header{

text-align:center;

margin-bottom:30px;

}



.header h1{

font-size:42px;

margin:0;

}



.header p{

opacity:.8;

font-size:18px;

}





/* IMPORT */


.import-panel{

background:#0d2347;

padding:25px;

border-radius:18px;

box-shadow:0 10px 30px rgba(0,0,0,.5);

margin-bottom:30px;

}



textarea{

width:100%;

height:260px;

background:#071529;

color:white;

border:none;

border-radius:12px;

padding:15px;

font-size:15px;

}



button{

width:100%;

margin-top:15px;

padding:15px;

border:none;

border-radius:12px;

background:#2196f3;

color:white;

font-size:18px;

font-weight:bold;

cursor:pointer;

}



button:hover{

background:#42a5f5;

}



.reset{

background:#e53935;

}






/* SPIEL */


.match-card{

background:#0d2347;

padding:25px;

border-radius:18px;

margin-bottom:30px;

}



.teams{

display:flex;

justify-content:space-between;

align-items:center;

text-align:center;

}



.team{

width:40%;

}



.team h2{

font-size:25px;

}



.score{

font-size:60px;

font-weight:bold;

}



.vs{

font-size:22px;

opacity:.7;

}





/* STATISTIK */


.stats-box{

background:#0d2347;

padding:25px;

border-radius:18px;

margin-bottom:30px;

}



.stat{

margin-bottom:30px;

}



.stat-header{

display:flex;

justify-content:space-between;

font-size:18px;

font-weight:bold;

margin-bottom:10px;

}



.home-number{

color:#42a5f5;

}



.away-number{

color:#ff867f;

}



.bar{

height:22px;

background:#1b304e;

border-radius:20px;

overflow:hidden;

display:flex;

}



.home-bar{

height:100%;

width:50%;

background:#2196f3;

transition:1s;

}



.away-bar{

height:100%;

width:50%;

background:#ff5252;

transition:1s;

}





/* KARTEN */


.cards{

display:grid;

grid-template-columns:repeat(auto-fit,minmax(180px,1fr));

gap:15px;

}



.card{

background:#0d2347;

padding:20px;

border-radius:15px;

text-align:center;

}



.card h3{

opacity:.8;

font-size:15px;

}



.card span{

font-size:30px;

font-weight:bold;

}





.obs-button{

background:#8e24aa;

}



</style>

</head>



<body>


<div class="container">


<div class="header">


<h1>
⚽ LiveStats Pro
</h1>


<p>
Automatische Fußball Statistik Analyse
</p>


</div>





<div class="import-panel">


<h2>
📋 Statistik einfügen
</h2>



<textarea id="rawStats"

placeholder="Sofascore / FotMob Statistik hier einfügen">


</textarea>




<button onclick="readStats()">

📊 Statistik auslesen

</button>



<button class="reset">

🔄 Zurücksetzen

</button>


</div>






<div class="match-card">


<div class="teams">


<div class="team">


<h2 id="homeTeam">

Heimteam

</h2>


<div class="score" id="homeScore">

0

</div>


</div>




<div class="vs">

VS

</div>




<div class="team">


<h2 id="awayTeam">

Auswärtsteam

</h2>


<div class="score" id="awayScore">

0

</div>


</div>


</div>


</div>






<div class="stats-box">


<h2>
📊 Live Statistik
</h2>




<div class="stat">


<div class="stat-header">

<span>
Expected Goals (xG)
</span>


<span id="xgValue">

0.00 - 0.00

</span>


</div>



<div class="bar">


<div class="home-bar" id="xgHomeBar"></div>


<div class="away-bar" id="xgAwayBar"></div>


</div>


</div>





<div class="stat">


<div class="stat-header">

<span>
Ballbesitz
</span>


<span id="posValue">

0% - 0%

</span>


</div>



<div class="bar">


<div class="home-bar" id="posHomeBar"></div>


<div class="away-bar" id="posAwayBar"></div>


</div>


</div>


</div>






<div class="cards">


<div class="card">

<h3>
Schüsse
</h3>

<span id="shots">

0 - 0

</span>


</div>




<div class="card">

<h3>
Torschüsse
</h3>

<span id="target">

0 - 0

</span>


</div>




<div class="card">

<h3>
Großchancen
</h3>

<span id="big">

0 - 0

</span>


</div>




<div class="card">

<h3>
Ecken
</h3>

<span id="corner">

0 - 0

</span>


</div>




<div class="card">

<h3>
Gelbe Karten
</h3>

<span id="yellow">

0 - 0

</span>


</div>


</div>



<button class="obs-button">

📺 OBS Modus

</button>


<script>


// ==========================
// DATENSPEICHER
// ==========================


const stats = {};




// ==========================
// WERTE BEREINIGEN
// ==========================


function clean(value){

if(!value){

return "";

}


return value
.replace(",",".")
.replace("%","")
.trim();

}






// ==========================
// STATISTIK AUSLESEN
// ==========================


function readStats(){


let text =
document
.getElementById("rawStats")
.value;



let lines =
text
.split(/\r?\n/)
.map(line=>line.trim())
.filter(line=>line !== "");





lines.forEach(function(line,index){



switch(line){



case "Expected Goals (xG)":



stats.xgHome =
clean(lines[index-1]);



stats.xgAway =
clean(lines[index+1]);



break;







case "Ballbesitz":



stats.posHome =
clean(lines[index-1]);



stats.posAway =
clean(lines[index+1]);



break;







case "Schüsse insgesamt":



stats.shotsHome =
clean(lines[index-1]);



stats.shotsAway =
clean(lines[index+1]);



break;







case "Schüsse aufs Tor":



stats.targetHome =
clean(lines[index-1]);



stats.targetAway =
clean(lines[index+1]);



break;







case "Großchance":



stats.bigHome =
clean(lines[index-1]);



stats.bigAway =
clean(lines[index+1]);



break;







case "Eckbälle":



stats.cornerHome =
clean(lines[index-1]);



stats.cornerAway =
clean(lines[index+1]);



break;







case "Gelbe Karten":



stats.yellowHome =
clean(lines[index-1]);



stats.yellowAway =
clean(lines[index+1]);



break;



}



});



updateDisplay();


}









// ==========================
// ANZEIGE AKTUALISIEREN
// ==========================


function updateDisplay(){



// xG


if(stats.xgHome){



document
.getElementById("xgValue")
.innerHTML =


'<span class="home-number">'
+
stats.xgHome
+
'</span> - <span class="away-number">'
+
stats.xgAway
+
'</span>';



updateBar(

"xgHomeBar",

"xgAwayBar",

parseFloat(stats.xgHome),

parseFloat(stats.xgAway)

);



}







// Ballbesitz


if(stats.posHome){



document
.getElementById("posValue")
.innerHTML =


'<span class="home-number">'
+
stats.posHome
+
'%</span> - <span class="away-number">'
+
stats.posAway
+
'%</span>';




document
.getElementById("posHomeBar")
.style.width =
stats.posHome+"%";



document
.getElementById("posAwayBar")
.style.width =
stats.posAway+"%";



}








// Karten


updateCard(

"shots",

stats.shotsHome,

stats.shotsAway

);



updateCard(

"target",

stats.targetHome,

stats.targetAway

);



updateCard(

"big",

stats.bigHome,

stats.bigAway

);



updateCard(

"corner",

stats.cornerHome,

stats.cornerAway

);



updateCard(

"yellow",

stats.yellowHome,

stats.yellowAway

);



}








// ==========================
// KARTEN AKTUALISIEREN
// ==========================


function updateCard(id,home,away){


if(home !== undefined){


document
.getElementById(id)
.innerHTML =

home
+
" - "
+
away;


}



}








// ==========================
// BALKEN BERECHNEN
// ==========================


function updateBar(homeID,awayID,home,away){



let total =
home + away;



if(total <= 0){

return;

}



let homePercent =
(home / total) * 100;



let awayPercent =
(away / total) * 100;



document
.getElementById(homeID)
.style.width =
homePercent+"%";



document
.getElementById(awayID)
.style.width =
awayPercent+"%";



}



</script>
<script>


// ==========================
// SPEICHERN
// ==========================


function saveStats(){


localStorage.setItem(

"LiveStatsPro",

JSON.stringify(stats)

);


}







// ==========================
// LADEN
// ==========================


function loadStats(){



let saved =

localStorage.getItem(

"LiveStatsPro"

);



if(saved){


Object.assign(

stats,

JSON.parse(saved)

);



updateDisplay();


}



}







// ==========================
// RESET
// ==========================


document
.querySelector(".reset")
.onclick=function(){



localStorage.removeItem(

"LiveStatsPro"

);



location.reload();



};








// ==========================
// OBS MODUS
// ==========================


document
.querySelector(".obs-button")
.onclick=function(){



document
.body
.classList
.toggle("obs");



};








// ==========================
// OBS DESIGN
// ==========================


let obsStyle = document.createElement("style");


obsStyle.innerHTML = `


.obs{


background:#000;

}



.obs .import-panel{

display:none;

}



.obs .obs-button{

display:none;

}



.obs .container{

max-width:1200px;

}



`;



document
.head
.appendChild(obsStyle);








// ==========================
// AUTOMATISCH STARTEN
// ==========================


window.onload=function(){


loadStats();


};



</script>
<script>


// ==========================
// ANIMATIONEN
// ==========================


function animateValue(id){


let element =
document.getElementById(id);



if(element){


element.style.transform="scale(1.1)";


setTimeout(function(){


element.style.transform="scale(1)";


},200);


}



}







[
"shots",
"target",
"big",
"corner",
"yellow",
"xgValue",
"posValue"

].forEach(function(id){


let element =
document.getElementById(id);



if(element){



element.style.transition="0.2s";



}



});








// ==========================
// TEST IMPORT
// ==========================


// Beispiel:
// 
// 1.24
// Expected Goals (xG)
// 0.80
//
// 50%
// Ballbesitz
// 50%
//
// 10
// Schüsse insgesamt
// 12
//
// 3
// Schüsse aufs Tor
// 5
//
// 1
// Großchance
// 2
//
// 3
// Eckbälle
// 4
//
// 0
// Gelbe Karten
// 1



</script>



</div>


</body>


</html>
