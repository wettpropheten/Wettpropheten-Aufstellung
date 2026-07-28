<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro</title>


<style>


*{
box-sizing:border-box;
font-family:Arial, Helvetica, sans-serif;
}


body{

margin:0;

background:
linear-gradient(
135deg,
#061326,
#12345f
);

color:white;

min-height:100vh;

}



.container{

width:95%;

max-width:1000px;

margin:auto;

padding:30px 0;

}



/* TITEL */


.header{

text-align:center;

margin-bottom:30px;

}


.header h1{

font-size:40px;

margin:0;

}


.header p{

opacity:.8;

font-size:18px;

}





/* IMPORT */


.import-panel{


background:#0d2347;

padding:25px;

border-radius:18px;

box-shadow:
0 10px 30px rgba(0,0,0,.5);

margin-bottom:30px;


}



.import-panel h2{

margin-top:0;

}



textarea{


width:100%;

height:260px;

background:#071529;

color:white;

border:none;

border-radius:12px;

padding:15px;

font-size:15px;

resize:vertical;


}



button{


width:100%;

margin-top:20px;

padding:15px;


border:none;

border-radius:12px;


background:#2196f3;

color:white;


font-size:18px;

font-weight:bold;


cursor:pointer;


}




button:hover{

background:#42a5f5;

}




/* SPIEL */


.match-card{


background:#0d2347;

border-radius:18px;

padding:25px;

margin-bottom:30px;


}



.teams{


display:flex;

justify-content:space-between;

align-items:center;

text-align:center;


}



.team{

width:40%;

}



.team h2{

font-size:24px;

}



.score{

font-size:45px;

font-weight:bold;

}



.vs{

font-size:20px;

opacity:.7;

}




/* STATISTIK */


.stats-box{


background:#0d2347;

padding:25px;

border-radius:18px;

margin-bottom:30px;


}



.stat{


margin-bottom:25px;


}



.stat-title{


display:flex;

justify-content:space-between;

font-size:18px;

font-weight:bold;

margin-bottom:10px;


}



.bar{


height:16px;

background:#243957;

border-radius:20px;

overflow:hidden;

display:flex;


}



.home-bar{


background:#2196f3;

width:50%;

transition:1s;


}



.away-bar{


background:#ff5252;

width:50%;

transition:1s;


}





/* KLEINE KARTEN */


.cards{


display:grid;

grid-template-columns:
repeat(auto-fit,minmax(180px,1fr));


gap:15px;


}



.card{


background:#0d2347;

border-radius:15px;

padding:20px;

text-align:center;


}



.card h3{

margin:0;

font-size:15px;

opacity:.8;

}



.card span{


display:block;

font-size:28px;

font-weight:bold;

margin-top:10px;


}






@media(max-width:600px){


.header h1{

font-size:30px;

}


.score{

font-size:35px;

}


}



</style>


</head>



<body>



<div class="container">



<div class="header">


<h1>⚽ LiveStats Pro</h1>

<p>Automatische Fußball Statistik Analyse</p>


</div>





<div class="import-panel">


<h2>
📋 Statistik einfügen
</h2>


<textarea id="rawStats"
placeholder="Hier Statistik einfügen...

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

1
Großchance
2

3
Eckbälle
4

0
Gelbe Karten
1

"></textarea>



<button onclick="readStats()">

Statistik auslesen

</button>


</div>









<div class="match-card">


<div class="teams">


<div class="team">

<h2>
Heimteam
</h2>


<div class="score">

0

</div>


</div>



<div class="vs">

VS

</div>




<div class="team">

<h2>
Auswärtsteam
</h2>


<div class="score">

0

</div>


</div>



</div>


</div>









<div class="stats-box">


<h2>
📊 Spielstatistik
</h2>




<div class="stat">


<div class="stat-title">

<span>
Expected Goals (xG)
</span>


<span>

0.00 - 0.00

</span>


</div>


<div class="bar">


<div class="home-bar"></div>

<div class="away-bar"></div>


</div>


</div>








<div class="stat">


<div class="stat-title">


<span>
Ballbesitz
</span>


<span>

0% - 0%

</span>


</div>


<div class="bar">


<div class="home-bar"></div>

<div class="away-bar"></div>


</div>


</div>




</div>









<div class="cards">


<div class="card">

<h3>
Schüsse
</h3>

<span>
0 - 0
</span>

</div>




<div class="card">

<h3>
Schüsse aufs Tor
</h3>

<span>
0 - 0
</span>

</div>




<div class="card">

<h3>
Großchancen
</h3>

<span>
0 - 0
</span>

</div>




<div class="card">

<h3>
Eckbälle
</h3>

<span>
0 - 0
</span>

</div>




<div class="card">

<h3>
Gelbe Karten
</h3>

<span>
0 - 0
</span>

</div>



</div>






</div>







<script>


function readStats(){


alert("Automatischer Import kommt in Teil 3");


}

/* ==========================
   LIVE SOFASCORE BALKEN
========================== */


.live-title{

display:flex;

justify-content:space-between;

align-items:center;

font-size:18px;

font-weight:bold;

margin-bottom:12px;

}



.live-values{

display:flex;

gap:35px;

}



