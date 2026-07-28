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
#444,
#000 75%
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


background:

linear-gradient(
145deg,
#252525,
#080808
);


border-radius:25px;


padding:20px;


border:1px solid #555;


box-shadow:

0 30px 60px #000,

inset 0 0 30px #333;


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


border:1px solid #666;


border-radius:15px;


padding:15px;


font-size:16px;


}







button{


width:100%;


margin-top:15px;


padding:15px;


border-radius:15px;


background:

linear-gradient(
180deg,
#666,
#111
);


color:white;


border:1px solid #888;


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

font-size:18px;

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

inset 0 0 35px #333;


}





.scoreboard{


display:flex;


justify-content:space-between;


align-items:center;


padding-bottom:30px;


border-bottom:1px solid #444;


}




.team-name{


width:40%;


text-align:center;


font-size:38px;


font-weight:bold;


text-shadow:

0 10px 25px #000;


}




.score{


font-size:85px;


font-weight:bold;


text-shadow:

0 15px 30px #000;


}




</style>


</head>



<body>



<div class="container">



<div class="layout">



<!-- =====================
     SPIELTAG LINKS
===================== -->


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




<button onclick="loadMatches()">

SPIELE LADEN

</button>




<div id="matchList">

</div>



</div>







<!-- =====================
     HAUPTBEREICH
===================== -->


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



<!-- TEIL 2 KOMMT HIER -->


</div>



</div>



</div>
<style>


/* =====================
   TOP STATISTIK
===================== */


.top-stat{


margin-top:35px;


}




.stat-title{


text-align:center;


font-size:25px;


font-weight:bold;


margin-bottom:15px;


}





.stat-values{


display:flex;


justify-content:space-between;


font-size:38px;


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






.stat-bar{


height:30px;


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
#ffffff88,
transparent
),
var(--home-color);


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


}







/* =====================
   3D STAT BOXEN
===================== */



.stats-grid{


display:grid;


grid-template-columns:

repeat(3,1fr);


gap:20px;


margin-top:40px;


}





.stat-box{


background:

linear-gradient(
145deg,
#333,
#0b0b0b
);


border-radius:22px;


padding:25px;


text-align:center;


border:1px solid #555;


box-shadow:

0 20px 40px #000,

inset 0 0 20px #444;


}





.box-title{


color:#aaa;


font-size:15px;


}





.box-value{


font-size:36px;


font-weight:bold;


margin-top:15px;


}






</style>









<!-- =====================
     EXPECTED GOALS
===================== -->


<div class="top-stat">


<div class="stat-title">

Expected Goals (xG)

</div>




<div class="stat-values">


<span id="xgHome"

class="home-value">

0.00

</span>




<span id="xgAway"

class="away-value">

0.00

</span>


</div>




<div class="stat-bar">


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


<div class="top-stat">


<div class="stat-title">

Ballbesitz

</div>



<div class="stat-values">


<span id="posHome"

class="home-value">

50%

</span>



<span id="posAway"

class="away-value">

50%

</span>


</div>




<div class="stat-bar">


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

ECKEN

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


<span id="passRateHome"

class="home-value">

0%

</span>


:


<span id="passRateAway"

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

<style>


/* =====================
   LIVE EINGABE
===================== */


.input-box{


margin-top:40px;


background:

linear-gradient(
145deg,
#252525,
#090909
);


border-radius:25px;


padding:25px;


border:1px solid #555;


box-shadow:

0 25px 50px #000;


}



.input-box h2{


text-align:center;


}



#dataInput{


width:100%;


height:260px;


background:#000;


color:white;


border-radius:15px;


border:1px solid #666;


padding:15px;


font-size:16px;


resize:none;


}




.import-button{


margin-top:15px;


}




/* =====================
   SPEICHER BUTTONS
===================== */


.save-area{


display:flex;


gap:20px;


margin-top:25px;


}




.save-area button{


flex:1;


}






/* =====================
   VERSTECKTE DATENBANK
===================== */


#dataStore{


display:none;


}




</style>








<!-- =====================
     LIVE DATEN
===================== -->


<div class="input-box">


<h2>

LIVE DATEN EINGEBEN

</h2>



<textarea

id="dataInput"

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

">


</textarea>




<button

class="import-button"

onclick="importData()"

>

DATEN ÜBERNEHMEN

</button>



</div>








<!-- =====================
     SPEICHERN
===================== -->


<div class="save-area">


