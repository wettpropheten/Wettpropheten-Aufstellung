<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>Wettpropheten - Aufstellung</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    min-height:100vh;
    background:#111;
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



/* Kopf bleibt */

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

    color:white;

    display:flex;
    justify-content:center;
    align-items:center;

    border-radius:15px;

    font-size:28px;
    font-weight:bold;

}


.vs{

    color:white;
    font-size:36px;
    font-weight:bold;

}



/* zwei Felder */

.fields{

    display:flex;

    justify-content:center;

    gap:60px;

    perspective:1400px;

}



/* Feld */

.field{

    width:430px;

    height:650px;

    position:relative;


    background:

    repeating-linear-gradient(
        0deg,
        #267541 0px,
        #267541 45px,
        #2e8249 45px,
        #2e8249 90px
    );


    border:3px solid white;


    transform-style:preserve-3d;


    transform:

    rotateX(48deg);


    box-shadow:

    0 70px 90px rgba(0,0,0,.8);

}



/* richtige Mittellinie */

.field .middle{

    position:absolute;

    left:0;

    top:50%;

    width:100%;

    height:3px;

    background:white;

    transform:translateY(-50%);

}



/* Mittelkreis */

.field .circle{

    position:absolute;

    left:50%;

    top:50%;


    width:110px;

    height:110px;


    border:3px solid white;

    border-radius:50%;


    transform:translate(-50%,-50%);

}



/* Strafräume */

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

<div class="middle"></div>

<div class="circle"></div>

<div class="penalty top"></div>

<div class="penalty bottom"></div>

</div>




<div class="field">

<div class="middle"></div>

<div class="circle"></div>

<div class="penalty top"></div>

<div class="penalty bottom"></div>

</div>


</div>



</div>


</body>
</html>
