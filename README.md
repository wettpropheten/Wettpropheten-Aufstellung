<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>


*{

margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;

}



html,body{


width:100%;
height:100%;


background:#050505;

color:white;


overflow:hidden;


}




:root{


--home-color:#0099ff;

--away-color:#ff3344;


}




/* =====================
   APP
===================== */


.app{


display:flex;

width:100vw;

height:100vh;


}




/* =====================
   SIDEBAR
===================== */


.sidebar{


width:320px;

min-width:320px;


height:100vh;


background:

linear-gradient(

180deg,

#252525,

#080808

);



border-right:2px solid #444;


padding:20px;


overflow-y:auto;


}




.logo{


text-align:center;


font-size:28px;


font-weight:bold;


color:#f5c542;


margin-bottom:20px;


}




textarea{


width:100%;


height:220px;


background:#111;


color:white;


border:1px solid #555;


border-radius:15px;


padding:15px;


resize:none;


}





button{


width:100%;


margin-top:12px;


padding:14px;


border-radius:15px;


border:1px solid #777;


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


filter:brightness(1.3);


}





/* =====================
   SPIELKARTEN
===================== */



.spiel-card{


margin-top:15px;


padding:15px;


border-radius:18px;


background:


linear-gradient(

145deg,

#333,

#111

);



border:1px solid #555;


cursor:pointer;


text-align:center;


}



.spiel-card:hover{


border-color:#f5c542;


}





/* =====================
   MAIN
===================== */


.main{


flex:1;


height:100vh;


overflow-y:auto;


padding:25px;


background:


linear-gradient(

145deg,

#181818,

#050505

);



}




/* =====================
   SPIELKOPF
===================== */


.header{


height:200px;


display:grid;


grid-template-columns:

1fr 220px 1fr;


align-items:center;



border-radius:30px;


background:#111;


border:1px solid #333;


}





.team{


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





.home-text{


color:var(--home-color);


}




.away-text{


color:var(--away-color);


}


</style>

</head>



<body>



<div class="app">



<!-- =====================
     SPIELTAG
===================== -->


<div class="sidebar">



<div class="logo">

WETTPROPHETEN

</div>



<textarea id="spieltagInput"

placeholder="

Spieltag einfügen:

29.08. 15:30

FC Bayern München

Borussia Dortmund

-

29.08. 18:30

Bayer Leverkusen

RB Leipzig

-

"></textarea>




<button id="importBtn">

SPIELTAG EINLESEN

</button>



<button id="saveBtn">

💾 SPIELTAG SPEICHERN

</button>



<button id="loadBtn">

📂 SPIELTAG LADEN

</button>




<div id="spielListe">

</div>



</div>








<!-- =====================
     HAUPTBEREICH
===================== -->


<div class="main">





<div class="header">



<div id="heimTeam"

class="team home-text">

HEIM

</div>




<div class="score">

0 : 0

</div>




<div id="gastTeam"

class="team away-text">

GAST

</div>




</div>






<!-- =====================
     xG
===================== -->


<div class="panel">



<div class="panel-title">

Expected Goals (xG)

</div>




<div class="werte">


<span id="xgHome"

class="home-text">

0.00

</span>




<span id="xgAway"

class="away-text">

0.00

</span>


</div>





<div class="balken">


<div id="xgHomeBar"

class="home-bar">

</div>



<div id="xgAwayBar"

class="away-bar">

</div>



</div>




</div>








<!-- =====================
     BALLBESITZ
===================== -->


<div class="panel">



<div class="panel-title">

Ballbesitz

</div>




<div class="werte">


<span id="posHome"

class="home-text">

50%

</span>



<span id="posAway"

class="away-text">

50%

</span>


</div>




<div class="balken">


<div id="posHomeBar"

class="home-bar">

</div>



<div id="posAwayBar"

class="away-bar">

</div>



</div>



</div>







<style>


/* =====================
   PANELS
===================== */


.panel{


margin-top:25px;


background:


linear-gradient(

145deg,

#252525,

#101010

);



border-radius:25px;


padding:30px;


border:1px solid #333;


}




.panel-title{


font-size:26px;


font-weight:bold;


color:#f5c542;


margin-bottom:20px;


}




.werte{


display:flex;


justify-content:space-between;


padding:0 40px;


font-size:38px;


font-weight:bold;


margin-bottom:15px;


}




.balken{


height:40px;


width:100%;


display:flex;


background:#000;


border-radius:25px;


overflow:hidden;


border:1px solid #555;


}




.home-bar{


height:100%;


background:var(--home-color);


transition:.5s;


}




.away-bar{


height:100%;


background:var(--away-color);


transition:.5s;


}



</style>
<!-- =====================
     STATISTIK BEREICH
===================== -->


<div class="stats-grid">



<div class="stat-box">

<div class="stat-name">

SCHÜSSE

</div>


<div class="stat-value">

<span id="shotsHome"
class="home-text">

0

</span>


:


<span id="shotsAway"
class="away-text">

0

</span>


</div>


</div>







<div class="stat-box">

<div class="stat-name">

SCHÜSSE AUFS TOR

</div>


<div class="stat-value">

<span id="targetHome"
class="home-text">

0

</span>


:


<span id="targetAway"
class="away-text">

0

</span>


</div>


</div>







<div class="stat-box">

<div class="stat-name">

GROSSCHANCEN

</div>


<div class="stat-value">

<span id="chanceHome"
class="home-text">

0

</span>


:


<span id="chanceAway"
class="away-text">

0

</span>


</div>


</div>







<div class="stat-box">

<div class="stat-name">

ECKEN

</div>


<div class="stat-value">

<span id="cornerHome"
class="home-text">

0

</span>


:


<span id="cornerAway"
class="away-text">

0

</span>


</div>


</div>







<div class="stat-box">

<div class="stat-name">

PÄSSE

</div>


<div class="stat-value">

<span id="passHome"
class="home-text">

0/0

</span>


:


<span id="passAway"
class="away-text">

0/0

</span>


</div>


</div>







<div class="stat-box">

<div class="stat-name">

GELBE KARTEN

</div>


<div class="stat-value">

<span id="cardHome"
class="home-text">

0

</span>


:


<span id="cardAway"
class="away-text">

0

</span>


</div>


</div>





</div>









<style>


/* =====================
   STATISTIK KARTEN
===================== */


.stats-grid{


margin-top:25px;


display:grid;


grid-template-columns:

repeat(3,1fr);


gap:20px;


}




.stat-box{


background:


linear-gradient(

145deg,

#333,

#111

);



border-radius:22px;


padding:25px;


text-align:center;


border:1px solid #444;


box-shadow:

0 15px 30px #000;


}




.stat-name{


color:#aaa;


font-size:14px;


letter-spacing:2px;


margin-bottom:15px;


}




.stat-value{


font-size:36px;


font-weight:bold;


}





/* =====================
   LIVE EINGABE
===================== */


.live-panel{


margin-top:25px;


background:


linear-gradient(

145deg,

#252525,

#101010

);



border-radius:25px;


padding:30px;


border:1px solid #333;


}





.live-title{


font-size:26px;


font-weight:bold;


color:#f5c542;


margin-bottom:20px;


}





#liveInput{


width:100%;


height:220px;


background:#050505;


color:white;


border:1px solid #555;


border-radius:15px;


padding:20px;


font-size:16px;


}







