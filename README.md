<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro Final V2</title>

<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


body{
margin:0;
background:transparent;
color:white;
}


.overlay{

width:1100px;

margin:40px auto;

background:rgba(5,15,35,.96);

border-radius:20px;

padding:30px;

box-shadow:0 0 50px rgba(0,0,0,.8);

}



/* SPIELSTAND */

.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

border-bottom:2px solid #26354d;

padding-bottom:20px;

}


.team{

width:35%;

text-align:center;

}


.team-name{

font-size:34px;

font-weight:900;

}


.score{

font-size:75px;

font-weight:900;

}


.timer{

font-size:30px;

font-weight:bold;

color:#00c8ff;

}




/* BALKEN */

.stat{

margin-top:30px;

}


.stat-title{

text-align:center;

font-size:22px;

font-weight:bold;

margin-bottom:10px;

}


.bar-area{

position:relative;

height:70px;

}



.stat-value{

position:absolute;

top:0;

font-size:25px;

font-weight:bold;

}



.left-value{

left:25%;

transform:translateX(-50%);

color:#00b7ff;

}



.right-value{

left:75%;

transform:translateX(-50%);

color:#ff4757;

}



.bar{

position:absolute;

bottom:10px;

width:100%;

height:18px;

background:#18263d;

border-radius:20px;

overflow:hidden;

display:flex;

}



.home-bar{

height:100%;

background:#00b7ff;

}



.away-bar{

height:100%;

background:#ff4757;

}




.home{

color:#00b7ff;

}


.away{

color:#ff4757;

}



/* STATISTIK BOXEN */


.grid{

display:grid;

grid-template-columns:repeat(4,1fr);

gap:15px;

margin-top:35px;

}



.box{

background:#101d35;

border-radius:12px;

padding:15px;

text-align:center;

}



.box-title{

font-size:13px;

opacity:.7;

}


.box-value{

font-size:30px;

font-weight:bold;

}




/* EINGABE */


.input-area{

margin-top:35px;

background:#0c1930;

padding:20px;

border-radius:15px;

}



textarea{

width:100%;

height:260px;

background:#071326;

color:white;

border:0;

border-radius:10px;

padding:15px;

font-size:16px;

}



button{

width:100%;

margin-top:15px;

padding:15px;

background:#00b7ff;

border:0;

border-radius:10px;

color:white;

font-size:18px;

font-weight:bold;

cursor:pointer;

}


</style>

</head>


<body>


<div class="overlay">
<!-- SPIELSTAND -->


<div class="scoreboard">


<div class="team">

<div class="team-name" id="homeTeam">
HEIMTEAM
</div>


<div class="score" id="homeScore">
0
</div>

</div>





<div class="timer" id="gameTime">
00:00
</div>





<div class="team">

<div class="team-name" id="awayTeam">
AUSWÄRTS
</div>


<div class="score" id="awayScore">
0
</div>

</div>


</div>







<!-- EXPECTED GOALS -->


<div class="stat">


<div class="stat-title">
Expected Goals (xG)
</div>



<div class="bar-area">


<div class="stat-value left-value" id="xgHome">
0.00
</div>


<div class="stat-value right-value" id="xgAway">
0.00
</div>




<div class="bar">


<div class="home-bar" id="xgHomeBar" style="width:50%">
</div>


<div class="away-bar" id="xgAwayBar" style="width:50%">
</div>


</div>


</div>


</div>







<!-- BALLBESITZ -->


<div class="stat">


<div class="stat-title">
Ballbesitz
</div>



<div class="bar-area">


<div class="stat-value left-value" id="posHome">
50%
</div>



<div class="stat-value right-value" id="posAway">
50%
</div>




<div class="bar">


<div class="home-bar" id="posHomeBar" style="width:50%">
</div>


<div class="away-bar" id="posAwayBar" style="width:50%">
</div>


</div>


</div>


</div>







<!-- STATISTIK WERTE -->


<div class="grid">



<div class="box">

<div class="box-title">
SCHÜSSE AUFS TOR
</div>


<div class="box-value">

<span class="home" id="targetHome">
0
</span>

:

<span class="away" id="targetAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
SCHÜSSE NEBEN TOR
</div>


<div class="box-value">

<span class="home" id="offHome">
0
</span>

:

<span class="away" id="offAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
GEBLOCKTE SCHÜSSE
</div>


<div class="box-value">

<span class="home" id="blockHome">
0
</span>

:

<span class="away" id="blockAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
ECKEN
</div>


<div class="box-value">

<span class="home" id="cornerHome">
0
</span>

:

<span class="away" id="cornerAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
ABSEITS
</div>


<div class="box-value">

<span class="home" id="offsideHome">
0
</span>

:

<span class="away" id="offsideAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
FOULS
</div>


<div class="box-value">

<span class="home" id="foulHome">
0
</span>

:

