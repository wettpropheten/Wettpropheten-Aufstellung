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

*{

    box-sizing:border-box;
    margin:0;
    padding:0;
    font-family:Arial,Helvetica,sans-serif;

}



body{

    width:100%;
    height:100vh;

    background:#050505;

    color:white;

    overflow:hidden;

}




/* =====================
HAUPT LAYOUT
===================== */


.app{

    display:flex;

    width:100vw;

    height:100vh;

}





/* =====================
LINKER SPIELTAG
===================== */


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

    margin-bottom:20px;

    font-size:28px;

}




textarea{

    width:100%;

    height:220px;


    background:#050505;

    color:white;


    border:1px solid #555;

    border-radius:15px;


    padding:12px;

    resize:none;

    font-size:15px;

}





button{


    width:100%;

    margin-top:12px;


    padding:13px;


    background:

    linear-gradient(
        #555,
        #111
    );


    border:1px solid #777;

    border-radius:15px;


    color:white;

    font-weight:bold;

    cursor:pointer;


}



button:hover{


    border-color:#f5c542;


}





/* =====================
SPIELKARTEN
===================== */


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



.datum{


    color:#aaa;

    font-size:13px;


}


.teamname{


    margin:8px;

    font-weight:bold;

    font-size:17px;


}





/* =====================
RECHTER BEREICH
===================== */


.main{


    flex:1;


    height:100vh;


    overflow-y:auto;


    padding:0;


}





/* =====================
SPIELKOPF
===================== */


.spielkopf{


    margin-top:20px;

    margin-left:0;

    margin-right:20px;


    height:190px;


    display:grid;


    grid-template-columns:

    1fr 200px 1fr;


    align-items:center;


    background:#111;


    border-radius:30px;


    border:1px solid #333;


}





.team{


    text-align:center;


    font-size:38px;


    font-weight:bold;


}




.heim{


    color:#0099ff;


}




.gast{


    color:#ff3344;


}




.score{


    text-align:center;


    font-size:75px;


    font-weight:bold;


    color:#f5c542;


}





/* =====================
PANELS
===================== */


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


    margin-bottom:20px;


}




.panel h3{


    margin-top:15px;

    margin-bottom:10px;


    color:#aaa;


}





/* =====================
STATISTIK
===================== */


.stats{


    display:grid;


    grid-template-columns:

    repeat(4,1fr);


    gap:15px;


}



.stats div{


    background:#050505;


    border:1px solid #555;


    border-radius:18px;


    padding:15px;


    text-align:center;


}



.stats span{


    display:block;


    margin-top:10px;


    font-size:30px;


    color:#f5c542;


}





/* =====================
BALLBESITZ
===================== */


.bar{


    width:100%;


    height:28px;


    background:#333;


    border-radius:20px;


    overflow:hidden;


    border:1px solid #555;


}



#ballBalken{


    height:100%;


    width:50%;


    background:#0099ff;


    transition:.3s;


}





.ballwerte{


    display:flex;


    justify-content:space-between;


    margin-top:8px;


    font-size:18px;


}





/* =====================
INPUTS
===================== */


label{


    display:block;


    margin-top:12px;


    color:#aaa;


}



input{


    float:right;


    width:120px;


    padding:7px;


    background:#050505;


    color:white;


    border:1px solid #555;


    border-radius:8px;


}





#status{


    margin-top:15px;


    color:#aaa;


    text-align:center;


}





/* =====================
HANDY
===================== */


@media(max-width:900px){


.app{

    flex-direction:column;

}



.sidebar{

    width:100%;

    height:auto;

}



.stats{

    grid-template-columns:

    repeat(2,1fr);

}


}

let spiele = [];



let dashboard = {


    statistik:{


        xgHeim:1.00,

        xgGast:1.00,


        ballHeim:50,


        passHeim:0,


        passGast:0,


        quoteHeim:0,


        quoteGast:0


    },


    aktuell:{


        heim:"HEIM",

        gast:"GAST"


    }


};





/* =========================
SPIELTAG LADEN
========================= */


