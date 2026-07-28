<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro 3D 2.0</title>


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
#1b1b1b,
#050505
);


border-radius:35px;


box-shadow:


0 50px 100px #000,


inset 0 0 50px #333;


}




.layout{


display:grid;


grid-template-columns:400px 1fr;


gap:25px;


}





.panel{


background:

linear-gradient(
145deg,
#292929,
#080808
);


border-radius:25px;


padding:20px;


border:1px solid #555;


box-shadow:


0 25px 60px #000,


inset 0 0 30px #333;


}






/* SPIELTAG */


.left-panel{


height:1000px;


overflow:auto;


}




h2{


text-align:center;


}




textarea{


width:100%;


background:#000;


color:white;


border:1px solid #666;


border-radius:15px;


padding:15px;


font-size:16px;


}




#matchInput{


height:250px;


}



button{


width:100%;


margin-top:15px;


padding:15px;


border-radius:15px;


border:1px solid #777;


background:


linear-gradient(
180deg,
#666,
#111
);


color:white;


font-weight:bold;


cursor:pointer;


box-shadow:


0 8px 0 #000;


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


cursor:pointer;


box-shadow:


0 15px 30px #000;


}



.match-card:hover{


transform:translateY(-4px);


}





.match-team{


font-weight:bold;


font-size:18px;


margin:8px 0;


}



.match-vs{


text-align:center;


color:#999;


}




/* RECHTS */


.right-panel{


min-height:1000px;


}



.scoreboard{


display:flex;


justify-content:space-between;


align-items:center;


border-bottom:1px solid #555;


padding-bottom:25px;


}




.team-name{


width:40%;


text-align:center;


font-size:36px;


font-weight:bold;


text-shadow:


0 10px 25px black;


}




.score{


font-size:80px;


font-weight:bold;


}



</style>


</head>


<body>



<div class="container">



<div class="layout">



<div class="panel left-panel">


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





<div class="panel right-panel">



<div class="scoreboard">


<div id="homeName" class="team-name">

HEIM

</div>


<div class="score">

0 : 0

</div>



<div id="awayName" class="team-name">

GAST

</div>


</div>



<!-- DATENTABELLE KOMMT TEIL 2 -->

<div id="dataTableArea">


</div>



</div>



</div>


</div>
<style>


/* ==========================
   DATENTABELLE
========================== */


.data-table-box{


margin-top:35px;


background:

linear-gradient(
145deg,
#222,
#090909
);


border-radius:25px;


padding:20px;


border:1px solid #555;


box-shadow:

0 25px 50px #000,

inset 0 0 25px #333;


}




.data-table-box h2{


font-size:24px;


text-align:center;


}





table{


width:100%;


border-collapse:collapse;


margin-top:20px;


}





th{


background:#111;


padding:12px;


border:1px solid #555;


}



td{


padding:12px;


border:1px solid #444;


text-align:center;


font-size:18px;


}





.stat-name{


text-align:left;


font-weight:bold;


color:#ccc;


}



.table-home{


color:var(--home-color);


font-weight:bold;


}



.table-away{


color:var(--away-color);


font-weight:bold;


}





</style>








<!-- ==========================
   SPIELDATEN TABELLE
========================== -->


<div class="data-table-box">


<h2>

SPIELDATENBANK

</h2>




<table>


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




<tbody id="statsTable">



<tr>


<td class="stat-name">

Expected Goals (xG)

</td>


<td id="table_xg_home"
class="table-home">

0.00

</td>


<td id="table_xg_away"
class="table-away">

0.00

</td>


</tr>






<tr>


<td class="stat-name">

Ballbesitz

</td>


<td id="table_pos_home"
class="table-home">

0

</td>


<td id="table_pos_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Schüsse

</td>


<td id="table_shots_home"
class="table-home">

0

</td>


<td id="table_shots_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Schüsse aufs Tor

</td>


<td id="table_target_home"
class="table-home">

0

</td>


<td id="table_target_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Großchancen

</td>


<td id="table_chance_home"
class="table-home">