.live-bar{

height:20px;

width:100%;

background:#182c48;

border-radius:20px;

overflow:hidden;

display:flex;

}



.live-home{

height:100%;

background:#2196f3;

width:50%;

transition:
width 1.5s ease;


}



.live-away{

height:100%;

background:#ff5252;

width:50%;

transition:
width 1.5s ease;


}



.stat-box-live{


background:#081a35;

padding:20px;

border-radius:15px;

margin-top:20px;


}



.stat-box-live h3{

margin-top:0;

}




.number-animation{


animation:
numberPop .5s ease;


}



@keyframes numberPop{


0%{

transform:scale(.7);

opacity:0;

}


100%{

transform:scale(1);

opacity:1;

}


}
<script>


const stats = {};



function cleanNumber(value){

    if(!value) return "";

    return value
    .replace(",",".")
    .trim();

}




function valueBefore(lines,index){

    return lines[index-1] || "";

}



function valueAfter(lines,index){

    return lines[index+1] || "";

}






function readStats(){



let text=document
.getElementById("rawStats")
.value;



let lines=text
.split(/\r?\n/)
.map(x=>x.trim())
.filter(x=>x!="");



lines.forEach((line,index)=>{


switch(line){



case "Expected Goals (xG)":


stats.xgHome=
cleanNumber(valueBefore(lines,index));


stats.xgAway=
cleanNumber(valueAfter(lines,index));


break;






case "Ballbesitz":


stats.posHome=
valueBefore(lines,index);


stats.posAway=
valueAfter(lines,index);


break;







case "Schüsse insgesamt":


stats.shotsHome=
valueBefore(lines,index);


stats.shotsAway=
valueAfter(lines,index);


break;







case "Schüsse aufs Tor":


stats.targetHome=
valueBefore(lines,index);


stats.targetAway=
valueAfter(lines,index);


break;







case "Großchance":


stats.bigHome=
valueBefore(lines,index);


stats.bigAway=
valueAfter(lines,index);


break;







case "Eckbälle":


stats.cornerHome=
valueBefore(lines,index);


stats.cornerAway=
valueAfter(lines,index);


break;







case "Gelbe Karten":


stats.yellowHome=
valueBefore(lines,index);


stats.yellowAway=
valueAfter(lines,index);


break;




}



});



updateStats();


}








function updateStats(){



console.log(stats);





// xG


if(stats.xgHome){


document
.getElementById("xgHome")
.innerHTML=
stats.xgHome;



document
.getElementById("xgAway")
.innerHTML=
stats.xgAway;




updateBar(
"xgHomeBar",
"xgAwayBar",
parseFloat(stats.xgHome),
parseFloat(stats.xgAway)
);



}







// Ballbesitz


if(stats.posHome){


document
.getElementById("posHome")
.innerHTML=
stats.posHome;



document
.getElementById("posAway")
.innerHTML=
stats.posAway;




let home=
parseInt(stats.posHome);


let away=
parseInt(stats.posAway);



document
.getElementById("posHomeBar")
.style.width=
home+"%";



document
.getElementById("posAwayBar")
.style.width=
away+"%";


}







}




function updateBar(homeID,awayID,home,away){



let total=
home+away;



if(total===0)
return;



let homePercent=
(home/total)*100;


let awayPercent=
(away/total)*100;



document
.getElementById(homeID)
.style.width=
homePercent+"%";



document
.getElementById(awayID)
.style.width=
awayPercent+"%";



}
function updateStats(){



console.log(stats);





if(stats.xgHome){


document.getElementById("xgHome").innerHTML=
stats.xgHome;


document.getElementById("xgAway").innerHTML=
stats.xgAway;



updateBar(
"xgHomeBar",
"xgAwayBar",
parseFloat(stats.xgHome),
parseFloat(stats.xgAway)
);


}







if(stats.posHome){


document.getElementById("posHome").innerHTML=
stats.posHome;


document.getElementById("posAway").innerHTML=
stats.posAway;



document.getElementById("posHomeBar").style.width=
parseInt(stats.posHome)+"%";


document.getElementById("posAwayBar").style.width=
parseInt(stats.posAway)+"%";


}







if(stats.shotsHome){


document.getElementById("shots").innerHTML=

stats.shotsHome
+
" - "
+
stats.shotsAway;


}






if(stats.targetHome){


document.getElementById("target").innerHTML=

stats.targetHome
+
" - "
+
stats.targetAway;


}






if(stats.bigHome){


document.getElementById("big").innerHTML=

stats.bigHome
+
" - "
+
stats.bigAway;


}






if(stats.cornerHome){


document.getElementById("corner").innerHTML=

stats.cornerHome
+
" - "
+
stats.cornerAway;


}







if(stats.yellowHome){


document.getElementById("yellow").innerHTML=

stats.yellowHome
+
" - "
+
stats.yellowAway;


}



saveStats();


}







function saveStats(){


localStorage.setItem(
"LiveStats",
JSON.stringify(stats)
);


}







function loadStats(){


let saved=
localStorage.getItem("LiveStats");



if(saved){


Object.assign(
stats,
JSON.parse(saved)
);


updateStats();


}


}







function resetStats(){


localStorage.removeItem(
"LiveStats"
);


location.reload();


}






window.onload=function(){


loadStats();


}

</script>




</body>

</html>
