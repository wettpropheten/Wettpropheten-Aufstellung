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
padding:0;

width:100%;
height:100%;

background:#050505;

color:white;

}


/* ==========================
   GESAMT
========================== */


.app{

display:flex;

width:100vw;

height:100vh;

overflow:hidden;

}



/* ==========================
   SPIELTAG LINKS
========================== */


.sidebar{

width:260px;

min-width:260px;

height:100vh;

background:

linear-gradient(
180deg,
#222,
#080808
);


border-right:2px solid #444;

padding:15px;

overflow-y:auto;

}



.sidebar h1{

text-align:center;

color:#f5c542;

font-size:26px;

margin:10px 0 20px;

}



#spieltagInput{

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

padding:14px;

margin-top:12px;

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

filter:brightness(1.2);

}





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


border:1px solid #555;

cursor:pointer;

}



.match-card:hover{

border-color:#f5c542;

}



.match-time{

font-size:13px;

color:#aaa;

text-align:center;

}



.match-team{

text-align:center;

font-size:17px;

font-weight:bold;

margin:5px;

}







/* ==========================
   HAUPTBEREICH
========================== */


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



/* SPIELKOPF */


.score-header{


display:grid;

grid-template-columns:

1fr 200px 1fr;


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





/* ==========================
   VEREINSFARBEN
========================== */


:root{

--home-color:#00b7ff;

--away-color:#ff4757;

}






</style>


</head>


<body>


<div class="app">



<!-- ==========================
     SPIELTAG
========================== -->


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






<!-- ==========================
     HAUPTFENSTER
========================== -->


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





<!-- ==========================
     xG BEREICH
========================== -->


<div class="panel">


<div class="panel-title">

Expected Goals (xG)

</div>



<div class="values">

<span id="xgHomeValue">

0.00

</span>


<span id="xgAwayValue">

0.00

</span>


</div>



<div class="bar">

<div id="xgHomeBar"

class="home-bar">

</div>


<div id="xgAwayBar"

class="away-bar">

</div>

</div>



</div>








<!-- ==========================
     BALLBESITZ
========================== -->


<div class="panel">


<div class="panel-title">

Ballbesitz

</div>



<div class="values">


<span id="posHomeValue">

50%

</span>



<span id="posAwayValue">

50%

</span>



</div>




<div class="bar">


<div id="posHomeBar"

class="home-bar">

</div>



<div id="posAwayBar"

class="away-bar">

</div>



</div>


</div>








<!-- ==========================
     STATISTIK KÄSTCHEN
========================== -->


<div class="stats-grid">



<div class="stat-box">

<div>

SCHÜSSE

</div>

<strong id="shotsHome">

0

</strong>

:

<strong id="shotsAway">

0

</strong>


</div>





<div class="stat-box">

<div>

SCHÜSSE AUFS TOR

</div>


<strong id="targetHome">

0

</strong>

:

<strong id="targetAway">

0

</strong>


</div>







<div class="stat-box">

<div>

GROSSCHANCEN

</div>


<strong id="chanceHome">

0

</strong>

:

<strong id="chanceAway">

0

</strong>


</div>







<div class="stat-box">

<div>

ECKEN

</div>


<strong id="cornerHome">

0

</strong>

:

<strong id="cornerAway">

0

</strong>


</div>







<div class="stat-box">

<div>

PÄSSE

</div>


<strong id="passesHome">

0/0

</strong>

:

<strong id="passesAway">

0/0

</strong>


</div>







<div class="stat-box">

<div>

GELBE KARTEN

</div>


<strong id="cardsHome">

0

</strong>

:

<strong id="cardsAway">

0

</strong>


</div>



</div>









<!-- ==========================
     TABELLE
========================== -->


<div class="panel">


<div class="panel-title">

SPIELDATEN

</div>




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

<td id="tabPosHome">

50%

</td>


<td id="tabPosAway">

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
Passquote
</td>

<td id="tabRateHome">

0%

</td>


<td id="tabRateAway">

0%

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


<div class="panel">


<div class="panel-title">

LIVE DATEN EINGEBEN

</div>



<textarea id="datenInput"

style="width:100%;height:250px;"

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


/* ==========================
   MODULE
========================== */


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

box-shadow:

0 20px 45px #000;

border:1px solid #333;

}




