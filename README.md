<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Fußball Analyse</title>

<style>

* {
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}


body {

    min-height:100vh;
    background:#111;
    display:flex;
    justify-content:center;
    align-items:center;

}


.container {

    width:1400px;
    padding:40px;
    background:#181818;
    border-radius:25px;

}


/* Kopf */

.header {

    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:60px;

}


.team {

    width:35%;
    height:80px;
    background:#222;
    border-radius:15px;

    display:flex;
    justify-content:center;
    align-items:center;

    color:white;
    font-size:28px;
    font-weight:bold;

}


.vs {

    color:white;
    font-size:35px;
    font-weight:bold;

}



/* Felder */

.fields {

    display:flex;
    justify-content:center;
    gap:70px;

    perspective:1200px;

}



.field {

    width:420px;
    height:650px;

    position:relative;

    background:
    repeating-linear-gradient(
        0deg,
        #287342,
        #287342 45px,
        #317d49 45px,
        #317d49 90px
    );


    border:3px solid white;


    transform:
    rotateX(55deg);


    box-shadow:
    0 45px 70px rgba(0,0,0,.8);


    overflow:hidden;

}



/* Mittellinie richtig */

.field::before {

    content:"";

    position:absolute;

    left:0;
    top:50%;

    width:100%;
    height:3px;

    background:white;

    transform:translateY(-50%);

}



/* Mittelkreis */

.field::after {

    content:"";

    position:absolute;

    left:50%;
    top:50%;


    width:110px;
    height:110px;


    border:3px solid white;

    border-radius:50%;


    transform:
    translate(-50%,-50%);

}



/* Strafräume */

.penalty {

    position:absolute;

    left:50%;

    width:220px;
    height:90px;

    border:3px solid white;

    transform:translateX(-50%);

}


.top {

    top:0;

}


.bottom {

    bottom:0;

}



/* Tor */

.goal {

    position:absolute;

    left:50%;

    width:90px;
    height:25px;

    border:3px solid white;

    transform:translateX(-50%);

}


.goal-top {

    top:0;

}


.goal-bottom {

    bottom:0;

}



</style>

</head>


<body>


<div class="container">


<div class="header">

<div class="team">
HEIMTEAM
</div>


<div class="vs">
VS
</div>


<div class="team">
GASTTEAM
</div>


</div>



<div class="fields">


<div class="field">

<div class="penalty top"></div>
<div class="penalty bottom"></div>

<div class="goal goal-top"></div>
<div class="goal goal-bottom"></div>

</div>



<div class="field">

<div class="penalty top"></div>
<div class="penalty bottom"></div>

<div class="goal goal-top"></div>
<div class="goal goal-bottom"></div>

</div>


</div>



</div>


</body>
</html>
