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


body{

    width:100%;
    height:100vh;
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

    width:280px;
    min-width:280px;

    height:100vh;

    background:
    linear-gradient(
        180deg,
        #252525,
        #080808
    );

    border-right:2px solid #444;

    padding:15px;

}



.sidebar h1{

    text-align:center;

    color:#f5c542;

    font-size:28px;

    margin-bottom:20px;

}



.spieltag-box{

    height:calc(100vh - 90px);

    background:#111;

    border-radius:20px;

    border:1px solid #444;

    padding:15px;

    overflow-y:auto;

}




#spieltagInput{

    width:100%;

    height:220px;

    background:#050505;

    color:white;

    border:1px solid #555;

    border-radius:15px;

    padding:15px;

    resize:none;

}





.button{

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

    cursor:pointer;

}



.spielkarte:hover{

    border-color:#f5c542;

}



.spielzeit{

    color:#aaa;

    font-size:13px;

}



.verein{

    font-size:17px;

    font-weight:bold;

    margin:5px;

}





/* =========================
HAUPTBEREICH
========================= */


.main{


    flex:1;

    height:100vh;

    padding:20px;

    background:

    linear-gradient(
    145deg,
    #191919,
    #050505
    );

    overflow-y:auto;


}




/* =========================
SPIELKOPF
========================= */


.spielkopf{


    width:100%;

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




.ergebnis{


    text-align:center;

    font-size:85px;

    font-weight:bold;

    color:#f5c542;

}





.heim{

    color:#0099ff;

}



.gast{

    color:#ff3344;

}





/* =========================
xG BASIS
========================= */


.panel{


    margin-top:25px;

    padding:25px;

    background:

    linear-gradient(
    145deg,
    #252525,
    #101010
    );


    border-radius:25px;

    border:1px solid #333;


}



.panel h2{

    color:#f5c542;

    margin-bottom:15px;

}




.balken{


    width:100%;

    height:45px;

    background:#000;

    border-radius:25px;

    overflow:hidden;

    display:flex;


}




.heim-balken{

    width:50%;

    background:#0099ff;

}



.gast-balken{

    width:50%;

    background:#ff3344;

}



</style>


</head>



<body>


<div class="app">



<!-- =========================
LINKS SPIELTAG
========================= -->


<div class="sidebar">


<h1>SPIELTAG</h1>


<div class="spieltag-box">


<textarea id="spieltagInput"
placeholder="
08.08.2026

1. FC Union Berlin
Eintracht Frankfurt

-
">
</textarea>



<button class="button" onclick="spieltagLaden()">

SPIELTAG LADEN

</button>



<div id="spielListe"></div>



</div>


</div>





<!-- =========================
RECHTS
========================= -->


<div class="main">


<div class="spielkopf">


<div class="team heim" id="heimTeam">

HEIM

</div>



<div class="ergebnis">

0 : 0

</div>



<div class="team gast" id="gastTeam">

GAST

</div>



</div>




<div class="panel">


<h2>

Expected Goals (xG)

</h2>



<div class="balken">


<div class="heim-balken"></div>


<div class="gast-balken"></div>


</div>



</div>



</div>


</div>





<script>


let spiele=[];



function spieltagLaden(){


let text=
document.getElementById("spieltagInput").value;



let zeilen=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x!=="");



spiele=[];


document.getElementById("spielListe").innerHTML="";



for(let i=0;i<zeilen.length;i++){



if(/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])){


let spiel={


datum:zeilen[i],

heim:zeilen[i+1],

gast:zeilen[i+2]


};



spiele.push(spiel);



karteErstellen(spiel);



}


}


}





function karteErstellen(spiel){


let div=document.createElement("div");


div.className="spielkarte";


div.innerHTML=`

<div class="spielzeit">
${spiel.datum}
</div>


<div class="verein">
${spiel.heim}
</div>


<div>
VS
</div>


<div class="verein">
${spiel.gast}
</div>

`;



div.onclick=function(){

spielLaden(spiel);

};



document
.getElementById("spielListe")
.appendChild(div);



}





function spielLaden(spiel){


document.getElementById("heimTeam")
.textContent=
spiel.heim;



document.getElementById("gastTeam")
.textContent=
spiel.gast;



}



</script>

<!-- =========================
     TEIL 2 - VEREINS FARB SYSTEM
========================= -->


<style>


:root{

    --heim-farbe:#0099ff;

    --gast-farbe:#ff3344;

}



/* Team Farben */

