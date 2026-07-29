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
radial-gradient(circle at top,#333,#050505 75%);

color:white;

}



.app{

width:98%;

max-width:1700px;

margin:20px auto;

display:grid;

grid-template-columns:340px 1fr;

gap:25px;

align-items:start;

}





/* ======================
   SPIELTAG LINKS
====================== */


.sidebar{


background:

linear-gradient(145deg,#252525,#090909);


border-radius:25px;

padding:20px;

height:900px;

border:1px solid #555;

box-shadow:

0 30px 70px #000;


}



.sidebar h2{

text-align:center;

color:#f5c542;

font-size:28px;

}



.match{

background:

linear-gradient(145deg,#333,#111);

border-radius:18px;

padding:15px;

margin-top:15px;

border:1px solid #555;

}



.match div{

text-align:center;

margin:5px;

font-weight:bold;

}





/* ======================
   HAUPTANSICHT RECHTS
====================== */


.main{


background:

linear-gradient(145deg,#181818,#050505);


border-radius:30px;

padding:35px;

min-height:900px;


box-shadow:

0 40px 90px #000;


}






/* SPIELKOPF */


.game-header{


display:grid;

grid-template-columns:1fr 220px 1fr;

align-items:center;


background:

linear-gradient(90deg,#ffffff15,transparent,#ffffff15);


border-radius:25px;

padding:40px;


}




.team{


font-size:40px;

font-weight:bold;

text-align:center;


}



.score{


font-size:95px;

font-weight:bold;

text-align:center;


}





/* Platzhalter Bereiche */


.section{


margin-top:35px;

background:

linear-gradient(145deg,#222,#090909);


border-radius:25px;

padding:30px;


}



.section-title{


font-size:24px;

color:#f5c542;

margin-bottom:20px;


}



</style>

</head>



<body>


<div class="app">





<!-- ======================
     SPIELTAG
====================== -->


<div class="sidebar">


<h2>

SPIELTAG

</h2>



<div class="match">

<div>
29.08. 15:30
</div>

<div>
1. FC Köln
</div>

<div>
VS
</div>

<div>
TSG Hoffenheim
</div>

</div>




<div class="match">

<div>
29.08. 15:30
</div>

<div>
RB Leipzig
</div>

<div>
VS
</div>

<div>
Borussia Mönchengladbach
</div>

</div>




</div>









<!-- ======================
     HAUPTBEREICH
====================== -->


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

<div class="section-title">

Expected Goals (xG)

</div>

</div>




<div class="section">

<div class="section-title">

Ballbesitz

</div>

</div>





<div class="section">

<div class="section-title">

Statistik

</div>

</div>





<div class="section">

<div class="section-title">

Spieldaten

</div>

</div>




</div>



</div>



</body>

</html>
