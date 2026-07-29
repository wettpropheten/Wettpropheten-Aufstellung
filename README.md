<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Dashboard Teil 1</title>


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

    overflow:hidden;

}



body{

    position:absolute;

    left:0;
    top:0;

}



/* =========================
   HAUPT CONTAINER
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
   SPIELTAG LINKS
========================= */


.sidebar{


    flex:0 0 260px;

    width:260px;

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


    color:#f5c542;

    text-align:center;

    font-size:26px;

    margin-bottom:20px;


}



.spieltag{

    height:calc(100vh - 80px);


    border-radius:15px;


    background:#111;


    border:1px solid #555;


    padding:15px;


    color:#aaa;


}






/* =========================
   HAUPTFENSTER
========================= */


.main{


    flex:1;


    height:100vh;


    width:calc(100vw - 260px);


    padding:20px;


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


.header{


    width:100%;


    height:180px;


    display:grid;


    grid-template-columns:1fr 200px 1fr;


    align-items:center;


    border-radius:30px;


    background:#111;


}



.team{


    text-align:center;


    color:white;


    font-size:42px;


    font-weight:bold;


}



.score{


    text-align:center;


    font-size:90px;


    font-weight:bold;


    color:#f5c542;


}



</style>


</head>


<body>


<div class="app">



<div class="sidebar">


<h1>

SPIELTAG

</h1>


<div class="spieltag">


Hier kommen später die Spiele rein


</div>


</div>





<div class="main">


<div class="header">


<div class="team">

HEIM

</div>



<div class="score">

0 : 0

</div>



<div class="team">

GAST

</div>


</div>


</div>



</div>



</body>

</html>