.team.heim{

    color:var(--heim-farbe)!important;

}



.team.gast{

    color:var(--gast-farbe)!important;

}



/* Balken Farben */

.heim-balken{

    background:var(--heim-farbe)!important;

}



.gast-balken{

    background:var(--gast-farbe)!important;

}



</style>





<script>


/* =========================
   VEREINS DATENBANK
   EXAKTE SCHREIBWEISE
========================= */


const vereinsFarben={



"1. FC Union Berlin":"#eb0016",

"Eintracht Frankfurt":"#e1000f",

"Bayern München":"#dc052d",

"Bayer Leverkusen":"#e32221",

"Werder Bremen":"#1d9053",

"Schalke 04":"#004d9f",

"HSV":"#0066b3",

"Borussia Dortmund":"#f6d800",

"Borussia Mönchengladbach":"#009b3a",

"TSG Hoffenheim":"#005ca9",

"1. FC Köln":"#ffffff",

"FSV Mainz 05":"#c31432",

"SC Freiburg":"#e2001a",

"FC Augsburg":"#ba3733",

"SC Paderborn":"#005ca9",

"VfB Stuttgart":"#e32219",

"SV Elversberg":"#111111",

"RB Leipzig":"#dd0000"



};







/* =========================
   FARBEN SETZEN
========================= */


function farbenSetzen(heim,gast){



let heimFarbe=

vereinsFarben[heim]
||
"#0099ff";



let gastFarbe=

vereinsFarben[gast]
||
"#ff3344";





document.documentElement.style.setProperty(

"--heim-farbe",

heimFarbe

);



document.documentElement.style.setProperty(

"--gast-farbe",

gastFarbe

);



}







/* =========================
   SPIEL LADEN ERWEITERN
========================= */


const alteSpielLaden=

spielLaden;



spielLaden=function(spiel){



alteSpielLaden(spiel);



farbenSetzen(

spiel.heim,

spiel.gast

);




/* Balken zurücksetzen */

document.querySelector(".heim-balken")
.style.width="50%";



document.querySelector(".gast-balken")
.style.width="50%";



};



</script>
<!-- =========================
     TEIL 3 - xG + BALLBESITZ
========================= -->


<style>


/* gemeinsames Balken-System */


.stat-balken-panel{

    margin-top:25px;

    padding:25px;

    background:
    linear-gradient(
        145deg,
        #252525,
        #101010
    );

    border-radius:25px;

    border:1px solid #333;

}



.stat-balken-panel h2{

    color:#f5c542;

    margin-bottom:15px;

}



.balken-werte{

    display:flex;

    justify-content:space-between;

    font-size:24px;

    font-weight:bold;

    margin-bottom:10px;

}



.balken-heim-text{

    color:var(--heim-farbe);

}



.balken-gast-text{

    color:var(--gast-farbe);

}





.stat-balken{

    width:100%;

    height:45px;

    background:#000;

    border-radius:25px;

    overflow:hidden;

    display:flex;

}



#xgHeim{

    width:50%;

}



#xgGast{

    width:50%;

}



#besitzHeim{

    width:50%;

}



#besitzGast{

    width:50%;

}



</style>





<!-- =========================
     xG BALKEN
========================= -->


<div class="stat-balken-panel">


<h2>
Expected Goals (xG)
</h2>



<div class="balken-werte">

<span class="balken-heim-text" id="xgWertHeim">
0.00
</span>


<span class="balken-gast-text" id="xgWertGast">
0.00
</span>


</div>




<div class="stat-balken">


<div id="xgHeim"
class="heim-balken">
</div>


<div id="xgGast"
class="gast-balken">
</div>


</div>



</div>







<!-- =========================
     BALLBESITZ BALKEN
========================= -->


<div class="stat-balken-panel">


<h2>
Ballbesitz
</h2>



<div class="balken-werte">


<span class="balken-heim-text" id="besitzWertHeim">
50%
</span>


<span class="balken-gast-text" id="besitzWertGast">
50%
</span>



</div>



<div class="stat-balken">


<div id="besitzHeim"
class="heim-balken">
</div>


<div id="besitzGast"
class="gast-balken">
</div>


</div>



</div>








<script>


/* =========================
   PROZENT AUS xG BERECHNEN
========================= */


function xGBerechnen(a,b){


let gesamt=a+b;


if(gesamt===0){

return [50,50];

}



return [

(a/gesamt*100),

(b/gesamt*100)

];


}









