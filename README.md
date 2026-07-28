<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro V3</title>


<style>

*{
    box-sizing:border-box;
    font-family:Arial, Helvetica, sans-serif;
}


body{

    margin:0;
    height:100vh;
    background:transparent;
    color:white;

}



.overlay{

    width:950px;

    margin:60px auto;

    background:rgba(5,15,35,.96);

    border-radius:18px;

    padding:25px;

    border:1px solid rgba(255,255,255,.15);

    box-shadow:0 0 40px rgba(0,0,0,.8);

}



/* SCORE */


.scoreboard{

    display:flex;

    justify-content:space-between;

    align-items:center;

    padding-bottom:20px;

    border-bottom:2px solid #26354d;

}



.team{

    width:35%;

    text-align:center;

}



.team-name{

    font-size:30px;

    font-weight:800;

}



.score{

    font-size:65px;

    font-weight:900;

}



.timer{

    font-size:28px;

    font-weight:bold;

    color:#00c8ff;

}



/* STATISTIK */


.stats{

    margin-top:25px;

}



.stat{

    margin-bottom:25px;

}



.stat-title{

    text-align:center;

    font-size:22px;

    font-weight:bold;

    margin-bottom:8px;

}



.values{

    display:flex;

    justify-content:space-between;

    font-size:22px;

    font-weight:bold;

    margin-bottom:8px;

}



.home{

    color:#00b7ff;

}



.away{

    color:#ff4757;

}



.bar{

    height:18px;

    background:#17243b;

    display:flex;

    border-radius:20px;

    overflow:hidden;

}



.home-bar{

    background:#00b7ff;

}



.away-bar{

    background:#ff4757;

}





/* ZAHLEN */


.grid{

    display:grid;

    grid-template-columns:repeat(4,1fr);

    gap:15px;

    margin-top:25px;

}



.box{

    background:#101d35;

    padding:15px;

    text-align:center;

    border-radius:12px;

}



.label{

    font-size:13px;

    opacity:.7;

}



.number{

    font-size:30px;

    font-weight:bold;

}






/* DATENQUELLE */


.source-box{

    margin-top:30px;

    background:#0c1930;

    padding:20px;

    border-radius:15px;

}



.source-box label{

    display:block;

    margin-bottom:8px;

}



.source-box input{

    width:100%;

    padding:12px;

    background:#071326;

    border:none;

    border-radius:8px;

    color:white;

    font-size:16px;

}



button{

    width:100%;

    margin-top:15px;

    padding:14px;

    background:#00b7ff;

    color:white;

    border:none;

    border-radius:8px;

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

<div class="team-name">

HEIMTEAM

</div>


<div class="score">

0

</div>


</div>




<div class="timer">

00:00

</div>




<div class="team">

<div class="team-name">

AUSWÄRTS

</div>


<div class="score">

0

</div>


</div>



</div>






<!-- STATISTIK -->


<div class="stats">



<!-- xG -->


<div class="stat">


<div class="stat-title">

Expected Goals (xG)

</div>



<div class="values">


<span class="home" id="xgHomeValue">

0.00

</span>


<span class="away" id="xgAwayValue">

0.00

</span>


</div>



<div class="bar">


<div class="home-bar" id="xgHomeBar" style="width:50%"></div>


<div class="away-bar" id="xgAwayBar" style="width:50%"></div>


</div>


</div>







<!-- BALLBESITZ -->


<div class="stat">


<div class="stat-title">

Ballbesitz

</div>



<div class="values">


<span class="home" id="posHomeValue">

50%

</span>


<span class="away" id="posAwayValue">

50%

</span>


</div>




<div class="bar">


<div class="home-bar" id="posHomeBar" style="width:50%"></div>


<div class="away-bar" id="posAwayBar" style="width:50%"></div>


</div>


</div>








<!-- ZAHLEN -->


<div class="grid">



<div class="box">

<div class="label">

SCHÜSSE

</div>


<div class="number">

<span class="home" id="shotsHome">

0

</span>

:

<span class="away" id="shotsAway">

0

</span>


</div>


</div>






<div class="box">

<div class="label">

TORSCHÜSSE

</div>


<div class="number">


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

<div class="label">

ECKEN

</div>


<div class="number">


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

<div class="label">

KARTEN

</div>


<div class="number">


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






<!-- DATENLINK -->


<div class="source-box">


<label>

Datenquelle / API-Link

</label>


<input id="dataURL" placeholder="https://deine-datenquelle.de/live.json">



<button onclick="loadData()">

AKTUALISIEREN

</button>


</div>



</div>

<script>


async function loadData(){


let url = document.getElementById("dataURL").value;



if(!url){

alert("Bitte zuerst einen Daten-Link eingeben!");

return;

}



try{


let response = await fetch(url);


let data = await response.json();





// SPIELINFO


document.querySelectorAll(".team-name")[0].innerHTML =
data.homeTeam || "HEIMTEAM";


document.querySelectorAll(".team-name")[1].innerHTML =
data.awayTeam || "AUSWÄRTS";



document.querySelectorAll(".score")[0].innerHTML =
data.homeScore ?? 0;



document.querySelectorAll(".score")[1].innerHTML =
data.awayScore ?? 0;



document.querySelector(".timer").innerHTML =
data.time || "00:00";







// xG


let xgHome = Number(data.xgHome || 0);

let xgAway = Number(data.xgAway || 0);



document.getElementById("xgHomeValue").innerHTML =
xgHome.toFixed(2);



document.getElementById("xgAwayValue").innerHTML =
xgAway.toFixed(2);





let xgTotal = xgHome + xgAway;


if(xgTotal > 0){


document.getElementById("xgHomeBar").style.width =
(xgHome / xgTotal * 100) + "%";


document.getElementById("xgAwayBar").style.width =
(xgAway / xgTotal * 100) + "%";


}









// BALLBESITZ


let posHome = Number(data.posHome || 50);

let posAway = Number(data.posAway || 50);



document.getElementById("posHomeValue").innerHTML =
posHome + "%";


document.getElementById("posAwayValue").innerHTML =
posAway + "%";



document.getElementById("posHomeBar").style.width =
posHome + "%";


document.getElementById("posAwayBar").style.width =
posAway + "%";









// STATISTIKEN



document.getElementById("shotsHome").innerHTML =
data.shotsHome || 0;


document.getElementById("shotsAway").innerHTML =
data.shotsAway || 0;




document.getElementById("targetHome").innerHTML =
data.targetHome || 0;


document.getElementById("targetAway").innerHTML =
data.targetAway || 0;





document.getElementById("cornerHome").innerHTML =
data.cornersHome || 0;


document.getElementById("cornerAway").innerHTML =
data.cornersAway || 0;





document.getElementById("cardHome").innerHTML =
data.cardsHome || 0;


document.getElementById("cardAway").innerHTML =
data.cardsAway || 0;





localStorage.setItem(
"dataURL",
url
);



}

catch(error){


alert(
"Fehler beim Laden der Daten: " + error
);


}



}






window.onload=function(){


let saved =
localStorage.getItem("dataURL");


if(saved){

document.getElementById("dataURL").value=saved;

}


}


</script>
</body>

</html>
