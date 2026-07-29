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

border-radius:30px;

box-shadow:
0 30px 80px #000;

}



.content{

display:grid;

grid-template-columns:360px 1fr;

gap:25px;

}




/* SPIELTAG */

.sidebar{

background:
linear-gradient(145deg,#292929,#090909);

border-radius:25px;

padding:20px;

height:900px;

overflow:auto;

border:1px solid #555;

}



.sidebar h2{

text-align:center;

font-size:28px;

}



#spieltagInput{

width:100%;

height:220px;

background:#000;

color:white;

border-radius:15px;

padding:15px;

font-size:15px;

border:1px solid #555;

}



button{

width:100%;

padding:14px;

margin-top:12px;

border-radius:15px;

border:1px solid #777;

background:
linear-gradient(#555,#111);

color:white;

font-weight:bold;

cursor:pointer;

}



.match-item{

margin-top:15px;

padding:15px;

background:
linear-gradient(145deg,#333,#111);

border-radius:18px;

border:1px solid #555;

cursor:pointer;

}



.match-time{

color:#aaa;

font-size:13px;

}



.match-team{

text-align:center;

font-size:17px;

font-weight:bold;

margin:5px;

}





/* HAUPTBEREICH */


.main-area{

background:
linear-gradient(145deg,#181818,#050505);

border-radius:30px;

padding:30px;

min-height:900px;

}





.score-header{

display:flex;

justify-content:space-between;

align-items:center;

padding:30px;

background:
linear-gradient(90deg,#ffffff15,transparent,#ffffff15);

border-radius:25px;

}



.team{

width:40%;

text-align:center;

font-size:32px;

font-weight:bold;

}



.score{

font-size:70px;

font-weight:bold;

}



</style>

</head>


<body>


<div class="main-container">


<div class="content">


<!-- SPIELTAG -->

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





<!-- HAUPTANSICHT -->


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
     xG BALKEN
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
     BALLBESITZ BALKEN
========================== -->


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



<div class="bar">


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

<span id="shotsHome">
0
</span>

:

<span id="shotsAway">
0
</span>

</div>

</div>





<div class="stat-box">

<h3>
SCHÜSSE AUFS TOR
</h3>

<div>

<span id="targetHome">
0
</span>

:

<span id="targetAway">
0
</span>

</div>

</div>





<div class="stat-box">

<h3>
GROSSCHANCEN
</h3>

<div>

<span id="chanceHome">
0
</span>

:

<span id="chanceAway">
0
</span>

</div>

</div>





<div class="stat-box">

<h3>
ECKEN
</h3>

<div>

<span id="cornerHome">
0
</span>

:

<span id="cornerAway">
0
</span>

</div>

</div>





<div class="stat-box">

<h3>
PÄSSE
</h3>

<div>

<span id="passesHome">
0/0
</span>

:

<span id="passesAway">
0/0
</span>

</div>

</div>





<div class="stat-box">

<h3>
GELBE KARTEN
</h3>

<div>

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


.big-stat{

margin-top:35px;

}



.big-stat h2{

text-align:center;

}



.big-values{

display:flex;

justify-content:space-between;

font-size:34px;

font-weight:bold;

padding:0 40px;

}



.bar{

height:32px;

display:flex;

background:#000;

border-radius:20px;

overflow:hidden;

border:1px solid #555;

margin-top:15px;

}



.home-bar{

height:100%;

background:var(--home);

}



.away-bar{

height:100%;

background:var(--away);

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

border-radius:20px;

padding:25px;

text-align:center;

font-size:30px;

box-shadow:

0 15px 35px #000;

}



.stat-box h3{

font-size:16px;

color:#aaa;

margin-bottom:15px;

}



</style>

</div>



<!-- ==========================
     SPIELDATEN TABELLE
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


.table-box{

margin-top:40px;

background:

linear-gradient(145deg,#222,#080808);

padding:25px;

border-radius:25px;

}



.table-box h2{

text-align:center;

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

border-radius:15px;

padding:15px;

font-size:16px;

}



</style>

<script>


const spieleDaten = {};

let aktuellesSpiel = null;





/* ==========================
   DATENSTRUKTUR
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

document
.getElementById("spieltagInput")
.value;



let zeilen=

text

.split("\n")

.map(x=>x.trim())

.filter(x=>x);



let liste=

document
.getElementById("spieleListe");



liste.innerHTML="";



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
teams.indexOf(zeilen[j])===-1
){

teams.push(zeilen[j]);

}


}



if(teams.length>=2){


erstelleSpiel(

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


function erstelleSpiel(

datum,

heim,

gast

){


let box=

document.createElement("div");



box.className="match-item";



box.innerHTML=

`

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




document

.getElementById("heimTeam")

.innerHTML=

heim;



document

.getElementById("gastTeam")

.innerHTML=

gast;



anzeigeAktualisieren();


}







/* ==========================
   DATEN ÜBERNEHMEN
========================== */


document

.getElementById("datenUebernehmen")

.onclick=function(){


datenEinlesen();


};





function datenEinlesen(){


if(!aktuellesSpiel)

return;



let text=

document

.getElementById("datenInput")

.value;



let s=

spieleDaten[aktuellesSpiel].stats;



let zeilen=

text

.split("\n")

.map(x=>x.trim())

.filter(x=>x);




function finde(wort){


let index=

zeilen.findIndex(

x=>

x.toLowerCase()

.includes(wort.toLowerCase())

);



if(index<0)

return [0,0];



return [

zahlen(zeilen[index-1]),

zahlen(zeilen[index+1])

];


}







function zahlen(t){


let n=

t.match(/\d+(?:[.,]\d+)?/g);



return n?

Number(

n[0].replace(",", ".")

)

:0;


}









let xg=

finde("Expected Goals");

s.xg.heim=xg[0];

s.xg.gast=xg[1];




let pos=

finde("Ballbesitz");

s.ballbesitz.heim=pos[0];

s.ballbesitz.gast=pos[1];





let sch=

finde("Schüsse insgesamt");

s.schuesse.heim=sch[0];

s.schuesse.gast=sch[1];





let tor=

finde("Schüsse aufs Tor");

s.aufsTor.heim=tor[0];

s.aufsTor.gast=tor[1];





let chance=

finde("Großchance");

s.grosschancen.heim=chance[0];

s.grosschancen.gast=chance[1];





let ecken=

finde("Eck");

s.ecken.heim=ecken[0];

s.ecken.gast=ecken[1];





let karten=

finde("Gelbe Karten");

s.karten.heim=karten[0];

s.karten.gast=karten[1];






let p=

text.match(/\d+\/\d+/g);



if(p && p.length>=2){


s.paesse.heim=p[0];


s.paesse.gast=p[1];


}





let q=

text.match(/\d+%/g);



if(q && q.length>=2){


s.passquote.heim=q[0];


s.passquote.gast=q[1];


}



anzeigeAktualisieren();


}





/* ==========================
   ANZEIGE AKTUALISIEREN
========================== */


function anzeigeAktualisieren(){



if(!aktuellesSpiel)

return;



let s=

spieleDaten[aktuellesSpiel].stats;






/* Balken Werte */


xgHeim.innerHTML=

s.xg.heim.toFixed(2);


xgGast.innerHTML=

s.xg.gast.toFixed(2);





possHeim.innerHTML=

s.ballbesitz.heim+"%";


possGast.innerHTML=

s.ballbesitz.gast+"%";






let xgGesamt=

s.xg.heim+s.xg.gast;


if(xgGesamt>0){


xgHomeBar.style.width=

(s.xg.heim/xgGesamt*100)+"%";


xgAwayBar.style.width=

(s.xg.gast/xgGesamt*100)+"%";


}



possHomeBar.style.width=

s.ballbesitz.heim+"%";


possAwayBar.style.width=

s.ballbesitz.gast+"%";







/* Kästchen */


shotsHome.innerHTML=

s.schuesse.heim;


shotsAway.innerHTML=

s.schuesse.gast;



targetHome.innerHTML=

s.aufsTor.heim;


targetAway.innerHTML=

s.aufsTor.gast;



chanceHome.innerHTML=

s.grosschancen.heim;


chanceAway.innerHTML=

s.grosschancen.gast;



cornerHome.innerHTML=

s.ecken.heim;


cornerAway.innerHTML=

s.ecken.gast;



passesHome.innerHTML=

s.paesse.heim;


passesAway.innerHTML=

s.paesse.gast;



cardsHome.innerHTML=

s.karten.heim;


cardsAway.innerHTML=

s.karten.gast;









/* Tabelle */


tabXgHome.innerHTML=

s.xg.heim.toFixed(2);


tabXgAway.innerHTML=

s.xg.gast.toFixed(2);



tabPossHome.innerHTML=

s.ballbesitz.heim+"%";


tabPossAway.innerHTML=

s.ballbesitz.gast+"%";



tabShotsHome.innerHTML=

s.schuesse.heim;


tabShotsAway.innerHTML=

s.schuesse.gast;



tabTargetHome.innerHTML=

s.aufsTor.heim;


tabTargetAway.innerHTML=

s.aufsTor.gast;



tabChanceHome.innerHTML=

s.grosschancen.heim;


tabChanceAway.innerHTML=

s.grosschancen.gast;



tabCornerHome.innerHTML=

s.ecken.heim;


tabCornerAway.innerHTML=

s.ecken.gast;



tabPassHome.innerHTML=

s.paesse.heim;


tabPassAway.innerHTML=

s.paesse.gast;



tabPassRateHome.innerHTML=

s.passquote.heim;


tabPassRateAway.innerHTML=

s.passquote.gast;



tabCardHome.innerHTML=

s.karten.heim;


tabCardAway.innerHTML=

s.karten.gast;



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

spieleDaten[aktuellesSpiel]

)

);



alert(

"Spiel gespeichert"

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


spieleDaten[aktuellesSpiel]

=

JSON.parse(daten);



anzeigeAktualisieren();



alert(

"Spiel geladen"

);



}



};









/* ==========================
   SPIELTAG SPEICHERN
========================== */


window.onload=function(){



let alt=

localStorage.getItem(

"Wettpropheten_Spieltag"

);



if(alt){


spieltagInput.value=alt;


}



};









document

.getElementById("spieleLaden")

.addEventListener(

"click",

function(){



localStorage.setItem(

"Wettpropheten_Spieltag",

spieltagInput.value

);



}

);



</script>



</div>

</div>


</body>

</html>
