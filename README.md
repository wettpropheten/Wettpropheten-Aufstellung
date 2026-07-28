<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro Ultimate</title>


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

background:#000;

color:white;

}



.overlay{

width:1400px;

margin:20px auto;

background:#050505;

border-radius:20px;

padding:20px;

box-shadow:0 0 60px #000;

}





/* HAUPT LAYOUT */

.main-layout{

display:grid;

grid-template-columns:250px 1fr 250px;

gap:20px;

}





/* MANNSCHAFTS BOXEN */


.team-panel{

background:#080808;

border:1px solid #333;

border-radius:15px;

padding:15px;

height:850px;

overflow-y:auto;

}



.team-panel h2{

text-align:center;

font-size:22px;

margin-top:5px;

}



.team-panel label{

display:block;

background:#111;

padding:10px;

margin:8px 0;

border-radius:8px;

cursor:pointer;

font-size:15px;

}



.team-panel label:hover{

background:#222;

}



.team-panel input{

transform:scale(1.3);

margin-right:10px;

}





/* MITTE */


.stats-panel{

background:#050505;

border-radius:15px;

padding:25px;

}




.scoreboard{

display:flex;

justify-content:space-between;

align-items:center;

border-bottom:1px solid #333;

padding-bottom:20px;

}



.team-name{

font-size:30px;

font-weight:bold;

text-align:center;

}



.score{

font-size:65px;

font-weight:bold;

color:var(--home-color);

}



.away-score{

color:var(--away-color);

}



.timer{

font-size:28px;

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

height:70px;

position:relative;

}



.value-left,
.value-right{

position:absolute;

top:0;

font-size:25px;

font-weight:bold;

}



.value-left{

left:25%;

transform:translateX(-50%);

color:var(--home-color);

}



.value-right{

left:75%;

transform:translateX(-50%);

color:var(--away-color);

}



.bar{

position:absolute;

bottom:10px;

width:100%;

height:20px;

background:#000;

border:1px solid #333;

border-radius:20px;

overflow:hidden;

display:flex;

}



.home-bar{

height:100%;

background:var(--home-color);

}



.away-bar{

height:100%;

background:var(--away-color);

}
<!-- STATISTIK BOXEN -->

<style>

.grid{

display:grid;

grid-template-columns:repeat(3,1fr);

gap:15px;

margin-top:35px;

}



.box{

background:#101010;

border:1px solid #333;

border-radius:12px;

padding:15px;

text-align:center;

}



.box-title{

font-size:13px;

opacity:.7;

}



.box-value{

font-size:28px;

font-weight:bold;

}



.home{

color:var(--home-color);

}



.away{

color:var(--away-color);

}





.input-area{

margin-top:30px;

background:#080808;

border:1px solid #333;

padding:20px;

border-radius:15px;

}



textarea{

width:100%;

height:220px;

background:#000;

color:white;

border:1px solid #333;

border-radius:10px;

padding:15px;

font-size:16px;

}



button{

width:100%;

margin-top:15px;

padding:15px;

background:#222;

color:white;

border:1px solid #555;

border-radius:10px;

font-size:18px;

font-weight:bold;

cursor:pointer;

}



</style>





<!-- MITTLERE STATISTIK -->


<div class="stat">


<div class="stat-title">
Expected Goals (xG)
</div>


<div class="bar-area">


<div class="value-left" id="xgHome">
0.00
</div>


<div class="value-right" id="xgAway">
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






<div class="stat">


<div class="stat-title">
Ballbesitz
</div>


<div class="bar-area">


<div class="value-left" id="posHome">
50%
</div>


<div class="value-right" id="posAway">
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






<div class="grid">



<div class="box">

<div class="box-title">
SCHÜSSE GESAMT
</div>

<div class="box-value">

<span class="home" id="shotsHome">0</span>
:
<span class="away" id="shotsAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
SCHÜSSE AUFS TOR
</div>

<div class="box-value">

<span class="home" id="targetHome">0</span>
:
<span class="away" id="targetAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
GROSSCHANCEN
</div>

<div class="box-value">

<span class="home" id="chanceHome">0</span>
:
<span class="away" id="chanceAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
ECKBÄLLE
</div>

<div class="box-value">

<span class="home" id="cornerHome">0</span>
:
<span class="away" id="cornerAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
PASSQUOTE
</div>

<div class="box-value">

<span class="home" id="passHome">0%</span>
:
<span class="away" id="passAway">0%</span>

</div>

</div>





<div class="box">

<div class="box-title">
PÄSSE GESAMT
</div>

<div class="box-value">

<span class="home" id="passTotalHome">
0/0
</span>

:

<span class="away" id="passTotalAway">
0/0
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






<div class="input-area">

<h2>
LIVE DATEN EINFÜGEN
</h2>


<textarea id="dataInput"
placeholder="Statistik hier einfügen..."></textarea>


<button onclick="updateData()">
AKTUALISIEREN
</button>


</div>



</div> <!-- Ende Statistik Panel -->



<script>


/* MANNSCHAFTEN + FARBEN */