</style>








<!-- =====================
     LIVE DATEN
===================== -->


<div class="live-panel">



<div class="live-title">

LIVE DATEN EINGEBEN

</div>




<textarea id="liveInput"

placeholder="

xG:

1.24

0.80


Ballbesitz:

58%

42%


Schüsse:

10

12


Pässe:

454/526

464/524


Karten:

1

2

"></textarea>





<button id="updateBtn">

DATEN ÜBERNEHMEN

</button>




</div>
<script>


/* =====================
   VEREINSFARBEN
===================== */


const teams = {


"FC Bayern München":"#dc052d",

"Borussia Dortmund":"#f6d800",

"Bayer Leverkusen":"#e32221",

"RB Leipzig":"#dd0000",

"Eintracht Frankfurt":"#e1000f",

"VfB Stuttgart":"#e32219",

"SC Freiburg":"#e2001a",

"1. FSV Mainz 05":"#c31432",

"Werder Bremen":"#1d9053",

"Borussia Mönchengladbach":"#009b3a",

"VfL Wolfsburg":"#65b32e",

"TSG Hoffenheim":"#005ca9",

"FC Augsburg":"#ba3733",

"1. FC Union Berlin":"#eb0016",

"FC St. Pauli":"#5a2d14",

"Holstein Kiel":"#d50000",

"VfL Bochum":"#005ca9",

"1. FC Heidenheim":"#e30613"


};






let spieltag=[];

let aktuellesSpiel=null;







/* =====================
   SPIELTAG EINLESEN
===================== */


document
.getElementById("importBtn")
.onclick=function(){



let text=document
.getElementById("spieltagInput")
.value;



if(text.trim()==""){


alert("Bitte Spieltag einfügen");


return;


}




let zeilen=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x);



spieltag=[];



for(let i=0;i<zeilen.length;i++){



if(
zeilen[i].match(/\d{2}\.\d{2}/)
){



let datum=zeilen[i];


let vereine=[];



for(
let j=i+1;
j<zeilen.length;
j++
){



if(
zeilen[j]=="-"
){

break;

}



vereine.push(
zeilen[j]
);



}




if(
vereine.length>=2
){



spieltag.push({


datum:datum,


heim:vereine[0],


gast:vereine[1],


daten:{


xg:[0,0],


besitz:[50,50],


schuesse:[0,0],


aufsTor:[0,0],


chancen:[0,0],


ecken:[0,0],


paesse:["0/0","0/0"],


karten:[0,0]


}



});



}


}



}



zeigeSpiele();



alert(

spieltag.length+" Spiele geladen"

);



};









/* =====================
   SPIELE LINKS ANZEIGEN
===================== */


function zeigeSpiele(){



let liste=document
.getElementById("spielListe");



liste.innerHTML="";




spieltag.forEach(

(spiel,index)=>{



let box=document
.createElement("div");



box.className="spiel-card";




box.innerHTML=`

<div style="color:#aaa">

${spiel.datum}

</div>


<div style="color:${teams[spiel.heim] || '#0099ff'}">

${spiel.heim}

</div>


<div>

VS

</div>


<div style="color:${teams[spiel.gast] || '#ff3344'}">

${spiel.gast}

</div>

`;





box.onclick=function(){



spielLaden(index);



};



liste.appendChild(box);



}



);



}









/* =====================
   SPIEL ÖFFNEN
===================== */


function spielLaden(index){



aktuellesSpiel=index;



let spiel=spieltag[index];



document
.getElementById("heimTeam")
.innerHTML=

spiel.heim;



document
.getElementById("gastTeam")
.innerHTML=

spiel.gast;




farbenSetzen(

spiel.heim,

spiel.gast

);




anzeigen();



}









/* =====================
   FARBEN SETZEN
===================== */


function farbenSetzen(

heim,

gast

){



document.documentElement.style.setProperty(

"--home-color",

teams[heim] || "#0099ff"

);



document.documentElement.style.setProperty(

"--away-color",

teams[gast] || "#ff3344"

);



}


</script>
</body>
</html>
