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


body{

margin:0;

background:

radial-gradient(circle at top,#444,#050505 75%);

color:white;

}



/* =========================
   GESAMTANSICHT
========================= */


.app{

display:grid;

grid-template-columns:320px 1fr;

width:100vw;

min-height:100vh;

}



/* =========================
   SPIELTAG LINKS
========================= */


.sidebar{

background:

linear-gradient(180deg,#1d1d1d,#080808);

padding:20px;

border-right:2px solid #444;

}



.sidebar h1{

text-align:center;

font-size:28px;

color:#f5c542;

margin-top:0;

}



.match{

background:

linear-gradient(145deg,#333,#111);

border:1px solid #555;

border-radius:18px;

padding:18px;

margin-bottom:15px;

text-align:center;

font-weight:bold;

}



.match:hover{

border-color:#f5c542;

}






/* =========================
   HAUPTFENSTER
========================= */


.main{

padding:30px;

background:

linear-gradient(145deg,#151515,#050505);

}




.game-header{

width:100%;

display:grid;

grid-template-columns:1fr 180px 1fr;

align-items:center;

background:#222;

border:1px solid #555;

border-radius:30px;

padding:40px;

}



.team{

font-size:42px;

font-weight:bold;

text-align:center;

}



.score{

font-size:90px;

font-weight:bold;

text-align:center;

color:#f5c542;

}






/* Platzhalter für Module */


.panel{

margin-top:30px;

background:

linear-gradient(145deg,#222,#101010);

border-radius:25px;

border:1px solid #444;

padding:30px;

font-size:25px;

}



.panel-title{

color:#f5c542;

font-size:24px;

margin-bottom:20px;

}




</style>

</head>


<body>



<div class="app">



<!-- =====================
     LINKER SPIELTAG
===================== -->


<div class="sidebar">


<h1>

SPIELTAG

</h1>



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



</div>








<!-- =====================
     HAUPTBEREICH
===================== -->


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







<div class="panel">

<div class="panel-title">

Expected Goals (xG)

</div>

Balkenbereich

</div>






<div class="panel">

<div class="panel-title">

Ballbesitz

</div>

Balkenbereich

</div>






<div class="panel">

<div class="panel-title">

Statistik Kästchen

</div>

Bereich für Live-Werte

</div>






<div class="panel">

<div class="panel-title">

Spieldaten Tabelle

</div>

Bereich für Tabelle

</div>





</div>


</div>



</body>

</html>