<button onclick="saveGame()">

💾 SPIEL SPEICHERN

</button>



<button onclick="loadGame()">

📂 SPIEL LADEN

</button>



</div>









<!-- =====================
 INTERNE DATENTABELLE
 NICHT SICHTBAR
===================== -->


<table id="dataStore">



<tr>

<th>STAT</th>

<th>HEIM</th>

<th>GAST</th>

</tr>



<tr>

<td>xG</td>

<td id="storeXgHome">0</td>

<td id="storeXgAway">0</td>

</tr>




<tr>

<td>Ballbesitz</td>

<td id="storePosHome">0</td>

<td id="storePosAway">0</td>

</tr>




<tr>

<td>Schüsse</td>

<td id="storeShotsHome">0</td>

<td id="storeShotsAway">0</td>

</tr>




<tr>

<td>Schüsse aufs Tor</td>

<td id="storeTargetHome">0</td>

<td id="storeTargetAway">0</td>

</tr>




<tr>

<td>Großchancen</td>

<td id="storeChanceHome">0</td>

<td id="storeChanceAway">0</td>

</tr>




<tr>

<td>Ecken</td>

<td id="storeCornerHome">0</td>

<td id="storeCornerAway">0</td>

</tr>




<tr>

<td>Pass angekommen</td>

<td id="storePassHome">0</td>

<td id="storePassAway">0</td>

</tr>




<tr>

<td>Pässe gesamt</td>

<td id="storePassTotalHome">0</td>

<td id="storePassTotalAway">0</td>

</tr>




<tr>

<td>Passquote</td>

<td id="storePassRateHome">0</td>

<td id="storePassRateAway">0</td>

</tr>




<tr>

<td>Gelbe Karten</td>

<td id="storeCardsHome">0</td>

<td id="storeCardsAway">0</td>

</tr>



</table>
<script>


let currentGame="";





/* =====================
 SPIELTAG
===================== */


function loadMatches(){



let text=

document.getElementById("matchInput").value;



localStorage.setItem(
"matchday",
text
);



let lines=

text
.split("\n")
.map(x=>x.trim())
.filter(Boolean);



let list=

document.getElementById("matchList");



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



let card=

document.createElement("div");



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



homeName.innerHTML=home;

awayName.innerHTML=away;



currentGame=

home+"_"+away;



loadGame();



};



matchList.appendChild(card);



}









/* =====================
 ZAHLEN ERKENNEN
===================== */



function getNumbers(text){



return text

.match(/\d+[.,]?\d*/g)

?.map(x=>

Number(
x.replace(",",".")
)

)

||[];


}









function findBlock(name){



let lines=

dataInput.value

.split("\n")

.map(x=>x.trim())

.filter(Boolean);



let index=

lines.findIndex(

x=>

x.toLowerCase()
.includes(
name.toLowerCase()
)

);



if(index==-1)

return [0,0];





let before=[];


for(let i=Math.max(0,index-2);i<index;i++){


let n=getNumbers(lines[i]);


if(n.length)

before.push(...n);


}






let after=[];



for(let i=index+1;i<lines.length;i++){



let n=getNumbers(lines[i]);



if(n.length)

after.push(...n);



if(after.length>=2)

break;


}





if(before.length>=2)


return [

before[0],
before[1]

];





return [

after[0]||0,
after[1]||0

];



}









/* =====================
 PÄSSE
===================== */



function findPasses(){



let matches=

dataInput.value.match(

/\((\d+)\/(\d+)\)/g

);



if(!matches || matches.length<2)


return [

0,0,0,0

];





let home=

matches[0]

.match(/\d+/g);



let away=

matches[1]

.match(/\d+/g);





return [

Number(home[0]),

Number(home[1]),

Number(away[0]),

Number(away[1])

];



}









/* =====================
 DATEN IMPORT
===================== */



