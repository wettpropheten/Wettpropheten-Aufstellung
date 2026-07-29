<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

/* =========================
   GRUND SYSTEM
========================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,Helvetica,sans-serif;
}


:root{

    --heim-farbe:#0099ff;
    --gast-farbe:#ff3344;

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
   LINKER SPIELTAG
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



/* =========================
   BUTTON
========================= */


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



/* =========================
   SPIELKARTEN LINKS
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

    cursor:pointer;

}



.spielkarte:hover{

    border-color:#f5c542;

}



.spielzeit{

    color:#aaa;

    font-size:13px;

    margin-bottom:8px;

}



.verein{

    font-size:17px;

    font-weight:bold;

    margin:5px;

}



/* =========================
   RECHTER BEREICH
========================= */


.main{

    flex:1;

    height:100vh;

    padding:0;

    overflow-y:auto;

    background:

    linear-gradient(
    145deg,
    #191919,
    #050505
    );

}



/* =========================
   SPIELKOPF
========================= */


.spielkopf{

    margin:20px;

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



.team.heim{

    color:var(--heim-farbe);

}



.team.gast{

    color:var(--gast-farbe);

}



.ergebnis{

    text-align:center;

    font-size:85px;

    font-weight:bold;

    color:#f5c542;

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




<button class="button"
onclick="spieltagLaden()">

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


<div class="team heim">

HEIM

</div>



<div class="ergebnis">

0 : 0

</div>



<div class="team gast">

GAST

</div>



</div>
<!-- =========================
     TEIL 2 - SPIELTAG SYSTEM
========================= -->


<style>


/* =========================
   SPIELTAG KARTE
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

    cursor:pointer;

    transition:.2s;


}



.spielkarte:hover{


    border-color:#f5c542;

    transform:scale(1.02);


}



.spielzeit{


    color:#aaa;

    font-size:13px;

    margin-bottom:8px;


}



.verein{


    font-size:17px;

    font-weight:bold;

    margin:6px;


}


</style>





<script>


let spiele=[];



/* =========================
   BUNDESLIGA NAMEN
========================= */


const vereine=[


"1. FC Union Berlin",

"Eintracht Frankfurt",

"Bayern München",

"Bayer Leverkusen",

"Werder Bremen",

"Schalke 04",

"HSV",

"Borussia Dortmund",

"Borussia Mönchengladbach",

"TSG Hoffenheim",

"1. FC Köln",

"FSV Mainz 05",

"SC Freiburg",

"FC Augsburg",

"SC Paderborn",

"VfB Stuttgart",

"SV Elversberg",

"RB Leipzig"


];





/* =========================
   SPIELTAG LADEN
========================= */


function spieltagLaden(){



let text=document
.getElementById("spieltagInput")
.value;



let zeilen=text

.split("\n")

.map(z=>z.trim())

.filter(z=>z!=="");



spiele=[];



let liste=document
.getElementById("spielListe");



liste.innerHTML="";





for(let i=0;i<zeilen.length;i++){



if(/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])){



let spiel={


datum:zeilen[i],

heim:zeilen[i+1],

gast:zeilen[i+2]


};



if(spiel.heim && spiel.gast){



spiele.push(spiel);



spielkarteErstellen(spiel);



}



}



}



}







/* =========================
   SPIELKARTE ERSTELLEN
========================= */


