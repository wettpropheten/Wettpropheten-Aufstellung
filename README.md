<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

/* =========================
RESET
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,Helvetica,sans-serif;
}


/* =========================
GRUNDLAYOUT
========================= */

html,
body{

    width:100%;
    height:100%;

    background:#050505;

    color:white;

    overflow:hidden;

}



.app{

    display:flex;

    width:100vw;

    height:100vh;

}



/* =========================
LINKER BEREICH
========================= */


.sidebar{

    width:300px;

    flex-shrink:0;

    height:100vh;

    padding:15px;

    background:
    linear-gradient(
    180deg,
    #252525,
    #080808
    );

    border-right:2px solid #444;

    overflow-y:auto;

}



.sidebar h1{

    text-align:center;

    color:#f5c542;

    font-size:28px;

    margin-bottom:20px;

}





textarea{

    width:100%;

    height:220px;

    padding:12px;

    background:#050505;

    color:white;

    border:1px solid #555;

    border-radius:15px;

    resize:none;

}





.button{

    width:100%;

    padding:13px;

    margin-top:10px;

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



.button:hover{

    border-color:#f5c542;

}





/* =========================
SPIELLISTE
========================= */


.spielkarte{

    margin-top:15px;

    padding:15px;

    background:

    linear-gradient(
    145deg,
    #333,
    #111
    );

    border-radius:18px;

    border:1px solid #555;

    text-align:center;

}



.spielkarte:hover{

    border-color:#f5c542;

    cursor:pointer;

}



.datum{

    color:#aaa;

    font-size:13px;

}



.teamname{

    margin:7px;

    font-size:17px;

    font-weight:bold;

}



/* =========================
HAUPTBEREICH
========================= */


.main{

    flex:1;

    height:100vh;

    overflow-y:auto;

    padding:0;

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


.spielkopf{

    margin-top:20px;

    margin-left:0;

    margin-right:20px;

    height:190px;

    display:grid;

    grid-template-columns:

    1fr 220px 1fr;


    align-items:center;


    background:#111;

    border-radius:30px;

    border:1px solid #333;

}





.team{

    text-align:center;

    font-size:40px;

    font-weight:bold;

}



.heim{

    color:#0099ff;

}



.gast{

    color:#ff3344;

}





.ergebnis{

    text-align:center;

    font-size:80px;

    font-weight:bold;

    color:#f5c542;

}






/* =========================
PANELS
========================= */


.panel{

    margin-top:20px;

    margin-right:20px;

    margin-left:0;

    padding:20px;


    background:

    linear-gradient(
    145deg,
    #222,
    #111
    );


    border-radius:25px;

    border:1px solid #333;

}



.panel h2{

    color:#f5c542;

    margin-bottom:15px;

}



</style>

</head>



<body>


<div class="app">



<!-- =========================
SIDEBAR
========================= -->


<div class="sidebar">


<h1>
SPIELTAG
</h1>



<textarea id="spieltagInput"

placeholder="

08.08.2026

Bayern München
Borussia Dortmund


09.08.2026

Union Berlin
Frankfurt

"></textarea>



<button class="button"

onclick="spieltagLaden()">

SPIELTAG LADEN

</button>




<div id="spielListe"></div>



</div>





<!-- =========================
MAIN
========================= -->


<div class="main">



<div class="spielkopf">


<div id="heimName"

class="team heim">

HEIM

</div>



<div class="ergebnis">

0 : 0

</div>




<div id="gastName"

class="team gast">

GAST

</div>



</div>




<div class="panel">

<h2>

Statistik

</h2>


<div id="statistikBereich">

Wird geladen...

</div>


</div>



<script>


let spiele=[];



/* =========================
SPIELTAG EINLESEN
========================= */


function spieltagLaden(){


let text=document
.getElementById("spieltagInput")
.value;



let zeilen=text
.split(/\n/)
.map(
x=>x.trim()
)
.filter(
x=>x!=""
);



spiele=[];



for(let i=0;i<zeilen.length;i++){



if(
/^\d{2}\.\d{2}\.\d{4}$/
.test(
zeilen[i]
)

){


let datum=zeilen[i];

let heim=zeilen[i+1];

let gast=zeilen[i+2];



if(
heim &&
gast
){


spiele.push({

datum:datum,

heim:heim,

gast:gast


});



}



}


}



spieleAnzeigen();


}




/* =========================
SPIELE ANZEIGEN
========================= */


function spieleAnzeigen(){


let liste=document
.getElementById("spielListe");



liste.innerHTML="";



spiele.forEach(
function(spiel){



let box=document
.createElement("div");



box.className="spielkarte";



box.innerHTML=`

<div class="datum">

${spiel.datum}

</div>


<div class="teamname">

${spiel.heim}

</div>


<div>

VS

</div>


<div class="teamname">

${spiel.gast}

</div>

`;



box.onclick=function(){


spielLaden(spiel);


};



liste.appendChild(box);



}

);



}





/* =========================
SPIEL RECHTS LADEN
========================= */


function spielLaden(spiel){



document
.getElementById("heimName")
.textContent=

spiel.heim;



document
.getElementById("gastName")
.textContent=

spiel.gast;



}

<!-- =========================
TEIL 2
xG / BALLBESITZ / BALKEN
========================= -->


<style>


.statistik-grid{


    display:grid;

    grid-template-columns:

    repeat(2,1fr);

    gap:15px;


}



.stat-box{


    background:#050505;

    border:1px solid #555;

    border-radius:18px;

    padding:15px;

    text-align:center;


}



.stat-box h3{


    color:#aaa;

    margin-bottom:10px;


}



.stat-wert{


    font-size:35px;

    font-weight:bold;

    color:#f5c542;


}





.balken-box{


    margin-top:20px;


}



.balken-titel{


    display:flex;

    justify-content:space-between;

    margin-bottom:8px;


}



.balken{


    width:100%;

    height:28px;

    background:#333;

    border-radius:20px;

    overflow:hidden;

    border:1px solid #555;


}



.balken-heim{


    height:100%;

    width:50%;

    background:#0099ff;

    transition:.3s;


}




.ball-zeile{


    display:flex;

    justify-content:space-between;

    margin-top:8px;

    font-size:18px;


}



</style>





<script>


/* =========================
STATISTIK DATEN
========================= */



let daten={


xgHeim:1.00,


xgGast:1.00,


ballHeim:50,


ballGast:50,


paesseHeim:0,


paesseGast:0,


passquoteHeim:0,


passquoteGast:0



};





/* =========================
STATISTIK AUSGABE
========================= */



function statistikAnzeigen(){



document
.getElementById("statistikBereich")
.innerHTML=`

<div class="statistik-grid">


<div class="stat-box">

<h3>

xG Heim

</h3>

<div class="stat-wert">

${daten.xgHeim.toFixed(2)}

</div>

</div>



<div class="stat-box">

<h3>

xG Gast

</h3>


<div class="stat-wert">

${daten.xgGast.toFixed(2)}

</div>

</div>



<div class="stat-box">

<h3>

Pässe Heim

</h3>


<div class="stat-wert">

${daten.paesseHeim}

</div>

</div>




<div class="stat-box">

<h3>

Pässe Gast

</h3>


<div class="stat-wert">

${daten.paesseGast}

</div>

</div>



</div>





<div class="balken-box">


<div class="balken-titel">

<span>

Ballbesitz Heim

</span>


<span>

Ballbesitz Gast

</span>


</div>




<div class="balken">


<div class="balken-heim"

style="width:${daten.ballHeim}%">

</div>


</div>



<div class="ball-zeile">


<span>

${daten.ballHeim}%

</span>



<span>

${daten.ballGast}%

</span>



</div>



</div>





<div class="stat-box"

style="margin-top:20px">


<h3>

Passquote

</h3>



<div>

Heim:

${daten.passquoteHeim}%

</div>



<div>

Gast:

${daten.passquoteGast}%

</div>



</div>


`;



}






/* =========================
AUTOMATISCHE BERECHNUNG
========================= */


function passQuoteBerechnen(){


if(daten.paesseHeim>0){

daten.passquoteHeim=

Math.min(
100,
Math.round(
daten.paesseHeim / 600 *100
)

);


}



if(daten.paesseGast>0){


daten.passquoteGast=

Math.min(
100,
Math.round(
daten.paesseGast / 600 *100
)

);



}



}





/* =========================
WERTE ÄNDERN
========================= */



function statistikSetzen(

xgH,

xgG,

ball,

passH,

passG

){



daten.xgHeim=

Number(xgH);



daten.xgGast=

Number(xgG);



daten.ballHeim=

Number(ball);



daten.ballGast=

100-Number(ball);



daten.paesseHeim=

Number(passH);



daten.paesseGast=

Number(passG);



passQuoteBerechnen();



statistikAnzeigen();



}





/* STARTANZEIGE */


statistikAnzeigen();



</script>
<!-- =========================
TEIL 3
LIVE STATISTIK STEUERUNG
========================= -->


<style>


.steuerung{


    display:grid;

    grid-template-columns:

    repeat(2,1fr);

    gap:15px;


}



.input-box{


    background:#050505;

    border:1px solid #555;

    border-radius:15px;

    padding:15px;


}



.input-box label{


    display:block;

    color:#aaa;

    margin-bottom:6px;


}



.input-box input{


    width:100%;

    padding:10px;


    background:#111;

    color:white;


    border:1px solid #666;

    border-radius:10px;


    font-size:18px;


}




.aktualisieren{


    grid-column:1 / -1;


}



</style>






<div class="panel">


<h2>

Live Statistik ändern

</h2>




<div class="steuerung">



<div class="input-box">


<label>

xG Heim

</label>


<input 

id="inputXgHeim"

type="number"

step="0.01"

value="1.00">


</div>





<div class="input-box">


<label>

xG Gast

</label>


<input 

id="inputXgGast"

type="number"

step="0.01"

value="1.00">


</div>






<div class="input-box">


<label>

Ballbesitz Heim %

</label>


<input 

id="inputBall"

type="number"

min="0"

max="100"

value="50">


</div>






<div class="input-box">


<label>

Pässe Heim

</label>


<input 

id="inputPassHeim"

type="number"

value="0">


</div>







<div class="input-box">


<label>

Pässe Gast

</label>


<input 

id="inputPassGast"

type="number"

value="0">


</div>






<div class="aktualisieren">


<button 

class="button"

onclick="liveUpdate()">


STATISTIK AKTUALISIEREN


</button>



</div>



</div>


</div>








<script>


/* =========================
LIVE UPDATE
========================= */


function liveUpdate(){



let xgH=

document
.getElementById("inputXgHeim")
.value;




let xgG=

document
.getElementById("inputXgGast")
.value;




let ball=

document
.getElementById("inputBall")
.value;




let passH=

document
.getElementById("inputPassHeim")
.value;




let passG=

document
.getElementById("inputPassGast")
.value;





if(ball<0){

ball=0;

}



if(ball>100){

ball=100;

}





statistikSetzen(

xgH,

xgG,

ball,

passH,

passG

);



}





/* =========================
AUTOMATISCHES UPDATE
========================= */


document
.querySelectorAll(".input-box input")
.forEach(

function(input){



input.addEventListener(

"change",

function(){


liveUpdate();


}

);



}

);





</script>
<!-- =========================
TEIL 4
SPEICHERN / LADEN
========================= -->



<style>


.speicher-status{


    margin-top:15px;


    padding:15px;


    background:#050505;


    border-radius:15px;


    border:1px solid #555;


    color:#aaa;


    text-align:center;


}



</style>





<div class="panel">


<h2>

Dashboard speichern

</h2>




<button class="button"

onclick="dashboardSpeichern()">


💾 DATEN SPEICHERN


</button>




<button class="button"

onclick="dashboardLaden()">


📂 DATEN LADEN


</button>




<div class="speicher-status"

id="speicherStatus">


Bereit


</div>



</div>







<script>


/* =========================
SPEICHERN
========================= */


function dashboardSpeichern(){



let speicher={



spiele:spiele,



heim:

document
.getElementById("heimName")
.textContent,



gast:

document
.getElementById("gastName")
.textContent,



statistik:daten,



zeit:

new Date()
.toLocaleString("de-DE")



};






localStorage.setItem(

"WettprophetenDashboard",

JSON.stringify(speicher)

);





document
.getElementById("speicherStatus")
.textContent=

"Gespeichert: "

+

speicher.zeit;



}







/* =========================
LADEN
========================= */


function dashboardLaden(){



let datenGespeichert=

localStorage.getItem(

"WettprophetenDashboard"

);




if(!datenGespeichert){



document
.getElementById("speicherStatus")
.textContent=

"Keine Daten vorhanden";


return;


}






let speicher=

JSON.parse(

datenGespeichert

);






/* SPIELE WIEDERHERSTELLEN */


spiele=

speicher.spiele || [];



spieleAnzeigen();







/* AKTUELLES SPIEL */


if(
speicher.heim
){


document
.getElementById("heimName")
.textContent=

speicher.heim;



}





if(
speicher.gast
){


document
.getElementById("gastName")
.textContent=

speicher.gast;



}








/* STATISTIK */


if(
speicher.statistik

){



daten=

speicher.statistik;



statistikAnzeigen();



}







document
.getElementById("speicherStatus")
.textContent=

"Geladen: "

+

speicher.zeit;



}





</script>
<!-- =========================
TEIL 5
ABSCHLUSS / STARTSYSTEM
========================= -->



<script>


/* =========================
START KONTROLLE
========================= */


window.onload=function(){



/*
Falls bereits Daten gespeichert sind,
kann das Dashboard wiederhergestellt werden
*/


let vorhanden=

localStorage.getItem(

"WettprophetenDashboard"

);




if(vorhanden){



let laden=

confirm(

"Gespeicherte Dashboard-Daten laden?"

);



if(laden){


dashboardLaden();



}


}





/*
Startwerte anzeigen,
falls keine Daten vorhanden sind
*/


statistikAnzeigen();



};





/* =========================
SICHERHEIT
========================= */


function sichereZahl(wert, standard){



let zahl=

Number(wert);



if(
isNaN(zahl)
){


return standard;


}



return zahl;



}





</script>



</div>


</div>


</body>

</html>


</script>
