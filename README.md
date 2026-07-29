<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

/* =========================
   GRUNDLAYOUT
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
   HAUPT APP
========================= */


.app{

position:absolute;

left:0;
top:0;

width:100vw;

height:100vh;

display:flex;

}





/* =========================
   LINKE SEITE
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


overflow:hidden;

}





.sidebar h1{

text-align:center;

color:#f5c542;

font-size:26px;

margin-bottom:20px;

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


.header{

width:100%;

height:180px;


display:grid;

grid-template-columns:

1fr 200px 1fr;


align-items:center;


border-radius:30px;


background:

linear-gradient(

90deg,

#111,

#222,

#111

);


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
   MANNSCHAFTSFARBEN
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
   BALKEN
========================= */


.values{


display:flex;

justify-content:space-between;

padding:0 40px;

font-size:38px;

font-weight:bold;

margin-bottom:15px;


}



.bar{


width:100%;

height:42px;


display:flex;


background:#000;


border-radius:25px;


overflow:hidden;


border:1px solid #555;


}




.home-bar{


height:100%;


width:60%;


background:var(--home-color);


}




.away-bar{


height:100%;


width:40%;


background:var(--away-color);


}


<!-- =========================
   TEIL 2
   xG + BALLBESITZ
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


border:1px solid #444;


text-align:center;


box-shadow:

0 15px 30px #000;



}




.stat-title{


font-size:14px;


letter-spacing:2px;


color:#aaa;


margin-bottom:15px;



}





.stat-value{


font-size:38px;


font-weight:bold;


}





.stat-value .home{


color:var(--home-color);

}



.stat-value .away{


color:var(--away-color);

}



</style>





<div class="stats-grid">





<div class="stat-box">


<div class="stat-title">

SCHÜSSE

</div>


<div class="stat-value">


<span class="home">

10

</span>

:

<span class="away">

12

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

SCHÜSSE AUFS TOR

</div>


<div class="stat-value">


<span class="home">

5

</span>

:

<span class="away">

4

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

GROSSCHANCEN

</div>


<div class="stat-value">


<span class="home">

3

</span>

:

<span class="away">

2

</span>


</div>


</div>








<div class="stat-box">


<div class="stat-title">

ECKEN

</div>


<div class="stat-value">


<span class="home">

6

</span>

:

<span class="away">

4

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

PÄSSE

</div>


<div class="stat-value">


<span class="home">

454

</span>

:

<span class="away">

464

</span>


</div>


</div>







<div class="stat-box">


<div class="stat-title">

GELBE KARTEN

</div>


<div class="stat-value">


<span class="home">

1

</span>

:

<span class="away">

2

</span>


</div>


</div>





</div>
<!-- =========================
   TEIL 3
   SPIELTAG + MANNSCHAFTEN
========================= -->


<style>


/* SPIELKARTEN */

.spiel-liste{

margin-top:20px;

}



.spielkarte{


background:

linear-gradient(

145deg,

#333,

#111

);



border:1px solid #555;


border-radius:18px;


padding:15px;


margin-bottom:12px;


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


margin:5px;


}





/* VEREINSFARBEN */


.verein.home{


color:var(--home-color);


}




.verein.away{


color:var(--away-color);


}





</style>






<!-- =========================
   SPIELTAG LISTE
========================= -->


<div class="spiel-liste">





<div class="spielkarte">


<div class="spielzeit">

29.08. 15:30

</div>



<div class="verein home">

1. FC Köln

</div>


<div>

VS

</div>


<div class="verein away">

TSG Hoffenheim

</div>



</div>








<div class="spielkarte">


<div class="spielzeit">

29.08. 18:30

</div>



<div class="verein home">

Bayer Leverkusen

</div>


<div>

VS

</div>


<div class="verein away">

RB Leipzig

</div>



</div>








<div class="spielkarte">


<div class="spielzeit">

30.08. 15:30

</div>



<div class="verein home">

Borussia Dortmund

</div>


<div>

VS

</div>


<div class="verein away">

FC Bayern München

</div>



</div>





</div>








<!-- =========================
   LIGA TABELLE
========================= -->


<style>


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


font-size:20px;


margin-bottom:15px;


}





.liga-row{


display:grid;


grid-template-columns:

1fr 50px;



padding:10px;


border-bottom:1px solid #333;



}



.liga-row:last-child{


border-bottom:none;


}





.punkte{


text-align:right;


font-weight:bold;


color:#f5c542;


}



</style>







<div class="liga-tabelle">


<h2>

BUNDESLIGA

</h2>



<div class="liga-row">

<span>

1. FC Bayern München

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
   TEIL 4
   SPIELDATEN TABELLE
========================= -->


<style>


/* =========================
   DATEN TABELLE
========================= */


.daten-panel{


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



.daten-title{


font-size:26px;


font-weight:bold;


color:#f5c542;


margin-bottom:20px;


}





.daten-tabelle{


width:100%;


border-collapse:collapse;


font-size:18px;


}



.daten-tabelle th{


background:#333;


padding:15px;


}




.daten-tabelle td{


padding:15px;


border-bottom:1px solid #444;


text-align:center;


}





.daten-tabelle td:first-child{


text-align:left;


color:#aaa;


}





</style>






<div class="daten-panel">


<div class="daten-title">

SPIELDATEN

</div>





<table class="daten-tabelle">


<thead>


<tr>


<th>

STATISTIK

</th>


<th>

HEIM

</th>


<th>

GAST

</th>


</tr>


</thead>



<tbody>



<tr>

<td>

Expected Goals (xG)

</td>


<td class="home-number">

1.24

</td>


<td class="away-number">

0.80

</td>


</tr>






<tr>

<td>

Ballbesitz

</td>


<td class="home-number">

58%

</td>


<td class="away-number">

42%

</td>


</tr>







<tr>

<td>

Schüsse

</td>


<td class="home-number">

10

</td>


<td class="away-number">

12

</td>


</tr>







<tr>

<td>

Schüsse aufs Tor

</td>


<td class="home-number">

5

</td>


<td class="away-number">

4

</td>


</tr>







<tr>

<td>

Pässe

</td>


<td class="home-number">

454/526

</td>


<td class="away-number">

464/524

</td>


</tr>







<tr>

<td>

Passquote

</td>


<td class="home-number">

86%

</td>


<td class="away-number">

89%

</td>


</tr>








<tr>

<td>

Gelbe Karten

</td>


<td class="home-number">

1

</td>


<td class="away-number">

2

</td>


</tr>





</tbody>


</table>


</div>









<!-- =========================
   LIVE DATEN
========================= -->


<style>


.live-panel{


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



.live-title{


font-size:26px;


font-weight:bold;


color:#f5c542;


margin-bottom:20px;


}




#liveInput{


width:100%;


height:220px;


background:#050505;


color:white;


border:1px solid #555;


border-radius:18px;


padding:20px;


font-size:16px;


resize:none;


}




.live-button{


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



.live-button:hover{


filter:brightness(1.3);


}




</style>







<div class="live-panel">


<div class="live-title">

LIVE DATEN EINGEBEN

</div>





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

">

</textarea>





<button class="live-button">

DATEN ÜBERNEHMEN

</button>



<button class="live-button">

💾 SPIEL SPEICHERN

</button>



<button class="live-button">

📂 SPIEL LADEN

</button>



</div>
</script>
</body>
</html>
