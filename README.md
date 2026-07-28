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
radial-gradient(circle at top,#333,#000 70%);

color:white;

min-height:100vh;

}



.container{

width:1500px;

margin:20px auto;

padding:25px;

background:#080808;

border-radius:30px;

box-shadow:

0 40px 90px #000,

inset 0 0 40px #222;

}



.layout{

display:grid;

grid-template-columns:380px 1fr;

gap:25px;

}






/* ======================
   SPIELTAG LINKS
====================== */


.left-panel{

background:

linear-gradient(
145deg,
#222,
#080808
);


border-radius:25px;

padding:20px;


border:1px solid #444;


box-shadow:

0 25px 50px #000,

inset 0 0 25px #333;


height:950px;

overflow:auto;


}



.left-panel h2{

text-align:center;

font-size:28px;

}



#matchInput{

width:100%;

height:260px;

background:#000;

color:white;


border-radius:15px;

border:1px solid #555;


padding:15px;

font-size:15px;

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
#2b2b2b,
#111
);


border-radius:18px;


border:1px solid #555;


box-shadow:

0 15px 30px #000;


cursor:pointer;


transition:.25s;


}



.match-card:hover{


transform:

translateY(-5px)

scale(1.03);


}




.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:17px;

font-weight:bold;

margin:8px 0;

}



.match-vs{

text-align:center;

color:#777;

}







/* ======================
   RECHTS
====================== */


.right-panel{


background:

linear-gradient(
145deg,
#161616,
#050505
);


border-radius:25px;


padding:30px;


box-shadow:

0 30px 70px #000,

inset 0 0 30px #222;


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


font-size:34px;


font-weight:bold;


text-shadow:

0 8px 15px #000;


}




.score{


font-size:75px;


font-weight:bold;


text-shadow:

0 15px 30px #000;


}






button{


background:

linear-gradient(
180deg,
#555,
#111
);


color:white;


border:1px solid #777;


border-radius:14px;


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

transform:translateY(4px);

box-shadow:

0 3px 0 #000;

}


</style>

</head>


<body>


<div class="container">


<div class="layout">



<!-- ======================
     SPIELTAG
====================== -->


<div class="left-panel">


<h2>
SPIELTAG
</h2>



<textarea

id="matchInput"

placeholder="

Beispiel:

29.08. 15:30
1. FC Köln
TSG Hoffenheim
-
-

29.08. 15:30
Borussia Dortmund
Bayern München
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





<!-- ======================
     RECHTE SEITE
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
<!-- ==========================
     STATISTIK BEREICH
========================== -->


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

text-shadow:

0 0 15px var(--home-color);

}



.away-value{

color:var(--away-color);

text-shadow:

0 0 15px var(--away-color);

}



.bar{

height:28px;

width:100%;


background:#050505;


border-radius:20px;


overflow:hidden;


display:flex;


border:1px solid #444;


box-shadow:

inset 0 5px 15px #000;


}



.home-bar{

height:100%;


background:

linear-gradient(
180deg,
#ffffff88,
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
#ffffff88,
transparent
),
var(--away-color);


transition:.5s;


}





.save-area{

display:flex;

gap:15px;

margin-top:25px;

}




.save-area button{

flex:1;

}







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
#222,
#0b0b0b
);


border-radius:20px;


padding:22px;


text-align:center;


border:1px solid #444;


box-shadow:

0 15px 30px #000,

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







.input-area{


margin-top:35px;


background:

linear-gradient(
145deg,
#222,
#090909
);


border-radius:25px;


padding:25px;


border:1px solid #444;


box-shadow:

0 20px 40px #000;


}




#dataInput{


width:100%;


height:230px;


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


</style>







<!-- ==========================
     xG
========================== -->


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









<!-- ==========================
     BALLBESITZ
========================== -->


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








<!-- ==========================
     SPEICHER
========================== -->


<div class="save-area">


<button onclick="saveGame()">

💾 SPIEL SPEICHERN

</button>



<button onclick="loadGame()">

📂 SPIEL LADEN

</button>


</div>









<!-- ==========================
     BOXEN
========================== -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE

</div>


<div class="stat-number">

<span id="shotsHome" class="home-text">0</span>

:

<span id="shotsAway" class="away-text">0</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE AUFS TOR

</div>


<div class="stat-number">

<span id="targetHome" class="home-text">0</span>

:

<span id="targetAway" class="away-text">0</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

GROSSCHANCEN

</div>


<div class="stat-number">

<span id="chanceHome" class="home-text">0</span>

:

<span id="chanceAway" class="away-text">0</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

ECKEN

</div>


<div class="stat-number">

<span id="cornerHome" class="home-text">0</span>

:

<span id="cornerAway" class="away-text">0</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

PASSQUOTE

</div>


<div class="stat-number">

<span id="passHome" class="home-text">0%</span>

:

<span id="passAway" class="away-text">0%</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

PÄSSE

</div>


<div class="stat-number">

<span id="passesHome" class="home-text">0</span>

:

<span id="passesAway" class="away-text">0</span>

</div>


</div>






<div class="stat-box">

<div class="stat-title-small">

GELBE KARTEN

</div>


<div class="stat-number">

<span id="cardsHome" class="home-text">0</span>

:

<span id="cardsAway" class="away-text">0</span>

</div>


</div>



</div>









<!-- ==========================
     LIVE DATEN
========================== -->


<div class="input-area">


<h2>

LIVE DATEN EINGEBEN

