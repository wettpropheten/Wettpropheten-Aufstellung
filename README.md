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

inset 0 0 40px #333;


}






.layout{


display:grid;


grid-template-columns:380px 1fr;


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


height:260px;


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


font-weight:bold;


border:1px solid #777;


cursor:pointer;


box-shadow:

0 8px 0 #000;


}




button:hover{


transform:translateY(-2px);


}







/* SPIELTAG */


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




.match-team{


font-size:18px;


font-weight:bold;


margin:8px 0;


}





.match-vs{


text-align:center;


color:#aaa;


}







/* RECHTE SEITE */



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

0 10px 20px #000;


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






<!-- LINKS -->


<div class="panel">


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

">

</textarea>




<button onclick="loadMatches()">

SPIELE LADEN

</button>




<div id="matchList">

</div>



</div>








<!-- RECHTS -->


<div class="panel">



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





<!-- HIER KOMMEN TABELLE UND LIVE DATEN IN TEIL 2 -->




</div>






</div>





</div>
<style>


/* ==========================
   DATENTABELLE
========================== */


.data-box{


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

0 25px 50px #000;


}





table{


width:100%;


border-collapse:collapse;


}




th{


padding:12px;


background:#111;


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




.home-data{


color:var(--home-color);


font-weight:bold;


}



.away-data{


color:var(--away-color);


font-weight:bold;


}





/* ==========================
 LIVE ANZEIGE
========================== */



.live-box{


margin-top:30px;


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





.live-row{


display:flex;


justify-content:space-between;


align-items:center;


margin-top:20px;


font-size:28px;


font-weight:bold;


}




.home-text{


color:var(--home-color);


}



.away-text{


color:var(--away-color);


}





.cards{


display:grid;


grid-template-columns:repeat(3,1fr);


gap:20px;


margin-top:30px;


}




.card{


background:

linear-gradient(
145deg,
#333,
#111
);


border-radius:20px;


padding:20px;


text-align:center;


border:1px solid #555;


box-shadow:

0 15px 30px #000;


}





.card-title{


color:#aaa;


font-size:14px;


}





.card-value{


font-size:35px;


font-weight:bold;


margin-top:10px;


}




/* IMPORT */


.import-box{


margin-top:30px;


}




#dataInput{


height:250px;


}




</style>








<!-- ==========================
 SPIELDATEN TABELLE
========================== -->


<div class="data-box">


<h2>

SPIELDATEN

</h2>




<table>



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





<tr>

<td class="stat-name">

Expected Goals (xG)

</td>


<td id="xgHome"

class="home-data">

0.00

</td>


<td id="xgAway"

class="away-data">

0.00

</td>


</tr>







<tr>

<td class="stat-name">

Ballbesitz

</td>


<td id="posHome"

class="home-data">

0%

</td>


<td id="posAway"

class="away-data">

0%

</td>


</tr>







<tr>

<td class="stat-name">

Schüsse

</td>


<td id="shotsHome"

class="home-data">

0

</td>


<td id="shotsAway"

class="away-data">

0

</td>


</tr>







<tr>

<td class="stat-name">

Schüsse aufs Tor

</td>


<td id="targetHome"

class="home-data">

0

</td>


<td id="targetAway"

class="away-data">

0

</td>


</tr>







<tr>

<td class="stat-name">

Großchancen

</td>


<td id="chanceHome"

class="home-data">

0

</td>


<td id="chanceAway"

class="away-data">

0

</td>


</tr>







<tr>

<td class="stat-name">

Ecken

</td>


<td id="cornerHome"

class="home-data">

0

</td>


<td id="cornerAway"

class="away-data">

0

</td>


</tr>







<tr>

<td class="stat-name">

Pässe

</td>


<td id="passHome"

class="home-data">

0

</td>


<td id="passAway"

class="away-data">

0

</td>


</tr>







<tr>

<td class="stat-name">

Gelbe Karten

</td>


<td id="cardsHome"

class="home-data">

0

</td>


<td id="cardsAway"

class="away-data">

0

</td>


</tr>





</table>


</div>









<!-- LIVE ANZEIGE -->


<div class="live-box">


<h2>

LIVE STATISTIK

</h2>



<div class="live-row">


<span id="liveXgHome"

class="home-text">

0.00

</span>


Expected Goals


<span id="liveXgAway"

class="away-text">

0.00

</span>


</div>





<div class="cards">



<div class="card">

<div class="card-title">

SCHÜSSE

</div>


<div class="card-value">

<span id="liveShotsHome"
class="home-text">

0

</span>

:

<span id="liveShotsAway"
class="away-text">

0

</span>

</div>


</div>







<div class="card">

<div class="card-title">

SCHÜSSE AUFS TOR

</div>


<div class="card-value">

<span id="liveTargetHome"
class="home-text">

0

</span>

:

<span id="liveTargetAway"
class="away-text">

0

</span>

</div>


</div>







<div class="card">

<div class="card-title">

PÄSSE

</div>


<div class="card-value">

<span id="livePassHome"
class="home-text">

0

</span>

:

<span id="livePassAway"
class="away-text">

0

</span>

</div>


</div>



</div>


</div>








<!-- DATEN IMPORT -->


<div class="data-box import-box">


<h2>

LIVE DATEN EINGEBEN

</h2>



<textarea id="dataInput"

placeholder="

Hier Daten einfügen:

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


let currentGame="";





/* ==========================
   SPIELTAG LADEN
========================== */


function loadMatches(){


let lines=

matchInput.value
.split("\n")
.map(x=>x.trim())
.filter(Boolean);



matchList.innerHTML="";



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


saveMatchday();


}









function createMatch(time,home,away){



let div=document.createElement("div");


div.className="match-card";



div.innerHTML=`

<div>${time}</div>

<div class="match-team">${home}</div>

<div class="match-vs">VS</div>

<div class="match-team">${away}</div>

`;



div.onclick=function(){


homeName.innerHTML=home;

awayName.innerHTML=away;


currentGame=

home+"_"+away;



loadGame();


};



matchList.appendChild(div);



}









/* ==========================
   DATEN IMPORT
========================== */



function number(value){


let n=value.match(/\d+[.,]?\d*/);


if(!n)

return null;



return Number(
n[0].replace(",",".")
);


}






function lines(){


return dataInput.value

.split("\n")

.map(x=>x.trim())

.filter(Boolean);


}






function findStat(name){



let l=lines();



let index=l.findIndex(

x=>

x.toLowerCase()
.includes(
name.toLowerCase()
)

);



if(index<0)

return [0,0];




let before=null;


if(index>0){


before=number(l[index-1]);


}





let after=[];



for(let i=index+1;i<l.length;i++){



let n=number(l[i]);



if(n!==null)

after.push(n);



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







function findPasses(){



let p=

dataInput.value.match(

/\((\d+)\/\d+\)/g

);



if(p && p.length>=2){


return [

Number(p[0].match(/\d+/)[0]),

Number(p[1].match(/\d+/)[0])

];


}


return [0,0];



}









function importData(){



let xg=findStat(
"Expected Goals"
);


xgHome.innerHTML=xg[0].toFixed(2);

xgAway.innerHTML=xg[1].toFixed(2);





let pos=findStat(
"Ballbesitz"
);


posHome.innerHTML=pos[0]+"%";

posAway.innerHTML=pos[1]+"%";





let shots=findStat(
"Schüsse insgesamt"
);


shotsHome.innerHTML=shots[0];

shotsAway.innerHTML=shots[1];





let target=findStat(
"Schüsse aufs Tor"
);


targetHome.innerHTML=target[0];

targetAway.innerHTML=target[1];






let chance=findStat(
"Großchance"
);


chanceHome.innerHTML=chance[0];

chanceAway.innerHTML=chance[1];







let corner=findStat(
"Eckbälle"
);


cornerHome.innerHTML=corner[0];

cornerAway.innerHTML=corner[1];







let cards=findStat(
"Gelbe Karten"
);


cardsHome.innerHTML=cards[0];

cardsAway.innerHTML=cards[1];






let pass=findPasses();



passHome.innerHTML=pass[0];

passAway.innerHTML=pass[1];





updateLive();



saveGame();



}








/* ==========================
 LIVE ANZEIGE
========================== */



function updateLive(){



liveXgHome.innerHTML=xgHome.innerHTML;

liveXgAway.innerHTML=xgAway.innerHTML;



liveShotsHome.innerHTML=shotsHome.innerHTML;

liveShotsAway.innerHTML=shotsAway.innerHTML;



liveTargetHome.innerHTML=targetHome.innerHTML;

liveTargetAway.innerHTML=targetAway.innerHTML;



livePassHome.innerHTML=passHome.innerHTML;

livePassAway.innerHTML=passAway.innerHTML;



}









/* ==========================
 SPEICHERN
========================== */


function saveGame(){



if(!currentGame)

return;



let data={};



document
.querySelectorAll(
"td[id]"
)
.forEach(e=>{


data[e.id]=e.innerHTML;


});



localStorage.setItem(

"game_"+currentGame,

JSON.stringify(data)

);



}





function loadGame(){



let data=

localStorage.getItem(

"game_"+currentGame

);



if(!data)

return;



data=JSON.parse(data);



Object.keys(data)
.forEach(id=>{


if(document.getElementById(id)){


document.getElementById(id).innerHTML=data[id];


}



});



updateLive();



}









/* ==========================
 SPIELTAG SPEICHERN
========================== */



function saveMatchday(){


localStorage.setItem(

"matchday",

matchInput.value

);



}



function loadMatchday(){



let d=

localStorage.getItem(
"matchday"
);



if(d){


matchInput.value=d;


loadMatches();


}



}





window.onload=function(){


loadMatchday();


};



</script>


</body>

</html>