0

</td>


<td id="table_chance_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Ecken

</td>


<td id="table_corner_home"
class="table-home">

0

</td>


<td id="table_corner_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Passquote

</td>


<td id="table_passrate_home"
class="table-home">

0%

</td>


<td id="table_passrate_away"
class="table-away">

0%

</td>


</tr>







<tr>


<td class="stat-name">

Pässe

</td>


<td id="table_pass_home"
class="table-home">

0

</td>


<td id="table_pass_away"
class="table-away">

0

</td>


</tr>







<tr>


<td class="stat-name">

Gelbe Karten

</td>


<td id="table_cards_home"
class="table-home">

0

</td>


<td id="table_cards_away"
class="table-away">

0

</td>


</tr>



</tbody>


</table>


</div>







<!-- IMPORT BEREICH -->


<div class="data-table-box">


<h2>

LIVE DATEN IMPORT

</h2>



<textarea

id="dataInput"

placeholder="

Hier Live-Daten einfügen:

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



<button onclick="importData()">

DATEN ÜBERNEHMEN

</button>



</div>
<script>


/* ==========================
   SPIELDATEN SPEICHER
========================== */


let currentGame="";





/* ==========================
   SPIELTAG LADEN
========================== */


function loadMatches(){



let lines=

document
.getElementById("matchInput")
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

<div>

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









function setTeams(home,away){



currentGame=

home+"_"+away;



document
.getElementById("homeName")
.innerHTML=home;



document
.getElementById("awayName")
.innerHTML=away;



}









/* ==========================
   TEXT IN ZEILEN
========================== */


function getInputLines(){


return document
.getElementById("dataInput")
.value
.split("\n")
.map(x=>x.trim())
.filter(Boolean);


}





function getNumber(text){


let match=

text.match(
/\d+(?:[.,]\d+)?
/);



if(match)

return Number(
match[0]
.replace(",",".")
);



return null;


}










/* ==========================
   STATISTIK FINDEN
========================== */


function findValues(title){



let lines=getInputLines();



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


before=getNumber(
lines[index-1]
);


}




let after=[];



for(
let i=index+1;

i<lines.length;

i++

){



let n=getNumber(
lines[i]
);



if(n!==null){


after.push(n);


}



if(after.length===2)

break;



}





if(before!==null && after.length>0){


return [

before,

after[0]

];


}




return [

after[0] || 0,

after[1] || 0

];


}









/* ==========================
   PÄSSE
========================== */


function findPasses(){



let text=

document
.getElementById("dataInput")
.value;



let values=

text.match(
/\((\d+)\/\d+\)/g
);



if(values && values.length>=2){



return [

Number(
values[0]
.match(/\d+/)[0]
),


Number(
values[1]
.match(/\d+/)[0]
)

];


}



return [0,0];

}










/* ==========================
   IMPORT IN TABELLE
========================== */


function importData(){



let xg=

findValues(
"Expected Goals"
);



table_xg_home.innerHTML=

xg[0].toFixed(2);



table_xg_away.innerHTML=

xg[1].toFixed(2);








let pos=

findValues(
"Ballbesitz"
);



table_pos_home.innerHTML=

pos[0]+"%";


table_pos_away.innerHTML=

pos[1]+"%";







let shots=

findValues(
"Schüsse insgesamt"
);



table_shots_home.innerHTML=

shots[0];


table_shots_away.innerHTML=

shots[1];







let target=

findValues(
"Schüsse aufs Tor"
);



table_target_home.innerHTML=

target[0];


table_target_away.innerHTML=

target[1];







let chance=

findValues(
"Großchance"
);



table_chance_home.innerHTML=

chance[0];


table_chance_away.innerHTML=

chance[1];







let corner=

findValues(
"Eckbälle"
);



table_corner_home.innerHTML=

corner[0];


table_corner_away.innerHTML=

corner[1];







let cards=

findValues(
"Gelbe Karten"
);



table_cards_home.innerHTML=

cards[0];


table_cards_away.innerHTML=

cards[1];








let passes=findPasses();



table_pass_home.innerHTML=

passes[0];


table_pass_away.innerHTML=

passes[1];





}



