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


html,
body{

    width:100%;
    height:100%;

    background:#050505;

    color:white;

    overflow:hidden;

}



/* =========================
HAUPTSTRUKTUR
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




#spieltagInput{

    width:100%;

    height:220px;

    padding:12px;

    resize:none;

    background:#050505;

    color:white;

    border:1px solid #555;

    border-radius:15px;

    font-size:15px;

}




button{

    width:100%;

    margin-top:12px;

    padding:13px;

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



button:hover{

    border-color:#f5c542;

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




.datum{

    color:#aaa;

    font-size:13px;

}




.teamname{

    margin:8px;

    font-size:17px;

    font-weight:bold;

}



/* =========================
RECHTER BEREICH
========================= */


.main{

    flex:1;

    height:100vh;

    overflow-y:auto;

    padding:0;

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

    font-size:80px;

    font-weight:bold;

    color:#f5c542;

}



/* =========================
PANELS
========================= */


.panel{

    margin-top:20px;

    margin-left:0;

    margin-right:20px;

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




/* =========================
STATISTIK
========================= */


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
<!-- =========================
BALLBESITZ
========================= -->


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





/* =========================
EINGABEN
========================= */


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

    text-align:center;

    color:#aaa;

}





/* =========================
MOBILE
========================= */


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




</style>

</head>


<body>


<div class="app">



<!-- =========================
LINKER BEREICH
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
Eintracht Frankfurt

"></textarea>




<button onclick="spieltagLaden()">

SPIELTAG LADEN

</button>




<div id="spielListe"></div>



</div>







<!-- =========================
RECHTER BEREICH
========================= -->


<div class="main">



<div class="spielkopf">



<div id="heimName" class="team heim">

HEIM

</div>




<div class="score">

0 : 0

</div>




<div id="gastName" class="team gast">

GAST

</div>



</div>








<div class="panel">


<h2>
Statistik
</h2>



<div class="stats">



<div>

<h3>
xG Heim
</h3>

<span id="xgHeim">
1.00
</span>

</div>




<div>

<h3>
xG Gast
</h3>

<span id="xgGast">
1.00
</span>

</div>




<div>

<h3>
Pässe Heim
</h3>

<span id="passHeim">
0
</span>

</div>




<div>

<h3>
Pässe Gast
</h3>

<span id="passGast">
0
</span>

</div>



</div>







<h3>
Ballbesitz
</h3>



<div class="bar">

<div id="ballBalken"></div>

</div>




<div class="ballwerte">


<span id="ballHeim">
50%
</span>


<span id="ballGast">
50%
</span>



</div>







<h3>
Passquote
</h3>


<div id="passQuote">

Heim 0% | Gast 0%

</div>



</div>








<div class="panel">


<h2>
Werte ändern
</h2>




<label>

xG Heim

<input id="inputXgHeim"

type="number"

step="0.01"

value="1">

</label>





<label>

xG Gast

<input id="inputXgGast"

type="number"

step="0.01"

value="1">

</label>





<label>

Ballbesitz Heim %

<input id="inputBall"

type="number"

value="50">

</label>





<label>

Pässe Heim

<input id="inputPassHeim"

type="number"

value="0">

</label>





<label>

Pässe Gast

<input id="inputPassGast"

type="number"

value="0">

</label>





<button onclick="updateStatistik()">

AKTUALISIEREN

</button>




</div>
<div class="panel">


<h2>
Speichern / Laden
</h2>



<button onclick="speichern()">

💾 SPEICHERN

</button>




<button onclick="laden()">

📂 LADEN

</button>




<p id="status">

Bereit

</p>



</div>







</div>


</div>









<script>


let spiele=[];



let dashboard={


    aktuell:{


        heim:"HEIM",

        gast:"GAST"


    },


    statistik:{


        xgHeim:1,

        xgGast:1,

        ballHeim:50,

        passHeim:0,

        passGast:0,

        quoteHeim:0,

        quoteGast:0


    }


};








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