const teams = {


"SV Werder Bremen":"#00875A",

"Borussia Dortmund":"#FDE100",

"Bayern München":"#DC052D",

"Bayer Leverkusen":"#E32221",

"RB Leipzig":"#FFFFFF",

"VfB Stuttgart":"#FFFFFF",

"Borussia Mönchengladbach":"#FFFFFF",

"Eintracht Frankfurt":"#FFFFFF",

"1. FC Köln":"#FFFFFF",

"TSG Hoffenheim":"#005CA9",

"SC Freiburg":"#E30613",

"FSV Mainz 05":"#C41230",

"FC Augsburg":"#BA3733",

"VfL Wolfsburg":"#65B32E",

"FC St. Pauli":"#5A372A",

"Hamburger SV":"#005CA9",

"Hertha BSC":"#0057B8",

"Schalke 04":"#004C99",

"1. FC Union Berlin":"#EB0016"

};





function createTeams(){


let home=document.getElementById("homeList");

let away=document.getElementById("awayList");



Object.keys(teams).forEach(team=>{


home.innerHTML += `

<label>

<input type="checkbox"
class="homeChoice"
value="${team}">

${team}

</label>`;


away.innerHTML += `

<label>

<input type="checkbox"
class="awayChoice"
value="${team}">

${team}

</label>`;



});


}





/* FARBKONTRAST */


function colorDistance(a,b){


let c1=parseInt(a.replace("#",""),16);

let c2=parseInt(b.replace("#",""),16);


let r1=(c1>>16)&255;
let g1=(c1>>8)&255;
let b1=c1&255;


let r2=(c2>>16)&255;
let g2=(c2>>8)&255;
let b2=c2&255;



return Math.sqrt(

(r1-r2)**2+
(g1-g2)**2+
(b1-b2)**2

);


}






function setTeams(){


let home=document.querySelector(".homeChoice:checked");

let away=document.querySelector(".awayChoice:checked");



if(!home || !away){

return;

}



let homeColor=teams[home.value];

let awayColor=teams[away.value];




// gleiche Farben

if(colorDistance(homeColor,awayColor)<80){


awayColor="#777777";


}





document.documentElement.style
.setProperty(
"--home-color",
homeColor
);



document.documentElement.style
.setProperty(
"--away-color",
awayColor
);



document.getElementById("homeName")
.innerHTML=home.value;


document.getElementById("awayName")
.innerHTML=away.value;



}




document.addEventListener(
"change",
function(e){


if(
e.target.classList.contains("homeChoice")
||
e.target.classList.contains("awayChoice")
){

setTeams();

}


});






createTeams();









/* STATISTIK AUSLESEN */


function findNumbers(text,name){


let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let index=lines.findIndex(
x=>x.toLowerCase()
.includes(name.toLowerCase())
);



if(index<0){

return [0,0];

}



let values=[];




for(let i=index-1;i>=0;i--){


let m=lines[i].match(/\d+([.,]\d+)?/);


if(m){

values.unshift(
Number(m[0].replace(",","."))
);

break;

}


}





for(let i=index+1;i<lines.length;i++){


let m=lines[i].match(/\d+([.,]\d+)?/);


if(m){

values.push(
Number(m[0].replace(",","."))
);

break;

}


}



return values.length===2 ? values : [0,0];

}







function set(id,value){

document.getElementById(id).innerHTML=value;

}








function updateBar(a,b,left,right){


let total=a+b;


if(total<=0)return;


document.getElementById(left).style.width=
(a/total*100)+"%";


document.getElementById(right).style.width=
(b/total*100)+"%";


}








function updateData(){


let text=document
.getElementById("dataInput")
.value;



if(!text.trim()){

alert("Bitte Daten einfügen");

return;

}






let xg=findNumbers(
text,
"Expected Goals"
);



set("xgHome",xg[0].toFixed(2));

set("xgAway",xg[1].toFixed(2));


updateBar(
xg[0],
xg[1],
"xgHomeBar",
"xgAwayBar"
);







let pos=findNumbers(
text,
"Ballbesitz"
);



set("posHome",pos[0]+"%");

set("posAway",pos[1]+"%");



document.getElementById("posHomeBar")
.style.width=pos[0]+"%";


document.getElementById("posAwayBar")
.style.width=pos[1]+"%";







let shots=findNumbers(
text,
"Schüsse insgesamt"
);


set("shotsHome",shots[0]);

set("shotsAway",shots[1]);








let target=findNumbers(
text,
"Schüsse aufs Tor"
);


set("targetHome",target[0]);

set("targetAway",target[1]);








let chance=findNumbers(
text,
"Großchance"
);


set("chanceHome",chance[0]);

set("chanceAway",chance[1]);








let corner=findNumbers(
text,
"Eckbälle"
);


set("cornerHome",corner[0]);

set("cornerAway",corner[1]);








let cards=findNumbers(
text,
"Gelbe Karten"
);


set("cardHome",cards[0]);

set("cardAway",cards[1]);







let pass=text.match(
/(\d+)%\s*\((\d+)\/(\d+)\)[\s\S]*?(\d+)%\s*\((\d+)\/(\d+)\)/
);



if(pass){


set(
"passHome",
pass[1]+"%"
);


set(
"passAway",
pass[4]+"%"
);



set(
"passTotalHome",
pass[2]+"/"+pass[3]
);



set(
"passTotalAway",
pass[5]+"/"+pass[6]
);



}





localStorage.setItem(
"liveStats",
text
);



}







window.onload=function(){


let saved=
localStorage.getItem("liveStats");



if(saved){

document.getElementById("dataInput").value=saved;

updateData();

}


}



</script>


</div>


</div>


</body>

</html>
