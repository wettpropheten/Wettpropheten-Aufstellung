<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro 2.0 3D</title>


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

radial-gradient(
circle at top,
#444,
#000 65%
);

color:white;

min-height:100vh;

}



.container{

width:1500px;

margin:20px auto;

padding:25px;


background:

linear-gradient(
145deg,
#151515,
#050505
);


border-radius:30px;


box-shadow:

0 40px 100px #000,

inset 0 0 40px #333;


}



.layout{

display:grid;

grid-template-columns:360px 1fr;

gap:25px;


}





/* SPIELTAG */


.left-panel{


height:950px;


background:

linear-gradient(
145deg,
#252525,
#090909
);


border-radius:25px;


padding:20px;


border:1px solid #555;


box-shadow:

0 25px 50px #000,

inset 0 0 25px #333;


overflow:auto;


}



.left-panel h2{

text-align:center;

font-size:28px;

}




#matchInput{


width:100%;


height:250px;


background:#000;


color:white;


border-radius:15px;


border:1px solid #555;


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


border-radius:14px;


padding:14px;


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

0 15px 30px #000;


cursor:pointer;


}



.match-card:hover{


transform:

scale(1.03);


}




.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:17px;

font-weight:bold;

margin:7px 0;

}




.match-vs{

text-align:center;

color:#888;

}







/* RECHTS */


.right-panel{


background:

linear-gradient(
145deg,
#181818,
#050505
);


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


padding-bottom:25px;


border-bottom:1px solid #444;


}




.team-name{


width:40%;


text-align:center;


font-size:34px;


font-weight:bold;


text-shadow:

0 10px 20px #000;


}



.score{


font-size:75px;


font-weight:bold;


text-shadow:

0 15px 30px #000;


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





<div class="right-panel">



<div class="scoreboard">



<div 
class="team-name"
id="homeName">

HEIM

</div>




<div class="score">

0 : 0

</div>




<div 
class="team-name"
id="awayName">

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

0 0 20px var(--home-color);

}



.away-value{

color:var(--away-color);

text-shadow:

0 0 20px var(--away-color);

}






.bar{


height:28px;


width:100%;


background:#050505;


border-radius:20px;


overflow:hidden;


display:flex;


border:1px solid #555;


box-shadow:

inset 0 5px 15px #000;


}



.home-bar{


height:100%;


background:

linear-gradient(
180deg,
#fff8,
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
#fff8,
transparent
),
var(--away-color);


transition:.5s;


}





/* KARTEN */


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
#090909
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


margin-top:10px;


}




.home-text{

color:var(--home-color);

}



.away-text{

color:var(--away-color);

}





/* DATEN */


