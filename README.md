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



html,
body{

    width:100%;
    height:100%;

    background:#050505;

    color:white;

    overflow:hidden;

}




/* =========================
   HAUPT CONTAINER
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

    width:260px;

    min-width:260px;

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





/* =========================
   HAUPTFENSTER
========================= */


.main{

    flex:1;

    height:100vh;


    padding:20px;


    background:

    linear-gradient(
        145deg,
        #181818,
        #050505
    );


    overflow-y:auto;

}







/* =========================
   SPIELKOPF
========================= */


.header{


    width:100%;


    height:180px;



    display:grid;


    grid-template-columns:

    1fr 200px 1fr;



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






.score{


    text-align:center;


    font-size:90px;


    font-weight:bold;


    color:#f5c542;



}







/* =========================
   VEREINSFARBEN
========================= */


:root{


    --home-color:#0099ff;


    --away-color:#ff3344;


}




.home-color{

    color:var(--home-color);

}



.away-color{

    color:var(--away-color);

}




</style>

</head>



<body>


<div class="app">



<!-- =========================
     SPIELTAG
========================= -->


<div class="sidebar">


<h1>

SPIELTAG

</h1>


<div id="spielListe">

</div>



</div>






<!-- =========================
     HAUPTBEREICH
========================= -->


<div class="main">


<div class="header">


<div class="team home-color">

HEIM

</div>



<div class="score">

0 : 0

</div>



<div class="team away-color">

GAST

</div>



</div>
<!-- =========================
   GRAFIK BEREICH
========================= -->


<style>


/* =========================
   PANELS
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






.panel-title{


    font-size:26px;


    font-weight:bold;


    color:#f5c542;


    margin-bottom:20px;



}






/* =========================
   WERTE
========================= */


.values{


    display:flex;


    justify-content:space-between;


    padding:0 40px;


    font-size:38px;


    font-weight:bold;


    margin-bottom:15px;



}






/* =========================
   BALKEN
========================= */


.bar{


    width:100%;


    height:42px;


    background:#000;


    border-radius:25px;


    overflow:hidden;


    display:flex;


    border:1px solid #555;



}






.home-bar{


    height:100%;


    background:var(--home-color);


    width:60%;


    transition:.5s;


}




.away-bar{


    height:100%;


    background:var(--away-color);


    width:40%;


    transition:.5s;


}





</style>






<!-- =========================
   EXPECTED GOALS
========================= -->


<div class="panel">


<div class="panel-title">

Expected Goals (xG)

</div>




<div class="values">


<span class="home-color">

1.24

</span>



<span class="away-color">

0.80

</span>



</div>




<div class="bar">


<div class="home-bar"

style="width:61%">

</div>


<div class="away-bar"

style="width:39%">

</div>


</div>



</div>








<!-- =========================
   BALLBESITZ
========================= -->


<div class="panel">


<div class="panel-title">

Ballbesitz

</div>




<div class="values">


<span class="home-color">

58%

</span>



<span class="away-color">

42%

</span>



</div>




<div class="bar">


<div class="home-bar"

style="width:58%">

</div>




<div class="away-bar"

style="width:42%">

</div>



</div>



</div>
<!-- =========================
   STATISTIK KARTEN
========================= -->


<style>


.stats-grid{


    margin-top:25px;


    display:grid;


    grid-template-columns:

    repeat(3,1fr);


    gap:20px;



}






.stat-box{


    background:


    linear-gradient(
        145deg,
        #333,
        #111
    );



    border-radius:22px;


    padding:25px;


    text-align:center;


    border:1px solid #444;


    box-shadow:

    0 15px 30px #000;



}






.stat-title{


    color:#aaa;


    font-size:14px;


    letter-spacing:2px;


    margin-bottom:15px;



}






.stat-value{


    font-size:38px;


    font-weight:bold;



}




.home-number{


    color:var(--home-color);



}





.away-number{


    color:var(--away-color);



}




.stat-value span{


    margin:0 8px;


}



</style>







<div class="stats-grid">






<div class="stat-box">


<div class="stat-title">

SCHÜSSE

</div>


<div class="stat-value">


<span class="home-number">

10

</span>


:


<span class="away-number">

12

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

SCHÜSSE AUFS TOR

</div>


<div class="stat-value">


<span class="home-number">

5

</span>


:


<span class="away-number">

4

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

GROSSCHANCEN

</div>


<div class="stat-value">


<span class="home-number">

3

</span>


:


<span class="away-number">

2

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

ECKEN

</div>


<div class="stat-value">


<span class="home-number">

6

</span>


:


<span class="away-number">

4

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

PÄSSE

</div>


<div class="stat-value">


<span class="home-number">

454

</span>


:


<span class="away-number">

464

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

GELBE KARTEN

</div>


<div class="stat-value">


<span class="home-number">

1

</span>


:


<span class="away-number">

2

</span>


</div>


</div>







</div>
<!-- =========================
   SPIELTAG LISTE
========================= -->


<style>


.spielkarte{


    margin-top:15px;


    padding:15px;


    border-radius:18px;


    background:


    linear-gradient(
        145deg,
        #333,
        #111
    );


    border:1px solid #555;


    cursor:pointer;


    text-align:center;


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



.liga-tabelle{


    margin-top:25px;


    background:


    linear-gradient(
        145deg,
        #222,
        #090909
    );


    border-radius:20px;


    padding:15px;


    border:1px solid #444;



}





.liga-tabelle h2{


    text-align:center;


    color:#f5c542;


    margin-bottom:15px;


}





.liga-row{


    display:grid;


    grid-template-columns:

    1fr 40px;


    padding:10px;


    border-bottom:1px solid #333;


}





.punkte{


    text-align:right;


    font-weight:bold;


    color:#f5c542;


}




.live-box{


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




.live-box h2{


    color:#f5c542;


    margin-bottom:20px;


}





#liveInput{


    width:100%;


    height:220px;


    background:#050505;


    color:white;


    border:1px solid #555;


    border-radius:15px;


    padding:20px;


    resize:none;


}




button{


    width:100%;


    margin-top:15px;


    padding:15px;


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






<!-- =========================
   SPIELE LINKS
========================= -->


<div class="spielkarte">


<div class="spielzeit">

29.08. 15:30

</div>


<div class="verein home-color">

1. FC Köln

</div>


<div>

VS

</div>


<div class="verein away-color">

TSG Hoffenheim

</div>



</div>








<div class="spielkarte">


<div class="spielzeit">

29.08. 18:30

</div>


<div class="verein home-color">

Bayer Leverkusen

</div>


<div>

VS

</div>


<div class="verein away-color">

RB Leipzig

</div>



</div>









<!-- =========================
   TABELLE
========================= -->


<div class="liga-tabelle">


<h2>

BUNDESLIGA

</h2>



<div class="liga-row">

<span>

1. Bayern München

</span>

<span class="punkte">

45

</span>

</div>




<div class="liga-row">

<span>

2. Bayer Leverkusen

</span>

<span class="punkte">

42

</span>

</div>




<div class="liga-row">

<span>

3. Borussia Dortmund

</span>

<span class="punkte">

38

</span>

</div>




<div class="liga-row">

<span>

4. RB Leipzig

</span>

<span class="punkte">

35

</span>

</div>




</div>







<!-- =========================
   LIVE DATEN
========================= -->


<div class="live-box">


<h2>

LIVE DATEN

</h2>




<textarea id="liveInput"

placeholder="

1.24

0.80


58%

42%


10

12


454/526

464/524


1

2

"></textarea>




<button>

DATEN ÜBERNEHMEN

</button>



<button>

💾 SPIEL SPEICHERN

</button>



<button>

📂 SPIEL LADEN

</button>



</div>
<!-- =========================
   JAVASCRIPT
========================= -->


<script>


/* =========================
   MANNSCHAFTSFARBEN
========================= */


const teamColors = {


"1. FC Köln":"#e30613",

"TSG Hoffenheim":"#005ca9",

"Bayer Leverkusen":"#e32221",

"RB Leipzig":"#dd0000",

"Borussia Dortmund":"#f6d800",

"Bayern München":"#dc052d",

"Eintracht Frankfurt":"#e1000f",

"Mainz 05":"#c31432"


};





function setTeamColors(home,away){



let homeColor =

teamColors[home]

||

"#0099ff";



let awayColor =

teamColors[away]

||

"#ff3344";





document.documentElement.style.setProperty(

"--home-color",

homeColor

);



document.documentElement.style.setProperty(

"--away-color",

awayColor

);



}







/* =========================
   LIVE DATEN
========================= */


function datenAktualisieren(){



let text =

document.getElementById("liveInput").value;



let zahlen =

text.match(/\d+(?:\.\d+)?/g);



if(!zahlen)

return;





let xgHome =

Number(zahlen[0] || 0);



let xgAway =

Number(zahlen[1] || 0);



let gesamt =

xgHome + xgAway;





if(gesamt>0){


document.querySelectorAll(".home-bar")[0].style.width =

(xgHome / gesamt * 100)+"%";



document.querySelectorAll(".away-bar")[0].style.width =

(xgAway / gesamt * 100)+"%";


}





let prozent =

text.match(/\d+%/g);



if(prozent && prozent.length>=2){


document.querySelectorAll(".values span")[2].innerHTML =

prozent[0];


document.querySelectorAll(".values span")[3].innerHTML =

prozent[1];


}





}









/* =========================
   SPEICHERN
========================= */


function speichern(){



localStorage.setItem(

"Wettpropheten_Dashboard",

document.body.innerHTML

);



alert("Spiel gespeichert");



}







/* =========================
   LADEN
========================= */


function laden(){



let daten =

localStorage.getItem(

"Wettpropheten_Dashboard"

);



if(daten){



document.body.innerHTML = daten;



alert("Spiel geladen");



}



}







/* =========================
   START
========================= */


setTeamColors(

"1. FC Köln",

"TSG Hoffenheim"

);



</script>


</body>

</html>
