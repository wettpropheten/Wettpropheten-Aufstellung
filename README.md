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


html,body{

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

    position:absolute;

    left:0;
    top:0;

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





#spieltagBereich{


    height:calc(100vh - 90px);


    background:#111;


    border:1px solid #444;


    border-radius:20px;


    padding:15px;


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


    border-radius:30px;


    background:#111;


    border:1px solid #333;


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
   TEST BEREICH
========================= */


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


    border:1px solid #333;


}




.panel h2{


    color:#f5c542;


    margin-bottom:20px;


}





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



<!-- =========================
     LINKS
========================= -->


<div class="sidebar">


<h1>
SPIELTAG
</h1>


<div id="spieltagBereich">


Spieltag kommt hier rein


</div>


</div>






<!-- =========================
     HAUPT
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


    margin:6px;


}



</style>






<script>


let spiele=[];



function spieltagLaden(){


    let eingabe=document
    .getElementById("spieltagInput")
    .value;



    let zeilen=eingabe
    .split("\n")
    .map(x=>x.trim())
    .filter(x=>x);



    spiele=[];



    let liste=document
    .getElementById("spielListe");



    liste.innerHTML="";




    for(let i=0;i<zeilen.length;i++){



        if(zeilen[i].match(/\d{2}\.\d{2}/)){



            let datum=zeilen[i];


            let teams=[];



            for(let j=i+1;j<zeilen.length;j++){



                if(zeilen[j]=="-"){

                    break;

                }



                teams.push(zeilen[j]);



            }





            if(teams.length>=2){



                let spiel={

                    datum:datum,

                    heim:teams[0],

                    gast:teams[1]

                };



                spiele.push(spiel);



                spielkarteErstellen(spiel);



            }



        }



    }



}





function spielkarteErstellen(spiel){



    let box=document.createElement("div");



    box.className="spielkarte";



    box.innerHTML=`


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




    box.onclick=function(){



        document.querySelector(".heim").innerHTML=
        spiel.heim;



        document.querySelector(".gast").innerHTML=
        spiel.gast;



    };




    document
    .getElementById("spielListe")
    .appendChild(box);



}



</script>
<!-- =========================
   TEIL 3 - MANNSCHAFTEN + FARBEN
========================= -->


<style>


:root{

    --heim-farbe:#0099ff;

    --gast-farbe:#ff3344;

}





.heim{

    color:var(--heim-farbe)!important;

}



.gast{

    color:var(--gast-farbe)!important;

}




.heim-balken{

    background:var(--heim-farbe);

}



.gast-balken{

    background:var(--gast-farbe);

}




</style>





<script>


const vereinsFarben={



"FC Bayern München":"#dc052d",

"Borussia Dortmund":"#f6d800",

"Bayer Leverkusen":"#e32221",

"RB Leipzig":"#dd0000",

"Eintracht Frankfurt":"#e1000f",

"VfB Stuttgart":"#e32219",

"SC Freiburg":"#e2001a",

"1. FSV Mainz 05":"#c31432",

"Werder Bremen":"#1d9053",

"Borussia Mönchengladbach":"#009b3a",

"VfL Wolfsburg":"#65b32e",

"TSG Hoffenheim":"#005ca9",

"FC Augsburg":"#ba3733",

"1. FC Union Berlin":"#eb0016",

"FC St. Pauli":"#5a2d14",

"Holstein Kiel":"#d50000",

"VfL Bochum":"#005ca9",

"1. FC Heidenheim":"#e30613",



/* zusätzliche mögliche Teams */

"FC Schalke 04":"#004d9f",

"SC Paderborn":"#005ca9",

"SV Elversberg":"#111111"



};







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








/* Spiel öffnen erweitern */


function spielLaden(index){



let spiel=spiele[index];



if(!spiel)

return;





document.querySelector(".heim").innerHTML=

spiel.heim;



document.querySelector(".gast").innerHTML=

spiel.gast;





farbenSetzen(

spiel.heim,

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


    padding:25px;


    border:1px solid #333;


}




.live-bereich h2{


    color:#f5c542;


    margin-bottom:15px;


}




#liveDaten{


    width:100%;


    height:220px;


    background:#050505;


    color:white;


    border:1px solid #555;


    border-radius:15px;


    padding:15px;


    resize:none;


}






.statistik{


    margin-top:25px;


    display:grid;


    grid-template-columns:repeat(3,1fr);


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




</style>








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

1.24

0.80


Ballbesitz

58%

42%


Schüsse

10

12


Pässe

454

464


Gelbe Karten

1

2

"></textarea>




<button class="button"

onclick="liveAktualisieren()">

DATEN ÜBERNEHMEN

</button>



</div>








<!-- =========================
   STATISTIK
========================= -->


<div class="statistik">


<div class="statistik-box">

<h3>

SCHÜSSE

</h3>

<span id="anzeigeSchuesse">

0 : 0

</span>


</div>




<div class="statistik-box">

<h3>

PÄSSE

</h3>

<span id="anzeigePaesse">

0 : 0

</span>


</div>




<div class="statistik-box">

<h3>

GELBE KARTEN

</h3>

<span id="anzeigeKarten">

0 : 0

</span>


</div>


</div>







<script>


function liveAktualisieren(){



let text=document

.getElementById("liveDaten")

.value;





let zahlen=text.match(/\d+(?:\.\d+)?/g);



if(!zahlen || zahlen.length<2){

return;

}






/* xG */


let xgHeim=

Number(zahlen[0]);



let xgGast=

Number(zahlen[1]);



let sum=xgHeim+xgGast;





if(sum>0){


document.querySelector(".heim-balken").style.width=

(xgHeim/sum*100)+"%";



document.querySelector(".gast-balken").style.width=

(xgGast/sum*100)+"%";


}






/* Prozent */

let prozent=text.match(/\d+%/g);



if(prozent && prozent.length>=2){


/* Ballbesitz wird später erweitert */

}







/* Zahlen suchen */


let ganzeZahlen=text.match(/\b\d+\b/g);



if(ganzeZahlen){



let werte=ganzeZahlen.slice(2);



document.getElementById("anzeigeSchuesse").innerHTML=

(werte[0] || 0)+" : "+(werte[1] || 0);




document.getElementById("anzeigePaesse").innerHTML=

(werte[2] || 0)+" : "+(werte[3] || 0);




document.getElementById("anzeigeKarten").innerHTML=

(werte[4] || 0)+" : "+(werte[5] || 0);



}



}






</script>







</body>


</html>