/* =========================
   xG AUSLESEN
========================= */


function xGAuslesen(text){



let daten=text.match(

/xG\s*\n\s*([\d.,]+)\s*\n\s*([\d.,]+)/i

);



if(daten){


let heim=parseFloat(

daten[1].replace(",", ".")

);



let gast=parseFloat(

daten[2].replace(",", ".")

);



return [

heim,

gast

];


}



return [

0,

0

];


}








/* =========================
   DATEN FUNKTION ERWEITERN
========================= */


const alteDatenUebernehmen = datenUebernehmen;



datenUebernehmen=function(){



alteDatenUebernehmen();



let text=document

.getElementById("liveDaten")

.value;





/* xG */


let xg=xGAuslesen(text);



document.getElementById("xgWertHeim")

.textContent=

xg[0].toFixed(2);



document.getElementById("xgWertGast")

.textContent=

xg[1].toFixed(2);






let breite=xGBerechnen(

xg[0],

xg[1]

);





document.getElementById("xgHeim")

.style.width=

breite[0]+"%";



document.getElementById("xgGast")

.style.width=

breite[1]+"%";






/* Ballbesitz */


let ball=text.match(

/Ballbesitz\s*\n\s*(\d+)%\s*\n\s*(\d+)%/i

);



if(ball){



document.getElementById("besitzWertHeim")

.textContent=

ball[1]+"%";



document.getElementById("besitzWertGast")

.textContent=

ball[2]+"%";



document.getElementById("besitzHeim")

.style.width=

ball[1]+"%";



document.getElementById("besitzGast")

.style.width=

ball[2]+"%";



}



};



</script>
<!-- =========================
     TEIL 4 - TOP STATISTIK KÄSTCHEN
========================= -->


<style>


.top-statistik{


    margin-top:25px;


    display:grid;


    grid-template-columns:repeat(3,1fr);


    gap:20px;


}




.stat-box{


    background:

    linear-gradient(
        145deg,
        #333,
        #111
    );


    border-radius:20px;


    border:1px solid #444;


    padding:20px;


    text-align:center;


}





.stat-box h3{


    color:#aaa;


    font-size:15px;


    margin-bottom:15px;


}





.stat-wert{


    display:flex;


    justify-content:center;


    align-items:center;


    gap:15px;


    font-size:32px;


    font-weight:bold;


}





.heim-wert{


    color:var(--heim-farbe);


}




.gast-wert{


    color:var(--gast-farbe);


}




.stat-info{


    margin-top:8px;


    color:#777;


    font-size:13px;


}



</style>






<div class="top-statistik">





<div class="stat-box">

<h3>
SCHÜSSE
</h3>


<div class="stat-wert">

<span class="heim-wert" id="schuesseHeim">
0
</span>

:

<span class="gast-wert" id="schuesseGast">
0
</span>

</div>

</div>







<div class="stat-box">

<h3>
SCHÜSSE AUFS TOR
</h3>


<div class="stat-wert">

<span class="heim-wert" id="torHeim">
0
</span>

:

<span class="gast-wert" id="torGast">
0
</span>

</div>

</div>








<div class="stat-box">

<h3>
GROSSCHANCEN
</h3>


<div class="stat-wert">

<span class="heim-wert" id="chanceHeim">
0
</span>

:

<span class="gast-wert" id="chanceGast">
0
</span>

</div>

</div>







<div class="stat-box">

<h3>
ECKBÄLLE
</h3>


<div class="stat-wert">

<span class="heim-wert" id="eckenHeim">
0
</span>

:

<span class="gast-wert" id="eckenGast">
0
</span>

</div>

</div>







<div class="stat-box">

<h3>
PÄSSE
</h3>


<div class="stat-wert">

<span class="heim-wert" id="paesseHeim">
0
</span>

:

<span class="gast-wert" id="paesseGast">
0
</span>

</div>


<div class="stat-info">
Gesamtpässe
</div>


</div>







<div class="stat-box">

<h3>
PASSGENAUIGKEIT
</h3>


<div class="stat-wert">

<span class="heim-wert" id="passHeim">
0%
</span>

:

<span class="gast-wert" id="passGast">
0%
</span>

</div>


</div>







<div class="stat-box">

<h3>
GELBE KARTEN
</h3>


<div class="stat-wert">

<span class="heim-wert" id="kartenHeim">
0
</span>

:

<span class="gast-wert" id="kartenGast">
0
</span>

</div>


</div>



