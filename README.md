<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten-Aufstellung</title>


<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


:root{

--home:#00b7ff;
--away:#ff4757;

}



body{

margin:0;

background:

radial-gradient(circle at top,#444,#050505 70%);

color:white;

min-height:100vh;

}




.main-container{

width:1500px;

max-width:98%;

margin:20px auto;

padding:25px;

background:

linear-gradient(145deg,#222,#050505);

border-radius:35px;

box-shadow:

0 40px 100px #000,

inset 0 0 40px #444;

}





.content{

display:grid;

grid-template-columns:360px 1fr;

gap:25px;

}





/* ======================
   SPIELTAG LINKS
====================== */


.sidebar{

background:

linear-gradient(145deg,#292929,#080808);

border-radius:25px;

padding:20px;

border:1px solid #555;

box-shadow:

0 25px 50px #000;

height:900px;

overflow:auto;

}



.sidebar h2{

text-align:center;

}




#spieltagInput{

width:100%;

height:230px;

background:#000;

color:white;

border:1px solid #666;

border-radius:15px;

padding:15px;

font-size:15px;

}




button{

width:100%;

padding:15px;

margin-top:12px;

border-radius:15px;

border:1px solid #777;

background:

linear-gradient(#555,#111);

color:white;

font-weight:bold;

cursor:pointer;

}



button:hover{

filter:brightness(1.3);

}





.match-item{

margin-top:15px;

padding:15px;

border-radius:18px;

background:

linear-gradient(145deg,#333,#111);

border:1px solid #555;

cursor:pointer;

box-shadow:

0 10px 25px #000;

}



.match-item:hover{

transform:translateY(-3px);

}



.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

font-size:17px;

font-weight:bold;

margin:5px;

text-align:center;

}




/* ======================
   HAUPTBEREICH
====================== */


.main-area{

background:

linear-gradient(145deg,#181818,#050505);

border-radius:30px;

padding:30px;

box-shadow:

0 30px 70px #000,

inset 0 0 35px #333;

}





.score-header{

display:flex;

align-items:center;

justify-content:space-between;

padding:30px;

border-radius:25px;

background:

linear-gradient(

90deg,

#ffffff15,

transparent,

#ffffff15

);

}



.team{

width:40%;

text-align:center;

font-size:34px;

font-weight:bold;

}



.score{

font-size:80px;

font-weight:bold;

text-align:center;

}





</style>


</head>


<body>


<div class="main-container">


<div class="content">



<!-- LINKER BEREICH -->

<div class="sidebar">


<h2>

SPIELTAG

</h2>


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





<!-- HAUPTBEREICH -->


<div class="main-area">



<div class="score-header">


<div id="heimTeam" class="team">

HEIM

</div>


<div class="score">

0 : 0

</div>


<div id="gastTeam" class="team">

GAST

</div>

<!-- ==========================
     xG UND BALLBESITZ BALKEN
========================== -->


<div class="big-stat">


<h2>
Expected Goals (xG)
</h2>


<div class="big-values">

<span id="xgHeim">
0.00
</span>


<span id="xgGast">
0.00
</span>


</div>


<div class="bar-background">

<div id="xgHomeBar"
class="home-bar">
</div>


<div id="xgAwayBar"
class="away-bar">
</div>

</div>


</div>







<div class="big-stat">


<h2>
Ballbesitz
</h2>


<div class="big-values">

<span id="possHeim">
50%
</span>


<span id="possGast">
50%
</span>


</div>


<div class="bar-background">


<div id="possHomeBar"
class="home-bar">
</div>


<div id="possAwayBar"
class="away-bar">
</div>


</div>


</div>









<!-- ==========================
     STATISTIK KÄSTCHEN
========================== -->


<div class="stat-grid">



<div class="stat-box">

<h3>
SCHÜSSE
</h3>

<div>

<span id="shotsHome">0</span>

:

<span id="shotsAway">0</span>

</div>

</div>




<div class="stat-box">

<h3>
SCHÜSSE AUFS TOR
</h3>

<div>

<span id="targetHome">0</span>

:

<span id="targetAway">0</span>

</div>

</div>




<div class="stat-box">

<h3>
GROSSCHANCEN
</h3>

<div>

<span id="chanceHome">0</span>

:

<span id="chanceAway">0</span>

</div>

</div>




<div class="stat-box">

<h3>
ECKEN
</h3>

<div>

<span id="cornerHome">0</span>

:

<span id="cornerAway">0</span>

</div>

</div>




<div class="stat-box">

<h3>
PÄSSE
</h3>

<div>

<span id="passesHome">0/0</span>

:

<span id="passesAway">0/0</span>

</div>

</div>




<div class="stat-box">

<h3>
GELBE KARTEN
</h3>

<div>

<span id="cardsHome">0</span>

:

<span id="cardsAway">0</span>

</div>

</div>



</div>









<!-- ==========================
     SPIELDATEN TABELLE UNTEN
========================== -->


<div class="table-box">


<h2>

SPIELDATEN

</h2>



<table>


<thead>

<tr>

<th>
STATISTIK
</th>

<th>
HEIM
</th>

<th>
GAST
</th>


</tr>

</thead>


<tbody>



<tr>

<td>
Expected Goals (xG)
</td>

<td id="tabXgHome">
0.00
</td>

<td id="tabXgAway">
0.00
</td>


</tr>



<tr>

<td>
Ballbesitz
</td>

<td id="tabPossHome">
50%
</td>

<td id="tabPossAway">
50%
</td>

</tr>




<tr>

<td>
Schüsse
</td>

<td id="tabShotsHome">
0
</td>

<td id="tabShotsAway">
0
</td>

</tr>




<tr>

<td>
Schüsse aufs Tor
</td>

<td id="tabTargetHome">
0
</td>

<td id="tabTargetAway">
0
</td>

</tr>




<tr>

<td>
Großchancen
</td>

<td id="tabChanceHome">
0
</td>

<td id="tabChanceAway">
0
</td>

</tr>




<tr>

<td>
Ecken
</td>

<td id="tabCornerHome">
0
</td>

<td id="tabCornerAway">
0
</td>

</tr>




<tr>

<td>
Passquote
</td>

<td id="tabPassRateHome">
0%
</td>

<td id="tabPassRateAway">
0%
</td>

</tr>




<tr>

<td>
Pässe
</td>

<td id="tabPassHome">
0/0
</td>

<td id="tabPassAway">
0/0
</td>

</tr>




<tr>

<td>
Gelbe Karten
</td>

<td id="tabCardHome">
0
</td>

<td id="tabCardAway">
0
</td>

</tr>



</tbody>


</table>


</div>








<!-- ==========================
     LIVE DATEN
========================== -->


<div class="input-box">


<h2>
LIVE DATEN EINGEBEN
</h2>



<textarea id="datenInput"

placeholder="

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

86%
(454/526)
Pässe
89%
(464/524)

0
Gelbe Karten
1

">

</textarea>



<button id="datenUebernehmen">

DATEN ÜBERNEHMEN

</button>



<button id="speichern">

💾 SPIEL SPEICHERN

</button>



<button id="laden">

📂 SPIEL LADEN

</button>



</div>









<style>


.big-stat{

margin-top:35px;

}



.big-values{

display:flex;

justify-content:space-between;

font-size:34px;

font-weight:bold;

}



.bar-background{

height:35px;

background:#000;

border-radius:20px;

overflow:hidden;

display:flex;

margin-top:15px;

border:1px solid #555;

}



.home-bar{

background:var(--home);

height:100%;

}



.away-bar{

background:var(--away);

height:100%;

}




.stat-grid{

margin-top:35px;

display:grid;

grid-template-columns:repeat(3,1fr);

gap:20px;

}



.stat-box{

background:

linear-gradient(145deg,#333,#111);

padding:25px;

border-radius:20px;

text-align:center;

font-size:30px;

box-shadow:

0 15px 35px #000;

}



.stat-box h3{

font-size:16px;

color:#aaa;

}







.table-box{

margin-top:40px;

background:

linear-gradient(145deg,#222,#080808);

padding:25px;

border-radius:25px;

}



table{

width:100%;

border-collapse:collapse;

font-size:18px;

}



th,td{

padding:15px;

border-bottom:1px solid #444;

text-align:center;

}



td:first-child{

text-align:left;

color:#bbb;

}





.input-box{

margin-top:35px;

background:#111;

padding:25px;

border-radius:25px;

}



#datenInput{

width:100%;

height:250px;

background:#000;

color:white;

padding:15px;

border-radius:15px;

}



</style>

<script>


/* =====================================
   DATENBANK
===================================== */


const spieleDaten = {};



let aktuellesSpiel = null;








/* =====================================
   LEERE STATISTIK ERSTELLEN
===================================== */


function neueStatistik(){


return {


xg:{

heim:0,

gast:0

},



ballbesitz:{

heim:50,

gast:50

},



schuesse:{

heim:0,

gast:0

},



aufsTor:{

heim:0,

gast:0

},



grosschancen:{

heim:0,

gast:0

},



ecken:{

heim:0,

gast:0

},



paesse:{

heim:"0/0",

gast:"0/0"

},



passquote:{

heim:"0%",

gast:"0%"

},



karten:{

heim:0,

gast:0

}



};


}










/* =====================================
   SPIELTAG LADEN
===================================== */


document

.getElementById("spieleLaden")

.onclick=function(){


spieleLaden();


};








function spieleLaden(){



let text =

document

.getElementById("spieltagInput")

.value;



let zeilen =

text

.split("\n")

.map(

x=>x.trim()

)

.filter(

x=>x

);





let liste =

document

.getElementById("spieleListe");



liste.innerHTML="";







for(let i=0;i<zeilen.length;i++){



if(

zeilen[i].match(/\d{2}\.\d{2}/)

){



let datum = zeilen[i];



let teams=[];




for(

let j=i+1;

j<zeilen.length;

j++

){



if(

zeilen[j]==="-"

)

break;



if(

teams.indexOf(

zeilen[j]

)

===-1

){



teams.push(

zeilen[j]

);



}



}





if(

teams.length>=2

){



spielAnzeigen(

datum,

teams[0],

teams[1]

);



}



}



}



}









/* =====================================
   SPIELKARTE ERZEUGEN
===================================== */


function spielAnzeigen(

datum,

heim,

gast

){



let box=

document

.createElement("div");



box.className=

"match-item";



box.innerHTML=`

<div class="match-time">

${datum}

</div>

<div class="match-team">

${heim}

</div>

<div class="match-team">

VS

</div>

<div class="match-team">

${gast}

</div>

`;




box.onclick=function(){


spielOeffnen(

heim,

gast

);



};




document

.getElementById("spieleListe")

.appendChild(box);



}









/* =====================================
   SPIEL ÖFFNEN
===================================== */


function spielOeffnen(

heim,

gast

){



aktuellesSpiel =

heim+"_"+gast;






if(

!spieleDaten[aktuellesSpiel]

){



spieleDaten[aktuellesSpiel]={



heim:heim,

gast:gast,



stats:neueStatistik()



};



}





document

.getElementById("heimTeam")

.innerHTML=

heim;



document

.getElementById("gastTeam")

.innerHTML=

gast;




farbenSetzen();



anzeigeAktualisieren();



}









/* =====================================
   VEREINSFARBEN
===================================== */


const vereinsFarben={


"1. FC Köln":"#E30613",

"TSG Hoffenheim":"#005CA9",

"1. FC Union Berlin":"#E30613",

"Eintracht Frankfurt":"#C00000",

"FSV Mainz 05":"#C41230",

"SC Paderborn":"#005CA9",

"RB Leipzig":"#DD0000",

"Borussia Mönchengladbach":"#00A651",

"SV Elversberg":"#D4AF37",

"Bayer Leverkusen":"#E32221"


};








function farbenSetzen(){



let spiel=

spieleDaten[aktuellesSpiel];



let heimFarbe=

vereinsFarben[spiel.heim]

||

"#00b7ff";



let gastFarbe=

vereinsFarben[spiel.gast]

||

"#ff4757";





document.documentElement

.style

.setProperty(

"--home",

heimFarbe

);



document.documentElement

.style

.setProperty(

"--away",

gastFarbe

);



}



</div>
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

86%
(454/526)
Pässe
89%
(464/524)

0
Gelbe Karten
1


/* =====================================
   SPEICHERN
===================================== */


document

.getElementById("speichern")

.onclick=function(){



if(!aktuellesSpiel)

return;



localStorage.setItem(

"Wettpropheten_"+aktuellesSpiel,

JSON.stringify(

spieleDaten[aktuellesSpiel]

)

);



alert(

"Spiel gespeichert"

);



};








/* =====================================
   LADEN
===================================== */


document

.getElementById("laden")

.onclick=function(){



if(!aktuellesSpiel)

return;



let daten=

localStorage.getItem(

"Wettpropheten_"+aktuellesSpiel

);



if(daten){



spieleDaten[aktuellesSpiel]

=

JSON.parse(daten);



anzeigeAktualisieren();



alert(

"Spiel geladen"

);



}



};









/* =====================================
   SPIELTAG MERKEN
===================================== */


document

.getElementById("spieleLaden")

.addEventListener(

"click",

function(){



localStorage.setItem(

"Wettpropheten_Spieltag",

document

.getElementById("spieltagInput")

.value

);



}

);









/* =====================================
   AUTOMATISCHER START
===================================== */


window.onload=function(){



let gespeicherterSpieltag=

localStorage.getItem(

"Wettpropheten_Spieltag"

);



if(

gespeicherterSpieltag

){



document

.getElementById("spieltagInput")

.value=

gespeicherterSpieltag;



}



};





</script>


</div>

</div>


</body>

</html>
