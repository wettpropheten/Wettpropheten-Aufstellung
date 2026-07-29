<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

*{
    box-sizing:border-box;
    font-family:Arial, Helvetica, sans-serif;
}


html,
body{

    margin:0;
    padding:0;

    width:100%;
    height:100%;

    background:#050505;
    color:white;

    overflow:hidden;

}


/* =========================
   APP
========================= */


.app{

    display:flex;

    width:100vw;
    height:100vh;

}



/* =========================
   SPIELTAG LINKS
========================= */


.sidebar{

    width:260px;
    min-width:260px;

    height:100vh;

    background:
    linear-gradient(
        180deg,
        #222,
        #070707
    );

    border-right:2px solid #444;

    padding:15px;

    overflow-y:auto;

}



.sidebar h1{

    margin:10px 0 20px;

    text-align:center;

    color:#f5c542;

    font-size:26px;

}



/* Eingabe Spieltag */


#spieltagInput{

    width:100%;

    height:220px;

    resize:none;

    padding:15px;

    border-radius:15px;

    background:#111;

    color:white;

    border:1px solid #555;

    font-size:15px;

}



/* Buttons */


button{

    width:100%;

    margin-top:12px;

    padding:14px;

    border-radius:15px;

    border:1px solid #666;

    background:

    linear-gradient(
        #555,
        #111
    );

    color:white;

    font-weight:bold;

    cursor:pointer;

}


button:hover{

    filter:brightness(1.25);

}



/* Spielkarten links */


.match-card{

    margin-top:15px;

    padding:15px;

    border-radius:18px;

    background:

    linear-gradient(
        145deg,
        #333,
        #111
    );

    border:1px solid #444;

    cursor:pointer;

}


.match-card:hover{

    border-color:#f5c542;

}



.match-time{

    text-align:center;

    color:#aaa;

    font-size:13px;

}


.match-team{

    text-align:center;

    margin:6px;

    font-size:16px;

    font-weight:bold;

}



/* =========================
   HAUPTFENSTER
========================= */


.main{

    flex:1;

    height:100vh;

    overflow-y:auto;

    padding:20px;


    background:

    linear-gradient(
        145deg,
        #181818,
        #050505
    );

}



/* =========================
   SPIELKOPF
========================= */


.score-header{

    width:100%;

    display:grid;

    grid-template-columns:

    1fr 220px 1fr;


    align-items:center;


    padding:40px;


    border-radius:30px;


    background:

    linear-gradient(
        90deg,
        #ffffff15,
        transparent,
        #ffffff15
    );

}



.team-name{

    text-align:center;

    font-size:42px;

    font-weight:bold;

}



.score{

    text-align:center;

    font-size:90px;

    font-weight:bold;

    color:#f5c542;

}



/* Farben später per Javascript */

:root{

    --home-color:#00b7ff;

    --away-color:#ff4757;

}


</style>

</head>


<body>


<div class="app">



<!-- =========================
     LINKER SPIELTAG
========================= -->


<div class="sidebar">


<h1>
SPIELTAG
</h1>



<textarea id="spieltagInput"

placeholder="

29.08. 15:30

1. FC Köln

TSG Hoffenheim

-

-

">

</textarea>



<button id="spieleLaden">

SPIELE LADEN

</button>



<div id="spieleListe">

</div>



</div>





<!-- =========================
     HAUPTBEREICH
========================= -->


<div class="main">



<div class="score-header">



<div id="heimTeam"

class="team-name">

HEIM

</div>



<div class="score">

0 : 0

</div>



<div id="gastTeam"

class="team-name">

GAST

</div>



</div>



<!-- HIER KOMMEN IN TEIL 2:
     Balken
     Statistik-Karten
     Tabelle
     Live-Daten
-->



</div>



</div>


</body>

</html>
