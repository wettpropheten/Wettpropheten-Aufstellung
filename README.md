<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro 2.0</title>


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
radial-gradient(circle at top,#202020,#000 60%);

color:white;

min-height:100vh;

}




.container{

width:1500px;

margin:20px auto;

padding:25px;

background:#080808;

border-radius:25px;

box-shadow:

0 30px 80px #000,

inset 0 0 30px #111;

}




.layout{

display:grid;

grid-template-columns:380px 1fr;

gap:25px;

}







/* ==========================
   3D SPIELTAG
========================== */


.left-panel{


background:#111;

border-radius:20px;

padding:18px;


border:1px solid #333;


box-shadow:

0 15px 30px #000,

inset 0 0 20px #222;


}



h2{

text-align:center;

}



#matchInput{


width:100%;

height:250px;


background:#050505;

color:white;


border-radius:15px;

border:1px solid #444;


padding:15px;


font-size:15px;


}




button{


background:#222;

color:white;


border:1px solid #555;


border-radius:12px;


padding:14px;


font-weight:bold;


cursor:pointer;


box-shadow:

0 6px 0 #000;


transition:.2s;


}



button:hover{


transform:translateY(-2px);


background:#333;


}



button:active{


transform:translateY(4px);


box-shadow:

0 2px 0 #000;


}





.load-button{


width:100%;

margin-top:15px;


}







.match-card{


margin-top:15px;


padding:15px;


background:#171717;


border-radius:15px;


border:1px solid #333;


cursor:pointer;


box-shadow:


0 10px 20px #000;


transition:.25s;


}



.match-card:hover{


transform:

translateY(-5px)

scale(1.02);


background:#222;


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


background:#050505;


border-radius:20px;


padding:30px;


box-shadow:


inset 0 0 30px #111;


}




.scoreboard{


display:flex;

align-items:center;

justify-content:space-between;


padding-bottom:25px;


border-bottom:1px solid #333;


}



.team-name{


width:40%;


text-align:center;


font-size:32px;


font-weight:bold;


text-shadow:

0 5px 10px #000;


}




.score{


font-size:70px;

font-weight:bold;


text-shadow:

0 10px 20px #000;


}







/* ==========================
   3D STATISTIK BEREICH
========================== */


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


height:25px;


background:#111;


border-radius:20px;


overflow:hidden;


display:flex;


border:1px solid #333;


box-shadow:


inset 0 5px 10px #000;


}



.home-bar{


height:100%;


background:

linear-gradient(
180deg,
#fff5,
transparent
),
var(--home-color);


}



.away-bar{


height:100%;


background:

linear-gradient(
180deg,
#fff5,
transparent
),
var(--away-color);


}







/* ==========================
   BOXEN
========================== */


.stats-grid{


display:grid;


grid-template-columns:repeat(3,1fr);


gap:15px;


margin-top:35px;


}



.stat-box{


background:#111;


border-radius:15px;


padding:20px;


text-align:center;


border:1px solid #333;


box-shadow:


0 10px 25px #000,


inset 0 0 15px #222;


}



.stat-title-small{


color:#aaa;

font-size:13px;


}



.stat-number{


font-size:32px;


font-weight:bold;


margin-top:12px;


}



.home-text{

color:var(--home-color);

}



.away-text{

color:var(--away-color);

}
<style>


/* ==========================
   EINGABE BEREICH
========================== */


.input-area{


margin-top:35px;


background:#111;


padding:20px;


border-radius:20px;


border:1px solid #333;


box-shadow:


0 15px 30px #000,


inset 0 0 20px #222;


}




#dataInput{


width:100%;


height:230px;


background:#050505;


color:white;


border-radius:15px;


border:1px solid #444;


padding:15px;


font-size:16px;


}




.update-button{


width:100%;


margin-top:15px;


}







/* ==========================
   SPEICHER BUTTONS
========================== */


.save-area{


display:flex;


gap:15px;


margin-top:25px;


}



.save-area button{


flex:1;


}






</style>









<!-- ==========================
     RECHTE ANZEIGE WEITER
========================== -->




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








<!-- SPEICHERN -->


<div class="save-area">


<button onclick="saveGame()">

SPIEL SPEICHERN

</button>



<button onclick="loadGame()">

SPIEL LADEN

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








<!-- LIVE DATEN -->


<div class="input-area">


<h2>

LIVE DATEN EINFÜGEN

</h2>



<textarea

id="dataInput"

placeholder="

Statistik hier einfügen:

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
   VEREINSFARBEN SYSTEM
========================== */


const teams={


"Borussia Dortmund":{
main:"#FDE100",
alt:"#000000"
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
alt:"#777777"
},


"Eintracht Frankfurt":{
main:"#C00000",
alt:"#AAAAAA"
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
alt:"#FFFFFF"
},


"FC Augsburg":{
main:"#00875A",
alt:"#FFFFFF"
},


"1. FC Köln":{
main:"#E30613",
alt:"#FFFFFF"
},


"1. FSV Mainz 05":{
main:"#C41230",
alt:"#FFFFFF"
},


"FSV Mainz 05":{
main:"#C41230",
alt:"#FFFFFF"
},


"1. FC Union Berlin":{
main:"#E30613",
alt:"#AAAAAA"
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


let data=
document.getElementById("matchInput").value;


localStorage.setItem(
"matchday",
data
);


}






function loadMatchday(){


let data=
localStorage.getItem("matchday");


if(data){


document.getElementById("matchInput").value=data;


loadMatches();


}


}








/* ==========================
 SPIELE LADEN
========================== */


function loadMatches(){


let text=
document.getElementById("matchInput").value;



saveMatchday();



let lines=
text.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let list=
document.getElementById("matchList");


list.innerHTML="";



for(let i=0;i<lines.length;i++){


if(lines[i].match(/\d{2}\.\d{2}/)){



let date=lines[i];


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
date,
clubs[0],
clubs[1]
);


}


}


}



}







function createMatch(date,home,away){



let card=document.createElement("div");


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
 TEAM SETZEN
========================== */


function setTeams(home,away){



currentGame=
home+"_"+away;



homeName.innerHTML=home;


awayName.innerHTML=away;



let h=
teams[home] || {
main:"#00b7ff"
};



let a=
teams[away] || {
main:"#ff4757"
};





if(h.main===a.main){


a.main=a.alt;


}



document.documentElement
.style.setProperty(
"--home-color",
h.main
);



document.documentElement
.style.setProperty(
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
e.id!="matchInput"
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


let e=
document.getElementById(id);



if(e){

e.innerHTML=data[id];

}


});



}









/* ==========================
 STATISTIK
========================== */


function findValues(text,key){


let lines=
text.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let index=
lines.findIndex(

x=>x.toLowerCase()
.includes(key.toLowerCase())

);



if(index<0)
return [0,0];



let nums=[];



for(let i=Math.max(0,index-2);
i<Math.min(lines.length,index+4);
i++){



let m=
lines[i].match(/\d+(?:[.,]\d+)?/);



if(m){

nums.push(
Number(
m[0].replace(",",".")
)
);

}


}



return nums.length>=2
?
[
nums[0],
nums[1]
]
:
[0,0];



}







function updateStats(){



let text=
dataInput.value;





let xg=
findValues(text,"Expected Goals");



xgHome.innerHTML=
xg[0].toFixed(2);


xgAway.innerHTML=
xg[1].toFixed(2);





let pos=
findValues(text,"Ballbesitz");


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



list.forEach(s=>{


let v=
findValues(text,s[0]);



document.getElementById(s[1])
.innerHTML=v[0];



document.getElementById(s[2])
.innerHTML=v[1];


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
