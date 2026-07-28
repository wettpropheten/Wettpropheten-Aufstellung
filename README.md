<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>LiveStats Pro V2</title>


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
    overflow:hidden;

}



/* HAUPT OVERLAY */

.overlay{

    width:1000px;

    margin:60px auto;

    background:rgba(5,15,35,0.95);

    border-radius:20px;

    padding:30px;

    border:1px solid rgba(255,255,255,.15);

    box-shadow:0 0 40px rgba(0,0,0,.8);

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

    font-size:32px;

    font-weight:bold;

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



.home-color{

    color:#00b7ff;

}


.away-color{

    color:#ff4757;

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


<!-- STATISTIK BEREICH -->


<style>

.stats{

    margin-top:25px;

}



.stat-row{

    margin-bottom:22px;

}



.stat-header{

    display:flex;

    justify-content:space-between;

    font-size:20px;

    font-weight:bold;

}



.bar{

    height:18px;

    margin-top:8px;

    background:#18263d;

    border-radius:20px;

    overflow:hidden;

    display:flex;

}



.bar-home{

    height:100%;

    background:#00b7ff;

}



.bar-away{

    height:100%;

    background:#ff4757;

}





.stats-grid{

    margin-top:30px;

    display:grid;

    grid-template-columns:repeat(4,1fr);

    gap:15px;

}



.box{

    background:#101d35;

    padding:15px;

    border-radius:12px;

    text-align:center;

}



.box-title{

    font-size:13px;

    opacity:.7;

}



.box-value{

    font-size:32px;

    font-weight:bold;

    margin-top:10px;

}



</style>





<div class="stats">





<!-- xG -->


<div class="stat-row">


<div class="stat-header">

<span>Expected Goals (xG)</span>


<span>

<b class="home-color">1.24</b>

:

<b class="away-color">0.80</b>

</span>


</div>



<div class="bar">

<div class="bar-home" style="width:60%"></div>

<div class="bar-away" style="width:40%"></div>

</div>


</div>







<!-- BALLBESITZ -->


<div class="stat-row">


<div class="stat-header">

<span>Ballbesitz</span>


<span>

<b class="home-color">50%</b>

:

<b class="away-color">50%</b>

</span>


</div>



<div class="bar">


<div class="bar-home" style="width:50%"></div>


<div class="bar-away" style="width:50%"></div>


</div>


</div>







<!-- STATISTIK ZAHLEN -->


<div class="stats-grid">



<div class="box">

<div class="box-title">
SCHÜSSE
</div>

<div class="box-value">

<span class="home-color">10</span>
:
<span class="away-color">12</span>

</div>

</div>





<div class="box">

<div class="box-title">
TORSCHÜSSE
</div>

<div class="box-value">

<span class="home-color">3</span>
:
<span class="away-color">5</span>

</div>

</div>





<div class="box">

<div class="box-title">
ECKEN
</div>

<div class="box-value">

<span class="home-color">3</span>
:
<span class="away-color">4</span>

</div>

</div>





<div class="box">

<div class="box-title">
KARTEN
</div>

<div class="box-value">

<span class="home-color">0</span>
:
<span class="away-color">1</span>

</div>

</div>



</div>
<!-- STATISTIK BEREICH -->


<style>

.stats{

    margin-top:25px;

}



.stat-row{

    margin-bottom:22px;

}



.stat-header{

    display:flex;

    justify-content:space-between;

    font-size:20px;

    font-weight:bold;

}



.bar{

    height:18px;

    margin-top:8px;

    background:#18263d;

    border-radius:20px;

    overflow:hidden;

    display:flex;

}



.bar-home{

    height:100%;

    background:#00b7ff;

}



.bar-away{

    height:100%;

    background:#ff4757;

}





.stats-grid{

    margin-top:30px;

    display:grid;

    grid-template-columns:repeat(4,1fr);

    gap:15px;

}



.box{

    background:#101d35;

    padding:15px;

    border-radius:12px;

    text-align:center;

}



.box-title{

    font-size:13px;

    opacity:.7;

}



.box-value{

    font-size:32px;

    font-weight:bold;

    margin-top:10px;

}



</style>





<div class="stats">





<!-- xG -->


<div class="stat-row">


<div class="stat-header">

<span>Expected Goals (xG)</span>


<span>

<b class="home-color">1.24</b>

:

<b class="away-color">0.80</b>

</span>


</div>



<div class="bar">

<div class="bar-home" style="width:60%"></div>

<div class="bar-away" style="width:40%"></div>

</div>


</div>







<!-- BALLBESITZ -->


<div class="stat-row">


<div class="stat-header">

<span>Ballbesitz</span>


<span>

<b class="home-color">50%</b>

:

<b class="away-color">50%</b>

</span>


</div>



<div class="bar">


<div class="bar-home" style="width:50%"></div>


<div class="bar-away" style="width:50%"></div>


</div>


</div>







<!-- STATISTIK ZAHLEN -->


<div class="stats-grid">



<div class="box">

<div class="box-title">
SCHÜSSE
</div>

<div class="box-value">

<span class="home-color">10</span>
:
<span class="away-color">12</span>

</div>

</div>





<div class="box">

<div class="box-title">
TORSCHÜSSE
</div>

<div class="box-value">

<span class="home-color">3</span>
:
<span class="away-color">5</span>

</div>

</div>





<div class="box">

<div class="box-title">
ECKEN
</div>

<div class="box-value">

<span class="home-color">3</span>
:
<span class="away-color">4</span>

</div>

</div>





<div class="box">

<div class="box-title">
KARTEN
</div>

<div class="box-value">

<span class="home-color">0</span>
:
<span class="away-color">1</span>

</div>

</div>



</div>

</div>

<script>


function updateGame(){


let homeName =
document.getElementById("homeInput").value;


let awayName =
document.getElementById("awayInput").value;


let time =
document.getElementById("timeInput").value;


let homeScore =
document.getElementById("homeScoreInput").value;


let awayScore =
document.getElementById("awayScoreInput").value;



let teams =
document.querySelectorAll(".team-name");



teams[0].innerHTML = homeName;

teams[1].innerHTML = awayName;




let scores =
document.querySelectorAll(".score");



scores[0].innerHTML = homeScore;

scores[1].innerHTML = awayScore;




document.querySelector(".timer").innerHTML = time;





localStorage.setItem(
"homeName",
homeName
);


localStorage.setItem(
"awayName",
awayName
);


localStorage.setItem(
"homeScore",
homeScore
);


localStorage.setItem(
"awayScore",
awayScore
);


localStorage.setItem(
"time",
time
);



}




window.onload=function(){



if(localStorage.getItem("homeName")){


document.getElementById("homeInput").value =
localStorage.getItem("homeName");


document.getElementById("awayInput").value =
localStorage.getItem("awayName");


document.getElementById("homeScoreInput").value =
localStorage.getItem("homeScore");


document.getElementById("awayScoreInput").value =
localStorage.getItem("awayScore");


document.getElementById("timeInput").value =
localStorage.getItem("time");



updateGame();


}



}



</script>

</body>


</html>
