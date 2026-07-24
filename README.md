<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Aufstellung</title>


<style>

body{

margin:0;
padding:30px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#06101d,#075c35);

color:white;

}


h1{

text-align:center;
font-size:40px;

}



.container{

max-width:1600px;
margin:auto;

}



.fields{

display:flex;

justify-content:center;

gap:80px;

margin-top:40px;

}




.pitch{

width:420px;
height:620px;

background:
linear-gradient(#1c9b45,#0d6b2c);

border:4px solid white;

border-radius:20px;

position:relative;

transform:perspective(900px)
rotateX(18deg)
rotateY(-5deg);


box-shadow:

0 40px 60px black;


}



.pitch:before{

content:"";

position:absolute;

left:50%;
top:50%;

width:100px;
height:100px;

border:3px solid white;

border-radius:50%;

transform:translate(-50%,-50%);

}



.line{

position:absolute;

top:50%;

width:100%;

border-top:3px solid white;

}




.player{


position:absolute;

transform:translate(-50%,-50%);

text-align:center;

}



.shirt{


width:60px;

height:70px;

background:#e00000;

clip-path:polygon(
20% 0,
80% 0,
100% 20%,
75% 35%,
75% 100%,
25% 100%,
25% 35%,
0 20%
);


display:flex;

align-items:center;

justify-content:center;

font-size:22px;

font-weight:bold;

text-shadow:0 3px 5px black;


margin:auto;


}



.name{

margin-top:8px;

font-weight:bold;

font-size:16px;

}





.away .shirt{

background:#eeeeee;

color:#111;

}





.cards{

margin-top:80px;

display:grid;

grid-template-columns:
repeat(2,1fr);

gap:30px;


}



.card{


background:

rgba(255,255,255,.12);


border-radius:25px;

padding:25px;

box-shadow:

0 20px 40px black;


}



.card h2{

text-align:center;

}



.playerlist{

display:grid;

grid-template-columns:1fr 1fr;

gap:10px;

}



.playerlist div{


background:rgba(0,0,0,.4);

padding:10px;

border-radius:10px;


}



</style>


</head>



<body>


<div class="container">


<h1>
⚽ Wettpropheten Aufstellung
</h1>



<div class="fields">



<!-- HEIM -->

<div>

<h2 style="text-align:center">
Heim Mannschaft
</h2>


<div class="pitch">


<div class="line"></div>


<div class="player" style="left:50%;top:90%">
<div class="shirt">1</div>
<div class="name">Torwart</div>
</div>



<div class="player" style="left:50%;top:70%">
<div class="shirt">9</div>
<div class="name">Stürmer</div>
</div>



<div class="player" style="left:30%;top:50%">
<div class="shirt">10</div>
<div class="name">Spieler</div>
</div>



<div class="player" style="left:70%;top:50%">
<div class="shirt">7</div>
<div class="name">Spieler</div>
</div>



</div>

</div>





<!-- GAST -->


<div>

<h2 style="text-align:center">
Gast Mannschaft
</h2>


<div class="pitch away">


<div class="line"></div>



<div class="player" style="left:50%;top:10%">
<div class="shirt">1</div>
<div class="name">Torwart</div>
</div>



<div class="player" style="left:50%;top:30%">
<div class="shirt">9</div>
<div class="name">Stürmer</div>
</div>



<div class="player" style="left:30%;top:50%">
<div class="shirt">10</div>
<div class="name">Spieler</div>
</div>



<div class="player" style="left:70%;top:50%">
<div class="shirt">7</div>
<div class="name">Spieler</div>
</div>



</div>


</div>



</div>





<div class="cards">


<div class="card">


<h2>
Heim Aufstellung
</h2>


<div class="playerlist">


<div>1 Torwart</div>
<div>2 Verteidiger</div>
<div>3 Verteidiger</div>
<div>4 Verteidiger</div>
<div>6 Mittelfeld</div>
<div>8 Mittelfeld</div>
<div>10 Spielmacher</div>
<div>9 Stürmer</div>


</div>


</div>





<div class="card">


<h2>
Gast Aufstellung
</h2>


<div class="playerlist">


<div>1 Torwart</div>
<div>2 Verteidiger</div>
<div>3 Verteidiger</div>
<div>4 Verteidiger</div>
<div>6 Mittelfeld</div>
<div>8 Mittelfeld</div>
<div>10 Spielmacher</div>
<div>9 Stürmer</div>


</div>


</div>


</div>




</div>


</body>

</html>
