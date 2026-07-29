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
    font-family:Arial, Helvetica, sans-serif;
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
   SIDEBAR LINKS
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
    margin-bottom:20px;
    font-size:28px;

}



.spieltag-box{

    height:calc(100vh - 90px);

    background:#111;

    border-radius:20px;

    border:1px solid #444;

    padding:15px;

    overflow-y:auto;

}



/* =========================
   HAUPTBEREICH RECHTS
========================= */

.main{

    flex:1;

    height:100vh;

    padding:20px;

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

    width:100%;

    height:190px;

    display:grid;

    grid-template-columns:1fr 220px 1fr;

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

    font-size:85px;

    font-weight:bold;

    color:#f5c542;

}



/* =========================
   PANELS
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



/* =========================
   BALKEN BASIS
========================= */


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



/* =========================
   INPUT
========================= */


textarea{

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


.button:hover{

    filter:brightness(1.2);

}


</style>

</head>


<body>


<div class="app">


<!-- LINKSBEREICH -->

<div class="sidebar">


<h1>SPIELTAG</h1>


<div class="spieltag-box">


<textarea id="spieltagInput"
placeholder="08.08.2026

Bayern München
Borussia Dortmund

-">
</textarea>


<button class="button">
SPIELTAG LADEN
</button>


<div id="spielListe"></div>


</div>


</div>





<!-- RECHTS -->

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


</body>

</html>
<script>

let spiele = [];


/* =========================
   SPIELTAG LADEN
========================= */

document.querySelector(".sidebar .button").onclick = spieltagLaden;



function spieltagLaden(){


const text =
document.getElementById("spieltagInput").value;



const zeilen =
text
.split("\n")
.map(z=>z.trim())
.filter(z=>z!=="");



spiele=[];



const liste =
document.getElementById("spielListe");

liste.innerHTML="";



for(let i=0;i<zeilen.length;i++){



    if(/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])){


        let datum=zeilen[i];

        let heim=zeilen[i+1];

        let gast=zeilen[i+2];


        if(heim && gast){


            let spiel={

                datum,
                heim,
                gast

            };


            spiele.push(spiel);


            spielkarteErstellen(spiel);


        }


    }


}


}




/* =========================
   SPIELKARTE LINKS
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



document.getElementById("spielListe")
.appendChild(karte);



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



console.log(
"geladen:",
spiel.heim,
"vs",
spiel.gast
);



}



</script>


<style>


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

margin:5px;


}


</style>
<!-- =========================
     TEIL 3 - MANNSCHAFTEN + FARBEN + BALLBESITZ
========================= -->


<style>

/* =========================
   FARB VARIABLEN
========================= */


:root{

    --heim-farbe:#0099ff;

    --gast-farbe:#ff3344;

}



/* TEAM NAMEN */

.team.heim{

    color:var(--heim-farbe)!important;

}


.team.gast{

    color:var(--gast-farbe)!important;

}



/* ALLE BALKEN */

.heim-balken{

    background:var(--heim-farbe)!important;

}


.gast-balken{

    background:var(--gast-farbe)!important;

}



/* =========================
   BALLBESITZ
========================= */


.ballbesitz-panel{

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



.ballbesitz-werte{

    display:flex;

    justify-content:space-between;

    font-size:22px;

    font-weight:bold;

    margin-bottom:12px;

}



.ballbesitz-balken{

    width:100%;

    height:45px;

    background:#000;

    border-radius:25px;

    overflow:hidden;

    display:flex;

}



#ballHeim{

    width:50%;

}



#ballGast{

    width:50%;

}



</style>





<!-- =========================
     BALLBESITZ ANZEIGE
========================= -->


<div class="ballbesitz-panel">


<h2 style="color:#f5c542;margin-bottom:15px;">
Ballbesitz
</h2>


<div class="ballbesitz-werte">


<span class="heim-text">
50%
</span>


<span class="gast-text">
50%
</span>


</div>



<div class="ballbesitz-balken">


<div 
id="ballHeim"
class="heim-balken">
</div>



<div 
id="ballGast"
class="gast-balken">
</div>



</div>


</div>






<script>


/* =========================
   VEREINS FARB DATENBANK
   EXAKTE SCHREIBWEISE
========================= */


const vereinsFarben = {


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



let heimFarbe =

vereinsFarben[heim]

||

"#0099ff";




let gastFarbe =

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


const alteSpielLaden = spielLaden;



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



document.getElementById("ballHeim")
.style.width="50%";


document.getElementById("ballGast")
.style.width="50%";



};





</script><!-- =========================
     TEIL 4 - TOP STATISTIKEN
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

    justify-content:space-around;

    font-size:30px;

    font-weight:bold;


}



.heim-wert{


    color:var(--heim-farbe);


}



.gast-wert{


    color:var(--gast-farbe);


}



.stat-info{


    color:#777;

    font-size:14px;

    margin-top:8px;


}




</style>





<div class="top-statistik">





<!-- SCHÜSSE -->


<div class="stat-box">


<h3>
SCHÜSSE
</h3>