</div>
<!-- =========================
     TEIL 5 - LIVE DATEN SYSTEM
========================= -->


<style>


.live-bereich{


    margin-top:25px;


    background:

    linear-gradient(
        145deg,
        #252525,
        #101010
    );


    border-radius:25px;


    border:1px solid #333;


    padding:25px;


}



.live-bereich h2{


    color:#f5c542;


    margin-bottom:15px;


}




#liveDaten{


    width:100%;


    height:260px;


    background:#050505;


    color:white;


    border:1px solid #555;


    border-radius:15px;


    padding:15px;


    resize:none;


    font-size:16px;


}



</style>






<div class="live-bereich">


<h2>
LIVE DATEN
</h2>



<textarea id="liveDaten"

placeholder="

xG
0.81
0.74


Ballbesitz
44%
56%


Schüsse insgesamt
12
7


Schüsse aufs Tor
4
1


Großchance
1
2


Eckbälle
5
4


Pässe
372/433
475/552


Passgenauigkeit
86%
86%


Gelbe Karten
0
1

"></textarea>





<button class="button"

onclick="datenUebernehmen()">

DATEN ÜBERNEHMEN

</button>



</div>









<script>


/* =========================
   ZAHLEN AUSLESEN
========================= */


function zahlenPaar(text,titel){


let regex=new RegExp(

titel+
"\\s*\\n\\s*(\\d+)\\s*\\n\\s*(\\d+)",

"i"

);



let wert=text.match(regex);



if(wert){

return [

wert[1],

wert[2]

];

}



return [

"0",

"0"

];


}







function prozentPaar(text,titel){


let regex=new RegExp(

titel+
"\\s*\\n\\s*(\\d+)%\\s*\\n\\s*(\\d+)%",

"i"

);



let wert=text.match(regex);



if(wert){

return [

wert[1],
wert[2]

];

}


return [

"0",
"0"

];


}








/* =========================
   LIVE UPDATE
========================= */


function datenUebernehmen(){



let text=document

.getElementById("liveDaten")

.value;







/* SCHÜSSE */


let schuesse=

zahlenPaar(
text,
"Schüsse insgesamt"
);



schuesseHeim.textContent=schuesse[0];

schuesseGast.textContent=schuesse[1];








/* SCHÜSSE AUFS TOR */


let tor=

zahlenPaar(
text,
"Schüsse aufs Tor"
);



torHeim.textContent=tor[0];

torGast.textContent=tor[1];







/* GROSSCHANCEN */


let chance=

zahlenPaar(
text,
"Großchance"
);



chanceHeim.textContent=chance[0];

chanceGast.textContent=chance[1];








/* ECKEN */


let ecken=

zahlenPaar(
text,
"Eckbälle"
);



eckenHeim.textContent=ecken[0];

eckenGast.textContent=ecken[1];








/* KARTEN */


let karten=

zahlenPaar(
text,
"Gelbe Karten"
);



kartenHeim.textContent=karten[0];

kartenGast.textContent=karten[1];








/* PÄSSE */


let paesse=text.match(

/Pässe\s*\n\s*(\d+)\/\d+\s*\n\s*(\d+)\/\d+/i

);



if(paesse){


paesseHeim.textContent=paesse[1];

paesseGast.textContent=paesse[2];


}








/* PASSGENAUIGKEIT */


let pass=

prozentPaar(
text,
"Passgenauigkeit"
);



passHeim.textContent=

pass[0]+"%";


passGast.textContent=

pass[1]+"%";








/* BALLBESITZ */


let ball=

prozentPaar(
text,
"Ballbesitz"
);



if(ball[0]!="0"){


besitzWertHeim.textContent=

ball[0]+"%";


besitzWertGast.textContent=

ball[1]+"%";



besitzHeim.style.width=

ball[0]+"%";


besitzGast.style.width=

ball[1]+"%";


}








/* xG */


let xg=text.match(

/xG\s*\n\s*([\d.,]+)\s*\n\s*([\d.,]+)/i

);



if(xg){



let heim=parseFloat(

xg[1].replace(",", ".")

);



let gast=parseFloat(

xg[2].replace(",", ".")

);



xgWertHeim.textContent=

heim.toFixed(2);



xgWertGast.textContent=

gast.toFixed(2);





let gesamt=

heim+gast;



if(gesamt>0){



xgHeim.style.width=

(heim/gesamt*100)+"%";



xgGast.style.width=

(gast/gesamt*100)+"%";


}



}



}


</script>

</body>

</html>
