<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard</title>


<style>

*{
    box-sizing:border-box;
    font-family:Arial,Helvetica,sans-serif;
}


html,body{

    margin:0;
    padding:0;

    width:100%;
    height:100%;

    background:#050505;
    color:white;

    overflow:hidden;
}


/* =====================
   GESAMT
===================== */


.app{

    display:flex;

    width:100vw;
    height:100vh;

}


/* =====================
   SPIELTAG LINKS
===================== */


.sidebar{

    width:260px;
    min-width:260px;

    height:100vh;

    background:
    linear-gradient(
        180deg,
        #222,
        #070707
    );

    border-right:2px solid #444;

    padding:15px;

}



.sidebar h1{

    margin:5px 0 20px;

    text-align:center;

    color:#f5c542;

    font-size:26px;

}


.spieltag-box{

    background:#111;

    border:1px solid #555;

    border-radius:15px;

    height:300px;

    padding:15px;

    color:white;

}



/* =====================
   HAUPTBEREICH
===================== */


.main{

    flex:1;

    height:100vh;

    padding:20px;

    overflow:hidden;


    background:

    linear-gradient(
        145deg,
        #181818,
        #050505
    );

}




/* =====================
   SPIELKOPF
===================== */


.score-header{


    width:100%;

    height:180px;


    display:grid;

    grid-template-columns:1fr 200px 1fr;


    align-items:center;


    background:

    linear-gradient(
        90deg,
        #ffffff15,
        transparent,
        #ffffff15
    );


    border-radius:30px;


}


.team-name{


    text-align:center;

    font-size:42px;

    font-weight:bold;


}


.score{


    text-align:center;

    font-size:90px;

    color:#f5c542;

    font-weight:bold;

}





/* =====================
   BALKEN MODULE
===================== */


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




.panel-title{

    color:#f5c542;

    font-size:25px;

    font-weight:bold;

    margin-bottom:20px;

}



.values{


    display:flex;

    justify-content:space-between;


    font-size:35px;

    font-weight:bold;


    padding:0 30px;

    margin-bottom:15px;


}





.bar{


    width:100%;

    height:40px;


    display:flex;

    overflow:hidden;


    border-radius:20px;


    background:#000;


    border:1px solid #555;


}




.home-bar{

    width:60%;

    background:#0099ff;


}



.away-bar{

    width:40%;

    background:#ff3344;


}






/* =====================
   STATISTIK KARTEN
===================== */


.stats-grid{


    margin-top:25px;


    display:grid;

    grid-template-columns:repeat(3,1fr);


    gap:20px;


}



.stat-box{


    background:#181818;


    border:1px solid #444;


    border-radius:20px;


    padding:25px;


    text-align:center;


    font-size:18px;


}



.stat-box strong{


    display:block;


    margin-top:15px;


    font-size:35px;


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

Spiele kommen hier rein

</div>


</div>





<!-- HAUPTANSICHT -->

<div class="main">



<div class="score-header">


<div class="team-name">

HEIM

</div>


<div class="score">

0 : 0

</div>


<div class="team-name">

GAST

</div>


</div>





<div class="panel">


<div class="panel-title">

Expected Goals (xG)

</div>


<div class="values">

<span>

1.24

</span>


<span>

0.80

</span>


</div>


<div class="bar">


<div class="home-bar"></div>

<div class="away-bar"></div>


</div>


</div>







<div class="panel">


<div class="panel-title">

Ballbesitz

</div>


<div class="values">

<span>

58%

</span>


<span>

42%

</span>


</div>


<div class="bar">


<div class="home-bar"></div>

<div class="away-bar"></div>


</div>


</div>






<div class="stats-grid">


<div class="stat-box">

SCHÜSSE

<strong>

12 : 8

</strong>

</div>



<div class="stat-box">

ECKEN

<strong>

6 : 3

</strong>

</div>



<div class="stat-box">

PÄSSE

<strong>

450 : 380

</strong>

</div>



</div>



</div>


</div>


</body>

</html>