<div class="stat-wert">


<span class="heim-wert" id="schuesseHeim">
0
</span>


<span>:</span>


<span class="gast-wert" id="schuesseGast">
0
</span>


</div>


</div>







<!-- SCHÜSSE AUFS TOR -->


<div class="stat-box">


<h3>
SCHÜSSE AUFS TOR
</h3>


<div class="stat-wert">


<span class="heim-wert" id="torHeim">
0
</span>


<span>:</span>


<span class="gast-wert" id="torGast">
0
</span>


</div>


</div>








<!-- GROßCHANCEN -->


<div class="stat-box">


<h3>
GROSSCHANCEN
</h3>


<div class="stat-wert">


<span class="heim-wert" id="chanceHeim">
0
</span>


<span>:</span>


<span class="gast-wert" id="chanceGast">
0
</span>


</div>


</div>








<!-- ECKBÄLLE -->


<div class="stat-box">


<h3>
ECKBÄLLE
</h3>


<div class="stat-wert">


<span class="heim-wert" id="eckenHeim">
0
</span>


<span>:</span>


<span class="gast-wert" id="eckenGast">
0
</span>


</div>


</div>








<!-- PÄSSE -->


<div class="stat-box">


<h3>
PÄSSE
</h3>


<div class="stat-wert" style="font-size:22px">


<span class="heim-wert" id="paesseHeim">
0
</span>


<span>:</span>


<span class="gast-wert" id="paesseGast">
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


<div class="stat-wert">


<span class="heim-wert" id="passHeim">
0%
</span>


<span>:</span>


<span class="gast-wert" id="passGast">
0%
</span>


</div>


</div>








<!-- GELBE KARTEN -->


<div class="stat-box">


<h3>
GELBE KARTEN
</h3>


<div class="stat-wert">


<span class="heim-wert" id="kartenHeim">
0
</span>


<span>:</span>


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

font-size:16px;

resize:none;


}



.speicher-bereich{


margin-top:25px;


background:

linear-gradient(
145deg,
#252525,
#101010
);


border-radius:25px;


padding:25px;


border:1px solid #333;


}



</style>






<div class="live-bereich">


<h2>
LIVE DATEN
</h2>



<textarea id="liveDaten"

placeholder="

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

Ballbesitz
44%
56%

xG
0.81
0.74

"></textarea>



<button class="button"
onclick="datenUebernehmen()">

DATEN ÜBERNEHMEN

</button>



</div>







<script>


/* =========================
   WERTE AUSLESEN
========================= */


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


return ["0","0"];


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









function datenUebernehmen(){



let text=document
.getElementById("liveDaten")
.value;






/* SCHÜSSE */


let schuesse=


paarLesen(
text,
"Schüsse insgesamt"
);



schuesseHeim.textContent=schuesse[0];

schuesseGast.textContent=schuesse[1];







/* SCHÜSSE AUFS TOR */


let tore=


paarLesen(
text,
"Schüsse aufs Tor"
);



torHeim.textContent=tore[0];

torGast.textContent=tore[1];







/* GROßCHANCEN */


let chancen=


paarLesen(
text,
"Großchance"
);



chanceHeim.textContent=chancen[0];

chanceGast.textContent=chancen[1];







/* ECKEN */


let ecken=


paarLesen(
text,
"Eckbälle"
);



eckenHeim.textContent=ecken[0];

eckenGast.textContent=ecken[1];







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

prozentLesen(
text,
"Passgenauigkeit"
);



passHeim.textContent=pass[0];

passGast.textContent=pass[1];









/* KARTEN */


let karten=

paarLesen(
text,
"Gelbe Karten"
);



kartenHeim.textContent=karten[0];

kartenGast.textContent=karten[1];







/* BALLBESITZ */


let ball=

prozentLesen(
text,
"Ballbesitz"
);



document.querySelector(".heim-text")
.textContent=ball[0];


document.querySelector(".gast-text")
.textContent=ball[1];


ballHeim.style.width=ball[0];

ballGast.style.width=ball[1];





}



</script>






<!-- =========================
     SPEICHERN / LADEN
========================= -->


<div class="speicher-bereich">


<h2 style="color:#f5c542">

SPIELTAG SPEICHERN

</h2>



<button class="button"
onclick="spieltagSpeichern()">

💾 SPEICHERN

</button>



<button class="button"
onclick="spieltagLadenSpeicher()">

📂 LADEN

</button>


</div>





<script>



function spieltagSpeichern(){


localStorage.setItem(

"Wettpropheten_Spiele",

JSON.stringify(spiele)

);


alert(
"Spieltag gespeichert"
);


}







function spieltagLadenSpeicher(){



let daten=

localStorage.getItem(
"Wettpropheten_Spiele"
);



if(!daten){

alert(
"Keine Daten vorhanden"
);

return;

}



spiele=

JSON.parse(daten);



document.getElementById("spielListe")
.innerHTML="";



spiele.forEach(

spielkarteErstellen

);



alert(
"Spieltag geladen"
);



}



</script>
</div>
</body>
</html>