.panel-title{

font-size:26px;

font-weight:bold;

color:#f5c542;

margin-bottom:20px;

}




/* ==========================
   WERTE ÜBER BALKEN
========================== */


.values{

display:flex;

justify-content:space-between;

font-size:38px;

font-weight:bold;

padding:0 40px;

margin-bottom:15px;

}






/* ==========================
   BALKEN
========================== */


.bar{

width:100%;

height:38px;

background:#000;

border-radius:20px;

overflow:hidden;

display:flex;

border:1px solid #555;

}



.home-bar{

height:100%;

background:var(--home-color);

transition:.4s;

}



.away-bar{

height:100%;

background:var(--away-color);

transition:.4s;

}








/* ==========================
   STATISTIK KARTEN
========================== */


.stats-grid{


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


font-size:18px;


border:1px solid #444;


box-shadow:


0 15px 30px #000;


}



.stat-box div{


color:#aaa;


font-size:14px;


margin-bottom:15px;


letter-spacing:1px;


}



.stat-box strong{


font-size:32px;


}







/* ==========================
   TABELLE
========================== */


table{


width:100%;


border-collapse:collapse;


font-size:18px;


}



th{


background:#333;


padding:15px;


}



td{


padding:15px;


border-bottom:1px solid #444;


text-align:center;


}



td:first-child{


text-align:left;


color:#ccc;


}






/* ==========================
   LIVE TEXTFELD
========================== */


#datenInput{


background:#050505;


color:white;


border:1px solid #555;


padding:20px;


font-size:16px;


border-radius:18px;


}





/* ==========================
   VEREINSFARBEN
========================== */


:root{

--home-color:#00b7ff;

--away-color:#ff4757;

}




</style>





/* ==========================
   MANNSCHAFTS FARBEN
========================== */


const teamColors = {


"1. FC Köln":

{

main:"#e30613"

},



"TSG Hoffenheim":

{

main:"#005ca9"

},




"1. FC Union Berlin":

{

main:"#d00000"

},




"Eintracht Frankfurt":

{

main:"#e1000f"

},




"FSV Mainz 05":

{

main:"#c31432"

},




"SC Paderborn":

{

main:"#005ca9"

},




"RB Leipzig":

{

main:"#dd0000"

},




"Borussia Mönchengladbach":

{

main:"#009b3a"

},




"SV Elversberg":

{

main:"#000000"

},




"Bayer Leverkusen":

{

main:"#e32221"

}



};





/* ==========================
   FARBEN SETZEN
========================== */


function setTeamColors(home,away){



let homeColor =

teamColors[home]

?

teamColors[home].main

:

"#00b7ff";





let awayColor =

teamColors[away]

?

teamColors[away].main

:

"#ff4757";





document.documentElement.style.setProperty(

"--home-color",

homeColor

);




document.documentElement.style.setProperty(

"--away-color",

awayColor

);



}




<script>


let spiele = {};

let aktuellesSpiel = null;



/* ==========================
   SPIELTAG LADEN
========================== */


document
.getElementById("spieleLaden")
.onclick=function(){


let text =

document
.getElementById("spieltagInput")
.value;



let zeilen =

text.split("\n")
.map(x=>x.trim())
.filter(x=>x);



let liste =

document
.getElementById("spieleListe");



liste.innerHTML="";



for(let i=0;i<zeilen.length;i++){



if(zeilen[i].match(/\d{2}\.\d{2}/)){


let datum=zeilen[i];

let teams=[];



for(let j=i+1;j<zeilen.length;j++){


if(zeilen[j]=="-")

break;



if(!teams.includes(zeilen[j])){

teams.push(zeilen[j]);

}


}



if(teams.length>=2){


erstelleSpielkarte(

datum,

teams[0],

teams[1]

);


}


}



}


};









/* ==========================
   SPIELKARTE
========================== */