function spielkarteErstellen(spiel){



let karte=document.createElement("div");



karte.className="spielkarte";



karte.innerHTML=`

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





karte.onclick=function(){


spielLaden(spiel);


};




document
.getElementById("spielListe")
.appendChild(karte);



}







/* =========================
   VEREINS FARBEN
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



document.documentElement.style.setProperty(

"--heim-farbe",

vereinsFarben[heim] || "#0099ff"

);



document.documentElement.style.setProperty(

"--gast-farbe",

vereinsFarben[gast] || "#ff3344"

);



}








/* =========================
   SPIEL LADEN
========================= */


function spielLaden(spiel){



document.querySelector(".team.heim")
.textContent=
spiel.heim;



document.querySelector(".team.gast")
.textContent=
spiel.gast;




document.querySelector(".ergebnis")
.textContent=
"0 : 0";





farbenSetzen(

spiel.heim,

spiel.gast

);




}





</script>
<!-- =========================
     TEIL 3 - xG + BALLBESITZ
========================= -->


<style>


/* =========================
   PANELS
========================= */


.xg-panel,
.ballbesitz-panel{


    margin:20px;

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



.xg-panel h2,
.ballbesitz-panel h2{


    color:#f5c542;

    margin-bottom:15px;


}





/* =========================
   WERTE
========================= */


.xg-werte,
.ball-werte{


    display:flex;

    justify-content:space-between;

    font-size:30px;

    font-weight:bold;

    margin-bottom:12px;


}



.heim-wert{

    color:var(--heim-farbe);

}



.gast-wert{

    color:var(--gast-farbe);

}





/* =========================
   BALKEN
========================= */


.xg-balken,
.ball-balken{


    width:100%;

    height:45px;

    display:flex;

    background:#000;

    border-radius:25px;

    overflow:hidden;


}



#xgHeimBalken,
#ballHeimBalken{


    width:50%;

    background:var(--heim-farbe);


}



#xgGastBalken,
#ballGastBalken{


    width:50%;

    background:var(--gast-farbe);


}



</style>







<!-- =========================
     xG PANEL
========================= -->


<div class="xg-panel">


<h2>

Expected Goals (xG)

</h2>



<div class="xg-werte">


<span class="heim-wert"
id="xgHeim">

0.00

</span>



<span class="gast-wert"
id="xgGast">

0.00

</span>


</div>




<div class="xg-balken">


<div id="xgHeimBalken"></div>


<div id="xgGastBalken"></div>


</div>



</div>








<!-- =========================
     BALLBESITZ PANEL
========================= -->


<div class="ballbesitz-panel">


<h2>

Ballbesitz

</h2>



<div class="ball-werte">


<span class="heim-wert"
id="ballHeimWert">

50%

</span>



<span class="gast-wert"
id="ballGastWert">

50%

</span>


</div>




<div class="ball-balken">


<div id="ballHeimBalken"></div>


<div id="ballGastBalken"></div>


</div>




</div>










<script>


/* =========================
   xG BALKEN BERECHNUNG
========================= */


function xGBalkenBerechnen(heim,gast){



let gesamt =
heim + gast;



if(gesamt===0){


xgHeimBalken.style.width="50%";

xgGastBalken.style.width="50%";


return;


}




let heimProzent =
(heim / gesamt) * 100;



let gastProzent =
(gast / gesamt) * 100;





xgHeimBalken.style.width =
heimProzent+"%";



xgGastBalken.style.width =
gastProzent+"%";



}







/* =========================
   BALLBESITZ SETZEN
========================= */


function ballbesitzSetzen(heim,gast){



ballHeimWert.textContent =
heim+"%";



ballGastWert.textContent =
gast+"%";




ballHeimBalken.style.width =
heim+"%";



ballGastBalken.style.width =
gast+"%";



}







/* TESTWERTE ENTFERNEN SPÄTER
   kommen aus Teil 5
*/


xGBalkenBerechnen(
0.81,
0.74
);


ballbesitzSetzen(
44,
56
);



</script>
<!-- =========================
     TEIL 4 - TOP STATISTIKEN
========================= -->


<style>


/* =========================
   GRID 3 NEBENEINANDER
========================= */


.top-statistik{


    margin:20px;

    display:grid;

    grid-template-columns:repeat(3,1fr);

    gap:20px;


}




/* =========================
   STAT BOX
========================= */


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





.stat-werte{


    display:flex;

    justify-content:center;

    align-items:center;

    gap:15px;


    font-size:32px;

    font-weight:bold;


}




.heim-stat{


    color:var(--heim-farbe);


}




.gast-stat{


    color:var(--gast-farbe);


}




.stat-info{


    color:#777;

    font-size:13px;

    margin-top:8px;


}




</style>







<div class="top-statistik">





<!-- SCHÜSSE -->


<div class="stat-box">


<h3>
SCHÜSSE
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="schuesseHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="schuesseGast">

0

</span>


</div>


</div>







<!-- SCHÜSSE AUFS TOR -->


<div class="stat-box">


<h3>
SCHÜSSE AUFS TOR
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="torHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="torGast">

0

</span>


</div>


</div>







<!-- GROSSCHANCEN -->


<div class="stat-box">


<h3>
GROSSCHANCEN
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="chanceHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="chanceGast">

0

</span>


</div>


</div>








<!-- ECKBÄLLE -->


<div class="stat-box">


<h3>
ECKBÄLLE
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="eckenHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="eckenGast">

0

</span>


</div>


</div>







<!-- PÄSSE -->


<div class="stat-box">


<h3>
PÄSSE
</h3>


<div class="stat-werte"
style="font-size:24px">


<span class="heim-stat"
id="paesseHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="paesseGast">

0

</span>


</div>



<div class="stat-info">

Gesamtpässe

</div>



</div>








<!-- PASSGENAUIGKEIT -->


<div class="stat-box">


<h3>
PASSGENAUIGKEIT
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="passHeim">

0%

</span>


<span>:</span>


<span class="gast-stat"
id="passGast">

0%

</span>


</div>


</div>







<!-- GELBE KARTEN -->


<div class="stat-box">


<h3>
GELBE KARTEN
</h3>


<div class="stat-werte">


<span class="heim-stat"
id="kartenHeim">

0

</span>


<span>:</span>


<span class="gast-stat"
id="kartenGast">

0

</span>


</div>


</div>






</div>
</body>
</html>
