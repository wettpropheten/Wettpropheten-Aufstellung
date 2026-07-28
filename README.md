<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
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

}



.overlay{

    width:1000px;
    margin:50px auto;

    background:rgba(5,15,35,0.96);

    border-radius:20px;

    padding:30px;

    box-shadow:0 0 40px rgba(0,0,0,.8);

}



/* SCOREBOARD */


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
    color:#00c8ff;
    font-weight:bold;

}



/* FARBEN */


.home{

    color:#00b7ff;

}


.away{

    color:#ff4757;

}



/* STATISTIK */


.stats{

    margin-top:25px;

}


.row{

    margin-bottom:20px;

}


.header{

    display:flex;

    justify-content:space-between;

    font-size:20px;

    font-weight:bold;

}



.bar{

    height:18px;

    background:#18263d;

    border-radius:20px;

    display:flex;

    overflow:hidden;

    margin-top:8px;

}



.left{

    background:#00b7ff;

}



.right{

    background:#ff4757;

}



.grid{

    display:grid;

    grid-template-columns:repeat(4,1fr);

    gap:15px;

    margin-top:30px;

}



.card{

    background:#101d35;

    padding:15px;

    border-radius:12px;

    text-align:center;

}



.card-title{

    font-size:13px;

    opacity:.7;

}



.value{

    font-size:32px;

    font-weight:bold;

}



/* STEUERUNG */


.control{

    margin-top:30px;

    background:#0c1930;

    padding:20px;

    border-radius:15px;

}



.control-grid{

    display:grid;

    grid-template-columns:repeat(3,1fr);

    gap:15px;

}



.input-box{

    background:#132542;

    padding:12px;

    border-radius:10px;

}



label{

    display:block;

    font-size:13px;

    opacity:.7;

    margin-bottom:5px;

}



input{

    width:100%;

    padding:10px;

    background:#071326;

    color:white;

    border:none;

    border-radius:8px;

    font-size:18px;

}



button{

    width:100%;

    padding:12px;

    margin-top:22px;

    background:#00b7ff;

    color:white;

    border:none;

    border-radius:8px;

    font-weight:bold;

    cursor:pointer;

}



button:hover{

    opacity:.8;

}


</style>

</head>



<body>


<div class="overlay">



<div class="scoreboard">


<div class="team">

<div class="team-name" id="homeTeam">

HEIMTEAM

</div>


<div class="score" id="homeGoals">

0

</div>

</div>



<div class="timer" id="time">

00:00

</div>



<div class="team">

<div class="team-name" id="awayTeam">

AUSWÄRTS

</div>


<div class="score" id="awayGoals">

0

</div>

</div>



</div>





<div class="stats">


<div class="row">

<div class="header">

<span>xG</span>

<span>
<b class="home">1.24</b>
:
<b class="away">0.80</b>
</span>

</div>


<div class="bar">

<div class="left" style="width:60%"></div>

<div class="right" style="width:40%"></div>

</div>

</div>





<div class="row">

<div class="header">

<span>Ballbesitz</span>

<span>
<b class="home">50%</b>
:
<b class="away">50%</b>
</span>

</div>


<div class="bar">

<div class="left" style="width:50%"></div>

<div class="right" style="width:50%"></div>

</div>

</div>






<div class="grid">


<div class="card">

<div class="card-title">
SCHÜSSE
</div>

<div class="value">

<span class="home">10</span>
:
<span class="away">12</span>

</div>

</div>



<div class="card">

<div class="card-title">
TORSCHÜSSE
</div>

<div class="value">

<span class="home">3</span>
:
<span class="away">5</span>

</div>

</div>




<div class="card">

<div class="card-title">
ECKEN
</div>

<div class="value">

<span class="home">3</span>
:
<span class="away">4</span>

</div>

</div>




<div class="card">

<div class="card-title">
KARTEN
</div>

<div class="value">

<span class="home">0</span>
:
<span class="away">1</span>

</div>

</div>


</div>

</div>







<div class="control">


<h2>
LIVE STEUERUNG
</h2>


<div class="control-grid">



<div class="input-box">

<label>Heimteam</label>

<input id="homeInput" value="HEIMTEAM">

</div>




<div class="input-box">

<label>Auswärtsteam</label>

<input id="awayInput" value="AUSWÄRTS">

</div>




<div class="input-box">

<label>Spielzeit</label>

<input id="timeInput" value="00:00">

</div>




<div class="input-box">

<label>Heimtore</label>

<input id="homeScoreInput" type="number" value="0">

</div>




<div class="input-box">

<label>Auswärtstore</label>

<input id="awayScoreInput" type="number" value="0">

</div>




<div class="input-box">

<button onclick="updateGame()">

AKTUALISIEREN

</button>

</div>



</div>


</div>



</div>






<script>


function updateGame(){


document.getElementById("homeTeam").innerHTML =
document.getElementById("homeInput").value;


document.getElementById("awayTeam").innerHTML =
document.getElementById("awayInput").value;


document.getElementById("time").innerHTML =
document.getElementById("timeInput").value;


document.getElementById("homeGoals").innerHTML =
document.getElementById("homeScoreInput").value;


document.getElementById("awayGoals").innerHTML =
document.getElementById("awayScoreInput").value;



localStorage.setItem("home",
document.getElementById("homeInput").value);


localStorage.setItem("away",
document.getElementById("awayInput").value);


localStorage.setItem("time",
document.getElementById("timeInput").value);


localStorage.setItem("homeGoals",
document.getElementById("homeScoreInput").value);


localStorage.setItem("awayGoals",
document.getElementById("awayScoreInput").value);


}




window.onload=function(){


if(localStorage.getItem("home")){


document.getElementById("homeInput").value =
localStorage.getItem("home");


document.getElementById("awayInput").value =
localStorage.getItem("away");


document.getElementById("timeInput").value =
localStorage.getItem("time");


document.getElementById("homeScoreInput").value =
localStorage.getItem("homeGoals");


document.getElementById("awayScoreInput").value =
localStorage.getItem("awayGoals");


updateGame();


}


}



</script>


</body>

</html>