</script>
<style>


/* ==========================
   LIVE ANZEIGE
========================== */


.live-panel{


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

0 25px 60px #000,

inset 0 0 30px #333;


}





.live-title{


text-align:center;


font-size:28px;


font-weight:bold;


margin-bottom:25px;


}




.stat-line{


margin-top:25px;


}





.stat-head{


display:flex;


justify-content:space-between;


font-size:30px;


font-weight:bold;


}



.home-live{


color:var(--home-color);


text-shadow:

0 0 15px var(--home-color);


}



.away-live{


color:var(--away-color);


text-shadow:

0 0 15px var(--away-color);


}





.stat-bar{


height:28px;


display:flex;


background:#000;


border-radius:20px;


overflow:hidden;


border:1px solid #555;


margin-top:10px;


}



.stat-bar-home{


background:var(--home-color);


height:100%;


}



.stat-bar-away{


background:var(--away-color);


height:100%;


}




.live-grid{


display:grid;


grid-template-columns:repeat(3,1fr);


gap:20px;


margin-top:35px;


}





.live-box{


background:

linear-gradient(
145deg,
#333,
#090909
);


border-radius:20px;


padding:20px;


text-align:center;


border:1px solid #555;


box-shadow:

0 15px 35px #000;


}




.live-box-title{


color:#aaa;


font-size:14px;


}





.live-number{


font-size:34px;


font-weight:bold;


margin-top:10px;


}





</style>







<div class="live-panel">


<div class="live-title">

LIVE STATISTIK

</div>





<div class="stat-line">


<div class="stat-head">

<span class="home-live">

<span id="live_xg_home">

0.00

</span>

</span>



Expected Goals (xG)



<span class="away-live">

<span id="live_xg_away">

0.00

</span>

</span>


</div>


</div>









<div class="stat-line">


<div class="stat-head">


<span class="home-live">

<span id="live_pos_home">

0%

</span>

</span>



Ballbesitz



<span class="away-live">

<span id="live_pos_away">

0%

</span>

</span>


</div>


<div class="stat-bar">


<div id="pos_live_home"
class="stat-bar-home"
style="width:50%">

</div>


<div id="pos_live_away"
class="stat-bar-away"
style="width:50%">

</div>


</div>


</div>









<div class="live-grid">



<div class="live-box">


<div class="live-box-title">

SCHÜSSE

</div>


<div class="live-number">


<span id="live_shots_home"
class="home-live">

0

</span>


:


<span id="live_shots_away"
class="away-live">

0

</span>


</div>


</div>








<div class="live-box">


<div class="live-box-title">

SCHÜSSE AUFS TOR

</div>


<div class="live-number">


<span id="live_target_home"
class="home-live">

0

</span>


:


<span id="live_target_away"
class="away-live">

0

</span>


</div>


</div>








<div class="live-box">


<div class="live-box-title">

GROSSCHANCEN

</div>


<div class="live-number">


<span id="live_chance_home"
class="home-live">

0

</span>


:


<span id="live_chance_away"
class="away-live">

0

</span>


</div>


</div>








<div class="live-box">


<div class="live-box-title">

ECKEN

</div>


<div class="live-number">


<span id="live_corner_home"
class="home-live">

0

</span>


:


<span id="live_corner_away"
class="away-live">

0

</span>


</div>


</div>








<div class="live-box">


<div class="live-box-title">

PÄSSE

</div>


<div class="live-number">


<span id="live_pass_home"
class="home-live">

0

</span>


:


<span id="live_pass_away"
class="away-live">

0

</span>


</div>


</div>








<div class="live-box">


<div class="live-box-title">

GELBE KARTEN

</div>


<div class="live-number">


<span id="live_cards_home"
class="home-live">

0

</span>


:


<span id="live_cards_away"
class="away-live">

0

</span>


</div>


</div>



</div>


</div>