function spieltagLaden(){


    let text = document
    .getElementById("spieltagInput")
    .value;



    let zeilen = text
    .split(/\n/)
    .map(x => x.trim())
    .filter(x => x !== "");



    spiele = [];



    for(let i=0;i<zeilen.length;i++){



        if(
        /^\d{2}\.\d{2}\.\d{4}$/
        .test(zeilen[i])
        ){


            let datum = zeilen[i];


            let heim = zeilen[i+1];


            let gast = zeilen[i+2];



            if(heim && gast){


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


    let liste = document
    .getElementById("spielListe");



    liste.innerHTML="";



    spiele.forEach(function(spiel){



        let karte =
        document.createElement("div");



        karte.className="spielkarte";



        karte.innerHTML = `

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



        karte.onclick=function(){


            spielLaden(spiel);


        };



        liste.appendChild(karte);



    });


}







/* =========================
SPIEL AUSWÄHLEN
========================= */


function spielLaden(spiel){



    dashboard.aktuell.heim =
    spiel.heim;



    dashboard.aktuell.gast =
    spiel.gast;



    document
    .getElementById("heimName")
    .textContent =
    spiel.heim;



    document
    .getElementById("gastName")
    .textContent =
    spiel.gast;



}







/* =========================
STATISTIK UPDATE
========================= */


function updateStatistik(){



    dashboard.statistik.xgHeim =

    Number(
    document
    .getElementById("inputXgHeim")
    .value
    );




    dashboard.statistik.xgGast =

    Number(
    document
    .getElementById("inputXgGast")
    .value
    );






    dashboard.statistik.ballHeim =

    Number(
    document
    .getElementById("inputBall")
    .value
    );



    if(
    dashboard.statistik.ballHeim < 0
    ){

        dashboard.statistik.ballHeim=0;

    }




    if(
    dashboard.statistik.ballHeim > 100
    ){

        dashboard.statistik.ballHeim=100;

    }






    dashboard.statistik.passHeim =

    Number(
    document
    .getElementById("inputPassHeim")
    .value
    );





    dashboard.statistik.passGast =

    Number(
    document
    .getElementById("inputPassGast")
    .value
    );





    passQuoteBerechnen();



    statistikAnzeigen();



}







/* =========================
PASSQUOTE
========================= */


function passQuoteBerechnen(){



    let s =
    dashboard.statistik;



    if(s.passHeim > 0){


        s.quoteHeim =

        Math.round(
        (s.passHeim / 600) * 100
        );


    }
    else{


        s.quoteHeim=0;


    }






    if(s.passGast > 0){


        s.quoteGast =

        Math.round(
        (s.passGast / 600) * 100
        );


    }
    else{


        s.quoteGast=0;


    }




}







/* =========================
STATISTIK ANZEIGEN
========================= */


function statistikAnzeigen(){



let s =
dashboard.statistik;





document
.getElementById("xgHeim")
.textContent =
s.xgHeim.toFixed(2);




document
.getElementById("xgGast")
.textContent =
s.xgGast.toFixed(2);






document
.getElementById("passHeim")
.textContent =
s.passHeim;




document
.getElementById("passGast")
.textContent =
s.passGast;






document
.getElementById("ballBalken")
.style.width =
s.ballHeim+"%";





document
.getElementById("ballHeim")
.textContent =
s.ballHeim+"%";





document
.getElementById("ballGast")
.textContent =
(100-s.ballHeim)+"%";






document
.getElementById("passQuote")
.textContent =

"Heim "
+
s.quoteHeim
+
"% | Gast "
+
s.quoteGast
+
"%";



}







/* =========================
SPEICHERN
========================= */


function speichern(){



let speicher = {


spiele:spiele,


dashboard:dashboard



};




localStorage.setItem(

"Wettpropheten",

JSON.stringify(
speicher
)

);




document
.getElementById("status")
.textContent=

"Gespeichert";


}







/* =========================
LADEN
========================= */


function laden(){



let daten =

localStorage.getItem(
"Wettpropheten"
);



if(!daten){


document
.getElementById("status")
.textContent=

"Keine Daten gefunden";


return;


}





let speicher =

JSON.parse(daten);





spiele =
speicher.spiele || [];





dashboard =
speicher.dashboard || dashboard;





spieleAnzeigen();





document
.getElementById("heimName")
.textContent =

dashboard.aktuell.heim;




document
.getElementById("gastName")
.textContent =

dashboard.aktuell.gast;






statistikAnzeigen();





document
.getElementById("status")
.textContent=

"Geladen";


}







/* =========================
START
========================= */


window.onload=function(){


statistikAnzeigen();


};

{
  "spieltag": "08.08.2026",
  
  "spiele": [

    {
      "datum": "08.08.2026",
      "heim": "Bayern München",
      "gast": "Borussia Dortmund",

      "statistik": {

        "xgHeim": 1.85,
        "xgGast": 1.20,

        "ballbesitzHeim": 58,

        "paesseHeim": 520,
        "paesseGast": 410,

        "passquoteHeim": 87,
        "passquoteGast": 82

      }
    },


    {
      "datum": "09.08.2026",
      "heim": "Union Berlin",
      "gast": "Eintracht Frankfurt",

      "statistik": {

        "xgHeim": 1.10,
        "xgGast": 1.45,

        "ballbesitzHeim": 44,

        "paesseHeim": 350,
        "paesseGast": 480,

        "passquoteHeim": 76,
        "passquoteGast": 84

      }
    }

  ]
}
// ===============================
// WETTPROPHETEN DASHBOARD
// APP STARTSYSTEM
// ===============================


async function datenLaden(){


    try{


        const antwort =
        await fetch("data.json");


        const daten =
        await antwort.json();



        console.log(
            "Daten geladen:",
            daten
        );



    }
    catch(error){


        console.error(
            "Fehler beim Laden:",
            error
        );


    }


}





function dashboardStart(){


    statistikAnzeigen();


    datenLaden();


}





window.addEventListener(

"load",

dashboardStart

);
</body>

</html>