for(
let i=0;
i<zeilen.length;
i++
){



if(
/^\d{2}\.\d{2}\.\d{4}$/.test(zeilen[i])
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




spiele.forEach(function(spiel){



let karte=document
.createElement("div");



karte.className="spielkarte";




karte.innerHTML=`


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
SPIEL LADEN
========================= */


function spielLaden(spiel){



dashboard.aktuell.heim=
spiel.heim;



dashboard.aktuell.gast=
spiel.gast;




document
.getElementById("heimName")
.textContent=
spiel.heim;




document
.getElementById("gastName")
.textContent=
spiel.gast;




if(spiel.statistik){



dashboard.statistik.xgHeim=
spiel.statistik.xgHeim;



dashboard.statistik.xgGast=
spiel.statistik.xgGast;



dashboard.statistik.ballHeim=
spiel.statistik.ballHeim;



dashboard.statistik.passHeim=
spiel.statistik.passHeim;



dashboard.statistik.passGast=
spiel.statistik.passGast;



passQuote();


}



statistikAnzeigen();



}








/* =========================
STATISTIK UPDATE
========================= */


function updateStatistik(){



let s=dashboard.statistik;




s.xgHeim=zahl(
"inputXgHeim",
1
);




s.xgGast=zahl(
"inputXgGast",
1
);





s.ballHeim=zahl(
"inputBall",
50
);




if(s.ballHeim<0)
s.ballHeim=0;



if(s.ballHeim>100)
s.ballHeim=100;





s.passHeim=zahl(
"inputPassHeim",
0
);




s.passGast=zahl(
"inputPassGast",
0
);





passQuote();



statistikAnzeigen();



}



 
/* =========================
ZAHLEN SICHER LESEN
========================= */


function zahl(id,standard){



let wert=Number(

document
.getElementById(id)
.value

);



if(isNaN(wert)){


return standard;


}



return wert;



}








/* =========================
PASSQUOTE BERECHNEN
========================= */


function passQuote(){



let s=dashboard.statistik;



s.quoteHeim=

s.passHeim>0

?

Math.min(
100,
Math.round(s.passHeim/6)
)

:

0;





s.quoteGast=

s.passGast>0

?

Math.min(
100,
Math.round(s.passGast/6)
)

:

0;



}








/* =========================
STATISTIK ANZEIGEN
========================= */


function statistikAnzeigen(){



let s=dashboard.statistik;




document
.getElementById("xgHeim")
.textContent=
s.xgHeim.toFixed(2);





document
.getElementById("xgGast")
.textContent=
s.xgGast.toFixed(2);





document
.getElementById("passHeim")
.textContent=
s.passHeim;





document
.getElementById("passGast")
.textContent=
s.passGast;





document
.getElementById("ballBalken")
.style.width=
s.ballHeim+"%";





document
.getElementById("ballHeim")
.textContent=
s.ballHeim+"%";





document
.getElementById("ballGast")
.textContent=
(100-s.ballHeim)+"%";





document
.getElementById("passQuote")
.textContent=

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



let daten={


spiele:spiele,


dashboard:dashboard



};





localStorage.setItem(

"WettprophetenDashboard",

JSON.stringify(daten)

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



let daten=

localStorage.getItem(

"WettprophetenDashboard"

);





if(!daten){



document
.getElementById("status")
.textContent=

"Keine Daten vorhanden";


return;


}





let gespeichert=

JSON.parse(daten);





spiele=

gespeichert.spiele || [];





dashboard=

gespeichert.dashboard || dashboard;





spieleAnzeigen();





document
.getElementById("heimName")
.textContent=
dashboard.aktuell.heim;





document
.getElementById("gastName")
.textContent=
dashboard.aktuell.gast;





statistikAnzeigen();





document
.getElementById("status")
.textContent=

"Geladen";



}








/* =========================
BEISPIEL DATEN
========================= */


const beispielDaten={



spiele:[



{

datum:"08.08.2026",

heim:"Bayern München",

gast:"Borussia Dortmund",


statistik:{


xgHeim:1.85,

xgGast:1.20,

ballHeim:58,

passHeim:520,

passGast:410


}



},





{


datum:"09.08.2026",


heim:"Union Berlin",


gast:"Eintracht Frankfurt",


statistik:{


xgHeim:1.10,

xgGast:1.45,

ballHeim:44,

passHeim:350,

passGast:480


}



}



]


};








/* =========================
BEISPIEL SPIELE LADEN
========================= */


function beispieleLaden(){



spiele=

JSON.parse(

JSON.stringify(
beispielDaten.spiele
)

);





spieleAnzeigen();





document
.getElementById("status")
.textContent=

"Beispieldaten geladen";



}




 
/* =========================
STARTSYSTEM
========================= */


window.addEventListener(
"load",
function(){



statistikAnzeigen();



if(spiele.length===0){


beispieleLaden();


}



}

);





</script>



</body>

</html>
