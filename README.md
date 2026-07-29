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
    font-family:Arial, Helvetica, sans-serif;
}



body{

    width:100vw;
    height:100vh;
    background:#050505;
    color:white;
    overflow:hidden;

}




/* =========================
   GESAMT LAYOUT
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

    grid-template-columns:1fr 220px 1fr;

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
   xG PANEL
========================= */


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





.balken{

    width:100%;

    height:45px;

    display:flex;

    background:#000;

    border-radius:25px;

    overflow:hidden;

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



<!-- LINKS -->


<div class="sidebar">


<h1>
SPIELTAG
</h1>


<div class="spieltag-box">


<textarea id="spieltagInput"

placeholder="

08.08.2026

Bayern München

Borussia Dortmund

-
">

</textarea>



<button onclick="spieltagLaden()">

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



<script>


let spiele=[];


function spieltagLaden(){

console.log("Spieltag laden");

}


</script>
<script>


let spiele=[];



/* =========================
   SPIELTAG LADEN
========================= */


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

"Geladen:",
spiel.heim,
"vs",
spiel.gast

);



}



</script>



<style>


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
<style>

/* =========================
   FARB SYSTEM
========================= */


:root{

    --heim-farbe:#0099ff;
    --gast-farbe:#ff3344;

}



/* Mannschaftsfarben */

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





/* =========================
   BALLBESITZ
========================= */


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



.ballbesitz-panel h2{

    color:#f5c542;

    margin-bottom:15px;

}



.ballwerte{


    display:flex;

    justify-content:space-between;

    font-size:28px;

    font-weight:bold;

    margin-bottom:12px;


}



.ballbalken{


    height:45px;

    width:100%;

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
 BALLBESITZ BLOCK
========================= -->


<div class="ballbesitz-panel">


<h2>
Ballbesitz
</h2>



<div class="ballwerte">


<span class="heim-wert" id="ballTextHeim">
50%
</span>



<span class="gast-wert" id="ballTextGast">
50%
</span>


</div>



<div class="ballbalken">


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
   FARBEN ANWENDEN
========================= */


function farbenSetzen(heim,gast){



let heimFarbe=

vereinsFarben[heim] || "#0099ff";



let gastFarbe=

vereinsFarben[gast] || "#ff3344";




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



};




</script>

<!-- =========================
     TEIL 5 - LIVE DATEN SYSTEM
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



.xg-werte{

    display:flex;

    justify-content:space-between;

    font-size:28px;

    font-weight:bold;

    margin-bottom:10px;

}



.xg-panel{

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



.xg-panel h2{

    color:#f5c542;

}



</style>





<!-- =========================
     xG ANZEIGE
========================= -->


<div class="xg-panel">


<h2>
Expected Goals (xG)
</h2>



<div class="xg-werte">


<span class="heim-wert" id="xgHeim">
0.00
</span>



<span class="gast-wert" id="xgGast">
0.00
</span>


</div>




<div class="balken">


<div 
id="xgBalkenHeim"
class="heim-balken">
</div>



<div 
id="xgBalkenGast"
class="gast-balken">
</div>


</div>


</div>








<!-- =========================
     LIVE EINGABE
========================= -->


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




<button class="button" onclick="datenUebernehmen()">

DATEN ÜBERNEHMEN

</button>



</div>









<script>


/* =========================
   PROZENT AUSLESEN
========================= */


function prozentLesen(text,titel){


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


return ["50","50"];


}






/* =========================
   ZAHLEN AUSLESEN
========================= */


function zahlLesen(text,titel){


let regex=new RegExp(

titel+
"\\s*\\n\\s*([0-9.]+)\\s*\\n\\s*([0-9.]+)",
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









function datenUebernehmen(){



let text=document
.getElementById("liveDaten")
.value;





/* =========================
   xG
========================= */


let xg=

zahlLesen(
text,
"xG"
);



xgHeim.textContent=xg[0];

xgGast.textContent=xg[1];





let gesamt=

parseFloat(xg[0])+
parseFloat(xg[1]);



if(gesamt>0){


xgBalkenHeim.style.width=

(
parseFloat(xg[0]) /
gesamt *
100
)+"%";



xgBalkenGast.style.width=

(
parseFloat(xg[1]) /
gesamt *
100
)+"%";


}








/* =========================
   BALLBESITZ
========================= */


let ball=

prozentLesen(
text,
"Ballbesitz"
);



ballTextHeim.textContent=
ball[0]+"%";



ballTextGast.textContent=
ball[1]+"%";



ballHeim.style.width=
ball[0]+"%";



ballGast.style.width=
ball[1]+"%";





console.log(
"Live Daten übernommen"
);



}



</script>

</body>

</html>