function importData(){



let xg=

findBlock(
"Expected Goals"
);



storeXgHome.innerHTML=xg[0];

storeXgAway.innerHTML=xg[1];





let pos=

findBlock(
"Ballbesitz"
);



storePosHome.innerHTML=pos[0];

storePosAway.innerHTML=pos[1];





let shots=

findBlock(
"Schüsse insgesamt"
);



storeShotsHome.innerHTML=shots[0];

storeShotsAway.innerHTML=shots[1];






let target=

findBlock(
"Schüsse aufs Tor"
);



storeTargetHome.innerHTML=target[0];

storeTargetAway.innerHTML=target[1];






let chance=

findBlock(
"Großchance"
);



storeChanceHome.innerHTML=chance[0];

storeChanceAway.innerHTML=chance[1];






let corner=

findBlock(
"Eckbälle"
);



storeCornerHome.innerHTML=corner[0];

storeCornerAway.innerHTML=corner[1];








let passes=

findPasses();



storePassHome.innerHTML=

passes[0];



storePassTotalHome.innerHTML=

passes[1];



storePassAway.innerHTML=

passes[2];



storePassTotalAway.innerHTML=

passes[3];






storePassRateHome.innerHTML=

Math.round(

passes[0]/passes[1]*100

)||0;



storePassRateAway.innerHTML=

Math.round(

passes[2]/passes[3]*100

)||0;







let cards=

findBlock(
"Gelbe Karten"
);



storeCardsHome.innerHTML=cards[0];

storeCardsAway.innerHTML=cards[1];





updateDisplay();



saveGame();



}









/* =====================
 TABELLE → KÄSTCHEN
===================== */


function updateDisplay(){



xgHome.innerHTML=

Number(storeXgHome.innerHTML)
.toFixed(2);



xgAway.innerHTML=

Number(storeXgAway.innerHTML)
.toFixed(2);





posHome.innerHTML=

storePosHome.innerHTML+"%";



posAway.innerHTML=

storePosAway.innerHTML+"%";







shotsHome.innerHTML=

storeShotsHome.innerHTML;


shotsAway.innerHTML=

storeShotsAway.innerHTML;






targetHome.innerHTML=

storeTargetHome.innerHTML;


targetAway.innerHTML=

storeTargetAway.innerHTML;







chanceHome.innerHTML=

storeChanceHome.innerHTML;


chanceAway.innerHTML=

storeChanceAway.innerHTML;







cornerHome.innerHTML=

storeCornerHome.innerHTML;


cornerAway.innerHTML=

storeCornerAway.innerHTML;






passesHome.innerHTML=

storePassHome.innerHTML+

"/"+

storePassTotalHome.innerHTML;



passesAway.innerHTML=

storePassAway.innerHTML+

"/"+

storePassTotalAway.innerHTML;







passRateHome.innerHTML=

storePassRateHome.innerHTML+"%";



passRateAway.innerHTML=

storePassRateAway.innerHTML+"%";







cardsHome.innerHTML=

storeCardsHome.innerHTML;



cardsAway.innerHTML=

storeCardsAway.innerHTML;



}







/* =====================
 SPIEL SPEICHERN
===================== */


function saveGame(){



if(!currentGame)

return;



let save={};



document

.querySelectorAll(
"#dataStore td[id]"
)

.forEach(e=>{


save[e.id]=e.innerHTML;


});



localStorage.setItem(

"livestats_"+currentGame,

JSON.stringify(save)

);



}









/* =====================
 SPIEL LADEN
===================== */


function loadGame(){



if(!currentGame)

return;



let data=

localStorage.getItem(

"livestats_"+currentGame

);



if(!data)

return;



data=

JSON.parse(data);




Object.keys(data)

.forEach(id=>{


let el=

document.getElementById(id);



if(el){


el.innerHTML=data[id];


}



});



updateDisplay();



}









/* =====================
 SPIELTAG LADEN
===================== */


function loadMatchday(){



let data=

localStorage.getItem(
"matchday"
);



if(data){


matchInput.value=data;


loadMatches();


}



}









/* =====================
 VEREINSFARBEN
===================== */



const teamColors={



"1. FC Köln":

"#e30613",



"TSG Hoffenheim":

"#005ca9",



"1. FC Union Berlin":

"#e30613",



"Eintracht Frankfurt":

"#c00000",



"FSV Mainz 05":

"#c41230",



"SC Paderborn":

"#005ca9",



"RB Leipzig":

"#dd0000",



"Borussia Mönchengladbach":

"#00a651",



"SV Elversberg":

"#d4af37",



"Bayer Leverkusen":

"#e32221"



};









function setTeamColors(home,away){



let h=

teamColors[home]

||

"#00b7ff";



let a=

teamColors[away]

||

"#ff4757";




document.documentElement

.style

.setProperty(

"--home-color",

h

);



document.documentElement

.style

.setProperty(

"--away-color",

a

);



}









/* =====================
 START
===================== */


window.onload=function(){


loadMatchday();


};




</script>


</body>

</html>

