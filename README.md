<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten-Aufstellung V3</title>


<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


:root{

--home:#00b7ff;
--away:#ff4757;
--gold:#f5c542;

}



body{

margin:0;

background:
radial-gradient(circle at top,#333,#050505 75%);

color:white;

min-height:100vh;

}





.dashboard{

width:1600px;

max-width:98%;

margin:20px auto;

background:

linear-gradient(145deg,#1f1f1f,#050505);

border-radius:35px;

padding:25px;

box-shadow:

0 40px 100px #000;

}




.layout{

display:grid;

grid-template-columns:360px 1fr;

gap:25px;

}







/* ==========================
   SPIELTAG
========================== */


.matchday{


background:

linear-gradient(145deg,#292929,#101010);


border-radius:25px;

padding:20px;

border:1px solid #555;

height:950px;

overflow:auto;

}




.matchday-title{


font-size:28px;

font-weight:bold;

text-align:center;

color:var(--gold);

margin-bottom:20px;


}




#spieltagInput{


width:100%;

height:220px;

background:#000;

color:white;

border:1px solid #555;

border-radius:15px;

padding:15px;

}




button{


width:100%;

padding:15px;

margin-top:12px;

border-radius:15px;

border:none;

background:

linear-gradient(#555,#111);

color:white;

font-weight:bold;

cursor:pointer;


}



button:hover{


filter:brightness(1.3);


}







.match-card{


margin-top:15px;

padding:18px;

border-radius:20px;

background:

linear-gradient(145deg,#333,#111);


border:1px solid #555;


cursor:pointer;


box-shadow:

0 10px 25px #000;


}



.match-card:hover{


transform:scale(1.02);


}



.match-time{


color:#aaa;

font-size:13px;


}



.match-team{


text-align:center;

font-size:18px;

font-weight:bold;

margin:5px;


}








/* ==========================
   HAUPT DASHBOARD
========================== */


.main-panel{


background:

linear-gradient(145deg,#151515,#050505);


border-radius:30px;

padding:30px;


}








/* SPIELKOPF */


.game-header{


display:grid;

grid-template-columns:1fr 200px 1fr;

align-items:center;


background:

linear-gradient(

90deg,

#ffffff10,

transparent,

#ffffff10

);


border-radius:25px;

padding:35px;


}



.team-name{


font-size:38px;

font-weight:bold;

text-align:center;


}



.score{


font-size:90px;

font-weight:bold;

text-align:center;


}





</style>


</head>



<body>



<div class="dashboard">


<div class="layout">



<!-- SPIELTAG LINKS -->


<div class="matchday">


<div class="matchday-title">

SPIELTAG

</div>


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







<!-- HAUPTANSICHT -->


<div class="main-panel">



<div class="game-header">


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



<!-- ==========================
     EXPECTED GOALS
========================== -->


<div class="analysis-block">


<h2>
Expected Goals (xG)
</h2>



<div class="value-row">


<span id="xgHeim">
0.00
</span>



<span id="xgGast">
0.00
</span>



</div>



<div class="progress-bar">


<div id="xgHomeBar"

class="home-fill">

</div>


<div id="xgAwayBar"

class="away-fill">

</div>


</div>


</div>








<!-- ==========================
     BALLBESITZ
========================== -->


<div class="analysis-block">


<h2>
Ballbesitz
</h2>



<div class="value-row">


<span id="possHeim">
50%
</span>



<span id="possGast">
50%
</span>



</div>



<div class="progress-bar">


<div id="possHomeBar"

class="home-fill">

</div>


<div id="possAwayBar"

class="away-fill">

</div>


</div>


</div>









<style>


.analysis-block{


margin-top:35px;

background:

linear-gradient(145deg,#222,#090909);

border-radius:25px;

padding:25px;

box-shadow:

0 15px 35px #000;


}



.analysis-block h2{


text-align:center;

font-size:24px;

color:var(--gold);


}




.value-row{


display:flex;

justify-content:space-between;

padding:0 50px;

font-size:38px;

font-weight:bold;


}




.progress-bar{


height:38px;

margin-top:20px;

display:flex;

background:#000;

border-radius:25px;

overflow:hidden;

border:1px solid #555;


}




.home-fill{


height:100%;

background:var(--home);


}



.away-fill{


height:100%;

background:var(--away);


}



</style>

</div>


<!-- ==========================
     LIVE STATISTIK KARTEN
========================== -->


<div class="stats-container">



<div class="stat-card">


<div class="stat-title">
SCHÜSSE
</div>


<div class="stat-value">

<span id="shotsHome">
0
</span>

:

<span id="shotsAway">
0
</span>


</div>


</div>






<div class="stat-card">


<div class="stat-title">
SCHÜSSE AUFS TOR
</div>


<div class="stat-value">


<span id="targetHome">
0
</span>

:

<span id="targetAway">
0
</span>


</div>


</div>







<div class="stat-card">


<div class="stat-title">
GROSSCHANCEN
</div>


<div class="stat-value">


<span id="chanceHome">
0
</span>

:

<span id="chanceAway">
0
</span>


</div>


</div>








<div class="stat-card">


<div class="stat-title">
ECKEN
</div>


<div class="stat-value">


<span id="cornerHome">
0
</span>

:

<span id="cornerAway">
0
</span>


</div>


</div>







<div class="stat-card">


<div class="stat-title">
PÄSSE
</div>


<div class="stat-value">


<span id="passesHome">
0/0
</span>

:

<span id="passesAway">
0/0
</span>


</div>


</div>







<div class="stat-card">


<div class="stat-title">
GELBE KARTEN
</div>


<div class="stat-value">


<span id="cardsHome">
0
</span>

:

<span id="cardsAway">
0
</span>


</div>


</div>




</div>







<style>


.stats-container{


margin-top:35px;


display:grid;


grid-template-columns:repeat(3,1fr);


gap:20px;


}




.stat-card{


background:


linear-gradient(145deg,#303030,#101010);


border-radius:25px;


padding:30px;


text-align:center;


border:1px solid #444;


box-shadow:


0 20px 40px #000;


}




.stat-title{


font-size:15px;


color:#aaa;


letter-spacing:2px;


margin-bottom:15px;


}




.stat-value{


font-size:34px;


font-weight:bold;


}





</style>


<!-- ==========================
     SPIELDATEN TABELLE
========================== -->


<div class="data-panel">


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


<div class="live-panel">


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

0
Großchancen
0

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


.data-panel{


margin-top:40px;


background:


linear-gradient(145deg,#222,#090909);


border-radius:25px;


padding:30px;


box-shadow:


0 20px 40px #000;


}




.data-panel h2,


.live-panel h2{


text-align:center;


color:var(--gold);


}





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


padding:14px;


border-bottom:1px solid #444;


text-align:center;


}



td:first-child{


text-align:left;


color:#bbb;


}




.live-panel{


margin-top:35px;


background:


linear-gradient(145deg,#1f1f1f,#080808);


border-radius:25px;


padding:30px;


}




#datenInput{


width:100%;


height:260px;


background:#000;


color:white;


border:1px solid #555;


border-radius:20px;


padding:20px;


font-size:16px;


resize:none;


}



</style>

<script>


const spieleDaten = {};

let aktuellesSpiel = null;





/* ==========================
   BASIS DATEN
========================== */


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








/* ==========================
   SPIELTAG LADEN
========================== */


document
.getElementById("spieleLaden")
.onclick=function(){



let text=

spieltagInput.value;



let zeilen=

text.split("\n")

.map(x=>x.trim())

.filter(x=>x);



spieleListe.innerHTML="";





for(let i=0;i<zeilen.length;i++){



if(

zeilen[i].match(/\d{2}\.\d{2}/)

){



let datum=zeilen[i];

let teams=[];



for(let j=i+1;j<zeilen.length;j++){



if(zeilen[j]=="-")

break;



if(

!teams.includes(zeilen[j])

){

teams.push(zeilen[j]);

}


}



if(teams.length>=2){



spielKarte(

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


function spielKarte(

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



spieleListe.appendChild(div);



}









/* ==========================
   SPIEL ÖFFNEN
========================== */


function spielOeffnen(

heim,

gast

){



aktuellesSpiel=

heim+"_"+gast;





if(!spieleDaten[aktuellesSpiel]){


spieleDaten[aktuellesSpiel]={


heim:heim,

gast:gast,

stats:neueStatistik()


};


}




heimTeam.innerHTML=

heim;



gastTeam.innerHTML=

gast;



anzeigeAktualisieren();



}









/* ==========================
   ZAHLEN ERKENNEN
========================== */


function wert(text){


if(!text)

return 0;



let x=

text.match(/\d+(?:[.,]\d+)?/);



return x?

Number(

x[0].replace(",", ".")

)

:0;


}









/* ==========================
   DATEN EINLESEN
========================== */


datenUebernehmen.onclick=function(){



if(!aktuellesSpiel)

return;



let text=

datenInput.value;



let zeilen=

text.split("\n")

.map(x=>x.trim())

.filter(x=>x);




let s=

spieleDaten[aktuellesSpiel].stats;






function suche(name){


let i=

zeilen.findIndex(

x=>

x.toLowerCase()

.includes(

name.toLowerCase()

)

);



if(i<1)

return [0,0];



return [

wert(zeilen[i-1]),

wert(zeilen[i+1])

];


}







let xg=

suche("Expected Goals");

s.xg.heim=xg[0];

s.xg.gast=xg[1];






let pos=

suche("Ballbesitz");

s.ballbesitz.heim=pos[0];

s.ballbesitz.gast=pos[1];






let sch=

suche("Schüsse insgesamt");

s.schuesse.heim=sch[0];

s.schuesse.gast=sch[1];






let tor=

suche("Schüsse aufs Tor");

s.aufsTor.heim=tor[0];

s.aufsTor.gast=tor[1];






let ch=

suche("Großchancen");

s.grosschancen.heim=ch[0];

s.grosschancen.gast=ch[1];






let ek=

suche("Ecken");

s.ecken.heim=ek[0];

s.ecken.gast=ek[1];







let gelb=

suche("Gelbe Karten");

s.karten.heim=gelb[0];

s.karten.gast=gelb[1];







let pass=

text.match(/\d+\/\d+/g);



if(pass && pass.length>=2){


s.paesse.heim=pass[0];


s.paesse.gast=pass[1];


}




let quote=

text.match(/\d+%/g);



if(quote && quote.length>=2){


s.passquote.heim=quote[0];


s.passquote.gast=quote[1];


}



anzeigeAktualisieren();



};









/* ==========================
   ANZEIGE
========================== */


function anzeigeAktualisieren(){



if(!aktuellesSpiel)

return;



let s=

spieleDaten[aktuellesSpiel].stats;







xgHeim.innerHTML=

s.xg.heim.toFixed(2);



xgGast.innerHTML=

s.xg.gast.toFixed(2);







possHeim.innerHTML=

s.ballbesitz.heim+"%";



possGast.innerHTML=

s.ballbesitz.gast+"%";







let ges=

s.xg.heim+s.xg.gast;



if(ges>0){


xgHomeBar.style.width=

(s.xg.heim/ges*100)+"%";


xgAwayBar.style.width=

(s.xg.gast/ges*100)+"%";


}




possHomeBar.style.width=

s.ballbesitz.heim+"%";


possAwayBar.style.width=

s.ballbesitz.gast+"%";






shotsHome.innerHTML=s.schuesse.heim;

shotsAway.innerHTML=s.schuesse.gast;


targetHome.innerHTML=s.aufsTor.heim;

targetAway.innerHTML=s.aufsTor.gast;


chanceHome.innerHTML=s.grosschancen.heim;

chanceAway.innerHTML=s.grosschancen.gast;


cornerHome.innerHTML=s.ecken.heim;

cornerAway.innerHTML=s.ecken.gast;


passesHome.innerHTML=s.paesse.heim;

passesAway.innerHTML=s.paesse.gast;


cardsHome.innerHTML=s.karten.heim;

cardsAway.innerHTML=s.karten.gast;



tabXgHome.innerHTML=s.xg.heim.toFixed(2);

tabXgAway.innerHTML=s.xg.gast.toFixed(2);


tabPossHome.innerHTML=s.ballbesitz.heim+"%";

tabPossAway.innerHTML=s.ballbesitz.gast+"%";


tabShotsHome.innerHTML=s.schuesse.heim;

tabShotsAway.innerHTML=s.schuesse.gast;


tabTargetHome.innerHTML=s.aufsTor.heim;

tabTargetAway.innerHTML=s.aufsTor.gast;


tabChanceHome.innerHTML=s.grosschancen.heim;

tabChanceAway.innerHTML=s.grosschancen.gast;


tabCornerHome.innerHTML=s.ecken.heim;

tabCornerAway.innerHTML=s.ecken.gast;


tabPassHome.innerHTML=s.paesse.heim;

tabPassAway.innerHTML=s.paesse.gast;


tabPassRateHome.innerHTML=s.passquote.heim;

tabPassRateAway.innerHTML=s.passquote.gast;


tabCardHome.innerHTML=s.karten.heim;

tabCardAway.innerHTML=s.karten.gast;



}








/* ==========================
   SPEICHERN / LADEN
========================== */


speichern.onclick=function(){


if(!aktuellesSpiel)

return;



localStorage.setItem(

"Wettpropheten_"+aktuellesSpiel,

JSON.stringify(

spieleDaten[aktuellesSpiel]

)

);


};





laden.onclick=function(){



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



}



};



</script>



</div>

</div>


</body>

</html>
