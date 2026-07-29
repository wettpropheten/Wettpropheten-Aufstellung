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


html,
body{

    width:100%;
    height:100%;

    background:#050505;
    color:white;

    overflow:hidden;

}


/* =========================
APP
========================= */

.app{

    width:100vw;
    height:100vh;

    display:flex;

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
SPIELKARTEN
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
RECHTE SEITE
========================= */


.main{

    flex:1;

    height:100vh;

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

    margin-top:20px;

    margin-left:0;

    margin-right:20px;

    height:190px;


    display:grid;

    grid-template-columns:
    1fr 220px 1fr;


    align-items:center;


    background:#111;

    border:1px solid #333;

    border-radius:30px;

}



.team{

    text-align:center;

    font-size:40px;

    font-weight:bold;

}



:root{

    --heim-farbe:#0099ff;

    --gast-farbe:#ff3344;

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
LINKS
========================= -->


<div class="sidebar">


<h1>
SPIELTAG
</h1>



<div class="spieltag-box">



<textarea id="spieltagInput">

08.08.2026

1. FC Union Berlin

Eintracht Frankfurt


09.08.2026

Bayern München

Borussia Dortmund

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


<div class="team heim" id="heimName">

HEIM

</div>



<div class="ergebnis">

0 : 0

</div>



<div class="team gast" id="gastName">

GAST

</div>



</div>





<!-- TEIL 2 FOLGT -->
<!-- =========================
SPIELTAG SYSTEM
========================= -->


<script>

let spiele=[];


/* =========================
SPIELTAG LADEN
========================= */


function spieltagLaden(){


let text=document
.getElementById("spieltagInput")
.value;



let zeilen=text
.split("\n")
.map(x=>x.trim())
.filter(x=>x!=="");



spiele=[];



let liste=document
.getElementById("spielListe");



liste.innerHTML="";



for(let i=0;i<zeilen.length;i++){



    if(/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])){


        let datum=zeilen[i];

        let heim=zeilen[i+1];

        let gast=zeilen[i+2];



        if(heim && gast){


            let spiel={

                datum:datum,

                heim:heim,

                gast:gast

            };


            spiele.push(spiel);


            spielkarteErstellen(spiel);


        }


    }


}



}





/* =========================
SPIELKARTE
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
SPIEL LADEN
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



document
.querySelector(".ergebnis")
.textContent=

"0 : 0";



farbenSetzen(
spiel.heim,
spiel.gast
);



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








function farbenSetzen(heim,gast){



let heimFarbe=

vereinsFarben[heim]

||

"#0099ff";



let gastFarbe=

vereinsFarben[gast]

||

"#ff3344";





document.documentElement
.style
.setProperty(

"--heim-farbe",

heimFarbe

);





document.documentElement
.style
.setProperty(

"--gast-farbe",

gastFarbe

);



}



</script>





<!-- =========================
xG + BALLBESITZ + TOP STATISTIKEN
========================= -->


<style>


.panel{

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



.panel h2{

    color:#f5c542;

    margin-bottom:15px;

}



.wert-zeile{

    display:flex;

    justify-content:space-between;

    font-size:28px;

    font-weight:bold;

    margin-bottom:12px;

}



.balken{

    width:100%;

    height:45px;

    background:#000;

    border-radius:25px;

    display:flex;

    overflow:hidden;

}



#xgBalkenHeim{

    width:50%;

    background:var(--heim-farbe);

}



#xgBalkenGast{

    width:50%;

    background:var(--gast-farbe);

}



#ballHeim{

    width:50%;

    background:var(--heim-farbe);

}



#ballGast{

    width:50%;

    background:var(--gast-farbe);

}




.heim-stat{

    color:var(--heim-farbe);

}



.gast-stat{

    color:var(--gast-farbe);

}




/* =========================
TOP KÄSTCHEN 3 NEBENEINANDER
========================= */