<script>


/* ==========================
   TABELLE → LIVE ANZEIGE
========================== */



function updateLiveView(){



live_xg_home.innerHTML=

table_xg_home.innerHTML;



live_xg_away.innerHTML=

table_xg_away.innerHTML;





live_pos_home.innerHTML=

table_pos_home.innerHTML;



live_pos_away.innerHTML=

table_pos_away.innerHTML;





pos_live_home.style.width=

table_pos_home.innerHTML;



pos_live_away.style.width=

table_pos_away.innerHTML;







live_shots_home.innerHTML=

table_shots_home.innerHTML;


live_shots_away.innerHTML=

table_shots_away.innerHTML;






live_target_home.innerHTML=

table_target_home.innerHTML;


live_target_away.innerHTML=

table_target_away.innerHTML;







live_chance_home.innerHTML=

table_chance_home.innerHTML;


live_chance_away.innerHTML=

table_chance_away.innerHTML;







live_corner_home.innerHTML=

table_corner_home.innerHTML;


live_corner_away.innerHTML=

table_corner_away.innerHTML;







live_pass_home.innerHTML=

table_pass_home.innerHTML;


live_pass_away.innerHTML=

table_pass_away.innerHTML;







live_cards_home.innerHTML=

table_cards_home.innerHTML;


live_cards_away.innerHTML=

table_cards_away.innerHTML;



}







/* nach Import aktualisieren */


let oldImportData=importData;



importData=function(){


oldImportData();


updateLiveView();


};



</script>
<script>


/* ==========================
   SPIEL SPEICHERN
========================== */


function saveGame(){



if(!currentGame)

return;



let save={



xgHome:table_xg_home.innerHTML,

xgAway:table_xg_away.innerHTML,


posHome:table_pos_home.innerHTML,

posAway:table_pos_away.innerHTML,


shotsHome:table_shots_home.innerHTML,

shotsAway:table_shots_away.innerHTML,


targetHome:table_target_home.innerHTML,

targetAway:table_target_away.innerHTML,


chanceHome:table_chance_home.innerHTML,

chanceAway:table_chance_away.innerHTML,


cornerHome:table_corner_home.innerHTML,

cornerAway:table_corner_away.innerHTML,


passHome:table_pass_home.innerHTML,

passAway:table_pass_away.innerHTML,


cardsHome:table_cards_home.innerHTML,

cardsAway:table_cards_away.innerHTML


};




localStorage.setItem(

"livestats_"+currentGame,

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

"livestats_"+currentGame

);



if(!data)

return;



data=

JSON.parse(data);





table_xg_home.innerHTML=data.xgHome;

table_xg_away.innerHTML=data.xgAway;


table_pos_home.innerHTML=data.posHome;

table_pos_away.innerHTML=data.posAway;


table_shots_home.innerHTML=data.shotsHome;

table_shots_away.innerHTML=data.shotsAway;


table_target_home.innerHTML=data.targetHome;

table_target_away.innerHTML=data.targetAway;


table_chance_home.innerHTML=data.chanceHome;

table_chance_away.innerHTML=data.chanceAway;


table_corner_home.innerHTML=data.cornerHome;

table_corner_away.innerHTML=data.cornerAway;


table_pass_home.innerHTML=data.passHome;

table_pass_away.innerHTML=data.passAway;


table_cards_home.innerHTML=data.cardsHome;

table_cards_away.innerHTML=data.cardsAway;



updateLiveView();



}










/* ==========================
   SPIELTAG SPEICHERN
========================== */


function saveMatchday(){


localStorage.setItem(

"spieltag",

document
.getElementById("matchInput")
.value

);


}







function loadMatchday(){



let data=

localStorage.getItem(
"spieltag"
);



if(data){


matchInput.value=data;


loadMatches();


}



}










/* ==========================
   AUTO SPEICHERN
========================== */


document
.getElementById("matchInput")
.addEventListener(
"change",
saveMatchday
);








window.onload=function(){


loadMatchday();


};





</script>



</body>

</html>
