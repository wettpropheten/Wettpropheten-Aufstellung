<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro Final</title>

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

box-shadow:0 0 50px black;

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

color:#00b7ff;

}



.value-right{

left:75%;

transform:translateX(-50%);

color:#ff4757;

}



.bar{

position:absolute;

bottom:10px;

height:18px;

width:100%;

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




/* BOXEN */


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

font-size:26px;

font-weight:bold;

}



.home{

color:#00b7ff;

}


.away{

color:#ff4757;

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

</head>


<body>


<div class="overlay">



<!-- EXPECTED GOALS -->


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





<!-- BALLBESITZ -->


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





<!-- STATISTIK BOXEN -->


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





<!-- DATENEINGABE -->


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
.filter(x=>x.length>0);



let index=lines.findIndex(
x=>x.toLowerCase().includes(name.toLowerCase())
);



if(index===-1){

return [0,0];

}



let values=[];



// Zahl vor Überschrift

for(let i=index-1;i>=0;i--){


let match=lines[i].match(/\d+([.,]\d+)?/);


if(match){

values.unshift(
Number(match[0].replace(",","."))
);

break;

}

}



// Zahl nach Überschrift

for(let i=index+1;i<lines.length;i++){


let match=lines[i].match(/\d+([.,]\d+)?/);


if(match){

values.push(
Number(match[0].replace(",","."))
);

break;

}

}



if(values.length<2){

return [0,0];

}


return values;


}







function findPassQuote(text){


let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x.length>0);



let index=lines.findIndex(
x=>x.toLowerCase().includes("pässe")
);



if(index===-1){

return [0,0];

}



let result=[];



for(let i=index-1;i>=0;i--){


let match=lines[i].match(/\d+%/);


if(match){

result.unshift(
parseInt(match[0])
);

break;

}

}



for(let i=index+1;i<lines.length;i++){


let match=lines[i].match(/\d+%/);


if(match){

result.push(
parseInt(match[0])
);

break;

}

}



return result.length===2 ? result : [0,0];

}







function findPassTotal(text){


let match=text.match(
/\((\d+)\/(\d+)\).*Pässe.*\((\d+)\/(\d+)\)/s
);



if(!match){

return ["0/0","0/0"];

}



return [

match[1]+"/"+match[2],

match[3]+"/"+match[4]

];


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


let text=document
.getElementById("dataInput")
.value;



if(text.trim()==""){

alert("Bitte Daten einfügen");

return;

}






// XG


let xg=findNumbers(
text,
"Expected Goals"
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









// BALLBESITZ


let pos=findNumbers(
text,
"Ballbesitz"
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









// SCHÜSSE GESAMT


let shots=findNumbers(
text,
"Schüsse insgesamt"
);


setValue(
"shotsHome",
shots[0]
);


setValue(
"shotsAway",
shots[1]
);









// SCHÜSSE AUFS TOR


let target=findNumbers(
text,
"Schüsse aufs Tor"
);


setValue(
"targetHome",
target[0]
);


setValue(
"targetAway",
target[1]
);









// GROSSCHANCEN


let chance=findNumbers(
text,
"Großchance"
);


setValue(
"chanceHome",
chance[0]
);


setValue(
"chanceAway",
chance[1]
);









// ECKBÄLLE


let corner=findNumbers(
text,
"Eckbälle"
);


setValue(
"cornerHome",
corner[0]
);


setValue(
"cornerAway",
corner[1]
);









// PASSQUOTE


let pass=findPassQuote(text);


setValue(
"passHome",
pass[0]+"%"
);


setValue(
"passAway",
pass[1]+"%"
);









// PÄSSE GESAMT


let passTotal=findPassTotal(text);


setValue(
"passTotalHome",
passTotal[0]
);


setValue(
"passTotalAway",
passTotal[1]
);









// GELBE KARTEN


let cards=findNumbers(
text,
"Gelbe Karten"
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


</body>

</html>