.top-statistik{


    margin:20px;

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



.stat-werte{


    display:flex;

    justify-content:center;

    align-items:center;

    gap:15px;

    font-size:32px;

    font-weight:bold;


}



</style>







<!-- =========================
EXPECTED GOALS
========================= -->


<div class="panel">


<h2>
Expected Goals (xG)
</h2>



<div class="wert-zeile">


<span class="heim-stat" id="xgHeim">
0.00
</span>


<span class="gast-stat" id="xgGast">
0.00
</span>


</div>




<div class="balken">


<div id="xgBalkenHeim"></div>


<div id="xgBalkenGast"></div>


</div>


</div>







<!-- =========================
BALLBESITZ
========================= -->


<div class="panel">


<h2>
Ballbesitz
</h2>



<div class="wert-zeile">


<span class="heim-stat" id="ballTextHeim">
50%
</span>


<span class="gast-stat" id="ballTextGast">
50%
</span>


</div>




<div class="balken">


<div id="ballHeim"></div>


<div id="ballGast"></div>


</div>



</div>







<!-- =========================
TOP STATISTIKEN
========================= -->


<div class="top-statistik">



<div class="stat-box">

<h3>
SCHÜSSE
</h3>

<div class="stat-werte">

<span class="heim-stat" id="schuesseHeim">
0
</span>

:

<span class="gast-stat" id="schuesseGast">
0
</span>

</div>

</div>






<div class="stat-box">

<h3>
SCHÜSSE AUFS TOR
</h3>

<div class="stat-werte">

<span class="heim-stat" id="torHeim">
0
</span>

:

<span class="gast-stat" id="torGast">
0
</span>

</div>

</div>






<div class="stat-box">

<h3>
GROSSCHANCEN
</h3>

<div class="stat-werte">

<span class="heim-stat" id="chanceHeim">
0
</span>

:

<span class="gast-stat" id="chanceGast">
0
</span>

</div>

</div>






<div class="stat-box">

<h3>
ECKBÄLLE
</h3>

<div class="stat-werte">

<span class="heim-stat" id="eckenHeim">
0
</span>

:

<span class="gast-stat" id="eckenGast">
0
</span>

</div>

</div>






<div class="stat-box">

<h3>
PÄSSE
</h3>

<div class="stat-werte">

<span class="heim-stat" id="paesseHeim">
0
</span>

:

<span class="gast-stat" id="paesseGast">
0
</span>

</div>

</div>






<div class="stat-box">

<h3>
PASSGENAUIGKEIT
</h3>

<div class="stat-werte">

<span class="heim-stat" id="passHeim">
0%
</span>

:

<span class="gast-stat" id="passGast">
0%
</span>

</div>

</div>





<div class="stat-box">

<h3>
GELBE KARTEN
</h3>

<div class="stat-werte">

<span class="heim-stat" id="kartenHeim">
0
</span>

:

<span class="gast-stat" id="kartenGast">
0
</span>

</div>

</div>



</div>





<!-- =========================
LIVE DATEN SYSTEM
========================= -->


<style>


.live-bereich{


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



function paarLesen(text,titel){


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







function prozentLesen(text,titel){


let regex=new RegExp(

titel+
"\\s*\\n\\s*(\\d+)%\\s*\\n\\s*(\\d+)%",

"i"

);



let wert=text.match(regex);



if(wert){

return [

wert[1]+"%",
wert[2]+"%"

];

}


return [

"0%",
"0%"

];


}







function xgLesen(text){


let wert=text.match(

/xG\s*\n\s*(\d+\.\d+)\s*\n\s*(\d+\.\d+)/i

);



if(wert){

return [

parseFloat(wert[1]),

parseFloat(wert[2])

];

}



return [

0,

0

];


}









function datenUebernehmen(){



let text=document
.getElementById("liveDaten")
.value;





/* =================
xG
================= */


let xg=xgLesen(text);



xgHeim.textContent=

xg[0].toFixed(2);



xgGast.textContent=

xg[1].toFixed(2);



let gesamt=

xg[0]+xg[1];



if(gesamt>0){



xgBalkenHeim.style.width=

(xg[0]/gesamt*100)+"%";



xgBalkenGast.style.width=

(xg[1]/gesamt*100)+"%";


}







/* =================
BALLBESITZ
================= */


let ball=

prozentLesen(
text,
"Ballbesitz"
);



ballTextHeim.textContent=

ball[0];



ballTextGast.textContent=

ball[1];



ballHeim.style.width=

ball[0];



ballGast.style.width=

ball[1];









/* =================
STATISTIKEN
================= */



let schuesse=

paarLesen(
text,
"Schüsse insgesamt"
);



schuesseHeim.textContent=

schuesse[0];


schuesseGast.textContent=

schuesse[1];







let tore=

paarLesen(
text,
"Schüsse aufs Tor"
);



torHeim.textContent=

tore[0];


torGast.textContent=

tore[1];







let chancen=

paarLesen(
text,
"Großchance"
);



chanceHeim.textContent=

chancen[0];


chanceGast.textContent=

chancen[1];







let ecken=

paarLesen(
text,
"Eckbälle"
);



eckenHeim.textContent=

ecken[0];


eckenGast.textContent=

ecken[1];







let paesse=

text.match(

/Pässe\s*\n\s*(\d+)\/\d+\s*\n\s*(\d+)\/\d+/i

);



if(paesse){


paesseHeim.textContent=

paesse[1];


paesseGast.textContent=

paesse[2];


}







let pass=

prozentLesen(
text,
"Passgenauigkeit"
);



passHeim.textContent=

pass[0];


passGast.textContent=

pass[1];








let karten=

paarLesen(
text,
"Gelbe Karten"
);



kartenHeim.textContent=

karten[0];


kartenGast.textContent=

karten[1];



}



</script>





<!-- =========================
TEIL 5
SPEICHERN / LADEN / ABSCHLUSS
========================= -->


<style>


.speicher-bereich{


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



.speicher-bereich h2{


color:#f5c542;

margin-bottom:15px;


}



.status-box{


margin-top:20px;

padding:15px;


background:#050505;


border-radius:15px;


border:1px solid #555;


color:#aaa;


font-size:14px;


}



</style>







<div class="speicher-bereich">


<h2>
SPIELTAG SPEICHERN
</h2>




<button class="button"
onclick="spieltagSpeichern()">

💾 SPIELTAG SPEICHERN

</button>





<button class="button"
onclick="spieltagLadenSpeicher()">

📂 SPIELTAG LADEN

</button>





<div class="status-box" id="statusBox">

Bereit

</div>



</div>









<script>


/* =========================
SPIELTAG SPEICHERN
========================= */


function spieltagSpeichern(){



let daten={


spiele:spiele,


datum:new Date()
.toLocaleString("de-DE"),



};



localStorage.setItem(

"Wettpropheten_Dashboard",

JSON.stringify(daten)

);



document.getElementById("statusBox")
.textContent=

"Gespeichert: "
+
daten.datum;



}









/* =========================
SPIELTAG LADEN
========================= */


function spieltagLadenSpeicher(){



let daten=

localStorage.getItem(

"Wettpropheten_Dashboard"

);



if(!daten){



document.getElementById("statusBox")
.textContent=

"Keine Daten gespeichert";


return;


}




let gespeichert=

JSON.parse(daten);



spiele=

gespeichert.spiele || [];





let liste=

document.getElementById(
"spielListe"
);



liste.innerHTML="";






spiele.forEach(function(spiel){


spielkarteErstellen(spiel);


});





document.getElementById("statusBox")
.textContent=

"Geladen: "
+
gespeichert.datum;



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
FARBEN AKTUALISIEREN
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




document.documentElement.style
.setProperty(

"--heim-farbe",

heimFarbe

);





document.documentElement.style
.setProperty(

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



};




</script>






</div>

</body>

</html>