<span class="away" id="foulAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
EINWÜRFE
</div>


<div class="box-value">

<span class="home" id="throwHome">
0
</span>

:

<span class="away" id="throwAway">
0
</span>

</div>

</div>





<div class="box">

<div class="box-title">
GELBE KARTEN
</div>


<div class="box-value">

<span class="home" id="cardHome">
0
</span>

:

<span class="away" id="cardAway">
0
</span>

</div>

</div>



</div>
<!-- EINGABE BEREICH -->


<div class="input-area">


<h2>
LIVE DATEN EINGEBEN
</h2>



<textarea 
id="dataInput"
placeholder="Hier die kopierten Live-Statistiken einfügen...">
</textarea>



<button onclick="updateData()">
AKTUALISIEREN
</button>


</div>


</div>






<script>


function extractNumber(value){

return Number(
value
.replace(",",".")
.match(/\d+(\.\d+)?/)?.[0] || 0
);

}





function findStat(text,keywords){



let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x!="");



let index=-1;



for(let word of keywords){


index=lines.findIndex(
line =>
line
.toLowerCase()
.includes(word.toLowerCase())
);



if(index!==-1){

break;

}


}




if(index===-1){

return [0,0];

}



let numbers=[];




// Zahl davor suchen

for(let i=index-1;i>=0;i--){


let n=lines[i].match(/\d+([.,]\d+)?/);


if(n){

numbers.unshift(
extractNumber(n[0])
);

break;

}


}






// Zahlen danach suchen

for(let i=index+1;i<lines.length;i++){


let n=lines[i].match(/\d+([.,]\d+)?/);



if(n){

numbers.push(
extractNumber(n[0])
);

break;

}


}




if(numbers.length!==2){

return [0,0];

}



return numbers;


}





function setValue(id,value){


document.getElementById(id).innerHTML=value;


}






function updateBar(home,away,left,right){


let total=home+away;



if(total<=0){

return;

}



document.getElementById(left).style.width=
(home/total*100)+"%";



document.getElementById(right).style.width=
(away/total*100)+"%";


}






function updateData(){



let text=
document.getElementById("dataInput").value;



if(text.trim()==""){


alert("Bitte zuerst Daten einfügen");


return;


}






// BALLBESITZ


let pos=findStat(
text,
[
"Ballbesitz",
"Ballbesitz (%)"
]
);



setValue(
"posHome",
pos[0]+"%"
);


setValue(
"posAway",
pos[1]+"%"
);



document.getElementById("posHomeBar").style.width=
pos[0]+"%";


document.getElementById("posAwayBar").style.width=
pos[1]+"%";









// EXPECTED GOALS


let xg=findStat(
text,
[
"xG",
"Expected Goals"
]
);



setValue(
"xgHome",
xg[0].toFixed(2)
);



setValue(
"xgAway",
xg[1].toFixed(2)
);



updateBar(
xg[0],
xg[1],
"xgHomeBar",
"xgAwayBar"
);







// SCHÜSSE AUFS TOR


let target=findStat(
text,
[
"Schüsse aufs Tor"
]
);


setValue(
"targetHome",
target[0]
);


setValue(
"targetAway",
target[1]
);







// SCHÜSSE NEBEN TOR


let off=findStat(
text,
[
"Schüsse neben das Tor",
"Schüsse neben"
]
);


setValue(
"offHome",
off[0]
);


setValue(
"offAway",
off[1]
);







// GEBLOCKTE SCHÜSSE


let block=findStat(
text,
[
"Geblockte Schüsse"
]
);


setValue(
"blockHome",
block[0]
);


setValue(
"blockAway",
block[1]
);







// ECKEN


let corner=findStat(
text,
[
"Eckstöße",
"Ecken"
]
);


setValue(
"cornerHome",
corner[0]
);


setValue(
"cornerAway",
corner[1]
);







// ABSEITS


let offside=findStat(
text,
[
"Abseitsstellungen",
"Abseits"
]
);


setValue(
"offsideHome",
offside[0]
);


setValue(
"offsideAway",
offside[1]
);







// FOULS


let foul=findStat(
text,
[
"Fouls"
]
);


setValue(
"foulHome",
foul[0]
);


setValue(
"foulAway",
foul[1]
);







// EINWÜRFE


let throwin=findStat(
text,
[
"Einwürfe"
]
);


setValue(
"throwHome",
throwin[0]
);


setValue(
"throwAway",
throwin[1]
);







// GELBE KARTEN


let cards=findStat(
text,
[
"Gelbe Karten"
]
);


setValue(
"cardHome",
cards[0]
);


setValue(
"cardAway",
cards[1]
);





localStorage.setItem(
"liveStatsFinal",
text
);



}
window.onload=function(){


let saved=
localStorage.getItem("liveStatsFinal");



if(saved){


document.getElementById("dataInput").value=saved;


updateData();


}


}



</script>


</body>

</html>
