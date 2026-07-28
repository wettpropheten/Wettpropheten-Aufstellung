<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro V6</title>

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

font-size:70px;

font-weight:900;

}



.timer{

font-size:30px;

font-weight:bold;

color:#00c8ff;

}



.stat{

margin-top:25px;

}



.stat-title{

text-align:center;

font-size:22px;

font-weight:bold;

}



.values{

display:flex;

justify-content:space-between;

font-size:24px;

font-weight:bold;

margin:10px;

}



.home{

color:#00b7ff;

}


.away{

color:#ff4757;

}



.bar{

height:18px;

background:#18263d;

border-radius:20px;

overflow:hidden;

display:flex;

}



.home-bar{

background:#00b7ff;

height:100%;

}



.away-bar{

background:#ff4757;

height:100%;

}



.grid{

display:grid;

grid-template-columns:repeat(4,1fr);

gap:15px;

margin-top:30px;

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



.input{

margin-top:30px;

background:#0c1930;

padding:20px;

border-radius:15px;

}



textarea{

width:100%;

height:220px;

background:#071326;

color:white;

border:none;

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

font-size:18px;

font-weight:bold;

color:white;

}



</style>

</head>


<body>


<div class="overlay">


<div class="scoreboard">


<div class="team">

<div class="team-name">
HEIMTEAM
</div>

<div class="score" id="homeScore">
0
</div>

</div>



<div class="timer" id="time">
00:00
</div>



<div class="team">

<div class="team-name">
AUSWÄRTS
</div>

<div class="score" id="awayScore">
0
</div>

</div>


</div>
<!-- STATISTIK BEREICH -->


<div class="stat">


<div class="stat-title">
Expected Goals (xG)
</div>


<div class="values">

<span class="home" id="xgHome">
0.00
</span>


<span class="away" id="xgAway">
0.00
</span>


</div>



<div class="bar">

<div class="home-bar" id="xgBarHome" style="width:50%"></div>

<div class="away-bar" id="xgBarAway" style="width:50%"></div>

</div>


</div>






<div class="stat">


<div class="stat-title">
Ballbesitz
</div>


<div class="values">

<span class="home" id="posHome">
50%
</span>


<span class="away" id="posAway">
50%
</span>


</div>


<div class="bar">

<div class="home-bar" id="posBarHome" style="width:50%"></div>

<div class="away-bar" id="posBarAway" style="width:50%"></div>

</div>


</div>






<div class="grid">



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
SCHÜSSE NEBEN TOR
</div>

<div class="box-value">

<span class="home" id="offHome">0</span>

:

<span class="away" id="offAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
GEBLOCKTE SCHÜSSE
</div>

<div class="box-value">

<span class="home" id="blockHome">0</span>

:

<span class="away" id="blockAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
ECKEN
</div>

<div class="box-value">

<span class="home" id="cornerHome">0</span>

:

<span class="away" id="cornerAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
ABSEITS
</div>

<div class="box-value">

<span class="home" id="offsideHome">0</span>

:

<span class="away" id="offsideAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
FOULS
</div>

<div class="box-value">

<span class="home" id="foulHome">0</span>

:

<span class="away" id="foulAway">0</span>

</div>

</div>





<div class="box">

<div class="box-title">
EINWÜRFE
</div>

<div class="box-value">

<span class="home" id="throwHome">0</span>

:

<span class="away" id="throwAway">0</span>

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






<div class="input">


<h2>
LIVE DATEN EINGEBEN
</h2>


<textarea id="dataInput" placeholder="Statistik hier einfügen..."></textarea>


<button onclick="updateData()">
AKTUALISIEREN
</button>


</div>
<script>


function findValue(text,name){


let lines=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x!="");



let index=lines.findIndex(
x=>x.toLowerCase().includes(name.toLowerCase())
);



if(index===-1){

return [0,0];

}



let nums=[];



// sucht Zahlen vor dem Titel

for(let i=index-1;i>=0;i--){

let n=lines[i].match(/\d+(\.\d+)?/);

if(n){

nums.unshift(Number(n[0]));

break;

}

}




// sucht Zahlen nach dem Titel

for(let i=index+1;i<lines.length;i++){


let n=lines[i].match(/\d+(\.\d+)?/);


if(n){

nums.push(Number(n[0]));

break;

}


}




if(nums.length<2){

return [0,0];

}



return nums;


}





function put(id,value){

document.getElementById(id).innerHTML=value;

}






function updateData(){


let text=document.getElementById("dataInput").value;



if(text.trim()==""){

alert("Bitte Daten einfügen");

return;

}






// BALLBESITZ


let pos=findValue(text,"Ballbesitz");


put("posHome",pos[0]+"%");
put("posAway",pos[1]+"%");



document.getElementById("posBarHome").style.width=
pos[0]+"%";


document.getElementById("posBarAway").style.width=
pos[1]+"%";








// SCHÜSSE AUFS TOR


let target=findValue(text,"Schüsse aufs Tor");


put("targetHome",target[0]);
put("targetAway",target[1]);







// NEBEN TOR


let off=findValue(text,"Schüsse neben");


put("offHome",off[0]);
put("offAway",off[1]);







// GEBLOCKT


let block=findValue(text,"Geblockte Schüsse");


put("blockHome",block[0]);
put("blockAway",block[1]);







// ECKEN


let corner=findValue(text,"Ecken");


put("cornerHome",corner[0]);
put("cornerAway",corner[1]);







// ABSEITS


let offside=findValue(text,"Abseitsstellungen");


put("offsideHome",offside[0]);
put("offsideAway",offside[1]);







// FOULS


let foul=findValue(text,"Fouls");


put("foulHome",foul[0]);
put("foulAway",foul[1]);







// EINWÜRFE


let throwin=findValue(text,"Einwürfe");


put("throwHome",throwin[0]);
put("throwAway",throwin[1]);







// GELBE KARTEN


let cards=findValue(text,"Gelbe Karten");


put("cardHome",cards[0]);
put("cardAway",cards[1]);






localStorage.setItem(
"stats",
text
);



}







window.onload=function(){


let saved=localStorage.getItem("stats");


if(saved){


document.getElementById("dataInput").value=saved;


updateData();


}


}


</script>
</div>
</body>
</html>
