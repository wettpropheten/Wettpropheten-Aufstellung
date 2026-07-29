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

html,
body{
    width:100%;
    height:100%;
    background:#050505;
    color:#fff;
    overflow:hidden;
}

/* =========================
   APP LAYOUT
========================= */

.app{
    width:100vw;
    height:100vh;
    display:flex;
}

/* =========================
   SIDEBAR
========================= */

.sidebar{
    width:280px;
    min-width:280px;
    height:100vh;
    background:linear-gradient(180deg,#252525,#080808);
    border-right:2px solid #444;
    padding:15px;
}

.sidebar h1{
    text-align:center;
    color:#f5c542;
    font-size:28px;
    margin-bottom:20px;
}

#spieltagBereich{
    height:calc(100vh - 90px);
    background:#111;
    border:1px solid #444;
    border-radius:20px;
    padding:15px;
    overflow-y:auto;
}

/* =========================
   HAUPTBEREICH
========================= */

.main{
    flex:1;
    height:100vh;
    padding:20px;
    background:linear-gradient(145deg,#191919,#050505);
    overflow-y:auto;
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
    border:1px solid #333;
    border-radius:30px;
}

.team{
    text-align:center;
    font-size:42px;
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
    font-size:90px;
    font-weight:bold;
    color:#f5c542;
}

/* =========================
   STANDARD PANEL
========================= */

.panel{
    margin-top:25px;
    background:linear-gradient(145deg,#252525,#101010);
    border-radius:25px;
    padding:30px;
    border:1px solid #333;
}

.panel h2{
    color:#f5c542;
    margin-bottom:20px;
}

/* =========================
   xG-BALKEN
========================= */

.balken{
    width:100%;
    height:40px;
    background:#000;
    border-radius:20px;
    overflow:hidden;
    display:flex;
}

.heim-balken{
    width:60%;
    background:#0099ff;
}

.gast-balken{
    width:40%;
    background:#ff3344;
}

</style>

</head>

<body>

<div class="app">

    <!-- SIDEBAR -->
    <div class="sidebar">

        <h1>SPIELTAG</h1>

        <div id="spieltagBereich">

            <textarea id="spieltagInput" placeholder="08.08.2026

FC Bayern München
Borussia Dortmund

-"></textarea>

            <button class="button" onclick="spieltagLaden()">
                SPIELTAG LADEN
            </button>

            <div id="spielListe"></div>

        </div>

    </div>

    <!-- HAUPTBEREICH -->
    <div class="main">

        <div class="spielkopf">

            <div class="team heim">HEIM</div>

            <div class="ergebnis">0 : 0</div>

            <div class="team gast">GAST</div>

        </div>

        <div class="panel">

            <h2>Expected Goals (xG)</h2>

            <div class="balken">
                <div class="heim-balken"></div>
                <div class="gast-balken"></div>
            </div>

        </div>

        <!-- HIER BEGINNT TEIL 2 -->
<!-- =========================
     TEIL 2 - SPIELTAG SYSTEM
========================= -->

<style>

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
    background:linear-gradient(#555,#111);
    color:white;
    font-weight:bold;
    cursor:pointer;
}

.button:hover{
    filter:brightness(1.2);
}

.spielkarte{
    margin-top:15px;
    padding:15px;
    background:linear-gradient(145deg,#333,#111);
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

let spiele = [];

function spieltagLaden(){

    const text = document.getElementById("spieltagInput").value;

    const zeilen = text
        .split("\n")
        .map(z => z.trim())
        .filter(z => z !== "");

    spiele = [];

    const liste = document.getElementById("spielListe");
    liste.innerHTML = "";

    for(let i = 0; i < zeilen.length; ){

        if(!/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])){
            i++;
            continue;
        }

        const datum = zeilen[i];

        if(i + 2 >= zeilen.length) break;

        const heim = zeilen[i + 1];
        const gast = zeilen[i + 2];

        spiele.push({
            datum,
            heim,
            gast
        });

        spielkarteErstellen(spiele[spiele.length - 1]);

        i += 3;

        while(i < zeilen.length && zeilen[i] === "-"){
            i++;
        }
    }
}

function spielkarteErstellen(spiel){

    const karte = document.createElement("div");

    karte.className = "spielkarte";

    karte.innerHTML = `
        <div class="spielzeit">${spiel.datum}</div>
        <div class="verein">${spiel.heim}</div>
        <div>VS</div>
        <div class="verein">${spiel.gast}</div>
    `;

    karte.onclick = function(){
        spielLaden(spiele.indexOf(spiel));
    };

    document.getElementById("spielListe").appendChild(karte);
}

</script>

<!-- =========================
     TEIL 3 - MANNSCHAFTEN + FARBEN SYSTEM
========================= -->

<style>

:root{

    --heim-farbe:#0099ff;
    --gast-farbe:#ff3344;

}


/* Mannschaft Namen */

.team.heim{

    color:var(--heim-farbe)!important;

}


.team.gast{

    color:var(--gast-farbe)!important;

}


/* xG Balken */

.heim-balken{

    background:var(--heim-farbe)!important;

}


.gast-balken{

    background:var(--gast-farbe)!important;

}


/* kleine Anzeige */

.team-info{

    margin-top:15px;
    text-align:center;
    color:#aaa;
    font-size:14px;

}


</style>



<script>


/* =========================
   VEREINS FARB DATENBANK
========================= */


const vereinsFarben = {

"FC Augsburg":"#ba3733",
"1. FC Union Berlin":"#eb0016",
"Werder Bremen":"#1d9053",
"Borussia Dortmund":"#f6d800",
"SV Elversberg":"#111111",
"Eintracht Frankfurt":"#e1000f",
"SC Freiburg":"#e2001a",
"Hamburger SV":"#0066b3",
"TSG Hoffenheim":"#005ca9",
"1. FC Köln":"#ffffff",
"RB Leipzig":"#dd0000",
"Bayer 04 Leverkusen":"#e32221",
"1. FSV Mainz 05":"#c31432",
"Bor. Mönchengladbach":"#009b3a",
"Bayern München":"#dc052d",
"SC Paderborn 07":"#005ca9",
"FC Schalke 04":"#004d9f",
"VfB Stuttgart":"#e32219"

};



function farbenSetzen(heim,gast){


let heimFarbe =
vereinsFarben[heim] || "#0099ff";


let gastFarbe =
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




function spielLaden(index){


let spiel = spiele[index];


if(!spiel){
return;
}



document.querySelector(".team.heim").textContent =
spiel.heim;


document.querySelector(".team.gast").textContent =
spiel.gast;



document.querySelector(".ergebnis").textContent =
"0 : 0";



farbenSetzen(
spiel.heim,
spiel.gast
);



document.querySelector(".heim-balken").style.width="50%";

document.querySelector(".gast-balken").style.width="50%";



console.log(
"Geladen:",
spiel.heim,
"vs",
spiel.gast
);


}

</script>
<!-- =========================
   TEIL 4 - SPEICHERN / LADEN
========================= -->


<style>


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




.speicher-bereich h2{


    color:#f5c542;


    margin-bottom:15px;


}





</style>






<div class="speicher-bereich">


<h2>

SPIELTAG SPEICHERN

</h2>



<button class="button" onclick="speichern()">

💾 SPEICHERN

</button>



<button class="button" onclick="laden()">

📂 LADEN

</button>



</div>







<script>


let gespeicherteDaten={};





function speichern(){



    gespeicherteDaten={


        spiele:spiele,


        datum:new Date().toLocaleString("de-DE")


    };





    localStorage.setItem(

        "Wettpropheten_Daten",

        JSON.stringify(gespeicherteDaten)

    );





    alert(

        "Spieltag gespeichert"

    );



}







function laden(){



    let daten=

    localStorage.getItem(

        "Wettpropheten_Daten"

    );





    if(!daten){


        alert(

            "Keine Daten vorhanden"

        );


        return;


    }






    gespeicherteDaten=

    JSON.parse(daten);





    spiele=

    gespeicherteDaten.spiele || [];





    let liste=document

    .getElementById("spielListe");



    liste.innerHTML="";





    spiele.forEach(function(spiel){


        spielkarteErstellen(spiel);


    });





    alert(

        "Spieltag geladen"

    );



}
</script>


<!-- =========================
   TEIL 5 - LIVE DATEN SYSTEM NEU
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

padding:25px;

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

font-size:16px;

resize:none;

}




.statistik{

margin-top:25px;

display:grid;

grid-template-columns:repeat(4,1fr);

gap:20px;

}



.statistik-box{

background:
linear-gradient(
145deg,
#333,
#111
);

border-radius:20px;

padding:20px;

text-align:center;

border:1px solid #444;

}



.statistik-box h3{

color:#aaa;

font-size:14px;

margin-bottom:15px;

}



.statistik-box span{

font-size:30px;

font-weight:bold;

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

</style>





<div class="live-bereich">

<h2>
LIVE DATEN
</h2>


<textarea id="liveDaten"

placeholder="

Schüsse insgesamt
4
2

Schüsse aufs Tor
0
0

Großchance
0
3

Eckbälle
0
4

Pässe
37/43
32/40

Passquote
86%
80%

Gelbe Karten
1
2

"></textarea>



<button class="button"

onclick="liveAktualisieren()">

DATEN ÜBERNEHMEN

</button>


</div>






<div class="statistik">



<div class="statistik-box">
<h3>SCHÜSSE</h3>
<span id="schuesse">0 : 0</span>
</div>



<div class="statistik-box">
<h3>SCHÜSSE AUFS TOR</h3>
<span id="torSchuesse">0 : 0</span>
</div>



<div class="statistik-box">
<h3>GROSSCHANCEN</h3>
<span id="grosschance">0 : 0</span>
</div>



<div class="statistik-box">
<h3>ECKBÄLLE</h3>
<span id="ecken">0 : 0</span>
</div>



<div class="statistik-box">
<h3>PÄSSE</h3>
<span id="paesse">0 : 0</span>
</div>



<div class="statistik-box">
<h3>PASSQUOTE</h3>
<span id="passquote">0% : 0%</span>
</div>



<div class="statistik-box">
<h3>GELBE KARTEN</h3>
<span id="karten">0 : 0</span>
</div>



</div>








<script>

function wertPaar(text, titel){

let regex = new RegExp(

titel +
"\\s*\\n\\s*(\\d+)\\s*\\n\\s*(\\d+)",

"i"

);


let daten=text.match(regex);


if(daten){

return daten[1]+" : "+daten[2];

}


return "0 : 0";

}





function liveAktualisieren(){


let text=document
.getElementById("liveDaten")
.value;





// SCHÜSSE

document.getElementById("schuesse").innerHTML =

wertPaar(
text,
"Schüsse insgesamt"
);





// SCHÜSSE AUFS TOR

document.getElementById("torSchuesse").innerHTML =

wertPaar(
text,
"Schüsse aufs Tor"
);





// GROSSCHANCEN

document.getElementById("grosschance").innerHTML =

wertPaar(
text,
"Großchance"
);





// ECKBÄLLE

document.getElementById("ecken").innerHTML =

wertPaar(
text,
"Eckbälle"
);



// PÄSSE GETRENNT

let paesse=text.match(

/Pässe\s*\n\s*(\d+)\/\d+\s*\n\s*(\d+)\/\d+/i

);



if(paesse){

document.getElementById("paesse").innerHTML =

paesse[1]+" : "+paesse[2];

}








// PASSQUOTE GETRENNT

let quote=text.match(

/Passquote\s*\n\s*(\d+)%\s*\n\s*(\d+)%/i

);



if(quote){

document.getElementById("passquote").innerHTML =

quote[1]+"% : "+quote[2]+"%";

}













// GELBE KARTEN

document.getElementById("karten").innerHTML =

wertPaar(
text,
"Gelbe Karten"
);


}

</script>


</body>

</html>
