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
