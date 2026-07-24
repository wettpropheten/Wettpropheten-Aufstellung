<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>Wettpropheten - Fußball Analyse</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{

    background:#111;
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;

}


.container{

    width:1400px;
    padding:40px;

    background:#181818;
    border-radius:25px;

}



.header{

    display:flex;
    justify-content:space-between;
    align-items:center;

    margin-bottom:50px;

}


.team{

    width:35%;
    height:80px;

    background:#222;

    border-radius:15px;

    color:white;

    display:flex;
    align-items:center;
    justify-content:center;

    font-size:28px;
    font-weight:bold;

}


.vs{

    color:white;
    font-size:38px;
    font-weight:bold;

}



/* 3D FELDER */

.fields{

    display:flex;
    justify-content:center;
    gap:80px;

    perspective:1200px;

}


.field{

    width:430px;
    height:650px;

    position:relative;


    background:
    repeating-linear-gradient(
        0deg,
        #24723d 0px,
        #24723d 45px,
        #2d8248 45px,
        #2d8248 90px
    );


    border:3px solid white;


    transform:

        perspective(900px)

        rotateX(60deg);


    transform-origin:center bottom;


    box-shadow:

        0 80px 100px rgba(0,0,0,.85),

        inset 0 0 40px rgba(0,0,0,.35);


    overflow:hidden;

}



/* RICHTIGE MITTELLINIE */

.field::before{

    content:"";

    position:absolute;

    left:0;
    top:50%;


    width:100%;
    height:3px;


    background:white;


    transform:translateY(-50%);

}



/* MITTELKREIS */

.field::after{

    content:"";

    position:absolute;

    left:50%;
    top:50%;


    width:110px;
    height:110px;


    border:3px solid white;

    border-radius:50%;


    transform:translate(-50%,-50%);

}



/* STRAFRAUM */

.penalty{

    position:absolute;

    left:50%;


    width:230px;
    height:100px;


    border:3px solid white;


    transform:translateX(-50%);

}


.top{

    top:0;

}


.bottom{

    bottom:0;

}



/* TOR */

.goal{

    position:absolute;

    left:50%;


    width:90px;
    height:30px;


    border:3px solid white;


    transform:translateX(-50%);

}


.goal-top{

    top:0;

}


.goal-bottom{

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