.input-area{


margin-top:35px;


background:

linear-gradient(
145deg,
#222,
#080808
);


border-radius:25px;


padding:25px;


border:1px solid #555;


box-shadow:

0 25px 50px #000;


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



/* SPEICHER UNTEN */


.bottom-save{


display:flex;


gap:15px;


margin-top:35px;


}



.bottom-save button{


flex:1;


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


<span 
id="xgHome"
class="home-value">

0.00

</span>



<span 
id="xgAway"
class="away-value">

0.00

</span>


</div>



<div class="bar">


<div

id="xgHomeBar"

class="home-bar"

style="width:50%">

</div>



<div

id="xgAwayBar"

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


<span

id="posHome"

class="home-value">

50%

</span>



<span

id="posAway"

class="away-value">

50%

</span>



</div>



<div class="bar">


<div

id="posHomeBar"

class="home-bar"

style="width:50%">

</div>



<div

id="posAwayBar"

class="away-bar"

style="width:50%">

</div>


</div>


</div>









<!-- ==========================
 STATISTIK KARTEN
========================== -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE

</div>


<div class="stat-number">

<span id="shotsHome" class="home-text">

0

</span>


:


<span id="shotsAway" class="away-text">

0

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

SCHÜSSE AUFS TOR

</div>


<div class="stat-number">

<span id="targetHome" class="home-text">

0

</span>


:


<span id="targetAway" class="away-text">

0

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

GROSSCHANCEN

</div>


<div class="stat-number">

<span id="chanceHome" class="home-text">

0

</span>


:


<span id="chanceAway" class="away-text">

0

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

ECKEN

</div>


<div class="stat-number">

<span id="cornerHome" class="home-text">

0

</span>


:


<span id="cornerAway" class="away-text">

0

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

PASSQUOTE

</div>


<div class="stat-number">

<span id="passHome" class="home-text">

0%

</span>


:


<span id="passAway" class="away-text">

0%

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

PÄSSE

</div>


<div class="stat-number">

<span id="passesHome" class="home-text">

0

</span>


:


<span id="passesAway" class="away-text">

0

</span>


</div>

</div>






<div class="stat-box">

<div class="stat-title-small">

GELBE KARTEN

</div>


<div class="stat-number">

<span id="cardsHome" class="home-text">

0

</span>


:


<span id="cardsAway" class="away-text">

0

</span>


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

Top-Statistiken einfügen:

Expected Goals
1.24
0.80

Ballbesitz
50
50

Schüsse
12
3

Schüsse aufs Tor
5
1

Großchancen
2
0

Ecken
3
4

Pässe
454
464

Gelbe Karten
0
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








<!-- ==========================
 SPEICHERN GANZ UNTEN
========================== -->


<div class="bottom-save">


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


const teams={


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
main:"#000000",
alt:"#E10000"
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
alt:"#111111"
}


};





let currentGame="";





/* ==========================
 SPIELTAG SPEICHERN
========================== */


function saveMatchday(){


localStorage.setItem(

"matchday",

document.getElementById("matchInput").value

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
 SPIELTAG PARSER
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

let teamsFound=[];



for(let j=i+1;j<lines.length;j++){


if(lines[j]=="-")
break;



if(!teamsFound.includes(lines[j])){


teamsFound.push(lines[j]);


}


}



if(teamsFound.length>=2){


createMatch(

time,

teamsFound[0],

teamsFound[1]

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



matchList.appendChild(card);


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

teams[home] ||

{
main:"#00b7ff",
alt:"#FFFFFF"
};



let a=

teams[away] ||

{
main:"#ff4757",
alt:"#FFFFFF"
};




/* gleiche Farbe verhindern */


if(h.main===a.main){


a.main=a.alt;


}





document.documentElement
.style
.setProperty(

"--home-color",

h.main

);



document.documentElement
.style
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



let data={};



document.querySelectorAll("[id]")
.forEach(el=>{


if(

el.id!="dataInput"

&&

el.id!="matchInput"

&&

el.id!="matchList"

){


data[el.id]=el.innerHTML;


}


});



localStorage.setItem(

"game_"+currentGame,

JSON.stringify(data)

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


let el=

document.getElementById(id);



if(el){


el.innerHTML=data[id];


}


});


}









/* ==========================
 NEUER STATISTIK LESER
========================== */


function getStat(name){


let text=

document
.getElementById("dataInput")
.value;



let lines=

text
.split("\n")
.map(x=>x.trim())
.filter(Boolean);



let index=

lines.findIndex(

x=>

x.toLowerCase()
.includes(name.toLowerCase())

);



if(index===-1)

return [0,0];





let values=[];



for(
let i=index+1;

i<lines.length;

i++

){


if(

lines[i]
.match(/[a-zA-ZäöüÄÖÜ]/)

)

break;



let number=

parseFloat(

lines[i]
.replace(",", ".")

);



if(!isNaN(number)){


values.push(number);


}



if(values.length===2)

break;


}



return values.length===2

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



document
.getElementById(left)
.style.width=

(a/total*100)+"%";



document
.getElementById(right)
.style.width=

(b/total*100)+"%";


}









/* ==========================
 UPDATE
========================== */


function updateStats(){



let xg=getStat("Expected Goals");



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






let pos=getStat("Ballbesitz");



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


["Ecken","cornerHome","cornerAway"],


["Gelbe Karten","cardsHome","cardsAway"]


];





stats.forEach(s=>{


let value=getStat(s[0]);



document
.getElementById(s[1])
.innerHTML=value[0];



document
.getElementById(s[2])
.innerHTML=value[1];


});






let passes=getStat("Pässe");



passesHome.innerHTML=

passes[0];


passesAway.innerHTML=

passes[1];




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