function erstelleSpielkarte(

datum,

heim,

gast

){



let div=

document.createElement("div");



div.className="match-card";



div.innerHTML=`

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



div.onclick=function(){


spielOeffnen(

heim,

gast

);


};



document
.getElementById("spieleListe")
.appendChild(div);



}









/* ==========================
   SPIEL ÖFFNEN
========================== */


function spielOeffnen(

heim,

gast

){



aktuellesSpiel =

heim+"_"+gast;





if(!spiele[aktuellesSpiel]){


spiele[aktuellesSpiel]={


heim:heim,

gast:gast,


xg:[0,0],


besitz:[50,50],


schuesse:[0,0],


aufsTor:[0,0],


chancen:[0,0],


ecken:[0,0],


paesse:["0/0","0/0"],


passquote:["0%","0%"],


karten:[0,0]


};


}





document
.getElementById("heimTeam")
.innerHTML=heim;



document
.getElementById("gastTeam")
.innerHTML=gast;



setTeamColors(

heim,

gast

);



anzeigen();



}









/* ==========================
   DATEN ÜBERNEHMEN
========================== */


document
.getElementById("datenUebernehmen")
.onclick=function(){



if(!aktuellesSpiel)

return;



let text=

document
.getElementById("datenInput")
.value;



let s=

spiele[aktuellesSpiel];





let zahlen =

text.match(/\d+(?:[.,]\d+)?/g)

|| [];





if(zahlen.length>=2){


s.xg=[

Number(zahlen[0].replace(",",".")),

Number(zahlen[1].replace(",","."))

];


}





let pass =

text.match(/\d+\/\d+/g);



if(pass && pass.length>=2){

s.paesse=[

pass[0],

pass[1]

];

}




let prozent =

text.match(/\d+%/g);



if(prozent && prozent.length>=2){


s.besitz=[

parseInt(prozent[0]),

parseInt(prozent[1])

];


}




anzeigen();



};









/* ==========================
   ANZEIGE AKTUALISIEREN
========================== */


function anzeigen(){


if(!aktuellesSpiel)

return;



let s=

spiele[aktuellesSpiel];







/* xG */


xgHomeValue.innerHTML=

s.xg[0].toFixed(2);



xgAwayValue.innerHTML=

s.xg[1].toFixed(2);



let xgSum=

s.xg[0]+s.xg[1];



if(xgSum>0){


xgHomeBar.style.width=

(s.xg[0]/xgSum*100)+"%";


xgAwayBar.style.width=

(s.xg[1]/xgSum*100)+"%";


}






/* Besitz */


posHomeValue.innerHTML=

s.besitz[0]+"%";


posAwayValue.innerHTML=

s.besitz[1]+"%";



posHomeBar.style.width=

s.besitz[0]+"%";



posAwayBar.style.width=

s.besitz[1]+"%";









/* Kästchen */


shotsHome.innerHTML=s.schuesse[0];

shotsAway.innerHTML=s.schuesse[1];


targetHome.innerHTML=s.aufsTor[0];

targetAway.innerHTML=s.aufsTor[1];


chanceHome.innerHTML=s.chancen[0];

chanceAway.innerHTML=s.chancen[1];


cornerHome.innerHTML=s.ecken[0];

cornerAway.innerHTML=s.ecken[1];


passesHome.innerHTML=s.paesse[0];

passesAway.innerHTML=s.paesse[1];


cardsHome.innerHTML=s.karten[0];

cardsAway.innerHTML=s.karten[1];





/* Tabelle */


tabXgHome.innerHTML=s.xg[0].toFixed(2);

tabXgAway.innerHTML=s.xg[1].toFixed(2);


tabPosHome.innerHTML=s.besitz[0]+"%";

tabPosAway.innerHTML=s.besitz[1]+"%";


tabPassHome.innerHTML=s.paesse[0];

tabPassAway.innerHTML=s.paesse[1];


tabRateHome.innerHTML=s.passquote[0];

tabRateAway.innerHTML=s.passquote[1];


tabCardHome.innerHTML=s.karten[0];

tabCardAway.innerHTML=s.karten[1];



}









/* ==========================
   SPEICHERN
========================== */


document
.getElementById("speichern")
.onclick=function(){



if(!aktuellesSpiel)

return;



localStorage.setItem(

"Wettpropheten_"+aktuellesSpiel,

JSON.stringify(

spiele[aktuellesSpiel]

)

);


};







/* ==========================
   LADEN
========================== */


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


spiele[aktuellesSpiel]=

JSON.parse(daten);



anzeigen();


}



};







</div>

</div>
</script>
</body>

</html>
