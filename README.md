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

background:transparent;

color:white;

}



.overlay{

width:1100px;

margin:30px auto;

background:rgba(5,15,35,.96);

border-radius:20px;

padding:30px;

box-shadow:0 0 50px black;

}





/* MANNSCHAFT AUSWAHL */


.team-select{

background:#0c1930;

padding:20px;

border-radius:15px;

margin-bottom:25px;

}



.team-select h2{

text-align:center;

margin-top:0;

}



.team-columns{

display:grid;

grid-template-columns:1fr 1fr;

gap:25px;

}



.team-list{

background:#101d35;

padding:15px;

border-radius:12px;

height:300px;

overflow-y:auto;

}



.team-list h3{

text-align:center;

}



.team-list label{

display:block;

background:#071326;

padding:8px;

margin:5px 0;

border-radius:8px;

cursor:pointer;

}



.team-list input{

transform:scale(1.3);

margin-right:10px;

}





/* SPIELANZEIGE */


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

font-size:32px;

font-weight:900;

}



.score{

font-size:70px;

font-weight:900;

color:var(--home-color);

}



.away-score{

color:var(--away-color);

}



.timer{

font-size:30px;

font-weight:bold;

}





/* STATISTIK BALKEN */


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



.value-left,
.value-right{

position:absolute;

top:0;

font-size:24px;

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

height:18px;

background:#000000;

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
<style>

/* STATISTIK BOXEN */

.grid{

display:grid;

grid-template-columns:repeat(3,1fr);

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

font-size:28px;

font-weight:bold;

}



.home{

color:var(--home-color);

}



.away{

color:var(--away-color);

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

height:250px;

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





<!-- MANNSCHAFT AUSWAHL -->


<div class="team-select">

<h2>
HEIM / AUSWÄRTS AUSWAHL
</h2>


<div class="team-columns">


<div class="team-list">

<h3>HEIMMANNSCHAFT</h3>


<div id="homeTeams"></div>


</div>





<div class="team-list">

<h3>AUSWÄRTSMANNSCHAFT</h3>


<div id="awayTeams"></div>


</div>


</div>

</div>





<!-- SPIELSTAND -->


<div class="scoreboard">


<div class="team">


<div class="team-name" id="homeName">
HEIMTEAM
</div>


<div class="score" id="homeScore">
0
</div>


</div>





<div class="timer">
00:00
</div>





<div class="team">


<div class="team-name" id="awayName">
AUSWÄRTS
</div>


<div class="score away-score" id="awayScore">
0
</div>


</div>


</div>






<script>


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
"1. FC Union Berlin":"#EB0016",
"Borussia Mönchengladbach":"#FFFFFF"

};





function createTeamLists(){


let home=document.getElementById("homeTeams");

let away=document.getElementById("awayTeams");



Object.keys(teams).forEach(team=>{


home.innerHTML+=`

<label>

<input type="checkbox" 
class="homeChoice"
value="${team}">

${team}

</label>`;


away.innerHTML+=`

<label>

<input type="checkbox" 
class="awayChoice"
value="${team}">

${team}

</label>`;



});



}



createTeamLists();







function colorDifference(c1,c2){


let a=parseInt(c1.substring(1),16);

let b=parseInt(c2.substring(1),16);



let r1=a>>16;
let g1=(a>>8)&255;
let b1=a&255;


let r2=b>>16;
let g2=(b>>8)&255;
let b2=b&255;



return Math.sqrt(

(r1-r2)**2+
(g1-g2)**2+
(b1-b2)**2

);


}








function setTeams(){


let home=document.querySelector(
".homeChoice:checked"
);


let away=document.querySelector(
".awayChoice:checked"
);



if(!home || !away){

return;

}



let homeColor=teams[home.value];

let awayColor=teams[away.value];




// gleiche Farben erkennen


if(
colorDifference(homeColor,awayColor)<90
){


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



</script>
<!-- STATISTIK -->


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





<!-- BOXEN -->


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

<span class="home" id="passTotalHome">0/0</span>
:
<span class="away" id="passTotalAway">0/0</span>

</div>

</div>





<div class="box">

<div class="box-title">
GELBE KARTEN
</div>

<div class="box-value">

<span class="home" id="cardHome">0</span>
:
<span class="away" id="cardAway">0</span>

</div>

</div>


</div>







<!-- DATEN EINGABE -->


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






<script>



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







function updateBar(home,away,left,right){


let total=home+away;


if(total<=0)return;


document.getElementById(left)
.style.width=(home/total*100)+"%";


document.getElementById(right)
.style.width=(away/total*100)+"%";


}







function updateData(){


let text=
document.getElementById("dataInput").value;



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


set("passHome",pass[1]+"%");
set("passAway",pass[4]+"%");


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


let save=
localStorage.getItem("liveStats");


if(save){

document.getElementById("dataInput").value=save;

updateData();

}


}



</script>


</div>


</body>

</html>
