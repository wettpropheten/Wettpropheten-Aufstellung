<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


html,body{

margin:0;

width:100%;

height:100%;

background:#050505;

color:white;

overflow:hidden;

}



/* =========================
   GESAMT
========================= */


.app{

display:grid;

grid-template-columns:250px 1fr;

width:100vw;

height:100vh;

}



/* =========================
   SPIELTAG LINKS
========================= */


.sidebar{


background:

linear-gradient(180deg,#202020,#090909);


height:100vh;


padding:15px;


border-right:2px solid #444;


overflow-y:auto;


}




.sidebar h2{


text-align:center;


color:#f5c542;


font-size:24px;


margin:10px 0 20px;


}




.match{


background:#151515;


border:1px solid #444;


border-radius:15px;


padding:12px;


margin-bottom:12px;


text-align:center;


font-size:15px;


}




/* =========================
   HAUPTFENSTER
========================= */


.main{


height:100vh;


width:100%;


padding:20px;


background:


linear-gradient(145deg,#181818,#050505);


overflow:auto;


}




/* SPIELKOPF */


.game-header{


width:100%;


height:170px;


display:grid;


grid-template-columns:1fr 180px 1fr;


align-items:center;


background:#222;


border-radius:25px;


border:1px solid #444;


}




.team{


font-size:38px;


font-weight:bold;


text-align:center;


}




.score{


font-size:80px;


font-weight:bold;


text-align:center;


color:#f5c542;


}






/* BEREICHE */


.section{


margin-top:20px;


height:120px;


background:#151515;


border:1px solid #333;


border-radius:20px;


padding:20px;


font-size:22px;


color:#f5c542;


}



</style>

</head>



<body>



<div class="app">



<!-- =========================
     SPIELTAG
========================= -->


<div class="sidebar">


<h2>

SPIELTAG

</h2>



<div class="match">

29.08. 15:30

<br><br>

1. FC Köln

<br>

VS

<br>

TSG Hoffenheim

</div>




<div class="match">

29.08. 15:30

<br><br>

RB Leipzig

<br>

VS

<br>

Borussia Mönchengladbach

</div>



<div class="match">

29.08. 15:30

<br><br>

Mainz 05

<br>

VS

<br>

Paderborn

</div>



</div>







<!-- =========================
     HAUPTBEREICH
========================= -->


<div class="main">



<div class="game-header">


<div class="team">

1. FC Köln

</div>



<div class="score">

0 : 0

</div>



<div class="team">

TSG Hoffenheim

</div>



</div>







<div class="section">

Expected Goals (xG)

</div>




<div class="section">

Ballbesitz

</div>




<div class="section">

Statistik Kästchen

</div>




<div class="section">

Spieldaten Tabelle

</div>




</div>



</div>



</body>

</html>
