<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Taktik Board</title>

<style>

*{
box-sizing:border-box;
}

body{
margin:0;
background:#06152d;
font-family:Arial,Helvetica,sans-serif;
color:white;
}


.board{
max-width:1200px;
margin:auto;
padding:20px;
}


/* HEADER */

.header{

display:flex;
align-items:center;
justify-content:center;
gap:20px;
margin-bottom:25px;

}


.team{

width:40%;
height:70px;

background:white;
border-radius:40px;

display:flex;
align-items:center;

padding:10px;

}


.logo{

width:55px;
height:55px;

border-radius:50%;
background:#ddd;

display:flex;
align-items:center;
justify-content:center;

overflow:hidden;

}


.logo img{

width:100%;
height:100%;
object-fit:cover;

}


.team input{

border:0;
outline:0;

font-size:25px;
font-weight:bold;

width:100%;
text-align:center;

color:#092451;

}



.vs{

background:#006cff;

padding:15px 30px;

border-radius:20px;

font-size:30px;

font-weight:bold;

}



/* SPIELFELD */


.tactical-area{

position:relative;

width:100%;

aspect-ratio:16/9;

background-image:url("DEIN_ORIGINAL_BILD.jpg");

background-size:cover;

background-position:center;

border-radius:20px;

overflow:hidden;

box-shadow:
0 15px 40px rgba(0,0,0,.6);

}



/* SPIELER */


.player{

position:absolute;

transform:translate(-50%,-50%);

text-align:center;

cursor:pointer;

}


.circle{

width:45px;
height:45px;

border-radius:50%;

display:flex;

align-items:center;
justify-content:center;

background:#087cff;

border:3px solid white;

font-weight:bold;

}



.name{

margin-top:5px;

background:white;

color:#111;

padding:3px 8px;

border-radius:5px;

font-size:12px;

font-weight:bold;

}




/* KADER */


.squad{

margin-top:25px;

display:grid;

grid-template-columns:1fr 1fr;

gap:20px;

}



.card{

background:#102852;

padding:20px;

border-radius:15px;

}


.card h2{

text-align:center;

}



.player-line{

padding:8px;

background:rgba(255,255,255,.08);

margin:5px;

}




@media(max-width:800px){

.header,
.squad{

display:block;

}


.team{

width:100%;
margin-bottom:10px;

}


.vs{

text-align:center;

}


}


</style>

</head>


<body>


<div class="board">


<div class="header">


<div class="team">

<div class="logo">
⚽
</div>

<input value="HEIM TEAM">

</div>


<div class="vs">
VS
</div>


<div class="team">


<div class="logo">
⚽
</div>


<input value="GAST TEAM">


</div>


</div>





<div class="tactical-area">


<!-- Spieler werden hier platziert -->


<div class="player" style="left:50%;top:85%;">

<div class="circle">
1
</div>

<div class="name">
TORWART
</div>

</div>



<div class="player" style="left:50%;top:50%;">

<div class="circle">
10
</div>

<div class="name">
SPIELER
</div>

</div>



</div>




<div class="squad">


<div class="card">

<h2>HEIM KADER</h2>

<div class="player-line">
1 Torwart
</div>

<div class="player-line">
2 Spieler
</div>


<div class="player-line">
3 Spieler
</div>


</div>



<div class="card">

<h2>GAST KADER</h2>

<div class="player-line">
1 Torwart
</div>

<div class="player-line">
2 Spieler
</div>


<div class="player-line">
3 Spieler
</div>


</div>


</div>



</div>


</body>
</html>