</h2>




<textarea

id="dataInput"

placeholder="

Statistik einfügen:

Expected Goals
Ballbesitz
Schüsse
Schüsse aufs Tor
Großchancen
Ecken
Pässe
Karten

">

</textarea>





<button

class="update-button"

onclick="updateStats()"

>

AKTUALISIEREN

</button>


</div>
<script>


/* ==========================
   MANNSCHAFTEN FARBEN
========================== */


const teamColors={


"Borussia Dortmund":{
main:"#FDE100",
alt:"#888888"
},


"SV Werder Bremen":{
main:"#00875A",
alt:"#FFFFFF"
},


"Werder Bremen":{
main:"#00875A",
alt:"#FFFFFF"
},


"FC Bayern München":{
main:"#DC052D",
alt:"#FFFFFF"
},


"Bayern München":{
main:"#DC052D",
alt:"#FFFFFF"
},


"Bayer 04 Leverkusen":{
main:"#E32221",
alt:"#FFFFFF"
},


"Bayer Leverkusen":{
main:"#E32221",
alt:"#FFFFFF"
},


"RB Leipzig":{
main:"#DD0000",
alt:"#FFFFFF"
},


"VfB Stuttgart":{
main:"#FFFFFF",
alt:"#888888"
},


"Eintracht Frankfurt":{
main:"#C00000",
alt:"#CCCCCC"
},


"Borussia Mönchengladbach":{
main:"#00A651",
alt:"#FFFFFF"
},


"TSG 1899 Hoffenheim":{
main:"#005CA9",
alt:"#FFFFFF"
},


"TSG Hoffenheim":{
main:"#005CA9",
alt:"#FFFFFF"
},


"SC Freiburg":{
main:"#E30613",
alt:"#AAAAAA"
},


"FC Augsburg":{
main:"#00875A",
alt:"#FFFFFF"
},


"1. FC Köln":{
main:"#E30613",
alt:"#FFFFFF"
},


"FSV Mainz 05":{
main:"#C41230",
alt:"#FFFFFF"
},


"1. FSV Mainz 05":{
main:"#C41230",
alt:"#FFFFFF"
},


"1. FC Union Berlin":{
main:"#E30613",
alt:"#CCCCCC"
},


"FC Schalke 04":{
main:"#004C99",
alt:"#FFFFFF"
},


"Hamburger SV":{
main:"#005CA9",
alt:"#FFFFFF"
},


"SC Paderborn 07":{
main:"#005CA9",
alt:"#FFFFFF"
},


"SC Paderborn":{
main:"#005CA9",
alt:"#FFFFFF"
},


"SV Elversberg":{
main:"#D4AF37",
alt:"#FFFFFF"
}


};







let currentGame="";








/* ==========================
 SPIELTAG SPEICHERN
========================== */


function saveMatchday(){


localStorage.setItem(

"savedMatchday",

document.getElementById("matchInput").value

);


}





function loadMatchday(){


let data=

localStorage.getItem(
"savedMatchday"
);



if(data){


document.getElementById("matchInput").value=data;


loadMatches();


}


}







/* ==========================
 SPIELE LADEN
========================== */


function loadMatches(){


saveMatchday();



let text=

document.getElementById("matchInput").value;



let lines=

text.split("\n")
.map(x=>x.trim())
.filter(x=>x);



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



card.innerHTML=`

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



let h=

teamColors[home] || {

main:"#00b7ff",
alt:"#FFFFFF"

};



let a=

teamColors[away] || {

main:"#ff4757",
alt:"#FFFFFF"

};





if(h.main===a.main){


a.main=a.alt;


}





document.documentElement.style
.setProperty(

"--home-color",

h.main

);



document.documentElement.style
.setProperty(

"--away-color",

a.main

);



}








/* ==========================
 SPIEL SPEICHERN
========================== */


function saveGame(){


if(!currentGame)
return;



let save={};



document.querySelectorAll("[id]")
.forEach(e=>{


if(

e.id!="dataInput" &&

e.id!="matchInput" &&

e.id!="matchList"

){


save[e.id]=e.innerHTML;


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



data=JSON.parse(data);



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
 STATISTIK AUSLESEN
========================== */


function readStat(text,name){



let reg=

new RegExp(

name+"[^0-9]*([0-9]+(?:[.,][0-9]+)?)[^0-9]+([0-9]+(?:[.,][0-9]+)?)",

"i"

);



let result=text.match(reg);



if(result){


return [

Number(result[1].replace(",",".")),

Number(result[2].replace(",", "."))

];


}



return [0,0];


}







function updateStats(){



let text=

document.getElementById("dataInput").value;





let xg=

readStat(
text,
"Expected Goals"
);



xgHome.innerHTML=

xg[0].toFixed(2);



xgAway.innerHTML=

xg[1].toFixed(2);





let pos=

readStat(
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







let list=[


["Schüsse","shotsHome","shotsAway"],


["Schüsse aufs Tor","targetHome","targetAway"],


["Großchancen","chanceHome","chanceAway"],


["Ecken","cornerHome","cornerAway"],


["Gelbe Karten","cardsHome","cardsAway"]


];





list.forEach(item=>{


let value=

readStat(
text,
item[0]
);



document.getElementById(item[1])
.innerHTML=value[0];



document.getElementById(item[2])
.innerHTML=value[1];


});




saveGame();


}








window.onload=function(){


loadMatchday();


};



</script>


</div>

</div>


</body>

</html>
